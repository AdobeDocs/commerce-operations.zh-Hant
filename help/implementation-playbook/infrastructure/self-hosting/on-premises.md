---
title: 內部部署基礎結構
description: 瞭解Adobe Commerce內部部署基礎結構和第三方雲端服務。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Adobe Commerce內部部署基礎結構

開始新的Adobe Commerce實作或將現有的內部部署Adobe Commerce實作移至雲端的動機很多，但最常見的策略推動因素在於減少資本支出、降低持續成本、改善擴充能力和彈性、縮短上市時間，以及達成安全性與合規性方面的改善。

下圖顯示在AWS基礎結構上部署Adobe Commerce內部部署的參考架構。 Azure、Google Cloud和Alibaba Cloud等其他雲端服務供應商也有類似的基礎架構設計和同類服務。

![在協力廠商雲端服務上自行託管Adobe Commerce基礎結構的圖表](/help/assets/playbooks/on-premises-infrastructure.svg)

讓我們更深入地探討上述基礎架構各層面的角色和功能：

1. Amazon Route 53提供DNS設定。

1. AWS WAF是網頁應用程式防火牆，可保護Adobe Commerce免受常見的Web攻擊。

1. Amazon CloudFront是快速內容傳遞網路(CDN)，可加速靜態和動態網頁內容的發佈。

1. 第一個Elastic Load Balancing應用程式負載平衡器會將Varnish執行個體的流量分配到多個可用區域的AWS Auto Scaling群組中。

1. 清漆快取是網頁應用程式加速器快取HTTP反向Proxy。 建議使用AWS Marketplace提供的企業版本，因為其提供更好的功能，可支援雲端後端，並在動態主機上清除快取。

1. 第二個Elastic Load Balancing應用程式負載平衡器會將Varnish快取的流量分散到多個可用區域的Adobe Commerce執行個體的AWS Auto Scaling群組中。

1. 在Amazon EC2執行個體上安裝最新版的Adobe Commerce。 安裝包含Adobe Commerce應用程式、Nginx Web伺服器及PHP。 建置Amazon機器影像(AMI)以在Auto Scaling群組中啟動新執行個體。

1. AmazonElasticsearch服務是用於Adobe Commerce目錄搜尋的受管理Elasticsearch服務。

1. 適用於Redis的Amazon ElastiCache提供資料庫的快取階層。

1. 使用Amazon Aurora或AmazonRDS來簡化資料庫管理（包括高可用性與多主要組態）。

1. EFSMount Target有助於將Amazon Elastic File System (AmazonEFS)對應到Varnish和Adobe Commerce執行個體。

1. 使用Amazon EFS來存取在Adobe Commerce執行個體間塗漆和共用媒體資產間的共用設定。

## 雲端服務

除了在Adobe Commerce環境的AWS上提供支援DevOps流程的技術平台外，AWS還提供了一組服務，可提供（若未提供）或增強您現有的軟體設定管理(SCM)解決方案。 這包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，後者允許受管理的原始檔控制、建置、持續整合/持續部署(CI/CD)和部署服務。

## 雲端移轉

有幾項服務提供營運分析能力與靈活性，進一步提升將Adobe Commerce移轉至AWS的價值主張。 我們的意思是不僅從技術角度（例如每小時要求數），而且從業務營運角度（例如每小時訂單數）對平台進行營運分析，特別是當兩組資料可以結合時。 這可提供近乎即時的行銷活動績效、平台營運成本及其他指標調查。

AWS的Adobe Commerce設定可讓您在雲端中使用受完整管理的替代方案，取代特定應用程式相依性。 例如，許多應用程式的資料庫可輕鬆由Amazon關聯式資料庫服務(AmazonRDS)取代，而不用直接在EC2執行個體上託管關聯式資料庫。 此策略的優點在於，無差異元件的作業責任可以解除安裝至AWS，而不需要大幅變更核心應用程式。

有數個部署選項可用於在AWS上執行Adobe Commerce。 最適合的選擇取決於您的成本、規模、可用性和彈性需求，以及貴組織的AWS和Adobe Commerce技能。

{{$include /help/_includes/hosting-related-links.md}}
