---
title: 阿帕奇
description: 按照以下步驟安裝和配置Apache Web伺服器，以在本地安裝Adobe Commerce和Magento Open Source。
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---

# 阿帕奇

Adobe Commerce支援Apache 2.4.x。

## Apache必需指令

1. 設定 `AllowEncodedSlashes` 在伺服器配置（全局）或虛擬主機配置中，以避免解碼可能導致URL問題的編碼斜槓。 例如，當通過API檢索SKU中帶有斜槓的產品時，您不希望轉換它。 示例塊不完整，需要其他指令。

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache重寫和htaccess

本主題討論如何啟用Apache 2.4重寫並指定 [分佈式配置檔案， `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)。

Adobe Commerce和Magento Open Source使用伺服器重寫和 `.htaccess` 提供Apache的目錄級說明。 以下說明也包含在本主題的所有其他部分中。

使用此部分可啟用Apache 2.4重寫並指定 [分佈式配置檔案， `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce和Magento Open Source使用伺服器重寫和 `.htaccess` 提供Apache的目錄級說明。

>[!NOTE]
>
>啟用這些設定失敗通常會導致在店面或管理員上不顯示樣式。

1. 啟用Apache重寫模組：

   ```bash
   a2enmod rewrite
   ```

1. 使應用程式能夠使用分佈式 `.htaccess` 配置檔案，請參閱 [Apache 2.4文檔](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)。

   >[!TIP]
   >
   >在Apache 2.4中，伺服器的預設站點配置檔案為 `/etc/apache2/sites-available/000-default.conf`。

   例如，可將以下內容添加到 `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >有時，可能需要附加參數。 有關詳細資訊，請參見 [Apache 2.4文檔](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)。

1. 如果更改了Apache設定，請重新啟動Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 如果從早期的Apache版本升級，請首先查找 `<Directory "/var/www/html">` 或 `<Directory "/var/www">` 在 `000-default.conf`。
   >- 必須更改 `AllowOverride` 指令中，指示您希望將Adobe Commerce或Magento Open Source軟體安裝到的目錄。 例如，要在Web伺服器docroot中安裝，請在中編輯該指令 `<Directory /var/www>`。


>[!NOTE]
>
>啟用這些設定失敗通常會導致樣式不顯示在店面或管理員上。

## Apache所需模組

Adobe Commerce和Magento Open Source要求安裝以下Apache模組：

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## 驗證Apache版本

要驗證您當前正在運行的Apache版本，請輸入：

```bash
apache2 -v
```

結果顯示與以下內容類似：

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- 如果Apache為 *不* 已安裝，請參閱：
   - [在Ubuntu上安裝或升級Apache](#installing-apache-on-ubuntu)
   - [在CentOS上安裝Apache](#installing-apache-on-centos)

## 在Ubuntu上安裝或升級Apache

以下各節討論如何安裝或升級Apache:

- 安裝Apache
- 升級到Ubuntu上的Apache 2.4以使用PHP 7.4。

### 在Ubuntu上安裝Apache

要安裝預設版本的Apache:

1. 安裝Apache

   ```bash
   apt-get -y install apache2
   ```

1. 驗證安裝。

   ```bash
   apache2 -v
   ```

   結果顯示與以下內容類似：

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. 啟用 [重寫 `.htaccess`](#apache-rewrites-and-htaccess)。

### 在Ubuntu上升級Apache

要升級到Apache 2.4:

1. 添加 `ppa:ondrej` 儲存庫，它包含Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. 安裝Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >如果「apt-get install」命令由於依賴項未滿足而失敗，請咨詢資源，如 [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)。

1. 驗證安裝。

   ```bash
   apache2 -v
   ```

   應顯示類似以下消息：

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. 啟用 [重寫 `.htaccess`](#apache-rewrites-and-htaccess)。

## 在CentOS上安裝Apache

Adobe Commerce和Magento Open Source要求Apache使用伺服器重寫。 還必須指定可用於的指令類型 `.htaccess`，應用程式用於指定重寫規則。

安裝和配置Apache基本上是一個三步過程：安裝軟體、啟用重寫並指定 `.htaccess` 指令。

### 安裝Apache

1. 如果尚未安裝Apache 2.4，請安裝。

   ```bash
   yum -y install httpd
   ```

1. 驗證安裝：

   ```bash
   httpd -v
   ```

   與以下顯示類似的消息，確認安裝成功：

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 繼續下一節。

   >[!NOTE]
   >
   >即使預設情況下Apache 2.4與CentOS一起提供，請參見以下部分進行配置。

### 為CentOS啟用重寫和.htaccess

1. 開啟 `/etc/httpd/conf/httpd.conf` 要編輯的檔案：

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 找到以下開頭的塊：

   ```conf
   <Directory "/var/www/html">
   ```

1. 更改 `AllowOverride` 至 `All`。

   比如說，

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
   >上面的值 `Order` 可能不會全部奏效。 有關詳細資訊，請參閱Apache文檔([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order))。

1. 保存檔案並退出文本編輯器。

1. 要應用Apache設定，請重新啟動Apache。

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>啟用這些設定失敗通常會導致在店面或管理員上不顯示樣式。

### 為Ubuntu啟用重寫和.htaccess

1. 開啟 `/etc/apache2/sites-available/default` 要編輯的檔案：

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 找到以下開頭的塊：

   `<Directory "/var/www/html">`

1. 更改 `AllowOverride` 至 `All`。

   例如：

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. 保存檔案並退出文本編輯器。

1. 將Apache配置為使用 `mod_rewrite` 模組：

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. 重新啟動Apache以應用更改：

   ```bash
   service apache2 restart
   ```

## 解決403（禁止）錯誤

如果在嘗試訪問站點時遇到403個「禁止」錯誤，則可以更新Apache配置或虛擬主機配置，以使訪問站點的人能夠：

### 解決Apache 2.4的403個禁止錯誤

要使網站訪問者能夠訪問您的網站，請使用 [需要指令](https://httpd.apache.org/docs/2.4/howto/access.html)。

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
>上面的值 `Order` 可能不會全部奏效。 有關詳細資訊，請參見 [Apache文檔](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)。
