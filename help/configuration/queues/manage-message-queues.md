---
title: 管理消息隊列
description: 瞭解如何從命令行管理Adobe Commerce的消息隊列。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# 管理消息隊列

您可以使用cron作業或外部進程管理器從命令行管理消息隊列，以確保使用者正在檢索消息。

## 流程管理

Cron作業是重新啟動使用者的預設機制。 進程啟動者 `cron` 使用指定的消息數，然後終止。 重新運行 `cron` 重新啟動使用者。

以下示例顯示 `crontab` 運行使用者的配置：

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
>您檢查消息隊列的頻率取決於業務邏輯和可用系統資源。 通常，您可能希望檢查新客戶併發送歡迎電子郵件的頻率要高於資源密集型流程，如更新目錄。 您應定義 `cron` 根據您的業務需要安排時間。
>
>可以在組的「管理儲存」>「設定」>「配置」>「高級」>「系統」>「Cron」配置選項中配置：消費者。
>
>請參閱 [配置並運行cron](../cli/configure-cron-jobs.md) 有關使用的詳細資訊 `cron` 和商業。

您還可以使用進程管理器，如 [主管](http://supervisord.org/index.html) 監視進程的狀態。 管理器可以根據需要使用命令行重新啟動進程。

## 配置

### 預設行為

- 克龍作業 `consumers_runner` 已啟用
- 克龍作業 `consumers_runner` 運行所有定義的使用者
- 每個使用者處理10000條消息，然後終止

>[!INFO]
>
>如果您的Adobe Commerce商店托管在雲平台上，請使用 [`CRON_CONSUMERS_RUNNER`](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 配置 `consumers_runner` 乾粗活。

### 特定配置

編輯 `/app/etc/env.php` 要配置cron作業的檔案 `consumers_runner`。

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

- `cron_run`  — 啟用或禁用 `consumers_runner` cron作業（預設值） `true`)。
- `max_messages`  — 每個使用者在終止前必須處理的最大郵件數(預設值= `10000`)。 儘管我們不建議使用，但您可以使用0來防止使用者終止。 請參閱 [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) 配置使用者處理來自消息隊列的消息的方式。
- `consumers`  — 一個字串陣列，指定要運行的使用者。 空陣列運行 *全部* 消費者。
- `multiple_processes`  — 一組鍵值對，指定在多少進程中運行哪個使用者。

   >[!INFO]
   >
   >建議不要在MySQL操作的隊列上運行多個使用者。 請參閱 [將消息隊列從MySQL更改為AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) 的子菜單。

   >[!INFO]
   >
   >如果您的Adobe Commerce商店托管在雲平台上，請使用 [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://devdocs.magento.com/cloud/env/variables-deploy.html#consumers_wait_for_max_messages) 配置使用者處理來自消息隊列的消息的方式。

請參閱 [啟動消息隊列使用者](../cli/start-message-queues.md)。
