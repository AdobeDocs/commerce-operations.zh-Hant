---
title: 卸載語言包
description: 按照以下步驟卸載Adobe Commerce或Magento Open Source語言包。
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# 卸載語言包

本節討論如何卸載一個或多個語言包，可選地包括檔案系統中的語言包代碼。 您可以先建立備份，以便以後恢復資料。

此命令將卸載 *僅* 在中指定的語言包 `composer.json`;換句話說，是作為Composer包提供的語言包。 如果語言包不是Composer包，則必須通過從檔案系統中刪除語言包代碼來手動卸載它。

您可以隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 的子菜單。

命令用法：

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

語言包卸載命令執行以下任務：

1. 檢查依賴項；如果是，則命令終止。

   要解決此問題，您可以同時卸載所有相關語言包，也可以先卸載相關語言包。

1. 如果 `--backup code` 指定，備份檔案系統(不包括 `var` 和 `pub/static` 目錄) `var/backups/<timestamp>_filesystem.tgz`
1. 使用 `composer remove`。
1. 清除快取。

例如，如果嘗試卸載另一語言包所依賴的語言包，則會顯示以下消息：

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

備份代碼庫後，可以卸載兩個語言包：

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

類似於以下顯示的消息：

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
