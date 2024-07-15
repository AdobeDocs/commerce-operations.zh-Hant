---
title: 解除安裝模組
description: 請依照下列步驟解除安裝Adobe Commerce模組。
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# 解除安裝模組

本節說明如何解除安裝一或多個模組。 在解除安裝期間，您可以選擇移除模組的程式碼、資料庫架構和資料庫資料。 您可以先建立備份，以便稍後復原資料。

您必須確定不會使用模組，才可解除安裝模組。 您可以依照[啟用或停用模組](manage-modules.md)中的說明來停用模組，而不是解除安裝模組。

>[!NOTE]
>
>這個命令只會檢查在`composer.json`檔案中宣告的相依性。 如果您解除安裝在`composer.json`檔案中定義為&#x200B;_非_&#x200B;的模組，這個命令會解除安裝模組而不檢查相依性。 這個命令&#x200B;_不_，但是請從檔案系統移除模組的程式碼。 您必須使用檔案系統工具來移除模組的程式碼（例如，`rm -rf <path to module>`）。 或者，您可以[停用](manage-modules.md)非撰寫器模組。

命令使用方式：

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

其中`{ModuleName}`以`<VendorName>_<ModuleName>`格式指定模組名稱。 例如，客戶模組名稱為`Magento_Customer`。 若要取得模組名稱清單，請輸入`magento module:status`

模組解除安裝命令會執行下列工作：

1. 驗證指定的模組存在於程式碼庫中，且是撰寫器所安裝的套件。

   這個命令只對定義為Composer套件的模組運作&#x200B;_1}。_

1. 檢查與其他模組的相依性，如果有任何未滿足的相依性，則會終止指令。

   若要解決此問題，您可以同時解除安裝所有模組，也可以先解除安裝相依模組。

1. 要求確認以繼續。
1. 將商店置於維護模式。
1. 處理下列指令選項。

   | 選項 | 含義 | 備份檔案名稱和位置 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | 備份檔案系統（不包括`var`和`pub/static`目錄）。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | 備份pub/media目錄 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | 備份資料庫。 | `var/backups/<timestamp>_db.gz` |

1. 若指定`--remove-data`，請移除在模組的`Uninstall`類別中定義的資料庫結構描述和資料。

   針對要解除安裝的每個指定模組，叫用其`Uninstall`類別中的`uninstall`方法。 此類別必須繼承自[Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php)。

1. 從`setup_module`資料庫資料表中移除指定的模組。
1. 從[部署組態](../../configuration/reference/deployment-files.md)的模組清單移除指定的模組。
1. 使用`composer remove`從程式碼基底移除程式碼。

   >[!NOTE]
   >
   >解除安裝模組&#x200B;_一律_&#x200B;執行`composer remove`。 `--remove-data`選項會移除模組的`Uninstall`類別所定義的資料庫資料與結構描述。

1. 清除快取。
1. 更新產生的類別。
1. 若指定`--clear-static-content`，則清除[產生的靜態檢視檔](../../configuration/cli/static-view-file-deployment.md)。
1. 將存放區帶出維護模式。

例如，如果您嘗試解除安裝另一個模組所依賴的模組，會顯示下列訊息：

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

另一種選擇是在備份模組檔案系統、`pub/media`檔案和資料庫表格之後，解除安裝這兩個模組，但&#x200B;_不會_&#x200B;移除模組的資料庫結構描述或資料：

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

類似下列顯示的訊息：

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
>如果您嘗試解除安裝與其他模組相依的模組，則會顯示錯誤。 在這種情況下，您無法解除安裝一個模組；您必須同時解除安裝兩個模組。

## 復原檔案系統、資料庫或媒體檔案

若要將程式碼基底還原成您備份它的狀態，請使用下列指令：

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

其中`<filename>`是`<app_root>/var/backups`目錄中備份檔案的名稱。 若要顯示備份檔案清單，請輸入`magento info:backups:list`

>[!WARNING]
>
>此命令會先刪除指定的檔案或資料庫，然後再還原它們。 例如，`--media-file`選項會先刪除`pub/media`目錄下的媒體資產，再從指定的復原檔案還原。 使用此命令之前，請確定您尚未變更要保留的檔案系統或資料庫。

>[!NOTE]
>
>若要顯示可用備份檔案的清單，請輸入`magento info:backups:list`

此命令會執行下列工作：

1. 將商店置於維護模式。
1. 驗證備份檔案名稱。
1. 如果您指定程式碼復原檔案：

   a.驗證復原目的地位置是否可寫入（請注意，`pub/static`和`var`資料夾將被忽略）。

   b.刪除應用程式安裝目錄下的所有檔案和目錄。

   c.將封存檔案擷取至目的地位置。

1. 如果您指定資料庫倒回檔案：

   a.卸除整個資料庫。

   b.使用資料庫備份還原資料庫。

1. 如果您指定媒體倒回檔案：

   a.驗證倒回目的地位置是否可寫入。

   b.刪除`pub/media`下的所有檔案和目錄

   c.將封存檔案擷取至目的地位置。

1. 將存放區帶出維護模式。

例如，若要還原程式碼（亦即檔案系統）備份，請依照顯示的順序輸入下列命令：

* 顯示備份清單：

  ```bash
  magento info:backups:list
  ```

* 還原名為`1433876616_filesystem.tgz`的檔案備份：

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  類似下列顯示的訊息：

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
>若要在不變更目錄的情況下再次執行`magento`命令，您可能需要輸入`cd pwd`。
