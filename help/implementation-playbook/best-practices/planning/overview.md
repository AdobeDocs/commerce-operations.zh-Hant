---
title: 實作規劃階段
description: 瞭解Adobe Commerce專案規劃階段的實作最佳實務。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 1%

---

# 規劃階段

計畫階段包含下列作業：

- 架構設計
- 目錄設計
- 擴充功能採購
- 專案範圍
- 需求收集
- 銷售與行銷

下列章節包含規劃階段的最佳實務資訊。

## 需求收集

<table>
<thead>
  <tr>
    <th>最佳實務</th>
    <th>說明</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>應用程式設定</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">設定網站、商店和商店檢視</a></td>
    <td>設定網站、商店和商店檢視以最大化網站效能。</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">常見設定問題</a></td>
    <td>修正和防止Adobe Commerce網站最常見的五個設定問題。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">快取</a></td>
    <td>使用快取管理工具來改善網站的效能。</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">全頁快取</a></td>
    <td>瞭解在Adobe Commerce或Magento Open Source擴充功能中實作快取時，如何使用公開資料。</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache記憶體大小</a></td>
    <td>使用OPcache記憶體耗用的特定設定來避免效能降低。</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">設定報告</a></td>
    <td>如果您未使用報表模組，請將其移除，以最佳化網站效能。</td>
  </tr>
  <tr>
    <td colspan="2"><em>資料庫設定</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">設定雲端部署的資料庫</a></td>
    <td>設定資料庫和應用程式設定，以在雲端基礎結構專案上部署Adobe Commerce時提高效能。</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">設定MySQL</a></td>
    <td>瞭解MySQL觸發器和從屬連線如何影響網站效能以及如何有效使用它們。</td>
  </tr>
  <tr>
    <td colspan="2"><em>服務設定</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">設定Fastly</a></td>
    <td>在雲端基礎結構專案上為您的Adobe Commerce設定Fastly服務。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">設定New Relic的通知通道</a></td>
    <td>存取您的New Relic控制面板，並分析雲端基礎結構專案上Adobe Commerce的資料。</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">設定Redis</a></td>
    <td>使用適用於Adobe Commerce的延伸Redis快取實作，以改善快取效能。</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Realpath快取大小</a></td>
    <td>更新PHP 'readlpath'快取組態以使用建議的設定來最佳化效能。</td>
  </tr>
</tbody>
</table>

## 架構設計

| 最佳實務 | 說明 |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [全球參考架構(GRA)](../../architecture/global-reference/examples.md) | 瞭解組織GRA程式碼基底的常用方法。 |

## 目錄設計

| 最佳實務 | 說明 |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [類別設定](catalog-management.md#category-limits) | 設定產品類別以獲得最佳效能。 |
| [產品組態&#x200B;](catalog-management.md#product-sku-limits) | 設定產品SKU以獲得最佳效能。 |
| [產品變數設定](catalog-management.md#product-variations) | 設定產品變數以獲得最佳效能。 |
| [產品選項設定](catalog-management.md#product-options) | 設定產品選項以獲得最佳效能。 |
| [產品屬性設定&#x200B;](catalog-management.md#product-attributes) | 設定產品屬性以獲得最佳效能。 |
| [產品清單的分頁設定](catalog-management.md#product-listing-pagination) | 設定產品清單分頁以獲得最佳效能。 |

## 擴充功能

| 最佳實務 | 說明 |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [在Adobe Commerce中使用協力廠商擴充功能](extensions.md) | 瞭解如何避免第三方Adobe Commerce擴充功能造成的效能問題。 |

## 專案範圍

| 最佳實務 | 說明 |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [合作夥伴升級](partner-escalation.md) | 準備好與Adobe客戶團隊一起升級合作夥伴問題，或瞭解如何避免升級。 |
| [付款儲存處理](payment-processing-storage.md) | 安全地處理和儲存付款詳細資料。 |

## 銷售與行銷

| 最佳實務 | 說明 |
|------------------------------------------------------------|--------------------------------------------------------------|
| [產品購物車限制](catalog-management.md#cart-limits) | 管理購物車限制以獲得最佳效能。 |
| [設定促銷活動](catalog-management.md#promotions) | 設定購物車中專案的銷售和促銷活動。 |
