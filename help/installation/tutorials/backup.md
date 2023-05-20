---
title: 備份和回滾檔案系統、介質和資料庫
description: 按照以下步驟備份和恢復您的Adobe Commerce或Magento Open Source應用程式。
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# 備份和回滾檔案系統、介質和資料庫

此命令使您能夠備份：

* 檔案系統(不包括 `var` 和 `pub/static` 目錄)
* 的 `pub/media` 目錄
* 資料庫

備份儲存在 `var/backups` 目錄，可隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 的子菜單。

備份後，您可以 [回退](#rollback) 再說。

>[!TIP]
>
>有關Adobe Commerce雲基礎架構項目，請參閱 [快照和備份管理](https://devdocs.magento.com/cloud/project/project-webint-snap.html) 的 _雲指南_。

## 啟用備份

預設情況下，備份功能被禁用。 要啟用，請輸入以下CLI命令：

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**棄用通知：**
>備份功能自2.1.16、2.2.7和2.3.0起已棄用。我們建議調查其他備份技術和二進位備份工具（如Percona XtraBackup）。

## 設定開啟的檔案限制

回滾到以前的備份可能會以靜默方式失敗，導致使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 的子菜單。

有時，長查詢字串會導致用戶分配的記憶體空間由於遞歸調用過多而耗盡記憶體。

## 如何設定開啟的檔案 `ulimit`

建議設定開啟的檔案 [`ulimit`](https://ss64.com/bash/ulimit.html) 檔案系統用戶的值 `65536` 或更多。

您可以在命令行上執行此操作，也可以通過編輯用戶的shell指令碼將其設定為永久設定。

在繼續之前，如果尚未執行此操作，請切換到 [檔案系統所有者](../prerequisites/file-system/overview.md)。

命令：

```bash
ulimit -s 65536
```

如果需要，可以將其更改為較大的值。

>[!NOTE]
>
>開啟檔案的語法 `ulimit` 取決於您使用的UNIX shell。 前面的設定應與CentOS和Ubuntu一起使用Bash外殼。 但是，對macOS來說，正確的設定是 `ulimit -S 65532`。 有關詳細資訊，請參閱手冊頁或作業系統引用。

要（可選）在用戶的Bash shell中設定值：

1. 如果尚未執行此操作，請切換到 [檔案系統所有者](../prerequisites/file-system/overview.md)。
1. 開啟 `/home/<username>/.bashrc` 的子菜單。
1. 添加以下行：

   ```bash
   ulimit -s 65536
   ```

1. 將更改保存到 `.bashrc` 並退出文本編輯器。

>[!WARNING]
>
>建議您避免為 [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) 的 `php.ini` 檔案，因為它可能導致不完整的回滾，且沒有失敗通知。

## 備份

命令用法：

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

該命令執行以下任務：

1. 將儲存置於維護模式。
1. 執行下列命令選項之一。

   | 選項 | 意義 | 備份檔案名和位置 |
   |--- |--- |--- |
   | `--code` | 備份檔案系統（不包括var和pub/static目錄）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | 備份pub/media目錄。 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | 備份資料庫。 | `var/backups/<timestamp>/_db.sql` |

1. 使儲存退出維護模式。

例如，要備份檔案系統和資料庫，

```bash
bin/magento setup:backup --code --db
```

類似於以下顯示的消息：

```terminal
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## 回滾

本節討論如何回滾到您以前做過的備份。 必須知道要還原的備份檔案的檔案名。

要查找備份的名稱，請輸入：

```bash
bin/magento info:backups:list
```

備份檔案名中的第一個字串是時間戳。

要回滾到上一個備份，請輸入：

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

例如，要恢復名為 `1440611839_filesystem_media.tgz`輸入

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

類似於以下顯示的消息：

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
