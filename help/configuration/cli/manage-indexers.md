---
title: 管理索引子
description: 請參閱如何檢視和管理Commerce索引器的範例。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---

# 管理索引子

{{file-system-owner}}

若要檢視所有索引子的清單：

```bash
bin/magento indexer:info
```

清單顯示如下：

```
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

>[!NOTE]
> 使用「即時搜尋」、「目錄服務」或「產品Recommendations」的Adobe Commerce商家可選擇使用[SaaS式價格索引](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html)。

## 檢視索引器狀態

使用此指令可檢視所有索引器或特定索引器的狀態。 例如，瞭解索引器是否需要重新索引。

命令選項：

```bash
bin/magento indexer:status [indexer]
```

其中`[indexer]`是以空格分隔的索引子清單。 省略`[indexer]`以檢視所有索引子的狀態。

範例結果：

```
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

```
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

```
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

## 設定索引子

使用此指令來設定下列索引器選項：

- **儲存時更新(`realtime`)**：在管理員中進行變更時，索引資料會更新。 （例如，將產品新增至管理員中的類別後，類別產品索引會重新索引。） 這是預設值。
- **依排程更新(`schedule`)**：資料已根據cron工作設定的排程編制索引。

[進一步瞭解索引](https://developer.adobe.com/commerce/php/development/components/indexing/)。

### 顯示目前的設定

若要檢視目前的索引器組態：

```bash
bin/magento indexer:show-mode [indexer]
```

其中`[indexer]`是以空格分隔的索引子清單。 省略`[indexer]`以顯示所有索引子模式。 例如，若要顯示所有索引子的模式：

範例結果：

```
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

### 設定索引器模式

>[!IMPORTANT]
>
>請務必以`realtime`設定[!DNL Customer Grid]，而非`schedule`。 只能使用[!UICONTROL Update on Save]選項來重新索引[!DNL Customer Grid]。 此索引不支援`Update by Schedule`選項。 使用以下命令列，設定此索引器在儲存時更新： `php bin/magento indexer:set-mode realtime customer_grid`
>
>請參閱&#x200B;_實作行動手冊_&#x200B;中的[索引子組態的最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)。

>[!INFO]
>
>在切換索引器模式之前，請將您的網站設定為[維護](../../installation/tutorials/maintenance-mode.md)模式和[停用cron工作](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs)。 這可確保您不會遭受資料庫鎖定的困擾。

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

**已略過重新索引**：已略過`suspended`個索引子及任何共用相同`shared_index`的索引子的自動重新索引。 這樣可確保不會重新索引與已暫停處理序相關的資料，以節省系統資源。

**已略過具體化視觀表更新**：與重新索引類似，也會暫停與`suspended`索引子或其共用索引相關的具體化視觀表更新。 此動作會進一步減少暫停期間的系統負載。

>[!INFO]
>
>`indexer:reindex`命令會重新索引所有索引子，包括標示為`suspended`的索引子，以便在自動索引子暫停時手動更新。

>[!IMPORTANT]
>
>將索引器的狀態從`suspended`或`invalid`變更為`valid`需要謹慎。 如果有累積的未索引資料，此動作可能會導致效能降低。
>
>在手動將狀態更新為`valid`以維持系統效能和資料完整性之前，請務必確保所有資料都正確編制索引。
