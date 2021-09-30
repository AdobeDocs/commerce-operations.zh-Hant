---
title: Managed Services
description: 檢閱Adobe Managed Services、客戶和雲端服務提供者在雲端基礎架構實作上為您的Adobe商務所承擔的責任。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# 托管服務

Adobe雲端基礎架構管理服務上的商務預設為安全。

![顯示Adobe商務托管服務的圖表](../../../assets/playbooks/managed-services.svg)

## 分擔的責任

AdobeCommerce Pro計畫依賴共用責任安全模型。 在這種模式中，各方對維護系統安全負有不同的責任。 此方法既允許靈活使用，又允許使用同類最佳的雲技術。

![顯示Adobe商務共用責任模型的圖表](../../../assets/playbooks/shared-responsibility.svg)

### Adobe管理的服務責任

Adobe Managed Services負責AdobeCommerce Pro雲端環境、核心AdobeCommerce Pro應用程式程式碼以及內部商務系統的安全性和可用性。 這包括但不限於：

- 伺服器級打補丁
- 運行必要的服務以提供AdobeCommerce Pro計畫
- 漏洞測試
- 安全事件記錄和監控
- 事件管理
- 操作監控
- 24/7支援
- 確保客戶基礎架構可根據SLA提供

Adobe Managed Services也負責管理伺服器防火牆設定(iptables)和外圍防火牆設定（安全群組）。 Adobe也可定期向核心應用程式發佈安全更新。 客戶有責任應用這些修補程式。 這些領域均受雲基礎架構系統Adobe商務的PCI認證所涵蓋。

### AWS職責

Adobe Managed Services將Amazon Web Services(AWS)用於雲端伺服器基礎架構。 AWS負責網路的安全，包括通過防火牆系統和入侵檢測系統(IDS)進行路由、交換和外圍網路安全。 AWS負責對管理Adobe雲環境的資料中心進行物理安全，並負責環境安全，以確保適當的電源、冷卻和機制控制。

Adobe商務專業計畫使用：

- Amazon Elastic Compute Cloud(EC2)
- Amazon Simple Storage Service(S3)
- Amazon Elastic Block Store(EBS)
- Amazon Virtual Private Cloud(VPC)
- Amazon彈性負載平衡器(ELB)
- Amazon雲端軌跡服務。

Amazon擁有廣泛的合規計畫，其中包括PCI DSS、SOC 2和ISO 27001認證。

### 解決方案合作夥伴/客戶責任

Adobe主要負責在Commerce Pro計畫雲環境中運行的Adobe商務應用程式的定製實施的安全性。 這包括：

- 確保應用程式和安全監控活動的安全配置和編碼，包括滲透測試和常規漏洞掃描。

- 系統中使用的任何自訂、擴充功能、其他應用程式或整合的安全性。

- 其用戶的安全性以及對其配置和應用程式的訪問權限。

- 客戶會控制所有程式碼部署至其非生產環境。 此控制項還負責將應用程式安全補丁程式應用到核心Adobe商務應用程式、擴展或任何自定義代碼。

- 客戶應對其自訂應用程式執行滲透測試。 客戶、實施合作夥伴或Adobe商務專業服務可利用技術資源解決這些責任。

- 客戶負責其定制應用程式和自身流程的PCI要求。 客戶的PCI合規性建立在AWS和Adobe商務的PCI認證之上，以便最大限度地減少必須審查的領域。
