---
title: 配置促銷的最佳做法
description: 瞭解配置銷售規則和優惠券代碼以優化Commerce商店效能的最佳做法。
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 配置促銷的最佳做法

為獲得最佳效能，請遵循以下最佳做法為購物車中的物料配置銷售和促銷：

- **銷售規則（購物車價格規則）** — 為所有網站配置不超過1000個購物車價格規則
   - 管理並刪除未使用的規則。
   - 添加嚴格的規則條件（如屬性或類別篩選器）以實現最有效的匹配。
- **優惠券**—
   - 驗證資料庫中的優惠券總數是否少於250,000。
   - 刪除未使用和過期的優惠券。
   - 僅生成滿足市場活動要求所需的優惠券數量。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 潛在的效能影響

超過建議的購物車價格規則或優惠券的最大數量會影響站點效能，其方式如下：

- 將產品添加到購物車時的響應時間增加。
- 載入和呈現迷你圖片的時間增加。
- 顯示購物車頁面的時間增加。
- 顯示 **合計** 在「簽出」頁面上阻止。
- 申請優惠券可能需要超過2秒。

## 其他資訊

- [瞭解市場營銷活動和促銷](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [購物車價格規則](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [教程：建立購物車價格規則](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [優惠券代碼](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce在雲基礎架構方面：儲存配置的最佳做法](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
