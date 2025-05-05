---
title: 稽核前端效能
description: 透過使用網站效能工具稽核Adobe Commerce店面作業，找出並解決對網站效能產生負面影響的問題。
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 1%

---

# 前端效能的最佳實務

使用網頁效能工具來檢查Adobe Commerce商店的前端效能。
這些工具會使用各種量度來提供強大的分析和建議，以改善線上商店的效能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 檢查前端效能

若要檢查網站商店的前端效能：

1. 使用Web效能工具稽核前端效能，例如：

   - **[Google Lighthouse](https://web.dev/measure/)**—Lighthouse具有效能、協助工具、漸進式網頁應用程式、SEO等的稽核。 如需執行Lighthouse的不同方式的詳細資訊，請參閱[Lighthouse概觀](https://developer.chrome.com/docs/lighthouse/overview)。
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)**—PageSpeed Insights會快速傳送關於網頁效能緩慢原因的詳細報告，以及修正建議。

1. 檢閱稽核報告並實作所提供的建議以改善商店效能。

## 其他資訊

- [管理員使用者的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- 使用CLI [索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=zh-Hant)
- [開發人員的索引概觀](https://developer.adobe.com/commerce/php/development/components/indexing/)
