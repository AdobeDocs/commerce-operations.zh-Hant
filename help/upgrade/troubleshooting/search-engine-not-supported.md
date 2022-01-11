---
title: 不支援當前的搜索引擎
description: 針對不支援的搜尋引擎發生錯誤後，疑難排解Adobe Commerce或Magento Open Source升級。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# 不支援當前的搜索引擎

以下錯誤訊息指出您要升級的Magento版本已設定為使用目錄搜尋引擎，而您要升級至的Magento版本不支援此引擎：

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

此錯誤表示下列其中一個條件在Adobe Commerce或Magento Open Source的下層版本中為true:

- 搜索引擎被設定為MySQL。
- 搜尋引擎已設為不再支援的Elasticsearch版本。

使用以下命令檢查當前搜索引擎：

```bash
bin/magento config:show catalog/search/engine
```

若傳回的值為 `mysql` 或 `elasticsearch`.

>[!WARNING]
>
>如果您收到此錯誤，Magento的狀態會不一致，且您無法存取管理員。 建議您在解決此錯誤時，回復成舊版。 要執行此操作，請運行以下命令之一：
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
>其中 `<version>` 是您執行的Magento版本 **befor** 升級。 例如， `2.3.5`.

請依照以下各節所述的准則，從不一致的狀態中恢復。

## 如果您的搜尋引擎是 `mysql`

在2.4之前， MySQL是預設的目錄搜索引擎，但此容量不再支援MySQL。 現在，您必須先安裝並將Elasticsearch設定為搜尋引擎，才能升級至2.4。

使用下列資源來協助您完成此程式：

- [安裝和配置Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- 配置Elasticsearch以使用 [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) 或 [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

配置Elasticsearch和重新索引後，即可升級至2.4。

## 如果您的搜尋引擎是 `elasticsearch`

值 `elasticsearch` 指出您的下層版本Adobe Commerce或Magento Open Source已設定為使用Elasticsearch2.x。不再支援此版本的Elasticsearch。

升級到2.4之前，必須執行以下任務：

1. 更新Elasticsearch。 建議更新至Elasticsearch7.x。請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關在部署到生產環境之前備份資料、檢測潛在遷移問題和測試升級的完整說明。 視您當前的Elasticsearch版本而定，可能需要或不需要完全群集重新啟動。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發套件(JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 來檢查安裝的JDK版本。

1. [配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) 和重新索引。

配置Elasticsearch和重新索引後，即可升級至2.4。
