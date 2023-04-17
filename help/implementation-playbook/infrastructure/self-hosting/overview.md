---
title: 自行托管概觀
description: 了解要考慮的自行托管最佳實務。 主題範圍從安全元素到災難恢復等。 這些主題旨在協助決定自行托管其版本Adobe Commerce的公司。 所呈現的項目並非全部包羅永珍，但應提供一系列完善的概念，以促進一個安全、穩定且可復原的網站。
landing-page-description: 了解自行托管Adobe Commerce時應考量的一些概念和事項。
short-description: 了解自行托管Adobe Commerce的策略和概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ef89ace2f03d5010384ba759e81695b6ae7e630b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# 自行托管Adobe Commerce概觀

在考慮轉向Adobe Commerce等電子商務平台時，您有選擇。 但是，隨著這些選擇的出現，需要考慮的成本、風險和責任也隨之增加。 托管商務網站可使用封裝解決方案完成，例如 [Adobe Commerce雲基礎架構](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}，基礎架構、伺服器、電子郵件、SSL憑證等均已預先設定並準備好使用。 在雲端基礎架構上尋找良好的托管解決方案(例如Adobe Commerce)可讓整個程式更輕鬆，但自行托管您的Commerce網站有充分的理由。 隨附的頁面中包含許多主題，提供自我托管所提供之服務、技術和概念的深入分析和指引。 此處的資訊並非詳盡無遺，且您不應實作所有建議。 不過，這些文章可協助您了解可讓Adobe Commerce自行托管作業盡可能穩定和安全的概念。

若您不打算在雲端基礎架構上使用Adobe Commerce，則使用的辭彙為自行托管或內部部署，或甚至使用內部部署。 內部部署不僅指公司所擁有建築中的資料中心。 此術語代表Adobe Commerce未管理其基礎架構支援的任何項目。 有些代管公司適合Adobe Commerce，也被視為自行托管或內部托管。

關於Adobe Commerce和Magento開放原始碼，提供的大部分建議和秘訣適用於任一版本。 儘管它可能不會直接說明這一點，但人們的期望是，它適用於兩者。 在Adobe Commerce的自行托管選項主題中，會考量兩個版本。 最後，大多數話題都與 [Adobe Commerce雲基礎架構](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} 被選作托管提供者。

## 術語級別集

在與DevOps團隊討論及與公司支援合作時，下列詞語在Experience League文章中經常使用：

* **DevOps** 是一個術語，用來說明負責處理伺服器設定、設定、管理、SSL憑證，以及執行Adobe Commerce網站所用實際伺服器和服務之其他一切的團隊。 此術語用於幫助指定開發人員的責任通常何時終止以及基礎架構團隊的分級和支援何時開始。

* **安全性概念** 包括在伺服器上建立Adobe Commerce代碼庫、檔案和檔案系統的幾個主題和注意事項，以及減少許多已知利用漏洞模式攻擊面的任何配置或更新。

* **監控工具** 涵蓋監控Adobe Commerce網站的一些現有工具和服務。 這些工具有時可提供改善項目、揭露問題和安全弱點的秘訣。

* **災難恢復** 有助於為損壞或已利用的項目的不幸事件提供一些概念和考慮。

* **效能提示** 提供一些專業提示和指引，讓Adobe Commerce應用程式盡可能發揮效能。

* **壞演員** 是用於嘗試執行惡意或未授權操作的人員或團隊的術語。 它不僅限於商務應用程式，還延伸到基礎架構或與網站相關的任何元件。

* **Web應用程式防火牆** (WAF)可協助您觀看商務應用程式的每個請求標題，並封鎖已知的模式和漏洞。 WAF通常與自訂篩選器和規則搭配使用，以協助管理DDOS攻擊。

* **分佈式拒絕服務** (DDoS)是一種攻擊方法，可強制執行網站的伺服器使用數量足夠的錯誤請求，使其無法再回應合法請求。

## 接下來呢？

這些主題不按任何特殊順序或順序排列。 這些建議旨在為DevOps工程師、商務架構師以及參與決定在何處及如何托管Adobe Commerce的其他任何人提供談話要點。

{{$include /help/_includes/hosting-related-links.md}}
