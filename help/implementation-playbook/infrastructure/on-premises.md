---
title: 內部部署基礎設施
description: 了解Adobe商務的內部基礎架構和第三方雲服務。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---


# Adobe商務內部部署基礎結構

啟動新AdobeCommerce實施或將現有內部AdobeCommerce實施遷移到雲的動機很多，但最常見的戰略驅動因素是減少資本支出、降低持續成本、提高可擴充性和彈性、改進上市時間，以及實現安全性和合規性方面的改進。

下圖顯示了在AWS基礎設施上部署Adobe商務的參考體系結構。 其他雲提供商，如Azure、Google Cloud和Alibaba Cloud，都有類似的基礎設施設計和同類服務。

![圖表顯示第三方雲端服務上自行托管的Adobe商務基礎架構](../../assets/playbooks/on-premises-infrastructure.svg)

讓我們更深入探討上述基礎架構各個方面的角色和功能：

1. Amazon Route 53提供DNS配置。

1. AWS WAF是Web應用程式防火牆，可保護Adobe商務免受常見Web木馬程式攻擊。

1. Amazon CloudFront是快速內容傳遞網路(CDN)，可加快靜態和動態網頁內容的傳遞。

1. 第一個Elastic Load Balancing應用程式負載平衡器在多個可用區域中，在AWS Auto Scaling組的Rehist實例之間分配流量。

1. 清漆快取是Web應用程式加速器快取HTTP反向代理。 建議使用通過AWS Marketplace提供的企業版，因為它具有更好的功能，可支援雲後端和跨動態主機的快取清除。

1. 第二個Elastic Load Balancing應用程式負載平衡器在多個可用區域中，從Queiste Cache跨AWS Auto Scaling組Adobe商務實例分配流量。

1. 在Amazon EC2實例上安裝最新版的Magento Open Source或Adobe商務。 安裝由Adobe商務應用程式、Nginx Webserver和PHP組成。 建立Amazon電腦影像(AMI)，以在「自動縮放」群組中啟動新例項。

1. AmazonElasticsearch服務是用於Adobe商務目錄搜尋的托管Elasticsearch服務。

1. Amazon ElastiCache for Redis提供資料庫的快取層。

1. 使用Amazon Aurora或AmazonRDS簡化資料庫管理（包括高可用性和多主配置）。

1. EFSMount Target有助於將Amazon彈性檔案系統(AmazonEFS)映射到清漆和Adobe商務實例。

1. 使用Amazon EFS在Adobe商務實例間訪問清漆和共用媒體資產的共用配置。

## 雲端服務

除了提供支援技術平台，以便圍繞您的Adobe商務環境在AWS上啟用DevOps流程外，AWS還提供一系列服務，可以提供（在沒有的情況下）或增強您現有的軟體配置管理(SCM)解決方案。 這包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，它允許進行受管源控制、構建、連續整合/連續部署(CI/CD)和部署服務。

## 雲端移轉

通過提供操作洞察力和靈活性的多種服務，將Adobe商務遷移到AWS的價值主張得到了進一步增強。 我們的意思是，對平台的運營洞察力不僅從技術角度（例如，每小時請求），還從業務運營角度（例如，每小時訂單），尤其是當兩組資料可以結合時。 這可提供行銷活動績效、平台運作成本以及幾乎無限個其他指標的近乎即時分析。

AdobeAWS的Commerce設定可以取代特定應用程式依賴項，而雲端提供完全管理的替代項。 例如，許多應用程式的資料庫可以輕鬆地替換為Amazon關係資料庫服務(AmazonRDS)，而不是直接在EC2實例上托管關係資料庫。 此策略的好處是，可以將未區分元件的運營責任卸載到AWS中，而無需對核心應用程式進行重大更改。

在AWS上執行Adobe商務(Magento Open Source和Adobe商務版本)有數個可用的部署選項。 最合適的選擇取決於貴機構對成本、規模、可用性和靈活性的要求，以及貴機構的AWS和Adobe商務技能。
