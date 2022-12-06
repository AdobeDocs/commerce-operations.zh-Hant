---
title: 「 [!UICONTROL [!DNL RabbitMQ]] tab
description: 了解 [!UICONTROL [!DNL RabbitMQ]]標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: e59b8db21c449fcf91466df7482849a0454bfe3e
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 此 [!UICONTROL [!DNL RabbitMQ]] 標籤

此 **[!UICONTROL [!DNL RabbitMQ]]** 頁簽中的 [!DNL RabbitMQ] 訊號。

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] 基礎架構事件](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** 框架顯示涉及的基礎架構事件 [!DNL RabbitMQ] 在所選時間範圍內發生的事件：

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`)作為 `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`)作為 `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`)作為 `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`)作為 `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`)作為 `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`)作為 `node2_timeout_exceeded`
* `%401 Unauthorized%`)作為 `401_unauth`
* `%401 Unauthorized%`)作為 `401_unauth`
* `%Service restarted: rabbitmq-server%`)作為 `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`)作為 `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`)作為 `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`)作為 `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`)作為 `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`)作為 `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`)作為 `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`)作為 `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`)作為 `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`)作為 `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`)作為 `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] 服務啟動/停止信號](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

此框顯示 [!DNL RabbitMQ] 在所選時間範圍內發生的服務啟動/停止信號：

* `%RabbitMQ is asked to stop...%`)作為 `rabbitmq_stop`
* `%Starting RabbitMQ%`)作為 `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] 錯誤](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

此框顯示 [!DNL RabbitMQ] 在所選時間範圍內發生的錯誤：

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` as `exit_timeout`
* `%client unexpectedly closed TCP connection%`)作為 `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`)作為 `undef_exit`
* `%Connection attempt from disallowed node%`)作為 `disallowed_node`
* `%closing AMQP connection%`)作為 `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] 節點狀態](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`)作為 `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`)作為 `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`)作為 `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`)作為 `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`)作為 `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`)作為 `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] 按隊列的消息高級摘要狀態](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** 圖表顯示已發佈訊息的數量，依 [!DNL RabbitMQ] 排入所選時間範圍。

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] 消息詳細資訊摘要](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`)作為 `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`)作為 `queue_err`
* `%authenticated and granted access to vhost%`)作為 `auth`
* `%closing AMQP connection%`)作為 `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] 隊列消耗MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** 圖表顯示每個 [!DNL RabbitMQ] 排入佇列。

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] 按隊列發佈的消息](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** 圖表顯示每個 [!DNL RabbitMQ] 排入佇列。

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] 按隊列發佈的消息吞吐量](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** 圖形顯示每秒平均發佈的訊息數 [!DNL RabbitMQ] 排入佇列。

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] 按隊列列出的總消息吞吐量](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** 圖表顯示每秒平均報文總數，依 [!DNL RabbitMQ] 排入佇列。

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] 依佇列的消費者](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** 圖表顯示每個 [!DNL RabbitMQ] 排入佇列。
