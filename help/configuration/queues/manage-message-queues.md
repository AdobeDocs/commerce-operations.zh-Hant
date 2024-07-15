---
title: 管理訊息佇列
description: 瞭解如何從Adobe Commerce的命令列管理訊息佇列。
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# 管理訊息佇列

您可以使用cron作業或外部程式管理員從命令列管理訊息佇列，以確保消費者正在擷取訊息。

## 程式管理

Cron作業是重新啟動消費者的預設機制。 由`cron`啟動的處理序會使用指定數目的訊息，然後終止。 重新執行`cron`會重新啟動消費者。

下列範例顯示用於執行消費者的`crontab`設定：

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
>您檢查訊息佇列的頻率取決於您的商業邏輯和可用的系統資源。 一般而言，您會想要檢查新客戶，並比更新目錄等資源較密集的程式更頻繁地傳送歡迎電子郵件。 您應根據業務需求定義`cron`個排程。
>
>您可以在管理員商店>設定>設定>進階>系統> Cron設定選項中設定群組：消費者。
>
>如需搭配Commerce使用`cron`的詳細資訊，請參閱[設定並執行cron](../cli/configure-cron-jobs.md)。

您也可以使用程式管理員（例如[監督員](https://supervisord.readthedocs.io/en/latest/)）來監視程式的狀態。 管理員可視需要使用命令列來重新啟動程式。

## 設定

### 預設行為

- Cron工作`consumers_runner`已啟用
- Cron工作`consumers_runner`執行所有已定義的使用者
- 每個消費者都會處理10000訊息，然後終止

>[!INFO]
>
>如果您的Adobe Commerce存放區託管在Cloud平台上，請使用[`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner)設定`consumers_runner` cron工作。

### 特定設定

編輯`/app/etc/env.php`檔案以設定cron工作`consumers_runner`。

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

- `cron_run` — 布林值，可啟用或停用`consumers_runner` cron工作（預設= `true`）。
- `max_messages` — 終止前，每個消費者必須處理的訊息數目上限（預設值= `10000`）。 雖然我們不建議這麼做，但您可以使用0來防止消費者終止。 請參閱[`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages)以設定消費者處理訊息佇列中訊息的方式。
- `consumers` — 字串陣列，指定要執行的使用者。 空陣列執行&#x200B;*所有*&#x200B;消費者。
- `multiple_processes` — 機碼值組的陣列，指定要在多少處理序中執行哪個取用者。 在Commerce 2.4.4或更新版本中支援。

  >[!INFO]
  >
  >不建議在MySQL操作的佇列上執行多個取用者。 如需詳細資訊，請參閱[將訊息佇列從MySQL變更為AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp)。

  >[!INFO]
  >
  >如果您的Adobe Commerce存放區託管於雲端平台，請使用[`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages)設定消費者處理訊息佇列訊息的方式。

請參閱[啟動訊息佇列消費者](../cli/start-message-queues.md)。
