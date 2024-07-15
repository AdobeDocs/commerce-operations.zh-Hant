---
title: 解除安裝主題
description: 請依照下列步驟解除安裝Adobe Commerce佈景主題。
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 解除安裝主題

使用此指令之前，您必須知道佈景主題的相對路徑。 主題位於`<magento_root>/app/design/<area name>`的子目錄中。 您必須指定以區域開頭的佈景主題路徑，其為`frontend` （適用於店面佈景主題）或`adminhtml` （適用於管理佈景主題）。

例如，Adobe Commerce提供的Luma主題路徑是`frontend/Magento/luma`。

如需主題的詳細資訊，請參閱[主題結構](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/)。

## 解除安裝主題概觀

本節討論如何解除安裝一或多個主題，選擇性地包括檔案系統中的主題程式碼。 您可以先建立備份，以便稍後還原資料。

這個命令只會解除安裝`composer.json`中指定的&#x200B;*僅*&#x200B;個主題；換言之，是提供為Composer套件的主題。 如果您的佈景主題不是Composer套件，則必須透過以下方式手動解除安裝：

* 正在更新`theme.xml`中的`parent`節點資訊以移除對主題的參照。
* 正在從檔案系統移除主題程式碼。

  [主題繼承的詳細資訊](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/)。

## 解除安裝主題

命令使用方式：

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

位置

* `{theme path}`是佈景主題的相對路徑，從區域名稱開始。 例如，Adobe Commerce提供的空白佈景主題的路徑是`frontend/Magento/blank`。
* `--backup-code`會備份程式碼基底，如下面的段落所述。
* `--clear-static-content`清除產生的[靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md)，這是讓靜態檢視檔案正確顯示所必需的。

指令會執行下列工作：

1. 驗證指定的主題路徑是否存在；如果不存在，則終止指令。
1. 驗證主題是否為撰寫器套件；如果不是，則命令會終止。
1. 檢查相依性，如果有任何未滿足的相依性，則終止指令。

   若要解決此問題，您可以同時解除安裝所有主題，也可以先根據主題解除安裝。

1. 驗證主題是否未被使用；如果正在使用它，則命令終止。
1. 確認主題不是虛擬主題的基底；如果它是虛擬主題的基底，則命令終止。
1. 將商店置於維護模式。
1. 若指定`--backup-code`，請備份程式碼基底，排除`pub/static`、`pub/media`和`var`目錄。

   備份檔案名稱為`var/backups/<timestamp>_filesystem.tgz`

   您可以隨時使用[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files)命令還原備份。

1. 從`theme`資料庫資料表中移除主題。
1. 使用`composer remove`從程式碼基底移除主題。
1. 清除快取。
1. 清除產生的類別
1. 若指定`--clear-static-content`，則清除[產生的靜態檢視檔](../../configuration/cli/static-view-file-deployment.md)。

例如，如果您嘗試解除安裝另一個主題所依賴的主題，會顯示以下訊息：

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

另一種選擇是同時解除安裝兩個主題，如備份程式碼基底：

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

類似下列顯示的訊息：

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
>若要解除安裝Admin主題，您也必須從元件的相依性插入設定`<component root directory>/etc/di.xml`中移除該主題。
