---
title: 為Commerce配置清漆
description: 瞭解更新和管理Commerce應用程式的清漆配置檔案。
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 將Commerce應用程式配置為使用清漆

要將Commerce配置為使用清漆：

1. 以管理員身份登錄到管理員。
1. 按一下 **[!UICONTROL Stores]** >設定> **配置** > **高級** > **系統** > **全頁快取**。
1. 從 **[!UICONTROL Caching Application]** 清單，按一下 **清漆快取**。
1. 在 **[!UICONTROL TTL for public content]** 的子菜單。
1. 展開 **[!UICONTROL Varnish Configuration]** 並輸入以下資訊：

   | 欄位 | 說明 |
   | ----- | ----------- |
   | 訪問清單 | 輸入完全限定的主機名、 IP地址或 [無類域間路由(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 要使內容無效的符號IP地址範圍。 請參閱 [清漆快取清除](https://varnish-cache.org/docs/3.0/tutorial/purging.html)。 |
   | 後端主機 | 輸入清漆的完全限定主機名或IP地址和偵聽埠 _後端_ 或 _源伺服器_;即，提供清漆內容的伺服器加速。 通常，這是您的Web伺服器。 請參閱 [清漆快取後端伺服器](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)。 |
   | 後端埠 | 源伺服器的偵聽埠。 |
   | 寬限期 | 如果後端沒有響應，則寬限期確定清漆服務陳舊內容的時間。 預設值為300秒。 |

1. 按一下 **保存配置**。

也可以使用C命令行介面工具從命令行激活清漆，而不是登錄到Admin:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## 導出清漆配置檔案

要從Admin導出清漆配置檔案，請執行以下操作：

1. 按一下其中一個導出按鈕以建立 `varnish.vcl` 你可以用清漆。

   例如，如果有清漆4，請按一下 **清漆4的導出VCL**

   下圖顯示了一個示例：

   ![將Commerce配置為在管理中使用清漆](../../assets/configuration/varnish-admin-22.png)

1. 備份現有 `default.vcl`。 然後更名 `varnish.vcl` 您剛導出的檔案 `default.vcl`。 然後將檔案複製到 `/etc/varnish/` 的子菜單。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe建議您開啟 `default.vcl` 並更改 `acl purge` 到清漆主機的IP地址。 （可以在單獨的行上指定多個主機，也可以使用CIDR表示法。）

   比如說，

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 如果要自定義流浪健康檢查或寬限模式或聖模式配置，請參閱 [高級清漆配置](config-varnish-advanced.md)。

1. 重新啟動清漆和Web伺服器：

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 快取靜態檔案

預設情況下，靜態檔案不應快取，但如果要快取它們，可以編輯節 `Static files caching` 中的「VCL 」，以具有以下內容：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

在將Commerce配置為使用清漆之前，必須進行這些更改。
