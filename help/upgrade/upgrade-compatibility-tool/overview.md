---
title: 概述 [!DNL Upgrade Compatibility Tool]
description: 瞭解 [!DNL Upgrade Compatibility Tool] 以及它如何幫助你完成Adobe Commerce計畫。
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# 指南概述

本指南適用於Adobe Commerce的管理員和軟體工程師。 它包括有關安裝 [!DNL Upgrade Compatibility Tool]，以及其配置和管理。 它假定對核心Commerce配置和功能有基本的瞭解。

## 概述 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

的 [!DNL Upgrade Compatibility Tool] 是一種命令行工具，它通過分析Adobe Commerce定制實例中安裝的所有模組和核心代碼來對照特定版本檢查該實例。 它返回一個重要問題、錯誤和警告的清單，在升級到更新版本的Adobe Commerce之前，必須解決這些問題。

請參閱 [運行工具](../upgrade-compatibility-tool/run.md) 的子菜單。

請參閱 [安裝](../upgrade-compatibility-tool/install.md) 第一步 [!DNL Upgrade Compatibility Tool]。

查看 [視頻教程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)瞭解有關 [!DNL Upgrade Compatibility Tool]。

### 工作流

下圖顯示了運行 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 圖](../../assets/upgrade-guide/uct-diagram-v5.png)

### 的 [!DNL Upgrade Compatibility Tool] 用例

以下用例描述了Adobe Commerce合作夥伴升級客戶端實例的典型過程：

1. 下載 [!DNL Upgrade Compatibility Tool] 包來自Adobe Commerce儲存庫(`https://repo.magento.com/`)。 查看 [下載 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 的子菜單。
1. 執行 [!DNL Upgrade Compatibility Tool] 在 [β](https://devdocs.magento.com/release/beta-program.html) 最新階段 [Adobe Commerce釋放](https://devdocs.magento.com/release/)。
1. 為當前安裝的特定版本的Adobe Commerce生成香草實例。 查看 [貢獻者指南](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 的子菜單。 `instance` 命令生成香草安裝。

   >[!NOTE]
   >
   >Vanilla實例是指特定版本的指定版本標籤或分支的全新安裝。

1. 的 [!DNL Upgrade Compatibility Tool] 確定將幫助軟體工程師瞭解複雜性並評估升級工作的升級問題。
1. 此資訊與利益相關方共用。
1. 將為升級定義預算和時間表。
1. 然後，軟體工程師可以處理所需的代碼修改來修復損壞的模組。
1. 的 [!DNL Upgrade Compatibility Tool] 可以執行以跟蹤升級進度。
1. 現在，所有檢查和工程部門都可以將代碼推送到分段環境，在該環境中，回歸test確認所有test都是綠色的，這樣，他們就可以在Adobe Commerce預發佈的同一天將最新的Adobe Commerce版本發佈到生產環境中。

   ![[!DNL Upgrade Compatibility Tool] 觀眾](../../assets/upgrade-guide/audience-uct-v3.png)

### 幫助改進 [!DNL Upgrade Compatibility Tool]

如果您需要資訊或有本指南未包括的問題，請使用以下資源：

與 [!DNL Upgrade Compatibility Tool] 團隊，在工程Slack渠道與我們聯繫 [#upgrade相容性工具](https://magentocommeng.slack.com/archives/C019Y143U9F)。 我們希望聽取您的反饋、問題和建議，以幫助我們改進該工具。

的 [!DNL Upgrade Compatibility Tool] 使用我們 [編碼標準](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) 確保您的項目遵循Adobe Commerce的最佳實踐並幫助您改進和擴展 [!DNL Upgrade Compatibility Tool]。

請參閱 [貢獻](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  主題，以瞭解有關提供編碼標準的詳細資訊。

### 資源

我們開發了以下資源來幫助您瞭解Adobe Commerce升級：

- [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [即將發佈的版本](https://devdocs.magento.com/release/)
- [社區資源](https://devdocs.magento.com/community/resources/resources.html) 的子菜單。
- [相關工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
