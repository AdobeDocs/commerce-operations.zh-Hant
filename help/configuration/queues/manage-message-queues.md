---
title: 管理消息隊列
description: 了解如何從Adobe Commerce的命令列管理訊息佇列。
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: caca8df48c498977f830082ef27d9afb6220ae92
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 管理消息隊列

您可以使用cron作業或外部進程管理器從命令行管理消息隊列，以確保消費者正在檢索消息。

## 流程管理

Cron作業是重新啟動消費者的預設機制。 由啟動的流程 `cron` 使用指定的消息數，然後終止。 重新執行 `cron` 重新啟動消費者。

下列範例顯示 `crontab` 運行使用者的配置：

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>檢查消息隊列的頻率取決於您的業務邏輯和可用的系統資源。 一般而言，您可能會想要檢查新客戶，並比更頻繁地傳送歡迎電子郵件，而不是更耗用資源的程式，例如更新目錄。 您應定義 `cron` 根據您的業務需求進行排程。
>
>您可在群組的「管理員存放區>設定>設定>進階>系統>開啟」設定選項中進行設定：消費者。
>
>請參閱 [設定並執行cron](../cli/configure-cron-jobs.md) 有關使用的詳細資訊 `cron` 和商務。

您也可以使用流程管理器，例如 [主管](http://supervisord.org/index.html) 監視進程的狀態。 管理器可以根據需要使用命令行重新啟動進程。

## 設定

### 預設行為

- Cron作業 `consumers_runner` 已啟用
- Cron作業 `consumers_runner` 運行所有已定義的用戶
- 每個用戶都處理10000條報文，然後終止

>[!INFO]
>
>如果您的Adobe Commerce商店托管於雲端平台，請使用 [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) 若要設定 `consumers_runner` 幹活。

### 特定配置

編輯 `/app/etc/env.php` 配置cron作業的檔案 `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run`  — 可啟用或停用的布林值 `consumers_runner` cron作業(預設= `true`)。
- `max_messages`  — 每個使用者在終止前必須處理的最大郵件數(預設= `10000`)。 雖然我們不建議使用，但您可以使用0來防止消費者終止。 請參閱 [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) 配置消費者處理來自消息隊列的消息的方式。
- `consumers`  — 字串的陣列，指定要執行的使用者。 空陣列運行 *all* 消費者。
- `multiple_processes`  — 索引鍵值配對的陣列，指定要在多少個程式中執行哪個使用者。 支援Commerce 2.4.4或更新版本。

   >[!INFO]
   >
   >不建議在MySQL操作的隊列上運行多個使用者。 請參閱 [將消息隊列從MySQL更改為AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) 以取得更多資訊。

   >[!INFO]
   >
   >如果您的Adobe Commerce商店托管於雲端平台，請使用 [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) 配置消費者處理來自消息隊列的消息的方式。

請參閱 [啟動消息隊列消費者](../cli/start-message-queues.md).
