---
title: 升級模組和擴展
description: 使用命令行介面和Magento Open Source器升級Adobe Commerce和編譯模組和擴展。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# 升級模組和擴展

要更新或升級模組或擴展：

1. 從Marketplace或其他擴展開發人員下載更新的檔案。 請注意模組名稱和版本。

1. 將內容導出到Adobe Commerce或Magento Open Source根安裝目錄。

1. 如果模組存在Composer包，請運行以下程式之一。

   每個模組名稱的更新：

   ```bash
   composer update vendor/module-name
   ```

   每個版本的更新：

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
