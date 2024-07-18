---
title: 解除安裝語言套件
description: 請依照下列步驟解除安裝Adobe Commerce語言套件。
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 解除安裝語言套件

本節討論如何解除安裝一或多個語言套件，選擇性地包括檔案系統中的語言套件程式碼。 您可以先建立備份，以便稍後還原資料。

這個命令只會解除安裝`composer.json`中指定的&#x200B;*僅*&#x200B;語言套件；換句話說，會解除安裝提供為Composer套件的語言套件。 如果您的語言套件不是Composer套件，您必須從檔案系統移除語言套件程式碼，以手動方式解除安裝它。

您可以隨時使用[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files)命令還原備份。

命令使用方式：

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

語言套件解除安裝命令會執行下列工作：

1. 檢查相依性；如果是，則命令終止。

   若要解決此問題，您可以同時解除安裝所有相依的語言套件，或者先解除安裝相依的語言套件。

1. 若指定`--backup code`，請將檔案系統（不包括`var`與`pub/static`目錄）備份至`var/backups/<timestamp>_filesystem.tgz`
1. 使用`composer remove`從程式碼基底移除語言套件檔案。
1. 清除快取。

例如，如果您嘗試解除安裝其他語言套件所依賴的語言套件，會顯示下列訊息：

```
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

另一種選擇是在備份程式碼基底後解除安裝兩個語言套件：

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

類似下列顯示的訊息：

```
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
