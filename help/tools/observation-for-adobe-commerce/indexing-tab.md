---
title: 「 [!UICONTROL Indexing] 標籤」
description: 了解 [!UICONTROL Indexing] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 此 [!UICONTROL Indexing] 標籤

此 **[!UICONTROL Indexing]** tab嘗試解釋索引問題並找出潛在原因。

## [!UICONTROL Core index invalidated]

![核心索引失效](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

此 **[!UICONTROL Core index invalidated]** frame會在選取的時間範圍內查看索引失效。 如果索引與其他資源密集型項目同時進行 [!DNL crons]，則會對網站資源造成大量負載。

* `%Catalog Product Rule indexer has been invalidated%`)作為 `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`)作為 `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`)作為 `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`)作為 `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`)作為 `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`)作為 `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`)作為 `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`)作為 `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`)作為 `product_price_idx_reset`
* `%Stock indexer has been invalidated%`)作為 `stock_idx_reset`
* `%Inventory indexer has been invalidated%`)作為 `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`)作為 `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`)作為 `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![核心索引重建](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

此 **[!UICONTROL Core index rebuilds]** frame會查看在選取的時間範圍內重新建置的核心索引。 以下是從日誌中剖析的字串，以指示索引重建完成。

* `%Catalog Product Rule index has been rebuilt%`)作為 `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`)作為 `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`)作為 `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`)作為 `category_products_idx`
* `%Customer Grid index has been rebuilt%`)作為 `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`)作為 `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`)作為 `product_categories_idx`
* `%Product EAV index has been rebuilt%`)作為 `product_eav_idx`
* `%Product Price index has been rebuilt%`)作為 `product_price_idx`
* `%Stock index has been rebuilt%`)作為 `stock_idx`
* `%Inventory index has been rebuilt successfully%`)作為 `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`)作為 `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`)作為 `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![目錄搜索索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

此 **[!UICONTROL catalogsearch index table(s)]** frame會查看所選時間範圍內的目錄搜尋索引表。 此查詢正在查看針對具有 `%catalogsearch%` 在表名中。

## [!UICONTROL product index table(s)]

![產品索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

此 **[!UICONTROL product index table(s)]** frame會查看所選時間範圍內的產品索引表。 此查詢正在查看針對具有 `%product%` 在表名中。
