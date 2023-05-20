---
title: 修改docroot以提高安全性
description: 防止未經授權的基於瀏覽器的訪問Adobe Commerce或Magento Open Source本地檔案系統。
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# 修改docroot以提高安全性

在帶有Apache Web伺服器的標準安裝中，Adobe Commerce和Magento Open Source安裝到預設Web根： `/var/www/html/magento2`。

的 `magento2/` 目錄包含以下內容：

- `pub/`
- `setup/`
- `var/`

申請由 `/var/www/html/magento2/pub`。 其餘檔案系統易受攻擊，因為可以從瀏覽器訪問該檔案系統。
將webroot設定為 `pub/` 目錄阻止站點訪問者從瀏覽器訪問檔案系統的敏感區域。

本主題介紹如何更改現有實例上的Apache域，以從 `pub/` 目錄，這更安全。

## 關於nginx的注釋

如果您使用 [nginx](../prerequisites/web-server/nginx.md) 和 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 安裝目錄中包含的檔案，您可能已在從 `pub/` 的子菜單。

在定義站點的伺服器塊中使用時， `nginx.conf.sample` 配置將覆蓋伺服器的docroot設定，以從 `pub/` 的子菜單。 例如，請參閱以下配置中的最後一行：

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

要完成本教程，您需要訪問運行在 [燈](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) 堆棧：

- Linux
- Apache(2.4+)
- MySQL(5.7+)
- 菲律賓比索(7.4)
- Elasticsearch(7.x)或OpenSearch(1.2)
- Adobe Commerce或Magento Open Source(2.4+)

>[!NOTE]
>
>請參閱 [先決條件](../prerequisites/overview.md) 和 [安裝指南](../overview.md) 的子菜單。

## 1。編輯伺服器配置

虛擬主機檔案的名稱和位置取決於正在運行的Apache版本。 此示例顯示Apache v2.4上虛擬主機檔案的名稱和位置。

1. 登錄到應用程式伺服器。
1. 編輯虛擬主機檔案：

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 將路徑添加到 `pub/` 目錄 `DocumentRoot` 指令：

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

## 2.更新基URL

如果在安裝應用程式時將目錄名附加到伺服器的主機名或IP地址以建立基本URL(例如 `http://192.168.33.10/magento2`)，需要將其刪除。

>[!NOTE]
>
>替換 `192.168.33.10` 伺服器主機名。

1. 登錄到資料庫：

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

將以下節點追加到 `env.php` 的子菜單。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

請參閱 [env.php引用](../../configuration/reference/config-reference-envphp.md) 的子菜單。

## 4.切換模式

[應用模式](../../configuration/bootstrap/application-modes.md)，包括 `production` 和 `developer`，旨在提高安全性，使開發更容易。 如名字所示，您應切換到 `developer` 模式：擴展或自定義應用程式並切換到 `production` 模式。

在驗證伺服器配置是否正常工作時，在模式之間切換是一個重要步驟。 可以使用CLI工具在以下模式之間切換：

1. 轉到安裝目錄。
1. 切換到 `production` 的子菜單。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 刷新瀏覽器並驗證店面是否正確顯示。
1. 切換到 `developer` 的子菜單。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 刷新瀏覽器並驗證店面是否正確顯示。

## 5.驗證店面

轉到Web瀏覽器中的店面，以驗證所有操作是否正常。

1. 開啟Web瀏覽器，在地址欄中輸入伺服器的主機名或IP地址。 比如說， `http://192.168.33.10`。

   下圖顯示了一個樣例的店面頁面。 如果按如下所示顯示，則您的安裝成功！

   ![驗證安裝成功的Storefront](../../assets/installation/install-success_store.png)

   請參閱 [疑難解答部分](https://support.magento.com/hc/en-us/articles/360032994352) 如果頁面顯示404（未找到）或未能載入影像、CSS和JS等其他資產。

1. 嘗試從瀏覽器訪問應用程式目錄。 在地址欄中將目錄名附加到伺服器的主機名或IP地址：

   如果看到404或「拒絕訪問」消息，則成功限制了對檔案系統的訪問。

   ![拒絕訪問](../../assets/installation/access-denied.png)
