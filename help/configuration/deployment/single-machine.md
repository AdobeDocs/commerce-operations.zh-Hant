---
title: 單一電腦部署
description: 瞭解如何使用命令列在生產伺服器上部署對Commerce的更新。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '189'
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
>貢獻開發人員應使用[本指南](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)更新其Commerce安裝。

## 部署步驟

1. 以或切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)的身份登入您的生產伺服器。

1. 將目錄變更為Commerce基底目錄：

   ```shell
   cd <Commerce base directory>
   ```

1. 使用命令啟用維護模式：

   ```shell
   bin/magento maintenance:enable
   ```

1. 使用下列命令模式將更新套用至Commerce或其元件：

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **封裝**：您要更新的封裝名稱。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**：您要更新的封裝目標版本。

1. 使用Composer更新元件：

   ```shell
   composer update
   ```

1. 更新資料庫架構和資料：

   ```shell
   bin/magento setup:upgrade
   ```

1. 編譯程式碼：

   ```shell
   bin/magento setup:di:compile
   ```

1. 部署靜態內容：

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. 清除快取：

   ```shell
   bin/magento cache:clean
   ```

1. 退出維護模式：

   ```shell
   bin/magento maintenance:disable
   ```

