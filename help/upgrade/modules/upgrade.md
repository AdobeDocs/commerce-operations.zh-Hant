---
title: 升級模組和擴充功能
description: 使用命令列介面和撰寫器來升級Adobe Commerce和Magento Open Source模組和擴充功能。
source-git-commit: 682963fb66519097e54f14f2b84ed71528030054
workflow-type: tm+mt
source-wordcount: '191'
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

## 供應商套件擴充功能(VBE)

Adobe移除所有 [VBE](https://devdocs.magento.com/extensions/vendor/) 在2.4.4中。廠商持續在Adobe Commerce Marketplace上支援這些擴充功能。

如果您想要繼續將這些擴充功能與Adobe Commerce 2.4.4和更新版本搭配使用，必須更新您 `composer.json` 檔案 _befor_ 升級至2.4.4。請與供應商聯繫，以獲取要使用的包名稱和版本。

如需詳細資訊，請參閱下列Adobe Commerce Marketplace清單：

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [克拉納](https://marketplace.magento.com/klarna-m2-klarna.html)
- [頂點](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [約特波](https://marketplace.magento.com/yotpo-module-yotpo.html)

