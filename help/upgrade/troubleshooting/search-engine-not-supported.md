---
title: 不支援當前搜索引擎
description: 在遇到有關不受支援的搜索引擎的錯誤後，對Adobe Commerce或Magento Open Source升級進行故障排除。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# 不支援當前搜索引擎

以下錯誤消息表示您要升級的Magento版本已配置為使用在要升級到的Magento版本中不支援的目錄搜索引擎：

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

此錯誤表示以下條件之一在Adobe Commerce或Magento Open Source的低級版本中為真：

- 搜索引擎已設定為MySQL。
- 搜索引擎被設定為不再支援的Elasticsearch版本。

使用以下命令檢查當前搜索引擎：

```bash
bin/magento config:show catalog/search/engine
```

如果返回的值為 `mysql` 或 `elasticsearch`。

>[!WARNING]
>
>如果您收到此錯誤，則Magento處於不一致狀態，您無法訪問管理員。 我們建議您在解決此錯誤時恢復到以前的版本。 要執行此操作，請運行以下命令之一：
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>位置 `<version>` 是您運行的Magento版本 **先** 升級。 比如說， `2.3.5`。

按照以下各節中介紹的指導原則從不一致狀態中恢復。

## 如果搜索引擎 `mysql`

在2.4之前， MySQL是預設目錄搜索引擎，但此容量不再支援MySQL。 現在，必須先安裝並配置Elasticsearch作為搜索引擎，然後才能升級到2.4。

使用以下資源幫助您完成此過程：

- [安裝和配置Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- 配置要使用的Elasticsearch [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) 或 [阿帕奇](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

配置Elasticsearch和重新索引後，即可升級到2.4。

## 如果搜索引擎 `elasticsearch`

值 `elasticsearch` 表示您的Adobe Commerce或Magento Open Source的低級版本已配置為使用Elasticsearch2.x。此版本的Elasticsearch不再受支援。

升級到2.4之前，必須執行以下任務：

1. 更新Elasticsearch。 我們建議更新到7.xElasticsearch。請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關備份資料、檢測潛在遷移問題和在部署到生產之前測試升級的完整說明。 根據您當前版本的Elasticsearch，可能需要或不需要完全群集重新啟動。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發工具包(JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 以檢查安裝的JDK版本。

1. [配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) 重新索引。

配置Elasticsearch和重新索引後，即可升級到2.4。
