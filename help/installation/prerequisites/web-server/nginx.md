---
title: 恩金
description: 按照以下步驟安裝和配置Nginx Web伺服器，以在本地安裝Adobe Commerce和Magento Open Source。
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---

# 恩金

Adobe Commerce支援nginx 1.18(或 [最新主線版本](https://nginx.org/en/linux_packages.html#mainline))。 您還必須安裝 `php-fpm`。

安裝說明因您使用的作業系統而異。 請參閱 [菲律賓比索](../php-settings.md) 的雙曲餘切值。

## 烏邦圖

以下部分介紹如何使用nginx、PHP和MySQL在Ubuntu上安裝Adobe Commerce和Magento Open Source2.x。

### 安裝nginx

```bash
sudo apt -y install nginx
```

您也可以 [從源生成nginx](https://www.armanism.com/blog/install-nginx-on-ubuntu)

完成以下部分並安裝應用程式後，我們將使用示例配置檔案 [配置nginx](#configure-nginx)。

### 安裝和配置php-fpm

Adobe Commerce和Magento Open Source需要 [PHP擴展](../php-settings.md) 才能正常工作。 除了這些擴展外，還必須安裝和配置 `php-fpm` 的子菜單。

安裝和配置 `php-fpm`:

1. 安裝 `php-fpm` 和 `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >此命令安裝PHP 7.2.X的最新版本。請參閱 [系統要求](../../system-requirements.md) 支援的PHP版本。

1. 開啟 `php.ini` 編輯器中的檔案：

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. 編輯兩個檔案以匹配以下行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >我們建議在測試Adobe Commerce和Magento Open Source時將記憶體限制設定為2 G。 請參閱 [所需的PHP設定](../php-settings.md) 的子菜單。

1. 保存並退出編輯器。

1. 重新啟動 `php-fpm` 服務：

   ```bash
   systemctl restart php7.2-fpm
   ```

### 安裝和配置MySQL

請參閱 [MySQL](../database/mysql.md) 的子菜單。

### 安裝和配置

下載Adobe Commerce和Magento Open Source有多種方法，包括：

* [獲得作曲家的暗喻](../../composer.md)

* [克隆Git儲存庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

此示例使用命令行顯示基於Composer的安裝。

1. 作為 [檔案系統所有者](../file-system/overview.md)，登錄到應用程式伺服器。

1. 更改為Web伺服器docroot目錄或您已配置為虛擬主機docroot的目錄。 在本示例中，我們使用Ubuntu預設值 `/var/www/html`。

   ```bash
   cd /var/www/html
   ```

1. 全局安裝Composer。 安裝Adobe Commerce或Magento Open Source之前，需要更新依賴關係：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Magento Open Source或Adobe Commerce元包建立Composer項目。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   在出現提示時，輸入 [身份驗證密鑰](../authentication-keys.md)。 您 _公鑰_ 是您的用戶名；你 _私鑰_ 是您的密碼。

1. 在安裝應用程式之前，設定Web伺服器組的讀寫權限。 這是必需的，以便命令行可以將檔案寫入檔案系統。

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. 從 [命令行](../../advanced.md)。 此示例假定安裝目錄的名稱 `magento2ee`，也請參見Wiki頁。 `db-host` 在同一台電腦上(`localhost`)，而且 `db-name`。 `db-user`, `db-password` 全部 `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. 切換到開發模式：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 配置nginx

建議使用 `nginx.conf.sample` 安裝目錄和nginx虛擬主機中提供的配置檔案。

這些說明假定您正在為nginx虛擬主機使用Ubuntu預設位置(例如， `/etc/nginx/sites-available`)和Ubuntu預設docroot(例如， `/var/www/html`)但是，您可以更改這些位置以適合您的環境。

1. 為您的站點建立新虛擬主機：

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 添加以下配置：

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >的 `include` 指令必須指向安裝目錄中的示例nginx配置檔案。

1. 替換 `www.magento-dev.com` 域名。 這必須與安裝Adobe Commerce或Magento Open Source時指定的基URL匹配。

1. 保存並退出編輯器。

1. 通過在 `/etc/nginx/sites-enabled` 目錄：

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 驗證語法是否正確：

   ```bash
   nginx -t
   ```

1. 重新啟動nginx:

   ```bash
   systemctl restart nginx
   ```

### 驗證安裝

開啟Web瀏覽器並導航至網站的基URL，以 [驗證安裝](../../next-steps/verify.md)。

## CentOS 7

以下部分介紹如何使用nginx、PHP和MySQL在CentOS 7上安裝Adobe Commerce和Magento Open Source2.x。

### 安裝nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

安裝完成後，啟動nginx並將其配置為在啟動時啟動：

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

完成以下部分並安裝應用程式後，我們將使用示例配置檔案來配置nginx。

### 安裝和配置php-fpm

Adobe Commerce和Magento Open Source需要 [菲律賓比索](../php-settings.md) 功能正常的擴展。 除了這些擴展外，還必須安裝和配置 `php-fpm` 加分機。

1. 安裝 `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. 開啟 `/etc/php.ini` 的子菜單。

1. 取消注釋 `cgi.fix_pathinfo` 並將值更改為 `0`。

1. 編輯檔案以匹配以下行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >我們建議在測試Adobe Commerce或Magento Open Source時將記憶體限制設定為2 G。 請參閱 [所需的PHP設定](../php-settings.md) 的子菜單。

1. 取消對會話路徑目錄的注釋並設定路徑：

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 保存並退出編輯器。

1. 開啟 `/etc/php-fpm.d/www.conf` 編輯。

1. 編輯檔案以匹配以下行：

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 取消注釋環境行：

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. 保存並退出編輯器。

1. 建立PHP會話路徑的目錄，並將所有者更改為 `apache` 用戶和組：

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. 建立PHP會話路徑的目錄，並將所有者更改為 `apache` 用戶和組：

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. 啟動 `php-fpm` 服務並配置它在啟動時啟動：

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. 驗證 `php-fpm` 服務正在運行：

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### 安裝和配置MySQL

請參閱 [MySQL](..//database/mysql.md) 的子菜單。

### 安裝和配置

下載Adobe Commerce和Magento Open Source有幾種方法，包括：

* [獲得作曲家的暗喻](../../composer.md)

* [克隆Git儲存庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

此示例使用命令行顯示基於Composer的安裝。

1. 作為 [檔案系統所有者](../file-system/overview.md)，登錄到應用程式伺服器。

1. 更改為Web伺服器docroot目錄或您已配置為虛擬主機docroot的目錄。 在本示例中，我們使用Ubuntu預設值 `/var/www/html`。

   ```bash
   cd /var/www/html
   ```

1. 全局安裝Composer。 安裝Adobe Commerce或Magento Open Source之前，需要更新依賴關係：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Magento Open Source或Adobe Commerce元包建立Composer項目。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   在出現提示時，輸入 [身份驗證密鑰](../authentication-keys.md)。 您 _公鑰_ 是您的用戶名；你 _私鑰_ 是您的密碼。

1. 在安裝應用程式之前，設定Web伺服器組的讀寫權限。 這是必需的，以便命令行可以將檔案寫入檔案系統。

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. 從 [命令行](../../advanced.md)。 此示例假定安裝目錄的名稱 `magento2ee`，也請參見Wiki頁。 `db-host` 在同一台電腦上(`localhost`)，而且 `db-name`。 `db-user`, `db-password` 全部 `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 切換到開發模式：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 配置nginx

建議使用 `nginx.conf.sample` 安裝目錄和nginx虛擬主機中提供的配置檔案。

這些說明假定您正在為nginx虛擬主機使用CentOS預設位置(例如， `/etc/nginx/conf.d`)和預設docroot(例如， `/usr/share/nginx/html`)但是，您可以更改這些位置以適合您的環境。

1. 為您的站點建立新虛擬主機：

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. 添加以下配置：

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >的 `include` 指令必須指向安裝目錄中的示例nginx配置檔案。

1. 替換 `www.magento-dev.com` 域名。

1. 保存並退出編輯器。

1. 驗證語法是否正確：

   ```bash
   nginx -t
   ```

1. 重新啟動nginx:

   ```bash
   systemctl restart nginx
   ```

### 配置SELinux和Firewalld

預設情況下，SELinux在CentOS 7上啟用。 使用以下命令查看它是否正在運行：

```bash
sestatus
```

配置SELinux和防火牆：

1. 安裝SELinux管理工具：

   ```bash
   yum -y install policycoreutils-python
   ```

1. 運行以下命令以更改安裝目錄的安全上下文：

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. 安裝防火牆包：

   ```bash
   yum -y install firewalld
   ```

1. 啟動防火牆服務並將其配置為在啟動時啟動：

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. 運行以下命令以開啟HTTP和HTTPS的埠，以便您可以從Web瀏覽器訪問基本URL:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### 驗證安裝

開啟Web瀏覽器並導航至網站的基URL，以 [驗證安裝](../../next-steps/verify.md)。
