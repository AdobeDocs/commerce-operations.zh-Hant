---
title: ' [!DNL Upgrade Compatibility Tool]的總覽'
description: 瞭解 [!DNL Upgrade Compatibility Tool] 以及它如何協助您進行Adobe Commerce專案。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 指南概述

{{commerce-only}}

本指南適用於Adobe Commerce的管理員和軟體工程師。 其中包含安裝[!DNL Upgrade Compatibility Tool]及其組態與管理的詳細資訊。 它假定您對核心Commerce設定和功能有基本的瞭解。

## [!DNL Upgrade Compatibility Tool]的總覽

[!DNL Upgrade Compatibility Tool]是一種工具，可透過分析安裝在其中的所有模組和核心程式碼，針對特定版本檢查Adobe Commerce自訂執行個體。 它會傳回在升級至較新版Adobe Commerce之前必須解決的嚴重問題、錯誤和警告清單。

## 使用[!DNL Upgrade Compatibility Tool]

您可以透過以下方式使用[!DNL Upgrade Compatibility Tool]：

- 作為獨立[命令列介面](../upgrade-compatibility-tool/run.md)工具。 如需可用命令的完整清單，請參閱[`bin/uct`參考](../../tools/reference/uct.md)。
- 整合[!DNL Upgrade Compatibility Tool]與[[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md)。
- [Magento PHPStorm外掛程式](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md)中的執行組態。

## 工作流程

下圖顯示執行[!DNL Upgrade Compatibility Tool]時可能的工作流程：

![[!DNL Upgrade Compatibility Tool]圖表](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool]展示

觀看此影片以瞭解[!DNL Upgrade Compatibility Tool]：

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 協助改善[!DNL Upgrade Compatibility Tool]

如果您需要本指南未涵蓋的資訊或問題，請使用下列資源：

若要與[!DNL Upgrade Compatibility Tool]團隊連線，請透過工程Slack管道[#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F)聯絡我們。 我們希望聽到您的意見、問題和建議，以協助我們改進工具。

[!DNL Upgrade Compatibility Tool]使用我們[編碼標準](https://developer.adobe.com/commerce/php/coding-standards/)中定義的規則，以確保您的專案遵循Adobe Commerce最佳實務，並協助您改善及擴充[!DNL Upgrade Compatibility Tool]。

請參考[Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/)主題，以取得有關協助撰寫程式碼標準的更多資訊。

## 資源

請參閱下列資源，協助您瞭解Adobe Commerce升級：

- [升級指南](../overview.md)提供典型Adobe Commerce升級歷程的概觀，以及此歷程中要遵循的最佳實務。
- [即將發行版本](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule)頁面提供已排程和即將發行的日期。
- [社群資源](https://developer.adobe.com/commerce/contributor/community/)頁面將放置以開始討論，或尋找更多資訊。
- 請檢視[相關工具](../upgrade-compatibility-tool/related-tools.md)頁面，瞭解一般升級歷程中的實用工具。
