---
title: 為您的搜尋引擎設定Apache
description: 請依照下列步驟，使用Apache Web伺服器來設定搜尋引擎，以進行Adobe Commerce和Magento Open Source的內部部署安裝。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---


# 為您的搜尋引擎設定Apache

{{$include /help/_includes/web-server-communication.md}}

## 設定代理

>[!NOTE]
>
>2.4.4中新增了OpenSearch支援。OpenSearch是相容的Elasticsearch復本。 配置Elasticsearch7的所有說明均適用於OpenSearch。 請參閱 [將Elasticsearch移轉至OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 以取得更多資訊。

本節探討如何將Apache設定為 *取消安全* 代理，讓Adobe Commerce或Magento Open Source可以使用此伺服器上執行的搜尋引擎。 本節不討論如何設定HTTP Basic驗證；在 [與Apache的安全通訊](#secure-communication-with-apache).

>[!NOTE]
>
>此範例中未保護代理的原因是更容易設定及驗證。 您可以將此Proxy使用TLS。 如果您要這麼做，請務必將代理資訊新增至您的安全虛擬主機設定。

### 設定Apache 2.4的代理

本節探討如何使用虛擬主機來配置代理。

1. 啟用 `mod_proxy` 如下所示：

   ```bash
   a2enmod proxy_http
   ```

1. 使用文本編輯器開啟 `/etc/apache2/sites-available/000-default.conf`
1. 在檔案頂端新增下列指令：

   ```conf
   Listen 8080
   ```

1. 在檔案底部新增下列項目：

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. 重新啟動Apache:

   ```bash
   service apache2 restart
   ```

1. 輸入以下命令以驗證代理是否工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您使用Elasticsearch，而您的代理使用埠8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   顯示的訊息類似於下列，以指出成功：

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## 與Apache的安全通訊

本節探討如何使用來保護Apache和搜尋引擎之間的通訊 [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) 使用Apache進行驗證。 如需更多選項，請參閱下列其中一項資源：

* [Apache 2.4驗證和授權教學課程](https://httpd.apache.org/docs/2.4/howto/auth.html)

請參閱下列其中一節：

* [建立密碼檔案](#create-a-password)
* [配置您的安全虛擬主機](#secure-communication-with-apache)

### 建立密碼

出於安全原因，您可以在Web伺服器域外的任意位置找到密碼檔案。 在此示例中，我們將說明如何將密碼檔案儲存在新目錄中。

#### 如有需要，請安裝htpasswd

首先，查看您是否擁有Apache `htpasswd` 實用程式安裝方式如下：

1. 輸入以下命令以確定 `htpasswd` 已安裝：

   ```bash
   which htpasswd
   ```

   如果顯示路徑，則會安裝路徑；如果命令未返回任何輸出， `htpasswd` 未安裝。

1. 如有必要，請安裝 `htpasswd`:

   * 烏本圖： `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### 建立密碼檔案

以用戶身份輸入以下命令 `root` 權限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

其中

* `<username>` 可以是：

   * 設定開關：Web伺服器用戶或其他用戶。

   在此範例中，我們使用Web伺服器使用者，但使用者的選擇由您決定。

   * 設定Elasticsearch:已命名為 `magento_elasticsearch` 在此範例中


* `<password file name>` 必須是隱藏的檔案(開頭為 `.`)，且應反映使用者的名稱。 如需詳細資訊，請參閱本節稍後的範例。

按照螢幕上的提示為用戶建立密碼。

#### 範例

**範例1:cron**
您只能為cron設定一個用戶的身份驗證；在此示例中，我們使用web伺服器用戶。 要為Web伺服器用戶建立密碼檔案，請輸入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**範例2:Elasticsearch**
您必須為兩個使用者設定驗證：一個可存取nginx，另一個可存取Elasticsearch。 要為這些用戶建立密碼檔案，請輸入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 新增其他使用者

若要將其他用戶添加到密碼檔案中，請輸入以下命令，作為用戶使用 `root` 權限：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### 與Apache的安全通訊

本節探討如何設定 [HTTP基本驗證](https://httpd.apache.org/docs/2.2/howto/auth.html). 同時使用TLS和HTTP Basic驗證，可防止任何人攔截與Elasticsearch或您應用程式伺服器的通訊。

本節探討如何指定誰可以存取Apache伺服器。

1. 使用文字編輯器將下列內容新增至您的安全虛擬主機。

   * Apache 2.4:編輯 `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elastic Server"
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. 如果將前面的添加到安全虛擬主機，請刪除 `Listen 8080` 和 `<VirtualHost *:8080>` 先前添加到不安全虛擬主機的指令。

1. 儲存變更、退出文字編輯器，然後重新啟動Apache:

   * CentOS: `service httpd restart`
   * 烏本圖： `service apache2 restart`

#### 驗證

{{$include /help/_includes/verify-secure-communication.md}}
