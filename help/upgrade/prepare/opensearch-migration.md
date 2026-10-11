---
title: 從Elasticsearch移轉至OpenSearch
description: 瞭解如何取代用於內部部署Adobe Commerce的搜尋引擎。
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%
---
# 移轉至OpenSearch

OpenSearch是Elasticsearch 7.10.2的開放原始碼復本，在Elasticsearch授權變更後建立。

截至2.4.4、2.4.3-p2和2.3.7-p3，Adobe Commerce支援OpenSearch。 雖然雲端基礎結構上的Elasticsearch已不再支援內部部署安裝，但仍可繼續支援Adobe Commerce。 從2.4.6版開始，OpenSearch在管理員組態設定中有自己的模組和欄位。

## 移轉路徑

移轉至OpenSearch的步驟非常簡單，而且很大程度上遵循Elasticsearch設定的步驟。 這些步驟假設Adobe Commerce是唯一使用搜尋引擎的應用程式。 如果有多個應用程式使用搜尋引擎，請遵循官方移轉指南[從開放原始碼Elasticsearch移轉至OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/)。

1. 確定您的安裝符合[搜尋引擎必要條件](../../installation/prerequisites/search-engine/overview.md)。

1. 將網站置於[維護模式](../../installation/tutorials/maintenance-mode.md)。

1. 可選擇解除安裝Elasticsearch。

1. [安裝OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/)。

1. [設定搜尋引擎](../../configuration/search/configure-search-engine.md)並執行相關工作，例如排清快取並重新索引目錄搜尋索引。

不需要進一步變更設定值。
