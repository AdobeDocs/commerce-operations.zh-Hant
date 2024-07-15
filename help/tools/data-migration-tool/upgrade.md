---
title: 升級 [!DNL Data Migration Tool]
description: 瞭解如何升級 [!DNL Data Migration Tool] 以在Magento1和Magento2之間傳輸資料。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 升級[!DNL Data Migration Tool]

若要確定您目前的Magento2安裝版本與[!DNL Data Migration Tool]完全相符，您可能需要升級工具。

## 必要條件

升級[!DNL Data Migration Tool]之前，您必須：

* 升級您的Magento軟體以取得最新版本

* 備份`vendor/magento/data-migration-tool`目錄

* 確定[!DNL Data Migration Tool]版本符合Magento應用程式版本

### 升級您的Magento軟體

如果您尚未升級，請[升級Magento軟體](../../upgrade/overview.md)。

### 備份`vendor/magento/data-migration-tool`目錄

升級[!DNL Data Migration Tool]之前，請至少備份`vendor/magento/data-migration-tool`目錄。 在升級期間，它可能會被刪除並由更新的程式碼取代。

您也可以使用下列指令來備份整個Magento程式碼基底和資料庫：

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>`vendor/magento/data-migration-tool`目錄包含您的自訂程式碼。 若未進行備份，升級期間可能會遺失自訂內容。


### 確定版本相符

[!DNL Data Migration Tool]和您的Magento軟體的版本必須完全相符。 例如，Magento2.1.2需要[!DNL Data Migration Tool]的2.1.2版。

請參閱[安裝 [!DNL Data Migration Tool]](install.md)主題，瞭解如何：

* [檢查](install.md#check-your-version)您的Magento2版本

* [尋找[!DNL Data Migration Tool]的](install.md#find-released-versions-of-data-migration-tool)發行版本

* [檢查](install.md#check-version-of-installed-data-migration-tool) [!DNL Data Migration Tool]版本

## 升級[!DNL Data Migration Tool]

1. 以[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)身分登入您的應用程式伺服器，或切換至。
1. 變更至應用程式根目錄。
1. 輸入下列命令：

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   其中`<version>`必須符合Magento2程式碼基底的版本。

   例如，對於2.1.2版，請輸入：

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 等待命令完成。
