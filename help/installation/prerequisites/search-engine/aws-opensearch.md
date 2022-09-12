---
title: AWS OpenSearch
description: 請依照下列步驟，為AWS和Magento Open Source的內部部署安裝設定Adobe Commerce OpenSearch Web服務。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# AWS OpenSearch

Adobe Commerce和Magento Open Source2.4.3支援使用Amazon OpenSearch Service叢集。 此服務是AmazonElasticsearch服務的後繼服務。 本主題說明如何設定商務以使用AWS OpenSearch，以及如何將資料從本機Elasticsearch或OpenSearch執行個體移轉至AWS OpenSearch叢集。

## 建立AWS OpenSearch服務網域

您必須先在AWS中建立OpenSearch例項。
閱讀 [建立和管理Amazon OpenSearch服務網域](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) 以取得詳細指示。

## 將資料傳送至AWS OpenSearch

在AWS上準備好所有內容後，就可以填入資料。

若是較小的安裝，我們建議您直接在AWS執行個體上建立索引，原因如下：

* 重新建立索引是一個快速操作。
* 舊例項和AWS例項之間可能有版本不相容的情形，您可以直接在AWS例項上建置，以避免這些情形。

較大型的安裝可能會想要考慮將其資料索引從現有執行個體移轉至AWS。 雖然這可能會減少停機時間，但由於舊Elasticsearch伺服器與AWS之間的版本不同，因此出現不相容問題的風險仍然很小。

不需要移轉索引，因為這些可以輕鬆在AWS例項上重新建立。
不過，在移轉資料索引時，請確定Elasticsearch/OpenSearch的版本相容。

請參閱Amazon [移轉至Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) 詳細資訊說明。

### 配置OpenSearch的商務

配置OpenSearch的步驟在 [進階安裝](../../advanced.md) 主題。

要測試新配置是否正在工作，請直接測試OpenSearch端點：

1. 在管理員中建立產品(例如：sku=&quot;testproduct1&quot;)。
1. 透過管理員重新索引。
1. 查詢OpenSearch端點(可在AWS UI中找到):

   要獲取索引，請附加： `/_cat/indices/*?v=true` 至URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

要從索引獲取產品，請附加： `/magento2docker_product_1/_search?q=*` 至URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 其他資源

如需詳細資訊，請參閱 [OpenSearch AWS檔案](https://docs.aws.amazon.com/opensearch-service/index.html).
