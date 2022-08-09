---
title: 管理索引器
description: 請參閱如何查看和管理Commerce索引器的示例。
source-git-commit: dd84039be22b6bd25d57912615d64bad91970926
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# 管理索引器

{{file-system-owner}}

要查看所有索引器的清單：

```bash
bin/magento indexer:info
```

清單顯示如下：

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

## 查看索引器狀態

使用此命令可以查看所有索引器或特定索引器的狀態。 例如，查找是否需要重新索引索引器。

命令選項：

```bash
bin/magento indexer:status [indexer]
```

位置 `[indexer]` 是索引器的空格分隔清單。 省略 `[indexer]` 查看所有索引器的狀態。

示例結果：

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## 重新索引

使用此命令僅對所有索引器或所選索引器重新索引一次。

>[!INFO]
>
>此命令僅對一次重新索引。 要使索引器保持最新，必須設定 [克倫](../cli/configure-cron-jobs.md)。

命令選項：

```bash
bin/magento indexer:reindex [indexer]
```

位置 `[indexer]` 是索引器的空格分隔清單。 省略 `[indexer]` 重新索引所有索引器。

示例結果：

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>對於擁有大量產品、客戶、類別和促銷規則的商店，重新索引所有索引器可能需要很長時間。

### 在並行模式下重新索引

索引器被確定範圍並進行多線程，以支援在並行模式下重新索引。 它按索引器的尺寸並行並跨多個線程執行，從而縮短處理時間。

在這種背景下， `dimension` 是重新索引的範圍，例如 `website` 或者只是 `customer_group`。

索引並行化僅影響範圍內的索引器，這意味著Commerce將資料拆分為多個表，使用索引器作為其範圍，而不是將所有資料保留在一個表中。

可以在並行模式下運行以下索引：

- `Catalog Search Fulltext` 可以與商店景觀並行。
- `Category Product` 可以與商店景觀並行。
- `Catalog Price` 網站和客戶群可以並行。
- `Catalog Permissions` 可以與客戶群並行。

要使用並行化，請為產品價格索引器設定一個可用的維度模式：

- `none` （預設）
- `website`
- `customer_group`
- `website_and_customer_group`

例如，要設定每個網站的模式：

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

要對目錄權限使用並行化，請為目錄權限索引器設定一個可用的維模式：

- `none` （預設）
- `customer_group`

或者，要檢查當前模式：

```bash
bin/magento indexer:show-dimensions-mode
```

要在並行模式下重新索引，請使用環境變數運行reindex命令 `MAGE_INDEXER_THREADS_COUNT`，或將環境變數添加到 `env.php` 的子菜單。 此變數設定重新索引處理的線程數。

例如，以下命令運行 `Catalog Search Fulltext` 索引器跨三個線程：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 重置索引器

使用此命令可使所有索引器或特定索引器的狀態失效。

命令選項：

```bash
bin/magento indexer:reset [indexer]
```

位置 ```[indexer]``` 是索引器的空格分隔清單。 省略 `[indexer]` 使所有索引器失效。

示例結果：

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## 配置索引器

使用此命令可設定以下索引器選項：

- **保存時更新(`realtime`)**:在管理員中進行更改時，將更新索引資料。 （例如，在將產品添加到管理中的類別後，將重新索引類別產品索引。） 這是預設值。
- **按計畫更新(`schedule`)**:根據cron作業設定的計畫編製資料索引。

[瞭解有關索引的更多資訊](https://developer.adobe.com/commerce/php/development/components/indexing/)。

### 顯示當前配置

要查看當前索引器配置，請執行以下操作：

```bash
bin/magento indexer:show-mode [indexer]
```

位置 `[indexer]` 是索引器的空格分隔清單。 省略 `[indexer]` 顯示所有索引器模式。 例如，要顯示所有索引器的模式：

示例結果：

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### 配置索引器

>[!INFO]
>
>在切換索引器模式之前，我們建議將您的網站置於 [維護](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html) 模式和 [禁用cron作業](https://devdocs.magento.com/cloud/configure/setup-cron-jobs.html#disable-cron-jobs)。 這可確保您不會遭受資料庫鎖。

要指定索引器配置：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

位置：

- `realtime` — 設定要在保存時更新的選定索引器。
- `schedule` — 根據cron計畫設定要保存的指定索引器。
- `indexer` — 是索引器的空格分隔清單。 省略 `indexer` 以相同方式配置所有索引器。

例如，要僅更改類別產品和產品類別索引器以按計畫更新，請輸入：

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

示例結果：

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

當索引器模式設定為時，將添加與索引器相關的資料庫觸發器 `schedule` 在索引器模式設定為時刪除 `realtime`。 如果索引器設定為時資料庫中缺少觸發器 `schedule`，將索引器更改為 `realtime` 然後把它們改回 `schedule`。 這將重置觸發器。
