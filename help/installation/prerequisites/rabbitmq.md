---
title: 消息代理
description: 按照以下步驟安裝和配置所需的消息代理軟體(如 [!DNL RabbitMQ]為Adobe Commerce和Magento Open Source的內部安裝。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 消息代理

Adobe Commerce使用 [!DNL RabbitMQ] 開源消息代理。 它提供可靠、高可用、可擴展和便攜的消息傳遞系統。

消息隊列提供了非同步通信機制，其中消息的發送者和接收者不相互聯繫。 他們也不需要同時與消息隊列通信。 當發件人將郵件放入隊列時，會將其儲存，直到收件人收到郵件。

在安裝Adobe Commerce或Magento Open Source之前，必須建立消息隊列系統。 基本順序是：

1. 安裝 [!DNL RabbitMQ] 和任何先決條件。
1. 連接 [!DNL RabbitMQ] Adobe Commerce或Magento Open Source。

>[!NOTE]
>
>可以使用MySQL或 [!DNL RabbitMQ] 消息隊列處理。 有關設定消息隊列系統的詳細資訊，請參閱 [消息隊列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/)。 如果您正在將批量API與Adobe Commerce一起使用，則消息隊列系統配置預設為使用 [!DNL RabbitMQ] 作為消息代理。 請參閱 [啟動消息隊列使用者](../../configuration/cli/start-message-queues.md) 的子菜單。

## 安裝 [!DNL RabbitMQ] 在烏班圖

安裝 [!DNL RabbitMQ] 在Ubuntu 16上，輸入以下命令：

```bash
sudo apt install -y rabbitmq-server
```

此命令還安裝所需的Erlang程式包。

如果你有更舊版本的烏班圖， [!DNL RabbitMQ] 建議從其網站安裝軟體包。

1. 從下載.deb包 [rabbitmq伺服器](https://www.rabbitmq.com/download.html)。
1. 安裝包時 `dpkg`。

請參閱 [在Debian/Ubuntu上安裝](https://www.rabbitmq.com/install-debian.html) 的子菜單。

## 安裝 [!DNL RabbitMQ] 在CentOS上

### 安裝Erlang

[!DNL RabbitMQ] 是使用Erlang寫程式語言編寫的，必須安裝在與 [!DNL RabbitMQ]。

請參閱 [手動安裝](https://www.erlang-solutions.com/downloads/) 的子菜單。

請參閱 [[!DNL RabbitMQ]/Erlang版本矩陣](https://www.rabbitmq.com/which-erlang.html) 安裝正確的版本。

### 安裝 [!DNL RabbitMQ]

的 [!DNL RabbitMQ] 伺服器包含在CentOS上，但該版本通常是舊版本。 [!DNL RabbitMQ] 建議從其網站安裝軟體包。

請參閱 [!DNL RabbitMQ] 「安裝」頁，以獲取最新支援的版本。 Adobe Commerce和Magento Open Source2.3和2.4支援 [!DNL RabbitMQ] 3.8.x

請參閱 [在基於RPM的Linux上安裝](https://www.rabbitmq.com/install-rpm.html) 的子菜單。

## 配置 [!DNL RabbitMQ]

審查官員 [!DNL RabbitMQ] 配置和管理文檔 [!DNL RabbitMQ]。 請注意以下事項：

* 環境變數
* 埠訪問
* 預設用戶帳戶
* 啟動和停止代理
* 系統限制

## 安裝時 [!DNL RabbitMQ] 連接

如果安裝Adobe Commerce或Magento Open Source _後_ 安裝 [!DNL RabbitMQ]，在安裝過程中添加以下命令行參數：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

位置：

| 參數 | 說明 |
|--- |--- |
| `--amqp-host` | 主機名，其中 [!DNL RabbitMQ] 已安裝。 |
| `--amqp-port` | 用於連接到的埠 [!DNL RabbitMQ]。 預設值為 `5672`。 |
| `--amqp-user` | 用於連接到的用戶名 [!DNL RabbitMQ]。 不使用預設用戶 `guest`。 |
| `--amqp-password` | 用於連接到的密碼 [!DNL RabbitMQ]。 不使用預設密碼 `guest`。 |
| `--amqp-virtualhost` | 用於連接到的虛擬主機 [!DNL RabbitMQ]。 預設值為 `/`。 |
| `--amqp-ssl` | 指示是否連接到 [!DNL RabbitMQ]。 預設值為 `false`。 如果將值設定為true，請參閱配置SSL以瞭解詳細資訊。 |

## 連接 [!DNL RabbitMQ]

如果已安裝了Adobe Commerce或Magento Open Source，並且要將其連接到 [!DNL RabbitMQ]，添加 `queue` 的 `<install_directory>/app/etc/env.php` 檔案，使其與以下內容類似：

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

也可以設定 [!DNL RabbitMQ] 配置值使用 `bin/magento setup:config:set` 命令：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

運行命令或更新 `<install_directory>/app/etc/env.php` 具有AMQP配置值的檔案，運行 `bin/magento setup:upgrade` 應用更改並建立所需的隊列和交換 [!DNL RabbitMQ]。

## 配置SSL

要配置對SSL的支援，請編輯 `ssl` 和 `ssl_options` 參數 `<install_directory>/app/etc/env.php` 檔案，以便它們與以下內容類似：

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

在你把Adobe Commerce和 [!DNL RabbitMQ]，必須啟動消息隊列使用者。 請參閱 [配置消息隊列](../../configuration/cli/start-message-queues.md) 的雙曲餘切值。
