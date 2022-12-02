---
title: 管理索引器
description: 請參閱如何檢視和管理商務索引器的範例。
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '626'
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

使用此命令可以查看所有索引器或特定索引器的狀態。 例如，了解索引器是否需要重新索引。

命令選項：

```bash
bin/magento indexer:status [indexer]
```

其中 `[indexer]` 是以空格分隔的索引器清單。 忽略 `[indexer]` 查看所有索引器的狀態。

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

使用此命令僅對所有索引器或選定索引器重新索引一次。

>[!INFO]
>
>此命令僅重新索引一次。 要使索引器保持最新，您必須設定 [cron job](../cli/configure-cron-jobs.md).

命令選項：

```bash
bin/magento indexer:reindex [indexer]
```

其中 `[indexer]` 是以空格分隔的索引器清單。 忽略 `[indexer]` 重新索引所有索引器。

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

索引器是限定範圍和多線程的，以支援在並行模式下重新索引。 它由索引器的維度並行並跨多個線程執行，從而減少處理時間。

在這方面， `dimension` 是重新索引的範圍，例如a `website` 或只是特定 `customer_group`.

索引並行化僅影響限定範圍的索引器，這意味著Commerce使用索引器作為其範圍將資料分割為多個表，而不是將所有資料保留在一個表中。

您可以以平行模式執行下列索引：

- `Catalog Search Fulltext` 可以並行顯示商店視圖。
- `Category Product` 可以並行顯示商店視圖。
- `Catalog Price` 可以與網站和客戶群並行。
- `Catalog Permissions` 可以由客戶群並行。

要使用並行化，請為產品價格索引器設定可用的維模式之一：

- `none` （預設）
- `website`
- `customer_group`
- `website_and_customer_group`

例如，若要根據網站設定模式：

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

要對目錄權限使用並行化，請為目錄權限索引器設定一個可用的維模式：

- `none` （預設）
- `customer_group`

或者，檢查當前模式：

```bash
bin/magento indexer:show-dimensions-mode
```

要在並行模式下重新索引，請使用環境變數運行reindex命令 `MAGE_INDEXER_THREADS_COUNT`，或將環境變數新增至 `env.php` 檔案。 此變數會設定重新索引處理的執行緒數。

例如，下列命令會執行 `Catalog Search Fulltext` 三個線程的索引器：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 重置索引器

使用此命令可使所有索引器或特定索引器的狀態無效。

命令選項：

```bash
bin/magento indexer:reset [indexer]
```

其中 ```[indexer]``` 是以空格分隔的索引器清單。 忽略 `[indexer]` 使所有索引器失效。

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

- **儲存時更新(`realtime`)**:在管理員中進行變更時，會更新已編列索引的資料。 （例如，將產品新增至「管理員」中的類別後，會重新索引類別產品索引。） 這是預設值。
- **按計畫更新(`schedule`)**:資料會根據您cron工作設定的排程進行索引。

[進一步了解索引](https://developer.adobe.com/commerce/php/development/components/indexing/).

### 顯示當前配置

要查看當前索引器配置，請執行以下操作：

```bash
bin/magento indexer:show-mode [indexer]
```

其中 `[indexer]` 是以空格分隔的索引器清單。 忽略 `[indexer]` 顯示所有索引器的模式。 例如，要顯示所有索引器的模式：

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
>在切換索引器模式之前，建議您先將網站放置在 [維護](../../installation/tutorials/maintenance-mode.md) 模式和 [禁用cron作業](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). 這可確保您不會受到資料庫鎖定的影響。

要指定索引器配置：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

其中：

- `realtime` — 設定要在保存時更新的選定索引器。
- `schedule` — 設定指定的索引器以根據cron調度進行保存。
- `indexer` — 是以空格分隔的索引器清單。 忽略 `indexer` 以相同的方式配置所有索引器。

例如，要僅更改類別產品和產品類別索引器以按計畫更新，請輸入：

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

示例結果：

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

當索引器模式設定為 `schedule` 和已刪除 `realtime`. 如果索引器設定為 `schedule`，請將索引器變更為 `realtime` 然後將它們變回 `schedule`. 這會重設觸發器。
