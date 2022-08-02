---
title: 搜索引擎概述
description: Adobe Commerce和Magento Open Source的搜索引擎選項概述。
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 搜索引擎概述

在2.4.4版中，Adobe Commerce和Magento Open Source要求 [Elasticsearch] 或 [開啟搜索] 成為目錄搜索引擎。 2.4.x的早期版本需要Elasticsearch。 有關安裝搜索引擎和初始配置的詳細資訊，請參閱以下主題：

- [搜索引擎先決條件]
- [為搜索引擎配置nginx]
- [為搜索引擎配置Apache]
- [安裝Commerce軟體] （命令行介面）

在安裝搜索引擎並將其與Adobe Commerce整合後，必須執行其他維護：

- [配置搜索停止字](search-stopwords.md)
- [搜索引擎配置](configure-search-engine.md)

<!-- Link Definitions -->

[搜索引擎先決條件]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[為搜索引擎配置nginx]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[為搜索引擎配置Apache]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[安裝Commerce軟體]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[開啟搜索]: https://opensearch.org/docs/latest/opensearch/install/index/
