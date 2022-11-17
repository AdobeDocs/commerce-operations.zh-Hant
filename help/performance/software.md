---
title: 軟體Recommendations
description: 檢閱與Adobe Commerce和Magento Open Source部署最佳效能相關的建議軟體清單。
source-git-commit: 8572cc8702d6f7e9c40b64110a9ba18aa5784f44
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---


# 軟體建議

我們需要下列軟體才能用於 [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx和 [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] 或OpenSearch](../installation/prerequisites/search-engine/overview.md)

對於多伺服器部署，或針對計畫擴展其業務的商戶，我們建議：

* [[!DNL Varnish] 快取](../configuration/cache/config-varnish.md)
* [雷迪斯](../configuration/cache/redis-session.md) （來自2.0.6+）
* 另一個Redis例項，作為 [預設快取](../configuration/cache/redis-pg-cache.md) （請勿將此例項用於頁面快取）

請參閱 [系統需求](../installation/system-requirements.md) 有關每種軟體類型的支援版本的資訊。

## 作業系統

作業系統配置和最佳化類似 [!DNL Commerce] 與其他高負載Web應用程式相比。 隨著伺服器處理的併發連接數的增加，可用套接字的數量可以被完全分配。 Linux內核支援一種「重用」TCP連接的機制。 若要啟用此機制，請在 `/etc/sysctl.conf`:

>[!INFO]
>
>啟用net.ipv4.tcp_tw_reuse對傳入的連接沒有影響。

```text
net.ipv4.tcp_tw_reuse = 1
```

內核參數 `net.core.somaxconn` 控制等待連接的開啟套接字的最大數量。 此值可以安全地增加到1024 ，但應與伺服器處理此數量的能力相關。 要啟用此內核參數，請在 `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento完全支援PHP 7.3和7.4。在配置PHP時，有幾個因素要考慮，以便在處理請求時獲得最大的速度和效率。

### PHP擴充功能

建議將活動PHP擴展的清單限制為 [!DNL Commerce] 功能。

Magento Open Source與Adobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* 外接字元
* 外鈉
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

此外，Adobe Commerce需要：

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* 外接字元
* 外鈉
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

新增更多擴充功能會增加程式庫載入時間。

>[!INFO]
>
>`php-mcrypt` 已從PHP 7.2中移除，並取代為 [`sodium` 資料庫](https://www.php.net/manual/en/book.sodium.php). 確保 [鈉](https://www.php.net/manual/en/sodium.installation.php) 在升級PHP時正確啟用。

>[!INFO]
>
>任何設定檔和除錯擴充功能的存在可能會對頁面的回應時間造成負面影響。 例如，沒有任何除錯工作階段的作用中xDebug模組可將頁面回應時間增加最多30%。

### PHP設定

確保成功執行所有 [!DNL Commerce] 在不將資料或代碼轉儲到磁碟的情況下，按如下方式設定記憶體限制：

```text
memory_limit=1G
```

若為除錯，請將此值增加至2G。

#### Realpath_cache配置

改善 [!DNL Commerce] 效能、新增或更新下列建議 `realpath_cache` 設定 `php.ini` 檔案。 此配置允許PHP進程快取到檔案的路徑，而不是每次頁面載入時查找路徑。 請參閱 [效能調整](https://www.php.net/manual/en/ini.core.php) 在PHP文檔中。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### 位元組代碼

使最大速度超出 [!DNL Commerce] 在PHP 7上，必須激活OpCache模組並正確配置它。 建議對模組使用下列設定：

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

當您微調opcache的記憶體分配時，請考慮Magento的代碼庫大小和所有擴展。 Magento的效能團隊使用上述範例中的值進行測試，因為它在opcache中提供足夠的空間，可容納平均已安裝擴充功能數量。

如果您有記憶體不足的電腦，且您未安裝許多擴充功能或自訂項目，請使用下列設定來取得類似的結果：

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

建議您啟用 [PHP APCu擴展](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) 和 [配置 `composer` 支援](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) 以最佳化以發揮最大效能。 此擴充功能會快取已開啟檔案的檔案位置，以提高 [!DNL Commerce] 伺服器呼叫，包括頁面、Ajax呼叫和端點。

編輯 `apcu.ini` 檔案以包含下列項目：

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web伺服器

Magento完全支援Nginx和Apache Web伺服器。 [!DNL Commerce] 在中提供建議的組態檔範例  `<magento_home>/nginx.conf.sample` (Nginx)和  `<magento_home>.htaccess.sample` (Apache)檔案。  Nginx示例包含用於提高效能的設定，並且設計為無需重新配置。 範例檔案中定義的一些主要設定最佳實務包括：

* 快取瀏覽器中靜態內容的設定
* PHP的記憶體和執行時間設定
* 內容壓縮設定

您也應設定用於輸入請求處理的執行緒數，如下所列：

| Web伺服器 | 屬性名稱 | 位置 | 相關資訊 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [調整NGINX以獲得效能](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache效能調整](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM常見指令](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

本檔案未提供深入資訊 [!DNL MySQL] 調整指示，因為每個商店和環境都不同，但我們可以提供一些一般建議。

在 [!DNL MySQL] 5.7.9我們有信心 [!DNL MySQL] 已分發，且預設設定良好。 最關鍵的設定是：

| 參數 | 預設 | 說明 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 預設值設為8，以避免多個執行緒嘗試存取相同執行個體時發生問題。 |
| `innodb_buffer_pool_size` | 128MB | 與上述多個池實例結合，這意味著預設記憶體分配為1024MB。 總大小在所有緩衝池之間被平分。 為達到最佳效率，請指定 `innodb_buffer_pool_instances` 和 `innodb_buffer_pool_size` 使每個緩衝池實例至少為1 GB。 |
| `max_connections` | 150 | 的值 `max_connections` 參數應與應用程式伺服器中配置的PHP線程總數相關。 一般性建議為300個，中等環境為1 000個。 |
| `innodb_thread_concurrency` | 0 | 此設定的最佳值應依公式計算： `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento強烈建議使用 [!DNL Varnish] 作為儲存的整頁快取伺服器。 PageCache模組仍存在於程式碼基底中，但僅應用於開發用途。 它不應與，或取代，一起使用 [!DNL Varnish].

安裝 [!DNL Varnish] 位於Web層前面的獨立伺服器上。 它應接受所有傳入的請求，並提供快取的頁面副本。 若要允許 [!DNL Varnish] 為了有效地與安全頁面協作，可將SSL終端代理放置在 [!DNL Varnish]. Nginx可用於此用途。

[!DNL Commerce] 分發示例配置檔案 [!DNL Varnish] （第4版和第5版），包含所有建議的效能設定。 其中，效能方面最關鍵的是：

* **後端健康狀況檢查** 投票 [!DNL Commerce] 伺服器，以判斷其是否及時回應。
* **寬限模式** 可讓您指示 [!DNL Varnish] 若要將物件保留在快取中超過其存留時間(TTL)期間，並在 [!DNL Commerce] 狀態不正常，或尚未擷取新內容時。
* **Saint模式** 不健康的黑名單 [!DNL Commerce] 伺服器，可設定時間量。 因此，使用時，不健康的後端無法提供流量 [!DNL Varnish] 作為負載平衡器。

請參閱 [進階 [!DNL Varnish] 配置](../configuration/cache/config-varnish-advanced.md) 以取得實作這些功能的詳細資訊。

### 最佳化資產效能

一般而言，建議您將資產（影像、JS、CSS等）儲存在CDN上，以獲得最佳效能。

如果您的網站不需要部署大量地區設定，且您的伺服器與大部分客戶位於相同地區，則您可能會發現，將資產儲存在 [!DNL Varnish] 而非使用CDN。

若要將資產儲存在 [!DNL Varnish]，請在您的 `default.vcl` 檔案生成者 [!DNL Commerce] for [!DNL Varnish] 5。

在 `if` PURGE請求的語句 `vcl_recv` 子程式，添加：

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

在 `vcl_backend_response` 子程式，查找 `if` 取消設定cookie的陳述式 `GET` 或 `HEAD` 要求。
已更新 `if` 區塊應如下所示：

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

重新啟動 [!DNL Varnish] 伺服器，在您升級網站或部署/更新資產時排清快取的資產。

## 快取和工作階段伺服器

Magento提供了儲存快取和會話資料的多種選項，包括Redis、Memcache、檔案系統和資料庫。 以下將討論其中的一些選項。

### 單一Web節點設定

如果您只打算用一個Web節點為所有流量提供服務，將快取放在遠程Redis伺服器上是沒有意義的。 請改為使用檔案系統或本地Redis伺服器。 如果要使用檔案系統，請將快取資料夾放在RAM檔案系統上裝載的卷上。 如果您想使用本地Redis伺服器，我們強烈建議配置Redis ，以便它使用套接字進行直接連接，而不是通過HTTP交換資料。

### 設定多個Web節點

對於多個Web節點設定，Redis是最佳選項。 因為 [!DNL Commerce] 主動快取大量資料以獲得更好的效能，請注意Web節點與Redis伺服器之間的網路通道。 您不希望管道成為請求處理的瓶頸。

>[!INFO]
>
>如果您需要同時處理數以百計的請求，則可能需要1 Gb（甚至更寬）的通道來連接您的Redis伺服器。
