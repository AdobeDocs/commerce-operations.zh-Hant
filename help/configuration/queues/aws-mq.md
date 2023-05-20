---
title: 設定Amazon消息隊列
description: 瞭解如何配置Commerce使用AWSMQ服務。
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 設定Amazon消息隊列

從Commerce 2.4.3開始，Amazon消息隊列(MQ)可用作本地消息隊列實例的雲就緒替換。

要在AWS上建立消息隊列，請參見 [設定AmazonMQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 的 _AWS文檔_。

## 配置AWSMQ的商務

要連接到AWSMQ服務，請配置 `queue.amqp` 對象 `env.php` 的子菜單。
AWS消息隊列需要SSL/TLS連接。

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

位置：

- `host`- AMQP端點的url;按一下AWS的代理名稱(刪除「https://」和尾隨埠號)
- `user` — 建立AWSMQ Broker時輸入的用戶名值
- `password` — 建立AWSMQ Broker時輸入的密碼值

>[!INFO]
>
>AmazonMQ僅支援TLS連接。 不支援對等驗證。

編輯後 `env.php` 檔案，運行以下命令以完成安裝：

```bash
bin/magento setup:upgrade
```

## Commerce如何使用AWSMQ服務

的 `async.operations.all` 消息隊列使用者使用AMQP連接。

此使用者路由以前置詞的任何主題名稱 `async` 通過AWSMQ連接。

例如，在 `InventoryCatalog` 有：

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

預設配置 `InventoryCatalog` 不將消息發佈到 [!DNL RabbitMQ];預設行為是在同一用戶線程中執行操作。 告訴 `InventoryCatalog` 發佈消息，啟用 `cataloginventory/bulk_operations/async`。 從管理員，轉到 **商店** >配置> **目錄** > **庫存** >管理批量操作和設定  `Run asynchronously`至 **是**。

## 測試消息隊列

test消息從Commerce發送到 [!DNL RabbitMQ]:

1. 登錄到 [!DNL RabbitMQ] Web控制台，用於監視隊列。
1. 在管理中，建立產品。
1. 建立庫存來源。
1. 啟用 **商店** >配置> **目錄** > **庫存** >管理批量操作>非同步運行。
1. 轉到 **目錄** >產品。 從網格中，選擇上面建立的產品，然後按一下 **分配庫存來源**。
1. 按一下 **保存並關閉** 來完成此過程。

   現在，您應看到 [!DNL RabbitMQ] web控制台。

1. 啟動 `async.operations.all` 消息隊列使用者。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

現在，您應在中看到已排隊的消息 [!DNL RabbitMQ] web控制台。
驗證管理中產品的清單源是否已更改。
