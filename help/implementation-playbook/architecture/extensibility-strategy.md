---
title: Adobe Commerce擴充性策略
description: 瞭解Adobe Commerce的擴充性模型如何讓您能夠自訂實作。
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 擴充性策略

Adobe Commerce的可擴充性平台可讓品牌有效率地自訂程式、整合系統，以及部署新功能，同時維持可升級性。

## Commerce擴充功能策略概觀

擴充Commerce平台功能包含下列高階方法：

* 擴充Commerce平台的原生功能。 例如，商家可以安裝Marketplace應用程式（通常由第三方建立），以擴充和調整平台的原生功能，例如可在結帳時驗證運送地址，以及促進與UPS電信業者地址API快速整合的擴充功能。

* 將協力廠商應用程式/擴充功能與Commerce平台整合。 開發人員可以使用Commerce的現有、完整REST和GraphQL API，直接將Commerce與協力廠商解決方案整合。

然而，平台架構決定了擴充平台的最佳策略。 Commerce為Headless部署提供豐富的GQL和REST API涵蓋範圍。 核心Commerce程式碼庫繼續向模組化架構和單一整合層發展，提供新的、改良的自訂工具：

* [適用於Adobe Commerce的App Builder](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) 是以Adobe基礎結構為基礎的開發架構和工具集。 開發人員可利用它來建立Commerce擴充功能，範圍包含使用者體驗/店面自訂、中介軟體和商業邏輯擴充功能等。

* [Adobe Developer App Builder的API網格](https://developer.adobe.com/graphql-mesh-gateway/) 可讓開發人員將多個資料來源合併為單一API端點。 這支援私人和第三方API的API協調，或整合，以及其他使用Adobe I/O的Adobe Commerce API和Adobe產品的軟體介面。

* [Adobe Commerce的Adobe I/O事件](https://developer.adobe.com/commerce/events/get-started/) 讓使用App Builder和協力廠商Web鉤點開發的應用程式可以使用交易式資料，支援建立事件驅動的應用程式。

這些工具可讓您存取Adobe Developer主控台和Adobe開發人員工具，以建立API並整合自訂外掛程式和整合。

下圖著重說明Commerce擴充功能策略的主要元件。

![Adobe Commerce擴充功能策略圖](../../assets/playbooks/extensibility-strategy-overview.png)
