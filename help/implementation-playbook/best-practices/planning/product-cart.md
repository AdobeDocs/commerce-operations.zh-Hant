---
title: 產品購物車最佳實務
description: 了解如何限制購物車中的產品數量，以最佳化Adobe Commerce效能。
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 產品購物車管理的最佳實務

為獲得最佳效能，請使用下列准則來管理Adobe Commerce和Magento Open Source的購物車限制：

- 若為2.3.x - 2.4.2版，購物車最多可允許100種產品。
- 對於2.4.3版和更新版本，對銷售規則功能的增強將購物車上限增加至750。


對於2.3.x - 2.4.2版，根據購物車項目限制的預期效能為：

- 最多 **100** 購物車中的產品 — 產品可運作，在回應時間內達到效能目標。
- 最多 **300** 購物車中的產品 — 產品有效，但回應時間會增加到超過目標。
- 以上 **500** 購物車中的產品 — 購物車和結帳流程無法保證運作

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 減少購物車項目數

使用下列策略來管理購物車項目的數量

- 使用 [!UICONTROL Add Item by SKU] 功能。
- 僅新增載入項目清單所需的自訂邏輯和購物車自訂。

## 潛在績效影響

購物車中的產品數量超過建議的最大數量，可能會透過下列方式影響網站效能：

- 增加資料檢索操作、驗證購物車項目、檢查是否應用價格規則以及稅和總計計算的響應時間。
- 增加迷你圖演算的回應時間，包括轉譯購物車檢視、結帳流程和執行。
- 增加有迷你圖的所有網站頁面的載入時間。

## 其他資訊

- [設定產品選項](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [管理購物車](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
