---
title: 軟體建議
description: 瞭解Adobe Commerce的軟體需求與建議。 探索生產環境的支援版本和設定最佳實務。
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 0%

---

# 軟體建議

我們需要[!DNL Commerce]的生產執行個體使用下列軟體：

* [PHP](../installation/system-requirements.md)
* Nginx和[PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch]或OpenSearch](../installation/prerequisites/search-engine/overview.md)

針對多伺服器部署或計畫擴充業務的商家，我們建議下列事項：

* [[!DNL Varnish]快取](../configuration/cache/config-varnish.md)
* 工作階段的[Redis](../configuration/cache/redis-session.md) （從2.0.6+開始）
* 單獨的Redis執行個體作為您的[預設快取](../configuration/cache/redis-pg-cache.md) （請勿將此執行個體用於頁面快取）

如需每種軟體型別支援版本的相關資訊，請參閱[系統需求](../installation/system-requirements.md)。

## 作業系統

[!DNL Commerce]的作業系統組態和最佳化與其他高負載Web應用程式類似。 隨著伺服器處理的同時連線數目增加，可用的通訊端數目可以完全配置。 Linux核心支援「重複使用」TCP連線的機制。 若要啟用此機制，請在`/etc/sysctl.conf`中設定下列值：

>[!INFO]
>
>啟用net.ipv4.tcp_tw_reuse對連入連線沒有影響。

```text
net.ipv4.tcp_tw_reuse = 1
```

核心引數`net.core.somaxconn`控制等待連線的開啟通訊端數目上限。 此值可以安全地增加到1024，但應該與伺服器處理此數量的能力相關聯。 若要啟用此核心引數，請在`/etc/sysctl.conf`中設定下列值：

```text
net.core.somaxconn = 1024
```

## PHP

Magento完全支援PHP 7.3和7.4。配置PHP以獲得請求處理的最高速度和效率時，需要考慮幾個因素。

### PHP擴充功能

我們建議將作用中PHP副檔名的清單限製為[!DNL Commerce]功能所需的清單。

Magento Open Source和Adobe Commerce：

* ext-bcmath
* ext-ctype
* 外部捲曲
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
* 外部soap
* 外部通訊端
* 分鈉
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

此外，Adobe Commerce需要：

* ext-bcmath
* ext-ctype
* 外部捲曲
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
* 外部soap
* 外部通訊端
* 分鈉
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

新增更多擴充功能會增加程式庫的載入時間。

>[!INFO]
>
>已從PHP 7.2移除`php-mcrypt`並取代為[`sodium`資料庫](https://www.php.net/manual/en/book.sodium.php)。 升級PHP時，請確定已正確啟用[na](https://www.php.net/manual/en/sodium.installation.php)。

>[!INFO]
>
>任何設定檔和偵錯擴充功能的存在，可能會對頁面的回應時間造成負面影響。 例如，沒有任何偵錯工作階段的使用中xDebug模組最多可將頁面回應時間增加30%。

### PHP設定

若要保證順利執行所有[!DNL Commerce]執行個體，而不將資料或程式碼傾印到磁碟，請依照下列方式設定記憶體限制：

```text
memory_limit=1G
```

若要進行偵錯，請將此值增加到2G。

#### Realpath_cache設定

若要改善[!DNL Commerce]效能，請在`realpath_cache`檔案中新增或更新下列建議的`php.ini`設定。 此組態可讓PHP處理序快取檔案的路徑，而不是在每次頁面載入時查詢它們。 請參閱PHP檔案中的[效能調整](https://www.php.net/manual/en/ini.core.php)。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

若要在PHP 7上取得[!DNL Commerce]的最大速度，您必須啟動OpCache模組並正確設定它。 建議將下列設定用於模組：

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

當您微調opcache的記憶體配置時，請考慮Magento程式碼庫的大小和所有擴充功能。 Magento的效能團隊會使用前述範例中的值進行測試，因為它在opcache中提供的空間足以供平均已安裝擴充功能數目使用。

如果您的電腦記憶體不足，但未安裝許多擴充功能或自訂專案，請使用下列設定來取得類似的結果：

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

我們建議您啟用[PHP APCu延伸模組](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache)和[設定`composer`以支援它](../performance/deployment-flow.md#preprocess-dependency-injection-instructions)，最佳化最大效能。 此擴充功能會快取已開啟檔案的檔案位置，以提升[!DNL Commerce]伺服器呼叫（包括頁面、Ajax呼叫和端點）的效能。

編輯您的`apcu.ini`檔案以包含以下專案：

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## 網頁伺服器

Magento完全支援Nginx和Apache網頁伺服器。 [!DNL Commerce]在`<magento_home>/nginx.conf.sample` (Nginx)和`<magento_home>.htaccess.sample` (Apache)檔案中提供範例建議組態檔。  Nginx範例包含改善效能的設定，因此不需要重新配置。 範例檔案中定義的部分主要設定最佳實務包括：

* 在瀏覽器中快取靜態內容的設定
* PHP的記憶體和執行時間設定
* 內容壓縮設定

您也應該設定用於輸入請求處理的執行緒數量，如下所示：

| 網頁伺服器 | 屬性名稱 | 位置 | 相關資訊 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [調整NGINX的效能](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache效能調整](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM通用指示](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

此檔案未提供深入的[!DNL MySQL]調整指示，因為每個商店和環境都不同，但我們可以提出一些一般建議。

已對[!DNL MySQL] 5.7.9進行多項改善。我們相信[!DNL MySQL]會以良好的預設設定發佈。 最關鍵的設定如下：

| 引數 | 預設 | 說明 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 預設值設為8，以避免多個執行緒嘗試存取相同執行個體時發生問題。 |
| `innodb_buffer_pool_size` | 128MB | 結合上述多個集區執行個體，這表示1024MB的預設記憶體配置。 總大小會分配到所有緩衝集區。 為達到最佳效率，請指定`innodb_buffer_pool_instances`和`innodb_buffer_pool_size`的組合，讓每個緩衝集區執行個體至少有1 GB。 |
| `max_connections` | 150 | `max_connections`引數的值應該與應用程式伺服器中設定的PHP執行緒總數相關。 一般建議是300 （小型環境）和1,000 （中型環境）。 |
| `innodb_thread_concurrency` | 0 | 此組態的最佳值應該透過下列公式計算： `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento強烈建議使用[!DNL Varnish]作為商店的完整頁面快取伺服器。 PageCache模組仍存在於程式碼基底中，但應僅用於開發目的。 不應與[!DNL Varnish]搭配使用，或改用。

將[!DNL Varnish]安裝在Web層前面的個別伺服器上。 它應接受所有傳入請求並提供快取頁面副本。 為了允許[!DNL Varnish]有效處理安全頁面，可在[!DNL Varnish]前放置SSL終止Proxy。 Nginx可用於此用途。

[!DNL Commerce]會為[!DNL Varnish] （版本4和5）散發包含所有建議效能設定的範例組態檔。 其中最關鍵的效能包括：

* **後端健康情況檢查**&#x200B;輪詢[!DNL Commerce]伺服器以判斷它是否及時回應。
* **寬限模式**&#x200B;可讓您指示[!DNL Varnish]在快取中保留超過其存留時間(TTL)期間的物件，並在[!DNL Commerce]狀況不佳或尚未擷取最新內容時提供此過時內容。
* **Saint模式**&#x200B;黑名單不健康的[!DNL Commerce]伺服器（時間長度可設定）。 因此，不健康的後端無法在使用[!DNL Varnish]作為負載平衡器時提供流量。

如需實作這些功能的詳細資訊，請參閱[進階 [!DNL Varnish] 組態](../configuration/cache/config-varnish-advanced.md)。

### 資產效能最佳化

一般而言，我們建議將您的資產（影像、JS、CSS等）儲存在CDN上以發揮最佳效能。

如果您的網站不需要部署大量地區設定，且您的伺服器位於與大多數客戶相同的區域，您可以將資產儲存在[!DNL Varnish]中，而不使用CDN，以較低的成本獲得顯著的效能提升。

若要將您的資產儲存在[!DNL Varnish]，請在`default.vcl`為[!DNL Commerce] 5產生的[!DNL Varnish]檔案中新增下列VCL專案。

在`if`子常式中PURGE要求的`vcl_recv`陳述式結尾處，新增：

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

在`vcl_backend_response`子常式中，尋找為`if`或`GET`要求取消設定Cookie的`HEAD`陳述式。
更新的`if`區塊應如下所示：

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

每當您升級網站或部署/更新資產時，請重新啟動[!DNL Varnish]伺服器以清除快取的資產。

## 快取與工作階段伺服器

Magento提供一些儲存快取和工作階段資料的選項，包括Redis、Memcache、檔案系統和資料庫。 這些選項中的部分將於下文討論。

### 單一Web節點設定

如果您只打算使用一個Web節點提供所有流量，將快取放在遠端Redis伺服器上是不合理的。 請改用檔案系統或本機Redis伺服器。 如果要使用檔案系統，請將快取資料夾放在RAM檔案系統上掛載的磁碟區上。 如果您想要使用本機Redis伺服器，強烈建議您設定Redis，使其使用通訊端進行直接連線，而非透過HTTP交換資料。

### 多個Web節點設定

若是設定多個Web節點，Redis是最佳選項。 因為[!DNL Commerce]主動快取大量資料以提升效能，請注意網頁節點與Redis伺服器之間的網路通道。 您不希望該管道成為處理請求的瓶頸。

>[!INFO]
>
>如果您需要同時處理數百及數千個請求，則可能需要一個最多1 Gbit （或更寬）的通道連線您的Redis伺服器。
