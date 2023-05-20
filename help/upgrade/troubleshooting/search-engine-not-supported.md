---
title: 不支援當前搜索引擎
description: 在遇到有關不受支援的搜索引擎的錯誤後，對Adobe Commerce或Magento Open Source升級進行故障排除。
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 不支援當前搜索引擎

以下錯誤消息表示您要升級的Adobe Commerce或Magento Open Source版本配置為使用在要升級到的版本中不受支援的目錄搜索引擎：

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

如果返回的值為 `mysql`。 `elasticsearch`或 `elasticsearch6`。

>[!WARNING]
>
>如果您收到此錯誤，則您的安裝處於不一致狀態，您無法訪問管理員。 我們建議您在解決此錯誤時恢復到以前的版本。 要執行此操作，請運行以下命令之一：
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

在2.4之前， MySQL是預設目錄搜索引擎，但此容量不再支援MySQL。 現在，必須先安裝並配置Elasticsearch或OpenSearch作為搜索引擎，然後才能升級到2.4。

使用以下資源幫助您完成此過程：

- [安裝和配置搜索引擎](../../configuration/search/overview-search.md)
- [搜索引擎配置](../../configuration/search/configure-search-engine.md)

配置搜索引擎並重新編製索引後，您就可以升級到2.4。

## 如果搜索引擎 `elasticsearch`

Elasticsearch6和更早版本不再受支援。

值 `elasticsearch` 表示您的Adobe Commerce或Magento Open Source的低級版本已配置為使用Elasticsearch2.x。此版本的Elasticsearch不再受支援。

升級到2.4之前，必須執行以下任務：

1. 更新到Commerce支援的Elasticsearch版本。 請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關備份資料、檢測潛在遷移問題和在部署到生產之前測試升級的完整說明。 根據您當前版本的Elasticsearch，可能需要或不需要完全群集重新啟動。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發工具包(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 以檢查安裝的JDK版本。

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md) 重新索引。

配置搜索引擎並重新編製索引後，您就可以升級到2.4。
