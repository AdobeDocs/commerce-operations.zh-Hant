---
title: 實施規劃階段
description: 瞭解Adobe Commerce項目規劃階段實施最佳做法。
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 規劃階段

計畫階段包括以下活動：

- 要求收集
- 建築設計
- 目錄設計
- 項目範圍
- 帳戶設定
- 用戶訪問
- 延期採購

以下各節包括規劃階段的最佳做法資訊。

## 要求收集

- **應用程式配置**
   - [配置站點、儲存和儲存視圖（雲基礎架構）的最佳實踐](sites-stores-store-views.md)
   - [如何防止和修復Adobe Commerce站點最常見的五個配置問題](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [快取的最佳做法](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [全頁快取](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache記憶體大小](opcache-memory-size.md)
   - [報告配置](reporting-configuration.md)

- **資料庫配置**
   - [用於雲部署的資料庫配置最佳做&#x200B;法](database-on-cloud.md)
   - [MySQL從連接配&#x200B;置](configure-mysql-slave-connection-on-cloud.md)
   - [MySQL觸發器用法](mysql-triggers-usage.md)

- **服務配置**
   - [設定Repost](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic — 配置通知通道](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis服務配置的最佳做法&#x200B;](redis-service-configuration.md)
   - [Realpath快取大小最佳實踐](realpath-cache-size.md)

## **建築設計**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [瞭解全局參考體系結構](../../../implementation-playbook/architecture/global-reference.md)

## **目錄設計**

以下主題介紹配置Adobe Commerce目錄的效能優化最佳實踐，包括建議的類別數、產品有效SKU、產品變體、產品屬性和選項的最大值，等等。

- [類別配置](category-limits.md)
- [產品配&#x200B;置](product-sku-limits.md)
- [產品變體配置](product-variations.md)
- [產品選項配置](product-options.md)
- [產品屬性配&#x200B;置](product-attributes-and-options.md)
- [產品清單的分頁配置](product-listing-pagination.md)

## **銷售和市場營銷**

- [針對產品購物車限制的最佳做法](product-cart.md)
- [配置促銷的最佳做法](product-cart-promotions.md)

## **項目範圍**

- [合作夥伴升級](partner-escalation.md)
- [付款儲存處理](payment-processing-storage.md)

## **採購擴展**

- [在Adobe Commerce使用第三方擴展的最佳做法](extensions.md)
