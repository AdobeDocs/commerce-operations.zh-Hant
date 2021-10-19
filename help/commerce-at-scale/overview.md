---
title: 大規模提供體驗
description: 了解如何使用Adobe Commerce和Adobe Experience Manager大規模提供體驗。
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 透過Adobe Commerce、Commerce Integration Framework和Adobe Experience Manager大規模提供體驗

使用CIF作為連接器的AEM與Adobe Commerce之間，建議採用整合模式，讓AEM擁有展示層（「玻璃」）和Adobe Commerce，將商務後端作為「無頭」後端提供支援。 此整合方法充分利用了每個應用程式的優勢：Adobe Commerce AEM和電子商務營運的製作、個人化和全通路功能。

在AEM/CIF/Adobe Commerce環境中，電子商務網站訪客最初將抵達AEM。 AEM會檢查其dispatcher快取中是否有可用的請求頁面。 如果頁面存在，系統會向訪客提供此快取頁面，不需要進一步處理。 如果Dispatcher不包含請求的頁面，或該頁面已過期，則Dispatcher會請求AEM Publisher建置頁面，而Dispatcher會視需要呼叫Adobe Commerce，以取得電子商務資料來建置頁面。 接著，內建的頁面會傳遞至Dispatcher以提供給訪客，接著會進行快取，以避免在其他訪客對相同頁面提出後續請求時，將進一步的載入放置到伺服器上。

![AdobeExperience Manager與Adobe Commerce架構的概觀圖表](../assets/commerce-at-scale/overview.png)

AEM/CIF/Adobe Commerce模型中可結合使用伺服器端轉譯和用戶端轉譯：伺服器端轉譯，提供靜態內容，用戶端轉譯，從使用者的瀏覽器內直接呼叫Adobe Commerce以取得特定元件，以提供經常變更或個人的動態內容。

以下範例中會顯示AEM電子商務店面上產品詳細資料頁面中不同元件的範例：

![AdobeExperience Manager與Adobe Commerce架構的概觀圖表](../assets/commerce-at-scale/product-details-page.svg)

## 伺服器端轉譯

產品詳細資料頁面(PDP)和產品清單頁面(PLP)等電子商務頁面不太可能經常變更，且適合在使用AEM CIF核心元件在伺服器端轉譯後完全快取。 應使用在AEM中建立的一般範本，在AEM發佈商上轉譯頁面。 這些元件可透過GraphQL API從Adobe Commerce取得資料。 這些頁面會動態建立、在伺服器上轉譯、在AEM Dispatcher上快取，然後傳送至瀏覽器。 上述範例的紫色方塊中會顯示此範例。

## 用戶端轉譯

如果顯示更多動態屬性（例如庫存量/可用性或價格），例如在產品詳細資訊頁面(PDP)上，則可使用用戶端元件。 雖然您可以使用上述伺服器端轉譯方法在Dispatcher上建立和快取範本頁面，但在靜態頁面本身內，可能會有動態用戶端Web元件。 這些動態元件可透過GraphQL API，直接從用戶端的Adobe Commerce瀏覽器擷取資料，以便即時檢查（例如PDP上的目前價格或庫存水準）。 這可確保在頁面載入時一律會擷取通常對即時顯示而言至關重要的內容。 上述範例會顯示在紅色方塊中。

在結帳過程中，也可使用AEM範本和用戶端轉譯的組合：用戶端購物車元件可呈現購物車、結帳表單，以及與付款服務提供者的整合。 此混合方法也可用於Adobe Commerce的帳戶管理功能，例如建立帳戶、登入帳戶及忘記密碼。
