---
title: 升級 [!DNL Data Migration Tool]
description: 了解如何升級 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# 升級 [!DNL Data Migration Tool]

若要確認您目前Magento2的版本安裝，以及 [!DNL Data Migration Tool] 完全符合，您可能需要升級工具。

## 必要條件

升級之前 [!DNL Data Migration Tool]，您必須：

* 升級您的Magento軟體以取得最新版本

* 備份 `vendor/magento/data-migration-tool` 目錄

* 請確定 [!DNL Data Migration Tool] 版本符合Magento應用程式版本

### 升級您的Magento軟體

如果你還沒做， [升級Magento軟體](../../upgrade/overview.md).

### 備份 `vendor/magento/data-migration-tool` 目錄

升級之前 [!DNL Data Migration Tool]，至少備份 `vendor/magento/data-migration-tool` 目錄。 在升級期間，可將其刪除，並由更新的程式碼取代。

您也可以使用以下命令備份整個Magento代碼庫和資料庫：

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>此 `vendor/magento/data-migration-tool` 目錄包含您的自訂程式碼。 如果無法備份，表示在升級期間，您可能會丟失自定義。


### 確認版本符合

版本 [!DNL Data Migration Tool] 而您的Magento軟體必須完全匹配。 例如，Magento2.1.2需使用2.1.2版 [!DNL Data Migration Tool].

請參閱 [安裝 [!DNL Data Migration Tool]](install.md) 主題，了解如何：

* [檢查](install.md#check-your-version) 您的Magento2版

* [查找](install.md#find-released-versions-of-data-migration-tool) 發行版本 [!DNL Data Migration Tool]

* [檢查](install.md#check-version-of-installed-data-migration-tool) the [!DNL Data Migration Tool] 版本

## 升級 [!DNL Data Migration Tool]

1. 以或切換到的方式登錄到應用伺服器， [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到應用程式根目錄。
1. 輸入以下命令：

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` 必須符合Magento2程式碼庫的版本。

   例如，對於2.1.2版，請輸入：

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 命令完成後等待。
