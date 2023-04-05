---
title: 安裝 [!DNL Data Migration Tool]
description: 了解如何安裝 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# 安裝 [!DNL Data Migration Tool]

>[!INFO]
>
>Magento和 [!DNL Data Migration Tool] 必須符合。


請確定您使用 *相同發行版本* Magento2和 [!DNL Data Migration Tool]. 例如，若是Magento2.2.0版，您也必須使用 [!DNL Data Migration Tool] 2.2.0版。

## 檢查您的版本

使用下列方法來驗證您的Magento版本：

- [撰寫器](#composer-metapackage)
- [GitHub存放庫](#github-repository)

### 撰寫器暗語

如果您使用撰寫器元資料包下載了Magento軟體，請輸入以下命令：

```bash
php <magento_root>/bin/magento --version
```

### GitHub存放庫

如果您複製了Magento2 GitHub存放庫，請輸入下列命令：

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

如果您目前在 `develop` 分支，您必須變更為 [釋放分支](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 之後繼續。

如果您尚未安裝Adobe Commerce或Magento Open Source軟體， [立即安裝](../../installation/prerequisites/commerce.md).
若要複製GitHub存放庫，請務必如 [（貢獻者）複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## 尋找的發行版本 [!DNL Data Migration Tool]

前往 [版本](https://github.com/magento/data-migration-tool/releases) 頁面 [!DNL Data Migration Tool] GitHub存放庫，以尋找可用的發行版本。

## 安裝 [!DNL Data Migration Tool]

您可以安裝 [!DNL Data Migration Tool] 從：

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

安裝之前，請確定您有：

- 已完成 [先決條件](prerequisites.md) 節
- [已驗證版本](install.md#check-your-version) Magento2軟體

### 從安裝 `repo.magento.com`

若要安裝 [!DNL Data Migration Tool]，您必須更新 `composer.json` 在Magento根安裝目錄中，提供 [!DNL Data Migration Tool] 包。

1. 以 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到應用程式根目錄。
1. 輸入以下命令：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   其中 `<version>` 必須符合Magento2程式碼庫的版本。

   例如，對於2.2.0版，請輸入：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 出現提示時，請輸入 [驗證金鑰](../../installation/prerequisites/authentication-keys.md). 您的公開金鑰是您的使用者名稱；您的私密金鑰是您的密碼。

### 從GitHub安裝

如果您已複製GitHub存放庫，請依照下列步驟安裝 [!DNL Data Migration Tool].

1. 以 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到應用程式根目錄。
1. 輸入以下命令：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` 必須符合Magento2程式碼庫的版本。

   例如，對於2.2.0版，請輸入：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 檢查已安裝的版本 [!DNL Data Migration Tool]

1. 變更至 [!DNL Data Migration Tool] 目錄： `<vendor>/magento/data-migration-tool`.

1. 開啟 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) 在文字編輯器中。

1. 此 `version` 該檔案中的項目是 [!DNL Data Migration Tool].
