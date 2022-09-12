---
title: 卸載語言包
description: 請依照下列步驟，解除安裝Adobe Commerce或Magento Open Source語言套件。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# 卸載語言包

本節討論如何卸載一個或多個語言包，可選地包括檔案系統中的語言包代碼。 您可以先建立備份，以便以後恢復資料。

此命令將卸載 *僅限* 在 `composer.json`;換言之，提供為 [撰寫器](https://glossary.magento.com/composer) 套件。 若您的 [語言包](https://glossary.magento.com/language-package) 不是撰寫器套件，您必須從檔案系統中移除語言套件程式碼，以手動解除安裝。

您可以隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

命令用法：

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

語言包卸載命令執行以下任務：

1. 檢查相依性；若存在，則命令終止。

   要解決此問題，您可以同時卸載所有相依語言包，也可以先卸載相依語言包。

1. 若 `--backup code` 已指定，請備份檔案系統(不包括 `var` 和 `pub/static` 目錄) `var/backups/<timestamp>_filesystem.tgz`
1. 使用從程式碼基底移除語言套件檔案 `composer remove`.
1. 清除 [快取](https://glossary.magento.com/cache).

例如，如果嘗試卸載另一個語言包所依賴的語言包，則會顯示以下消息：

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

備份程式碼基底後，其中一個替代方法是解除安裝這兩種語言套件：

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

顯示的訊息類似下列：

```terminal
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
