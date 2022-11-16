---
title: 消息隊列概述
description: 閱讀有關訊息佇列架構，以及其如何與Adobe Commerce和Magento Open Source應用程式搭配運作的資訊。
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# 消息隊列概述

消息隊列框架(MQF)是允許 [模組](https://glossary.magento.com/module) 將消息發佈到隊列。 它也會定義非同步接收訊息的使用者。 MQF使用 [[!DNL RabbitMQ]](https://www.rabbitmq.com) 作為消息代理，它為發送和接收消息提供了可擴展的平台。 它還包括用於儲存未傳送消息的機制。 [!DNL RabbitMQ] 基於高級消息隊列協定(AMQP)0.9.1規範。

下圖說明了消息隊列框架：

![消息隊列框架](../../assets/configuration/mq-framework.png)

- A [發佈者](https://glossary.magento.com/publisher-subscriber-pattern) 是將訊息傳送至exchange的元件。 它知道要發佈到哪個交換機，以及它發送的報文格式。

- Exchange接收來自發佈商的消息，並將其發送到隊列。 雖然 [!DNL RabbitMQ] 支援多種類型的交換，商務僅使用主題交換。 主題包含路由鍵，該鍵包含以點分隔的文本字串。 主題名稱的格式為 `string1.string2`:例如， `customer.created` 或 `customer.sent.email`.

   代理程式允許您在設定轉發報文的規則時使用通配符。 您可以使用星號(`*`)取代 _one_ 字串或井字型大小(`#`)來取代0或多個字串。 例如， `customer.*` 會過濾 `customer.create` 和 `customer.delete`，但不是 `customer.sent.email`. 不過 `customer.#` 會過濾 `customer.create`,  `customer.delete`，和 `customer.sent.email`.

- 隊列是儲存消息的緩衝區。

- 消費者會接收訊息。 它知道要使用哪個隊列。 它可以將消息的處理器映射到特定隊列。

也可以設定基本消息隊列系統，而無需使用 [!DNL RabbitMQ]. 在此系統中， MySQL [適配器](https://glossary.magento.com/adapter) 將消息儲存在資料庫中。 三個資料庫表(`queue`, `queue_message`，和 `queue_message_status`)管理消息隊列工作負載。 Cron工作可確保消費者能夠接收訊息。 此解決方案的可擴充性不強。 [!DNL RabbitMQ] 應盡可能使用。
