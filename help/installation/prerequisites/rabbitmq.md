---
title: 消息代理
description: 請按照以下步驟安裝和配置所需的消息代理軟體(如 [!DNL RabbitMQ])，適用於Adobe Commerce和Magento Open Source的內部部署。
source-git-commit: 1233d2e1d80a3228626be3e20f1bd826b1283523
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# 消息代理

Adobe Commerce使用 [!DNL RabbitMQ] 開源消息代理程式。 它提供可靠、高可用、可擴展和便攜的報文傳送系統。

消息隊列提供非同步通信機制，其中消息的發送者和接收者不相互聯繫。 它們也不需要同時與消息隊列通信。 當發送者將郵件放入隊列時，會儲存該郵件，直到收件者收到郵件為止。

在安裝Adobe Commerce或Magento Open Source之前，必須建立消息隊列系統。 基本順序為：

1. 安裝 [!DNL RabbitMQ] 和任何先決條件。
1. Connect [!DNL RabbitMQ] 至Adobe Commerce或Magento Open Source。

>[!NOTE]
>
>您可以使用MySQL或 [!DNL RabbitMQ] 用於處理消息隊列。 有關設定消息隊列系統的詳細資訊，請參見 [消息隊列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/). 如果您使用大量API搭配Adobe Commerce，訊息佇列系統組態會預設為使用 [!DNL RabbitMQ] 作為消息代理。 請參閱 [啟動消息隊列消費者](../../configuration/cli/start-message-queues.md) 以取得更多資訊。

## 安裝 [!DNL RabbitMQ] 在烏本圖

安裝 [!DNL RabbitMQ] 在Ubuntu 16上，輸入以下命令：

```bash
sudo apt install -y rabbitmq-server
```

此命令還安裝所需的Erlang軟體包。

如果你有Ubuntu的舊版本， [!DNL RabbitMQ] 建議您從網站安裝套件。

1. 從下載.deb套件 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. 使用安裝套件 `dpkg`.

請參閱 [在Debian/Ubuntu上安裝](https://www.rabbitmq.com/install-debian.html) 以取得更多資訊。

## 安裝 [!DNL RabbitMQ] 在CentOS上

### 安裝Erlang

[!DNL RabbitMQ] 是使用Erlang寫程式語言寫的，必須安裝在與 [!DNL RabbitMQ].

請參閱 [手動安裝](https://www.erlang-solutions.com/downloads/) 以取得更多資訊。

請參閱 [[!DNL RabbitMQ]/Erlang版本矩陣](https://www.rabbitmq.com/which-erlang.html) 以安裝正確的版本。

### 安裝 [!DNL RabbitMQ]

此 [!DNL RabbitMQ] 伺服器包含在CentOS中，但版本通常為舊版。 [!DNL RabbitMQ] 建議您從網站安裝套件。

請參閱 [!DNL RabbitMQ] 「安裝」頁面，以取得最新的支援版本。 Adobe Commerce和Magento Open Source2.3和2.4支援 [!DNL RabbitMQ] 3.8.x。

請參閱 [在基於RPM的Linux上安裝](https://www.rabbitmq.com/install-rpm.html) 以取得更多資訊。

## 設定 [!DNL RabbitMQ]

審查 [!DNL RabbitMQ] 配置和管理文檔 [!DNL RabbitMQ]. 請注意下列事項：

* 環境變數
* 埠訪問
* 預設用戶帳戶
* 啟動和停止代理
* 系統限制

## 安裝方式 [!DNL RabbitMQ] 和連接

如果您安裝Adobe Commerce或Magento Open Source _after_ 安裝 [!DNL RabbitMQ]，請在安裝期間新增下列命令列參數：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

其中：

| 參數 | 說明 |
|--- |--- |
| `--amqp-host` | 其中的主機名 [!DNL RabbitMQ] 已安裝。 |
| `--amqp-port` | 用於連接到的埠 [!DNL RabbitMQ]. 預設為 `5672`. |
| `--amqp-user` | 用於連接到的用戶名 [!DNL RabbitMQ]. 請勿使用預設使用者 `guest`. |
| `--amqp-password` | 用於連接到 [!DNL RabbitMQ]. 請勿使用預設密碼 `guest`. |
| `--amqp-virtualhost` | 用於連接到的虛擬主機 [!DNL RabbitMQ]. 預設為 `/`. |
| `--amqp-ssl` | 指示是否連接到 [!DNL RabbitMQ]. 預設為 `false`. 如果將值設為true，請參閱設定SSL以取得詳細資訊。 |

## Connect [!DNL RabbitMQ]

如果您已安裝Adobe Commerce或Magento Open Source，且想要將其連線至 [!DNL RabbitMQ]，新增 `queue` 區段 `<install_directory>/app/etc/env.php` 檔案，使其類似下列內容：

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

您也可以設定 [!DNL RabbitMQ] 設定值使用 `bin/magento setup:config:set` 命令：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

執行命令或更新 `<install_directory>/app/etc/env.php` 檔案中的AMQP配置值，請運行 `bin/magento setup:upgrade` 以應用更改並在 [!DNL RabbitMQ].

## 配置SSL

若要設定SSL支援，請編輯 `ssl` 和 `ssl_options` 參數 `<install_directory>/app/etc/env.php` 檔案，使其類似下列內容：

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## 啟動消息隊列使用者

在您連接了Adobe Commerce和 [!DNL RabbitMQ]，您必須啟動訊息佇列使用者。 請參閱 [配置消息隊列](../../configuration/cli/start-message-queues.md) 以取得詳細資訊。
