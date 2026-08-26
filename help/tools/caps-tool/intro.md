---
title: '[!DNL Adobe Commerce Patching Automation]'
description: 瞭解 [!DNL Adobe Commerce Patching Automation]、其用途、存取方法，以及自動修補的最佳實務
hide: true
source-git-commit: f70924d6f0d1777104c59f3f9e776360308abceb
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

[!DNL Adobe Commerce Patching Automation]工具可讓您在雲端環境中自動套用及回覆Adobe Commerce的修補程式。 它為Commerce專案管理員提供簡化的工作流程，以便套用及還原修補程式。 內建的驗證和健康狀態檢查可協助確保雲端環境保持穩定與安全。

本指南專為Adobe Commerce Cloud商家和合作夥伴所設計，他們想要簡化修補流程、降低修補程式相關問題的風險、改善環境的安全性和穩定性，以及自動化例行的修補程式作業。

## [!DNL Patching Automation]個主題

* **[如何存取](access.md)**
* **[工作流程總覽](workflow.md)**
* **[GitHub整合](github-integration.md)**
* **[最佳實務](best-practices.md)**
* **[疑難排解](troubleshooting.md)**

## 工具概覽

* **UI介面**
  * 針對特定專案和環境組合，即時顯示修補程式可用性和狀態
  * 顯示進度、錯誤和任何其他相關訊息的完整修補狀態資訊
  * [!UICONTROL Patch Management Dashboard]用於：
    * 檢視可用的修補程式
    * 使用一鍵式操作套用修補程式
    * 還原先前套用的修補程式
    * 監視修補程式操作狀態和結果

* **使用結構化工作流程的自動修補服務**
  * **初步檢查** — 驗證修補程式相容性和環境整備
  * **修補** — 在整合環境中自動套用或還原修補程式
  * **驗證** — 執行健康狀態檢查以確認應用程式已啟動，且其資料庫和快取連線可連線

* **安全功能**
  * 在應用程式之前驗證修補程式相容性
  * 先在暫時整合環境中套用修補程式（確認其成功部署並透過健康狀態檢查），然後再合併至您的目標環境，然後在部署後立即執行最終的健康狀態檢查
  * 將修補程式套用至`m2-hotfixes`資料夾，並在重新版本轉換期間自動移除

## 與Adobe Commerce Cloud的整合

[!DNL Patching Automation]與Adobe Commerce Cloud基礎架構完全整合，並與您現有的雲端環境無縫運作。 其運用雲端原生功能以獲得最佳效能、提供詳細的記錄與監控，以及與Adobe Commerce雲端支援工具整合。

## 教學課程影片

瞭解[!DNL Adobe Commerce Patching Automation]以及此工具如何協助使用者快速尋找及套用安全性修補程式。 下列影片說明如何透過「全網站分析工具」(SWAT)儀表板存取它、選擇您的專案和環境，以及按一下即可套用修補程式。

>[!VIDEO](https://video.tv.adobe.com/v/3476258/?captions=chi_hant&learn=on&enablevpops)

## 常見使用案例

* **安全性修補程式** — 快速套用重要安全性更新
* **修補復原** — 安全地還原透過服務套用的有問題的修補程式
* **安全性法規遵循** — 透過自動修補維護安全性標準
* **操作穩定性** — 確認應用程式啟動並在每次修補作業後通過健康狀態檢查
