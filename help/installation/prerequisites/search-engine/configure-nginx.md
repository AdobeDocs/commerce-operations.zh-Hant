---
title: 為搜索引擎配置Nginx
description: 按照以下步驟，使用Nginx Web伺服器配置搜索引擎，以在本地安裝Adobe Commerce和Magento Open Source。
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# 為搜索引擎配置Nginx

{{$include /help/_includes/web-server-communication.md}}

## 設定代理

>[!NOTE]
>
>已在2.4.4中添加了OpenSearch支援。OpenSearch是相容的Elasticsearch分叉。 請參閱 [將Elasticsearch遷移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 的子菜單。

本節討論如何將nginx配置為 *不安全* 代理，以便Adobe Commerce可以使用此伺服器上運行的搜索引擎。 本節不討論設定HTTP Basic身份驗證；在中討論 [與nginx的安全通信](#secure-communication-with-nginx)。

>[!NOTE]
>
>此示例中代理沒有安全的原因是設定和驗證更容易。 如果需要，可將此代理使用TLS;為此，請確保將代理資訊添加到安全伺服器塊配置中。

### 在全局配置中指定其他配置檔案

確保您的全局 `/etc/nginx/nginx.conf` 包含以下行，以便載入下面各節中討論的其他配置檔案：

```conf
include /etc/nginx/conf.d/*.conf;
```

### 將nginx設定為代理

本節討論如何指定可以訪問nginx伺服器的用戶。

1. 使用文本編輯器建立檔案 `/etc/nginx/conf.d/magento_es_auth.conf` 內容如下：

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. 重新啟動nginx:

   ```bash
   service nginx restart
   ```

1. 輸入以下命令驗證代理是否工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果代理使用埠8080:

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

## 與nginx的安全通信

本節討論如何設定 [HTTP基本身份驗證](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) 安全代理。 使用TLS和HTTP Basic身份驗證一起防止任何人攔截與Elasticsearch或OpenSearch或您的應用程式伺服器的通信。

由於nginx本機支援HTTP Basic身份驗證，因此我們建議對它進行驗證，例如， [摘要身份驗證](https://www.nginx.com/resources/wiki/modules/auth_digest/)，在生產中不推薦。

其他資源：

* [如何在Ubuntu 14.04（數字海洋）上使用Nginx設定密碼驗證](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [使用Nginx(HowtoForge)進行基本HTTP身份驗證](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Nginx配置示例Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

有關詳細資訊，請參閱以下各節：

* [建立密碼](#create-a-password)
* [設定對nginx的訪問](#set-up-access-to-nginx)
* [設定搜索引擎的受限上下文](#set-up-a-restricted-context-for-the-search-engine)
* [驗證通信是否安全](#secure-communication-with-nginx)

### 建立密碼

建議您使用Apache `htpasswd` 命令，用於為具有Elasticsearch或OpenSearch訪問權限的用戶編碼口令(命名為 `magento_elasticsearch` )。

建立密碼：

1. 輸入以下命令以確定 `htpasswd` 已安裝：

   ```bash
   which htpasswd
   ```

   如果顯示路徑，則安裝路徑；如果命令不返回輸出， `htpasswd` 未安裝。

1. 如有必要，請安裝 `htpasswd`:

   * 烏班圖： `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. 建立 `/etc/nginx/passwd` 儲存密碼的目錄：

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >出於安全原因， `<filename>` 應該隱藏；就是說，必須從一個時間開始。

1. *（可選）。* 要將其他用戶添加到密碼檔案中，請輸入相同的命令 `-c` (create)選項：

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. 驗證 `/etc/nginx/passwd` 正確。

### 設定對nginx的訪問

本節討論如何指定可以訪問nginx伺服器的用戶。

>[!WARNING]
>
>所示示例是 *不安全* 代理。 要使用安全代理，請將下列內容（偵聽埠除外）添加到安全伺服器塊。

使用文本編輯器修改 `/etc/nginx/conf.d/magento_es_auth.conf` （不安全）或安全伺服器塊，其內容如下：

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>上例所示的搜索引擎偵聽埠僅是示例。 出於安全原因，建議您使用非預設監聽埠。

### 設定搜索引擎的受限上下文

本節討論如何指定可以訪問搜索引擎伺服器的人員。

1. 輸入以下命令以建立一個目錄來儲存驗證配置：

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. 使用文本編輯器建立檔案 `/etc/nginx/auth/magento_elasticsearch.conf` 內容如下：

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. 如果設定安全代理，請刪除 `/etc/nginx/conf.d/magento_es_auth.conf`。
1. 重新啟動nginx並繼續下一節：

   ```bash
   service nginx restart
   ```

#### 驗證

{{$include /help/_includes/verify-secure-communication.md}}
