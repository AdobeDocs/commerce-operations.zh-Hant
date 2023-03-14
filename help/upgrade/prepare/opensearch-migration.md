---
title: 從Elasticsearch移轉至OpenSearch
description: 了解如何更換用於Adobe Commerce和Magento Open Source內部部署安裝的搜尋引擎。
source-git-commit: 682963fb66519097e54f14f2b84ed71528030054
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# 移轉至OpenSearch

OpenSearch是Elasticsearch授權變更後建立的Elasticsearch7.10.2的開放原始碼復本。

自2.4.4、2.4.3-p2和2.3.7-p3起，Adobe Commerce和Magento Open Source支援OpenSearch。 雖然Adobe Commerce不再支援雲基礎架構，但內部部署安裝仍可繼續支援Elasticsearch。 從2.4.6版開始， OpenSearch在管理配置設定中有其自己的模組和欄位。

## 移轉路徑

遷移到OpenSearch的步驟很簡單，而且基本上遵循Elasticsearch配置的步驟。 這些步驟假設Adobe Commerce是唯一使用搜尋引擎的應用程式。 若有多個應用程式使用搜尋引擎，請遵循官方移轉指南 [從開放原始碼Elasticsearch移至OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. 確保安裝符合 [搜尋引擎必要條件](../../installation/prerequisites/search-engine/overview.md).

1. 將網站置於 [維護模式](../../installation/tutorials/maintenance-mode.md).

1. （可選）卸載Elasticsearch。

1. [安裝OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [設定搜尋引擎](../../configuration/search/configure-search-engine.md) 並執行相關任務，例如刷新快取並重新索引目錄搜索索引。

無需進一步變更設定值。
