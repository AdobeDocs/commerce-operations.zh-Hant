---
title: 卸載模組
description: 請依照下列步驟，解除安裝Adobe Commerce或Magento Open Source模組。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---


# 卸載模組

本節將討論如何卸載一個或多個模組。 在卸載期間，您可以選擇刪除模組的代碼、資料庫架構和資料庫資料。 您可以先建立備份，以便以後恢復資料。

只有在您確定不會使用模組時，才應解除安裝模組。 您可以停用模組，而不是解除安裝模組，如 [啟用或禁用模組](manage-modules.md).

>[!NOTE]
>
>此命令僅檢查 `composer.json` 檔案。 如果您解除安裝 [模組](https://glossary.magento.com/module) 是 _not_ 在 `composer.json` 檔案中，此命令將卸載該模組，而不檢查相依性。 此命令可 _not_&#x200B;但是，請從檔案系統中移除模組的程式碼。 您必須使用檔案系統工具來移除模組的程式碼(例如 `rm -rf <path to module>`)。 另外，您可以 [disable](manage-modules.md) 非撰寫器模組。

命令用法：

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

其中 `{ModuleName}` 在中指定模組名稱 `<VendorName>_<ModuleName>` 格式。 例如，客戶模組名稱為 `Magento_Customer`. 若要取得模組名稱清單，請輸入 `magento module:status`

模組卸載命令執行以下任務：

1. 驗證指定的模組是否存在於代碼庫中，並且由 [撰寫器](https://glossary.magento.com/composer).

   此命令有效 _僅限_ 模組定義為撰寫器套件。

1. 檢查與其他模組的依賴關係，並在存在未滿足的依賴關係時終止命令。

   要解決此問題，您可以同時卸載所有模組，也可以先卸載相依模組。

1. 請求確認以繼續。
1. 將儲存置於維護模式。
1. 處理以下命令選項。

   | 選項 | 意義 | 備份檔案名和位置 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | 備份檔案系統(不包括 `var` 和 `pub/static` 目錄)。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | 備份pub/media目錄。 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | 備份資料庫。 | `var/backups/<timestamp>_db.gz` |

1. 若 `--remove-data` 已指定，請刪除模組中定義的資料庫架構和資料 `Uninstall` 類別。

   對於要卸載的每個指定模組，請調用 `uninstall` 方法 `Uninstall` 類別。 此類必須繼承 [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. 從 `setup_module` 資料庫表。
1. 從 [部署配置](../../configuration/reference/deployment-files.md).
1. 從程式碼基底移除程式碼，使用 `composer remove`.

   >[!NOTE]
   >
   >解除安裝模組 _always_ 執行 `composer remove`. 此 `--remove-data` 選項刪除由模組 `Uninstall` 類別。

1. 清除 [快取](https://glossary.magento.com/cache).
1. 更新生成的類。
1. 若 `--clear-static-content` 指定時清除 [生成的靜態視圖檔案](../../configuration/cli/static-view-file-deployment.md).
1. 將儲存區帶出維護模式。

例如，如果嘗試卸載另一個模組所依賴的模組，則會顯示以下消息：

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

備份模組檔案系統後卸載兩個模組， `pub/media` 檔案和資料庫表，但 _not_ 移除模組的 [資料庫模式](https://glossary.magento.com/database-schema) 或資料：

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

顯示的訊息類似下列：

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>如果嘗試卸載依賴於其他模組的模組，則會顯示錯誤。 在這種情況下，無法卸載一個模組；您必須同時解除安裝兩者。

## 回滾檔案系統、資料庫或媒體檔案

要將代碼庫還原為備份該代碼庫的狀態，請使用以下命令：

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

其中 `<filename>` 是 `<app_root>/var/backups` 目錄。 要顯示備份檔案的清單，請輸入 `magento info:backups:list`

>[!WARNING]
>
>此命令在還原指定的檔案或資料庫之前刪除它們。 例如， `--media-file` 選項會刪除 `pub/media` 從指定的回滾檔案還原之前的目錄。 使用此命令之前，請確保未更改要保留的檔案系統或資料庫。

>[!NOTE]
>
>要顯示可用備份檔案的清單，請輸入 `magento info:backups:list`

此命令執行以下任務：

1. 將儲存置於維護模式。
1. 驗證備份檔案名。
1. 如果指定代碼回滾檔案：

   a.驗證回滾目標位置是否可寫(請注意 `pub/static` 和 `var` 會忽略資料夾)。

   b.刪除應用程式安裝目錄下的所有檔案和目錄。

   c.將存檔檔案提取到目標位置。

1. 如果指定資料庫回滾檔案：

   a.刪除整個資料庫。

   b.使用資料庫備份還原資料庫。

1. 如果指定介質回滾檔案：

   a.驗證回滾目標位置是否可寫。

   b.刪除下面的所有檔案和目錄 `pub/media`

   c.將存檔檔案提取到目標位置。

1. 將儲存區帶出維護模式。

例如，要恢復代碼（即檔案系統）備份，請按照以下順序輸入以下命令：

* 顯示備份清單：

   ```bash
   magento info:backups:list
   ```

* 還原名為的檔案備份 `1433876616_filesystem.tgz`:

   ```bash
   magento setup:rollback --code-file="1433876616_filesystem.tgz"
   ```

   顯示的訊息類似下列：

   ```terminal
   Enabling maintenance mode
   Code rollback is starting ...
   Code rollback filename: 1433876616_filesystem.tgz
   Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
   [SUCCESS]: Code rollback has completed successfully.
   Disabling maintenance mode
   ```

>[!NOTE]
>
>若要執行 `magento` 命令，而不更改目錄，則可能需要輸入 `cd pwd`.
