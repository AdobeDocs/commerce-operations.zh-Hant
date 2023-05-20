---
title: 的 [!UICONTROL [!DNL RabbitMQ][ ]頁籤
description: 瞭解 [!UICONTROL [!DNL RabbitMQ]]頁籤 [!DNL Observation for Adobe Commerce]。
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 的 [!UICONTROL [!DNL RabbitMQ]] 頁籤

的 **[!UICONTROL [!DNL RabbitMQ]]** 頁籤中的資訊 [!DNL RabbitMQ] 信號。

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] 基礎架構事件](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

的 **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** 框架顯示涉及 [!DNL RabbitMQ] 所選時間範圍內發生的錯誤：

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) `node2_timeout_exceeded`
* `%401 Unauthorized%`) `401_unauth`
* `%401 Unauthorized%`) `401_unauth`
* `%Service restarted: rabbitmq-server%`) `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] 服務啟動/停止信號](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

此框顯示 [!DNL RabbitMQ] 在所選時間段內發生的服務啟動/停止信號：

* `%RabbitMQ is asked to stop...%`) `rabbitmq_stop`
* `%Starting RabbitMQ%`) `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] 錯誤](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

此框顯示 [!DNL RabbitMQ] 在選定時間段內發生的錯誤：

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` 如 `exit_timeout`
* `%client unexpectedly closed TCP connection%`) `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) `undef_exit`
* `%Connection attempt from disallowed node%`) `disallowed_node`
* `%closing AMQP connection%`) `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] 節點狀態](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] 按隊列顯示的消息高級摘要狀態](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

的 **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** 圖形顯示 [!DNL RabbitMQ] 為所選時間段排隊。

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] 消息詳細資訊摘要](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) `queue_err`
* `%authenticated and granted access to vhost%`) `auth`
* `%closing AMQP connection%`) `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] 隊列消耗MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

的 **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** 圖形顯示每個佔用的位元組數 [!DNL RabbitMQ] 在所選時間段內排隊。

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] 按隊列發佈的消息](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

的 **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** 圖形顯示每個佔用的位元組數 [!DNL RabbitMQ] 在所選時間段內排隊。

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] 按隊列發佈的消息吞吐量](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

的 **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** 圖形顯示每秒發佈的平均消息數 [!DNL RabbitMQ] 在所選時間段內排隊。

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] 按隊列列出的消息總吞吐量](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

的 **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** 圖形顯示每秒的平均消息總數 [!DNL RabbitMQ] 在所選時間段內排隊。

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] 按隊列顯示的使用者](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

的 **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** 圖表顯示每個用戶的平均總數 [!DNL RabbitMQ] 在所選時間段內排隊。
