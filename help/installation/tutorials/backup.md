---
title: 備份及回覆檔案系統、媒體及資料庫
description: 請依照下列步驟備份和還原Adobe Commerce應用程式。
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# 備份及回覆檔案系統、媒體及資料庫

這個命令可讓您備份：

* 檔案系統（不包括`var`和`pub/static`目錄）
* `pub/media`目錄
* 資料庫

備份儲存在`var/backups`目錄中，並可隨時使用[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files)命令還原。

備份之後，您稍後可以[回覆](#rollback)。

>[!TIP]
>
>對於雲端基礎結構專案上的Adobe Commerce，請參閱[雲端指南](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)中的&#x200B;_快照和備份管理_。

## 啟用備份

備份功能預設為停用。 若要啟用，請輸入下列CLI命令：

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**淘汰通知：**
>&#x200B;>備份功能自2.1.16、2.2.7和2.3.0起已過時。我們建議您研究其他備份技術和二進位備份工具（例如Percona XtraBackup）。

## 設定開啟檔案限制

復原到先前的備份可能會無訊息地失敗，導致使用[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files)命令將不完整的資料寫入檔案系統或資料庫。

有時，長查詢字串會導致使用者的記憶體空間因太多遞回呼叫而用盡記憶體。

## 如何設定開啟的檔案`ulimit`

建議將檔案系統使用者的開啟檔案[`ulimit`](https://ss64.com/bash/ulimit.html)設定為`65536`或以上的值。

您可以在命令列上執行此操作，也可以透過編輯使用者的shell指令碼將其設為永久設定。

繼續之前，如果您尚未這樣做，請切換至[檔案系統擁有者](../prerequisites/file-system/overview.md)。

命令：

```bash
ulimit -s 65536
```

如有需要，可將其變更為較大的值。

>[!NOTE]
>
>開啟檔案`ulimit`的語法取決於您使用的UNIX Shell。 前面的設定應該適用於CentOS和Ubuntu以及Bash shell。 不過，對於macOS，正確的設定是`ulimit -S 65532`。 如需詳細資訊，請參閱線上手冊或作業系統參考資訊。

若要選擇設定使用者的Bash shell中的值：

1. 如果您尚未這樣做，請切換至[檔案系統擁有者](../prerequisites/file-system/overview.md)。
1. 在文字編輯器中開啟`/home/<username>/.bashrc`。
1. 新增下列行：

   ```bash
   ulimit -s 65536
   ```

1. 將變更儲存至`.bashrc`並結束文字編輯器。

>[!WARNING]
>
>建議您避免在[`pcre.recursion_limit`檔案中設定](https://www.php.net/manual/en/pcre.configuration.php)`php.ini`的值，因為這會產生未完成且沒有失敗通知的回覆。

## 備份

命令使用方式：

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

指令會執行下列工作：

1. 將商店置於維護模式。
1. 執行下列其中一個命令選項。

   | 選項 | 含義 | 備份檔案名稱和位置 |
   |--- |--- |--- |
   | `--code` | 備份檔案系統（不包括var和pub/static目錄）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | 備份pub/media目錄 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | 備份資料庫。 | `var/backups/<timestamp>/_db.sql` |

1. 將存放區帶出維護模式。

例如，若要備份檔案系統和資料庫，

```bash
bin/magento setup:backup --code --db
```

類似下列顯示的訊息：

```
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

## 回覆

本節將討論如何回覆至您先前建立的備份。 您必須知道要還原之備份檔案的檔案名稱。

若要尋找備份的名稱，請輸入：

```bash
bin/magento info:backups:list
```

備份檔案名稱中的第一個字串是時間戳記。

若要復原到先前的備份，請輸入：

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

例如，若要還原名為`1440611839_filesystem_media.tgz`的媒體備份，請輸入

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

類似下列顯示的訊息：

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
