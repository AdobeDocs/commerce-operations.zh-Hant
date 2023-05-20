---
title: 升級的維護模式選項
description: 在您執行升級時，建立客戶在您的Adobe Commerce或Magento Open Source店面看到的自定義維護模式頁面。
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 升級的維護模式選項

本主題討論如何在升級Magento應用程式時建立向用戶顯示的自定義維護頁。 建立自定義頁面是可選的，但建議使用，因為您的站點在升級過程中可以訪問。

建立自定義頁面以將用戶重定向到該頁面會阻止對站點的任何訪問，並通知您的用戶站點正在進行維護。

>[!NOTE]
>
>您必須以用戶身份執行本節中的任務 `root` 權限。 在開發人員模式下無法設定自定義維護頁。

## 建立自定義維護頁

要建立維護頁並重定向到該頁，請首先建立名為：

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

添加以下內容：

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Apache的自定義維護頁

本節討論如何建立自定義維護頁以及如何將通信重定向到該頁。

本節中的示例說明如何修改以下檔案，這是設定維護頁的一種方法：

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` （烏班圖）, `/etc/httpd/conf/httpd.conf` (CentOS)

要將通信重定向到自定義維護頁：

1. 更新Apache配置以執行以下操作：

   - 將所有通信重定向到維護頁
   - 允許列出某些IP，以便管理員可以升級Magento軟體。

   以下示例允許列出192.0.2.110。

   在Apache配置檔案的末尾添加以下內容：

   ```terminal
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. 重新啟動Apache:

   - CentOS: `service httpd restart`
   - 烏班圖： `service apache2 restart`

1. 輸入以下命令：

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [升級系統](../implementation/perform-upgrade.md)。
1. Test您的站點，確保其正常運行。
1. 升級完成後，刪除 `maintenance.enable`。

## nginx的自定義維護頁

本節討論如何建立自定義維護頁以及如何將通信重定向到該頁。

要將通信重定向到自定義維護頁：

1. 使用文本編輯器開啟包含伺服器塊的nginx配置檔案。
1. 將以下內容添加到伺服器塊(`server` 僅顯示為清晰；不添加第二個伺服器塊)。

   以下允許列出安裝Magento的系統上的IP地址192.0.2.110和192.0.2.115 `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 輸入以下命令：

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. 重新載入nginx配置：

   ```bash
   service nginx reload
   ```

1. [升級系統](../implementation/perform-upgrade.md)。
1. Test您的站點，確保其正常運行。
1. 升級完成後，刪除或更名 `maintenance.enable`
1. 重新載入nginx配置：

   ```bash
   service nginx reload
   ```
