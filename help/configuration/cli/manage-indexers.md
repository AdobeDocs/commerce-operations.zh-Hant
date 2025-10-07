---
title: 管理索引子
description: 瞭解如何使用命令列工具檢視和管理Adobe Commerce索引子。 探索索引器命令、狀態檢查和重新索引技術。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---

# 管理索引子

{{file-system-owner}}

若要檢視所有索引子的清單：

```bash
bin/magento indexer:info
```

清單顯示如下：

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> 使用Live Search、目錄服務或產品推薦的Adobe Commerce商家可選擇使用[SaaS式價格索引](https://experienceleague.adobe.com/zh-hant/docs/commerce/price-indexer/price-indexing)。

## 檢視索引器狀態

使用此指令可檢視所有索引器或特定索引器的狀態。 例如，瞭解索引器是否需要重新索引。

命令選項：

```bash
bin/magento indexer:status [indexer]
```

其中`[indexer]`是以空格分隔的索引子清單。 省略`[indexer]`以檢視所有索引子的狀態。

範例結果：

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
```

## 重新索引

使用此指令可只重新索引一次所有或選取的索引子。

>[!INFO]
>
>此命令只會重新索引一次。 若要讓索引子保持最新狀態，您必須設定[cron工作](../cli/configure-cron-jobs.md)。

命令選項：

```bash
bin/magento indexer:reindex [indexer]
```

其中`[indexer]`是以空格分隔的索引子清單。 省略`[indexer]`以重新索引所有索引子。

範例結果：

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>對於有大量產品、客戶、類別和促銷規則的商店，重新索引所有索引子可能需要很長的時間。

### 以平行模式重新索引

{{php-process-control}}

索引器具有範圍和多執行緒，以支援在平行模式中重新索引。 它透過索引器的維度來平行處理，並在多個執行緒上執行，以減少處理時間。

在此內容中，`dimension`是重新索引的範圍，例如執行個體`website`或只是特定`customer_group`。

索引平行化只會影響範圍的索引子，這表示Commerce會使用索引子做為範圍將資料分割成多個表格，而非將所有資料儲存在單一表格中。

您可以在平行模式下執行下列索引：

- `Catalog Search Fulltext`可透過存放區檢視並行。
- `Category Product`可透過存放區檢視並行。
- `Catalog Price`可由網站和客戶群組並行。
- `Catalog Permissions`可由客戶群組並行。

>[!INFO]
>
>目錄搜尋全文檢索與類別產品的平行化預設為啟用。

若要使用平行化，請針對產品價格索引器設定其中一個可用的維度模式：

- `none` （預設）
- `website`
- `customer_group`
- `website_and_customer_group`

例如，若要為每個網站設定模式：

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

若要對目錄許可權使用平行化，請為目錄許可權索引器設定其中一個可用的維度模式：

- `none` （預設）
- `customer_group`

或檢查目前模式：

```bash
bin/magento indexer:show-dimensions-mode
```

若要以平行模式重新索引，請使用環境變數`MAGE_INDEXER_THREADS_COUNT`執行重新索引命令，或將環境變數新增到`env.php`檔案。 此變數會設定重新索引處理的執行緒數目。

例如，下列命令會在三個執行緒上執行`Catalog Search Fulltext`索引器：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 重設索引子

使用此命令可讓所有索引器或特定索引器的狀態失效。

命令選項：

```bash
bin/magento indexer:reset [indexer]
```

其中```[indexer]```是以空格分隔的索引子清單。 省略`[indexer]`以讓所有索引子失效。

範例結果：

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## 設定索引子

使用此指令來設定下列索引器選項：

- **儲存時更新(`realtime`)**：在管理員中進行變更時，索引資料會更新。 （例如，將產品新增至管理員中的類別後，類別產品索引會重新索引。）
- **依排程更新(`schedule`)**：資料已根據cron工作設定的排程編制索引。

[進一步瞭解索引](https://developer.adobe.com/commerce/php/development/components/indexing/)。

### 顯示目前的設定

若要檢視目前的索引器組態：

```bash
bin/magento indexer:show-mode [indexer]
```

其中`[indexer]`是以空格分隔的索引子清單。 省略`[indexer]`以顯示所有索引子模式。 例如，若要顯示所有索引子的模式：

範例結果：

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### 設定索引器模式

>[!IMPORTANT]
>
>[!DNL Customer Grid]索引子行為在2.4.8中變更：
>
>- **2.4.8**&#x200B;之前： [!DNL Customer Grid]索引子只能使用[!UICONTROL Update on Save]選項重新索引，不支援[!UICONTROL Update by Schedule]選項。
>
>   使用下列命令設定此索引器在儲存時更新：
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8和更新版本**： [!DNL Customer Grid]索引子同時支援[!UICONTROL Update on Save]和[!UICONTROL Update by Schedule]模式，且預設為[!UICONTROL Update by Schedule]。
>
>請參閱[實作行動手冊](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration)中的&#x200B;_索引子組態的最佳實務_。

>[!INFO]
>
>在切換索引器模式之前，請將您的網站設定為[維護](../../installation/tutorials/maintenance-mode.md)模式和[停用cron工作](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property)。 這樣可確保不會發生資料庫鎖定的情況。

若要指定索引器組態：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

其中：

- `realtime` — 將選取的索引子設定為在儲存時更新。
- `schedule` — 設定要根據cron排程儲存的指定索引子。
- `indexer` — 是以空格分隔的索引子清單。 省略`indexer`以相同方式設定所有索引子。

例如，若要只變更類別產品和產品類別索引器，以依排程更新，請輸入：

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

範例結果：

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

當索引器模式設定為`schedule`時，會新增與索引器相關的資料庫觸發程式，而當索引器模式設定為`realtime`時，則會移除這些觸發程式。 如果索引子設為`schedule`時資料庫中缺少觸發程式，請將索引子變更為`realtime`，然後再變更回`schedule`。 這會重設觸發程式。

### 設定索引子狀態

已在Adobe Commerce 2.4.7中引入`bin/magento indexer:set-status`命令。它可讓管理員修改一或多個索引器的運作狀態，在資料匯入、更新或維護等大量作業期間最佳化系統效能。

命令語法：

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

其中：

- `invalid` — 將索引器標籤為過期，在下次cron執行時提示重新索引，除非它們被暫停。
- `suspended` — 暫時停止索引器的自動cron觸發更新。 此狀態同時適用於即時和排程模式，確保在密集作業期間暫停自動更新。
- `valid` — 表示索引器資料是最新的，不需要重新索引。
- `indexer` — 是以空格分隔的索引子清單。 省略`indexer`以相同方式設定所有索引子。

例如，若要暫停特定索引子，請輸入：

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

範例結果：

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### 管理暫停的索引器狀態

當索引子設定為`suspended`狀態時，它主要影響自動重新索引和具體化視觀表更新。 以下是簡短概述：

**已略過重新索引**：系統略過`suspended`個索引器及共用相同`shared_index`的任何索引器的自動重新索引。 此方法可避免重新索引與已暫停程式相關的資料，以節省系統資源。

**已略過具體化視觀表更新**：與重新索引類似，系統也會暫停與`suspended`索引器或其共用索引相關的具體化視觀表更新。 此暫停會進一步減少暫停期間的系統負載。

>[!INFO]
>
>`indexer:reindex`命令會重新索引所有索引子，包括標示為`suspended`的索引子，以便在自動索引子暫停時進行手動更新時非常有用。

>[!IMPORTANT]
>
>將索引器的狀態從`valid`或`suspended`變更為`invalid`需要謹慎。 如果有累積的未索引資料，此動作可能會導致效能降低。
>
>在手動將狀態更新為`valid`以維持系統效能和資料完整性之前，請務必確保所有資料都正確編制索引。
