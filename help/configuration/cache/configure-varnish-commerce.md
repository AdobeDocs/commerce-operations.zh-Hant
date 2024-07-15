---
title: 設定Commerce的光漆
description: 瞭解如何更新和管理Commerce應用程式的Varnish設定檔案。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# 設定Commerce應用程式以使用Varnish

若要設定Commerce使用光澤處理：

1. 以管理員身分登入管理員。
1. 按一下「**[!UICONTROL Stores]**」>「設定」>「**組態**」>「**進階**」>「**系統**」>「**全頁快取**」。
1. 從&#x200B;**[!UICONTROL Caching Application]**&#x200B;清單中，按一下&#x200B;**清漆快取**。
1. 在&#x200B;**[!UICONTROL TTL for public content]**&#x200B;欄位中輸入值。
1. 展開&#x200B;**[!UICONTROL Varnish Configuration]**&#x200B;並輸入下列資訊：

   | 欄位 | 說明 |
   | ----- | ----------- |
   | 存取清單 | 輸入完整的主機名稱、IP位址或要使其內容失效的[無類別網域間路由(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking)標籤法IP位址範圍。 請參閱[清漆快取清除](https://varnish-cache.org/docs/3.0/tutorial/purging.html)。 |
   | 後端主機 | 輸入完整的主機名稱或IP位址，並接聽Varnish _後端_&#x200B;或&#x200B;_原始伺服器_&#x200B;的連線埠；也就是說，提供內容Varnish的伺服器會加速。 通常這是您的網頁伺服器。 請參閱[清漆快取後端伺服器](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)。 |
   | 後端連線埠 | 原始伺服器的接聽連線埠。 |
   | 寬限期 | 決定如果後端沒有回應，Varnish提供過時內容的時間長度。 預設值為300秒。 |
   | 處理引數大小 | 指定全頁快取在[`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) HTTP端點上要處理的[配置控制代碼](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles)最大數量。 限制大小可以改善安全性和效能。 預設值為100。 |

1. 按一下&#x200B;**儲存設定**。

您也可以使用C命令列介面工具，從命令列啟動Varnish （而不是登入Admin）：

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## 匯出清漆組態檔

若要從Admin匯出Varnish組態檔：

1. 按一下其中一個匯出按鈕，以建立可與Varnish搭配使用的`varnish.vcl`。

   例如，如果您有Varnish 4，請按一下&#x200B;**Export VCL for Varnish 4**

   下圖顯示一個範例：

   ![設定Commerce以在Admin中使用Varnish](../../assets/configuration/varnish-admin-22.png)

1. 備份您現有的`default.vcl`。 然後將您剛匯出的`varnish.vcl`檔案重新命名為`default.vcl`。 然後將檔案複製到`/etc/varnish/`目錄。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe建議您開啟`default.vcl`，並將`acl purge`的值變更為Varnish主機的IP位址。 （您可以在不同的行上指定多個主機，也可以使用CIDR標籤法。）

   例如，

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 若要自訂Vagrant健康情況檢查、寬限模式或saint模式設定，請參閱[進階塗漆設定](config-varnish-advanced.md)。

1. 重新啟動Varnish與您的網頁伺服器：

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 快取靜態檔案

預設不應該快取靜態檔案，但如果您要快取它們，可以編輯VCL中的區段`Static files caching`，使其具有下列內容：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

您必須進行這些變更，才能設定Commerce使用Varnish。
