---
title: 「 [!DNL Cron] 標籤」
description: 了解 [!DNL Cron] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: 38467ebd2ec29f9e1679182fb1ee7076d738664b
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 此 [!DNL Cron] 標籤

此標籤旨在快速隔離問題和原因 [!DNL cron] 問題。

## [!UICONTROL Cron transaction duration in seconds]

![Cron交易持續時間（以秒為單位）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

此 **[!UICONTROL Cron transaction duration in seconds]** 框顯示器 [!DNL crons] 交易期間（以秒為單位）。 這會顯示執行時間較長的交易。 深入探討APM後，將會顯示更多詳細資訊，說明交易/操作可能執行的查詢。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![按節點列出的MySQL非休眠線程](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

此 **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame按節點顯示所選時間範圍內的MySQL非休眠線程。

## [!UICONTROL SQL Trace count by path]

![按路徑的SQL跟蹤計數](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

此 **[!UICONTROL SQL Trace count by path]** frame會依路徑查看MySQL追蹤計數，這有助於在所選時間範圍內追蹤SQL陳述式。

## [!UICONTROL Cron database call]

![Cron資料庫呼叫](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

此 **[!UICONTROL Cron database call]** frame會查看 [!DNL crons] 在所選時間範圍內呼叫至資料庫。

## [!UICONTROL Cron schedule table locks]

![Cron調度表鎖定](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

此 **[!UICONTROL Cron schedule table locks]** 框架外觀 [!DNL cron] 計畫表鎖定在選定的時間範圍內。

## [!UICONTROL Cron schedule clean cron fired]

![Cron調度表鎖定](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

此 **[!UICONTROL Cron schedule clean cron fired]** frame會查看 [!DNL crons] 已在選取的時間範圍內清理。 如果此框架中未顯示任何資料，則可能表示 [!DNL crons] 正常運作。 若 [!DNL cron] 作業計畫未清除， [!DNL crons] 不會以最佳方式執行，且可能需要較長的時間才能執行。

## [!UICONTROL Cron schedule clean records details table]

![Cron計劃清除記錄詳細資訊表](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

此 **[!UICONTROL Cron schedule clean records details table]** 表格提供清除以下記錄的作業的詳細資訊： `cron_schedule` 表格。

## [!UICONTROL cron_schedule table updates]

![cron_schedule表更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

此 **[!UICONTROL cron_schedule table updates]** frame會查看 [!DNL cron] 已排程表格會在選取的時間範圍內更新。 此表格的刪除或更新活動高，可能表示 [!DNL crons]. 此外， [!DNL crons] 運行和完成時更新此表，因此，如果此表上沒有活動且 [!DNL crons] 已配置，可能 [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![資料儲存操作表](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

此 **[!UICONTROL Datastore Operations Tables]** 查看資料庫表操作，包括 `SELECT`, `DELETE`，和 `UPDATE` 的時間範圍。 此框架顯示對其運行頻率最高的資料庫表。
