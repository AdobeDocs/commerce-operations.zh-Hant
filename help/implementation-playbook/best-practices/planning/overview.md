---
title: 實施規劃階段
description: 了解Adobe Commerce專案規劃階段的實作最佳實務。
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 規劃階段

規劃階段包括以下活動：

- 需求收集
- 建築設計
- 目錄設計
- 專案範圍
- 帳戶布建
- 使用者存取
- 擴充功能購買

以下各節包括規劃階段的最佳做法資訊。

## 需求收集

- **應用程式配置**
   - [設定網站、商店和商店檢視的最佳實務（雲端基礎架構）](sites-stores-store-views.md)
   - [如何防止和修正Adobe Commerce網站最常見的五個設定問題](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [快取最佳作法](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [全頁快取](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache記憶體大小](opcache-memory-size.md)
   - [報表設定](reporting-configuration.md)

- **資料庫配置**
   - [雲端部署的資料庫設定最佳作&#x200B;法](database-on-cloud.md)
   - [MySQL從連接配&#x200B;置](configure-mysql-slave-connection-on-cloud.md)
   - [MySQL觸發器用法](mysql-triggers-usage.md)

- **服務配置**
   - [設定Obmey](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [新建內容 — 設定通知通道](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis服務配置的最佳實&#x200B;務](redis-service-configuration.md)
   - [Realpath快取大小最佳實踐](realpath-cache-size.md)

## **建築設計**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [了解全域參考架構](../../../implementation-playbook/architecture/global-reference.md)

## **目錄設計**

以下主題說明設定Adobe Commerce目錄的效能最佳化最佳實務，包括類別數、產品有效SKU、產品變數、產品屬性和選項等的建議上限。

- [類別設定](category-limits.md)
- [產品設&#x200B;定](product-sku-limits.md)
- [產品變異配置](product-variations.md)
- [產品選項設定](product-options.md)
- [產品屬性設&#x200B;定](product-attributes-and-options.md)
- [產品清單的分頁設定](product-listing-pagination.md)

## **銷售與行銷**

- [產品購物車限制最佳實務&#x200B;](product-cart.md)
- [設定促銷活動的最佳實務](product-cart-promotions.md)

## **專案範圍**

- [合作夥伴升級](partner-escalation.md)

## **購買擴充功能**

- [在Adobe Commerce中使用協力廠商擴充功能的最佳作&#x200B;法](extensions.md)
