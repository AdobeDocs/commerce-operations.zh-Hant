---
title: 產品限制最佳實務
description: 了解設定產品存貨保存件(SKU)以發揮網站效能的最佳實務。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 3a187ae8c066e56df0d7f4981d26ffb934f64576
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 產品SKU配置最佳實務

為了最大限度地提高效能，建議的有效產品庫存保持件數(SKU)的最大值為2.42億。 此有效產品最大值的計算方式為：

```text
Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups
```

超過最大有效SKU數量會減慢產品資料擷取速度，並增加完成管理作業的時間。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 減少產品數量

使用下列策略來減少產品(SKU)數量：

- 最小乘數 — 
   - 移動商店或網站會降低乘數。 如果您有50,000個SKU、10個網站和10個客戶群組，則SKU的有效數量為500萬。 移除五個客戶群組後，有效SKU會減少至250萬個。
   - 使用自訂定價的替代產品功能來取代共用目錄和客戶群組乘數。
- 重組目錄 — 
   - 減少分配給類別的產品數。
   - 減少商店、網站、客戶群組或產品數量，以減少SKU數量。
- 使用自訂選項提供更多產品變數，而非建立個別產品。
- 停用或移除未使用的系統元件，例如模組。 (請參閱  [卸載模組](../../../installation/tutorials/uninstall-modules.md).)
- 在外部平台管理系統(PMS)中管理產品。

## 其他資訊

- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [產品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- 雲基礎架構： [設定多個網站和商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 內部部署： [多個網站或商店](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce雲基礎架構：儲存配置最佳實務](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
