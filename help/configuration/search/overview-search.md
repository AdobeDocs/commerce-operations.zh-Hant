---
title: 搜尋引擎概觀
description: 瞭解Elasticsearch和OpenSearch，以進行Adobe Commerce目錄搜尋、先決條件、網頁伺服器設定和安裝後維護工作。
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '117'
ht-degree: 0%
---
# 搜尋引擎概觀

截至2.4.4版，Adobe Commerce需要[Elasticsearch](https://www.elastic.co)或[OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/)做為目錄搜尋引擎。 舊版2.4.x需要Elasticsearch。 如需有關安裝搜尋引擎和初始設定的詳細資訊，請參閱下列主題：

- [搜尋引擎必要條件](../../installation/prerequisites/search-engine/overview.md)
- [為您的搜尋引擎設定nginx](../../installation/prerequisites/search-engine/configure-nginx.md)
- [為您的搜尋引擎設定Apache](../../installation/prerequisites/search-engine/configure-apache.md)
- [安裝Commerce軟體](../../installation/composer.md) （命令列介面）

安裝搜尋引擎並與Adobe Commerce整合後，您必須執行其他維護作業：

- [設定搜尋停用詞](search-stopwords.md)
- [搜尋引擎設定](configure-search-engine.md)

