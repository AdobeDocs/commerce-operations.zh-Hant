---
title: 修改docroot以提高安全性
description: 防止未經授權的基於瀏覽器的訪問Adobe Commerce或Magento Open Source本地檔案系統。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 修改docroot以提高安全性

在具有Apache Web伺服器的標準安裝中，Adobe Commerce和Magento Open Source會安裝到預設Web根目錄中： `/var/www/html/magento2`.

此 `magento2/` 目錄包含下列內容：

- `pub/`
- `setup/`
- `var/`

應用程式由 `/var/www/html/magento2/pub`. 其餘檔案系統易受攻擊，因為可從瀏覽器訪問。
將Webroot設定為 `pub/` 目錄會阻止網站訪客從瀏覽器存取檔案系統的敏感區域。

本主題說明如何變更現有執行個體上的Apache Docroot，以從 `pub/` 目錄，更安全。

## 關於nginx的備注

如果您使用 [nginx](../prerequisites/web-server/nginx.md) 和 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 檔案包含在安裝目錄中，則您可能已從 `pub/` 目錄。

若用於定義網站的伺服器區塊中， `nginx.conf.sample` 配置會覆寫伺服器的docroot設定，以從 `pub/` 目錄。 例如，請參閱下列設定中的最後一行：

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## 開始之前

若要完成本教學課程，您需要存取在 [燈](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) 堆棧：

- Linux
- Apache(2.4+)
- MySQL(5.7+)
- PHP(7.4)
- Elasticsearch(7.x)或OpenSearch(1.2)
- Adobe Commerce或Magento Open Source(2.4+)

>[!NOTE]
>
>請參閱 [必要條件](../prerequisites/overview.md) 和 [安裝指南](../overview.md) 以取得更多資訊。

## 1.編輯您的伺服器配置

虛擬主機檔案的名稱和位置取決於您運行的Apache版本。 此示例顯示Apache v2.4上虛擬主機檔案的名稱和位置。

1. 登入您的應用程式伺服器。
1. 編輯虛擬主機檔案：

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 將路徑新增至 `pub/` 目錄 `DocumentRoot` 指令：

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. 重新啟動Apache:

   ```bash
   systemctl restart apache2
   ```

## 2.更新基礎URL

如果在伺服器的主機名或IP地址中附加目錄名，以在安裝應用程式時建立基本URL(例如 `http://192.168.33.10/magento2`)，您需要將其移除。

>[!NOTE]
>
>取代 `192.168.33.10` 伺服器的主機名。

1. 登入資料庫：

   ```bash
   mysql -u <user> -p
   ```

1. 指定在安裝應用程式時建立的資料庫：

   ```shell
   use <database-name>
   ```

1. 更新基本URL:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3.更新env.php檔案

將下列節點附加至 `env.php` 檔案。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

請參閱 [env.php參考](../../configuration/reference/config-reference-envphp.md) 以取得更多資訊。

## 4.切換模式

[應用程式模式](../../configuration/bootstrap/application-modes.md)，其中包括 `production` 和 `developer`，旨在改善安全性並讓開發更輕鬆。 如名稱所示，您應切換至 `developer` 模式（擴展或自定義應用程式時），並切換到 `production` 模式。

在模式之間切換是驗證伺服器配置是否正常運作的重要步驟。 可以使用CLI工具在模式之間切換：

1. 前往您的安裝目錄。
1. 切換至 `production` 模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 重新整理瀏覽器，確認店面顯示正確。
1. 切換至 `developer` 模式。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 重新整理瀏覽器，確認店面顯示正確。

## 5.驗證店面

前往網頁瀏覽器中的店面，確認一切都正常運作。

1. 開啟Web瀏覽器，然後在位址列中輸入您伺服器的主機名稱或IP位址。 例如， `http://192.168.33.10`.

   下圖顯示了一個樣例的店面頁面。 如果顯示如下，表示您的安裝成功！

   ![驗證安裝成功的Storefront](../../assets/installation/install-success_store.png)

   請參閱 [疑難排解章節](https://support.magento.com/hc/en-us/articles/360032994352) 如果頁面顯示404（找不到）或無法載入影像、CSS和JS等其他資產。

1. 嘗試從瀏覽器訪問應用程式目錄。 將目錄名稱附加至位址列中伺服器的主機名稱或IP位址：

   如果您看到404或「拒絕訪問」消息，表示您已成功限制對檔案系統的訪問。

   ![拒絕訪問](../../assets/installation/access-denied.png)
