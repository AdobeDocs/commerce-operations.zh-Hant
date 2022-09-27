---
title: 配置商務清漆
description: 了解如何更新和管理Commerce應用程式的清漆組態檔。
source-git-commit: d451ea025a6f4fc8a4a9f15ca83896a63058a3a0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 配置商務應用程式以使用清漆

要配置商務以使用清漆：

1. 以管理員身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** >設定> **設定** > **進階** > **系統** > **全頁快取**.
1. 從 **[!UICONTROL Caching Application]** 清單，按一下 **清漆快取**.
1. 在 **[!UICONTROL TTL for public content]** 欄位。
1. 展開 **[!UICONTROL Varnish Configuration]** 並輸入以下資訊：

   | 欄位 | 說明 |
   | ----- | ----------- |
   | 訪問清單 | 輸入完全限定的主機名、 IP地址，或 [無類域間路由(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 表示法IP位址範圍，使內容無效。 請參閱 [清漆快取清除](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | 後端主機 | 輸入清漆的完全限定主機名或IP地址和偵聽埠 _後端_ 或 _來源伺服器_;也就是說，提供內容清漆的伺服器加速了。 通常，這是您的Web伺服器。 請參閱 [清漆快取後端伺服器](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | 後端埠 | 源伺服器的偵聽埠。 |
   | 寬限期 | 如果後端不回應，寬限期會決定清漆提供過時內容的時間長度。 預設值為300秒。 |

1. 按一下 **儲存設定**.

您也可以使用C命令行介面工具從命令行（而不是登錄到管理員）激活清漆：

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## 導出清漆配置檔案

要從管理員導出清漆配置檔案，請執行以下操作：

1. 按一下其中一個匯出按鈕以建立 `varnish.vcl` 你可以用清漆。

   例如，如果您有清漆4，請按一下 **清漆4的出口VCL**

   下圖顯示了一個示例：

   ![設定商務以在管理員中使用清漆](../../assets/configuration/varnish-admin-22.png)

1. 備份現有 `default.vcl`. 然後重新命名 `varnish.vcl` 檔案 `default.vcl`. 然後將檔案複製到 `/etc/varnish/` 目錄。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe建議您開啟 `default.vcl` 並變更 `acl purge` 到清漆主機的IP地址。 （您可以在不同的行上指定多個主機，也可以使用CIDR標籤法。）

   例如，

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 如果您要自訂流浪者健康狀況檢查、寬限模式或saint模式設定，請參閱 [高級清漆配置](config-varnish-advanced.md).

1. 重新啟動清漆和Web伺服器：

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 快取靜態檔案

預設不應快取靜態檔案，但如果要快取靜態檔案，則可編輯區段 `Static files caching` （在VCL中）以具有下列內容：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

您必須先進行這些變更，才能將商務設定為使用清漆。
