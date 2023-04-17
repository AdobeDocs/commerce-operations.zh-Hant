---
title: 內部部署基礎設施
description: 了解Adobe Commerce內部部署基礎架構和第三方雲端服務。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: a253da8cfe95083d1df76d3253aaa424b78a4865
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerce內部基礎設施

啟動新的Adobe Commerce實施或將現有的內部部署Adobe Commerce實施移至雲端的動機很多，但最常見的戰略驅動因素是減少資本支出、降低持續成本、改善可擴充性和彈性、縮短上市時間，以及改善安全性和合規性。

下圖顯示在AWS基礎架構上部署Adobe Commerce內部部署的參考架構。 其他雲提供商，如Azure、Google雲和阿里巴巴雲，都有類似的基礎設施設計和同類服務。

![圖表顯示在協力廠商雲端服務上自行托管Adobe Commerce基礎架構](/help/assets/playbooks/on-premises-infrastructure.svg)

讓我們更深入探討上述基礎架構各個方面的角色和功能：

1. Amazon Route 53提供DNS配置。

1. AWS WAF是Web應用程式防火牆，可保護Adobe Commerce不受常見Web木馬程式攻擊。

1. Amazon CloudFront是快速內容傳遞網路(CDN)，可加快靜態和動態網頁內容的傳遞。

1. 第一個Elastic Load Balancing應用程式負載平衡器在多個可用區域中，在AWS Auto Scaling組的Rehist實例之間分配流量。

1. 清漆快取是Web應用程式加速器快取HTTP反向代理。 建議使用透過AWS Marketplace提供的企業版，因為其具備更佳功能，可支援雲端後端和跨動態主機的快取清除。

1. 第二個Elastic Load Balancing應用程式負載平衡器在多個可用區域中，將來自清漆快取的流量分佈到Adobe Commerce實例的AWS自動縮放組。

1. 在Amazon EC2實例上安裝最新版的Magento Open Source或Adobe Commerce。 安裝由Adobe Commerce應用程式、Nginx Webserver和PHP組成。 建立Amazon電腦影像(AMI)，以在「自動縮放」群組中啟動新例項。

1. AmazonElasticsearch服務是Adobe Commerce目錄搜尋的受管Elasticsearch服務。

1. Amazon ElastiCache for Redis提供資料庫的快取層。

1. 使用Amazon Aurora或AmazonRDS簡化資料庫管理（包括高可用性和多主配置）。

1. EFSMount Target有助於將Amazon彈性檔案系統(AmazonEFS)映射到清漆和Adobe Commerce實例。

1. 使用Amazon EFS訪問跨清漆的共用配置和跨Adobe Commerce實例的共用媒體資產。

## 雲端服務

除了提供支援技術平台以在Adobe Commerce環境中於AWS上啟用DevOps程式外，AWS還提供一系列服務，可提供（在沒有的情況下）或增強您現有的軟體配置管理(SCM)解決方案。 這包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，它允許進行受管源控制、構建、連續整合/連續部署(CI/CD)和部署服務。

## 雲端移轉

將Adobe Commerce移轉至AWS的價值主張，透過提供營運洞察力和靈活度的多項服務而進一步增強。 我們的意思是，對平台的運營洞察力不僅從技術角度（例如，每小時請求），還從業務運營角度（例如，每小時訂單），尤其是當兩組資料可以結合時。 這可提供行銷活動績效、平台運作成本以及幾乎無限個其他指標的近乎即時分析。

Adobe Commerce設定至AWS後，雲端提供的完全托管替代方案可取代特定應用程式相依性。 例如，許多應用程式的資料庫可以輕鬆地替換為Amazon關係資料庫服務(AmazonRDS)，而不是直接在EC2實例上托管關係資料庫。 此策略的好處是，無差別元件的操作責任可卸載至AWS，而無需對核心應用程式進行重大更改。

在AWS上執行Adobe Commerce(包括Magento Open Source和Adobe Commerce版本)有數個可用的部署選項。 最合適的選擇取決於貴組織對成本、規模、可用性和靈活性的要求，以及貴組織的AWS和Adobe Commerce技能。

{{$include /help/_includes/hosting-related-links.md}}
