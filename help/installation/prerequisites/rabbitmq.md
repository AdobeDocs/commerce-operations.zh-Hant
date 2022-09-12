---
title: 消息代理
description: 請依照下列步驟，安裝並配置所需的報文代理軟體（如RabbitMQ），以在本地安裝Adobe Commerce和Magento Open Source。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# 消息代理

Adobe Commerce使用RabbitMQ開放原始碼訊息代理程式。 它提供可靠、高可用、可擴展和便攜的報文傳送系統。

消息隊列提供非同步通信機制，其中消息的發送者和接收者不相互聯繫。 它們也不需要同時與消息隊列通信。 當發送者將郵件放入隊列時，會儲存該郵件，直到收件者收到郵件為止。

在安裝Adobe Commerce或Magento Open Source之前，必須建立消息隊列系統。 基本順序為：

1. 安裝RabbitMQ和任何必要條件。
1. 將RabbitMQ連接到Adobe Commerce或Magento Open Source。

>[!NOTE]
>
>您可以使用MySQL或RabbitMQ來處理訊息佇列。 有關設定消息隊列系統的詳細資訊，請參見 [消息隊列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/). 如果您使用Bulk API搭配Adobe Commerce，則訊息佇列系統設定預設為使用RabbitMQ作為訊息代理。 請參閱 [啟動消息隊列消費者](../../configuration/cli/start-message-queues.md) 以取得更多資訊。

## 在Ubuntu上安裝RabbitMQ

要在Ubuntu 16上安裝RabbitMQ，請輸入以下命令：

```bash
sudo apt install -y rabbitmq-server
```

此命令還安裝所需的Erlang軟體包。

如果您有較舊版本的Ubuntu,RabbitMQ建議從其網站安裝該軟體包。

1. 從下載.deb套件 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. 使用安裝套件 `dpkg`.

請參閱 [在Debian/Ubuntu上安裝](https://www.rabbitmq.com/install-debian.html) 以取得更多資訊。

## 在CentOS上安裝RabbitMQ

### 安裝Erlang

RabbitMQ是使用Erlang寫程式語言編寫的，該語言必須安裝在與RabbitMQ相同的系統上。

請參閱 [手動安裝](https://www.erlang-solutions.com/downloads/) 以取得更多資訊。

請參閱 [RabbitMQ/Erlang版本矩陣](https://www.rabbitmq.com/which-erlang.html) 以安裝正確的版本。

### 安裝RabbitMQ

CentOS上包含RabbitMQ伺服器，但版本通常為舊版。 RabbitMQ建議從其網站安裝軟體包。

請參閱RabbitMQ安裝頁面，以取得最新支援的版本。 Adobe Commerce和Magento Open Source2.3和2.4支援RabbitMQ 3.8.x。

請參閱 [在基於RPM的Linux上安裝](https://www.rabbitmq.com/install-rpm.html) 以取得更多資訊。

## 配置RabbitMQ

查看官方的RabbitMQ文檔以配置和管理RabbitMQ。 請注意下列事項：

* 環境變數
* 埠訪問
* 預設用戶帳戶
* 啟動和停止代理
* 系統限制

## 使用RabbitMQ安裝並連接

如果您安裝Adobe Commerce或Magento Open Source _after_ 安裝RabbitMQ時，請在安裝期間添加以下命令行參數：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

其中：

| 參數 | 說明 |
|--- |--- |
| `--amqp-host` | 安裝RabbitMQ的主機名。 |
| `--amqp-port` | 用於連接到RabbitMQ的埠。 預設為 `5672`. |
| `--amqp-user` | 連接到RabbitMQ的用戶名。 請勿使用預設使用者 `guest`. |
| `--amqp-password` | 連接到RabbitMQ的密碼。 請勿使用預設密碼 `guest`. |
| `--amqp-virtualhost` | 用於連接到RabbitMQ的虛擬主機。 預設為 `/`. |
| `--amqp-ssl` | 指示是否連接到RabbitMQ。 預設為 `false`. 如果將值設為true，請參閱設定SSL以取得詳細資訊。 |

## Connect RabbitMQ

如果已安裝Adobe Commerce或Magento Open Source，並且要將其連接到RabbitMQ，請添加 `queue` 區段 `<install_directory>/app/etc/env.php` 檔案，使其類似下列內容：

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

您也可以使用 `bin/magento setup:config:set` 命令：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

執行命令或更新 `<install_directory>/app/etc/env.php` 檔案中的AMQP配置值，請運行 `bin/magento setup:upgrade` 在RabbitMQ中應用更改並建立所需的隊列和交換。

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

連接了Adobe Commerce和RabbitMQ後，必須啟動消息隊列消費者。 請參閱 [配置消息隊列](../../configuration/cli/start-message-queues.md) 以取得詳細資訊。
