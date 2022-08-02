---
title: 高級清漆配置
description: 配置高級清漆功能，包括健康檢查、寬限和聖模式。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# 高級清漆配置

清漆提供了幾種功能，可防止客戶在Commerce伺服器無法正常工作時遇到長時間延遲和超時。 這些功能可在 `default.vcl` 的子菜單。 本主題介紹Commerce在從Admin下載的VCL（清漆配置語言）檔案中提供的附加內容。

查看 [清漆參考手冊](https://varnish-cache.org/docs/6.3/reference/index.html) 的子菜單。

## 運行狀況檢查

清漆運行狀況檢查功能輪詢Commerce伺服器以確定它是否正在及時響應。 如果響應正常，則在「生存時間(TTL)」期間過期後重新生成新內容。 否則，清漆總是含有陳腐的內容。

Commerce定義以下預設運行狀況檢查：

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

每5秒，這個健康檢查 `pub/health_check.php` 的下界。 此指令碼檢查伺服器、每個資料庫和Redis（如果已安裝）的可用性。 指令碼必須在2秒內返迴響應。 如果指令碼確定這些資源中的任何資源已關閉，則返回500 HTTP錯誤代碼。 如果在十次嘗試中六次收到此錯誤代碼， [後端](https://glossary.magento.com/backend) 被認為不健康。

的 `health_check.php` 指令碼位於 `pub` 的子菜單。 如果您的Commerce根目錄為 `pub`，然後確保更改 `url` 參數 `/pub/health_check.php` 至 `health_check.php`。

有關詳細資訊，請參見 [清漆運行狀況檢查](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) 文檔。

## 優雅模式

Grace模式允許清漆將對象保留在 [快取](https://glossary.magento.com/cache) 超過其TTL值。 清漆可在讀取新版本時提供過期（陳舊）內容。 這改善了流量並減少了負載時間。 它用於以下情況：

- 當Commerce後端正常，但請求所花的時間比正常時間長
- 當Commerce後端不正常時。

的 `vcl_hit` 子常式定義清漆如何響應已快取對象的請求。

### 當Commerce後端正常時

當運行狀況檢查確定Commerce後端是否正常時，清漆檢查時間是否在寬限期內。 預設寬限期為300秒，但商家可以 [管理](https://glossary.magento.com/admin) 如所述 [將Commerce配置為使用清漆](config-varnish-magento.md)。 如果寬限期尚未過期，則清漆將提供陳舊內容，並從Commerce伺服器非同步刷新對象。 如果寬限期已過，則清漆將提供陳舊內容並從Commerce後端同步刷新對象。

清漆服務陳舊對象的最大時間量是寬限期（預設為300秒）和TTL值（預設為86400秒）之和。

更改預設寬限期，從 `default.vcl` 檔案，編輯 `vcl_hit` 子常式：

```conf
if (obj.ttl + 300s > 0s) {
```

### 當Commerce後端不正常時

如果Commerce後端沒有響應，則清漆會從快取中提供三天（或如中定義）的陳舊內容 `beresp.grace`)加上剩餘TTL（預設為一天），除非手動清除快取內容。

## 聖模式

Saint模式在可配置的時間段內排除不正常的後端。 因此，使用清漆作為負載平衡器時，不健康的後端無法為通信服務。 Saint模式可與Grace模式一起使用，以允許對不正常的後端伺服器進行複雜處理。 例如，如果一個後端伺服器不正常，則可以將重試次數路由到另一個伺服器。 如果所有其它伺服器都已關閉，則提供陳舊的快取對象。 在中定義Saint模式後端主機和封鎖期 `default.vcl` 的子菜單。

當Commerce實例單獨離線以執行維護和升級任務而不影響Commerce站點的可用性時，也可以使用Saint模式。

### Saint模式先決條件

指定一台電腦作為主安裝。 在此電腦上，安裝Commerce、mySQL資料庫和Huist等主實例。

在所有其他電腦上，Commerce實例必須具有訪問主電腦的mySQL資料庫的權限。 輔助電腦還應具有對主Commerce實例的檔案的訪問權限。

或者， [靜態檔案](https://glossary.magento.com/static-files) 可以在所有電腦上關閉版本控制。 可以從管理員訪問 **商店** >設定> **配置** > **高級** > **開發人員** > **靜態檔案設定** > **簽名靜態檔案** = **否**。

最後，所有Commerce實例必須處於生產模式。 啟動清漆之前，清除每個實例上的快取。 在管理員中，轉到 **系統** >工具> **快取管理** 按一下 **刷新Magento快取**。 您還可以運行以下命令清除快取：

```bash
bin/magento cache:flush
```

### 安裝

Saint模式不是主清漆包的一部分。 它是獨立版本 `vmod` 必須下載和安裝。 因此，您應從源中重新編譯清漆，如下文所述：

- [安裝清漆6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [安裝清漆6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

重新編譯後，可以安裝Saint模式 [模組](https://glossary.magento.com/module)。 一般來說，請執行以下步驟：

1. 從獲取原始碼 [清漆模組](https://github.com/varnish/varnish-modules)。 自0.9.x版本包含原始碼錯誤以來克隆Git版本（主版本）。
1. 使用自動工具生成原始碼：

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

請參閱 [清漆模組集合](https://github.com/varnish/varnish-modules) 的子菜單。

### 示例VCL檔案

以下代碼示例顯示必須添加到VCL檔案以啟用saint模式的代碼。 放置 `import` 報表和 `backend` 定義。

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
