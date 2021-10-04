---
title: AEM效能最佳化
description: 最佳化您的預設Adobe Experience Manager設定，以支援Adobe商務的高負載。
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# AEM效能最佳化

AEM Dispatcher是反向的Proxy，可協助傳送快速且動態的環境。 它可作為靜態HTML伺服器（例如Apache HTTP Server）的一部分，以靜態資源的形式，盡可能儲存（或「快取」）網站內容。 此方法旨在將盡可能存取AEM頁面呈現功能和Adobe商務GraphQL服務的需求降至最低。 將大部分頁面以靜態HTML、CSS和JS形式提供，可為使用者提供效能優勢，並降低環境的基礎架構需求。 快取時，應考量使用者之間可能重複相同的任何頁面或查詢。

以下小節從高層顯示要審查的建議技術重點區域，以便在CIF/Adobe商務環境中有效快取AEM。

## 基於AEM Dispatcher的快取

在Dispatcher上盡可能快取網站是任何AEM專案的最佳作法。 若使用基於時間的快取失效，則伺服器端會呈現CIF頁面，且會維持一定的有限時間。 設定時間過期後，下一個請求將從AEM發佈者和Adobe商務GraphQL重建頁面，並將其再次儲存在Dispatcher快取中，直到下次失效為止。

您可以使用ACS AEM Commons套件中的「Dispatcher TTL」元件，並在dispatcher.any設定檔案中設定/enableTTL &quot;1&quot;，在AEM中設定TTL快取功能。

如果已啟用，Dispatcher將評估後端的回應標題，如果回應標題包含「快取控制」的最大使用期或「過期」日期，則會建立快取檔案旁的輔助空白檔案，且修改時間等於到期日。 在修改時間之後請求快取檔案時，會自動從後端重新請求該檔案。 這提供有效的快取機制，一旦產品更新延遲(TTL)獲得業務利害關係人確認並接受，就不需要手動干預或維護。

## 瀏覽器快取

上述的Dispatcher TTL方法可大幅減少請求和發佈工具的負載，不過有些資產很可能不會變更，因此，將相關檔案快取在使用者的瀏覽器上，即可減少對Dispatcher的請求。 例如，網站的標誌會顯示在網站範本中網站的每個頁面上，不需要每次向Dispatcher請求。 這可儲存在使用者的瀏覽器快取中。 每個頁面載入的頻寬需求減少，會對網站回應速度和頁面載入時間造成很大影響。

瀏覽器層級的快取通常會透過「快取控制：max-age=」回應標題。 最大值設定會告訴瀏覽器，在嘗試「重新驗證」或再次從網站要求檔案之前，應先快取檔案的秒數。 此快取最大存留期概念通常稱為「快取過期」或TTL（「存留時間」）。 大規模提供商務體驗 — 透過Adobe Experience Manager、商務整合架構、Adobe商務7

AEM/CIF/Adobe商務網站的某些區域可在用戶端的瀏覽器中設定為快取：

- 影像(在AEM範本本身內，例如網站標誌和範本設計影像 — 透過Appeitly從Adobe商務呼叫目錄產品影像，稍後會討論快取這些影像)
- HTML檔案（針對不常變更的頁面 — 條款與條件頁面等）
- CSS檔案
- 所有網站JavaScript檔案 — 包括CIF JavaScript檔案

## Dispatcher statfilelevel和寬限期最佳化

預設Dispatcher設定使用/statfilelevel &quot;0&quot;設定，這表示單一&quot;。stat&quot;檔案會置於htdocs目錄（檔案根目錄）的根目錄中。 如果AEM中的頁面或檔案發生變更，則此單一stat檔案的修改時間會更新為變更時間。 如果時間比資源的修改時間還新，則Dispatcher會將所有資源視為已失效，且任何後續對已失效資源的請求都將觸發對Publish例項的呼叫。 因此，基本上，透過此設定，每次啟動都會使整個快取失效。

對於任何網站，尤其是載入量很大的商務網站，這會對整個網站結構造成不必要的AEM Publish層級負載，而只需更新一頁即會失效。

相反，可以將statfilelevel設定修改為更高的值，與文檔根目錄中htdocs目錄的子目錄深度相對應，這樣當某個級別的檔案失效時，只更新該.stat目錄級別及以下的檔案。

例如：假設您有以下位置的產品頁面範本：

```
content/ecommerce/us/en/products/product-page.html
```

每個資料夾層級都會有「stat level」，如上表所劃分所示。

| 內容(docroot) | 電子商務 | us | en | 產品 | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

在此案例中，如果您將statfilelevel屬性設為預設「0」，而product-page.html範本已更新並啟動，而觸發失效，則從docroot到4層的每個.stat檔案都將接觸，且檔案失效，進而導致AEM發佈例項針對網站上所有頁面（包括其他網站、國家和語言）提出進一步的要求，要求進行該次變更。

不過，如果statfilelevel屬性設定為level 4，並且對product-page.html進行了更改，則只會接觸該特定網站/國家/語言的產品目錄中的.stat檔案。

請注意，.stat檔案級別不應設定為過高級別 — 超過20級可能會影響效能。 在運行效能測試時執行批量檔案激活應為您提供將狀態級別調整為的正確級別。

設定statfilelevel時最佳化的另一個Dispatcher設定為gracePeriod設定。 這會定義上次啟動後，過時、自動失效的資源仍可從快取中提供服務的秒數。 自動失效的資源會因任何啟動而失效（當其路徑符合Dispatcher /invalidate區段，且達到statfilelevel屬性中指定的層級時）。 將gracePeriod設定設為2秒可用來防止多個請求持續傳送至發佈者的案例，即使發佈者仍在建立新頁面的程式中亦然。

>[!NOTE]
>
> [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub存放庫提供有關本主題的更詳細閱讀內容。

## CIF — 透過元件執行GraphQL快取

AEM中的個別元件可設為快取，這表示要Adobe的GraphQL請求
商務會呼叫一次，然後從AEM快取中擷取後續請求（最多到設定的時限），且不會將進一步載入至Adobe商務。 例如，網站導覽會以顯示於每個頁面上的類別樹為基礎，以及多面搜尋功能中的選項。這兩個區域只需要對Adobe商務進行耗用大量資源的查詢，才能建置，但不太可能定期變更，因此是快取的好選擇。 例如，即使發佈者正在重建PDP或PLP，導覽組建的資源密集型GraphQL請求也不會點擊Adobe商務，且可從AEM CIF上的GraphQL快取中擷取。

以下範例是要快取導覽元件，因為它會在網站的所有頁面上傳送相同的GraphQL查詢。 以下請求會為導覽結構快取過去100個項目10分鐘：

```
venia/components/structure/navigation:true:100:600
```

以下範例會在1小時內將過去100個多面的搜尋選項快取在搜尋頁面中：

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

請求（包括所有自訂的http標題和變數）必須完全相符，快取才會「點擊」，並防止重複呼叫Adobe商務。 請注意，一旦設定，就無法輕鬆手動使此快取失效。 這可能表示，如果Adobe商務中新增了新類別，除非上述快取中設定的到期時間已過，且GraphQL請求已重新整理，否則新類別不會開始出現在導覽中。 搜尋Facet也是一樣。 但是，鑑於此快取可帶來的效能優勢，這通常是可接受的折衷方案。

可使用「GraphQL用戶端」中的AEM OSGi設定主控台設定上述快取選項
配置工廠」。 每個快取配置項都可以使用以下格式指定：

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## 混合快取 — 快取Dispatcher頁面中的用戶端GraphQL請求

您也可以使用混合快取頁面的方式：CIF頁面可包含元件，元件一律會直接從Adobe的瀏覽器要求Commerce提供最新資訊。 對於範本中頁面的特定區域來說，這項功能相當實用，這些區域必須以即時資訊保持最新：例如，PDP內的產品價格。 當價格因動態價格比對而經常變更時，這些資訊可設定為不在Dispatcher上快取，而可以直接從Adobe商務透過具有AEM CIF網頁元件的GraphQL API，從客戶瀏覽器的用戶端擷取價格。

這可透過AEM元件設定來設定 — 如需產品清單頁面上的價格資訊，可在產品清單範本中設定，並在頁面設定上選取產品清單元件並核取「載入價格」選項。 同樣的方法也適用於庫存水準。

只有在需要即時、持續更新的資訊時，才應使用上述方法。 在上述定價範例中，可與業務利害關係人商定，只在低流量時每天更新價格，然後執行快取排清操作。 這樣，在建置顯示定價資訊的每個頁面時，就不需要即時定價資訊要求，也不需要Adobe商務的後續額外負載。

## 無法處理的GraphQL請求

不應快取頁面內的特定動態資料元件，且一律需要GraphQL呼叫來Adobe商務，例如購物車和在整個結帳頁面進行的呼叫。 此資訊是使用者專屬的，且會因客戶在網站上的活動（例如透過將產品新增至其購物車）而持續變更。

如果網站的設計會根據使用者的角色提供不同的回應，則不應為登入客戶快取GraphQL查詢結果。 例如，您可以建立多個客戶群組，並為每個群組設定不同的產品價格或不同的產品類別可見度。 這類快取結果可能會導致客戶查看其他客戶群組的價格，或顯示錯誤的類別。

## 忽略AEM Dispatcher快取上的追蹤參數

電子商務網站可能會使用PPC搜尋廣告或社交媒體行銷活動來促進網站的流量。

使用這些媒體表示會將追蹤ID新增至該平台的對外連結。 例如，Facebook會在URL中新增Facebook點按ID(fbclid),Google Addies會新增Google點按ID(gclid)，如此一來，連線至AEM前端的連結就會如下所示：

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

gclid和fbclid會隨著每位點按廣告的使用者而變更，這是為了追蹤目的，但透過其預設設定，AEM會將每個請求視為唯一頁面，而會略過Dispatcher，並在發佈商和Adobe商務上產生不必要的額外負載。

在電湧事件期間，這甚至可能導致AEM發佈者超載且無反應。 將某個頁面的參數設為忽略時，系統會在第一次要求頁面時快取該頁面。 快取頁面會提供頁面的後續要求，不論要求中的參數值為何。

>[!NOTE]
>
>[aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub存放庫中提供有關設定`ignoreUrlParams`之重要性的進一步資訊。

因此，應將其設定為依預設忽略「ignoreUrlParams」中的所有參數，除非使用GET參數會變更頁面的HTML結構。 例如，在搜尋頁面中，搜尋詞作為GET參數位於URL中 — 在此情況下，您應手動設定ignoreUrlParams，以忽略廣告頻道所使用的gclid、fbclid等參數，以及任何其他追蹤參數，而使一般網站作業所需的GET參數不受影響。

## MPM工作程式限制調度程式

MPM背景工作設定是進階的Apache HTTP伺服器設定，需要進行徹底測試，才能根據Dispatcher的可用CPU和RAM來最佳化。 但是，在本白皮書的範圍內，我們建議將ServerLimit和MaxRequestWorkers增加到伺服器的可用CPU和RAM支援的級別，然後將MinSpareThreads和MaxSpareThreads都增加到與MaxRequestWorkers匹配的級別。

此配置將使Apache HTTP保持「完全就緒」狀態，該狀態是對具有大量RAM和多個CPU核心的伺服器進行的高效能配置。 此設定可借由維持可供處理要求的永久性開放連線，從Apache HTTP產生最佳回應時間，並移除因應突然流量飆升（例如快閃記憶體銷售期間）而產生新程式的任何延遲。
