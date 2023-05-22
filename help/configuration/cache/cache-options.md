---
title: 快取選項
description: 配置對低級快取儲存的訪問。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 低級快取選項

Commerce應用程式使用低級快取前端和後端來提供對快取儲存的訪問。

## 低級前端快取

商業擴展 [結束快取核心](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 通過 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 前端快取。

## 低級後端快取

通常， Commerce應用程式與任何後端快取配合使用 [Zend_Cache後端](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) 支援。 但是，本指南僅涵蓋以下低級後端快取：

- [雷迪斯](config-redis.md)
- [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 檔案系統（預設）:使用檔案系統快取不需要配置。

[清漆](config-varnish.md) 不需要設定低級快取後端。
