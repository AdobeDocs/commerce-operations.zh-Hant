---
title: 「 [!UICONTROL Cron] 頁籤
description: 瞭解 [!UICONTROL Cron] 頁籤 [!DNL Observation for Adobe Commerce]。
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 的 [!UICONTROL Cron] 頁籤

此頁籤旨在快速隔離故障問題和故障原因。

## [!UICONTROL Cron transaction duration in seconds]

![Cron事務持續時間（秒）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

的 **[!UICONTROL Cron transaction duration in seconds]** 幀顯示crons事務持續時間（秒）。 這將顯示運行時間較長的事務。 深入瞭解APM將顯示有關事務/操作可能正在運行的查詢的詳細資訊。

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![按節點列出的MySql非休眠線程](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

的 **[!UICONTROL MySql Non-Sleeping Threads by Node]** frame按節點顯示所選時間範圍內的MySql非休眠線程。

## [!UICONTROL SQL Trace count by path]

![按路徑的SQL跟蹤計數](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

的 **[!UICONTROL SQL Trace count by path]** frame按路徑查看MySql跟蹤計數，這有助於在選定的時間範圍內跟蹤SQL陳述式。

## [!UICONTROL Cron database call]

![Cron資料庫調用](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

的 **[!UICONTROL Cron database call]** frame查看在選定時間範圍內調用資料庫的cron數。

## [!UICONTROL Cron schedule table locks]

![Cron計畫表鎖](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

的 **[!UICONTROL Cron schedule table locks]** frame會查看cron計畫表鎖在選定時間範圍內。

## [!UICONTROL Cron schedule clean cron fired]

![Cron計畫表鎖](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

的 **[!UICONTROL Cron schedule clean cron fired]** frame查看選定時間範圍內清理的cron數。 如果此框架中未顯示任何資料，則可能表示Cron運行正確有問題。 如果未清除cron作業計畫，則cron不會以最佳方式運行，運行可能需要較長時間。

## [!UICONTROL Cron schedule clean records details table]

![Cron計劃清除記錄詳細資訊表](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

的 **[!UICONTROL Cron schedule clean records details table]** 表提供了有關清除來自 `cron_schedule` 表。

## [!UICONTROL cron_schedule table updates]

![cron_schedule表更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

的 **[!UICONTROL cron_schedule table updates]** frame查看所選時間範圍內cron計畫表更新的數量。 刪除或更新此表時活動頻繁，可能表示出現cron問題。 另外，crons在運行和完成時更新此表，因此，如果此表上沒有活動且配置了cron，則crons可能有問題。

## [!UICONTROL Datastore Operations Tables]

![資料儲存操作表](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

的 **[!UICONTROL Datastore Operations Tables]** 查看資料庫表操作，包括 `SELECT`。 `DELETE`, `UPDATE` 跨選定的時間段。 此框架顯示對資料庫表具有最高操作頻率的資料庫表。
