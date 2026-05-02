---
title: 安裝Apache以供內部部署使用
description: 瞭解如何為內部部署Adobe Commerce安裝並設定Apache。 啟用必要的模組、重寫和'.htaccess'設定。
feature: Install, Configuration
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# 安裝Apache以供內部部署使用 {#apache}

本指南會逐步引導您安裝適用於Adobe Commerce內部部署的Apache，以及設定Commerce所需的Apache設定。 其中包含共用的Apache需求，以及Ubuntu和CentOS的作業系統特定程式。 Adobe建議遵循本指南中提供的設定指示，以保留Commerce應用程式的功能與安全性。

Adobe支援您的Adobe Commerce發行版本的[系統需求](../../system-requirements.md)中列出的Apache版本。 支援的版本因發行版本而異。 Apache還需要支援的PHP設定。 如需相關的PHP需求，請參閱[PHP設定](../php-settings.md)。

從符合您環境的區段開始：

- 如果已安裝Apache，請從[檢閱Apache需求](#review-apache-requirements)開始。
- 如果您需要在Ubuntu上安裝或升級Apache，請移至[在Ubuntu上安裝或升級Apache](#installing-or-upgrading-apache-on-ubuntu)。
- 如果您需要在CentOS上安裝Apache，請移至[在CentOS上安裝Apache](#installing-apache-on-centos)。

## 檢閱Apache需求

在託管Adobe Commerce的任何Apache伺服器上完成這些需求。

### 設定必要指示

在伺服器設定（全域）或虛擬主機設定中設定`AllowEncodedSlashes`，以避免解碼編碼斜線而導致URL發生問題。 例如，透過API在SKU中擷取斜線為的產品時，您不希望轉換斜線。 下列範例區塊尚未完成，需要其他指示。

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### 設定rewrites和.htaccess {#apache-rewrites-and-htaccess}

使用此區段來啟用Apache重寫及設定[分散式`.htaccess`檔案](https://httpd.apache.org/docs/current/howto/htaccess.html)。 Adobe Commerce使用伺服器重寫和`.htaccess`為Apache提供目錄層級的指示。

>[!IMPORTANT]
>
>無法啟用這些設定通常會導致您的店面或管理員上不顯示任何樣式。 它也能防止Apache套用`.htaccess`中定義的Adobe Commerce安全性保護。

1. 啟用Apache重寫模組：

   ```shell
   a2enmod rewrite
   ```

1. 啟用應用程式以使用分散式`.htaccess`設定檔。

   1. 在Ubuntu上編輯`/etc/apache2/sites-available/000-default.conf`。 如需其他Apache配置或需要其他引數，請參閱[Apache檔案](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)和[Apache存取控制檔案](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)。

   1. 為您計畫安裝Adobe Commerce的目錄新增或更新`AllowOverride`指令。

   例如，如果您在預設`docroot`中安裝Adobe Commerce，請將下列區塊新增至`000-default.conf`：

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >如果您從舊版Apache升級，請先在`000-default.conf`中尋找現有的`<Directory "/var/www/html">`或`<Directory "/var/www">`區塊。 如果您在不同的`docroot`中安裝Adobe Commerce，請更新該路徑的相符`<Directory>`區塊。

1. 重新啟動Apache以套用變更：

   ```shell
   service apache2 restart
   ```

### 安裝必要模組

Adobe Commerce需要安裝下列Apache模組：

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## 確認已安裝Apache

若要確認Apache已安裝並檢視目前版本，請輸入：

```shell
apache2 -v
```

結果會顯示類似下列的資訊：

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- 如果Apache *未安裝*，請參閱：
   - [在Ubuntu上安裝或升級Apache](#installing-or-upgrading-apache-on-ubuntu)
   - [在CentOS上安裝Apache](#installing-apache-on-centos)

## 在Ubuntu上安裝或升級Apache {#installing-or-upgrading-apache-on-ubuntu}

在Ubuntu上安裝和設定Apache的過程包含三個步驟：

1. 安裝軟體。
1. 啟用重寫。
1. 指定`.htaccess`指令。

設定Apache伺服器重寫時，您必須指定可在`.htaccess`中使用的指令型別，應用程式會使用這些指令來指定重寫規則和安全保護。

### 在Ubuntu上安裝Apache

1. 安裝Apache （如果尚未安裝）：

   ```shell
   apt-get -y install apache2
   ```

1. 確認安裝：

   ```shell
   apache2 -v
   ```

   類似下列的訊息會顯示以確認安裝成功：

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 繼續下一節。

   >[!NOTE]
   >
   >即使Apache預設隨附於Ubuntu，請參閱下一節以設定它。

### 在Ubuntu上升級Apache

如果已安裝Apache且您使用的版本早於`2.4`，請升級至Apache `2.4`或您已部署的Adobe Commerce版本支援的最新版本。 請參閱[系統需求](../../system-requirements.md)。

1. 更新封裝資訊：

   ```shell
   apt-get -y update
   ```

1. 如果需要，新增為環境提供支援Apache版本的存放庫。

1. 安裝或升級Apache：

   ```shell
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >如果`apt-get install`命令因未滿足的相依性而失敗，請查閱您的作業系統套件檔案或散發支援資源。

1. 確認安裝：

   ```shell
   apache2 -v
   ```

1. 在[系統需求](../../system-requirements.md)中，確認安裝的版本符合您的Adobe Commerce版本支援的版本。

1. 啟用Ubuntu[&#128279;](#enable-rewrites-and-htaccess-for-ubuntu)的重寫和`.htaccess`。

### 啟用Ubuntu的重寫和.htaccess

1. 開啟`/etc/apache2/sites-available/000-default.conf`檔案進行編輯：

   ```shell
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 找出開頭為的區塊：

   ```conf
   <Directory "/var/www/html">
   ```

1. 將`AllowOverride`的值變更為`All`。

   例如：

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. 儲存檔案並退出文字編輯器。

1. 設定Apache以使用`mod_rewrite`模組：

   ```shell
   cd /etc/apache2/mods-enabled
   ```

   ```shell
   ln -s ../mods-available/rewrite.load
   ```

1. 重新啟動Apache以套用變更：

   ```shell
   service apache2 restart
   ```

>[!IMPORTANT]
>
>無法啟用這些設定通常會導致您的店面或管理員上不顯示任何樣式。 它也能防止Apache套用`.htaccess`中定義的Adobe Commerce安全性保護。

## 在CentOS上安裝Apache {#installing-apache-on-centos}

在CentOS上安裝和設定Apache的過程分為三個步驟：

1. 安裝軟體
2. 啟用重新寫入
3. 指定`.htaccess`指令。

設定Apache伺服器重寫時，您必須指定可在`.htaccess`中使用的指令型別，應用程式會使用這些指令來指定重寫規則和安全保護。

### 安裝Apache

1. 安裝Apache （如果尚未安裝）。

   ```shell
   yum -y install httpd
   ```

1. 確認安裝：

   ```shell
   httpd -v
   ```

   類似下列的訊息會顯示以確認安裝成功：

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 繼續下一節。

   >[!NOTE]
   >
   >即使Apache預設隨附於CentOS，請參閱下一節以設定它。

### 啟用CentOS的重寫和.htaccess

1. 開啟`/etc/httpd/conf/httpd.conf`檔案進行編輯：

   ```shell
   vim /etc/httpd/conf/httpd.conf
   ```

1. 找出開頭為的區塊：

   ```conf
   <Directory "/var/www/html">
   ```

1. 將`AllowOverride`的值變更為`All`。

   例如：

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >`Order`的前述值可能並非在所有情況下都有效。 如需詳細資訊，請參閱[Apache檔案](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)。

1. 儲存檔案並退出文字編輯器。

1. 若要套用Apache設定，請重新啟動Apache。

   ```shell
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>無法啟用這些設定通常會導致您的店面或管理員上不顯示任何樣式。 它也能防止Apache套用`.htaccess`中定義的Adobe Commerce安全性保護。

## 解決403 （禁止）錯誤

如果您在嘗試存取網站時遇到403禁止錯誤，您可以更新Apache設定或虛擬主機設定，以啟用網站的訪客：

### 解決Apache的403禁止錯誤

若要讓網站訪客能夠存取您的網站，請使用[Require指示](https://httpd.apache.org/docs/2.4/howto/access.html)之一。

例如：

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>`Order`的前述值可能並非在所有情況下都有效。 如需詳細資訊，請參閱[Apache檔案](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)。
