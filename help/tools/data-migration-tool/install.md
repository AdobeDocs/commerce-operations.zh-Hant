---
title: 安裝 [!DNL Data Migration Tool]
description: 瞭解如何安裝 [!DNL Data Migration Tool] 以在Magento 1和Magento 2之間傳輸資料。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# 安裝[!DNL Data Migration Tool]

>[!INFO]
>
>Magento和[!DNL Data Migration Tool]的版本必須相符。


請確定您同時使用Magento 2和&#x200B;*的*&#x200B;相同發行版本[!DNL Data Migration Tool]。 例如，對於Magento 2.2.0版，您也必須使用[!DNL Data Migration Tool] 2.2.0版。

## 檢查您的版本

使用下列其中一種方法來驗證您的Magento版本：

- [作曲者](#composer-metapackage)
- [GitHub存放庫](#github-repository)

### Composer中繼資料

如果您使用Composer中繼資料下載Magento軟體，請輸入下列命令：

```bash
php <magento_root>/bin/magento --version
```

### GitHub存放庫

如果您複製Magento 2 GitHub存放庫，請輸入下列命令：

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

如果您目前在`develop`分支中，您必須變更為[已發行分支](https://developer.adobe.com/commerce/contributor/guides/install/change-version/)，才能繼續。

如果您尚未安裝Adobe Commerce軟體，請[立即安裝](../../installation/prerequisites/commerce.md)。
如果您正在複製GitHub存放庫，請務必取出版本標籤，如[&#x200B; （參與者）複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)中所述。

## 尋找[!DNL Data Migration Tool]的發行版本

前往[&#x200B; GitHub存放庫的](https://github.com/magento/data-migration-tool/releases)版本[!DNL Data Migration Tool]頁面以尋找可用的發行版本。

## 安裝[!DNL Data Migration Tool]

您可以從以下位置安裝[!DNL Data Migration Tool]：

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

安裝之前，請確定您擁有：

- 已完成[先決條件](prerequisites.md)區段中提及的所有工作
- [已驗證Magento 2軟體的版本](install.md#check-your-version)

### 從`repo.magento.com`安裝

若要安裝[!DNL Data Migration Tool]，您必須更新Magento根安裝目錄中的`composer.json`，以提供[!DNL Data Migration Tool]套件的位置。

1. 以或切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)的身份登入您的應用程式伺服器。
1. 變更至應用程式根目錄。
1. 輸入下列命令：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   其中`<version>`必須符合Magento 2程式碼基底的版本。

   例如，對於2.2.0版，輸入：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 出現提示時，請輸入您的[驗證金鑰](../../installation/prerequisites/authentication-keys.md)。 您的公開金鑰是您的使用者名稱；您的私密金鑰是您的密碼。

### 從GitHub安裝

如果您已複製GitHub存放庫，請依照下列步驟安裝[!DNL Data Migration Tool]。

1. 以或切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)的身份登入您的應用程式伺服器。
1. 變更至應用程式根目錄。
1. 輸入下列命令：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   其中`<version>`必須符合Magento 2程式碼基底的版本。

   例如，對於2.2.0版，輸入：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 檢查已安裝的[!DNL Data Migration Tool]版本

1. 變更至您的[!DNL Data Migration Tool]目錄： `<vendor>/magento/data-migration-tool`。

1. 在文字編輯器中開啟[`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json)。

1. 該檔案中的`version`專案是[!DNL Data Migration Tool]的版本。
