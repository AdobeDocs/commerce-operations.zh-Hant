---
title: 「 [!UICONTROL [!DNL RabbitMQ]] tab
description: 了解 [!UICONTROL [!DNL RabbitMQ]]標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# 此 [!UICONTROL [!DNL RabbitMQ]] 標籤

此 **[!UICONTROL [!DNL RabbitMQ]]** 頁簽中的 [!DNL RabbitMQ] 訊號。

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] 基礎架構事件](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** 框架顯示涉及的基礎架構事件 [!DNL RabbitMQ] 在所選時間範圍內發生的事件：

* %響應 [錯誤] 適用於節點 [rabbit@host1]:意外的http響應（來自%&#39;）作為&#39;意外的resp_node1&#39;
* 「%Response [錯誤] 適用於節點 [rabbit@host2]:意外的http響應（來自%&#39;）作為&#39;意外的resp_node2&#39;
* 「%Response [錯誤] 適用於節點 [rabbit@host3]:意外的http響應（來自%&#39;）作為&#39;意外的resp_node3&#39;
* 「%Response [錯誤] 適用於節點 [rabbit@host3]:獲取&quot;http://localhost:15672/api/healthchecks/node/rabbit@host3&quot;:內容截止時間超過%&#39;)，作為「node3_timeout_exceeded」
* 「%Response [錯誤] 適用於節點 [rabbit@host1]:獲取&quot;http://localhost:15672/api/healthchecks/node/rabbit@host1&quot;:內容截止期限超過%」)，作為「node1_timeout_exceeded」
* 「%Response [錯誤] 適用於節點 [rabbit@host2]:獲取&quot;http://localhost:15672/api/healthchecks/node/rabbit@host2&quot;:內容截止時間超過%&#39;)，作為「node2_timeout_exceeded」
* 「%401未授權%」)作為「401_unauth」
* 「%401未授權%」)作為「401_unauth」
* %服務重新啟動：rabbitmq-server%&#39;)作為&#39;rmq_service_restart&#39;
* 「%Response [失敗] 適用於節點 [rabbit@host1]:nodedown%&#39;)作為&#39;rmq_node1_down&#39;
* 「%Response [失敗] 適用於節點 [rabbit@host2]:nodedown%&#39;)作為&#39;rmq_node2_down&#39;
* 「%Response [失敗] 適用於節點 [rabbit@host2]:nodedown%&#39;)作為&#39;rmq_node2_down&#39;
* 已修改「%實體：exchange/bindings.destination%&#39;)作為&#39;rmq_entity_modified&#39;
* 已修改「%實體：exchange/bindings.destination%&#39;)作為&#39;rmq_entity_modified&#39;
* 已修改「%實體：queue/exclusive%&#39;)作為&#39;rmq_entity_created_q_exclusive&quot;%已修改實體：queue/auto_delete%&#39;)作為&#39;rmq_entity_q_delete&#39;
* 已修改「%實體：queue/fulired%&#39;)作為&#39;rmq_entity_modified_q_fulired&#39;
* 已修改「%實體：version/management%&#39;)作為&#39;rmq_entity_modified_ver_mgt&#39;
* 已修改「%實體：version/management%&#39;)作為&#39;rmq_entity_modified_ver_mgt&#39;

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] 服務啟動/停止信號](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

此框顯示 [!DNL RabbitMQ] 在所選時間範圍內發生的服務啟動/停止信號：

* &#39;%[!DNL RabbitMQ] 被要求停止……%&#39;)作為&#39;rabbitmq_stop&#39;
* 「%正在啟動 [!DNL RabbitMQ]%&#39;)作為&#39;rabbitmq_start&#39;

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] 錯誤](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

此框顯示 [!DNL RabbitMQ] 在所選時間範圍內發生的錯誤：

* 「%exit，原因為{case_clause,timeout}和stacktrace {rabbit_mgmt_wm_healthchecks%&#39;}，為「exit_timeout」
* 「%client意外關閉TCP連接%」)作為「client_closed_tcp_conn」
* 「%在未定義的退出時，上下文shutdown_error%」中原因關閉)為「undef_exit」
* 「%從不允許的節點%」嘗試連接)為「不允許的節點」
* 「%closing AMQP connection%」)作為「rmq_err_amqp_conn」

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] 節點狀態](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* 「%rabbit on node rabbit@host1 down%」)作為「rmq_node1_down」
* 「%rabbit on node rabbit@host2 down%」)作為「rmq_node2_down」
* 「%rabbit on node rabbit@host3 down%」)作為「rmq_node3_down」
* 「%rabbit on node rabbit@host1 up%」)作為「rmq_node1_up」
* 「%rabbit on node rabbit@host2 up%」)作為「rmq_node2_up」
* 「%rabbit on node rabbit@host3 up%」)作為「rmq_node3_up」

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] 按隊列的消息高級摘要狀態](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** 圖表顯示已發佈訊息的數量，依 [!DNL RabbitMQ] 排入所選時間範圍。

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] 消息詳細資訊摘要](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* 「%report.ERROR:Cron Job consumers_runner出現錯誤：NOT_FOUND - no queue%&#39;)作為「queue_err」
* 「%report.ERROR:Cron Job consumers_runner出現錯誤：NOT_FOUND - no queue%&#39;)作為「queue_err」
* 「%已驗證且已授予對vhost%的訪問」)作為「auth」
* 「%close_conn」)

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
