---
title: Cron工作
description: 瞭解cron群組和建立自訂cron工作。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron工作

這些主題討論如何設定自訂cron工作以及可選的自訂cron群組。 如果您的Commerce擴充功能需要定期執行排程工作，您可以使用這些主題來設定cron _工作_ （排程工作），以及選擇性地同時執行自訂工作的cron _群組_。

如果您使用Commerce提供的cron群組，則不需要定義自訂cron群組；但是，如果您希望cron工作以不同的排程執行，或希望所有工作一起執行，則應該定義cron群組

Commerce應用程式提供下列cron群組：

- 包含大多數cron工作的`default`
- `index`，它會重新整理[索引子](../cli/manage-indexers.md)
- `consumers`，執行訊息佇列[消費者](../cli/start-message-queues.md)
- 這些主題僅適用於Adobe Commerce
   - `staging`，執行[與暫存相關的](https://docs.magento.com/user-guide/cms/content-staging.html)工作
   - `catalog_event`，執行目標與購物車規則的工作
