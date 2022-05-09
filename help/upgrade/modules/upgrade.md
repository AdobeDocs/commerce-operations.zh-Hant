---
title: 升級模組和擴展
description: 使用命令行介面和Magento Open Source器升級Adobe Commerce和編譯模組和擴展。
source-git-commit: c619bff9785d22298bc49e2ac9874480ff7a320b
workflow-type: tm+mt
source-wordcount: '195'
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

## 供應商捆綁的擴展(VBE)

Adobe刪除所有 [VBE](https://devdocs.magento.com/extensions/vendor/) 的子2.4.4。供應商繼續在Adobe Commerce市場上支援這些擴展。

如果要繼續將這些擴展與Adobe Commerce和2.4.4及更高版本一起使用，必須更新您的 `composer.json` 檔案 _先_ 升級到2.4.4。請與供應商聯繫以獲取要使用的包名稱和版本。

有關詳細資訊，請參閱以下Adobe Commerce市場清單：

- [Amazon](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [點數](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [克拉爾納](https://marketplace.magento.com/klarna-m2-klarna.html)
- [頂點](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [約特波](https://marketplace.magento.com/yotpo-module-yotpo.html)

