---
title: 的 [!UICONTROL bots] 頁籤
description: 瞭解 [!UICONTROL bots] 頁籤 [!DNL Observation for Adobe Commerce]。
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
source-git-commit: 6c0607713231393ec0d7e190398518f7cd9559a4
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 0%

---

# 的 [!UICONTROL bots] 頁籤

此頁籤包含說明如何識別是否和何種資訊的資訊 [!DNL bots] 導致站點問題。

## 高級概述 [!DNL bots]:

* A [!DNL bot] 是運行重複性自動任務的軟體。 隨著人工智慧和機器學習的進化，任務、方法和交互 [!DNL bots] 正在更改。 有 *好* [!DNL bots] 通過搜索網站並將其添加到網際網路搜索引擎，這些網站將受益匪淺。 這導致網際網路用戶通過搜索引擎結果被引導到站點。 A *好* [!DNL bot] 通常涉及放置在 [!DNL bot] 按 `robots.txt` 檔案或設定。 邊界可以限制對站點或站點部分的訪問。
* 惡意 [!DNL bots] 忽略 `robots.txt` 否則他們可能會欺騙 [!DNL bot] 通過請求用戶代理欄位獲取HTTP請求資料。 有些東西 [!DNL bots] 執行：
   * 向站點添加負載以拒絕合法用戶訪問該站點。
   * 未經許可即可擦除和重用內容。
   * 註冊虛假帳戶以向電子郵件服務或地址發送大量郵件或重定向到其他站點([!DNL SPAM bots])。
   * 建立假視圖([!DNL Viewbots])。
   * 購買產品或票證([!DNL Focused bots])。
* 管理 [!DNL bots]
   * [!DNL Observation for Adobe Commerce] 有 [!DNL bot] 流量：
      * 它顯示未快取的總數 [!DNL bot] 活動，顯示 [!DNL bot] 即添加到站點，當負載發生時。
      * 它顯示 [!DNL bots] 正在生成錯誤。 通常，如果 [!DNL bot] 是添加導致站點問題的負載， [!DNL bot] 或IP地址有最高錯誤頻率。
      * 它顯示 [!DNL bot] 名稱（請求用戶代理欄位值）和要通過以下方式管理的IP地址：
         * [!DNL Fastly] (限速或 [!DNL VCLs] 阻止IP地址、範圍或 [!DNL bots] 按名稱值)。
         * 添加好 [!DNL bot] 資訊 `robots.txt field` 限制或限制站點訪問率。
         * 管理 [!DNL Bing] 或 [!DNL Google bots] 搜索引擎控制台。

## [!UICONTROL Experimental Potential Malicious Bots frame]

![潛在惡意Bot框架的實驗](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

的 **[!UICONTROL Experimental Potential Malicious Bots frame]** 幀運行於12個獨立的複雜查詢中。 它檢測惡意IP請求籤名，然後按降序對結果進行聚合、求和並按計數排序。 這些查詢包含CVE漏洞和其他惡意請求的大量資料簽名。 即使安全修復程式/補丁程式阻止了利用漏洞的攻擊並且對站點沒有威脅，仍然必須由網站處理該請求。 在很短的時間內，請求量會變得相當大。 此幀不顯示來自IP地址的請求總數，而是顯示具有指示該請求具有可疑意圖的信號的請求。

確保驗證通信是否可疑且不源自 [!DNL Content Distributed Network] (CDN)地址，該地址也可以傳遞有效請求。 如果確定請求來自CDN IP地址，請聯繫該服務供應商以幫助阻止通過其網路的可疑通信。 如果需要阻止地址或請求URL，請參閱 [阻止Adobe Commerce的惡意通信 [!DNL Fastly] 級別](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) 在Adobe Commerce支援知識庫中。

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![在請求的時間段內每秒HTTP請求（前25個）的速率](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

的 **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** frame顯示選定時間幀內每秒的IP地址請求數最多。 如果上表中也包含這些地址，請確保它們不是CDN地址並且是惡意的，並通過 [!DNL Fastly]。

## [!UICONTROL Total Bot traffic by bot name]:

![在選定的時間段內，按Bot名稱列出的Bot通信總量：](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

的 **[!UICONTROL Total Bot traffic by bot name during selected time period]** 表包含非快取請求的聚合計數，其中 [!UICONTROL request_user_agent] 欄位包含 [!DNL bots] 的雙曲餘切值。 這可能是或不是命名 [!DNL bot] 的 [!UICONTROL request_user_agent] 欄位值可以偽造。 位於 [!UICONTROL Count] 欄是最重要的。

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![按Bot名稱/IP地址在選定時間段內的Bot總流量如何阻止Rebistlevel上的Bot流量或通過您的robots.txt檔案管理botsAdobe Commercerobots.txt的最佳做法](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

的 **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 該表顯示與上一表相同的資料，但添加了代表命名的 [!DNL bot]。 惡意 [!DNL bots] 好壞 [!DNL bots], IP地址應通過識別濫用IP地址的網站或通過 *誰* 服務或 [!DNL DNS lookups]。 比如說， [!DNL Google] 出版 [[!DNL googlebot] IP地址](https://developers.google.com/search/apis/ipranges/googlebot.json) 和 [!DNL Microsoft] 具有用於 [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f)。

## [!UICONTROL Graph - Bots with HTTP status errors]

![圖形 — 在選定時間段內HTTP狀態錯誤的Bot如何阻止Repbiesl級別的Bot通信或通過您的robots.txt檔案管理botsAdobe Commercerobots.txt的最佳做法](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

的 **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 圖形顯示錯誤 [!DNL bots] 在request user agent欄位中聲明自己。 這不一定表示錯誤是由 [!DNL bot] 或其他交通。 錯誤可能是 [!DNL bot] 正在請求不存在的資訊或請求中存在其他問題。

如果在站點不穩定或停機期間IP地址上出現大量錯誤，則這些錯誤可能是站點問題的嫌疑人。

## [!UICONTROL Table - IPs that do not identify as bots]

![表 — 在選定時間段內不標識為具有HTTP狀態錯誤的bot的IP如何阻止Repsible級別上的bot通信或通過您的robots.txt檔案管理botsAdobe Commercerobots.txt的最佳做法 ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

的 **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 表將顯示具有非200個HTTP狀態代碼且DO SELF-identify為的IP請求 [!DNL bots] 中。 這些IP地址可能是惡意IP地址，特別是在所選時間段計數較高時。

如果非200 http狀態代碼計數低且IP地址範圍不相似，則地址可能不會導致站點問題。

## [!UICONTROL Table – Cache Status 'ERROR']

![表 — 快取狀態「ERROR」詳細資訊表（這些IP在做什麼？） 如何阻止Reblish級別上的bot通信或通過robots.txt檔案管理botAdobe Commercerobots.txt的最佳做法](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

當IP地址產生高頻錯誤時，請問它們在做什麼？ 的 **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 表將顯示請求的URL以及具有快取狀態的請求的HTTP狀態值 [!UICONTROL ERROR] 值。 該頻率按URL分面，因此計數可能較低。 請記住， IP地址在選定的時間段內可能發出數千個請求。 這是一個視圖，針對在時間範圍內最多2000個請求（記錄顯示限制）。

## [!UICONTROL Show 5XX status distribution]

![顯示跨IP地址（前200個地址）的5XX狀態分佈如何阻止Repbisy級別的bot通信或通過您的robots.txt檔案管理botsAdobe Commercerobots.txt的最佳做法 ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

的 **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 框架功能強大。 它顯示在選定時間段內具有5XX http狀態代碼的IP地址。 如果IP地址發出的請求數量較大，並且站點受到影響到無法處理通信量的位置，則發出請求頻率最高的IP地址通常會出現最大數量的錯誤。 5XX http狀態代碼通常表示一個難以響應請求的站點。

欄越寬，IP地址在該時間段內的5xx錯誤總數中的錯誤百分比就越大。 注：如果IP地址具有多個http狀態代碼（例如502和503 http狀態），則該圖形中可能包含多個段。

典型分佈將指向條的右側，其中IP地址的寬度相等，或者有幾個計數很低的寬條。

如果懸停在條形段上，它將顯示選定時間段內指示的錯誤數。

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![IP快取狀態(MISS、PASS、ERROR)和HTTP狀態在選定的時間段內如何阻止Reblish級別的bot通信或通過您的robots.txt檔案管理botsAdobe Commercerobots.txt的最佳做法](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

此 **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame顯示HTTPS狀態代碼計數和IP在所選時間幀內的非快取請求。 這表示每個IP地址和總卷的成比例負載。 它將顯示請求最多的IP地址。

## [!UICONTROL Fastly Cache Summary for selected time period]

![所選時間段的「快速快取摘要」](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

如果按一下 [!UICONTROL Error] 表徵圖中，您可以將最後兩個圖形進行比較。 這有助於指明負載是站點問題的原因。

![快速錯誤檢查](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![在選定時間段內不識別為bot而無錯誤的IP如何阻止Repbisy級別的bot通信或通過您的robots.txt檔案管理botsAdobe Commercerobots.txt的最佳做法](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

的 **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame顯示請求用戶代理欄位、請求用戶代理欄位未指示請求的IP地址和狀態代碼 [!DNL bot]。 此幀可能顯示來自任何IP地址的高頻請求，但應注意高頻請求，特別是在站點可能有問題的時間段內。

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![在所選時段內可疑的非Bot通信](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

的 **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** graph查找Go-http-client的請求用戶代理值，但將擴展為查看其他可疑請求用戶代理值。 此請求用戶代理值由站點用於從服務連接，可能有效，但也由惡意用戶使用 [!DNL bots]。

## [!UICONTROL Graph - Bot traffic by Bot name]

![圖形 — 按選定時間段內的Bot名稱顯示的Bot通信)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

的 **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** 幀顯示的資料與Bot總通信量相同 [!DNL Bot] 名稱。 它通過時間軸顯示資料，以便您能夠查看 [!DNL bots] 正在進行分發。

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![在選定時間段內前250個Bot名稱和IP地址如何阻止Rebistlevel上的Bot通信或通過您的robots.txt檔案管理botsAdobe Commercerobots.txt的最佳做法](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

的 **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 幀顯示的資料與「總」 [!DNL Bot] 按Bot名稱/IP地址在選定時間段表（位於頁籤頂部）中的通信量。 它通過時間表顯示資料，並通過IP地址對其進行對應。 這顯示了 [!DNL bots] 發出請求的IP和請求的分發。

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![在選定的時間段內阻止Bot名稱/IP地址（在Reptible中）。 此圖形顯示返回403禁止HTTP狀態代碼的bot通信和IP](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

的 **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** frame顯示bot名稱和被阻止的IP地址。 您可以在此圖表中查看所有請求的阻止方式 [!DNL Fastly] 繼續前進。

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![在選定的時間段內阻止非Bot名稱/IP地址（在「Abmestible」中）。 此圖形顯示返回403禁止HTTP狀態代碼的非bot通信和IP ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

的 **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** 幀顯示不標識為 [!DNL bot] 被堵住了 [!DNL Fastly]。

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![此表顯示每個IP地址的用戶代理數、成功、失敗和被阻止的請求數：](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

惡意 [!DNL bots] 經常嘲笑別人 [!DNL bots] 通過 [!UICONTROL Request User Agent] 的子菜單。 此表顯示IP地址在該欄位中具有的唯一值數。 值越高 [!UICONTROL Request User Agent] 欄位中， IP地址越可疑。

## [!UICONTROL IP with non-200 status errors]

![IP的狀態為非200錯誤 — 沒有403狀態](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

的 **[!UICONTROL IP with non-200 status errors – without 403 status]** frame顯示選定時間範圍內IP地址的分佈，HTTP狀態代碼不是200。 如果您在單個IP或IP地址組上看到更高的值，則需要進一步調查。

## [!UICONTROL IP with 403 status codes:]

![具有403個狀態代碼的IP:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

的 **[!UICONTROL IP with 403 status codes]** 幀顯示未快取的請求，但 [!UICONTROL cache_status=ERROR] HTTP狀態為403。 這可能表明源伺服器是403（未授權）的源，而不是來自 [!DNL Fastly]。

## [!UICONTROL Top 5 with non-200 status codes]

![前5個狀態代碼顯示cache_status，非200個狀態代碼：](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

的 **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** 表在IP/狀態級別上顯示 [!UICONTROL cache_status] 值。

## [!UICONTROL Pageview Latency will show as spikes]

![Pageview Latency將顯示為此圖形上的尖峰：](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

的 **[!UICONTROL Pageview Latency will show as spikes on this graph:]** 幀顯示頁載入/API響應延遲，該延遲可能與 [!DNL bot] 流量。
