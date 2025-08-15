---
title: 單一電腦部署
description: 瞭解如何使用命令列在生產伺服器上部署對Commerce的更新。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# 單一機器部署

本主題說明如何使用命令列，在生產伺服器上部署Commerce的更新。 此程式適用於負責在單一機器上執行存放區的技術使用者，該機器已安裝一些佈景主題和區域設定。

## 假設

- 您已使用[撰寫器](../../installation/composer.md)安裝Commerce。
- 您正在將更新直接套用至伺服器。

>[!WARNING]
>
>如果您使用`git clone`安裝Commerce，則本指南不適用。
>&#x200B;>貢獻開發人員應使用[本指南][install]更新其Commerce安裝。

## 部署步驟

1. 以或切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)的身份登入您的生產伺服器。

1. 將目錄變更為Commerce基底目錄：

   ```bash
   cd <Commerce base directory>
   ```

1. 使用命令啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 使用下列命令模式將更新套用至Commerce或其元件：

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **封裝**：您要更新的封裝名稱。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**：您要更新的封裝目標版本。

1. 使用Composer更新元件：

   ```bash
   composer update
   ```

1. 更新資料庫架構和資料：

   ```bash
   bin/magento setup:upgrade
   ```

1. 編譯程式碼：

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
