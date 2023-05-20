---
title: 安裝 [!DNL Data Migration Tool]
description: 瞭解如何安裝 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# 安裝 [!DNL Data Migration Tool]

>[!INFO]
>
>Magento和 [!DNL Data Migration Tool] 必須匹配。


確保您正在使用 *同一已發佈版本* Magento2和 [!DNL Data Migration Tool]。 例如，對於Magento2.2.0版，您還必須使用 [!DNL Data Migration Tool] 2.2.0版。

## 檢查您的版本

使用以下方法驗證您的Magento版本：

- [作曲家](#composer-metapackage)
- [GitHub儲存庫](#github-repository)

### 作曲家集合

如果使用Composer元包下載了Magento軟體，請輸入以下命令：

```bash
php <magento_root>/bin/magento --version
```

### GitHub儲存庫

如果克隆了Magento2 GitHub儲存庫，請輸入以下命令：

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

如果您當前在 `develop` 分支，必須更改為 [釋放分支](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 才能繼續。

如果您尚未安裝Adobe Commerce或Magento Open Source軟體， [立即安裝](../../installation/prerequisites/commerce.md)。
如果要克隆GitHub儲存庫，請確保簽出釋放標籤，如中所述 [（參與者）克隆GitHub儲存庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)。

## 查找已發佈版本 [!DNL Data Migration Tool]

轉到 [發行](https://github.com/magento/data-migration-tool/releases) 的 [!DNL Data Migration Tool] GitHub儲存庫，以查找可用的已發佈版本。

## 安裝 [!DNL Data Migration Tool]

您可以安裝 [!DNL Data Migration Tool] 從：

- [&#39;repo.magento.com](#install-from-repomagentocom)
- [GitHub](#install-from-github)

在安裝之前，請確保：

- 已完成中提及的所有任務 [先決條件](prerequisites.md) 節
- [已驗證版本](install.md#check-your-version) Magento2軟體

### 從 `repo.magento.com`

安裝 [!DNL Data Migration Tool]，必須更新 `composer.json` Magento根安裝目錄中，提供 [!DNL Data Migration Tool] 檔案。

1. 以或切換到的應用程式伺服器 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 更改到應用程式根目錄。
1. 輸入以下命令：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   位置 `<version>` 必須與Magento2代碼庫的版本匹配。

   例如，對於2.2.0版，請輸入：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 在出現提示時，輸入 [身份驗證密鑰](../../installation/prerequisites/authentication-keys.md)。 您的公鑰是您的用戶名；你的私鑰是你的密碼。

### 從GitHub安裝

如果已克隆了GitHub儲存庫，請按照以下步驟安裝 [!DNL Data Migration Tool]。

1. 以或切換到的應用程式伺服器 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 更改到應用程式根目錄。
1. 輸入以下命令：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   何處 `<version>` 必須與Magento2代碼庫的版本匹配。

   例如，對於2.2.0版，請輸入：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 檢查已安裝的版本 [!DNL Data Migration Tool]

1. 更改為 [!DNL Data Migration Tool] 目錄： `<vendor>/magento/data-migration-tool`。

1. 開啟 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) 的子菜單。

1. 的 `version` 檔案中的條目是 [!DNL Data Migration Tool]。
