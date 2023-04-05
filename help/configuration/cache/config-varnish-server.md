---
title: 配置Web伺服器
description: 了解如何配置Web伺服器以使用清漆。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# 配置Web伺服器

將Web伺服器配置為偵聽預設埠80以外的埠，因為Quiest直接響應傳入的HTTP請求，而非Web伺服器。

以下各節以埠8080為例。

**更改Apache 2.4偵聽埠**:

1. 開啟 `/etc/httpd/conf/httpd.conf` 在文字編輯器中。
1. 找出 `Listen` 指令。
1. 將監聽埠的值更改為 `8080`. （您可以使用任何可用的監聽埠。）
1. 將變更儲存至 `httpd.conf` 並退出文字編輯器。

## 修改清漆系統配置

要修改清漆系統配置：

1. 身為使用者 `root` 權限，在文本編輯器中開啟「Nish」配置檔案：

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - 烏本圖： `/etc/default/varnish`

1. 將清漆監聽埠設定為80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   對於清漆4.x，請確保DAEMON_OPTS包含正確的偵聽埠 `-a` 參數（即使QUESTE_LISTEN_PORT設定為正確值）:

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 保存對清漆配置檔案的更改並退出文本編輯器。

### 修改預設VCL

本節探討如何提供最小配置，以便Huilte返回HTTP響應標頭。 這可讓您在設定 [!DNL Commerce] 用清漆。

要最少配置清漆：

1. 備份 `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 開啟 `/etc/varnish/default.vcl` 在文字編輯器中。
1. 找到下列標題：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 取代 `.host` 具有完全限定的主機名或IP地址，以及清漆的偵聽埠 _後端_ 或 _來源伺服器_;即，提供內容清漆的伺服器將加速。

   通常，這是您的Web伺服器。 請參閱 [後端伺服器](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) 在 _清漆引導器_.

1. 取代 `.port` 使用Web伺服器的監聽埠（本示例中為8080）。

   範例：主機192.0.2.55上安裝了Apache，埠8080上安裝了Apache:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >如果清漆和Apache在同一台主機上執行，則Adobe建議您使用IP位址或主機名稱，而不要 `localhost`.

1. 將變更儲存至 `default.vcl` 並退出文字編輯器。

1. 重新啟動清漆：

   ```bash
   service varnish restart
   ```

如果清漆無法啟動，請嘗試從命令行運行它，如下所示：

```bash
varnishd -d -f /etc/varnish/default.vcl
```

這應該會顯示錯誤訊息。


>[!INFO]
>
>如果清漆不作為服務啟動，則必須配置SELinux規則以允許其運行。

## 驗證清漆是否正常工作

以下幾節將討論如何驗證清漆是否正常工作，但 _無_ 設定商務以使用它。 您應在設定商務前先嘗試此操作。

按照以下各節中所述的順序執行任務：

- [起始清漆](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### 起始清漆

輸入： `service varnish start`

如果Quiset無法作為服務啟動，請從命令行啟動，如下所示：

1. 啟動清漆CLI:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. 啟動清漆子進程：

   出現提示時，請輸入 `start`

   會顯示下列訊息以確認啟動成功：

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

登錄到清漆伺服器，然後輸入以下命令：

```bash
netstat -tulpn
```

請特別尋找下列輸出：

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

前面顯示的清漆在埠80上運行，在埠8080上運行的Apache。

如果您沒有看到的輸出 `varnishd`，確保清漆在運行。

請參閱 [`netstat` 選項](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## 安裝Commerce軟體

安裝商務軟體（如果尚未安裝）。 提示輸入基本URL時，請使用清漆主機和埠80（用於清漆），因為清漆接收所有傳入的HTTP請求。

安裝商務時可能出錯：

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

如果您遇到此錯誤，請編輯 `default.vcl` 並將逾時新增至 `backend` 斯坦扎如下：

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## 驗證HTTP回應標題

現在，您可以查看從任何頁面傳回的HTML回應標頭，以確認清漆是否正在提供頁面。

您必須先為開發人員模式設定商務，才能查看標題。 有幾種方法可以做到，最簡單的方法就是修改 `.htaccess` （在「商務」應用程式根目錄中）。 您也可以使用 [`magento deploy:mode:set`](../cli/set-mode.md) 命令。

### 為開發人員模式設定商務

若要設定開發人員模式的商務，請使用 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) 命令。

### 看清漆木

請確保清漆正在運行，然後在清漆伺服器上輸入以下命令：

```bash
varnishlog
```

在網頁瀏覽器中，前往任何「商務」頁面。

回應標題的長清單會顯示在命令提示視窗中。 尋找如下的標題：

```terminal
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

如果標題類似， _not_ 展示，停止清漆，檢查 `default.vcl`，然後重試。

### 查看HTML回應標題

有數種方式可查看回應標題，包括使用瀏覽器外掛程式或瀏覽器檢查器。

下列範例使用 `curl`. 您可以從任何可以使用HTTP訪問Commerce伺服器的電腦輸入此命令。

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

尋找如下的標題：

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
