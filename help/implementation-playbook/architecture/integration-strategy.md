---
title: Adobe Commerce整合戰略
description: 審查您的Adobe Commerce實施的整合戰略和選項。
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Adobe Commerce整合策略

整合您的平台的能力是「不容談判的」。 公司希望其電子商務平台能夠從各種接觸點訪問並無縫整合到其技術系統中，特別是ERP中。 定制性、全球可擴充性和經濟性在最終平台購買中也起著作用。

GraphQLAPI效能、綜合REST API以及Adobe Commerce和其他系統或服務之間的批處理檔案導入支援店面和後端系統的整體整合方法。

Adobe CommerceGraphQLAPI提供全面的店面覆蓋，您可以利用它與其他店面整合，包括：

- 數字型驗平台(DXP)，如Adobe Experience Manager和布盧姆瑞克
- 內容管理系統(CMS)，如Drupal和WordPress
- Adobe Commerce、PWA Studio、武業等現代定制店面應用

GraphQL提供高效、特定於渠道的響應，不會過度讀取資料，並靈活部署新的觸點功能。 它還經常被選擇與移動本地應用、POS、IoT、社交渠道和Facebook、Google、Instagram、微信和TikTok等直播商業渠道整合。

Adobe CommerceREST API提供全面的系統配置覆蓋面和資料管理功能，包括產品和目錄；購物車、報價和結帳；客戶、客戶和公司；訂單和退貨。 REST API支援批量操作、多種身份驗證模式和精細授權，因此通常選擇REST API與企業系統整合，包括：

- 企業資源規劃(ERP)系統，如SAP
- 產品資訊管理(PIM)系統，如Akeneo
- 客戶關係管理(CRM)系統，如Salesforce
- 訂單管理系統(OMS)，如MOM 、 Manhattan和SAP
- 倉庫管理系統(WMS)或第三方物流(3PL)，如Oracle、 NetSuite和SAP WM
- 配置、價格、報價(CPQ)，如SalesforceCPQ
- 數字資產管理(DAM)，如AdobeDAM。

批檔案導入還被認為是整合企業系統（如ERP和PIM）的一個好選項，因為資料不會經常更改，而且您通常在定時檔案導入時具有更好的效能。 因此，通常選擇批量檔案導入用於每日/每週和每月的完整資料同步，而選擇REST API用於增量資料更改同步，以獲得更好的效能。 這也只被視為一項計畫的工作，但可以根據業務需要頻繁完成 — 可能每15分鐘到1小時一次。

## 整合選項

Adobe Commerce提供三種靈活的整合選項：

- 直接與預構建的連接器進行系統到系統的整合。 某些系統可能已在Adobe Commerce市場或其自己的網站上擁有Adobe Commerce擴展。

- 通過自定義中間件實現系統到系統的整合。 部署的自定義中間件解決方案將用於流程資料映射、轉換和管理。

- 通過iPaaS（整合平台即服務）進行系統到系統的整合，也稱為EAI（企業應用整合平台），如Mulesoft、Boomi和Software AG。

![Adobe Commerce整合選項](../../assets/playbooks/integration-options.svg)

儘管通常需要即時整合，但在某些情況下也不需要。 Adobe Commerce本機支援 [!DNL RabbitMQ] 作為消息匯流排以啟用非同步進程，建議對於一些不需要即時交換的資料，而是使用批處理檔案交換或REST批處理資料進程API進行更新以非同步處理。
