---
title: 大規模提供體驗
description: 瞭解如何使用Adobe Commerce和Adobe Experience Manager大規模提供體驗。
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 使用Adobe Commerce、Commerce integration framework和Adobe Experience Manager大規模提供體驗

建議使用CIF作為聯結器的AEM與Adobe Commerce之間的整合模式，是讓AEM擁有展示層（「玻璃」）和Adobe Commerce，將商業後端作為「無頭式」後端來提供。 此整合方法利用了每個應用程式的優勢：AEM的編寫、個人化和全通路功能，以及Adobe Commerce的電子商務操作。

在AEM/CIF/Adobe Commerce環境中，電子商務網站的訪客將最先到達AEM。 AEM將檢查其Dispatcher快取中是否有請求的頁面可用。 如果頁面存在，則會將此快取頁面提供給訪客，不需要進一步處理。 如果Dispatcher不包含請求的頁面或頁面已過期，則Dispatcher會請求AEM發佈者建立頁面，發佈者會呼叫Adobe Commerce以取得電子商務資料，並視需要建立頁面。 隨後構建的頁面會傳遞給Dispatcher以提供給訪客，然後會進行快取，以防止其他訪客後續對相同頁面提出請求時，需要將進一步的載入放置到伺服器上。

![AdobeExperience Manager與Adobe Commerce架構的概觀圖表](../assets/commerce-at-scale/overview.png)

AEM/CIF/Adobe Commerce模式中可以使用伺服器端轉譯和使用者端轉譯的組合：伺服器端轉譯可直接呼叫特定元件的Adobe Commerce，提供靜態內容和使用者端轉譯，提供經常變更或個人動態內容
從使用者的瀏覽器中。

在以下的範例中可以看到AEM電子商務店面範例上，產品詳細資料頁面中不同元件的範例：

![AdobeExperience Manager與Adobe Commerce架構的概觀圖表](../assets/commerce-at-scale/product-details-page.svg)

## 伺服器端轉譯

電子商務頁面(例如產品詳細資料頁面(PDP)和產品清單頁面(PLP))不太可能經常變更，適合在使用AEM CIF核心元件在伺服器端轉譯後完全快取。 頁面應使用在AEM中建立的通用範本在AEM Publisher上呈現。 這些元件會透過GraphQL API從Adobe Commerce取得資料。 這些頁面會以動態方式建立、在伺服器上呈現、在AEM Dispatcher上快取，然後傳送給瀏覽器。 以上範例中的紫色方塊中顯示了這方面的範例。

## 使用者端轉譯

在顯示較動態屬性（例如庫存量/可用性或價格）時(例如在產品詳細資料頁面(PDP))，可以使用使用者端元件。 雖然範本頁面可以在Dispatcher上使用上述伺服器端轉譯方法建置和快取，但在靜態頁面本身中可以有動態使用者端Web元件。 Adobe Commerce這些動態元件可透過GraphQL API，在使用者端的瀏覽器中直接擷取資料，以即時檢查PDP上的目前價格或庫存量。 這可確保在頁面載入時，一律會擷取通常重要且要即時顯示的內容。 以上範例中的紅色方塊中顯示了這方面的範例。

結帳過程中也可以使用AEM範本和使用者端轉譯的組合：使用者端購物車元件轉譯購物車、結帳表單以及與支付服務提供者的整合。 此混合方法也可用於Adobe Commerce的帳戶管理功能，例如建立帳戶、登入帳戶及忘記密碼。
