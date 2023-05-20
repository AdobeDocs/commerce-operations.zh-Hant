---
title: 消息隊列概述
description: 閱讀有關消息隊列框架及其如何與Adobe Commerce和Magento Open Source應用程式協作的資訊。
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 消息隊列概述

消息隊列框架(MQF)是允許模組將消息發佈到隊列的系統。 它還定義了 [消費者](consumers.md) 非同步接收消息。 MQF使用 [[!DNL RabbitMQ]](https://www.rabbitmq.com) 作為消息代理，為消息的發送和接收提供了可擴展的平台。 它還包括用於儲存未傳送消息的機制。 [!DNL RabbitMQ] 基於高級消息隊列協定(AMQP)0.9.1規範。

下圖說明了消息隊列框架：

![消息隊列框架](../../assets/configuration/mq-framework.png)

- 發佈者是向交換機發送消息的元件。 它知道要發佈到哪個交換機，以及它發送的消息的格式。

- 交換機從發佈者接收消息，並將其發送到隊列。 儘管 [!DNL RabbitMQ] 支援多種交流類型，僅使用主題交流。 主題包括路由鍵，該路由鍵包含由點分隔的文本字串。 主題名稱的格式為 `string1.string2`:比如說， `customer.created` 或 `customer.sent.email`。

   代理允許您在設定轉發消息的規則時使用通配符。 可以使用星號(`*`)替換 _一個_ 字串或磅符號(`#`)替換0個或更多字串。 比如說， `customer.*` 過濾 `customer.create` 和 `customer.delete`，但 `customer.sent.email`。 但是 `customer.#` 過濾 `customer.create`。  `customer.delete`, `customer.sent.email`。

- 隊列是儲存消息的緩衝區。

- 消費者接收消息。 它知道要消耗的隊列。 它可以將消息的處理器映射到特定隊列。

也可以不使用 [!DNL RabbitMQ]。 在此系統中， MySQL適配器將消息儲存在資料庫中。 三個資料庫表(`queue`。 `queue_message`, `queue_message_status`)管理消息隊列工作量。 Cron作業確保用戶能夠接收消息。 此解決方案的可擴充性不強。 [!DNL RabbitMQ] 應盡可能使用。
