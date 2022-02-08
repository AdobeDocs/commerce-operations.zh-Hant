---
title: 雲基礎架構概述
description: 瞭解Adobe Commerce雲基礎架構。
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 概述

Adobe Commerce在AWS的最受歡迎的托管選擇之一是Adobe Commerce自己提供的。 Adobe Commerce雲基礎架構是Adobe Commerce軟體的完全托管的自動托管平台。

Adobe Commerce雲基礎架構是一種平台即服務(PaaS)產品，可快速部署完全可定製、安全且可擴展的網店，並結合領先的托管和托管服務基礎架構。 它提供兩個具有不同基礎設施的計畫。 Adobe CommerceStarter最適合於複雜性較小、目錄較小的小商店。 Adobe CommercePro是為更複雜、產品目錄更大或流量達到高峰的大型商店而構建的。 Adobe Commerce將在合作夥伴的投入下確定適當的架構。

Adobe Commerce已具備雲就緒性，並擁有完全冗餘的多雲托管基礎架構，可提供優化的效能、恢復力和彈性可擴充性。 您可以在Apphist的內容分發網路(CDN)上高效地運行您的商業平台，而使用New Relic進行監控和管理，您可以保持儲存環境的平穩運行。

Adobe Commerce提供了現代雲計算的所有優勢，這些優勢最常與SaaS解決方案相關聯：彈性可擴充性、高恢復力和可用性、PCI合規性、全球可用性和自動化修補，同時仍保持我們的商家所需的軟體定制靈活性。

![示出雲基礎架構上Adobe Commerce的體系結構元素的圖](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 好處

Adobe Commerce的其他好處包括：

- **針對Adobe Commerce優化**。 Adobe Commerce開發的構建指令碼和服務配置可確保正確調整和配置每個實例以獲得最佳商家效能。

- **一致、安全的版本**。 所有代碼部署都基於Git以實現一致性和可重複性，而只讀生產環境則可增強安全性。

- **合作夥伴的靈活性**。 完整的REST API和可指令碼化的命令行介面確保了與外部系統的輕鬆整合以及與現有代碼管理工作流的相容性。

- **靈活的部署工具集**。 可隨意快速啟動、合併、克隆和拆除無限制的環境，用於開發任務、QA測試或生產問題診斷。

- **連續雲交付**。 從開發到UAT，在代碼部門和開發團隊之間以持續的方式，滿懷信心地直接向生產過渡。

## 第三方服務

我們還來看一下讓Adobe Commerce的好處成為現實的軟體。

![顯示Adobe Commerce雲基礎架構技術堆棧的圖](../../../assets/playbooks/cloud-tech-stack.svg)

- Appeist CDN:當客戶訪問您的站點和儲存時，這些請求會快速載入快取的頁面。 Apphise WAF還提供DDoS保護服務。

- New Relic為您提供應用程式和操作環境的完整視圖。 它允許您將來自移動和瀏覽器應用程式的關鍵指標與支援服務、資料儲存和主機相結合，以便您能夠全面優化效能並確保每項計畫的成功。

- Composer管理Adobe Commerce的依賴項和升級，並提供有關包、包的功能以及它們如何組合的上下文。

- Git是儲存庫中的代碼。 它允許本地分支、方便的過渡區域和多個工作流，並可自動構建和部署，以實現高效的快速開發和連續部署。

- Platform-as-a-Service(PaaS)提供了預配置的基礎架構，包括PHP、MySQL、Redis、RabbitMQ和Elasticsearch技術。

- AWS或Azure的雲托管支援基礎架構即服務(IaaS)，它為線上銷售和零售提供可擴展且安全的環境。
