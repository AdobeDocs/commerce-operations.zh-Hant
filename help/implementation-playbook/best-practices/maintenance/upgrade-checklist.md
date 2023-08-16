---
title: 升級檢查清單最佳實務
description: 瞭解如何建立並使用升級檢查清單來計畫您的Adobe Commerce和Magento Open Source升級策略。
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 升級檢查清單最佳實務

在與電子商務團隊進行年度和季度對話時，請使用此檢查清單。 許多公司都依據年度預算和藍圖開展工作。 在這些年度討論中，您必須談論平台的健康、方向及年度升級策略，以及平台如何配合業務的整體目標與KPI。 每季交談時，請確定您建立的年度計畫仍符合您目前的狀況，若未符合的話，請樞紐分析。 此升級計畫檢查清單的目標是協助您規劃和排程Adobe Commerce升級，以確保在年內成功升級流程。 此檢查清單旨在由以下對象用於年度計畫和季度審查：

- Director /管理IT
- eCommerce Manager
- 解決方案合作夥伴/顧問

>[!NOTE]
>
>有關成功升級的技術步驟的詳細說明，請參閱 [完成升級必要條件](../../../upgrade/prepare/prerequisites.md) 在我們的使用者檔案中。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 目標

▢檢閱目前的KPI，並視需要調整。

## 擴充功能與自訂

▢檢閱所有目前的擴充功能和自訂功能，並根據業務需求確定仍需要這些功能。

▢請考慮取代任何缺乏與Adobe Commerce版本同步之良好往績記錄的擴充功能。

## 團隊

▢確保您擁有適當的團隊，以及適當的Adobe Commerce認證和技能組合。

## 預算與時間

▢使用Adobe Commerce [發行排程](../../../release/schedule.md) 以提前規劃下一次升級，並做好準備。

▢根據預期需求，討論您認為將會採用哪個版本（完整或僅限安全性）。

▢預留預算與團隊容量以進行升級。

## 協力廠商整合

▢檢閱該年度目前的Adobe Commerce協力廠商整合及其維護期間，並考慮讓升級工作與維護排程保持一致。

## 範圍與部署規劃

▢立搶先存取活動

- 合作夥伴參與 [測試版](../../../release/beta.md)
- Beta版發行說明稽核。

▢議定預算、時間表、範圍。

▢執行 [升級相容性工具](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢請考慮使用升級來解決由下列識別的問題： [全網站分析工具](../../../tools/site-wide-analysis-tool/intro.md).

▢ Document相依性和任何所需的技術棧疊變更，例如PHP或Elastic Search版本。

▢透過Adobe Commerce認證收集專案團隊。

▢建立利害關係人溝通計畫。

▢在預期停機時規劃維護期間。

▢檢閱及核准測試策略；考慮使用Adobe Commerce [測試架構](https://developer.adobe.com/commerce/testing/) 或協力廠商自動化套裝。

▢確認所有擴充功能和自訂內容都相容。

▢檢閱並更新上市後行動手冊；若在升級期間或升級後發現問題時使用。

## 部署後

▢監視網站的問題 — 效能、訂單處理、分析等。

▢執行Adobe Commerce [安全性掃描](https://account.magento.com/scanner/dashboard/) 或其他協力廠商掃描並檢閱潛在的安全性弱點。

▢與所有利害關係人進行回顧性分析，記錄哪些環節進展順利、哪些環節未順利，以及如何加以改善。

▢透過所學的課程修改您的下一次升級計畫。
