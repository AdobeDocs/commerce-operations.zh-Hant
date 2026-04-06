---
title: 安裝內部部署的Nginx
description: 瞭解如何為內部部署Adobe Commerce安裝並設定Nginx網頁伺服器。 設定PHP-FPM和您的虛擬主機。
feature: Install, Configuration
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# 安裝Nginx以供內部部署使用 {#nginx}

本指南會逐步引導您安裝適用於Adobe Commerce內部部署的Nginx，以及設定Commerce所需的Nginx設定。 它包括Ubuntu和CentOS的作業系統特定程式，以及設定PHP-FPM的指南。 Adobe建議遵循本指南中提供的設定指示，以保留Commerce應用程式的功能與安全性。

Adobe支援Adobe Commerce發行版本之[系統需求](../../system-requirements.md)中列出的Nginx版本。 支援的版本因發行版本而異。 Nginx也需要支援的PHP-FPM組態。 如需相關的PHP需求，請參閱[PHP](../php-settings.md)。

## 安裝在Ubuntu上

使用本節在Ubuntu上安裝Adobe Commerce搭配Nginx、PHP和MySQL。

### 安裝Nginx

```bash
sudo apt -y install nginx
```

您也可以[從來源](https://www.armanism.com/blog/install-nginx-on-ubuntu)建置Nginx。

完成下列章節並安裝應用程式之後，請使用範例組態檔來[設定Nginx](#configure-nginx)。 此建議的設定同時保留Commerce應用程式的功能與安全性。

### 安裝和配置PHP-FPM

Adobe Commerce需要多個[PHP擴充功能](../php-settings.md)才能正常運作。 除了這些擴充功能之外，如果您使用Nginx，您也必須安裝並設定`php-fpm`擴充功能。

若要安裝和設定`php-fpm`：

1. 安裝Adobe Commerce發行版本支援的PHP版本的`php-fpm`和`php-cli`套件。 在Ubuntu上，套件名稱通常遵循以下模式：

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >將`<php-version>`取代為您正在安裝的Adobe Commerce發行版本的[系統需求](../../system-requirements.md)中所列出的支援PHP次要版本。 在下列步驟中，在檔案路徑、服務名稱和通訊端路徑中使用相同的值。

1. 在編輯器中開啟`php.ini`檔案：

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. 編輯這兩個檔案以符合以下行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe建議在測試Adobe Commerce時將記憶體限制設為2 GB。 如需詳細資訊，請參閱[必要的PHP設定](../php-settings.md)。

1. 儲存並退出編輯器。

1. 重新啟動`php-fpm`服務：

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### 安裝及設定MySQL

如需詳細資訊，請參閱[MySQL](../database/mysql.md)。

### 安裝Adobe Commerce

您可以透過數種方式下載Adobe Commerce：

* [取得Composer中繼資料](../../composer.md)

* [複製Git存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

此範例顯示使用命令列的Composer型安裝。

1. 以[檔案系統擁有者](../file-system/overview.md)的身分，登入您的應用程式伺服器。

1. 變更至Web伺服器docroot目錄，或您設定為虛擬主機docroot的目錄。 在此範例中，我們使用Ubuntu預設值`/var/www/html`。

   ```bash
   cd /var/www/html
   ```

1. 全域安裝撰寫器。 安裝Adobe Commerce之前需要撰寫器更新相依性：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Adobe Commerce中繼資料建立撰寫器專案。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出現提示時，請輸入您的[驗證金鑰](../authentication-keys.md)。 您的&#x200B;_公開金鑰_&#x200B;是您的使用者名稱；_私密金鑰_&#x200B;是您的密碼。

1. 安裝應用程式之前，請先設定網頁伺服器群組的讀寫許可權。 這是必要的，以便命令列可以將檔案寫入檔案系統。

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

1. 從[命令列](../../advanced.md)安裝。 此範例假設安裝目錄名為`magento2ee`，且資料庫主機位於相同電腦(`localhost`)：

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >使用您正在安裝的Adobe Commerce發行版本所需的`--search-engine`值和相符的主機/連線埠選項。 若是2.4.6之前的版本，請搭配使用`elasticsearch7`與Elasticsearch 7或OpenSearch的`--elasticsearch-*`選項。 若是2.4.6版或更新版本，請使用該版本支援的搜尋引擎值和對應的CLI選項。

1. 切換到開發人員模式：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 設定Nginx

Adobe建議使用安裝目錄中提供的`nginx.conf.sample`設定檔和您的Nginx虛擬主機設定，以保留Commerce應用程式的功能與安全性。

>[!IMPORTANT]
>
>`nginx.conf.sample`檔案提供必要的應用程式路由以及安全性強化規則。 例如，它會限制執行上傳至伺服器的有害指令碼。 如果您未使用此檔案或修改其規則，則您有責任在您的自訂nginx設定中實作相同的安全性控制項。

這些指示假設您正在使用Nginx虛擬主機的Ubuntu預設位置（例如`/etc/nginx/sites-available`）和Ubuntu預設docroot （例如`/var/www/html`）。 您可以變更這些位置以符合您的環境。

1. 為您的網站建立新的虛擬主機：

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 新增下列設定：

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
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
   >`include`指示詞必須指向安裝目錄中的範例nginx組態檔。

1. 將`www.magento-dev.com`取代為您的網域名稱。 這必須符合您在安裝Adobe Commerce時指定的基底URL。

1. 儲存並退出編輯器。

1. 在`/etc/nginx/sites-enabled`目錄中建立新建立的虛擬主機的symlink以啟動它：

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 請確認語法正確：

   ```bash
   nginx -t
   ```

1. 重新啟動Nginx：

   ```bash
   systemctl restart nginx
   ```

### 驗證安裝

若要驗證安裝，請開啟網頁瀏覽器，並導覽至您網站的基底URL。 如需詳細資訊，請參閱[驗證安裝](../../next-steps/verify.md)。

## 在CentOS 7上安裝

使用本節將Adobe Commerce安裝在具有Nginx、PHP和MySQL的CentOS 7上。

### 安裝Nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

安裝完成後，請啟動nginx並將它設定為在開機時啟動：

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

完成下列各節並安裝應用程式後，請使用範例組態檔來設定Nginx。

### 安裝和配置PHP-FPM

Adobe Commerce需要多個[PHP](../php-settings.md)擴充功能才能正常運作。 除了這些擴充功能之外，如果您使用Nginx，您也必須安裝並設定`php-fpm`擴充功能。

1. 安裝`php-fpm`：

   ```bash
   yum -y install <php-fpm-package>
   ```

1. 在編輯器中開啟`/etc/php.ini`檔案。

   >[!NOTE]
   >
   >安裝為要安裝的Adobe Commerce發行版本所支援的PHP版本提供`php-fpm`的套件。 套件名稱會因存放庫和作業系統而異。 請參閱[系統需求](../../system-requirements.md)。

1. 取消註解`cgi.fix_pathinfo`行並將值變更為`0`。

1. 編輯檔案以符合下列各行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe建議在測試Adobe Commerce時將記憶體限制設為2 GB。 如需詳細資訊，請參閱[必要的PHP設定](../php-settings.md)。

1. 取消註解工作階段路徑目錄並設定路徑：

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 儲存並退出編輯器。

1. 在編輯器中開啟`/etc/php-fpm.d/www.conf`。

1. 編輯檔案以符合下列各行：

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 取消環境行的註解：

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. 儲存並退出編輯器。

1. 為PHP工作階段路徑建立目錄，並將擁有者變更為`nginx`使用者和群組：

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. 為PHP-FPM通訊端建立目錄，並將擁有者變更為`nginx`使用者和群組：

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
   ```

1. 啟動`php-fpm`服務，並將它設定為在開機時啟動：

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. 驗證`php-fpm`服務是否正在執行：

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### 安裝及設定MySQL

如需詳細資訊，請參閱[MySQL](../database/mysql.md)。

### 安裝Adobe Commerce

您可以透過數種方式下載Adobe Commerce：

* [取得Composer中繼資料](../../composer.md)

* [複製Git存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

此範例顯示使用命令列的Composer型安裝。

1. 以[檔案系統擁有者](../file-system/overview.md)的身分，登入您的應用程式伺服器。

1. 變更至Web伺服器docroot目錄，或您設定為虛擬主機docroot的目錄。 在此範例中，使用CentOS預設值`/usr/share/nginx/html`。

   ```bash
   cd /usr/share/nginx/html
   ```

1. 全域安裝撰寫器。 安裝Adobe Commerce之前需要撰寫器更新相依性：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Adobe Commerce中繼資料建立撰寫器專案。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出現提示時，請輸入您的[驗證金鑰](../authentication-keys.md)。 您的&#x200B;_公開金鑰_&#x200B;是您的使用者名稱；_私密金鑰_&#x200B;是您的密碼。

1. 安裝應用程式之前，請先設定網頁伺服器群組的讀寫許可權。 這是必要的，以便命令列可以將檔案寫入檔案系統。

   ```bash
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. 從[命令列](../../advanced.md)安裝。 此範例假設安裝目錄名為`magento2ee`，且資料庫主機位於相同電腦(`localhost`)：

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 切換到開發人員模式：

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 設定Nginx

我們建議使用安裝目錄中的`nginx.conf.sample`檔案以及您的Nginx虛擬主機組態來設定Nginx。

>[!IMPORTANT]
>
>`nginx.conf.sample`檔案提供必要的應用程式路由以及安全性強化規則。 例如，它會限制執行上傳至伺服器的有害指令碼。 如果您未使用此檔案或修改其規則，則您有責任在您的自訂nginx設定中實作相同的安全性控制項。

這些指示假設您正在使用Nginx虛擬主機的CentOS預設位置，例如`/etc/nginx/conf.d`，以及預設docroot，例如`/usr/share/nginx/html`。 您可以變更這些位置以符合您的環境。

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
   >`include`指示詞必須指向安裝目錄中的範例nginx組態檔。

1. 將`www.magento-dev.com`取代為您的網域名稱。

1. 儲存並退出編輯器。

1. 請確認語法正確：

   ```bash
   nginx -t
   ```

1. 重新啟動Nginx：

   ```bash
   systemctl restart nginx
   ```

### 設定SELinux和firewalld

CentOS 7預設啟用SELinux。 使用以下命令確認它正在執行：

```bash
sestatus
```

若要設定SELinux與firewald：

1. 安裝SELinux管理工具：

   ```bash
   yum -y install policycoreutils-python
   ```

1. 執行以下命令來變更安裝目錄的安全性內容：

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

1. 安裝防火牆套件：

   ```bash
   yum -y install firewalld
   ```

1. 啟動防火牆服務，並將它設定為在開機時啟動：

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. 執行以下命令來開啟HTTP和HTTPS的連線埠，以便您可以從網頁瀏覽器存取基本URL：

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

若要驗證安裝，請開啟網頁瀏覽器，並導覽至您網站的基底URL。 如需詳細資訊，請參閱[驗證安裝](../../next-steps/verify.md)。
