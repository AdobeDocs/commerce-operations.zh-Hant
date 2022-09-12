---
title: 卸載主題
description: 請依照下列步驟，解除安裝Adobe Commerce或Magento Open Source主題。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# 卸載主題

使用此命令之前，您必須知道主題的相對路徑。 主題位於的子目錄中 `<magento_root>/app/design/<area name>`. 您必須指定以區域開頭的主題路徑，該區域為 `frontend` （用於店面主題）或 `adminhtml` ( [管理](https://glossary.magento.com/magento-admin) 主題)。

例如，Luma的路徑 [主題](https://glossary.magento.com/theme) 隨附Adobe Commerce和Magento Open Source `frontend/Magento/luma`.

如需主題的詳細資訊，請參閱 [主題結構](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## 卸載主題概述

本節將討論如何卸載一個或多個主題，可選地包括檔案系統中的主題代碼。 您可以先建立備份，以便以後恢復資料。

此命令將卸載 *僅限* 在 `composer.json`;換言之，以 [撰寫器](https://glossary.magento.com/composer) 套件。 如果您的主題不是撰寫器套件，則必須透過以下方式手動解除安裝：

* 更新 `parent` 節點資訊 `theme.xml` 移除主題的參考。
* 正在從檔案系統中刪除主題代碼。

   [主題繼承的詳細資訊](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## 卸載主題

命令用法：

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

其中

* `{theme path}` 是主題的相對路徑，從區域名稱開始。 例如，隨Adobe Commerce和Magento Open Source提供之空白主題的路徑為 `frontend/Magento/blank`.
* `--backup-code` 備份代碼庫，如後面各段所述。
* `--clear-static-content` 已生成的 [靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md)，這是導致靜態檢視檔案正確顯示的必要條件。

命令執行下列任務：

1. 驗證指定的主題路徑是否存在；若非如此，則命令會終止。
1. 驗證主題是否為撰寫器套件；若非如此，則命令會終止。
1. 檢查相依性，並在有任何未滿足的相依性時終止命令。

   若要解決此問題，您可以同時解除安裝所有主題，或先根據主題解除安裝。

1. 驗證主題是否未被使用；如果正在使用它，則命令將終止。
1. 驗證主題不是虛擬主題的基礎；如果它是虛擬主題的基礎，則命令將終止。
1. 將儲存置於維護模式。
1. 若 `--backup-code` 已指定，請備份代碼庫，排除 `pub/static`, `pub/media`，和 `var` 目錄。

   備份檔案名為 `var/backups/<timestamp>_filesystem.tgz`

   您可以隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

1. 從 `theme` 資料庫表。
1. 使用從程式碼基底移除主題 `composer remove`.
1. 清除 [快取](https://glossary.magento.com/cache).
1. 清除生成的類
1. 若 `--clear-static-content` 指定時清除 [生成的靜態視圖檔案](../../configuration/cli/static-view-file-deployment.md).

例如，如果您嘗試解除安裝另一個主題所依賴的主題，會顯示下列訊息：

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

另一種方法是同時卸載兩個主題，如下所示，備份代碼庫：

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

顯示的訊息類似下列：

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>若要解除安裝 [管理](https://glossary.magento.com/admin) 主題，您也必須將其從元件的 [依賴注入](https://glossary.magento.com/dependency-injection) 配置， `<component root directory>/etc/di.xml`.
