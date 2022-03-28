---
title: 概述 [!DNL Upgrade Compatibility Tool]
description: 瞭解 [!DNL Upgrade Compatibility Tool] 以及它如何幫助你完成Adobe Commerce計畫。
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# 概述 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

的 [!DNL Upgrade Compatibility Tool] 是一種命令行工具，它通過分析Adobe Commerce定制實例中安裝的所有模組和核心代碼來對照特定版本檢查該實例。 它返回一列重要問題、錯誤和警告，在升級到最新版本的Adobe Commerce之前必須解決這些問題。 它還會發現在嘗試升級到較新版本的Adobe Commerce之前，必須在代碼中修復的潛在問題。

的 [!DNL Upgrade Compatibility Tool] 允許您確定何時對自定義功能進行了核心代碼更改。 查看 [運行工具](../upgrade-compatibility-tool/run.md) 的子菜單。

它以Composer包的形式分發，每個版本都有Adobe Commerce版本。 查看 [開發人員](../upgrade-compatibility-tool/developer.md) 的子菜單。

請參閱 [安裝](../upgrade-compatibility-tool/install.md) 主題 [!DNL Upgrade Compatibility Tool]。

## 工作流

下圖顯示了運行 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 圖](../../assets/upgrade-guide/mvp-diagram-v3.png)

## 的 [!DNL Upgrade Compatibility Tool] 用例

以下用例描述了Adobe Commerce合作夥伴升級客戶端實例的典型過程：

1. 下載 [!DNL Upgrade Compatibility Tool] 包來自Adobe Commerce儲存庫(`https://repo.magento.com/`)。 查看 [下載 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 的子菜單。
1. 執行 [!DNL Upgrade Compatibility Tool] 在 [β](https://devdocs.magento.com/release/beta-program.html) 最新階段 [Adobe Commerce釋放](https://devdocs.magento.com/release/)。
1. 主命令是 `upgrade:check`。 此命令將分析實例並檢查實例中的錯誤、警告和嚴重問題。 要優化結果：

   - 添加選項 `--ignore-current-version-compatibility-issues` 忽略當前Adobe Commerce版本的所有已知嚴重問題、錯誤和警告。 僅顯示所需版本的結果。
   - 使用選項 `--min-issue-level` 來設定最小問題級別。 幫助僅排定升級中最重要問題的優先順序。 如果只要分析某個供應商、模組甚至目錄，也可以指定路徑。 查看 [運行工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) 的子菜單。

1. 為當前安裝的特定版本的Adobe Commerce生成香草實例。 查看 [貢獻者指南](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 的子菜單。 `instance` 命令生成香草安裝。

   >[!NOTE]
   >
   >Vanilla實例是指特定版本的指定版本標籤或分支的全新安裝。

1. 的 [!DNL Upgrade Compatibility Tool] 標識自定義的損壞區域。 軟體工程師能夠瞭解升級的複雜性並評估升級的工作量。 此資訊與利益相關方共用。
1. 將為升級定義預算和時間表。
1. 然後，軟體工程師可以處理所需的代碼修改來修復損壞的模組。
1. 的 [!DNL Upgrade Compatibility Tool] 可以執行以跟蹤升級進度。
1. 現在，所有檢查和工程部門都可以將代碼推送到分段環境，在該環境中，回歸test確認所有test都是綠色的，這樣，他們就可以在Adobe Commerce預發佈的同一天將最新的Adobe Commerce版本發佈到生產環境中。

   ![[!DNL Upgrade Compatibility Tool] 觀眾](../../assets/upgrade-guide/audience-uct-v3.png)

## 幫助改進 [!DNL Upgrade Compatibility Tool]

與 [!DNL Upgrade Compatibility Tool] 團隊，在工程Slack渠道與我們聯繫 [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F)。 我們希望聽取您的反饋、問題和建議，以幫助我們改進該工具。

的 [!DNL Upgrade Compatibility Tool] 使用我們 [編碼標準](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) 確保您的項目遵循Adobe Commerce的最佳實踐並幫助您改進和擴展 [!DNL Upgrade Compatibility Tool]。

請參閱 [貢獻](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  主題，以獲取有關參與此項目的詳細資訊。

## 資源

我們開發了以下資源來幫助您瞭解Adobe Commerce升級：

- [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [即將發佈的版本](https://devdocs.magento.com/release/)
- [社區資源](https://devdocs.magento.com/community/resources/resources.html) 的子菜單。
