---
title: 「 [!UICONTROL Indexing] 頁籤
description: 瞭解 [!UICONTROL Indexing] 頁籤 [!DNL Observation for Adobe Commerce]。
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 的 [!UICONTROL Indexing] 頁籤

的 **[!UICONTROL Indexing]** 頁籤嘗試解釋索引問題並確定潛在原因。

## [!UICONTROL Core index invalidated]

![核心指數失效](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

的 **[!UICONTROL Core index invalidated]** 框架查看所選時段內的索引無效。 如果索引與其他資源密集型克隆同時進行，則會給站點資源帶來沈重負載。

* 「%目錄產品規則索引器已失效%」)作為「catalog_product_rule_idx_reset」
* 「%目錄規則產品索引器已失效%」)，作為「catalog_rule_product_idx_reset」
* 「%目錄搜索索引器已失效%」)作為「catalog_search_idx_reset」
* 「%Category Products索引器已失效%」)作為「category_products_idx_reset」
* 「%Customer Grid索引器已失效%」)作為「customer_grid_idx_reset」
* 「%Design Config Grid索引器已失效%」)作為「design_config_grid_idx_
* 「%Product Categories索引器已失效%」)作為「product_categories_idx_reset」
* 「%Product EAV索引器已失效%」)作為「product_eav_idx_reset」
* 「%Product Price索引器已失效%」)作為「product_price_idx_reset」
* 「%Stock索引器已失效%」)作為「stock_idx_reset」
* 「%Inventory索引器已失效%」)作為「inventory_idx_reset」
* 「%Inventory索引器已失效%」)作為「inventory_idx_reset」
* 「%Sales Rule索引器已失效%」)作為「sales_rule_idx_reset」

## [!UICONTROL Core index rebuilds]

![核心索引重建](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

的 **[!UICONTROL Core index rebuilds]** frame查看所選時間範圍內的核心索引重建。 下面是從日誌中分析的字串，以指示索引重建完成。

* 「%目錄產品規則索引已重建%」)作為「catalog_product_rule_idx」
* 「%目錄規則產品索引已重建%」)作為「catalog_rule_product_idx」
* 「%目錄搜索索引已重建%」)為「catalog_search_idx」
* 「%Category Products索引已成功重建%」)，作為「category_products_idx」
* 「%Customer網格索引已重建%」)作為「customer_grid_idx」
* 「%Design Config Grid索引已重建%」)為「design_config_grid_idx」
* 「%Product Categories索引已重建%」)為「product_categories_idx」
* 「%Product EAV索引已重建%」)作為「product_eav_idx」
* 「%產品價格指數已重建%」)作為「product_price_idx」
* 「%Stock Index已被重建%」)，作為「stock_idx」
* 「%Inventory索引已成功重建%」)作為「inventory_idx」
* %Product/Target Rule索引已成功重建%&#39;)為「prod_target_rule_idx」
* 「%Sales Rule索引已成功重建%」)作為「sales_rule_idx」


## [!UICONTROL catalogsearch index table(s)]

![目錄搜索索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

的 **[!UICONTROL catalogsearch index table(s)]** frame查看所選時間範圍內的catalogsearch索引表。 此查詢正在查看對表名中「%catalogsearch%」的表執行任何資料儲存操作的持續時間。

## [!UICONTROL product index table(s)]

![產品索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

的 **[!UICONTROL product index table(s)]** frame會查看所選時段內的產品索引表。 此查詢正在查看對表名中「%product%」的表執行任何資料儲存操作的持續時間。
