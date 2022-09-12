---
title: 為您的搜尋引擎設定Nginx
description: 請依照下列步驟，使用Nginx Web伺服器設定搜尋引擎，以進行Adobe Commerce和Magento Open Source的內部部署安裝。
source-git-commit: a0f2c6480edcda5540ca83835580d18f401de72f
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# 為您的搜尋引擎設定Nginx

{{$include /help/_includes/web-server-communication.md}}

## 設定代理

>[!NOTE]
>
>2.4.4中新增了OpenSearch支援。OpenSearch是相容的Elasticsearch復本。 配置Elasticsearch7的所有說明均適用於OpenSearch。 請參閱 [將Elasticsearch移轉至OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 以取得更多資訊。

本節探討如何將nginx設定為 *取消安全* 代理，讓Adobe Commerce或Magento Open Source可以使用此伺服器上執行的搜尋引擎。 本節不討論如何設定HTTP Basic驗證；在 [與nginx的安全通信](#secure-communication-with-nginx).

>[!NOTE]
>
>此範例中未保護代理的原因是更容易設定及驗證。 您可以隨此代理使用TLS;若要這麼做，請務必將代理資訊新增至您的安全伺服器區塊設定。

### 在全局配置中指定其他配置檔案

確定您的全域 `/etc/nginx/nginx.conf` 包含下列行，以載入下列各節中討論的其他組態檔：

```conf
include /etc/nginx/conf.d/*.conf;
```

### 將nginx設定為代理

本節探討如何指定哪些人可以存取 [nginx](https://glossary.magento.com/nginx) 伺服器。

1. 使用文本編輯器建立檔案 `/etc/nginx/conf.d/magento_es_auth.conf` 內容如下：

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. 重新啟動Nix:

   ```bash
   service nginx restart
   ```

1. 輸入以下命令以驗證代理是否工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您的代理使用埠8080:

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

## 與nginx的安全通信

本節探討如何設定 [HTTP基本驗證](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) 安全代理。 搭配使用TLS和HTTP Basic驗證可防止任何人攔截與Elasticsearch或您的Adobe Commerce或Magento Open Source伺服器的通訊。

因為Nignx原本支援HTTP Basic驗證，因此建議您改用，例如 [摘要式驗證](https://www.nginx.com/resources/wiki/modules/auth_digest/)，不建議在生產環境中使用。

其他資源：

* [如何在Ubuntu 14.04（數字海洋）上使用Nginx設定密碼驗證](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [使用Nginx進行基本HTTP驗證(HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Ninx設定範例以供Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

如需詳細資訊，請參閱下列章節：

* [建立密碼](#create-a-password)
* [設定對nginx的訪問](#set-up-access-to-nginx)
* [為搜尋引擎設定受限內容](#set-up-a-restricted-context-for-the-search-engine)
* [驗證通信是否安全](#secure-communication-with-nginx)

### 建立密碼

建議您使用Apache `htpasswd` 命令為具有Elasticsearch或OpenSearch訪問權限的用戶編碼(命名 `magento_elasticsearch` 在此範例中)。

要建立密碼：

1. 輸入以下命令以確定 `htpasswd` 已安裝：

   ```bash
   which htpasswd
   ```

   如果顯示路徑，則會安裝路徑；如果命令未返回任何輸出， `htpasswd` 未安裝。

1. 如有必要，請安裝 `htpasswd`:

   * 烏本圖： `apt-get -y install apache2-utils`
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
   >出於安全原因， `<filename>` 應該隱藏；也就是說，它必須從句號開始。

1. *（選用）。* 要向密碼檔案中添加其他用戶，請輸入相同的命令，而不使用 `-c` （建立）選項：

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. 驗證 `/etc/nginx/passwd` 正確。

### 設定對nginx的訪問

本節探討如何指定誰可以存取nginx伺服器。

>[!WARNING]
>
>所示範例適用於 *取消安全* 代理。 若要使用安全代理，請將下列內容（監聽埠除外）新增至您的安全伺服器區塊。

使用文本編輯器修改 `/etc/nginx/conf.d/magento_es_auth.conf` （不安全）或您的安全伺服器區塊，且包含下列內容：

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
>上述範例中顯示的搜尋引擎監聽埠僅為範例。 基於安全原因，我們建議您使用非預設監聽埠。

### 為搜尋引擎設定受限內容

本節探討如何指定哪些人可以存取搜尋引擎伺服器。

1. 輸入以下命令以建立用於儲存身份驗證配置的目錄：

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

1. 如果您設定了安全代理，請刪除 `/etc/nginx/conf.d/magento_es_auth.conf`.
1. 重新啟動nginx並繼續下一節：

   ```bash
   service nginx restart
   ```

#### 驗證

{{$include /help/_includes/verify-secure-communication.md}}
