---
title: 搜尋引擎概觀
description: Adobe Commerce和Magento Open Source的搜尋引擎選項概觀。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# 搜尋引擎概觀

自2.4.4版起，Adobe Commerce和Magento Open Source需要 [Elasticsearch] 或 [OpenSearch] 成為目錄搜尋引擎。 舊版2.4.x需要Elasticsearch。 如需安裝搜尋引擎和初始設定的詳細資訊，請參閱下列主題：

- [搜尋引擎必要條件]
- [為搜尋引擎設定nginx]
- [為您的搜尋引擎設定Apache]
- [安裝Commerce軟體] （命令列介面）

安裝搜尋引擎並將其與Adobe Commerce整合後，您必須執行其他維護：

- [配置搜索停止詞](search-stopwords.md)
- [搜尋引擎設定](configure-search-engine.md)

<!-- Link Definitions -->

[搜尋引擎必要條件]: ../../installation/prerequisites/search-engine/overview.md
[為搜尋引擎設定nginx]: ../../installation/prerequisites/search-engine/configure-nginx.md
[為您的搜尋引擎設定Apache]: ../../installation/prerequisites/search-engine/configure-apache.md
[Elasticsearch]: https://www.elastic.co
[安裝Commerce軟體]: ../../installation/composer.md
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
