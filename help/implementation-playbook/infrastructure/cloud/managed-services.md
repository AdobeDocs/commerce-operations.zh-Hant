---
title: Managed Services
description: 檢閱針對您的Managed ServicesAdobeAdobe Commerce、客戶和雲端服務供應商在雲端基礎結構實施上的責任。
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Managed Services

根據預設，雲端基礎結構上的Adobe Commerce受管服務是安全的。

![顯示Adobe Commerce Managed Services的圖表](../../../assets/playbooks/managed-services.svg)

## 共擔責任

Adobe Commerce Pro計畫採用共擔責任安全模式。 在此模型中，不同的當事人有不同的責任領域來維護系統的安全性。 此方法可讓您靈活運用同類最佳的雲端技術。

![顯示Adobe Commerce共用責任模型的圖表](../../../assets/playbooks/shared-responsibility.svg)

### AdobeManaged Services責任

Adobe Managed Services負責Adobe Commerce Pro雲端環境、核心Adobe Commerce Pro應用程式程式碼和內部商務系統的安全性與可用性。 這包含但不限於：

- 伺服器層級修補
- 操作必要的服務，以提供Adobe Commerce Pro計畫
- 弱點測試
- 安全性事件記錄與監控
- 事件管理
- 營運監控
- 全天候支援
- 確保客戶基礎設施可根據SLA使用

Adobe Managed Services還負責管理伺服器防火牆設定(iptables)和周邊防火牆設定（安全性群組）。 Adobe也會定期發行核心應用程式的安全性更新。 客戶有責任套用這些修補程式。 這些領域都包含在雲端基礎結構系統上的Adobe Commerce PCI認證中。

### AWS責任

Adobe Managed Services使用Amazon Web Services (AWS)進行雲端伺服器基礎建設。 AWS負責網路的安全性，包括路由、交換和周邊網路安全，透過防火牆系統和入侵偵測系統(IDS)。 AWS負責管理Adobe Commerce雲端環境的資料中心的實體安全性，以及環境安全性，以確保擁有適當的電源、冷卻和機制控制項。

Adobe Commerce Pro計畫使用：

- Amazon彈性運算雲端(EC2)
- Amazon簡單儲存服務(S3)
- Amazon彈性區塊存放區(EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon彈性負載平衡器(ELB)
- Amazon雲端軌跡服務。

Amazon擁有廣泛的法規遵循計畫，其中包括PCI DSS、SOC 2和ISO 27001認證。

### 解決方案合作夥伴/客戶責任

客戶主要負責在Adobe Commerce Pro計畫雲端環境中執行Adobe Commerce應用程式的自訂實施安全性。 其中包括：

- 確保應用程式的安全設定和編碼，以及安全監控活動，包括滲透測試和定期的弱點掃描。

- 任何在其系統中使用的自訂、擴充功能、其他應用程式或整合的安全性。

- 其使用者的安全性以及對其設定和應用程式的存取權授予。

- 客戶可控制所有程式碼部署至其非生產環境。 此控制項也有責任將應用程式安全性修補程式套用至核心Adobe Commerce應用程式、擴充功能或任何自訂程式碼。

- 客戶應對其自訂應用程式執行滲透測試。 這些責任可由客戶、實作合作夥伴或Adobe Commerce專業服務的技術資源來履行。

- 客戶需自行負責自訂應用程式和流程的PCI需求。 客戶的PCI法規遵循以AWS和Adobe Commerce的PCI認證為基礎，以儘量減少必須檢視的領域。
