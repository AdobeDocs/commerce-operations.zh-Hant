---
title: Adobe商務整合策略
description: 檢閱Adobe商務實作的整合策略和選項。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Adobe商務整合策略

整合您的平台的能力是「不可協商的」。 企業希望從各種接觸點訪問其電子商務平台，並將其無縫整合到其技術系統中，尤其是ERP中。 可定製性、全球可擴充性和價格可承受性，在最終的平台購買過程中也起著關鍵作用。

效能GraphQL API、完整的REST API，以及Adobe商務與其他系統或服務之間的批次檔案匯入，都支援店面與後端系統的整合方法。

Adobe商務GraphQL API提供完整的店面涵蓋範圍，可用來與其他店面整合，包括：

- 數位體驗平台(DXP)，例如Adobe體驗管理器和Bloomreach
- 內容管理系統(CMS)，如Drupal和WordPress
- 現代自訂店面應用程式，例如Adobe商務、PWA Studio和Vue Storefront

GraphQL提供高效、通道特定的回應、無過度擷取資料，以及新接觸點功能的快速部署。 它還經常被選擇與銷售渠道整合，如移動原生應用程式、POS、IoT、社交渠道，以及Facebook、Google、Instagram、微信和TikTok等直播商務渠道。

Adobe商務REST API提供全方位的系統設定涵蓋範圍和資料管理功能，包括產品和目錄；購物車、報價和結帳；客戶、客戶和公司；訂單和退貨。 REST API支援大量操作、多種驗證模式和精細的授權，因此REST API通常被選擇與企業系統整合，包括：

- 企業資源規劃(ERP)系統，如SAP
- 產品資訊管理(PIM)系統，如Akeneo
- 客戶關係管理(CRM)系統，如Salesforce
- 訂單管理系統(OMS)，如MOM 、 Manhattan和SAP
- 倉庫管理系統(WMS)或第三方物流(3PL)，如Oracle、 NetSuite和SAP WM
- 配置、價格、報價(CPQ)，如SalesforceCPQ
- 數位資產管理(DAM)，如AdobeDAM。

批檔案導入也被認為是整合企業系統（如ERP和PIM）的一個好選項，因為資料不經常更改，而且您經常在計畫的檔案導入中擁有更好的效能。 因此，批量檔案導入通常選擇每日/每週和每月完整資料同步進行批量資料同步，而REST API則選擇用於增量資料更改同步，以獲得更好的效能。 這也只被視為已排程的工作，但根據業務需要，可以頻繁執行（可能每15分鐘到1小時）。

## 整合選項

Adobe商務提供三種彈性的整合選項：

- 與預先建立的連接器直接進行系統對系統整合。 某些系統可能已在AdobeCommerce Marketplace或其自己的網站上擁有Adobe商務擴充功能。

- 通過自定義中間件進行系統到系統的整合。 部署的自定義中間件解決方案將用於處理資料映射、翻譯和管理。

- 通過iPaaS（整合平台即服務）進行系統到系統的整合，也稱為EAI（企業應用程式整合平台），如Mulesoft、Boomi和Software AG。

![Adobe商務整合選項](../../assets/playbooks/integration-options.svg)

即使通常需要即時整合，但在某些情況下並不需要。 Adobe商務原本支援RabbitMQ作為消息匯流排，以啟用非同步處理，對於某些不需要即時交換的資料，而建議使用批次檔案交換或REST批次資料處理API來更新以非同步處理。
