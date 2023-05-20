---
title: 生成系統設定
description: 瞭解如何將Commerce部署到生成系統。
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 生成系統設定

您可以擁有一個滿足以下要求的生成系統：

- 所有Commerce代碼與開發和生產系統位於同一儲存庫中，受原始碼管理
- 確保以下所有內容 _包括_ 在原始碼管理中：

   - `app/etc/config.php`
   - `generated` 目錄（和子目錄）
   - `pub/media` 目錄
   - `pub/media/wysiwyg` 目錄（和子目錄）
   - `pub/static` 目錄（和子目錄）

- 必須安裝相容的PHP版本
- 必須安裝Composer
- 它具有檔案系統所有權和權限集，如中所述 [開發、構建和生產系統的先決條件](../deployment/technical-details.md)。
- 生成系統不需要安裝Commerce，但代碼必須可用。

>[!WARNING]
>
>如果資料庫連接已包含在 `config.php`;見 [導出配置](../cli/export-configuration.md)。 否則，需要資料庫連接。

>[!INFO]
>
>生成電腦可以位於其自己的主機上，也可以位於與已安裝的Commerce系統相同的主機上。

## 配置生成電腦

以下各節討論如何配置生成電腦。

### 安裝合成器

首先，檢查是否已安裝Composer:

在命令提示符下，輸入以下任意命令：

- `composer --help`
- `composer list --help`

如果顯示命令幫助，則已安裝Composer。

如果顯示錯誤，請使用以下步驟安裝Composer。

要安裝Composer:

1. 更改到或在Commerce伺服器上建立空目錄。

1. 輸入以下命令：

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

有關其他安裝選項，請參見 [作曲家安裝文檔][composer]。

### 安裝PHP

在上安裝PHP [CentOS] 或 [烏邦圖]。

### 設定生成系統

設定生成系統：

1. 以檔案系統所有者身份或切換到檔案系統所有者身份登錄到生成系統。
1. 從原始碼管理中檢索Commerce代碼。

   如果使用Git，請使用以下命令：

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. 更改到Commerce根目錄並輸入：

   ```bash
   composer install
   ```

1. 等待相關項更新。
1. 設定所有權：

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   比如說，

   ```bash
   chown -R commerce-username:apache .
   ```

1. 如果使用Git，請開啟 `.gitignore` 的子菜單。
1. 使用 `#` 將其注釋掉的字元：

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 將更改保存到 `.gitignore` 並退出文本編輯器。
1. 如果使用Git，請使用以下命令提交更改：

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   查看 [`.gitignore` 參考](../reference/config-reference-gitignore.md) 的子菜單。

1. 生成系統應使用 [預設模式](../bootstrap/application-modes.md#default-mode) 或 [開發者模式](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` 。 它可以是 `default` 或 `developer`。

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[烏邦圖]: https://help.ubuntu.com/lts/serverguide/php.html
