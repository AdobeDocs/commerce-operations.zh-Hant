---
title: 大規模提供體驗
description: 學習如何與Adobe Commerce和Adobe Experience Manager進行大規模交流。
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 通過Adobe Commerce、商業整合框架和Adobe Experience Manager提供大規模體驗

建議將CIFAEM用作連接器的Adobe Commerce和Compers之間的整合模式AEM是，將展示層（「玻璃」）和Commerce後端作為「無頭」後端來提供電源。 此整合方法充分利用了每個應用程式的優勢：Adobe Commerce電子商務運營的創AEM作、個性化和人文功能。

在AEM/CIF/Adobe Commerce環境中，電子商務網站訪問者最初將抵AEM達。 將檢AEM查其調度程式快取中是否有可用的請求頁。 如果該頁面存在，則此快取的頁面將提供給訪問者，不需要進一步處理。 如果調度程式未包含請求的頁面，或者該頁面已過期，則調度程式會請求發佈程式生成該頁面AEM，發佈程式會呼叫Adobe Commerce以在必要時生成該頁面。 然後，將所構建的頁面傳遞給調度器以服務於訪問者，然後被快取，以防止在其他訪問者對同一頁面的後續請求上將進一步負載放置在伺服器上。

![Adobe經驗管理器和Adobe Commerce體系結構概覽圖](../assets/commerce-at-scale/overview.png)

伺服器端渲染和客戶端渲染的組合可用於AEM/CIF/Adobe Commerce模型：伺服器端呈現提供靜態內容和客戶端呈現，通過從用戶瀏覽器內直接調用Adobe Commerce特定元件來傳遞頻繁更改或個人動態內容。

在以下示例中，可以看到電子商AEM務店面上「產品詳細資訊」頁中不同元件的示例：

![Adobe經驗管理器和Adobe Commerce體系結構概覽圖](../assets/commerce-at-scale/product-details-page.svg)

## 伺服器端呈現

諸如產品詳細資訊頁面(PDP)和產品清單頁面(PLP)等電子商務頁面不太可能頻繁更改，並且適合於在使用AEMCIF核心元件呈現伺服器端後完全快取。 應使用中建立的通AEM用模板在發佈伺服器上呈AEM現頁。 這些元件通過GraphQL API從Adobe Commerce獲取資料。 這些頁面是動態建立的，呈現在伺服器上，快取在調AEM度器上，然後傳送到瀏覽器。 以上示例的紫色框中顯示了此示例。

## 客戶端呈現

在顯示更多動態屬性（如庫存水準/可用性或價格）的情況下，例如在產品詳細資訊頁面(PDP)上，可以使用客戶端元件。 雖然可以使用上述伺服器端呈現方法在調度器上構建和快取模板頁，但在靜態頁本身中可以有動態客戶端web元件。 這些動態元件可以通過GraphQL API直接在客戶端瀏覽器中從Adobe Commerce獲取資料，以在PDP上即時檢查當前價格或庫存水準。 這可確保在頁面載入時始終讀取通常對即時顯示至關重要的內容。 以上示例的紅色框中顯示了此示例。

在檢出過AEM程中，還可以使用模板和客戶端渲染的組合：客戶端購物車元件呈現購物車、結帳表以及與支付服務提供商的整合。 此混合方法還可用於Adobe Commerce的帳戶管理功能，如建立帳戶、登錄帳戶和忘記密碼。
