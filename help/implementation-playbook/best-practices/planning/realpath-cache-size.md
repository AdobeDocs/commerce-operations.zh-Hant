---
title: Realpath快取大小
description: 瞭解如何透過更新PHP Readlpath快取設定以使用建議的設定來最佳化Adobe Commerce效能。
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%
---
# Realpath快取設定最佳實務

Realpath快取會快取參照之檔案名稱的真實檔案系統路徑，而非每次都查詢。 每次執行各種檔案功能或需要檔案並使用相對路徑時，PHP都必須尋找該檔案真正存在的位置。

若要改善Commerce效能，請使用下列建議的設定來設定`php.ini`檔案中的`realpath_cache`設定：

- 將快取大小設定為10 MB (`realpath_cache_size=10M`)
- 將存留時間(ttl)設定為7200秒(`realpath_cache_ttl=7200`)

如需組態指示，請參閱[如何設定PHP選項](../../../installation/prerequisites/php-settings.md#how-to-set-php-options)。

## 受影響的產品和版本

- Adobe Commerce內部部署，所有2.3.x版及更新版本
- 雲端基礎結構上的Adobe Commerce，所有2.3.x版及更新版本

## 對效能的潛在影響

如果Realpath快取設定值太低或太高，它會在產生快取時增加額外的負荷，而這會降低效能。

## 其他資訊

- [內部部署： PHP設定](../../../performance/software.md#php-settings)
- 在雲端基礎結構上：
  - [資料庫最佳實務](database-on-cloud.md)
  - [Magento Commerce Cloud中最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
- [索引器「依排程更新」可最佳化Magento效能](../maintenance/indexer-configuration.md)
