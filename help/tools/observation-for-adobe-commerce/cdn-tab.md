---
title: 此 [!UICONTROL CDN] 標籤
description: 瞭解 [!UICONTROL CDN] 標籤之 [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# 此 [!UICONTROL CDN] 標籤

此標籤包含著重在 [!DNL content delivery network (CDN)]. 在Adobe Commerce Cloud中，此為 [!DNL Fastly] 服務。

## [!UICONTROL HIT rate]

![點選率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

此 **[!UICONTROL HIT rate]** 影格顯示產生的可快取要求數目 [!UICONTROL HITS] 在最後一分鐘。 這表示快取成功。 向右箭頭會顯示一週前同一時間的上方或下方百分比。

## [!UICONTROL HIT Processing]

![點選處理](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

這個 **[!UICONTROL HIT processing]** 方塊顯示產生的可快取要求數目 [!UICONTROL HITS] 在一週內。

## [!UICONTROL MISS rate]

![未命中率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

這個 **[!UICONTROL MISS rate]** 方塊顯示最後一分鐘可快取要求的遺漏次數。 未命中是指未快取要求，且要求必須傳遞至原始伺服器以提供內容時。 右邊的值是一週前每分鐘增加/減少的分鐘數比較。

## [!UICONTROL MISS time]

![未命中時間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![點選率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![錯誤百分比](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

此 **[!UICONTROL Error Percentage]** 方塊顯示要求的ERROR百分比值，並顯示一週前同一時間的相對增加/減少。

## [!UICONTROL Total Requests]

![要求總數](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![錯誤率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![所選時段的快速快取平均回應（以秒為單位）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

此框架顯示可快取要求的持續時間（以秒為單位），這表示 `cache_response` 是 [!UICONTROL MISS]，它會顯示所選時間遺漏快取回應的平均值。

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Fastly快取所選時段的平均回應（以秒為單位），由POP分面](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![所選時間範圍內的總頻寬（所有POP），與1週前相比（增加/減少%）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![請求 — 自選取的時間範圍與一星期前比較](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

此框架類似於的摘要方塊 [!UICONTROL Total Requests] 位於頂端，但會顯示前幾週的請求計數。 這些全都是請求，而不僅僅是可快取請求(其中 `is_cacheable` 為true)。

## [!UICONTROL Response Count]

![回應計數](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![依POP區分的頻寬](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![前5大URL （5xx或3xx狀態代碼）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

此 **[!UICONTROL Top 5 URLs]** 檢視會顯示發生5xx或3xx錯誤回應的前5個URL。 由於空間限制，您需要將滑鼠移至URL上方，才能檢視與該URL相關聯的特定錯誤代碼。 （例如上圖紅色方塊中的）。

## [!UICONTROL Top 25 URLs (200 status)]

![前25個URL （200個狀態）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

此 **[!UICONTROL Top 25 URLs]** 影格會顯示在所選時間範圍內依計數傳回200狀態的URL。

## [!UICONTROL Duration by Response Status]

![依回應狀態的持續時間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

此 **[!UICONTROL Duration by Response Status]** 圖表會依所選時間範圍內的計數顯示錯誤回應，並以錯誤狀態代碼分面。

## [!UICONTROL Duration by Response Status, top 25 urls]

![依回應狀態區分的持續時間，前25個URL](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

此 **[!UICONTROL Duration by Response Status, top 25 URLs]** 圖形會依回應持續時間顯示前25個URL （以秒為單位）。 您可能需要將滑鼠移至URL上方，才能檢視整個路徑。 此外，若要移除除一個URL外的所有其他URL，請按一下該URL。 接著，您可以按一下其他URL來重新新增它們。 如果您想要移除個別URL，可以按住索引鍵，然後按一下每個URL，即可從圖形中移除這些URL。

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![依回應狀態區分的持續時間，前25個非200個狀態](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

此 **[!UICONTROL Duration by Response Status, top 25 non-200 status]** 圖表與上一個類似，不同之處在於焦點在非200狀態代碼或錯誤狀態代碼。 它會顯示錯誤代碼，然後顯示URL。 您可能需要將滑鼠移至URL上方，才能檢視整個路徑。 此外，若要移除除一個URL外的所有其他URL，請按一下該URL。 接著，您可以按一下其他URL來重新新增它們。 如果您想要移除個別URL，可以按住索引鍵，然後按一下每個URL，即可從圖形中移除這些URL。

## [!UICONTROL Error Count by POP timeline]

![依POP時間軸錯誤計數](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

此 **[!UICONTROL Error Count by POP timeline]** 圖表會依所選時間範圍時間軸顯示錯誤狀態的計數，並以錯誤代碼分面。

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![依回應狀態的持續時間、前25個使用者端IP、非200個狀態](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

此 **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** 圖形會依據所選時間範圍內出現狀態錯誤碼的平均持續時間來顯示IP位址。

## [!UICONTROL IP Frequency]

![IP頻率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

此 **[!UICONTROL IP Frequency]** frame會計算（&#39;MISS&#39;和&#39;PASS&#39;）中每個IP的狀態 [!DNL Fastly] 記錄。 具有這些狀態的網頁請求將連線至原始伺服器，並將新增負載至伺服器。 這會顯示頻率排名前20個位址。 此框架可用來偵測網站上的IP攻擊或負載過重的來源。 此圖表也會顯示在摘要標籤上，並放置於此處，以方便與的更多詳細資料進行比較。 [!DNL Fastly] 記錄在此標籤上顯示的資訊。
