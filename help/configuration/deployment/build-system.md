---
title: 建置系統設定
description: 瞭解如何將Commerce部署至組建系統。
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 建置系統設定

您可以有一個符合下列要求的組建系統：

- 所有Commerce程式碼都位於與開發和生產系統相同的存放庫中，並受原始檔控制
- 請確定下列所有專案都包含在原始檔控制中&#x200B;_包含_：

   - `app/etc/config.php`
   - `generated`目錄（和子目錄）
   - `pub/media`目錄
   - `pub/media/wysiwyg`目錄（和子目錄）
   - `pub/static`目錄（和子目錄）

- 必須安裝相容的PHP版本
- 必須安裝Composer
- 它已經設定檔案系統擁有權和許可權，如[您的開發、組建和生產系統的先決條件](../deployment/technical-details.md)中所述。
- 組建系統不需要安裝Commerce，但程式碼必須可供使用。

>[!WARNING]
>
>如果資料庫連線已包含在`config.php`中，則不需要資料庫連線；請參閱[匯出組態](../cli/export-configuration.md)。 否則，需要資料庫連線。

>[!INFO]
>
>組建電腦可以位於自己的主機上，或與已安裝的Commerce系統位於相同主機上。

## 設定組建電腦

以下各節將討論如何設定組建電腦。

### 安裝撰寫器

首先，檢查是否已安裝Composer：

在命令提示字元中，輸入下列任一命令：

- `composer --help`
- `composer list --help`

如果顯示命令說明，表示已經安裝Composer。

如果顯示錯誤，請使用下列步驟安裝Composer。

若要安裝Composer：

1. 在您的Commerce伺服器上變更為或建立空白目錄。

1. 輸入下列命令：

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

如需其他安裝選項，請參閱[撰寫器安裝檔案][composer]。

### 安裝PHP

在[CentOS]或[Ubuntu]上安裝PHP。

### 設定組建系統

若要設定組建系統：

1. 以檔案系統擁有者的身分登入或切換到檔案系統。
1. 從原始檔控制擷取Commerce程式碼。

   如果您使用Git，請使用下列命令：

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. 變更至Commerce根目錄並輸入：

   ```bash
   composer install
   ```

1. 等待相依性更新。
1. 設定擁有權：

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   例如，

   ```bash
   chown -R commerce-username:apache .
   ```

1. 如果您使用Git，請在文字編輯器中開啟`.gitignore`。
1. 以下各行以`#`字元開頭，以便註解：

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 將變更儲存至`.gitignore`並結束文字編輯器。
1. 如果您使用Git，請使用下列命令來確認變更：

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   如需詳細資訊，請參閱[`.gitignore`參考](../reference/config-reference-gitignore.md)。

1. 組建系統應該使用[預設模式](../bootstrap/application-modes.md#default-mode)或[開發人員模式](../bootstrap/application-modes.md#developer-mode)：

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>`為必要項。 它可以是`default`或`developer`。

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[烏本圖]: https://help.ubuntu.com/lts/serverguide/php.html
