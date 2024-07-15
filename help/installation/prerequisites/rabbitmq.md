---
title: 訊息代理人
description: 請依照下列步驟，安裝並設定Adobe Commerce內部部署安裝所需的訊息代理程式軟體（例如 [!DNL RabbitMQ]）。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# 訊息代理人

Adobe Commerce使用[!DNL RabbitMQ]開放原始碼訊息代理人。 它提供可靠、高可用性、可擴充且可攜式的傳訊系統。

訊息佇列提供非同步通訊機制，讓訊息的傳送者與接收者不會相互聯絡。 也不需要同時與訊息佇列通訊。 當寄件者將郵件放入佇列時，郵件會儲存到收件者收到郵件為止。

安裝Adobe Commerce之前，必須先建立訊息佇列系統。 基本順序為：

1. 安裝[!DNL RabbitMQ]及任何先決條件。
1. 將[!DNL RabbitMQ]連線至Adobe Commerce。

>[!NOTE]
>
>您可以使用MySQL或[!DNL RabbitMQ]進行訊息佇列處理。 如需設定訊息佇列系統的詳細資訊，請參閱[訊息佇列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/)。 如果您搭配Adobe Commerce使用大量API，訊息佇列系統設定預設為使用[!DNL RabbitMQ]作為訊息代理人。 如需詳細資訊，請參閱[啟動訊息佇列消費者](../../configuration/cli/start-message-queues.md)。

## 在Ubuntu上安裝[!DNL RabbitMQ]

若要在Ubuntu 16上安裝[!DNL RabbitMQ]，請輸入下列命令：

```bash
sudo apt install -y rabbitmq-server
```

這個命令也會安裝必要的Erlang套件。

如果您有舊版Ubuntu，[!DNL RabbitMQ]建議從他們的網站安裝套件。

1. 從[rabbitmq-server](https://www.rabbitmq.com/download.html)下載.deb套件。
1. 安裝包含`dpkg`的套件。

如需詳細資訊，請參閱[在Debian/Ubuntu上安裝](https://www.rabbitmq.com/install-debian.html)。

## 在CentOS上安裝[!DNL RabbitMQ]

### 安裝Erlang

[!DNL RabbitMQ]是使用Erlang程式語言撰寫的，必須安裝在與[!DNL RabbitMQ]相同的系統上。

如需詳細資訊，請參閱[手動安裝](https://www.erlang-solutions.com/downloads/)。

請參閱[[!DNL RabbitMQ]/Erlang版本矩陣](https://www.rabbitmq.com/which-erlang.html)以安裝正確版本。

### 安裝[!DNL RabbitMQ]

[!DNL RabbitMQ]伺服器包含在CentOS上，但版本通常較舊。 [!DNL RabbitMQ]建議從他們的網站安裝套件。

請參閱[!DNL RabbitMQ]安裝頁面以取得最新支援的版本。 Adobe Commerce 2.3和2.4支援[!DNL RabbitMQ] 3.8.x。

如需詳細資訊，請參閱[在RPM Linux](https://www.rabbitmq.com/install-rpm.html)上安裝。

## 設定[!DNL RabbitMQ]

檢閱正式[!DNL RabbitMQ]檔案以設定和管理[!DNL RabbitMQ]。 請注意下列專案：

* 環境變數
* 連線埠存取
* 預設使用者帳戶
* 啟動和停止代理人
* 系統限制

## 使用[!DNL RabbitMQ]安裝並連線

如果您在&#x200B;_之後安裝Adobe Commerce_，則安裝[!DNL RabbitMQ]，請在安裝期間新增下列命令列引數：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

其中：

| 引數 | 說明 |
|--- |--- |
| `--amqp-host` | 安裝[!DNL RabbitMQ]的主機名稱。 |
| `--amqp-port` | 用來連線到[!DNL RabbitMQ]的連線埠。 預設值為`5672`。 |
| `--amqp-user` | 連線到[!DNL RabbitMQ]的使用者名稱。 不要使用預設使用者`guest`。 |
| `--amqp-password` | 連線到[!DNL RabbitMQ]的密碼。 不要使用預設密碼`guest`。 |
| `--amqp-virtualhost` | 連線至[!DNL RabbitMQ]的虛擬主機。 預設值為`/`。 |
| `--amqp-ssl` | 指示是否要連線到[!DNL RabbitMQ]。 預設值為`false`。 若將值設為true，請參閱設定SSL以取得詳細資訊。 |

## 連線[!DNL RabbitMQ]

如果您已安裝Adobe Commerce且想要將其連線至[!DNL RabbitMQ]，請在`<install_directory>/app/etc/env.php`檔案中新增`queue`區段，使其類似於以下內容：

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

您也可以使用`bin/magento setup:config:set`命令設定[!DNL RabbitMQ]組態值：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

執行命令或使用AMQP組態值更新`<install_directory>/app/etc/env.php`檔案之後，請執行`bin/magento setup:upgrade`以套用變更，並在[!DNL RabbitMQ]中建立必要的佇列和交換。

## 設定SSL

若要設定對SSL的支援，請編輯`<install_directory>/app/etc/env.php`檔案中的`ssl`和`ssl_options`引數，使其類似下列：

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

## 啟動訊息佇列取用者

連線Adobe Commerce和[!DNL RabbitMQ]後，您必須啟動訊息佇列取用者。 請參閱[設定訊息佇列](../../configuration/cli/start-message-queues.md)以取得詳細資料。
