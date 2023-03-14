---
title: 雲基礎架構概述
description: 了解Adobe Commerce雲端基礎架構相關資訊。
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: ea912c48176fb060e48654d05ae6b533436a2432
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 概述

Adobe Commerce本身提供AWS上Adobe Commerce最熱門的托管選項之一。 Adobe Commerce on cloud infrastructure是Adobe Commerce軟體的完整管理自動化托管平台。

Adobe Commerce雲端基礎架構是一種平台即服務(PaaS)產品，可與領先的托管和托管服務基礎架構相結合，快速部署可完全自訂、安全且可擴展的Web商店。 它提供兩個具有不同基礎架構的計畫。 Adobe Commerce Starter最適合規模較小、複雜度較低、目錄較小的商店。 Adobe Commerce Pro專為複雜度更高、產品目錄更大或流量達到峰值的大型商店而打造。 Adobe Commerce將透過合作夥伴的意見，決定適當的架構。

Adobe Commerce具備雲端就緒功能，具備完全冗餘的多雲托管基礎架構，可提供最佳效能、可復原性和彈性可擴充性。 您可以在Ampley的內容傳遞網路(CDN)上有效地執行商務平台，而透過New Relic進行監控和管理，您可以讓存放區環境持續順暢運作。

Adobe Commerce提供現代雲計算的所有優勢，這些優勢最常與SaaS解決方案相關聯：彈性可擴充性、高可復原性和可用性、PCI合規性、全局可用性和自動修補，同時仍保持我們的商戶所需的軟體定制靈活性。

![顯示雲基礎架構上Adobe Commerce架構元素的圖表](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 優點

Adobe Commerce的其他優點包括：

- **針對Adobe Commerce最佳化**. Adobe Commerce開發的建置指令碼和服務設定可確保每個執行個體都能正確調整及設定，以獲得最佳的商家效能。

- **一致、安全的發行**. 所有程式碼部署都以Git為基礎，提供一致性和重複性，並採用唯讀生產環境，強化安全性。

- **合作夥伴的靈活性**. 完整的REST API和可指令碼化的命令列介面可確保輕鬆與外部系統整合，並與現有的程式碼管理工作流程相容。

- **靈活的部署工具集**. 針對開發任務、QA測試或生產問題診斷，隨意快速回轉、合併、克隆和拆除無限的環境。

- **持續雲端傳送**. 在程式碼分支和開發團隊間，以持續的方式，自信地從開發直接移至UAT到生產環境。

## 第三方服務

讓我們來看看讓Adobe Commerce的好處成真的軟體。

![顯示雲基礎架構技術堆疊上Adobe Commerce的圖表](../../../assets/playbooks/cloud-tech-stack.svg)

- 快速CDN:當客戶存取您的網站和商店時，請求會以快速方式點擊，以更快載入快取頁面。 Emply WAF還提供DDoS保護服務。

- New Relic可讓您完整檢視您的應用程式和作業環境。 它可讓您將行動和瀏覽器應用程式的關鍵量度與支援服務、資料儲存和主機結合，以便您能全面最佳化效能，並確保每個計畫都能成功。

- 撰寫器可在Adobe Commerce中管理相依性和升級，並提供包含套件、套件的用途及其搭配方式的相關內容。

- Git是存放庫中的程式碼。 它可支援本機分支、方便的中繼區域，以及多個工作流程，並透過自動建置和部署，以有效快速開發及持續部署。

- Platform-as-a-Service(PaaS)提供了預配置的基礎架構，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]，以及OpenSearch或Elasticsearch技術。

- AWS或Azure的雲托管支援基礎架構即服務(IaaS)，為線上銷售和零售提供可擴展且安全的環境。
