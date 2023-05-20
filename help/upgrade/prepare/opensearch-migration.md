---
title: 從Elasticsearch遷移到OpenSearch
description: 瞭解更換用於Adobe Commerce和Magento Open Source內部安裝的搜索引擎。
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# 遷移到OpenSearch

OpenSearch是Elasticsearch7.10.2的開源分叉，該分叉在Elasticsearch的許可更改後建立。

截至2.4.4、2.4.3-p2和2.3.7-p3,Adobe Commerce和Magento Open Source支援OpenSearch。 內部安裝繼續支援Elasticsearch，儘管Adobe Commerce不再支援雲基礎架構。 從2.4.6版開始， OpenSearch在「管理」配置設定中有自己的模組和欄位。

## 遷移路徑

遷移到OpenSearch的步驟很簡單，並且基本上遵循Elasticsearch配置的步驟。 這些步驟假定Adobe Commerce是唯一使用搜索引擎的應用程式。 如果多個應用程式使用搜索引擎，請遵循官方遷移指南 [從開源Elasticsearch移動到OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/)。

1. 確保安裝符合 [搜索引擎先決條件](../../installation/prerequisites/search-engine/overview.md)。

1. 將站點放在 [維護模式](../../installation/tutorials/maintenance-mode.md)。

1. （可選）卸載Elasticsearch。

1. [安裝OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/)。

1. [配置搜索引擎](../../configuration/search/configure-search-engine.md) 並執行相關任務，如刷新快取和重新索引目錄搜索索引。

無需進一步更改配置值。
