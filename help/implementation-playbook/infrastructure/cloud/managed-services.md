---
title: Managed Services
description: 查看Adobe托管服務、客戶和雲服務提供商在雲基礎架構實施方面為您的Adobe Commerce承擔的責任。
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# 托管服務

Adobe Commerce雲基礎架構托管服務預設是安全的。

![顯示Adobe Commerce托管服務的圖表](../../../assets/playbooks/managed-services.svg)

## 分擔責任

Adobe Commerce·普羅的計畫依賴於共同責任的安全模式。 在這種模式中，各方對維護系統安全負有不同的責任。 此方法允許靈活使用同類最佳的雲技術。

![顯示Adobe Commerce共同責任模型的圖表](../../../assets/playbooks/shared-responsibility.svg)

### Adobe托管服務責任

Adobe Managed Services負責Adobe CommercePro雲環境、核心Adobe CommercePro應用程式碼和內部商務系統的安全性和可用性。 這包括但不限於：

- 伺服器級修補
- 運行必要的服務以提供Adobe Commerce專業計畫
- 漏洞測試
- 安全事件記錄和監視
- 事件管理
- 業務監測
- 24/7支援
- 確保客戶基礎架構按照SLA可用

Adobe Managed Services還負責管理伺服器防火牆配置(iptables)和外圍防火牆配置（安全組）。 Adobe還可以定期向核心應用程式發佈安全更新。 應用這些修補程式是客戶的責任。 這些領域都包括在雲基礎架構系統上的Adobe CommercePCI認證。

### AWS職責

Adobe Managed Services將Amazon Web Services(AWS)用於雲伺服器基礎架構。 AWS負責網路安全，包括通過防火牆系統和入侵檢測系統(IDS)進行路由、交換和外圍網路安全。 AWS負責為管理Adobe Commerce雲環境的資料中心提供物理安全保護，並負責環境安全，以確保適當的電源、冷卻和機制控制到位。

Adobe Commerce專業計畫使用：

- Amazon彈性計算雲(EC2)
- Amazon簡單儲存服務(S3)
- Amazon彈性塊儲存(EBS)
- Amazon虛擬專用雲(VPC)
- Amazon彈性負載平衡器(ELB)
- Amazon雲跟蹤服務。

Amazon擁有廣泛的合規性計畫，其中包括PCI DSS、SOC 2和ISO 27001認證。

### 解決方案合作夥伴/客戶責任

客戶主要負責在Adobe Commerce專業計畫雲環境中運行的Adobe Commerce應用程式的定製實施的安全性。 這包括：

- 確保應用程式和安全監控活動的安全配置和編碼，包括滲透測試和定期漏洞掃描。

- 系統中使用的任何自定義、擴展、其他應用程式或整合的安全性。

- 用戶的安全性以及對其配置和應用程式的訪問權限。

- 客戶控制到其非生產環境的所有代碼部署。 此控制項還負責將應用程式安全修補程式應用到核心Adobe Commerce應用程式、擴展或任何自定義代碼。

- 客戶應執行其定制應用程式的滲透test。 這些責任可由客戶、實施合作夥伴或Adobe Commerce專業服務提供的技術資源來解決。

- 客戶負責其定制應用程式和自己流程的PCI要求。 客戶的PCI合規性建立在AWS和Adobe Commerce的PCI認證之上，以最大限度地減少必須審查的領域。
