---
title: ' [!DNL Cron] 標籤'
description: 瞭解 [!DNL Observation for Adobe Commerce]的 [!DNL Cron] 標籤。
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# [!DNL Cron]索引標籤

此標籤嘗試快速隔離造成[!DNL cron]個問題的問題和原因。

## [!UICONTROL Cron transaction duration in seconds]

![Cron交易持續時間（以秒為單位）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

**[!UICONTROL Cron transaction duration in seconds]**&#x200B;框架會以秒為單位顯示[!DNL crons]交易持續時間。 這會顯示執行時間較長的交易。 深入探討APM將會顯示交易/作業可能執行之查詢的更多詳細資料。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL非睡眠的Threads （依節點）](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

**[!UICONTROL MySQL Non-Sleeping Threads by Node]**&#x200B;框架顯示所選時間範圍內節點的MySQL非睡眠執行緒。

## [!UICONTROL SQL Trace count by path]

依路徑](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)的![SQL追蹤計數

**[!UICONTROL SQL Trace count by path]**&#x200B;框架會依路徑檢視MySQL追蹤計數，這有助於在選取的時間範圍內追蹤SQL敘述句。

## [!UICONTROL Cron database call]

![Cron資料庫呼叫](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

**[!UICONTROL Cron database call]**&#x200B;框架會檢視在選取的時間範圍內呼叫資料庫的[!DNL crons]數目。

## [!UICONTROL Cron schedule table locks]

![Cron排程資料表鎖定](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

**[!UICONTROL Cron schedule table locks]**&#x200B;框架會檢視所選時間範圍內[!DNL cron]個排程資料表鎖定。

## [!UICONTROL Cron schedule clean cron fired]

![Cron排程資料表鎖定](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

**[!UICONTROL Cron schedule clean cron fired]**&#x200B;框架會檢視在選取的時間範圍內清理的[!DNL crons]數目。 如果此框架中未顯示任何資料，則可能表示[!DNL crons]正確執行時發生問題。 如果未清除[!DNL cron]工作排程，[!DNL crons]將不會以最佳方式執行，而且可能需要更長的時間才能執行。

## [!UICONTROL Cron schedule clean records details table]

![Cron排程清除記錄詳細資料表](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

**[!UICONTROL Cron schedule clean records details table]**&#x200B;表格提供工作的詳細資訊，以便在選取的時間範圍內從`cron_schedule`表格清除記錄。

## [!UICONTROL cron_schedule table updates]

![cron_schedule資料表更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

**[!UICONTROL cron_schedule table updates]**&#x200B;框架會檢視所選時間範圍內已排程資料表更新的[!DNL cron]個數目。 此資料表的刪除或更新活動頻繁可能表示[!DNL crons]有問題。 此外，[!DNL crons]會在表格執行並完成時更新此表格，因此如果此表格上沒有活動且已設定[!DNL crons]，則[!DNL crons]可能會發生問題。

## [!UICONTROL Datastore Operations Tables]

![資料存放區操作資料表](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]**&#x200B;在選取的時間範圍內檢視資料庫資料表作業，包括`SELECT`、`DELETE`和`UPDATE`。 此框架顯示對資料庫表格執行作業頻率最高的表格。
