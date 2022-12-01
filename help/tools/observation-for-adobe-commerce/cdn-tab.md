---
title: 「 [!UICONTROL CDN] 標籤」
description: 了解 [!UICONTROL CDN] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: 424c832ba7580e5d766dea33e3b776eaca7a0d77
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# 此 [!UICONTROL CDN] 標籤

此標籤的資訊主要針對 [!DNL content delivery network (CDN)]. 就Adobe Commerce Cloud而言， [!DNL Fastly] 服務。

## [!UICONTROL HIT rate]

![點擊率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

此 **[!UICONTROL HIT rate]** frame會顯示導致 [!UICONTROL HITS] 最後一刻。 這表示快取成功。 右側的箭頭會顯示一週前的同一時間以上或以下的百分比。

## [!UICONTROL HIT Processing]

![點擊處理](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

此 **[!UICONTROL HIT processing]** 方塊顯示導致 [!UICONTROL HITS] 一週。

## [!UICONTROL MISS rate]

![失敗率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

此 **[!UICONTROL MISS rate]** 框顯示最後一分鐘可快取請求的未命中數。 遺漏是指未快取要求時，且必須將要求傳遞至來源伺服器才能提供內容。 右側的值是增加/減少與前一週每分鐘的分鐘數的比較。

## [!UICONTROL MISS time]

![錯過時間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![點擊率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![錯誤百分比](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

此 **[!UICONTROL Error Percentage]** 方塊會顯示請求的「錯誤百分比」值，並顯示與前一週的相同時間相比的相對增加/減少。

## [!UICONTROL Total Requests]

![總請求數](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![錯誤率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![所選時段的快取平均響應（以秒為單位）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

此框架顯示可快取請求的持續時間（以秒為單位），這表示如果 `cache_response` 是 [!UICONTROL MISS]，則會顯示所選時間遺漏快取回應的平均值。

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![POP分面的選定時段的快取平均響應（秒）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![所選時間範圍內的總頻寬（所有POP），而1週前為1（增加/減少%）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![請求 — 自選取的時間範圍與一週前相比](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

此框架類似於 [!UICONTROL Total Requests] 在頂端，但會顯示前幾週的請求計數。 這些都是請求，而不只是可快取的請求(其中 `is_cacheable` 為true)。

## [!UICONTROL Response Count]

![回應計數](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![按POP的頻寬](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![前5個URL（5xx或3xx狀態代碼）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

此 **[!UICONTROL Top 5 URLs]** 檢視會顯示5xx或3xx錯誤回應的前5個URL。 由於空間限制，您必須將滑鼠移至URL上方，才能查看與該URL相關聯的特定錯誤碼。 （如上圖的紅色方塊中）。

## [!UICONTROL Top 25 URLs (200 status)]

![前25個URL（200個狀態）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

此 **[!UICONTROL Top 25 URLs]** frame會顯示在選取的時間範圍內，以計數傳回200個狀態的URL。

## [!UICONTROL Duration by Response Status]

![按響應狀態列出的持續時間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

此 **[!UICONTROL Duration by Response Status]** 圖形會依選取的時間範圍內（以錯誤狀態代碼分面）的計數顯示錯誤回應。

## [!UICONTROL Duration by Response Status, top 25 urls]

![持續時間（依回應狀態），前25個URL](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

此 **[!UICONTROL Duration by Response Status, top 25 URLs]** 圖表以秒為單位，顯示前25個URL。 您可能需要將滑鼠移至URL上，才能查看整個路徑。 此外，若要移除除一個URL以外的所有URL，請按一下該URL。 然後，您可以個別按一下其他URL，再將其新增回。 如果您想要移除個別URL，可以按住鍵並按一下每個URL，以從圖表中移除它們。

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![持續時間（依回應狀態），前25個非200個狀態](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

此 **[!UICONTROL Duration by Response Status, top 25 non-200 status]** 圖表與最後一個類似，只是焦點在非200個狀態代碼或錯誤狀態代碼上。 它會顯示錯誤碼，然後顯示URL。 您可能需要將滑鼠移至URL上，才能查看整個路徑。 此外，若要移除除一個URL以外的所有URL，請按一下該URL。 然後，您可以個別按一下其他URL，再將其新增回。 如果您想要移除個別URL，可以按住鍵並按一下每個URL，以從圖表中移除它們。

## [!UICONTROL Error Count by POP timeline]

![按POP時間軸計算錯誤數](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

此 **[!UICONTROL Error Count by POP timeline]** 圖形會依據錯誤代碼顯示所選時間軸的錯誤狀態計數。

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![持續時間（依回應狀態）、前25個用戶端IP、非200狀態](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

此 **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** 圖表會依所選時間範圍內具有狀態錯誤代碼的平均持續時間顯示IP位址。

## [!UICONTROL IP Frequency]

![IP頻率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

此 **[!UICONTROL IP Frequency]** frame會從 [!DNL Fastly] 記錄檔。 具有這些狀態的Web請求將會到達來源伺服器，並將載入伺服器。 它以頻率顯示前20個地址。 此框架可用於檢測網站上的IP攻擊或重載源。 此圖表也會顯示在摘要標籤上，並放置在此處，以便與 [!DNL Fastly] 此頁簽上顯示的日誌資訊。
