---
title: 審計前期績效
description: 通過使用Web效能工具審核Adobe Commerce店面運營，確定並解決對站點效能產生負面影響的問題。
role: Admin, User, Developer
feature: Best Practices
feature-set: Commerce
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 前端效能的最佳做法

使用Web效能工具檢查您的Adobe Commerce商店的前端效能。
這些工具使用各種指標來提供強大的洞察力和建議，以改進您的線上商店的效能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 檢查前端效能

要檢查網站商店的前端效能，請執行以下操作：

1. 使用Web效能工具(如：

   - **[Google燈塔](https://web.dev/measure/)**— Lighthouse對效能、可訪問性、漸進式Web應用、SEO等進行審核。 有關不同方式運行燈塔的詳細資訊，請參閱 [燈塔概述](https://developer.chrome.com/docs/lighthouse/overview)。)
   - **[GooglePageSpeed Insights](https://pagespeed.web.dev/)**— PageSpeed Insights快速提供有關網頁效能下降原因的詳細報告以及有關如何修復它的建議。

1. 審查審計報告，並實施為改進儲存效能而提供的建議。

## 其他資訊

- [管理員用戶的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用CLI進行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開發人員索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
