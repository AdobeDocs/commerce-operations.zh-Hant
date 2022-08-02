---
title: 克隆作業
description: 瞭解cron組並建立自定義cron作業。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# 克隆作業

這些主題討論如何設定自定義cron作業和（可選）自定義cron組。 如果您的Commerce擴展需要定期運行計畫任務，則可以使用這些主題來設定cron _工作_ （計畫任務）和（可選）cron _組_，它同時運行自定義任務。

如果使用Commerce提供的cron組，則不必定義自定義cron組；但是，如果您希望cron作業以其他計畫運行，或希望它們一起運行，則應定義cron組

Commerce應用程式提供以下cron組：

- `default`，包含大多數cron作業
- `index`，將刷新 [索引器](../cli/manage-indexers.md)
- `consumers`，運行消息隊列 [消費者](../cli/start-message-queues.md)
- 這些主題僅在Adobe Commerce提供
   - `staging`，運行 [與轉移相關](https://docs.magento.com/user-guide/cms/content-staging.html) 任務
   - `catalog_event`，運行目標和購物車規則的任務
