---
title: 不支援當前的搜索引擎
description: 針對不支援的搜尋引擎發生錯誤後，疑難排解Adobe Commerce或Magento Open Source升級。
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# 不支援當前的搜索引擎

下列錯誤訊息指出您要升級的Adobe Commerce或Magento Open Source版本已設定為使用目錄搜尋引擎，而您要升級至的版本不支援此引擎：

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

若傳回的值為 `mysql`, `elasticsearch`，或 `elasticsearch6`.

>[!WARNING]
>
>如果您收到此錯誤，表示您的安裝狀態不一致，且您無法存取管理員。 建議您在解決此錯誤時，回復成舊版。 要執行此操作，請運行以下命令之一：
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

在2.4之前， MySQL是預設的目錄搜索引擎，但此容量不再支援MySQL。 現在，您必須先安裝並設定Elasticsearch或OpenSearch作為搜尋引擎，才能升級至2.4。

使用下列資源來協助您完成此程式：

- [安裝並配置搜尋引擎](../../configuration/search/overview-search.md)
- [搜尋引擎設定](../../configuration/search/configure-search-engine.md)

設定搜尋引擎並重新索引後，即可升級至2.4。

## 如果您的搜尋引擎是 `elasticsearch`

Elasticsearch6及舊版不再受支援。

值 `elasticsearch` 指出您的下層版本Adobe Commerce或Magento Open Source已設定為使用Elasticsearch2.x。不再支援此版本的Elasticsearch。

升級到2.4之前，必須執行以下任務：

1. 更新至商務支援的Elasticsearch版本。 請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關在部署到生產環境之前備份資料、檢測潛在遷移問題和測試升級的完整說明。 視您當前的Elasticsearch版本而定，可能需要或不需要完全群集重新啟動。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發套件(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 來檢查安裝的JDK版本。

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md) 和重新索引。

設定搜尋引擎並重新索引後，即可升級至2.4。
