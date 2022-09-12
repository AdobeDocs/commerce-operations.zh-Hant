---
title: Nginx
description: 請依照下列步驟，安裝並設定Nginx Web伺服器，以在本地安裝Adobe Commerce和Magento Open Source。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---


# Nginx

Adobe Commerce支援nginx 1.18(或 [最新mainline版本](https://nginx.org/en/linux_packages.html#mainline))。 您也必須安裝 `php-fpm`.

安裝說明會因您使用的作業系統而異。 請參閱 [PHP](../php-settings.md) ，以了解詳情。

## 烏邦圖

以下章節說明如何使用nginx、PHP和MySQL在Ubuntu上安裝Adobe Commerce和Magento Open Source2.x。

### 安裝nginx

```bash
sudo apt -y install nginx
```

您也可以 [從來源建置nginx](https://www.armanism.com/blog/install-nginx-on-ubuntu)

完成下列章節並安裝應用程式後，我們會使用範例設定檔案來 [配置nginx](#configure-nginx).

### 安裝和配置php-fpm

Adobe Commerce和Magento Open Source需要數個 [PHP擴充功能](../php-settings.md) 才能正常運作。 除了這些擴充功能外，您也必須安裝並設定 `php-fpm` 擴充功能（若您使用nginx）。

安裝和配置 `php-fpm`:

1. 安裝 `php-fpm` 和 `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >此命令安裝最新的可用版本PHP 7.2.X。請參閱 [系統需求](../../system-requirements.md) 的PHP版本。

1. 開啟 `php.ini` 編輯器中的檔案：

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. 編輯兩個檔案以符合下列行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >建議您在測試Adobe Commerce和Magento Open Source時，將記憶體上限設為2 G。 請參閱 [必需的PHP設定](../php-settings.md) 以取得更多資訊。

1. 儲存並退出編輯器。

1. 重新啟動 `php-fpm` 服務：

   ```bash
   systemctl restart php7.2-fpm
   ```

### 安裝和配置MySQL

請參閱 [MySQL](../database/mysql.md) 以取得更多資訊。

### 安裝和配置

有數種方式可下載Adobe Commerce和Magento Open Source，包括：

* [取得撰寫器暗喻](../../composer.md)

* [複製Git存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

此示例使用命令行顯示基於撰寫器的安裝。

1. 作為 [檔案系統所有者](../file-system/overview.md)，請登入您的應用程式伺服器。

1. 更改為Web伺服器域目錄或配置為虛擬主機域的目錄。 在此範例中，我們使用Ubuntu預設值 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. 全域安裝撰寫器。 安裝Adobe Commerce或Magento Open Source之前，必須更新相依性撰寫器：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Magento Open Source或Adobe Commerce元資料庫建立撰寫器專案。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出現提示時，請輸入 [驗證金鑰](../authentication-keys.md). 您的 _公開金鑰_ 是您的使用者名稱；您的 _私密金鑰_ 是您的密碼。

1. 在安裝應用程式之前，為Web伺服器組設定讀寫權限。 這是必需的，這樣命令行才能將檔案寫入檔案系統。

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

1. 從安裝 [命令行](../../advanced.md). 本示例假定安裝目錄為 `magento2ee`, `db-host` 在同一台電腦上(`localhost`)，以及 `db-name`, `db-user`，和 `db-password` 全部 `magento`:

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

1. 切換至開發人員模式：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 設定nginx

建議您使用 `nginx.conf.sample` 安裝目錄和nginx虛擬主機中提供的配置檔案。

這些指示假定您使用的是Ubuntu預設位置，用於nginx虛擬主機(例如， `/etc/nginx/sites-available`)和Ubuntu預設docroot(例如 `/var/www/html`)，但您可以變更這些位置以符合您的環境。

1. 為您的網站建立新的虛擬主機：

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 新增下列設定：

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
   >此 `include` 指令必須指向安裝目錄中的示例nginx配置檔案。

1. 取代 `www.magento-dev.com` 和您的網域名稱。 這必須符合您在安裝Adobe Commerce或Magento Open Source時指定的基礎URL。

1. 儲存並退出編輯器。

1. 在 `/etc/nginx/sites-enabled` 目錄：

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 確認語法正確：

   ```bash
   nginx -t
   ```

1. 重新啟動Nix:

   ```bash
   systemctl restart nginx
   ```

### 驗證安裝

開啟網頁瀏覽器，並導覽至您網站的基本URL，以 [驗證安裝](../../next-steps/verify.md).

## CentOS 7

以下章節說明如何使用nginx、PHP和MySQL在CentOS 7上安裝Adobe Commerce和Magento Open Source2.x。

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

完成下列章節並安裝應用程式後，我們將使用範例設定檔案來設定nginx。

### 安裝和配置php-fpm

Adobe Commerce和Magento Open Source需要數個 [PHP](../php-settings.md) 擴充功能可正常運作。 除了這些擴充功能外，您也必須安裝並設定 `php-fpm` 擴充功能（如果您使用nginx）。

1. 安裝 `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. 開啟 `/etc/php.ini` 檔案。

1. 取消註解 `cgi.fix_pathinfo` 行並將值變更為 `0`.

1. 編輯檔案以符合下列行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >建議您在測試Adobe Commerce或Magento Open Source時，將記憶體上限設為2 G。 請參閱 [必需的PHP設定](../php-settings.md) 以取得更多資訊。

1. 取消對會話路徑目錄的注釋並設定路徑：

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 儲存並退出編輯器。

1. 開啟 `/etc/php-fpm.d/www.conf` 編輯里。

1. 編輯檔案以符合下列行：

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 取消註解環境行：

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. 儲存並退出編輯器。

1. 建立PHP會話路徑的目錄，並將所有者更改為 `apache` 使用者和群組：

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. 建立PHP會話路徑的目錄，並將所有者更改為 `apache` 使用者和群組：

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. 啟動 `php-fpm` 服務，並將其配置為在啟動時啟動。

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. 確認 `php-fpm` 服務正在運行：

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### 安裝和配置MySQL

請參閱 [MySQL](..//database/mysql.md) 以取得更多資訊。

### 安裝和配置

有數種方式可下載Adobe Commerce和Magento Open Source，包括：

* [取得撰寫器暗喻](../../composer.md)

* [複製Git存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

此示例使用命令行顯示基於撰寫器的安裝。

1. 作為 [檔案系統所有者](../file-system/overview.md)，請登入您的應用程式伺服器。

1. 更改為Web伺服器域目錄或配置為虛擬主機域的目錄。 在此範例中，我們使用Ubuntu預設值 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. 全域安裝撰寫器。 安裝Adobe Commerce或Magento Open Source之前，必須更新相依性撰寫器：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Magento Open Source或Adobe Commerce元資料庫建立撰寫器專案。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出現提示時，請輸入 [驗證金鑰](../authentication-keys.md). 您的 _公開金鑰_ 是您的使用者名稱；您的 _私密金鑰_ 是您的密碼。

1. 在安裝應用程式之前，為Web伺服器組設定讀寫權限。 這是必需的，這樣命令行才能將檔案寫入檔案系統。

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

1. 從安裝 [命令行](../../advanced.md). 本示例假定安裝目錄為 `magento2ee`, `db-host` 在同一台電腦上(`localhost`)，以及 `db-name`, `db-user`，和 `db-password` 全部 `magento`:

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

1. 切換至開發人員模式：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 設定nginx

建議您使用 `nginx.conf.sample` 安裝目錄和nginx虛擬主機中提供的配置檔案。

這些指示假定您使用CentOS預設位置作為原始虛擬主機(例如， `/etc/nginx/conf.d`)和預設docroot(例如， `/usr/share/nginx/html`)，但您可以變更這些位置以符合您的環境。

1. 為您的網站建立新的虛擬主機：

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. 新增下列設定：

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
   >此 `include` 指令必須指向安裝目錄中的示例nginx配置檔案。

1. 取代 `www.magento-dev.com` 和您的網域名稱。

1. 儲存並退出編輯器。

1. 確認語法正確：

   ```bash
   nginx -t
   ```

1. 重新啟動Nix:

   ```bash
   systemctl restart nginx
   ```

### 配置SELinux和Firewalld

CentOS 7預設會啟用SELinux。 使用以下命令查看它是否正在運行：

```bash
sestatus
```

要配置SELinux和Firewald:

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

1. 安裝firewald套件：

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

1. 運行以下命令以開啟HTTP和HTTPS的埠，以便從Web瀏覽器訪問基本URL:

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

開啟網頁瀏覽器，並導覽至您網站的基本URL，以 [驗證安裝](../../next-steps/verify.md).
