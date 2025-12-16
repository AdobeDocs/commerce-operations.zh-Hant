---
title: 訊息代理人(ActiveMQ Artemis)
description: 請依照下列步驟，針對Adobe Commerce的內部部署安裝來安裝和設定Apache ActiveMQ Artemis訊息代理人。
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# 訊息代理人(ActiveMQ Artemis)

Adobe Commerce也透過Simple Text Oriented Messaging Protocol (STOMP)支援ActiveMQ Artemis開放原始碼訊息代理人。 它提供可靠且可擴充的傳訊系統，提供彈性的STOMP式整合。


>[!NOTE]
>
>ActiveMQ Artemis是在Adobe Commerce 2.4.5和更新版本中引入。 如需有關在雲端基礎結構專案上在Adobe Commerce中安裝ActiveMQ Artemis的詳細資訊，請參閱[雲端上的Commerce ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemq)中的&#x200B;*設定ActiveMQ服務*。

訊息佇列提供非同步通訊機制，讓訊息的傳送者與接收者不會相互聯絡。 也不需要同時與訊息佇列通訊。 當寄件者將郵件放入佇列時，郵件會儲存到收件者收到郵件為止。

安裝Adobe Commerce之前，必須先建立訊息佇列系統。 基本順序為：

1. 安裝Apache ActiveMQ Artemis及任何必要條件。
1. 將ActiveMQ連線至Adobe Commerce。

>[!NOTE]
>
>您可以使用MySQL、ActiveMQ或[!DNL RabbitMQ]來處理訊息佇列。 如需設定訊息佇列系統的詳細資訊，請參閱[訊息佇列概述](https://developer.adobe.com/commerce/php/development/components/message-queues/)。 如果您搭配Adobe Commerce使用大量API，訊息佇列系統設定預設為使用[!DNL RabbitMQ]作為訊息代理人。 如需詳細資訊，請參閱[啟動訊息佇列消費者](../../configuration/cli/start-message-queues.md)。

>[!TIP]
>
>在安裝之前，請一律檢查[Apache ActiveMQ Artemis下載頁面](https://activemq.apache.org/components/artemis/download/)的最新穩定版本。 本檔案的範例使用2.42.0版，這是截至2025年9月的最新穩定版本。


## 安裝Apache ActiveMQ Artemis

您可以使用Docker （建議用於開發）或手動安裝（建議用於生產）來安裝ActiveMQ Artemis。

### 選項1：Docker安裝（建議用於開發）

#### 先決條件

確定您的系統上已安裝並執行Docker。

>[!TIP]
>
>如需官方ActiveMQ Artemis Docker影像的詳細資訊，請參閱[Apache ActiveMQ Artemis Docker中心頁面](https://hub.docker.com/r/apache/activemq-artemis)。

#### 安裝步驟

1. 使用官方Docker映像執行ActiveMQ Artemis：

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. 使用自訂認證執行：

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Docker管理命令

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### 存取服務

在Docker容器運行後，您可以訪問：

- **網頁主控台**： http://localhost:8161/主控台（預設認證： artemis/artemis）
- **STOMP連線埠**： localhost:61613 (用於Adobe Commerce連線)

>[!NOTE]
>
>建議將Docker安裝用於開發和測試。 在生產環境中，請考慮使用具有適當安全性設定的手動安裝。

### 選項2：在Ubuntu/CentOS上手動安裝

#### 先決條件

確認已安裝Java 17或更高版本（ActiveMQ Artemis 2.42.0+需要）。

### 安裝步驟

1. 從[Apache ActiveMQ Artemis網站](https://activemq.apache.org/components/artemis/download/)下載並安裝最新版本。 截至2025年9月，最新穩定版本為2.42.0：

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. 建立`artemis`使用者並設定擁有權：

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. 建立Broker執行個體：

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. 啟動代理人：

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## 設定ActiveMQ Artemis

檢閱官方ActiveMQ Artemis檔案以設定和管理代理人。 請注意下列專案：

- 環境變數
- 連線埠存取（STOMP通訊協定）
- 預設使用者帳戶和認證
- 啟動和停止代理人
- 系統限制和資源調整

### 金鑰組態檔

- `/var/lib/artemis-instance/etc/broker.xml` — 主要代理人組態
- `/var/lib/artemis-instance/etc/artemis-users.properties` — 使用者驗證
- `/var/lib/artemis-instance/etc/artemis-roles.properties` — 使用者角色
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Bootstrap設定

### 啟用STOMP通訊協定

檢查`/var/lib/artemis-instance/etc/broker.xml`以確定已設定STOMP接受器：

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

若要在STOMP上啟用SSL，您必須明確新增`stomp-ssl`接受者。

## 使用ActiveMQ Artemis安裝並連線

如果您在&#x200B;_之後安裝Adobe Commerce_，則在安裝ActiveMQ Artemis時新增下列命令列引數：

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

其中：

| 引數 | 說明 |
|--- |--- |
| `--stomp-host` | 安裝ActiveMQ的主機名稱。 |
| `--stomp-port` | 用來連線至ActiveMQ的連線埠。 預設值為`61613`。 |
| `--stomp-user` | 連線到ActiveMQ的使用者名稱。 不要使用預設使用者`artemis`。 |
| `--stomp-password` | 用於連線到ActiveMQ的密碼。 不要使用預設密碼`artemis`。 |
| `--stomp-ssl` | 指示是否要連線到ActiveMQ。 預設值為`false`。 若將值設為true，請參閱設定SSL以取得詳細資訊。 |

## 連線ActiveMQ Artemis

如果您在`<install_directory>/app/etc/env.php`檔案中已有具有RabbitMQ (AMQP)設定的Adobe Commerce執行個體，且您想要將其連線至ActiveMQ，請將`queue`區段取代為STOMP，使其類似於以下內容：

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

您也可以使用`bin/magento setup:config:set`命令設定ActiveMQ組態值（如果AMQP組態存在於`app/etc/env.php`檔案中，請將其移除）：

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

執行命令或使用STOMP組態值更新`<install_directory>/app/etc/env.php`檔案之後，請執行`bin/magento setup:upgrade`以套用變更並在ActiveMQ中建立必要的佇列。

## 設定SSL

若要設定對SSL的支援，請編輯`ssl`檔案中的`ssl_options`和`<install_directory>/app/etc/env.php`引數，使其類似下列：

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### SSL組態選項

| 選項 | 說明 | 預設 |
|--- |--- |--- |
| `verify_peer` | 驗證代理人的SSL憑證 | `true` |
| `verify_peer_name` | 驗證代理人的主機名稱符合憑證 | `true` |
| `allow_self_signed` | 允許自我簽署憑證 | `false` |
| `cafile` | 用於代理人驗證的CA憑證檔案的路徑 | SSL的必要專案 |
| `certfile` | 使用者端憑證檔案的路徑（用於雙向SSL） | 可選 |
| `keyfile` | 使用者端私密金鑰檔案的路徑（用於雙向SSL） | 可選 |
| `passphrase` | 使用者端私密金鑰的複雜密碼 | 可選 |

### 開發SSL設定

對於開發環境，您可以使用寬鬆SSL設定：

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## 效能調整

ActiveMQ Artemis提供幾個效能調整選項：

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## 監控與管理

### 網頁主控台

ActiveMQ Artemis提供可在下列位置存取的網頁式管理主控台：
- URL： `http://localhost:8161/console`
- 預設認證： `artemis/artemis`

## 疑難排解

### 常見問題

1. **連線遭拒**：請確定ActiveMQ Artemis正在執行且STOMP接受器已設定。
1. **驗證失敗**：請檢查中介設定和`env.php`檔案中的使用者名稱/密碼。
1. **SSL交握失敗**：驗證SSL憑證和設定。




### 驗證STOMP連線

使用telnet測試STOMP連線：

```bash
telnet localhost 61613
```

您應該會看到連線已建立。 若要使用STOMP指令進行測試：

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

預期的輸出應顯示已建立的連線和STOMP通訊協定回應。

## 啟動訊息佇列取用者

連線Adobe Commerce和ActiveMQ Artemis後，您必須啟動訊息佇列取用者。 請參閱[設定訊息佇列](../../configuration/cli/start-message-queues.md)以取得詳細資料。

