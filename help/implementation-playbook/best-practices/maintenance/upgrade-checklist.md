---
title: 升級核對表最佳做法
description: 瞭解如何建立和使用升級核對表來規劃您的Adobe Commerce和Magento Open Source升級戰略。
role: Leader
feature: Best Practices
feature-set: Commerce
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 升級核對表最佳做法

在與電子商務團隊進行年度和季度對話時使用此核對表。 許多公司都從年度預算和路線圖著手。 在這些年度討論中，您必須談論您的平台在本年度的運行狀況、方向和升級戰略，以及它如何適應業務的總體目標和KPI。 在每季度對話中，確保您建立的年度計畫與當前情況保持一致，如果不符合，請轉向。 此升級計畫核對表的目標是幫助您規劃和安排Adobe Commerce升級，以確保在年內成功完成升級過程。 此核對表旨在供以下受眾用於年度規劃和季度審查：

- Director/ IT經理
- 電子商務經理
- 解決方案合作夥伴/顧問

>[!NOTE]
>
>有關成功升級的技術步驟的詳細說明，請參閱 [完成升級先決條件](../../../upgrade/prepare/prerequisites.md) 在用戶文檔中。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 目標

▢複查當前KPI並根據需要進行調整。

## 擴展和自定義

▢查看所有當前擴展和定制，並根據業務需求確保仍然需要這些擴展和定制。

▢考慮用Adobe Commerce版本替換沒有良好記錄保持最新的任何擴展。

## 團隊

▢確保您擁有具備適當Adobe Commerce認證和技能的適當團隊。

## 預算和時間安排

▢使用Adobe Commerce [發佈計畫](../../../release/schedule.md) 計畫下一次升級並提前準備。

▢討論您認為將根據預期需求採用的版本（完整版或僅安全版）。

▢為升級預留預算和團隊能力。

## 第三方整合

▢查看當前的Adobe Commerce第三方整合及其本年度的維護窗口，並考慮將升級工作與您的維護計畫相協調。

## 範圍和部署規劃

▢早期進入活動

- 合作夥伴參與 [β](../../../release/beta.md)
- 測試版發行說明審閱。

▢就預算、時間表、範圍達成一致。

▢運行 [升級相容性工具](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢考慮使用升級解決由 [站點範圍分析工具](../../../tools/site-wide-analysis-tool/intro.md)。

▢記錄相關性和所需的任何技術堆棧更改，如PHP或Elastic Search版本。

▢收集具有Adobe Commerce認證的項目團隊。

▢制定利益相關方溝通計畫。

▢計畫維護窗口（如果預計停機）。

▢審查並批准測試策略；考慮使用Adobe Commerce [test框架](https://developer.adobe.com/commerce/testing/) 或第三方自動化套件。

▢確認所有擴展和自定義都相容。

▢審查和更新發佈後的行動手冊；在升級期間或升級後發現問題時使用。

## 部署後

▢監視站點以瞭解問題 — 效能、訂單處理、分析等。

▢執行Adobe Commerce [安全掃描](https://account.magento.com/scanner/dashboard/) 或其他第三方掃描並檢查潛在的安全漏洞。

▢與所有利益相關方進行回顧，記錄哪些項目進展順利、哪些項目未取得進展以及如何改進。

▢根據經驗教訓修改下一次升級的計畫。
