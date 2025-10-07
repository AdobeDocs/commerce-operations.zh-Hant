---
title: 進階清漆組態
description: 瞭解如何為Adobe Commerce設定進階塗漆功能，包括健康狀態檢查、寬限和saint模式。 探索VCL最佳化技術。
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# 進階清漆組態

Varnish提供數項功能，可防止客戶在Commerce伺服器無法正常運作時遭遇長時間延遲和逾時。 可在`default.vcl`檔案中設定這些功能。 本主題說明Commerce在您從Admin下載的VCL （清漆組態語言）檔案中提供的新增功能。

請參閱[清漆參考手冊](https://varnish-cache.org/docs/index.html)，以取得有關使用清漆組態語言的詳細資訊。

## 健康情況檢查

Varnish健康情況檢查功能會輪詢Commerce伺服器，判斷伺服器是否及時回應。 如果正常回應，新的內容會在存留時間(TTL)期間過期後重新產生。 否則，Varnish一律會提供過時內容。

Commerce會定義下列預設健康狀態檢查：

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

此健康情況檢查每5秒會呼叫`pub/health_check.php`指令碼。 此指令碼會檢查伺服器、每個資料庫和Redis （如果已安裝）的可用性。 指令碼必須在2秒內傳回回應。 如果指令碼判斷這些資源中有任何停用，則會傳回500 HTTP錯誤代碼。 如果在10次嘗試中，有6次收到此錯誤代碼，則會將後端視為不健康。

`health_check.php`指令碼位於`pub`目錄中。 如果您的Commerce根目錄為`pub`，請務必將`url`引數中的路徑從`/pub/health_check.php`變更為`health_check.php`。

如需詳細資訊，請參閱[清漆健康情況檢查](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks)檔案。

## 寬限模式

寬限模式可讓Varnish將快取中的物件保持在超過其TTL值的狀態。 然後，光澤處理便可在擷取新版本時提供過期（過時）的內容。 這能改善流量流量並減少載入時間。 它用於以下情況：

- 當Commerce後端狀況良好，但要求所花時間比正常情形更久時
- 當Commerce後端不正常時。

`vcl_hit`子常式定義Varnish如何回應已快取物件的要求。

### 當Commerce後端運作正常時

當健康情況檢查確定Commerce後端健康時，Varnish會檢查時間是否仍在寬限期中。 預設寬限期為300秒，但商家可以從Admin設定值，如[設定Commerce以使用Varnish](configure-varnish-commerce.md)中所述。 如果寬限期尚未到期，則Varnish會提供過時的內容，並從Commerce伺服器非同步重新整理物件。 如果寬限期已過， Varnish會提供過時內容，並從Commerce後端同步重新整理物件。

Varnish提供過時物件的時間長度上限是寬限期（預設為300秒）和TTL值(預設為86400秒)的總和。

若要從`default.vcl`檔案內變更預設寬限期，請編輯`vcl_hit`副程式中的下列行：

```conf
if (obj.ttl + 300s > 0s) {
```

### 當Commerce後端不正常時

如果Commerce後端沒有回應，則Varnish會從快取中提供三天的過時內容（或如`beresp.grace`中所定義）加上剩餘的TTL （預設為一天），除非手動清除快取的內容。

## Saint模式

Saint模式會在可設定的時間內排除不健康的後端。 因此，當使用Varnish作為負載平衡器時，不健康的後端將無法提供流量。 Saint模式可與寬限期模式搭配使用，以允許複雜地處理不健全的後端伺服器。 例如，如果一個後端伺服器狀況不良，可將重試路由到另一個伺服器。 如果所有其他伺服器都停止運作，則提供過時的快取物件。 在`default.vcl`檔案中定義了saint模式後端主機和中斷期間。

當Commerce執行個體個別離線以執行維護和升級工作，而不影響Commerce網站的可用性時，也可以使用Saint模式。

### Saint模式必要條件

指定一個電腦作為主要安裝。 在此電腦上安裝Commerce、mySQL資料庫和Varnish的主要執行個體。

在所有其他電腦上，Commerce執行個體必須能夠存取主要電腦的mySQL資料庫。 次要電腦也應該具有主要Commerce執行個體檔案的存取權。

或者，可以在所有電腦上關閉靜態檔案版本設定。 您可以從&#x200B;**商店** >設定> **設定** > **進階** > **開發人員** > **靜態檔案設定** > **簽署靜態檔案** = **否**&#x200B;下的管理員存取此專案。

最後，所有Commerce執行個體都必須處於生產模式。 在Varnish開始之前，清除每個執行個體上的快取。 在Admin中，移至&#x200B;**系統** >工具> **快取管理**&#x200B;並按一下&#x200B;**排清Magento快取**。 您也可以執行下列命令來清除快取：

```bash
bin/magento cache:flush
```

### 安裝

Saint模式不是主要Varnish套件的一部分。 它是必須下載和安裝的獨立版本化`vmod`。 因此，您必須從來源重新編譯Varnish，如您Varnish版本的[安裝指示](https://varnish-cache.org/docs/index.html)中所述。

重新編譯之後，您可以安裝Saint模式模組。 一般而言，請遵循下列步驟：

1. 從[Varnish模組](https://github.com/varnish/varnish-modules)取得原始碼。 複製Git版本（主要版本），因為0.9.x版本包含原始程式碼錯誤。
1. 使用autotools建置原始程式碼：

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

如需安裝Saint模式模組的相關資訊，請參閱[Varnish模組集合](https://github.com/varnish/varnish-modules)。

### 範例VCL檔案

下列程式碼範例顯示必須新增至VCL檔案才能啟用saint模式的程式碼。 將`import`陳述式和`backend`定義放在檔案的最上方。

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
