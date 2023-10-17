---
title: 產品可用性
description: 瞭解目前支援的Adobe Commerce功能，並檢查其與特定Adobe Commerce版本的相容性。
exl-id: 7e8e8ac2-a0b9-4023-a813-c0f1293e54c2
source-git-commit: df4a4b419fbd5780a98e062a12cb22c3bc9913a0
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 13%

---

# 產品可用性

下表說明Adobe Commerce軟體可用性的狀態以及取得該軟體的位置，尤其是傳統Adobe Commerce Composer套件外部提供的軟體。

服務和擴充功能會在產品發行時於最新發行版本的Commerce上測試。

Adobe已完整測試支援的版本。 Adobe客戶支援可提供支援版本的協助。 較舊版本或許可以正常運作，但並不正式支援。

>[!NOTE]
>
>對Adobe Commerce版本的支援還包括對 [可用的安全性修補程式](versions.md).

## Adobe編寫的擴充功能

這些Adobe Commerce擴充功能與核心Adobe Commerce程式碼基底脫鉤。 這可讓Adobe在更靈活的時間範圍內發佈這些擴充功能的反複專案，並讓客戶更早存取新功能。


下表顯示與Adobe Commerce版本相關的每個擴充功能的版本支援。

| **Adobe Commerce版本** | 2.4.7-beta2 | 2.4.6 | 2.4.5 | 2.4.4 |                                                                                                                                                                                                                                          |
|---------------------------------------|-------------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Adobe Commerce的Adobe I/O事件_ | 1.3.0 | 1.3.0 | 1.3.0 | 1.3.0 | [作曲者](https://developer.adobe.com/commerce/extensibility/events/installation/) <br/>[發行說明](https://developer.adobe.com/commerce/extensibility/events/release-notes/) |
| _B2B_ | 1.4.2 | 1.3.5+ | 1.3.4 | 1.3.3 | [作曲者](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html) <br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html) |
| _Experience Platform聯結器_ | 3.0.0-beta1 | 1.0.0+ | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html)<br/>[發行說明](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/release-notes.html) |
| _頁面產生器_ | - | 1.7.3 | 1.7.2 | 1.7.1 | [使用者指南](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/guide-overview.html)<br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/release-notes.html) |

## Commerce服務

[Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html) 是一套Adobe託管功能，結合您的Commerce執行個體，提供強大的功能及快速的回應時間。

建議商戶使用最新版本的服務，以確保最高的穩定性和功能。 本檔案說明目前發行的版本。

* Adobe Commerce服務目前與Commerce 2.4.4和更新版本相容。 建議商戶使用最新版服務。
* 系統將服務視為與舊版Commerce 2.4.x相容，但並不正式支援。
* 服務與Commerce 2.3.x不相容，除了產品Recommendations 3.3.7和更早版本。

下表顯示各服務相對於Adobe Commerce版本的版本支援。

| **Adobe Commerce版本** | 2.4.7-beta2 | 2.4.6 | 2.4.5 | 2.4.4 |                                                                                                                                                                                                                                                |
|----------------------------------------|-------------|--------|-----------------|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _AmazonSales Channel_ | - | 4.4.0+ | 4.3.0+ | 4.3.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-module-amazon.html)<br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-channels/amazon/release-notes.html) |
| _適用於Adobe Commerce的目錄服務_ | 1.13 | 1.13 | 1.13 | 1.13 | [概觀](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/guide-overview.html)<br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/release-notes.html) |
| _頻道管理員_ | 2.1.0 | 2.0.0 | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-channel-manager.html)<br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/release-notes.html) |
| _即時搜尋_ | 3.1.1 | 3.1.1 | 3.1.1 | 3.1.1 | [Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)<br/>[發行說明](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) |
| _付款服務_ | 2.2.0 | 2.2.0 | 2.2.0 (PHP 8.1) | 2.2.0 (PHP 8.1) | [Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html)<br/> [發行說明](https://commercemarketplace.adobe.com/magento-payment-services.html) |
| _產品Recommendations_ | 5.0.1 | 5.0.1 | 5.0 .1 | 5.0.1 | [Marketplace](https://commercemarketplace.adobe.com/magento-product-recommendations.html)<br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _快速簽出_ | - | 1.0.0+ | 1.2.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-quick-checkout.html)<br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _Adobe Commerce 的 Store Fulfillment_ | - | 1.5.0 | 1.2.0+ | 1.2.0+ | [Marketplace](https://commercemarketplace.adobe.com/store-fulfillment-magento-walmart.html)<br/> [發行說明](https://experienceleague.adobe.com/docs/commerce-merchant-services/store-fulfillment/release-notes.html) |
