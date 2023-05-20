---
title: 產品購物車最佳做法
description: 瞭解如何通過限制購物車中的產品數量來優化Adobe Commerce效能。
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 產品購物車管理的最佳做法

為獲得最佳效能，請使用以下准則管理Adobe Commerce和Magento Open Source的購物車限制：

- 對於2.3.x - 2.4.2版，在購物車中最多允許100種產品。
- 對於2.4.3版和更高版本，對銷售規則功能的增強將購物車最大數量增加到750。


對於2.3.x - 2.4.2版，基於購物車物料限制的預期效能是：

- 最多 **100** 購物車中的產品 — 產品工作正常，在響應時間內達到效能目標。
- 最多 **300** 購物車中的產品 — 產品工作正常，但響應時間會超過目標。
- 上 **500** 購物車中的產品 — 購物車和結帳流不保證有效

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 減少購物車物料數

使用以下策略管理購物車物料的數量

- 使用 [!UICONTROL Add Item by SKU] 的子菜單。
- 僅添加載入項目清單所需的自定義邏輯和購物車自定義。

## 潛在的效能影響

購物車中產品數量超過建議的最大數量可能會通過以下方式影響站點效能：

- 增加資料檢索操作、驗證購物車物料、檢查是否應用價格規則以及稅和總計計算的響應時間。
- 增加了微型圖案渲染的響應時間，包括繪製車車視圖、檢出流和執行。
- 為存在迷你圖的所有站點頁面增加載入時間。

## 其他資訊

- [配置產品選項](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [管理購物車](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
