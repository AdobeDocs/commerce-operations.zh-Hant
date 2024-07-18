---
title: 不支援目前的搜尋引擎
description: 在遇到有關不支援的搜尋引擎的錯誤後，疑難排解您的Adobe Commerce升級。
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# 不支援目前的搜尋引擎

以下錯誤訊息指出您要升級的Adobe Commerce版本已設定為使用目錄搜尋引擎，而您要升級到的版本不支援該目錄搜尋引擎：

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

此錯誤表示在舊版Adobe Commerce中，有下列條件之一為true：

- 搜尋引擎設定為MySQL。
- 搜尋引擎設定為不再支援的Elasticsearch版本。

使用以下命令檢查目前的搜尋引擎：

```bash
bin/magento config:show catalog/search/engine
```

如果傳回值為`mysql`、`elasticsearch`或`elasticsearch6`，就會發生錯誤。

>[!WARNING]
>
>如果您收到此錯誤，表示您的安裝處於不一致狀態，且您無法存取Admin。 建議您解決此錯誤後，還原成先前的版本。 要執行此操作，請執行以下其中一個命令：
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>其中`<version>`是您在升級&#x200B;**之前**&#x200B;執行的Magento版本。 例如，`2.3.5`。

請依照下列各節所述的准則，從不一致的狀態復原。

## 如果您的搜尋引擎為`mysql`

在2.4之前，MySQL是預設的目錄搜尋引擎，但此容量已不再支援MySQL。 現在，您必須先安裝並設定Elasticsearch或OpenSearch作為搜尋引擎，才能升級至2.4。

請使用下列資源來協助引導您完成此程式：

- [安裝及設定搜尋引擎](../../configuration/search/overview-search.md)
- [搜尋引擎設定](../../configuration/search/configure-search-engine.md)

設定搜尋引擎並重新索引後，您就可以升級至2.4了。

## 如果您的搜尋引擎為`elasticsearch`

不再支援Elasticsearch6及舊版。

值`elasticsearch`表示您的Adobe Commerce舊版已設定為使用Elasticsearch2.x。不再支援此版本的Elasticsearch。

升級至2.4之前，您必須執行下列工作：

1. 更新至Commerce支援的Elasticsearch版本。 請參閱[升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html)，以取得有關備份資料、偵測可能的移轉問題，以及在部署到生產環境之前測試升級的完整指示。 根據您目前的Elasticsearch版本，可能不需要完全重新啟動叢集。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更新版本。 請參閱[安裝Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk)以檢查已安裝的JDK版本。

1. [設定Elasticsearch](../../configuration/search/configure-search-engine.md)並重新索引。

設定搜尋引擎並重新索引後，您就可以升級至2.4了。
