---
title: Realpath快取大小
description: 了解如何將PHP讀路徑快取配置更新為使用建議的設定，以最佳化Adobe Commerce效能。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Realpath快取配置最佳實踐

Realpath快取快取引用檔案名的實際檔案系統路徑，而不是每次查找它們。 每次執行各種檔案功能或需要檔案並使用相對路徑時，PHP必須查找該檔案真正存在的位置。

若要改善商務效能，請使用下列建議的設定來設定 `realpath_cache` 設定 `php.ini` 檔案：

- 將快取大小設定為10 MB(`realpath cache_size=10M`)
- 將存留時間(ttl)設為7200秒(`realpath_cache_ttl=7200`)

如需設定指示，請參閱 [如何設定PHP選項](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## 受影響的產品和版本

- Adobe Commerce內部部署，所有2.3.x版及更新版本
- Adobe Commerce雲端基礎架構，所有2.3.x版及更新版本

## 潛在的效能影響

如果Realpath快取配置值太低或太高，則會在快取生成過程中增加額外開銷，從而降低效能。

## 其他資訊

- [內部部署：PHP設定](../../../performance/software.md#php-settings)
- 在雲基礎架構上：
   - [資料庫最佳實務](database-on-cloud.md)
   - [Magento Commerce Cloud中最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
- [索引器「按計畫更新」可優化Magento效能](../maintenance/indexer-configuration.md)

