---
title: 單機部署
description: 瞭解如何使用命令行將更新部署到生產伺服器上的Commerce。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# 單機部署

本主題提供了使用命令行將更新部署到生產伺服器上的Commerce的說明。 此過程適用於負責在安裝了某些主題和區域設定的單個電腦上運行儲存的技術用戶。

## 假設

- 您使用 [作曲家](../../installation/composer.md)。
- 您正在直接將更新應用到伺服器。

>[!WARNING]
>
>如果使用 `git clone` 來安裝Commerce。
>提供幫助的開發商應使用 [本指南][install] 以更新其Commerce安裝。

## 部署步驟

1. 以或切換到的生產伺服器 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。

1. 將目錄更改為Commerce基目錄：

   ```bash
   cd <Commerce base directory>
   ```

1. 使用以下命令啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 使用以下命令模式將更新應用於Commerce或其元件：

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **包**:要更新的包的名稱。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**:要更新的包的目標版本。

1. 使用Composer更新元件：

   ```bash
   composer update
   ```

1. 更新資料庫架構和資料：

   ```bash
   bin/magento setup:upgrade
   ```

1. 編譯代碼：

   ```bash
   bin/magento setup:di:compile
   ```

1. 部署靜態內容：

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 退出維護模式：

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
