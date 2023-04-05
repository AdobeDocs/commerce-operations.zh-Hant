---
title: 快取選項
description: 配置對低級快取儲存的訪問。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 低級快取選項

商務應用程式使用低級快取前端和後端來提供對快取儲存的訪問。

## 低級前端快取

商務擴展 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 執行 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 前端快取。

## 低階後端快取

一般而言，商務應用程式可搭配任何後端快取使用， [Zend_Cache後端](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) 支援。 不過，本指南僅涵蓋下列低階後端快取：

- [雷迪斯](config-redis.md)
- [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 檔案系統（預設）:使用檔案系統快取無需配置。

[清漆](config-varnish.md) 不需要設定低階快取後端。
