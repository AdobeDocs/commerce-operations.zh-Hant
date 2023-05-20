---
title: 整合 [!DNL Site-Wide Analysis Tool]
description: 按照以下步驟檢索 [!DNL Upgrade Compatibility Tool] 報告 [!DNL Site-Wide Analysis Tool] 你的Adobe Commerce項目的儀表板。
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 整合 [!DNL Site-Wide Analysis Tool]

的 [!DNL Site-Wide Analysis Tool] 提供24/7即時效能監控、報告和建議，以確保Adobe Commerce實例的安全性和可操作性。

的 [!DNL Upgrade Compatibility Tool] 現在與 [!DNL Site-Wide Analysis Tool] 為非技術人員提供管理 [!DNL Upgrade Compatibility Tool] 然後 [報告](../upgrade-compatibility-tool/reports.md) 包含每個檔案的問題清單。

查看 [[!DNL Site-Wide Analysis Tool] 使用手冊](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) 的子菜單。

## 運行 [!DNL Upgrade Compatibility Tool] 從 [!DNL Site-Wide Analysis Tool]

導航到 [!DNL Site-Wide Analysis Tool] 用於項目的儀表板並找到 [!DNL Upgrade Compatibility Tool] 小部件。

![UCT SWAT小部件 — 初始](../../assets/upgrade-guide/uct-swat-initial.png)

按一下 **[!UICONTROL Run Upgrade Scan]**。 根據項目大小，掃描可能需要一些時間。 掃描器指示掃描正在進行。

![UCT SWAT小部件 — 正在進行](../../assets/upgrade-guide/uct-swat-progress.png)

掃描完成後，高級結果將顯示在小部件中。

![UCT SWAT構件 — 結果](../../assets/upgrade-guide/uct-swat-results.png)

按一下 **[!UICONTROL Download Report]** 以檢索 [!DNL Upgrade Compatibility Tool] [HTML報告](../upgrade-compatibility-tool/reports.md#html-report) 並查看詳細資訊。


>[!NOTE]
>
> 運行 [!DNL Upgrade Compatibility Tool] 通過 [!DNL Site-Wide Analysis Tool] 優化結果，並幫助您專注於新問題和對目標升級至關重要的問題。 它使用 [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) 選項，並始終顯示將項目版本與最新版本進行比較的結果。
