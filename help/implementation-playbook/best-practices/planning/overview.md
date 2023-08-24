---
title: 實作規劃階段
description: 瞭解Adobe Commerce專案規劃階段的實作最佳實務。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 規劃階段

計畫階段包含下列作業：

- 需求收集
- 架構設計
- 目錄設計
- 專案範圍
- 帳戶布建
- 使用者存取權
- 擴充功能採購

下列章節包含規劃階段的最佳實務資訊。

## 需求收集

- **應用程式設定**
   - [設定網站、存放區和存放區檢視的最佳實務（雲端基礎結構）](sites-stores-store-views.md)
   - [如何預防並修正Adobe Commerce網站最常見的五個設定問題](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [快取的最佳實務](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [全頁快取](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache記憶體大小](opcache-memory-size.md)
   - [報告設定](reporting-configuration.md)

- **資料庫設定**
   - [雲端部署的資料庫設定最佳實務&#x200B;。](database-on-cloud.md)
   - [MySQL組態&#x200B;](mysql-configuration.md)

- **服務設定**
   - [設定Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic — 設定通知通道](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis服務組態的最佳作法&#x200B;。](redis-service-configuration.md)
   - [Realpath快取大小最佳實務](realpath-cache-size.md)

## **架構設計**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [瞭解全球參考架構](../../../implementation-playbook/architecture/global-reference.md)

## **目錄設計**

下列主題說明設定Adobe Commerce目錄的效能最佳化最佳實務，包括類別數、產品有效SKU、產品變化、產品屬性和選項等建議的最大值。

- [類別設定](catalog-management.md#category-limits)
- [產品組態&#x200B;](catalog-management.md#product-sku-limits)
- [產品變數設定](catalog-management.md#product-variations)
- [產品選項設定](catalog-management.md#product-options)
- [產品屬性設定&#x200B;](catalog-management.md#product-attributes)
- [產品清單的分頁設定](catalog-management.md#product-listing-pagination)

## **銷售與行銷**

- [有關產品購物車限制的最佳實務](catalog-management.md#cart-limits)
- [設定促銷活動的最佳作法](catalog-management.md#promotions)

## **專案範圍**

- [合作夥伴升級](partner-escalation.md)
- [付款儲存處理](payment-processing-storage.md)

## **購買延長期**

- [在Adobe Commerce中使用協力廠商擴充功能的最佳作法](extensions.md)
