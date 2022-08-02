---
title: 快取選項
description: 配置對低級快取儲存的訪問。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# 低級快取選項

Commerce應用程式使用低級別 [快取](https://glossary.magento.com/cache) [前](https://glossary.magento.com/frontend) 和 [後端](https://glossary.magento.com/backend) 提供對快取儲存的訪問。

## 低級前端快取

商業擴展 [結束快取核心](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 通過 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 前端快取。

## 低級後端快取

通常， Commerce應用程式與任何後端快取配合使用 [Zend_Cache後端](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) 支援。 但是，本指南僅涵蓋以下低級後端快取：

- [雷迪斯](config-redis.md)
- [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 檔案系統（預設）:使用檔案系統快取不需要配置。

[清漆](config-varnish.md) 不需要設定低級快取後端。
