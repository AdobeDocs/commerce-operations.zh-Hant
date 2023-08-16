---
title: 自行託管概述
description: 瞭解自託管最佳實務，供您考慮。 從安全性元素到災難回覆，主題涵蓋範圍甚廣。 這些主題旨在協助已決定託管自身Adobe Commerce版本的公司。 呈現的專案並非全包容，但應提供各種良好的概念，以推廣安全、穩定且可復原的網站。
landing-page-description: 瞭解自行託管Adobe Commerce時應考量的一些概念與事項。
short-description: 瞭解自行託管Adobe Commerce的策略和概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 63f552f3-836c-4a07-96c3-c0e00614fe39
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# 自行託管Adobe Commerce概述

考慮改用Adobe Commerce等電子商務平台時，擁有眾多選擇。 但是，有了這些選項，我們還要考慮額外的成本、風險和負債。 託管Commerce網站可使用封裝解決方案完成，例如 [雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}，基礎架構、伺服器、電子郵件、SSL憑證等已預先設定且可供使用。 在雲端基礎結構上尋找Adobe Commerce等良好的託管解決方案可讓整個程式更容易，有一些極具吸引力的原因可讓您自行託管您的商務網站。 在隨附的頁面中，有許多主題可針對自行託管所提供的服務、技巧和概念提供深入分析和指引。 這裡的資訊並非詳盡無遺，您也不應實作所有建議。 不過，這些文章可協助您瞭解讓Adobe Commerce自行託管儘可能穩定且安全的構想和概念。

若您未使用雲端基礎結構上的Adobe Commerce，則使用的字詞為自行託管或內部部署，或甚至使用內部部署。 內部部署不只代表公司擁有的大樓內的資料中心。 此辭彙代表任何非由Adobe Commerce管理的基礎架構支援。 有些託管公司是針對Adobe Commerce所用，也視為自行託管或內部部署。

關於Adobe Commerce和Magento開放原始碼，大多數建議和提示都適用於任一版本。 雖然其可能不會直接說明，但預期兩者皆適用。 在有關Adobe Commerce的自家託管選項的主題中，會同時考慮兩個版本。 最後，大多數主題都與以下內容相關： [雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} 已選取作為託管提供者。

## 術語層級集

下列辭彙在Experience League文章中經常使用，在與DevOps團隊交談以及搭配公司支援時也會使用：

* **DevOps** 這個術語用來描述處理伺服器設定、設定、管理、SSL憑證，以及有關執行Adobe Commerce網站所使用之實際伺服器和服務的所有其他專案的團隊。 這個術語是用來協助指定開發人員的責任通常何時結束，以及基礎架構團隊的分級和支援從何處開始。

* **安全性概念** 包含數個主題和考量事項，以利在伺服器上建立Adobe Commerce程式碼基底、檔案和檔案系統，以及任何可減少許多已知利用漏洞模式的攻擊面的設定或更新。

* **監控工具** 涵蓋數個監控Adobe Commerce網站的現有工具與服務。 這些工具有時可提供如何改善事物的提示，或揭示問題和安全性漏洞。

* **災難回覆** 有助於提供某些概念和考量事項，以因應專案損毀或被利用的不幸事件。

* **效能提示** 提供一些專業秘訣和指引，讓Adobe Commerce應用程式發揮儘可能高的效能。

* **不好的執行者** 是用來指稱企圖進行惡意或未經授權之行為的人或團隊。 不僅限於商務應用程式，也延伸至基礎架構或任何與網站相關的元件。

* **Web應用程式防火牆** (WAF)可協助您檢視商務應用程式的每個請求標題，並封鎖已知模式和漏洞。 通常WAF會與自訂篩選器和規則搭配使用，以協助管理DDOS攻擊。

* **分散式拒絕服務** (DDoS)是一種攻擊方法，可強制執行網站的伺服器以錯誤的要求來使用，且容量足以讓伺服器無法再回應合法的要求。

## 接下來呢？

這些主題並沒有任何特殊順序或順序。 這些簡報旨在向DevOps工程師、商務架構師，以及參與此重要決定(主辦Adobe Commerce的位置和方式)的任何人，提供談話要點。

{{$include /help/_includes/hosting-related-links.md}}
