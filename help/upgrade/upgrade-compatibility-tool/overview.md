---
title: 概述 [!DNL Upgrade Compatibility Tool]
description: 瞭解 [!DNL Upgrade Compatibility Tool] 以及它如何幫助你完成Adobe Commerce計畫。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# 指南概述

{{commerce-only}}

本指南適用於Adobe Commerce的管理員和軟體工程師。 它包括有關安裝 [!DNL Upgrade Compatibility Tool]，以及其配置和管理。 它假定對核心Commerce配置和功能有基本的瞭解。

## 概述 [!DNL Upgrade Compatibility Tool]

的 [!DNL Upgrade Compatibility Tool] 是一種工具，它通過分析Adobe Commerce定制實例中安裝的所有模組和核心代碼，來檢查特定版本的自定義實例。 它返回一個重要問題、錯誤和警告的清單，在升級到更新版本的Adobe Commerce之前，必須解決這些問題。

## 使用 [!DNL Upgrade Compatibility Tool]

您可以使用 [!DNL Upgrade Compatibility Tool] 通過：

- 作為獨立 [命令行介面](../upgrade-compatibility-tool/run.md) 工具欄。
- 整合 [!DNL Upgrade Compatibility Tool] 和 [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md)。
- 運行配置 [MagentoPHPStorm插件](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md)。

## 工作流

下圖顯示了運行 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 圖](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] 演示

觀看此視頻以瞭解 [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 幫助改進 [!DNL Upgrade Compatibility Tool]

如果您需要資訊或有本指南未包括的問題，請使用以下資源：

與 [!DNL Upgrade Compatibility Tool] 團隊，在工程Slack渠道與我們聯繫 [#upgrade相容性工具](https://magentocommeng.slack.com/archives/C019Y143U9F)。 我們希望聽取您的反饋、問題和建議，以幫助我們改進該工具。

的 [!DNL Upgrade Compatibility Tool] 使用我們 [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/) 確保您的項目遵循Adobe Commerce的最佳實踐並幫助您改進和擴展 [!DNL Upgrade Compatibility Tool]。

請參閱 [貢獻](https://developer.adobe.com/commerce/php/coding-standards/contributing/) 主題，以瞭解有關提供編碼標準的詳細資訊。

## 資源

查看以下資源，幫助您瞭解Adobe Commerce升級：

- 的 [升級指南](../overview.md) 概括介紹了Adobe Commerce或Magento Open Source的典型升級過程和遵循該過程的最佳做法。
- 的 [即將發佈](https://devdocs.magento.com/release/) 頁面提供計畫版本和即將發佈的日期。
- 的 [社區資源](https://developer.adobe.com/commerce/contributor/community/) 頁面可以啟動討論或查找更多資訊。
- 檢查 [相關工具](../upgrade-compatibility-tool/related-tools.md) 頁面，查看典型升級過程中的有用工具。
