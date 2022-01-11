---
title: 升級模組和擴充功能
description: 使用命令列介面和撰寫器來升級Adobe Commerce和Magento Open Source模組和擴充功能。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# 升級模組和擴充功能

若要更新或升級模組或擴充功能：

1. 從Marketplace或其他擴充功能開發人員下載更新的檔案。 記下模組名稱和版本。

1. 將內容匯出至Adobe Commerce或Magento Open Source根安裝目錄。

1. 如果模組的撰寫器套件存在，請執行下列其中一項。

   按模組名稱更新：

   ```bash
   composer update vendor/module-name
   ```

   按版本更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 運行以下命令以升級、部署和清除快取。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
