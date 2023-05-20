---
title: 自主承載概述
description: 瞭解要考慮的自我托管最佳做法。 主題範圍從安全元素到災難恢復等。 這些主題是為了幫助一家決定舉辦自己版本的Adobe Commerce的公司。 所介紹的項目並非全包，但應提供一系列好的概念，以促進一個安全、穩定和有彈性的網站。
landing-page-description: 學習一些概念和事情，在您自己主持Adobe Commerce會議時考慮。
short-description: 瞭解自己主持Adobe Commerce的戰略和概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 63f552f3-836c-4a07-96c3-c0e00614fe39
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# 自辦Adobe Commerce概述

考慮轉向Adobe Commerce等電子商務平台時，你有很多選擇。 但是，隨著這些選擇的到來，還有額外的成本、風險和負債需要考慮。 可以使用打包的解決方案(如 [Adobe Commerce在雲基礎架構上](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}，其中基礎架構、伺服器、電子郵件、SSL證書等已預先配置並可供使用。 在雲基礎架構上找到一個好的托管解決方案(如Adobe Commerce)使整個過程更加輕鬆，因此您有充分的理由自行托管您的Commerce站點。 在隨附的頁面中，有許多主題提供了自我托管所提供的服務、技術和概念的洞察和指導。 此處的資訊並非詳盡無遺，因此您不應該執行所有建議。 但是，這些文章可以幫助您理解使Adobe Commerce自主托管盡可能穩定和安全的理念和概念。

當您不與Adobe Commerce在雲基礎架構上合作時，使用的術語是自主托管或內部部署，甚至是在預先使用。 內部部署不僅意味著公司擁有的建築物中的資料中心。 這個詞代表了Adobe Commerce在基礎設施方面未予管理的任何支援。 有一些為Adobe Commerce服務的東道公司，它們也被視為自主或隨機。

關於Adobe Commerce和Magento開源，大多數建議和提示都適用於任何版本。 儘管它可能不會直接聲明，但人們期望它適用於兩者。 在Adobe Commerce自主承載選項這一主題中，考慮了兩個版本。 最後，大多數話題都與 [Adobe Commerce在雲基礎架構上](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} 已選擇為宿主提供程式。

## 術語級別集

在與DevOps團隊交談和與公司支援合作時，以下術語通常在Experience League文章中使用：

* **開發操作** 是一個術語，用於描述處理伺服器設定、配置、管理、SSL證書以及用於運行Adobe Commerce站點的實際伺服器和服務的其他一切的團隊。 此術語用於幫助指定開發人員的責任通常何時結束以及基礎架構團隊的分類和支援開始的位置。

* **安全概念** 包括幾個主題和注意事項，用於在伺服器上建立Adobe Commerce代碼庫、檔案和檔案系統，以及減少許多已知利用漏洞模式攻擊面的任何配置或更新。

* **監控工具** 包括一些監控Adobe Commerce網站的現有工具和服務。 這些工具有時可以提供一些提示，說明如何改進、發現問題和安全漏洞。

* **災難恢復** 有助於為損壞或被利用的項目的不幸事件提供一些概念和考慮。

* **效能提示** 為使Adobe Commerce應用程式盡可能發揮效能提供一些專業提示和指導。

* **壞演員** 是用於試圖做惡意或未經授權的事的人或團隊的術語。 它不僅限於商業應用，還延伸到基礎設施或與網站相關的任何元件。

* **Web應用程式防火牆** (WAF)通過監視指向商業應用程式的每個請求標題並阻止已知模式和漏洞利用來提供幫助。 通常，WAF與自定義篩選器和規則結合使用，以幫助管理DDOS攻擊。

* **分佈式拒絕服務** (DDoS)是一種攻擊方法，它強制運行網站的伺服器使用足夠數量的虛假請求，使其無法再響應合法請求。

## 下一步是什麼？

這些主題不按任何特殊順序或順序排列。 他們應該與DevOps工程師、 Commerce Architect以及參與決定在何處以及如何接待Adobe Commerce的其他任何人提供談話要點。

{{$include /help/_includes/hosting-related-links.md}}
