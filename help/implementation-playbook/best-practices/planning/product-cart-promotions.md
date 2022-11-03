---
title: 設定促銷活動的最佳實務
description: 了解設定銷售規則和抵用券代碼以最佳化商務商店效能的最佳實務。
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 設定促銷活動的最佳實務

為獲得最佳效能，請遵循以下最佳實務，為購物車中的項目設定銷售和促銷活動：

- **銷售規則（購物車價格規則）** — 為所有網站配置不超過1000個購物車價格規則
   - 管理並移除未使用的規則。
   - 新增嚴格的規則條件（例如屬性或類別篩選），以獲得最有效的比對。
- **優惠券**—
   - 確認資料庫中的抵用券總數少於250,000。
   - 移除未使用和過期的抵用券。
   - 僅產生滿足促銷活動需求所需的抵用券數量。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 潛在績效影響

超過建議的購物車價格規則或抵用券數量上限，可能會透過下列方式影響網站效能：

- 增加產品新增至購物車時的回應時間。
- 增載入入和轉譯迷你圖的時間。
- 增加轉譯購物車頁面的時間。
- 增加演算 **總計** 封鎖。
- 套用抵用券可能需要超過2秒的時間。

## 其他資訊

- [了解行銷活動和促銷活動](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [購物車價格規則](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [教學課程：建立購物車價格規則](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [抵用券代碼](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce雲基礎架構：儲存配置最佳實務](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
