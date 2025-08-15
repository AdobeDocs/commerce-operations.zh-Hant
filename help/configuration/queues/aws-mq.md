---
title: 設定Amazon訊息佇列
description: 瞭解如何設定Commerce以使用AWS MQ服務。
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 設定Amazon訊息佇列

自Commerce 2.4.3起，Amazon訊息佇列(MQ)可作為內部部署訊息佇列例項的雲端就緒替代專案。

若要在AWS上建立訊息佇列，請參閱[Amazon檔案](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html)中的&#x200B;_設定AWS MQ_。

## 設定適用於AWS MQ的Commerce

若要連線到AWS MQ服務，請設定`queue.amqp`檔案中的`env.php`物件。
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

- `host`—AMQP端點的URL；按一下AWS中的代理程式名稱即可使用(移除「https://」和尾端連線埠號碼)
- `user` — 建立AWS MQ代理人時輸入的使用者名稱值
- `password` — 建立AWS MQ Broker時輸入的密碼值

>[!INFO]
>
>Amazon MQ僅支援TLS連線。 不支援對等驗證。

編輯`env.php`檔案後，請執行以下命令以完成安裝：

```bash
bin/magento setup:upgrade
```

## Commerce如何使用AWS MQ服務

`async.operations.all`訊息佇列消費者使用AMQP連線。

此消費者會透過AWS MQ連線路由任何以`async`為前置詞的主題名稱。

例如，在`InventoryCatalog`中有：

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

`InventoryCatalog`的預設設定不會將訊息發佈到[!DNL RabbitMQ]；預設行為是在相同的使用者執行緒中執行動作。 若要通知`InventoryCatalog`發佈訊息，請啟用`cataloginventory/bulk_operations/async`。 從管理員移至&#x200B;**商店** >設定> **目錄** > **詳細目錄** >管理大量作業，並將`Run asynchronously`設定為&#x200B;**是**。

## 測試訊息佇列

若要測試從Commerce傳送至[!DNL RabbitMQ]的訊息：

1. 登入AWS中的[!DNL RabbitMQ]網頁主控台以監視佇列。
1. 在「管理員」中建立產品。
1. 建立「詳細目錄」來源。
1. 啟用&#x200B;**存放區** >設定> **目錄** > **詳細目錄** >管理員大量作業>非同步執行。
1. 前往&#x200B;**目錄** >產品。 從格線中，選取上面建立的產品，然後按一下&#x200B;**指派詳細目錄Source**。
1. 按一下&#x200B;**儲存並關閉**&#x200B;以完成程式。

   您現在應該會看到訊息出現在[!DNL RabbitMQ]網頁主控台中。

1. 啟動`async.operations.all`訊息佇列消費者。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

您現在應該會在[!DNL RabbitMQ] Web主控台中看到已處理佇列的訊息。
在「管理員」中確認產品上的詳細目錄來源已變更。
