---
title: 設定Amazon訊息佇列
description: 了解如何配置Commerce以使用AWS MQ服務。
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# 設定Amazon訊息佇列

自Commerce 2.4.3起，Amazon訊息佇列(MQ)可作為雲端就緒的替代，以取代內部部署訊息佇列例項。

若要在AWS上建立訊息佇列，請參閱 [設定Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 在 _AWS檔案_.

## 配置AWS MQ的Commerce

若要連線至AWS MQ服務，請設定 `queue.amqp` 物件(在 `env.php` 檔案。
AWS訊息佇列需要SSL/TLS連線。

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

其中：

- `host`- AMQP端點的url;按一下AWS中的代理名稱即可取得(移除&quot;https://&quot;和尾端埠號)
- `user` — 建立AWS MQ代理時輸入的用戶名值
- `password` — 建立AWS MQ代理時輸入的密碼值

>[!INFO]
>
>Amazon MQ僅支援TLS連線。 不支援對等驗證。

編輯 `env.php` 檔案中，運行以下命令以完成安裝：

```bash
bin/magento setup:upgrade
```

## Commerce如何使用AWS MQ服務

此 `async.operations.all` 消息隊列使用者使用AMQP連接。

此使用者會路由任何以開頭的主題名稱 `async` 通過AWS MQ連接。

例如，在 `InventoryCatalog` 有：

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

的預設設定 `InventoryCatalog` 不會將訊息發佈至 [!DNL RabbitMQ];預設行為是在同一用戶線程中執行操作。 告訴 `InventoryCatalog` 若要發佈訊息，請啟用 `cataloginventory/bulk_operations/async`. 從管理員，前往 **商店** >設定> **目錄** > **庫存** >管理大量作業並設定  `Run asynchronously`to **是**.

## 測試訊息佇列

測試從Commerce發送到的消息 [!DNL RabbitMQ]:

1. 登入 [!DNL RabbitMQ] AWS中的Web主控台，用於監視佇列。
1. 在管理員中，建立產品。
1. 建立庫存來源。
1. 啟用 **商店** >設定> **目錄** > **庫存** >管理大量作業>非同步執行。
1. 前往 **目錄** >產品。 從網格中，選擇上面建立的產品，然後按一下 **分配庫存來源**.
1. 按一下 **儲存並關閉** 來完成此程式。

   您現在應該會看到訊息出現在 [!DNL RabbitMQ] web主控台。

1. 啟動 `async.operations.all` 消息隊列使用者。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

現在，您應會在 [!DNL RabbitMQ] web主控台。
驗證「管理員」中的產品上的庫存來源是否已變更。
