---
title: AWSOpenSearch
description: 按照以下步驟配置AWSOpenSearch Web服務，用於Adobe Commerce和Magento Open Source的內部安裝。
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# AWSOpenSearch

Adobe Commerce和Magento Open Source2.4.5支援使用AmazonOpenSearch Service群集。 此服務是AmazonElasticsearch服務的後繼服務。 本主題介紹如何配置Commerce以使用AWSOpenSearch，以及如何將資料從本地Elasticsearch或OpenSearch實例遷移到AWSOpenSearch群集。

## 建立AWSOpenSearch服務域

必須先在AWS建立OpenSearch實例。
閱讀 [建立和管理AmazonOpenSearch服務域](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) 的上界。

## 將資料獲取到AWSOpenSearch

一旦在AWS做好一切準備，就該用資料來填充它了。

對於較小的安裝，我們建議您直接在AWS實例上建立索引，原因如下：

* 重新建立索引是一個快速操作。
* 舊實例和AWS實例之間可能存在版本不相容，通過直接在AWS實例上構建，可以避免這些不相容。

較大的安裝可能希望考慮將其資料索引從現有實例遷移到AWS。 雖然這可能減少停機時間，但由於舊Elasticsearch伺服器和AWS之間的版本不同，出現不相容問題的風險仍然很小。

無需遷移索引，因為可以在AWS實例上輕鬆重新建立索引。
但是，在遷移資料索引時，請確保Elasticsearch/OpenSearch的版本相容。

見Amazon [遷移到AmazonOpenSearch服務](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) 的子菜單。

### 為OpenSearch配置Commerce

配置OpenSearch的步驟在 [高級安裝](../../advanced.md) 主題。

要test新配置正在工作，請直接testOpenSearch終結點：

1. 在管理員中建立產品(例如：sku=&quot;testproduct1&quot;)。
1. 通過管理員重新索引。
1. 查詢OpenSearch終結點(在AWSUI中找到):

   要獲取索引，請追加： `/_cat/indices/*?v=true` 到URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

要從索引獲取產品，請追加： `/magento2docker_product_1/_search?q=*` 到URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 其他資源

有關其他資訊，請參閱 [OpenSearchAWS文檔](https://docs.aws.amazon.com/opensearch-service/index.html)。
