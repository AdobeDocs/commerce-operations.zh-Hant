---
title: AWS OpenSearch
description: 請依照下列步驟，為Adobe Commerce的內部部署安裝設定AWS OpenSearch Web服務。
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
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
source-wordcount: '341'
ht-degree: 0%
---
# AWS OpenSearch

Adobe Commerce 2.4.5支援使用Amazon OpenSearch Service叢集。 此服務是Amazon Elasticsearch服務的後續服務。 本主題說明如何設定Commerce以使用AWS OpenSearch，以及如何將資料從本機Elasticsearch或OpenSearch執行個體移轉至AWS OpenSearch叢集。

## 建立AWS OpenSearch服務網域

您必須先在AWS中建立OpenSearch執行個體。
閱讀[建立和管理Amazon OpenSearch Service網域](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html)以取得詳細指示。

## 將資料傳送至AWS OpenSearch

在AWS上完成所有準備工作後，就可以開始使用資料來填入了。

對於較小的安裝，我們建議您直接在AWS執行個體上建立索引，原因如下：

* 重新建立索引是一項快速操作。
* 舊執行個體和AWS執行個體之間可能存在版本不相容問題，直接在AWS執行個體上建置可以避免這些不相容問題。

大型安裝可能會考慮將其資料索引從現有執行個體移轉至AWS。 雖然這樣可以減少停機時間，但由於舊版Elasticsearch伺服器與AWS之間的版本不同，因此仍然存在不相容問題的小風險。

不需要移轉索引，因為這些可在AWS例項上輕鬆重新建立。
不過，移轉資料索引時，請確保Elasticsearch/OpenSearch的版本相容。

如需詳細資訊，請參閱Amazon的[移轉至Amazon OpenSearch服務](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html)指示。

### 為OpenSearch設定Commerce

設定OpenSearch的步驟包含在[進階安裝](../../advanced.md)主題中。

若要測試新設定是否正常運作，請直接測試OpenSearch端點：

1. 在「管理員」中建立產品（例如：sku=&quot;testproduct1&quot;）。
1. 透過Admin重新索引。
1. 查詢OpenSearch端點（可在AWS UI中找到）：

   若要取得索引，請附加： `/_cat/indices/*?v=true`至URL：
   `<AWS OS endpoint>/_cat/indices/*?v=true`

若要從索引取得產品，請將： `/magento2docker_product_1/_search?q=*`附加至URL：
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 其他資源

如需其他資訊，請參閱[OpenSearch AWS檔案](https://docs.aws.amazon.com/opensearch-service/index.html)。
