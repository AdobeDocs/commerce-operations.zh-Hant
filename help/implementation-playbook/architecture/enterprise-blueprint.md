---
title: 企業參考架構
description: 瞭解如何使用Adobe最新的可撰寫商務技術實施Adobe Commerce。
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
source-git-commit: 96afb0ccf5ea872cb42320babfd04ba51fa7dbf6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---


# Adobe Commerce企業參考架構

Adobe Commerce是體驗導向的平台，以獨特的方式搭配技術彈性與易用性，全都是為了建立卓越的體驗，推動業務成果。

Commerce已經進化，可滿足企業對效能、規模及安全性的需求。 採用現代化實作方法，利用Adobe最新的可撰寫商業解決方案，是企業成功的關鍵所在。 本頁技術性地詳細描述現代化的Commerce實作方法。

下列架構圖說明Adobe Commerce與所有Adobe Experience Cloud解決方案之間的資料流程。

![顯示Adobe Commerce如何連線至Experience Cloud解決方案的架構圖表](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>圖表中顯示的高階資料流程在大多數企業實作中是一致的。 讓實施具有唯一性的關鍵元件是建置目錄的方式（尤其是B2B）。 您應該小心地將目錄架構對應至 [Commerce網頁API](https://developer.adobe.com/commerce/webapi/get-started/).

## 雲端基礎

[雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) 是Commerce實作的基礎。 它提供 [secure](../../security-and-compliance/shared-responsibility.md) 採用自助式方法，在雲端原生環境中建置、部署、監控及管理您的Commerce應用程式，進而實現自動化託管平台。

請參閱下列雲端基礎技術詳細資訊：

- [**擴充架構**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) — 自動調整容量，以維持穩定、可預測的效能
- [**多個環境**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) — 預先布建PHP、MySQL (MariaDB)、Redis、RabbitMQ以及支援的搜尋引擎技術，以開發、測試和部署您的網站
- [**設定管理**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) — 可自訂的環境組態檔和命令列介面(CLI)，用於管理應用程式設定、路由、建置和部署動作以及通知。
- [**Git型工作流程**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) — 推送程式碼變更後自動建置和部署，以進行快速開發和持續部署
- [**內建可觀察性**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) — 結合來自多個來源的記錄資料以幫助您管理網站效能和診斷問題的工具
- [**全面的API涵蓋範圍**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) 和 [REST](https://developer.adobe.com/commerce/webapi/rest) 用於將核心Commerce應用程式與協力廠商系統整合及擴充Commerce功能的API

## 與Experience Cloud整合

Adobe Commerce與所有Experience Cloud解決方案整合，以提供 [大規模個人化商務體驗](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[資料連線](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) 開啟有關購物者購買行為的深入分析，以便您可以使用其他Adobe數位體驗產品跨所有管道建立個人化購物體驗。

>[!NOTE]
>
>另請參閱 [數位體驗藍圖](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) 以取得更多技術細節。


## 與協力廠商系統整合

Adobe為開發人員提供完整的擴充點和工具，以建置可擴充核心Commerce功能並整合Commerce與協力廠商系統（例如CRM、ERPS和PIMS）的應用程式。 這些工具可透過下列方式降低平台的總體擁有成本：

- **擴充性** — 應用程式可與核心軟體分開擴充，以提升效率並簡化升級程式。
- **隔離** — 孤立的環境表示開發人員可以自行升級或修改擴充功能，而不需依賴核心版本。
- **技術獨立性** — 開發人員可選擇符合其需求的任何技術棧疊和程式碼語言。

Adobe提供下列開發人員工具，用於建立整合與自訂：

- [**Adobe Developer App Builder的API網格**](https://developer.adobe.com/graphql-mesh-gateway/) — 協調多個API、GraphQL、REST和其他來源並將其結合為單一、可查詢的GraphQL端點。
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) — 建置和部署安全且可擴充的Web應用程式，這些應用程式可擴充Commerce功能並與協力廠商解決方案整合。
- [**活動**](https://developer.adobe.com/commerce/extensibility/events/) — 使用自訂事件觸發器與其他可擴充的開發工具互動。
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) — 使用Webhook自動觸發Commerce與協力廠商系統之間的互動。
- [**管理UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) — 透過商戶適用的新頁面和功能，自訂並增強Commerce管理員。

## 店面服務

Adobe提供一套豐富的智慧可撰寫商品化服務，協助您支援關鍵業務目標。 這些服務也提供對大規模最佳化效能至關重要的應用程式開發介面。

- [即時搜尋](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview) — 使用此AI支援的搜尋工具，為購物者提供更聰明、更快速且相關的結果。
- [產品Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) — 根據購物者行為、熱門趨勢、產品相似度等，新增AI支援的建議。
- [目錄服務](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview) — 為客戶提供最佳化的產品體驗，同時提升效能、改善擴充能力及提高轉換率。
- [付款服務](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview) — 提供多種付款方式，包括免息分期付款，以及付款處理、訂單和發票的單一檢視，以提升客戶滿意度。

## Headless店面

Headless商務是API優先的商務。 Adobe Commerce採用分離式架構，可透過GraphQL API層提供所有商務服務和資料，提供完整的Headless。 此架構可讓團隊獨立於核心應用程式開發前端，提供使用新興技術快速建立和測試新接觸點的靈活性。

Adobe提供現代化的Headless店面技術，具備以下所提供的相同優勢和功能： [Edge Delivery Services](https://www.aem.live/home) 以檔案為基礎的製作、以效能為先的架構，以及現成可用的原生實驗。 那個充分運用Adobe Commerce的規模與效能 [店面服務](#storefront-services) 以及彈性與便利性 [外掛程式元件](https://experienceleague.adobe.com/developer/commerce/storefront/) 以提供商務功能。
