---
title: 耦合式店面體系結構
description: 瞭解在無頭的Adobe Commerce體系結構中，耦合的店面意味著什麼。
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 耦合（傳統）Adobe Commerce店面結構

大多數商業客戶的當前預設部署選項包括：

- 跨B2B和B2C的100%功能支援
- 可快速部署/自定義的成熟參考主題(Luma)
- 成熟的SI合作夥伴實施專業知識
- 與Page Builder或Staging &amp; Preview等商業功能完全相容
- 與Adobe Commerce市場擴展的廣泛相容性

![顯示耦合的Adobe Commerce店面結構的圖](../../../assets/playbooks/coupled-storefront-architecture.svg)

## 舊店面的缺點

- **非無頭** — 整體Adobe Commerce應用程式的所有部分。 前端和後端之間沒有業務邏輯和流程的分離。

- **非PWA** — 儘管主題響應快，但站點效能遠遠落後於同類最佳PWA。

- **前端體系結構(Adobe CommerceUI元件)**—Adobe Commerce/PHP專家將在舊店面的基礎上再接再厲。

在進入無頭區之前，讓我們從更熟悉的店面結構開始。 如果無頭設備被解耦，則這將是耦合的店面體系結構，最常見的是我們的Luma演示。

這就是店面功能與核心商務服務緊密整合的地方，而不是由該GraphQL API層分隔。 所以，很多商業邏輯和這個主題相結合。 這種方法不是毫無頭緒的，也不是PWA。

這是目前最常被商戶使用的選項，因為它100%都支援B2B和B2C Commerce功能。 該社區對此很熟悉，其周圍有成熟的專業生態系統，它與Adobe Commerce市場的擴展有廣泛的相容性。

但是，它沒有我們前面講到的好處。 如果不分層，則在進行更改時會存在許多從屬關係和潛在故障點。 它不像一個實施良好的PWA那樣出色，如果某家商家在Adobe Commerce或PHP開發方面沒有專業知識，他們就必須去尋找這些資源。
