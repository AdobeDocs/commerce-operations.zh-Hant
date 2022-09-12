---
title: 「 [!DNL Upgrade Compatibility Tool]"
description: 了解 [!DNL Upgrade Compatibility Tool] 以及如何協助您完成Adobe Commerce專案。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# 指南概述

{{commerce-only}}

本指南適用於Adobe Commerce的管理員和軟體工程師。 其中包含安裝 [!DNL Upgrade Compatibility Tool]，及其設定和管理。 此版本假設基本了解核心商務組態和功能。

## 概觀 [!DNL Upgrade Compatibility Tool]

此 [!DNL Upgrade Compatibility Tool] 是一種工具，可透過分析其中安裝的所有模組和核心程式碼，根據特定版本檢查Adobe Commerce自訂例項。 它會傳回重要問題、錯誤和警告的清單，在升級至較新版本的Adobe Commerce之前，必須解決這些問題。

## 使用 [!DNL Upgrade Compatibility Tool]

您可以使用 [!DNL Upgrade Compatibility Tool] 透過：

- 獨立 [命令行介面](../upgrade-compatibility-tool/run.md) 工具。
- 整合 [!DNL Upgrade Compatibility Tool] 和 [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 中的執行設定 [MagentoPHPStorm外掛程式](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## 工作流程

下圖顯示執行 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 圖表](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] 示範

觀看此影片以了解 [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 協助改善 [!DNL Upgrade Compatibility Tool]

如果您需要資訊或有本指南未涵蓋的問題，請使用下列資源：

連線至 [!DNL Upgrade Compatibility Tool] 團隊，請透過「工程Slack」管道與我們連絡 [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). 我們想聽聽您的意見、問題和建議，以協助我們改善此工具。

此 [!DNL Upgrade Compatibility Tool] 使用 [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/) 確保您的專案遵循Adobe Commerce最佳實務，並協助您改善和擴充 [!DNL Upgrade Compatibility Tool].

請參閱 [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) 主題，以取得關於貢獻編碼標準的詳細資訊。

## 資源

請參閱下列資源，協助您了解Adobe Commerce升級：

- 此 [升級指南](../overview.md) 提供一般Adobe Commerce或Magento Open Source升級歷程的概觀，以及遵循該歷程的最佳實務。
- 此 [近期發行](https://devdocs.magento.com/release/) 頁面提供已排程和即將發行的日期。
- 此 [社群資源](https://developer.adobe.com/commerce/contributor/community/) 頁面是用來開始討論或尋找更多資訊的位置。
- 檢查 [相關工具](../upgrade-compatibility-tool/related-tools.md) 頁面，取得典型升級歷程中的實用工具。
