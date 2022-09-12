---
title: 備份和回滾檔案系統、介質和資料庫
description: 請依照下列步驟，備份及還原您的Adobe Commerce或Magento Open Source應用程式。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# 備份和回滾檔案系統、介質和資料庫

此命令允許您備份：

* 檔案系統(不包括 `var` 和 `pub/static` 目錄)
* 此 `pub/media` 目錄
* 資料庫

備份儲存在 `var/backups` 目錄，且可隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

備份後，您可以 [回滾](#rollback) 稍後。

>[!TIP]
>
>如需雲端基礎架構專案的Adobe Commerce，請參閱 [快照和備份管理](https://devdocs.magento.com/cloud/project/project-webint-snap.html) 在 _雲端指南_.

## 啟用備份

預設情況下禁用備份功能。 要啟用，請輸入以下CLI命令：

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**淘汰通知：**
>自2.1.16、2.2.7和2.3.0起，已棄用備份功能。我們建議調查其他備份技術和二進位備份工具（如Percona XtraBackup）。

## 設定開啟的檔案限制

回滾到以前的備份可能會無提示失敗，導致將不完整的資料寫入檔案系統或資料庫時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

有時，長查詢字串會導致使用者分配的記憶體空間因過多的遞歸呼叫而耗盡記憶體。

## 如何設定開啟的檔案 `ulimit`

建議您設定開啟的檔案 [`ulimit`](https://ss64.com/bash/ulimit.html) 檔案系統使用者的值 `65536` 或更多。

您可以在命令行上執行此操作，也可以通過編輯用戶的shell指令碼將其設定為用戶的永久設定。

繼續之前，如果尚未這麼做，請切換至 [檔案系統所有者](../prerequisites/file-system/overview.md).

命令：

```bash
ulimit -s 65536
```

您可以視需要將此值變更為較大值。

>[!NOTE]
>
>開啟檔案的語法 `ulimit` 取決於您使用的UNIX殼層。 前面的設定應與CentOS和Ubuntu搭配Bash殼層使用。 不過，對於macOS，正確的設定是 `ulimit -S 65532`. 有關詳細資訊，請參閱手冊頁或作業系統參考。

（可選）在用戶的Bash殼層中設定值：

1. 如果您尚未這麼做，請切換至 [檔案系統所有者](../prerequisites/file-system/overview.md).
1. 開啟 `/home/<username>/.bashrc` 在文字編輯器中。
1. 新增下列行：

   ```bash
   ulimit -s 65536
   ```

1. 將變更儲存至 `.bashrc` 並退出文字編輯器。

>[!WARNING]
>
>建議您避免為 [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) 在 `php.ini` 檔案，因為它可能導致回傳不完整，且沒有失敗通知。

## 備份

命令用法：

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

命令執行下列任務：

1. 將儲存置於維護模式。
1. 執行以下命令選項之一。

   | 選項 | 意義 | 備份檔案名和位置 |
   |--- |--- |--- |
   | `--code` | 備份檔案系統（不包括var和pub/static目錄）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | 備份pub/media目錄。 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | 備份資料庫。 | `var/backups/<timestamp>/_db.sql` |

1. 將儲存區帶出維護模式。

例如，要備份檔案系統和資料庫，

```bash
bin/magento setup:backup --code --db
```

顯示的訊息類似下列：

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

## 回復

本節將討論如何回滾到您以前進行的備份。 您必須知道要還原的備份檔案的檔案名。

要查找備份的名稱，請輸入：

```bash
bin/magento info:backups:list
```

備份檔案名中的第一個字串是時間戳。

要回滾到以前的備份，請輸入：

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

例如，要恢復名為 `1440611839_filesystem_media.tgz`，輸入

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

顯示的訊息類似下列：

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
