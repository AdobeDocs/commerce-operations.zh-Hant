---
title: 卸載主題
description: 按照以下步驟卸載Adobe Commerce或Magento Open Source主題。
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# 卸載主題

使用此命令之前，必須知道主題的相對路徑。 主題位於的子目錄中 `<magento_root>/app/design/<area name>`。 必須指定以區域開始的主題路徑，該區域為 `frontend` （用於店面主題）或 `adminhtml` （管理主題）。

例如，通向Luma主題的路徑是：Adobe Commerce和Magento Open Source `frontend/Magento/luma`。

有關主題的詳細資訊，請參見 [主題結構](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/)。

## 卸載主題概述

本節討論如何卸載一個或多個主題，可選地包括檔案系統中的主題代碼。 您可以先建立備份，以便以後恢復資料。

此命令將卸載 *僅* 指定的主題 `composer.json`;換句話說，作為Composer包提供的主題。 如果主題不是Composer包，則必須通過以下方式手動卸載它：

* 更新 `parent` 節點資訊 `theme.xml` 的子菜單。
* 正在從檔案系統中刪除主題代碼。

   [有關主題繼承的詳細資訊](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/)。

## 卸載主題

命令用法：

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

位置

* `{theme path}` 是主題的相對路徑，以區域名稱開頭。 例如，隨Adobe Commerce和Magento Open Source提供的空白主題的路徑是 `frontend/Magento/blank`。
* `--backup-code` 備份下面各段中討論的代碼庫。
* `--clear-static-content` 已清除 [靜態視圖檔案](../../configuration/cli/static-view-file-deployment.md)，這是使靜態視圖檔案正確顯示所必需的。

該命令執行以下任務：

1. 驗證指定的主題路徑是否存在；否則，命令將終止。
1. 驗證主題是否為Composer包；否則，命令將終止。
1. 檢查依賴項，如果存在任何未滿足的依賴項，則終止命令。

   要解決此問題，您可以同時卸載所有主題，也可以先卸載取決於主題的主題。

1. 驗證主題是否未被使用；如果正在使用，則命令將終止。
1. 驗證主題是否不是虛擬主題的基礎；如果它是虛擬主題的基，則命令將終止。
1. 將儲存置於維護模式。
1. 如果 `--backup-code` 指定，備份代碼庫，不包括 `pub/static`。 `pub/media`, `var` 的子菜單。

   備份檔案名為 `var/backups/<timestamp>_filesystem.tgz`

   您可以隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 的子菜單。

1. 從 `theme` 資料庫表。
1. 使用 `composer remove`。
1. 清除快取。
1. 清除生成的類
1. 如果 `--clear-static-content` 指定，清除 [生成的靜態視圖檔案](../../configuration/cli/static-view-file-deployment.md)。

例如，如果嘗試卸載另一個主題所依賴的主題，將顯示以下消息：

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

另一種方法是同時卸載這兩個主題，如備份代碼庫：

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

類似於以下顯示的消息：

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
>要卸載管理主題，還必須從元件的依賴項注入配置中刪除它， `<component root directory>/etc/di.xml`。
