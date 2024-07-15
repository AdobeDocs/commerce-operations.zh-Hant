---
title: '[!UICONTROL Indexing]索引標籤'
description: 瞭解 [!DNL Observation for Adobe Commerce]的[!UICONTROL Indexing]標籤。
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# [!UICONTROL Indexing]索引標籤

**[!UICONTROL Indexing]**&#x200B;索引標籤會嘗試說明索引問題，並找出可能的原因。

## [!UICONTROL Core index invalidated]

![核心索引已失效](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

**[!UICONTROL Core index invalidated]**&#x200B;框架會檢視所選時間範圍內的索引失效。 如果索引與其他資源密集型[!DNL crons]同時發生，將會對網站資源造成大量負載。

* `%Catalog Product Rule indexer has been invalidated%`)，作為`catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`)，作為`catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`)，作為`catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`)，作為`category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`)，作為`customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`)，作為`design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`)，作為`product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`)，作為`product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`)，作為`product_price_idx_reset`
* `%Stock indexer has been invalidated%`)，作為`stock_idx_reset`
* `%Inventory indexer has been invalidated%`)，作為`inventory_idx_reset`
* `%Inventory indexer has been invalidated%`)，作為`inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`)，作為`sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![核心索引重新建置](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

**[!UICONTROL Core index rebuilds]**&#x200B;框架會檢視所選時間範圍內重建的核心索引。 以下是從記錄中剖析以指示索引重建完成的字串。

* `%Catalog Product Rule index has been rebuilt%`)，作為`catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`)，作為`catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`)，作為`catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`)，作為`category_products_idx`
* `%Customer Grid index has been rebuilt%`)，作為`customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`)，作為`design_config_grid_idx`
* `%Product Categories index has been rebuilt%`)，作為`product_categories_idx`
* `%Product EAV index has been rebuilt%`)，作為`product_eav_idx`
* `%Product Price index has been rebuilt%`)，作為`product_price_idx`
* `%Stock index has been rebuilt%`)，作為`stock_idx`
* `%Inventory index has been rebuilt successfully%`)，作為`inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`)，作為`prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`)，作為`sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![目錄搜尋索引資料表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

**[!UICONTROL catalogsearch index table(s)]**&#x200B;框架會跨選取的時間範圍檢視catalogsearch索引表格。 此查詢正在檢視針對資料表名稱中有`%catalogsearch%`的資料表的任何資料存放區作業的持續時間。

## [!UICONTROL product index table(s)]

![產品索引資料表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

**[!UICONTROL product index table(s)]**&#x200B;框架會跨選取的時間範圍檢視產品索引表格。 此查詢正在檢視針對資料表名稱中有`%product%`的資料表的任何資料存放區作業的持續時間。
