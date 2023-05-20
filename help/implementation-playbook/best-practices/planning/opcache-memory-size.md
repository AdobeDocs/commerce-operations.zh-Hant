---
title: OPcache記憶體大小的最佳實踐
description: 介紹如何避免因Adobe Commerce項目上OPcache記憶體消耗的特定設定而導致效能下降。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# OPcache記憶體大小在Adobe Commerce的最佳實踐

對於Adobe Commerce雲基礎架構Pro計畫體系結構2.3.x，建議設定 `opcache.memory_consumption` 至少2 GB ，以避免效能降級。

## 受影響的產品和版本

* Adobe Commerce雲基礎架構Pro計畫體系結構2.3.x
* PHP 7.0及更高版本

## 配置記憶體

至少分配 **2 GB** 記憶體 [OPcache PHP模組](https://www.php.net/manual/en/book.opcache.php)。 OPcache模組在 `php.ini` 的子菜單。 要分配2048 MB記憶體，請設定 `opcache.memory_consumption = 2048`。

## 其他資訊

* [效能最佳實踐 — PHP設定](../../../performance/software.md#php-settings)
* [配置PHP選項](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [針對Adobe Commerce的雲基礎架構資料庫最佳做法](database-on-cloud.md)
* [Adobe Commerce雲基礎架構中最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
* [索引器「按時更新」可優化Adobe Commerce效能](../maintenance/indexer-configuration.md)
