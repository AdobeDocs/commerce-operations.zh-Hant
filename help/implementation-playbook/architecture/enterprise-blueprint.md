---
title: 企業參考架構
description: 瞭解如何使用Adobe的最新可撰寫商務技術實施Adobe Commerce。
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Commerce企業參考架構

Adobe Commerce是體驗導向的平台，以獨特的方式搭配技術彈性與易用性，全都是為了建立卓越的體驗，推動業務成果。

Commerce已經進化，可滿足企業對效能、規模及安全性的需求。 採用現代化實作方法，利用Adobe最新的可撰寫商務解決方案，是企業成功的關鍵所在。 本頁技術性地詳細介紹現代化的Commerce實作方法。

下列架構圖說明Adobe Commerce與所有Adobe Experience Cloud解決方案之間的資料流程。

![顯示Adobe Commerce如何連線至Experience Cloud解決方案的架構圖表](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>圖表中顯示的高階資料流程在大多數企業實作中是一致的。 讓實施具有唯一性的關鍵元件是建置目錄的方式（尤其是B2B）。 您應該小心地將目錄架構對應至[Commerce Web API](https://developer.adobe.com/commerce/webapi/get-started/)。

## 雲端基礎

[雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)是您Commerce實作的基礎。 它提供[安全](../../security-and-compliance/shared-responsibility.md)自動化託管平台，以及可在雲端原生環境中建立、部署、監控及管理Commerce應用程式的自助式方法。

請參閱下列雲端基礎技術詳細資訊：

- [**擴充的架構**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) — 自動調整容量，以維持穩定、可預測的效能
- [**多個環境**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) — 已預先布建PHP、MySQL (MariaDB)、Redis、RabbitMQ和支援的搜尋引擎技術，以開發、測試和部署您的網站
- [**組態管理**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) — 可自訂的環境組態檔和命令列介面(CLI)，用於管理應用程式設定、路由、建置和部署動作以及通知。
- [**以Git為基礎的工作流程**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) — 在推送程式碼變更以進行快速開發和持續部署後，自動建置和部署
- [**內建可觀察性**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) — 結合來自多個來源的記錄資料以幫助您管理網站效能和診斷問題的工具
- [**全面的API涵蓋範圍**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)及[REST](https://developer.adobe.com/commerce/webapi/rest) API，整合核心Commerce應用程式與協力廠商系統，並延伸Commerce功能

## 與Experience Cloud整合

Adobe Commerce與所有Experience Cloud解決方案整合，以大規模提供[個人化商務體驗](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu)。

[Data Connection](https://experienceleague.adobe.com/en/docs/commerce/data-connection/overview)可解鎖有關購物者購買行為的深入分析，以便您可以使用其他Adobe Digital Experience產品跨所有管道建立個人化購物體驗。

>[!NOTE]
>
>如需詳細資訊，請參閱下列資源：
>
>- [數位體驗藍圖](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview)，以取得更多技術細節。
>- 請參閱[個人化客戶體驗](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization)。


## 與協力廠商系統整合

Adobe為開發人員提供全方位的擴充點和工具，以便建立可擴充核心Commerce功能及將Commerce與協力廠商系統（例如CRM、ERPS和PIMS）整合的應用程式。 這些工具可透過下列方式降低平台的總體擁有成本：

- **擴充性** — 應用程式可與核心軟體分開擴充，以提升效率並簡化升級。
- **隔離** — 隔離的環境表示開發人員可以自行升級或修改其擴充功能，而不需依賴核心版本。
- **技術獨立性** — 開發人員可以選擇任何符合其需求的技術棧疊和程式碼語言。

Adobe提供下列開發人員工具，用於建立整合與自訂：

- 適用於Adobe Developer App Builder的&#x200B;[**API Mesh**](https://developer.adobe.com/graphql-mesh-gateway/) — 協調多個API、GraphQL、REST和其他來源並將其合併為單一、可查詢的GraphQL端點。
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) — 建置並部署安全且可擴充的Web應用程式，這些應用程式可擴充Commerce功能並與協力廠商解決方案整合。
- [**事件**](https://developer.adobe.com/commerce/extensibility/events/) — 使用自訂事件觸發程式與其他可擴充的開發工具互動。
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) — 使用Webhook自動觸發Commerce與協力廠商系統之間的互動。
- [**管理UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) — 使用商戶的新頁面和功能，自訂並增強Commerce管理。
- [**整合入門套件**](https://developer.adobe.com/commerce/extensibility/starter-kit/) — 透過參考整合、上線指令碼和標準化架構，加速您的Backoffice整合。

>[!NOTE]
>
>請參閱[現代方法：在Adobe Commerce中有效的擴充性](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility)。

## 店面服務

Adobe提供一套豐富的智慧型可撰寫商品化服務，協助您支援關鍵業務目標。 這些服務也提供對大規模最佳化效能至關重要的應用程式開發介面。

- [即時搜尋](https://experienceleague.adobe.com/en/docs/commerce/live-search/overview) — 使用此AI支援的搜尋工具，為購物者提供更聰明、更快速且相關的結果。
- [產品推薦](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/overview) — 根據購物者行為、熱門趨勢、產品相似性等新增AI輔助推薦。
- [目錄服務](https://experienceleague.adobe.com/en/docs/commerce/catalog-service/guide-overview) — 提供客戶最佳化的產品體驗，同時提升效能、改善擴充能力，並提高轉換率。
- [付款服務](https://experienceleague.adobe.com/en/docs/commerce/payment-services/guide-overview) — 提供多種付款方式，包括免息分期付款，以及付款處理、訂單和發票的單一檢視，以提升客戶滿意度。

## Headless店面

Headless商務是API優先的商務。 Adobe Commerce採用分離式架構，可透過GraphQL API層提供所有商務服務和資料，提供完整的Headless。 此架構可讓團隊獨立於核心應用程式開發前端，提供使用新興技術快速建立和測試新接觸點的靈活性。

Adobe提供現代化的headless storefront技術，其優點與功能與[Edge Delivery Services](https://www.aem.live/home)相同，包含檔案式撰寫、效能優先的架構，以及現成可用的原生實驗。 它運用Adobe Commerce [店面服務](#storefront-services)的規模與效能，以及[插入式元件](https://experienceleague.adobe.com/developer/commerce/storefront/)的彈性和便利性，提供商務功能。

