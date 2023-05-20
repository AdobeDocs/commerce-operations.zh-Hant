---
title: 為搜索引擎配置Apache
description: 按照以下步驟，使用Apache Web伺服器配置搜索引擎，以在本地安裝Adobe Commerce和Magento Open Source。
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# 為搜索引擎配置Apache

{{$include /help/_includes/web-server-communication.md}}

## 設定代理

>[!NOTE]
>
>已在2.4.4中添加了OpenSearch支援。OpenSearch是相容的Elasticsearch分叉。 請參閱 [將Elasticsearch遷移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 的子菜單。

本節討論如何將Apache配置為 *不安全* 代理，以便Adobe Commerce可以使用此伺服器上運行的搜索引擎。 本節不討論設定HTTP Basic身份驗證；在中討論 [與Apache的安全通信](#secure-communication-with-apache)。

>[!NOTE]
>
>此示例中代理沒有安全的原因是設定和驗證更容易。 您可以將此代理使用TLS。 如果您希望這樣做，請確保將代理資訊添加到安全虛擬主機配置中。

### 為Apache 2.4設定代理

本節討論如何使用虛擬主機配置代理。

1. 啟用 `mod_proxy` 如下：

   ```bash
   a2enmod proxy_http
   ```

1. 使用文本編輯器開啟 `/etc/apache2/sites-available/000-default.conf`
1. 在檔案頂部添加以下指令：

   ```conf
   Listen 8080
   ```

1. 在檔案底部添加以下內容：

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

1. 輸入以下命令驗證代理是否工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您使用Elasticsearch，而代理使用埠8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   與以下顯示類似的消息指示成功：

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## 與Apache的安全通信

本節討論如何使用Apache和搜索引擎之間的安全通信 [HTTP基本](https://datatracker.ietf.org/doc/html/rfc2617) 使用Apache進行身份驗證。 有關更多選項，請參考以下資源之一：

* [Apache 2.4身份驗證和授權教程](https://httpd.apache.org/docs/2.4/howto/auth.html)

請參閱以下部分之一：

* [建立密碼檔案](#create-a-password)
* [配置安全虛擬主機](#secure-communication-with-apache)

### 建立密碼

出於安全原因，您可以在Web伺服器域外的任何位置找到密碼檔案。 在此示例中，我們將介紹如何將密碼檔案儲存在新目錄中。

#### 如有必要，請安裝htpasswd

首先，看看你有沒有阿帕奇 `htpasswd` 實用程式的安裝方式如下：

1. 輸入以下命令以確定 `htpasswd` 已安裝：

   ```bash
   which htpasswd
   ```

   如果顯示路徑，則安裝路徑；如果命令不返回輸出， `htpasswd` 未安裝。

1. 如有必要，請安裝 `htpasswd`:

   * 烏班圖： `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### 建立密碼檔案

以用戶身份輸入以下命令 `root` 權限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

位置

* `<username>` 可以：

   * 設定cron:Web伺服器用戶或其他用戶。

   在本示例中，我們使用Web伺服器用戶，但用戶的選擇由您決定。

   * 設定Elasticsearch:用戶已命名 `magento_elasticsearch` 在此示例中


* `<password file name>` 必須是隱藏檔案(開頭為 `.`)，並應反映用戶名。 有關詳細資訊，請參閱本節後面的示例。

按照螢幕上的提示為用戶建立密碼。

#### 示例

**示例1:克隆**
您必須為cron僅設定一個用戶的身份驗證；在本示例中，我們使用web伺服器用戶。 要為Web伺服器用戶建立密碼檔案，請輸入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**示例2:Elasticsearch**
必須為兩個用戶設定身份驗證：一個可以訪問nginx，一個可以訪問Elasticsearch。 要為這些用戶建立密碼檔案，請輸入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 添加其他用戶

要將其他用戶添加到密碼檔案中，請以用戶身份輸入以下命令 `root` 權限：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### 與Apache的安全通信

本節討論如何設定 [HTTP基本身份驗證](https://httpd.apache.org/docs/2.2/howto/auth.html)。 使用TLS和HTTP Basic身份驗證一起防止任何人攔截與Elasticsearch或OpenSearch或您的應用程式伺服器的通信。

本節討論如何指定誰可以訪問Apache伺服器。

1. 使用文本編輯器將下列內容添加到安全虛擬主機。

   * Apache 2.4:編輯 `/etc/apache2/sites-available/default-ssl.conf`

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

1. 如果將前面的內容添加到安全虛擬主機，請刪除 `Listen 8080` 和 `<VirtualHost *:8080>` 您之前添加到不安全虛擬主機的指令。

1. 保存更改，退出文本編輯器，然後重新啟動Apache:

   * CentOS: `service httpd restart`
   * 烏班圖： `service apache2 restart`

#### 驗證

{{$include /help/_includes/verify-secure-communication.md}}
