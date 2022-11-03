---
title: OPcache記憶體大小的最佳做法
description: 說明如何避免因Adobe Commerce專案上OPcache記憶體耗用的特定設定而導致效能降低。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Adobe Commerce中OPcache記憶體大小的最佳實務

針對雲端基礎架構上的Adobe Commerce Pro計畫架構2.3.x，建議設定 `opcache.memory_consumption` 至少2 GB，以避免效能下降。

## 受影響的產品和版本

* Adobe Commerce on cloud infrastructure Pro計畫架構2.3.x
* PHP 7.0及更新版本

## 配置記憶體

至少分配 **2 GB** 記憶體 [OPcache PHP模組](https://www.php.net/manual/en/book.opcache.php). OPcache模組是在 `php.ini` 檔案。 要分配2048 MB記憶體，請設定 `opcache.memory_consumption = 2048`.

## 其他資訊

* [效能最佳實務 — PHP設定](../../../performance/software.md#php-settings)
* [配置PHP選項](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Adobe Commerce雲端基礎架構資料庫最佳實務](database-on-cloud.md)
* [Adobe Commerce雲端基礎架構中最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
* [索引器「按計畫更新」可優化Adobe Commerce效能](../maintenance/indexer-configuration.md)
