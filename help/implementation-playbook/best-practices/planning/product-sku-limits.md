---
title: 產品限制最佳做法
description: 瞭解配置產品庫存單位(SKU)以最大化站點效能的最佳實踐。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 產品SKU配置的最佳實踐

為了最大限度地提高效能，建議有效的產品庫存保持單位(SKU)的最大數量為2.42億。 此有效產品SKU最大值計算為：

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

位置：

- N表示該類別的項數
- 客戶組包括共用目錄，因為它會建立附加的客戶組。

有效SKU的數量超過最大值會降低產品資料檢索速度，並增加完成管理面板操作或索引的時間。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 減少產品數量

使用以下策略減少產品(SKU)的數量：

- 最小化乘數 — 
   - 整合網站會降低乘數。 如果您有50,000個SKU、10個網站和10個客戶組，則SKU的有效數量為500萬。 刪除五個客戶組將有效SKU減少到250萬。
   - 使用定制定價的替代產品功能替換共用目錄和客戶組乘數。
   - 客戶組和共用目錄都用作商店中有效SKU數的乘數。
- 重構目錄 — 
   - 減少分配給類別的產品數。
   - 通過減少網站、客戶組、共用目錄、產品數量或可配置產品選項的數量來減少SKU的數量
- 通過使用定制選項而不是建立單獨的產品，提供更多產品變體。
- 考慮到有效SKU可能包括許多潛在的價格排列，因為每個商店或客戶組的價格可以不同地指定。
- 停用或刪除未使用的系統元件（如模組）。 (請參閱  [卸載模組](../../../installation/tutorials/uninstall-modules.md)。)
- 在外部平台管理系統(PMS)中管理產品。

## 其他資訊

- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [產品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [使用共用目錄](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- 雲基礎架構： [設定多個網站和商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 內部： [多個網站或商店](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce在雲基礎架構方面：儲存配置的最佳做法](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
