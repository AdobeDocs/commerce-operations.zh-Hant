---
title: Realpath快取大小
description: 瞭解如何通過更新PHP讀取路徑快取配置以使用建議的設定來優化Adobe Commerce效能。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Realpath快取配置最佳做法

Realpath快取快取引用的檔案名的實際檔案系統路徑，而不是每次查找它們。 每次執行各種檔案函式或需要檔案並使用相對路徑時，PHP必須查找該檔案真正存在的位置。

要提高Commerce效能，請使用以下建議的設定配置 `realpath_cache` 的 `php.ini` 檔案：

- 將快取大小設定為10 MB(`realpath cache_size=10M`)
- 將生存時間(ttl)設定為7200秒(`realpath_cache_ttl=7200`)

有關配置說明，請參見 [如何設定PHP選項](../../../installation/prerequisites/php-settings.md#how-to-set-php-options)。

## 受影響的產品和版本

- Adobe Commerce本地，所有版本2.3.x及更高
- Adobe Commerce雲基礎架構，所有版本2.3.x及更高版本

## 潛在效能影響

如果Realpath快取配置值過低或過高，則會在快取生成過程中增加額外開銷，從而降低效能。

## 其他資訊

- [內部：PHP設定](../../../performance/software.md#php-settings)
- 在雲基礎架構上：
   - [資料庫最佳做法](database-on-cloud.md)
   - [Magento Commerce Cloud中最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
- [索引器「按計畫更新」可優化Magento效能](../maintenance/indexer-configuration.md)
