---
title: 為您的搜尋引擎設定Apache
description: 請依照下列步驟，使用Apache Web Server設定搜尋引擎，以供Adobe Commerce的內部部署安裝。
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 為您的搜尋引擎設定Apache

{{$include /help/_includes/web-server-communication.md}}

## 設定proxy

>[!NOTE]
>
>2.4.4版本新增OpenSearch支援。OpenSearch是相容的Elasticsearch復本。 如需詳細資訊，請參閱[將Elasticsearch移轉至OpenSearch](../../../upgrade/prepare/opensearch-migration.md)。

本節探討如何將Apache設定為&#x200B;*不安全* Proxy，讓Adobe Commerce能夠使用在此伺服器上執行的搜尋引擎。 本節不討論設定HTTP基本驗證；這將在與Apache](#secure-communication-with-apache)的[安全通訊中討論。

>[!NOTE]
>
>在此範例中，Proxy不受保護的原因是它更容易設定和驗證。 您可以透過此Proxy使用TLS。 如果您想要這麼做，請確定您將Proxy資訊新增至安全虛擬主機設定。

### 設定Apache 2.4的Proxy

本節探討如何使用虛擬主機來設定Proxy。

1. 啟用`mod_proxy`，如下所示：

   ```bash
   a2enmod proxy_http
   ```

1. 使用文字編輯器開啟`/etc/apache2/sites-available/000-default.conf`
1. 在檔案頂端新增下列指令：

   ```conf
   Listen 8080
   ```

1. 在檔案底部新增下列內容：

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. 重新啟動Apache：

   ```bash
   service apache2 restart
   ```

1. 輸入下列命令來驗證Proxy是否有效：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您使用Elasticsearch，而您的Proxy使用連線埠8080：

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   類似下列顯示以指示成功的訊息：

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## 與Apache的安全通訊

本節討論如何使用[HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617)驗證和Apache來保護Apache與搜尋引擎之間的通訊。 如需更多選項，請參閱下列資源之一：

* [Apache 2.4驗證和授權教學課程](https://httpd.apache.org/docs/2.4/howto/auth.html)

請參閱下列其中一節：

* [建立密碼檔案](#create-a-password)
* [設定您的安全虛擬主機](#secure-communication-with-apache)

### 建立密碼

基於安全考量，您可以在網頁伺服器docroot以外的任何地方找到密碼檔案。 在此範例中，我們說明如何將密碼檔案儲存在新目錄中。

#### 安裝htpasswd （如有必要）

首先，檢視是否已依照以下方式安裝Apache `htpasswd`公用程式：

1. 輸入下列命令以判斷是否已安裝`htpasswd`：

   ```bash
   which htpasswd
   ```

   如果路徑顯示，則表示已安裝；如果命令未傳回任何輸出，則不安裝`htpasswd`。

1. 如有必要，請安裝`htpasswd`：

   * Ubuntu： `apt-get -y install apache2-utils`
   * CentOS： `yum -y install httpd-tools`

#### 建立密碼檔案

以具有`root`許可權的使用者身分輸入下列命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

位置

* `<username>`可以是：

   * 設定cron：網頁伺服器使用者或其他使用者。

  在此範例中，我們使用Web伺服器使用者，但使用者的選擇由您決定。

   * 設定Elasticsearch：在此範例中，使用者名為`magento_elasticsearch`

* `<password file name>`必須為隱藏的檔案（以`.`開頭），且應反映使用者的名稱。 如需詳細資訊，請參閱本節稍後的範例。

按照畫面上的提示為使用者建立密碼。

#### 範例

**範例1： cron**
您必須為cron僅設定一個使用者的驗證；在此範例中，我們使用web伺服器使用者。 若要建立Web伺服器使用者的密碼檔，請輸入下列命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**範例2：Elasticsearch**
您必須為兩個使用者設定驗證：一個具有nginx存取權，另一個具有Elasticsearch存取權。 若要為這些使用者建立密碼檔案，請輸入下列命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 新增其他使用者

若要將其他使用者新增至您的密碼檔案，請以具有`root`許可權的使用者身分輸入下列命令：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### 與Apache的安全通訊

本節討論如何設定[HTTP基本驗證](https://httpd.apache.org/docs/2.2/howto/auth.html)。 同時使用TLS和HTTP Basic驗證可防止任何人攔截與Elasticsearch、OpenSearch或您的應用程式伺服器的通訊。

本節探討如何指定可以存取Apache伺服器的使用者。

1. 使用文字編輯器將下列內容新增至您的安全虛擬主機。

   * Apache 2.4：編輯`/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. 如果您已將前述新增至安全虛擬主機，請移除`Listen 8080`以及您先前新增至不安全虛擬主機的`<VirtualHost *:8080>`指示。

1. 儲存變更、退出文字編輯器，然後重新啟動Apache：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`

#### 驗證

{{$include /help/_includes/verify-secure-communication.md}}
