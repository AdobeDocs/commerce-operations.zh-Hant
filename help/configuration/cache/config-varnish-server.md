---
title: 設定nginx做為清漆快取
description: 瞭解如何設定網頁伺服器以搭配Adobe Commerce的Varnish快取。 探索連線埠組態和設定需求。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# 設定清漆快取的nginx {#configure-web-server-for-varnish-caching}

當Varnish用作Adobe Commerce前面的全頁快取時，Varnish通常會監聽公用HTTP連線埠，並在非預設後端連線埠（例如8080）上轉送要求給nginx。 更新Commerce原始伺服器的nginx網站設定，以便接聽Varnish將使用的後端連線埠。

{{varnish-config-cloud}}

以下各節以連線埠8080為例。

**變更Commerce原始伺服器的nginx接聽連線埠**：

1. 在文字編輯器中開啟Adobe Commerce原始伺服器的nginx網站設定。

位置取決於您的作業系統和Nginx配置。 例如，Ubuntu經常使用`/etc/nginx/sites-available/`下的檔案。

1. 在Commerce網站的`server`區塊中，將`listen`指示詞從公用HTTP連線埠變更為Varnish用來連線nginx的後端連線埠。

   例如，變更

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   至：

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. 儲存檔案。

1. 驗證nginx設定：

   ```shell
   nginx -t
   ```

1. 重新啟動nginx：

   ```shell
   systemctl restart nginx
   ```

## 修改Varnish系統設定

更新nginx以監聽後端連線埠後，設定Varnish以轉送要求至該主機和連線埠。 例如：

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### 修改預設VCL

本節探討如何提供最低限度的設定，好讓Varnish傳回HTTP回應標題。 這可讓您在設定[!DNL Commerce]應用程式使用Varnish之前，先驗證Varnish是否有效。

若要將清漆設定為最少：

1. 備份`default.vcl`：

   ```shell
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 在文字編輯器中開啟`/etc/varnish/default.vcl`。
1. 找到下列區段：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 將`.host`的值取代為Varnish _後端_&#x200B;或&#x200B;_原始伺服器_&#x200B;的完整主機名稱或IP位址和接聽連線埠；也就是說，提供內容Varnish的伺服器將會加速。

   通常這是您的網頁伺服器。 請參閱&#x200B;_清漆指南_&#x200B;中的[後端伺服器](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)。

1. 將`.port`的值取代為網頁伺服器的接聽連線埠（此範例中為8080）。

   範例： nginx安裝在主機192.0.2.55上並在連線埠8080上接聽：

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >如果Varnish和nginx在相同主機上執行，Adobe建議您使用IP位址或主機名稱，而非`localhost`。

1. 將變更儲存至`default.vcl`並結束文字編輯器。

1. 重新啟動清漆：

   ```shell
   service varnish restart
   ```

如果Varnish無法啟動，請嘗試從命令列執行，如下所示：

```shell
varnishd -d -f /etc/varnish/default.vcl
```

這應該會顯示錯誤訊息。


>[!INFO]
>
>如果Varnish不是以服務方式啟動，您必須設定SELinux規則以允許其執行。

## 確認亮光是否正常運作

以下各節討論如何驗證Varnish是否正常運作，但&#x200B;_沒有_&#x200B;設定Commerce以使用它。 在設定Commerce之前，請先嘗試此做法。

依照顯示的順序，執行下列各節中討論的工作：

- [開始塗漆](#start-varnish)
- [`netstat`](#netstat)

### 開始塗漆

輸入： `service varnish start`

如果Varnish無法作為服務啟動，請從命令列啟動它，如下所示：

1. 啟動Varnish CLI：

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. 啟動Varnish子程式：

   出現提示時，請輸入`start`

   系統會顯示下列訊息，確認啟動成功：

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

登入Varnish伺服器並輸入下列命令：

```shell
netstat -tulpn
```

請特別尋找下列輸出：

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

前文顯示了在連線埠80上執行的Varnish，以及在連線埠8080上執行的nginx。

如果您沒有看到`varnishd`的輸出，請確定Varnish正在執行。

檢視[`netstat`選項](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html)。

## 安裝Commerce軟體

安裝Commerce軟體（如果尚未安裝）。 提示輸入基底URL時，請使用Varnish主機和連線埠80 （適用於Varnish），因為Varnish會接收所有傳入的HTTP要求。

安裝Commerce時可能發生錯誤：

```text
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

如果您發生此錯誤，請編輯`default.vcl`並將逾時新增至`backend`段落，如下所示：

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## 驗證HTTP回應標題

現在，您可以檢視HTML從任何頁面傳回的回應標題，以確認Varnish正在為頁面提供服務。

在檢視標題之前，您必須先為開發人員模式設定Commerce 。 有幾種方法可以做到，最簡單的方法就是在Commerce應用程式根目錄中修改`.htaccess`。 您也可以使用[`magento deploy:mode:set`](../cli/set-mode.md)命令。

### 針對開發人員模式設定Commerce

若要將Commerce設為開發人員模式，請使用[`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode)命令。

### 檢視清漆日誌

請確定Varnish正在執行，然後在Varnish伺服器上輸入下列命令：

```shell
varnishlog
```

在網頁瀏覽器中，前往任何Commerce頁面。

命令提示字元視窗中會顯示一長串回應標頭清單。 尋找類似以下內容的標頭：

```text
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

如果這類標頭&#x200B;_不_&#x200B;顯示，請停止Varnish，檢查您的`default.vcl`，然後再試一次。

### 檢視HTML回應標頭

有幾種方式可檢視回應標題，包括使用瀏覽器外掛程式或瀏覽器檢測器。

下列範例使用`curl`。 您可以從任何可以使用HTTP存取Commerce伺服器的電腦輸入此命令。

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

例如，

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

尋找類似以下內容的標頭：

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
