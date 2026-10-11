---
title: OPcache記憶體大小的最佳實務
description: 說明如何藉由Adobe Commerce專案中的OPcache記憶體耗用特定設定來避免效能降低。
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 1%
---
# Adobe Commerce中OPcache記憶體大小的最佳作法

針對雲端基礎結構上的Adobe Commerce Pro計畫架構2.3.x，建議將`opcache.memory_consumption`設定為至少2 GB，以避免效能降低。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce Pro計畫架構2.3.x
* PHP 7.0和更新版本

## 設定記憶體

為[OPcache PHP模組](https://www.php.net/manual/en/book.opcache.php)分配至少&#x200B;**2GB**&#x200B;的記憶體。 OPcache模組設定在`php.ini`檔案中。 若要配置2048 MB的記憶體，請設定`opcache.memory_consumption = 2048`。

## 其他資訊

* [效能最佳實務 — PHP設定](../../../performance/software.md#php-settings)
* [設定PHP選項](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/configure-app-yaml)
* [雲端基礎結構上Adobe Commerce的資料庫最佳實務](database-on-cloud.md)
* [Adobe Commerce中雲端基礎結構最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
* [索引器「依排程更新」可最佳化Adobe Commerce效能](../maintenance/indexer-configuration.md)
