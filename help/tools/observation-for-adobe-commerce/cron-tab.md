---
title: 的 [!DNL Cron] 頁籤
description: 瞭解 [!DNL Cron] 頁籤 [!DNL Observation for Adobe Commerce]。
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 的 [!DNL Cron] 頁籤

此頁籤嘗試快速隔離問題和原因 [!DNL cron] 問題。

## [!UICONTROL Cron transaction duration in seconds]

![Cron事務持續時間（秒）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

的 **[!UICONTROL Cron transaction duration in seconds]** 幀顯示 [!DNL crons] 事務持續時間（秒）。 這將顯示運行時間較長的事務。 深入瞭解APM將顯示有關事務/操作可能正在運行的查詢的詳細資訊。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![按節點列出的MySQL非休眠線程](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

的 **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame按節點顯示所選時間範圍內的MySQL非休眠線程。

## [!UICONTROL SQL Trace count by path]

![按路徑的SQL跟蹤計數](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

的 **[!UICONTROL SQL Trace count by path]** frame按路徑查看MySQL跟蹤計數，這有助於在選定的時間範圍內跟蹤SQL陳述式。

## [!UICONTROL Cron database call]

![Cron資料庫調用](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

的 **[!UICONTROL Cron database call]** 框架查看 [!DNL crons] 在選定的時間段內調用資料庫。

## [!UICONTROL Cron schedule table locks]

![Cron計畫表鎖](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

的 **[!UICONTROL Cron schedule table locks]** 框看 [!DNL cron] 計畫選定時間段內的表鎖定。

## [!UICONTROL Cron schedule clean cron fired]

![Cron計畫表鎖](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

的 **[!UICONTROL Cron schedule clean cron fired]** 框架查看 [!DNL crons] 已在選定時間範圍內清理。 如果此框架中未顯示任何資料，則可能表示 [!DNL crons] 正確運行。 如果 [!DNL cron] 作業計畫未清除， [!DNL crons] 不會以最佳方式運行，運行可能需要更長時間。

## [!UICONTROL Cron schedule clean records details table]

![Cron計劃清除記錄詳細資訊表](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

的 **[!UICONTROL Cron schedule clean records details table]** 表提供了有關清除來自 `cron_schedule` 表。

## [!UICONTROL cron_schedule table updates]

![cron_schedule表更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

的 **[!UICONTROL cron_schedule table updates]** 框架查看 [!DNL cron] 計畫表在選定時間範圍內更新。 此表的刪除或更新活動頻繁，可能表明 [!DNL crons]。 還有， [!DNL crons] 運行並完成時更新此表，因此，如果此表上沒有活動且 [!DNL crons] 已配置，可能 [!DNL crons]。

## [!UICONTROL Datastore Operations Tables]

![資料儲存操作表](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

的 **[!UICONTROL Datastore Operations Tables]** 查看資料庫表操作，包括 `SELECT`。 `DELETE`, `UPDATE` 跨選定的時間段。 此框架顯示對資料庫表具有最高操作頻率的資料庫表。
