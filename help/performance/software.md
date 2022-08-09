---
title: 軟體Recommendations
description: 查看與Adobe Commerce和Magento Open Source部署的最佳效能相關的建議軟體清單。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 0%

---


# 軟體建議

我們要求以下軟體用於 [!DNL Commerce]:

* [菲律賓比索](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html)
* Nginx和 [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html)
* [[!DNL Elasticsearch] 或OpenSearch](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html)

對於多伺服器部署，或對於計畫擴展其業務的商家，我們建議執行以下操作：

* [[!DNL Varnish] 快取](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish.html)
* [雷迪斯](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-session.html) 用於會話(從2.0.6+)
* 另一個Redis實例 [預設快取](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html) （不將此實例用於頁面快取）

請參閱 [系統要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 有關每種軟體類型的受支援版本的資訊。

## 作業系統

作業系統配置和優化與 [!DNL Commerce] 與其他高負載Web應用程式相比。 隨著伺服器處理的併發連接數的增加，可用套接字的數量可以被完全分配。 Linux內核支援「重用」TCP連接的機制。 要啟用此機制，請在 `/etc/sysctl.conf`:

>[!INFO]
>
>啟用net.ipv4.tcp_tw_reuse對傳入連接沒有影響。

```terminal
net.ipv4.tcp_tw_reuse = 1
```

內核參數 `net.core.somaxconn` 控制等待連接的開啟套接字的最大數量。 此值可以安全地增加到1024 ，但應與伺服器處理此量的能力相關。 要啟用此內核參數，請在 `/etc/sysctl.conf`:

`net.core.somaxconn = 1024`

## 菲律賓比索

Magento完全支援七點三和七點四菲律賓比索。在配置PHP以獲得最大速度和效率處理請求時，需要考慮幾個因素。

### PHP擴展

建議將活動PHP擴展清單限制為 [!DNL Commerce] 功能。

Magento Open Source和Adobe Commerce:

* ext-bcmath
* 文本類型
* 外卷
* 分機
* 檔案資訊
* 外
* 外部哈希
* ext iconv
* 外部國際
* extjson
* ext libxml
* extmbstring
* 外部
* 分機
* ext_pdo_mysql
* 外簡體
* ext soap
* 外置套接字
* 外鈉
* 分機
* ext xmlwriter
* ext-xsl
* 分機
* libxml
* lib openssl

此外，Adobe Commerce要求：

* ext-bcmath
* 文本類型
* 外卷
* 分機
* 檔案資訊
* 外
* 外部哈希
* ext iconv
* 外部國際
* extjson
* ext libxml
* extmbstring
* 外部
* 分機
* ext_pdo_mysql
* 外簡體
* ext soap
* 外置套接字
* 外鈉
* 外部
* 分機
* ext xmlwriter
* ext-xsl
* 分機
* libxml
* lib openssl

添加更多擴展會增加庫載入時間。

>[!INFO]
>
>`php-mcrypt` 已從PHP 7.2中刪除，並替換為 [`sodium` 庫](https://www.php.net/manual/en/book.sodium.php)。 確保 [鈉](https://www.php.net/manual/en/sodium.installation.php) 在升級PHP時正確啟用。

>[!INFO]
>
>任何分析和調試擴展的存在都可能對頁面的響應時間產生負面影響。 例如，沒有任何調試會話的活動xDebug模組可將頁面響應時間增加30%。

### PHP設定

確保成功執行所有 [!DNL Commerce] 實例未將資料或代碼轉儲到磁碟，請按如下方式設定記憶體限制：

`memory_limit=1G`

對於調試，將此值增加到2G。

#### Realpath_cache配置

要改進 [!DNL Commerce] 效能、添加或更新以下建議 `realpath_cache` 的 `php.ini` 的子菜單。 此配置允許PHP進程快取檔案路徑，而不是每次載入頁面時查找它們。 請參閱 [效能調整](https://www.php.net/manual/en/ini.core.php) 的子菜單。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### 位元組代碼

使最大速度從 [!DNL Commerce] 在PHP 7上，必須激活OpCache模組並正確配置它。 建議為模組設定以下設定：

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

當您微調opcache的記憶體分配時，請考慮Magento的代碼庫大小和所有擴展。 Magento的效能團隊使用上例中的值進行測試，因為它在opcache中為平均安裝的擴展數提供了足夠的空間。

如果您有記憶體不足的電腦，並且沒有安裝多少擴展或自定義，請使用以下設定獲得類似的結果：

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

我們建議啟用 [PHP APCu擴展](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) 和 [配置 `composer` 支援它](https://devdocs.magento.com/guides/v2.4/performance-best-practices/deployment-flow.html#preprocess-dependency-injection-instructions) 以優化效能。 此擴展插件快取已開啟檔案的檔案位置，從而提高 [!DNL Commerce] 伺服器調用，包括頁面、Ajax調用和終結點。

編輯 `apcu.ini` 檔案以包括以下內容：

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web伺服器

Magento完全支援Nginx和Apache Web伺服器。 [!DNL Commerce] 提供了示例建議的配置檔案  `<magento_home>/nginx.conf.sample` (Nginx)和  `<magento_home>.htaccess.sample` (Apache)檔案。  Nginx示例包含用於提高效能的設定，並且設計為無需重新配置。 示例檔案中定義的一些主要配置最佳實踐包括：

* 在瀏覽器中快取靜態內容的設定
* PHP的記憶體和執行時間設定
* 內容壓縮設定

您還應配置用於輸入請求處理的線程數，如下所列：

| Web伺服器 | 屬性名稱 | 位置 | 相關資訊 |
|--- | --- | --- | ---|
| 恩金 | `worker_connections` | `/etc/nginx/nginx.conf` （德邊） | [調整NGINX以獲得效能](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache效能調整](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM通用指令](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

此文檔未提供深入 [!DNL MySQL] 調整說明，因為每個儲存和環境都不同，但我們可以提出一些一般建議。

在 [!DNL MySQL] 5.7.9我們相信 [!DNL MySQL] 是使用良好預設設定分發的。 最關鍵的設定是：

| 參數 | 預設 | 說明 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 預設值設定為8，以避免多個線程嘗試訪問同一實例時出現問題。 |
| `innodb_buffer_pool_size` | 128 MB | 結合上述多個池實例，這意味著預設記憶體分配為1024MB。 總大小在所有緩衝池中劃分。 為獲得最佳效率，請指定 `innodb_buffer_pool_instances` 和 `innodb_buffer_pool_size` 使每個緩衝池實例至少為1 GB。 |
| `max_connections` | 150 | 的值 `max_connections` 參數應與應用程式伺服器中配置的PHP線程總數相關。 一般性建議為300人，中等環境為1 000人。 |
| `innodb_thread_concurrency` | 0 | 此配置的最佳值應由公式計算： `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento強烈建議使用 [!DNL Varnish] 作為儲存的全頁快取伺服器。 PageCache模組仍在代碼庫中，但應僅用於開發目的。 它不應與，或代替， [!DNL Varnish]。

安裝 [!DNL Varnish] 在Web層前面的單獨伺服器上。 它應接受所有傳入請求並提供快取的頁面副本。 允許 [!DNL Varnish] 為了有效處理安全頁面，SSL終端代理可放置在 [!DNL Varnish]。 Nginx可用於此目的。

[!DNL Commerce] 分發示例配置檔案 [!DNL Varnish] （版本4和5），其中包含所有建議的效能設定。 其中，效能方面最關鍵的是：

* **後端運行狀況檢查** 民調 [!DNL Commerce] 確定伺服器是否正在及時響應。
* **優雅模式** 允許你指示 [!DNL Varnish] 將對象保留在快取中超過其生存時間(TTL)期間，並在 [!DNL Commerce] 不健康或尚未獲取新內容。
* **聖模式** 不健康的黑名單 [!DNL Commerce] 伺服器的可配置時間。 因此，使用時，不健康的後端無法為通信服務 [!DNL Varnish] 作為負載平衡器。

請參閱 [高級 [!DNL Varnish] 配置](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish-advanced.html) 的子菜單。

### 優化資產效能

通常，我們建議在CDN上儲存您的資產（映像、JS、CSS等），以獲得最佳效能。

如果您的站點不需要部署大量語言環境，並且您的伺服器與大多數客戶位於同一區域，則通過將您的資產儲存到 [!DNL Varnish] 而不是使用CDN。

將資產儲存在 [!DNL Varnish]，在 `default.vcl` 由 [!DNL Commerce] 為 [!DNL Varnish] 5.

在 `if` PURGE請求的語句 `vcl_recv` 子常式，添加：

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

在 `vcl_backend_response` 子常式，查找 `if` 取消設定cookie的語句 `GET` 或 `HEAD` 請求。
已更新 `if` 塊應如下所示：

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

重新啟動 [!DNL Varnish] 伺服器，在您升級站點或部署/更新資產時刷新快取資產。

## 快取和會話伺服器

Magento提供了許多用於儲存快取和會話資料的選項，包括Redis、Memcache、檔案系統和資料庫。 下面將討論其中一些選項。

### 單個Web節點設定

如果您計畫僅使用一個Web節點為所有通信服務，則將快取放在遠程Redis伺服器上是沒有意義的。 而是使用檔案系統或本地Redis伺服器。 如果要使用檔案系統，請將快取資料夾放在RAM檔案系統上裝入的卷上。 如果要使用本地Redis伺服器，我們強烈建議配置Redis，以便它使用套接字進行直接連接，而不是通過HTTP交換資料。

### 多個Web節點設定

對於多Web節點設定，Redis是最佳選項。 因為 [!DNL Commerce] 主動快取大量資料以獲得更好的效能，請注意Web節點和Redis伺服器之間的網路通道。 您不希望通道成為請求處理的瓶頸。

>[!INFO]
>
>如果您需要為數百個和數千個同時請求提供服務，則可能需要一個高達1 Gb（甚至更寬）的通道來連接到您的Redis伺服器。
