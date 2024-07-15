---
title: 整合 [!DNL Site-Wide Analysis Tool]
description: 請依照下列步驟，從您Adobe Commerce專案的 [!DNL Site-Wide Analysis Tool] 儀表板擷取 [!DNL Upgrade Compatibility Tool] 報告。
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 整合[!DNL Site-Wide Analysis Tool]

[!DNL Site-Wide Analysis Tool]提供24小時全年無休的即時效能監控、報告和建議，以確保Adobe Commerce執行個體的安全性和可操作性。

[!DNL Upgrade Compatibility Tool]現在已與[!DNL Site-Wide Analysis Tool]整合，以便讓非技術人員能夠執行[!DNL Upgrade Compatibility Tool]並取得包含每個檔案的問題清單的[報告](../upgrade-compatibility-tool/reports.md)。

如需詳細資訊，請參閱[[!DNL Site-Wide Analysis Tool] 使用手冊](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html)。

## 從[!DNL Site-Wide Analysis Tool]執行[!DNL Upgrade Compatibility Tool]

導覽至專案的[!DNL Site-Wide Analysis Tool]儀表板，並找到[!DNL Upgrade Compatibility Tool] Widget。

![UCT SWAT Widget — 初始](../../assets/upgrade-guide/uct-swat-initial.png)

按一下&#x200B;**[!UICONTROL Run Upgrade Scan]**。 掃描可能需要一些時間，視專案大小而定。 旋轉圖表示掃描正在進行中。

![UCT SWAT Widget — 進行中](../../assets/upgrade-guide/uct-swat-progress.png)

掃描完成後，高階結果會顯示在Widget中。

![UCT SWAT WIDGET — 結果](../../assets/upgrade-guide/uct-swat-results.png)

按一下&#x200B;**[!UICONTROL Download Report]**&#x200B;以擷取[!DNL Upgrade Compatibility Tool] [HTML報告](../upgrade-compatibility-tool/reports.md#html-report)並檢閱詳細資料。


>[!NOTE]
>
> 透過[!DNL Site-Wide Analysis Tool]執行[!DNL Upgrade Compatibility Tool]可最佳化您的結果，並幫助您專注於目標升級的新問題與重要問題。 它會使用[`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results)選項，並一律顯示比較您專案版本與最新發行版本的結果。
