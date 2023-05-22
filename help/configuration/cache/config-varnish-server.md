---
title: 配置Web伺服器
description: 瞭解如何將Web伺服器配置為使用清漆。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# 配置Web伺服器

將Web伺服器配置為偵聽預設埠80以外的埠，因為清漆直接響應傳入的HTTP請求，而不是Web伺服器。

以下各節以埠8080為示例。

**更改Apache 2.4偵聽埠**:

1. 開啟 `/etc/httpd/conf/httpd.conf` 的子菜單。
1. 查找 `Listen` 指令。
1. 將偵聽埠的值更改為 `8080`。 （可以使用任何可用的偵聽埠。）
1. 將更改保存到 `httpd.conf` 並退出文本編輯器。

## 修改清漆系統配置

要修改清漆系統配置：

1. 作為用戶 `root` 權限，在文本編輯器中開啟「消失」配置檔案：

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - 德比亞： `/etc/default/varnish`
   - 烏班圖： `/etc/default/varnish`

1. 將清漆偵聽埠設定為80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   對於清漆4.x，確保DAEMON_OPTS包含正確的偵聽埠 `-a` 參數（即使HOUSTE_LISTEN_PORT設定為正確值）:

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 將更改保存到清漆配置檔案並退出文本編輯器。

### 修改預設VCL

本節討論如何提供最小配置，以便清漆返回HTTP響應標頭。 這樣，您就可以在配置 [!DNL Commerce] 應用程式使用清漆。

要最低配置清漆：

1. 備份 `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 開啟 `/etc/varnish/default.vcl` 的子菜單。
1. 找到以下標籤：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 替換 `.host` 具有完全限定的主機名或IP地址和清漆的偵聽埠 _後端_ 或 _源伺服器_;即，提供清漆內容的伺服器會加速。

   通常，這是您的Web伺服器。 請參閱 [後端伺服器](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) 的 _清漆引導器_。

1. 替換 `.port` 與web伺服器的偵聽埠（本示例中為8080）。

   示例：Apache安裝在主機192.0.2.55上，Apache正在偵聽埠8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >如果清漆和Apache在同一主機上運行，Adobe建議您使用IP地址或主機名，而不是 `localhost`。

1. 將更改保存到 `default.vcl` 並退出文本編輯器。

1. 重新啟動清漆：

   ```bash
   service varnish restart
   ```

如果清漆無法啟動，請嘗試從命令行運行，如下所示：

```bash
varnishd -d -f /etc/varnish/default.vcl
```

這將顯示錯誤消息。


>[!INFO]
>
>如果清漆未作為服務啟動，則必須配置SELinux規則以允許其運行。

## 驗證清漆是否正常

以下各節討論如何驗證清漆是否正在工作，但 _無_ 配置Commerce以使用它。 在配置Commerce之前，應嘗試此操作。

按所示順序執行以下各節中討論的任務：

- [起始清漆](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### 起始清漆

輸入： `service varnish start`

如果清漆未能作為服務啟動，請從命令行啟動它，如下所示：

1. 啟動清漆CLI:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. 啟動清漆子進程：

   出現提示時，輸入 `start`

   顯示以下消息以確認成功啟動：

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

登錄到清漆伺服器並輸入以下命令：

```bash
netstat -tulpn
```

請特別查找以下輸出：

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

上面顯示了在埠80上運行的清漆和在埠8080上運行的Apache。

如果看不到輸出 `varnishd`確保清漆在流動。

請參閱 [`netstat` 選項](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html)。

## 安裝Commerce軟體

如果尚未安裝Commerce軟體，請安裝該軟體。 當提示輸入基本URL時，使用清漆主機和埠80（對於清漆），因為清漆接收所有傳入的HTTP請求。

安裝Commerce時可能出錯：

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

如果遇到此錯誤，請編輯 `default.vcl` 並添加超時 `backend` 斯坦扎如下：

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## 驗證HTTP響應標頭

現在，您可以通過查看從任何頁面返回的HTML響應標頭來驗證清漆是否正在提供頁面。

在查看標題之前，必須將Commerce設定為開發者模式。 有幾種方法可以做到，其中最簡單的方法是修改 `.htaccess` 中。 您還可以使用 [`magento deploy:mode:set`](../cli/set-mode.md) 的子菜單。

### 為開發者模式設定Commerce

要將Commerce設定為開發者模式，請使用 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) 的子菜單。

### 看清漆日誌

確保清漆正在運行，然後在清漆伺服器上輸入以下命令：

```bash
varnishlog
```

在Web瀏覽器中，轉到任何Commerce頁面。

在命令提示符窗口中顯示響應標頭的長清單。 查找標題，如下所示：

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

如果像這樣的標題 _不_ 顯示，清漆，檢查 `default.vcl`，然後重試。

### 查看HTML響應標頭

查看響應標頭有幾種方法，包括使用瀏覽器插件或瀏覽器檢查器。

以下示例使用 `curl`。 您可以從任何可以使用HTTP訪問Commerce伺服器的電腦輸入此命令。

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

比如說，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

查找標題，如下所示：

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
