---
title: 升級檢查清單最佳實務
description: 了解如何建立和使用升級檢查清單，以規劃您的Adobe Commerce和Magento Open Source升級策略。
role: Leader
feature: Best Practices
feature-set: Commerce
source-git-commit: 644970b350c7591896f7c00d4c94661c76495c73
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 升級檢查清單最佳實務

在與電子商務團隊進行年度和季度對話時使用此檢查清單。 許多公司從年度預算和路線圖中開展工作。 在這些年度討論中，您必須談一談您平台在本年度的健康狀況、方向和升級策略，以及該策略如何與業務的整體目標和KPI相符。 在每季的對話中，確保您建立的年度計畫與當前情況保持一致，如果不符合，則進行資料透視。 此升級計畫檢查清單的目標是協助您規劃及排程Adobe Commerce升級，以確保年內能順利升級。 此檢查清單旨在供下列受眾用於年度規劃和季度審核：

- Director / IT經理
- 電子商務經理
- 解決方案合作夥伴/顧問

>[!NOTE]
>
>有關成功升級的技術步驟的詳細說明，請參閱 [完整升級必要條件](../../../upgrade/prepare/prerequisites.md) 在我們的使用者檔案中。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 目標

▢檢閱目前的KPI，並視需要進行調整。

## 擴充功能與自訂

▢檢閱所有目前的擴充功能和自訂項目，並根據業務需求確定仍需要這些項目。

▢請考慮以Adobe Commerce版本取代任何沒有良好記錄可保持最新的擴充功能。

## 團隊

▢透過適當的Adobe Commerce認證和技能，確保您擁有合適的團隊。

## 預算與時間

▢使用Adobe Commerce [發行排程](../../../release/schedule.md) 計畫下次升級並提前準備。

▢根據預期需求，討論您將採用的版本（完整版或僅限安全版）。

▢為升級預留預算和團隊容量。

## 協力廠商整合

▢查看目前的Adobe Commerce協力廠商整合及其全年維護期間，並考慮將升級工作與您的維護排程一致。

## 範圍和部署規劃

▢搶先訪問活動

- 合作夥伴參與 [Beta](../../../release/beta-program.md)
- 測試版發行說明審核。

▢就預算、時間表、範圍達成一致。

▢運行 [升級相容性工具](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢請考慮使用升級解決 [網站範圍分析工具](../../../tools/site-wide-analysis-tool/intro.md).

▢記錄相依性和需要的任何技術堆棧更改，如PHP或Elastic Search版本。

▢收集具備Adobe Commerce認證的專案團隊。

▢建立利益相關方溝通計畫。

▢如果預期停機，則計畫維護窗口。

▢審核並批准測試策略；考慮使用Adobe Commerce [測試框架](https://developer.adobe.com/commerce/testing/) 或協力廠商自動化套裝。

▢確認所有擴充功能和自訂功能都相容。

▢審查和更新發佈後的行動手冊；以在升級期間或之後發現問題時使用。

## 部署後

▢監視網站以了解問題 — 效能、訂單處理、分析等。

▢執行Adobe Commerce [安全掃描](https://account.magento.com/scanner/dashboard/) 或其他協力廠商掃描並檢閱潛在的安全漏洞。

▢與所有利益相關方進行回顧，記錄哪些項目進展順利、哪些項目未進展，以及如何改進。

▢根據經驗教訓修改您的下一次升級計畫。
