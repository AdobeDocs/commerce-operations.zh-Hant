---
title: 內部基礎設施
description: 瞭解Adobe Commerce本地基礎架構和第三方雲服務。
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerce內部基礎設施

啟動新的Adobe Commerce實施或將現有的內部部署Adobe Commerce實施遷移到雲的動機眾多，但最常見的戰略驅動因素是降低資本支出、降低持續成本、提高可擴充性和彈性、縮短上市時間以及實現安全性和合規性的改進。

下圖顯示了在Adobe Commerce基礎設施上部署AWS內部部署的參考體系結構。 其他雲提供商，如Azure、Google雲和阿里巴巴雲，共用類似的基礎設施設計和相應服務。

![示出第三方雲服務上自主承載的Adobe Commerce基礎架構的圖表](../../assets/playbooks/on-premises-infrastructure.svg)

讓我們更深入地瞭解上面所示基礎架構各個方面的角色和功能：

1. Amazon路由53提供DNS配置。

1. AWSWAF是一個Web應用程式防火牆，可保護Adobe Commerce免受常見Web漏洞的攻擊。

1. AmazonCloudFront是一個快速內容分發網路(CDN)，可加快靜態和動態Web內容的分發。

1. 第一個彈性負載平衡應用程式負載平衡器在多個可用區中的AWS自動縮放組中的清漆實例之間分配流量。

1. 清漆快取是Web應用程式加速器快取HTTP反向代理。 建議使用通過AWS市場提供的企業版，因為它具有更好的功能，可支援雲後端和跨動態主機的快取清除。

1. 第二個彈性負載平衡應用程式負載平衡器將來自清漆快取的流量分佈到多個可用區中的AWS自動縮放Adobe Commerce實例組。

1. 在AmazonEC2實例上安裝最新版本的Magento Open Source或Adobe Commerce。 安裝由Adobe Commerce應用程式、Nginx Webserver和PHP組成。 構建Amazon電腦映像(AMI)以在自動縮放組中啟動新實例。

1. AmazonElasticsearch服務是用於Adobe Commerce目錄搜索的托管Elasticsearch服務。

1. AmazonRedis的ElastiCache為資料庫提供了快取層。

1. 使用AmazonAurora或AmazonRDS簡化資料庫管理（包括高可用性和多主配置）。

1. EFSMount Target有助於將Amazon彈性檔案系統(AmazonEFS)映射到清漆和Adobe Commerce實例。

1. 使用AmazonEFS跨清漆和跨Adobe Commerce實例共用媒體資產訪問共用配置。

## 雲服務

除了為在Adobe Commerce環境的AWS上啟用DevOps流程提供支援技術平台外，AWS還提供一系列服務，這些服務可以提供（在沒有的情況下）或補充您現有的軟體配置管理(SCM)解決方案。 這包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，它允許受管原始碼控制、生成、連續整合/連續部署(CI/CD)和部署服務。

## 雲遷移

將Adobe Commerce遷至AWS的價值主張因提供操作洞察力和靈活性的幾項服務而得到進一步加強。 我們的意思是，不僅從技術角度（例如，每小時請求數），而且從業務運營角度（例如，每小時訂單數），對平台的運營洞察力，特別是當兩組資料能夠結合時。 這幾乎可以即時查看市場活動績效、平台運營成本以及幾乎無窮無盡的其他指標。

Adobe Commerce到AWS的安裝程式可以用雲中提供的完全托管替代方案替換特定的應用程式依賴關係。 例如，許多應用程式的資料庫不是直接在EC2實例上托管關係資料庫，而是可以輕鬆地由Amazon關係資料庫服務(AmazonRDS)取代。 該戰略的好處是，無差別元件的運營責任可以卸到AWS，而不需要對核心應用進行重大更改。

在AWS上運行Adobe Commerce(Magento Open Source版和Adobe Commerce版)有幾種部署選項。 最合適的選擇取決於您對成本、規模、可用性和靈活性的要求，以及您組織的AWS和Adobe Commerce技能。
