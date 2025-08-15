---
title: 升級模組和擴充功能
description: 使用命令列介面和撰寫器來升級Adobe Commerce模組和擴充功能。
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 升級模組和擴充功能

若要更新或升級模組或擴充功能：

1. 從Marketplace或其他擴充功能開發人員下載更新的檔案。 記下模組名稱和版本。

1. 將內容匯出至您的Adobe Commerce根安裝目錄。

1. 如果模組存在撰寫器套件，請執行以下其中一項作業。

   每個模組名稱更新：

   ```bash
   composer update vendor/module-name
   ```

   每個版本更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 執行以下命令以升級、部署和清除快取。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## 廠商套件擴充功能(VBE)

Adobe已移除2.4.4中的所有[VBE](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/upgrade-guide/modules/upgrade)。廠商持續在Adobe Commerce Marketplace上支援這些擴充功能。

若要繼續將這些擴充功能與Adobe Commerce 2.4.4和更新版本搭配使用，您必須在`composer.json`升級至2.4.4之前，更新&#x200B;_檔案_&#x200B;中對應的套件相依性。請聯絡供應商，以取得要使用的套件名稱和版本。

如需詳細資訊，請參閱下列Adobe Commerce Marketplace清單：

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [頂點](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
