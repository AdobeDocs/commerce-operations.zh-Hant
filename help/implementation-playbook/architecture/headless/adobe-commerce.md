---
title: 無頭Adobe Commerce建築
description: 瞭解是什麼讓Adobe Commerce的無頭架構方法獨一無二。
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# 無頭Adobe Commerce建築

Adobe Commerce建築的好處是，它不是一個「要麼全有」或「一無所有」的命題，而且商家可以為其業務找到合適的解決方案組合。 他們可以構建一個PWA Studio驅動的PWA，以獲得主站點體驗，或者將Adobe Experience Manager作為複雜客戶旅程的一層，同時構建一個定製前端，以試驗新的觸地點。 沒有其他平台能與Adobe Commerce無頭架構提供的市場優勢和靈活性相媲美。

![示出無頭的Adobe Commerce店面體系結構的圖](../../../assets/playbooks/headless-storefront-architecture.svg)

每種方法並不互斥。 客戶可以構建自己的前端（頭部）、使用PWA Studio獲得網路/移動體驗，和/或使用Adobe Experience Manager獲得玻璃（採用完整部署或混合部署）。

Adobe Commerce始終允許使用REST API進行無頭部署。 儘管REST功能強大，特別是對於批量處理，但在無頭方面，GraphQL API通過直觀的開發人員體驗實現了更快的開發，允許不影響現有API的更改而實現更大的靈活性，以及通過將檢索到的資料量減少到所需的資料量而實現更好的效能。

GraphQL是效能API的行業標準，它被許多頂級電子商務平台所使用。 這是件好事，因為這意味著這是一個經過驗證的解決方案並且市場上存在專業知識。

雖然Adobe Commerce確實有一個耦合的店面，但商人並不需要使用Adobe Commerce的傳統店面。 商戶可以利用Adobe Commerce一流的商務服務來處理後端業務流程，並使用我們的店面API整合他們自己解耦的店面，以推動前端體驗。

現在，我們來看看各種無頭的選擇。

## PWA Studio

第一個是使用PWA Studio構建的漸進式Web應用程式。 部分原因在於PWA是與商業後端分離的無頭店面。 借助PWA Studio，商戶可以在Adobe Commerce之上構建高效能、可靠且經濟高效的PWA，在移動和案頭上提供一流的網路體驗。 隨著時間的推移，這將超過耦合的店面，作為預設選項。

大多數商戶都瞭解該行業在PWA方面的發展方向，許多潛在的阻塞劑正在迅速被移除。

一週比一週，在PWA Studio領域積累專業技能的合作夥伴數量不斷增加，而且客戶推出數量也在不斷增加。 最近對PWA Studio的更新包括擴展性，這些擴展性將有助於在與Adobe Commerce市場擴展的相容性方面取得重大進展。

許多商家可能覺得，他們還沒有準備好迎接無頭和PWA，因為他們需要嚴重依賴開發商。 同時擁有Adobe Commerce開發的商業應用程式和主管的巨大好處之一是，它有助於確保跨商業能力的相容性。

為了讓PWA更易於訪問和更便於我們的商家管理，我們授權業務用戶管理日常內容更改、建立新登錄頁，以及更多使用頁面生成器。 這兩項強大功能共同使所有設備和體驗都能快速進入市場。

## Adobe Experience Manager

Adobe Experience Manager是滿足您內容和數字資產管理需求的強大組合，它幫助商家更快地將個性化、內容導向的體驗推向市場，將數字資產管理與機器學習、Adobe Sensei支援的內容和客戶行程管理的強大功能相結合。

Adobe Commerce加Adobe Experience Manager是一個強有力的故事，因為商務引擎使企業能夠通過由Adobe Experience Manager提供動力的客戶介面來促進商業。

## 自定義頭

此處討論的最後一個選項是構建自定義前端的選項。 這一選擇適用於那些擁有現有專業知識的企業和擅長特定前端堆棧的內部開發商，如React。 如果他們不具備Adobe Commerce傳統前端開發方面的技能，他們就會認定，構建自己的定製React前端更具成本效益。

當然，此模型需要強大的客戶或系統整合前端開發技能和資源，而您無法從本機相容性中獲益，因為您需要PWA Studio的頁面生成器之類的功能。 一旦商家建立完全的定製，他們就可能失去上市時間優勢。

定制前端還支援創新和實驗。 AR/VR或語音商務被大家所談論，而像Adobe Commerce這樣的體系結構讓商家能夠探索這些選擇，而不會影響他們現有的網店。
