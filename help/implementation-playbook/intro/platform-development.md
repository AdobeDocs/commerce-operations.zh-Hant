---
title: 平台開發原則
description: 瞭解使用Adobe Commerce時的基本平台開發原則。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 3c1a49c2dc3dc0d3d47e16c724d4099b6a456c77
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# 平台開發原則

本主題將深入探討Adobe Commerce開發的一些主要標準，包括：

- 符合開發流程的功能和技術範圍
- 符合MVC架構的開發最佳實務
- 架構考量，包括GRA
- 針對指令碼和漏洞的安全標準
- 擴充功能開發最佳實務
- Web API與REST、SOAP和GraphQL整合
- 針對編碼和基礎建設的效能改良
- 測試工具、策略和方法

雖然某些解決方案實作者在方法、流程和工具方面可能有自己的偏好，但本行動手冊的重點是可在大多數實作中分享的公認最佳實務和方法。

就像任何大型IT專案一樣，Adobe Commerce是以使用最佳實務和標準化的編碼標準，以及已在Adobe Commerce中建立的標準為基礎而建置 [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/). 遵循這些標準對於消除錯誤以及改善自訂建置計畫碼的品質和可維護性非常重要。

## 雲端基礎結構上的Adobe Commerce

雲端基礎結構上的Adobe Commerce是適用於Adobe Commerce軟體的受管理、自動化託管平台。 雲端基礎結構上的Adobe Commerce提供各種功能，使其有別於內部部署Adobe Commerce和Magento Open Source實作。 請參閱 [雲端指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/overview.html).
