---
title: 消息隊列概述
description: 閱讀有關消息隊列框架及其如何與Adobe Commerce和Magento Open Source應用程式協作的資訊。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# 消息隊列概述

消息隊列框架(MQF)是允許 [模組](https://glossary.magento.com/module) 將消息發佈到隊列。 它還定義了非同步接收消息的用戶。 MQF使用 [兔MQ](http://www.rabbitmq.com) 作為消息代理，為消息的發送和接收提供了可擴展的平台。 它還包括用於儲存未傳送消息的機制。 RabbitMQ基於高級消息隊列協定(AMQP)0.9.1規範。

下圖說明了消息隊列框架：

![消息隊列框架](../../assets/configuration/mq-framework.png)

- A [發佈者](https://glossary.magento.com/publisher-subscriber-pattern) 是向Exchange發送消息的元件。 它知道要發佈到哪個交換機，以及它發送的消息的格式。

- 交換機從發佈者接收消息，並將其發送到隊列。 雖然RabbitMQ支援多種類型的交換，但Commerce只使用主題交換。 主題包括路由鍵，該路由鍵包含由點分隔的文本字串。 主題名稱的格式為 `string1.string2`:比如說， `customer.created` 或 `customer.sent.email`。

   代理允許您在設定轉發消息的規則時使用通配符。 可以使用星號(`*`)替換 _一個_ 字串或磅符號(`#`)替換0個或更多字串。 比如說， `customer.*` 過濾 `customer.create` 和 `customer.delete`，但 `customer.sent.email`。 但是 `customer.#` 過濾 `customer.create`。  `customer.delete`, `customer.sent.email`。

- 隊列是儲存消息的緩衝區。

- 消費者接收消息。 它知道要消耗的隊列。 它可以將消息的處理器映射到特定隊列。

也可以不使用RabbitMQ建立基本消息隊列系統。 在此系統中， MySQL [適配器](https://glossary.magento.com/adapter) 在資料庫中儲存消息。 三個資料庫表(`queue`。 `queue_message`, `queue_message_status`)管理消息隊列工作量。 Cron作業確保用戶能夠接收消息。 此解決方案的可擴充性不強。 應盡可能使用RabbitMQ。
