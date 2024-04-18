---
title: 概述 [!DNL Upgrade Compatibility Tool]
description: 瞭解 [!DNL Upgrade Compatibility Tool] 以及可如何協助您進行Adobe Commerce專案。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 指南概述

{{commerce-only}}

本指南適用於Adobe Commerce的管理員和軟體工程師。 其中包含有關安裝的 [!DNL Upgrade Compatibility Tool]、以及其設定和管理。 它假定您對核心Commerce設定和功能有基本的瞭解。

## 概述 [!DNL Upgrade Compatibility Tool]

此 [!DNL Upgrade Compatibility Tool] 是一種透過分析安裝在特定版本中的所有模組和核心程式碼來檢查Adobe Commerce自訂執行個體的工具。 它會傳回在升級至較新版Adobe Commerce之前必須解決的嚴重問題、錯誤和警告清單。

## 使用 [!DNL Upgrade Compatibility Tool]

您可以使用 [!DNL Upgrade Compatibility Tool] 透過：

- 作為獨立 [命令列介面](../upgrade-compatibility-tool/run.md) 工具。 如需可用命令的完整清單，請參閱 [`bin/uct` 參考](/help/reference/uct.md).
- 整合 [!DNL Upgrade Compatibility Tool] 使用 [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 內的執行設定 [MagentoPHPStorm外掛程式](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## 工作流程

下圖顯示執行時可能發生的工作流程 [!DNL Upgrade Compatibility Tool]：

![[!DNL Upgrade Compatibility Tool] 圖表](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] 示範

觀看此影片以瞭解 [!DNL Upgrade Compatibility Tool]：

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 協助改善 [!DNL Upgrade Compatibility Tool]

如果您需要本指南未涵蓋的資訊或問題，請使用下列資源：

若要與 [!DNL Upgrade Compatibility Tool] 團隊，透過工程Slack頻道聯絡我們 [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). 我們希望聽到您的意見、問題和建議，以協助我們改進工具。

此 [!DNL Upgrade Compatibility Tool] 使用的規則定義於 [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/) 確保您的專案遵循Adobe Commerce最佳實務，並協助您改善和擴充 [!DNL Upgrade Compatibility Tool].

請參閱 [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) 主題，以取得協助撰寫程式碼標準的詳細資訊。

## 資源

請參閱下列資源，協助您瞭解Adobe Commerce升級：

- 此 [升級指南](../overview.md) 提供典型Adobe Commerce升級歷程的概觀，以及在此歷程中要遵循的最佳實務。
- 此 [即將發行的版本](https://devdocs.magento.com/release/) 頁面提供已排程和即將發行的日期。
- 此 [社群資源](https://developer.adobe.com/commerce/contributor/community/) 頁面是要放置以開始討論，或尋找更多資訊的位置。
- 檢查 [相關工具](../upgrade-compatibility-tool/related-tools.md) 頁面，瞭解一般升級歷程中的實用工具。
