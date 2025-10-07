---
title: 快取選項
description: 瞭解Adobe Commerce中的低階快取選項和儲存設定。 探索Redis和資料庫的前端、後端和儲存設定。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# 低階快取選項

Commerce應用程式使用低階快取前端和後端來提供對快取儲存區的存取權。

## 低階前端快取

Commerce藉由實作[Magento\Framework\Cache\Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)前端快取來擴充[Zend_Cache_Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)。

## 低階後端快取

一般而言，Commerce應用程式可搭配[Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)支援的任何後端快取運作。 不過，本指南僅涵蓋下列低階後端快取：

- [Redis](config-redis.md)
- [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 檔案系統（預設）：不需要設定即可使用檔案系統快取。

[Varnish](config-varnish.md)不需要設定低階快取後端。
