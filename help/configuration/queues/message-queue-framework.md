---
title: 訊息佇列總覽
description: 閱讀訊息佇列架構及其如何與Adobe Commerce應用程式搭配運作。
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 6f15a24e650a7138bae6d0b40f230e6970a943b0
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# 訊息佇列總覽

Message Queue Framework (MQF)系統允許模組將訊息發佈至佇列。 它也會定義將非同步接收訊息的[消費者](consumers.md)。 MQF支援多個傳訊代理：

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** — 主要傳訊代理人，提供可擴充的平台來傳送及接收訊息。 它包含儲存未傳遞訊息的機制，並以進階訊息佇列通訊協定(AMQP) 0.9.1規格為基礎。
- **[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)** — 使用STOMP （簡單文字導向傳訊通訊協定）進行可靠且可擴充的傳訊的替代傳訊代理人。 在Adobe Commerce 2.4.6及更新版本中推出。

## RabbitMQ (AMQP)

下圖說明訊息佇列架構：

![訊息佇列架構](../../assets/configuration/mq-framework.png)

- 發佈者是將訊息傳送至交換的元件。 它知道要發佈到哪個交換以及它傳送的訊息格式。

- 交換會接收來自發佈者的訊息，並將訊息傳送至佇列。 雖然[!DNL RabbitMQ]支援多種型別的交換，但Commerce僅使用主題交換。 主題包含路由金鑰，其中包含以點分隔的文字字串。 主題名稱的格式是`string1.string2`：例如`customer.created`或`customer.sent.email`。

  代理程式可讓您在設定轉送訊息的規則時使用萬用字元。 您可以使用星號(`*`)取代&#x200B;_one_&#x200B;字串，或使用井字型大小(`#`)取代0或多個字串。 例如，`customer.*`會篩選`customer.create`和`customer.delete`，但不會篩選`customer.sent.email`。 但`customer.#`會篩選`customer.create`、`customer.delete`和`customer.sent.email`。

- 佇列是儲存訊息的緩衝區。

- 消費者會接收訊息。 它知道要使用哪個佇列。 它可以將訊息的處理器對應到特定佇列。

## Apache ActiveMQ Artemis (STOMP)

作為RabbitMQ的替代方案，Adobe Commerce也支援[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)作為使用簡單文字導向傳訊通訊協定(STOMP)的傳訊代理人。

>[!NOTE]
>
>ActiveMQ Artemis是在Adobe Commerce 2.4.6和更新版本中引入。

下圖說明具有ActiveMQ Artemis的STOMP架構：

![STOMP架構](../../assets/configuration/stomp-framework.png)

### STOMP Framework元件

- **發佈者**&#x200B;是將訊息傳送至目的地（佇列或主題）的元件。 它會知道要發佈到的目的地以及它傳送的訊息格式。

- STOMP中的&#x200B;**目的地**&#x200B;提供與AMQP中的交換類似的角色，接收來自發行者的郵件並將它們路由傳送。 STOMP使用直接目的地位址，並以點為分層的命名模式：例如`customer.created`或`inventory.updated`。

  Adobe Commerce對STOMP目的地使用&#x200B;**ANYCAST**&#x200B;定址模式，提供點對點訊息傳送。 在ANYCAST模式中，訊息僅會從可用的取用者集區傳送給一個取用者，以啟用多個取用者執行個體的負載平衡和工作分配。

- **佇列**&#x200B;是儲存訊息的緩衝區。 若使用ANYCAST定址，佇列可確保訊息僅傳送給一個消費者，即使有多個消費者連線到同一個目的地。

- **消費者**&#x200B;接收來自目的地的訊息。 它會知道要訂閱哪個目的地，並可以使用不同的確認模式（自動、使用者端或個人使用者端）處理訊息。

## MySQL配接器（備援）

您也可以設定基本訊息佇列系統，而不需要使用外部訊息代理人。 在此系統中，MySQL配接器會將訊息儲存在資料庫中。 三個資料庫表格（`queue`、`queue_message`和`queue_message_status`）管理訊息佇列工作負載。 Cron工作可確保消費者能夠接收訊息。 此解決方案的可擴充性不是很強。 應該儘可能將外部訊息代理（如[!DNL RabbitMQ]或Apache ActiveMQ Artemis）用於生產環境。

## 相關資訊

有關安裝和設定指示：

- [安裝及設定RabbitMQ](../../installation/prerequisites/rabbitmq.md)
- [安裝及設定ActiveMQ Artemis](../../installation/prerequisites/activemq.md)
- [管理訊息佇列](manage-message-queues.md)
- [訊息佇列取用者](consumers.md)
