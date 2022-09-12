---
title: 單機部署
description: 了解如何使用命令列在生產伺服器上部署更新至Commerce。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# 單機部署

本主題提供使用命令列在生產伺服器上將更新部署至Commerce的指示。 此過程適用於負責在安裝了某些主題和區域設定的單台電腦上運行的儲存的技術用戶。

## 假設

- 您使用 [撰寫器].
- 您直接將更新套用至伺服器。

>[!WARNING]
>
>若您使用 `git clone` 來安裝商務。
>貢獻開發人員應使用 [本指南][install] 以更新其Commerce安裝。

## 部署步驟

1. 以 [檔案系統所有者][file-owner].

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

   **套件**:要更新的包的名稱。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**:要更新的包的目標版本。

1. 使用撰寫器更新元件：

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
[composer]: ../../installation/composer.md
[file-owner]: ../../installation/prerequisites/file-system/overview.md
