---
title: Adobe Commerce微服務
description: 能夠區分Headless與Adobe Commerce相關的微服務。
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
feature: Integration, Services
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Headless和微服務

切勿將Headless與微服務混淆。 很多時候，我們會在與Headless相同的句子中聽到有關微服務的對話。 它們是完全不同的事物。 它們可以搭配使用，但概念完全不同。

微服務架構是一個術語，用來描述將應用程式分割成一組較小的、鬆散耦合服務的做法。 微服務可讓個別後端服務變成：

- **彼此隔離** — 例如，訂價服務與目錄服務沒有相依性。

- **部署單點** — 客戶只部署他們需要的應用程式部分。

- **獨立縮放** — 可以將資源指定給高需求服務，例如存貨查詢。

- **自主開發** — 可相互獨立地開發和部署。

微服務與切掉商務棧疊或API的頭無關。 當我們思考位於Adobe Commerce後台的核心程式碼中的商業服務時，就是將這些服務彼此隔離。 因此，微服務架構正在鬆散地分解所有服務，例如定價服務、目錄服務和存貨服務，並使每一項服務彼此隔離。

微服務可獨立擴充及自主開發。 微服務類似於多租使用者SaaS開發流程。 許多現代多租使用者SaaS產品都是使用多服務方法開發的。 甚至Adobe自己的SaaS產品（例如Order Management）、全新AI驅動的產品Recommendations工具，以及Adobe Commerce的其他SaaS元件，也正使用微服務方法進行開發。 需要澄清的是，Adobe Commerce 2.4.x並非微服務架構，而是Headless架構。
