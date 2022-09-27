---
title: 高級清漆配置
description: 設定進階清漆功能，包括健康檢查、寬限和saint模式。
source-git-commit: 974c3480ccf5d1e1a5308e1bd2b27fcfaf3c72b2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# 高級清漆配置

清漆提供幾項功能，可防止客戶在商務伺服器無法正常運作時遇到長時間的延遲和逾時。 這些功能可在 `default.vcl` 檔案。 本主題說明您從管理員下載的VCL（清漆組態語言）檔案中，商務提供的新增項目。

請參閱 [清漆參考手冊](https://varnish-cache.org/docs/6.3/reference/index.html) 有關使用清漆配置語言的詳細資訊。

## 運行狀況檢查

清漆運行狀況檢查功能將輪詢Commerce伺服器以確定它是否及時響應。 如果正常回應，則會在存留時間(TTL)期間過期後重新產生新內容。 否則，清漆總是含有陳腐的成分。

商務定義以下預設運行狀況檢查：

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

每5秒，此健康狀況檢查會呼叫 `pub/health_check.php` 指令碼。 此指令碼檢查伺服器、每個資料庫和Redis（如果已安裝）的可用性。 指令碼必須在2秒內傳回回應。 如果指令碼判斷這些資源中有任何一項已關閉，則會傳回500 HTTP錯誤碼。 如果每10次嘗試中有6次收到此錯誤代碼，則 [後端](https://glossary.magento.com/backend) 不健康。

此 `health_check.php` 指令碼位於 `pub` 目錄。 如果您的商務根目錄為 `pub`，請務必變更 `url` 參數 `/pub/health_check.php` to `health_check.php`.

如需詳細資訊，請參閱 [清漆運行狀況檢查](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) 檔案。

## 寬限模式

寬限模式允許清漆將對象保留在 [快取](https://glossary.magento.com/cache) 超過其TTL值。 清漆可在擷取新版本時提供過期（過時）的內容。 這可改善流量流量並減少載入時間。 它用於下列情況：

- 當商務後端運作正常，但要求所需時間比正常時間長
- 當商務後端不正常時。

此 `vcl_hit` 子常式定義清漆如何響應已快取對象的請求。

### 當商務後端運作正常時

當運行狀況檢查判斷商務後端運作狀況良好時，清漆會檢查寬限期中是否保留時間。 預設寬限期為300秒，但商家可以從 [管理](https://glossary.magento.com/admin) 如 [配置商務以使用清漆](configure-varnish-commerce.md). 如果寬限期尚未過期，清漆會傳送過時內容，並從商務伺服器非同步重新整理物件。 如果寬限期已過，清漆會提供過時內容，並從商務後端同步重新整理物件。

清漆提供過時物件的最大時間量是寬限期（預設為300秒）與TTL值(預設為86400秒)的總和。

若要從 `default.vcl` 檔案中，在 `vcl_hit` 子程式：

```conf
if (obj.ttl + 300s > 0s) {
```

### 當商務後端不正常時

如果商務後端沒有回應，清漆會從快取中提供三天(或如 `beresp.grace`)加上剩餘的TTL（預設為一天），除非手動清除快取內容。

## Saint模式

Saint模式會排除可設定時間量內不健康的後端。 因此，使用清漆作為負載平衡器時，不健康的後端無法提供流量。 Saint模式可與寬限期模式搭配使用，以複雜處理不健康的後端伺服器。 例如，如果一個後端伺服器不健康，則可將重試次數路由至另一個伺服器。 如果其他所有伺服器都關閉，則提供過時的快取對象。 在 `default.vcl` 檔案。

當商務例項個別離線，以執行維護和升級工作時，也可使用Saint模式，而不會影響商務網站的可用性。

### Saint模式必要條件

指定一台電腦作為主安裝。 在此電腦上，安裝Commerce、mySQL資料庫和Liesht的主實例。

在所有其他電腦上，商務實例必須具有訪問主電腦的mySQL資料庫的權限。 輔助電腦還應具有對主Commerce實例的檔案的訪問權限。

或者， [靜態檔案](https://glossary.magento.com/static-files) 可以在所有電腦上關閉版本設定。 您可從下方的「管理員」存取此項 **商店** >設定> **設定** > **進階** > **開發人員** > **靜態檔案設定** > **簽署靜態檔案** = **否**.

最後，所有商務執行個體必須處於生產模式。 清漆開始之前，請清除每個執行個體上的快取。 在管理員中，前往 **系統** >工具> **快取管理** 按一下 **刷新Magento快取**. 您也可以執行下列命令來清除快取：

```bash
bin/magento cache:flush
```

### 安裝

Saint模式不是主清漆包的一部分。 它是獨立版本 `vmod` 必須下載並安裝。 因此，應從源重新編譯清漆，如以下文章所述：

- [安裝清漆6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [安裝清漆6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

重新編譯後，您可以安裝Saint模式 [模組](https://glossary.magento.com/module). 一般而言，請遵循下列步驟：

1. 從獲取原始碼 [清漆模組](https://github.com/varnish/varnish-modules). 原地複製Git版本（主版），因為0.9.x版包含原始碼錯誤。
1. 使用自動工具建立原始碼：

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

請參閱 [清漆模組集合](https://github.com/varnish/varnish-modules) 以取得安裝Saint模式模組的相關資訊。

### 示例VCL檔案

下列程式碼範例顯示必須新增至VCL檔案以啟用saint模式的程式碼。 放置 `import` 報表和 `backend` 定義。

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
