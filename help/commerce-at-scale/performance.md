---
title: AEM效能最佳化
description: 最佳化您的預設Adobe Experience Manager設定，以支援Adobe Commerce上的高負載。
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# AEM效能最佳化

AEM Dispatcher是反向Proxy，有助於提供快速且動態的環境。 它可作為靜態HTML伺服器（例如Apache HTTP Server）的一部分運作，其目的是以靜態資源的形式儲存（或「快取」）儘可能多的網站內容。 此方法旨在儘可能減少存取AEM頁面轉譯功能和Adobe Commerce GraphQL服務的需求。 將許多頁面作為靜態HTML、CSS和JS提供的結果，為使用者提供效能優勢，並降低環境的基礎架構需求。 使用者之間重複出現的頁面或查詢應視為快取。

以下小節以高層級方式顯示建議的技術重點區域，以供檢閱，以便在CIF/Adobe Commerce環境中啟用AEM上的有效快取。

## AEM Dispatcher上的TTL型快取

在排程程式上儘可能多地快取網站是任何AEM專案的最佳實務。 使用以時間為基礎的快取失效將會在設定的有限時間內快取伺服器端轉譯的CIF頁面。 設定時間過期後，下一個請求將從AEM發佈者和Adobe Commerce GraphQL重建頁面，並將其再次儲存在Dispatcher快取中，直到下一次失效。

TTL快取功能可在AEM中使用ACS AEM Commons套件中的「Dispatcher TTL」元件進行設定，並在dispatcher.any設定檔案中設定/enableTTL &quot;1&quot; 。

如果啟用，Dispatcher將會評估來自後端的回應標頭，如果其中包含Cache-Control max-age或Expires date，則會在快取檔案旁邊建立空的輔助檔案，且修改時間等於到期日。 在修改時間過後請求快取檔案時，將會自動從後端重新請求該檔案。 一旦產品更新延遲(TTL)得到業務利害關係人的認可和接受，這可提供無需手動干預或維護的有效快取機制。

## 瀏覽器快取

上述Dispatcher TTL方法會大幅減少要求並載入發佈者的量，不過有些資產極不可能變更，因此甚至可以透過在使用者的瀏覽器上本機快取相關檔案來減少對Dispatcher的請求。 例如，網站的標誌（顯示在網站範本的每個頁面上）不需要每次都向Dispatcher要求。 這可以儲存在使用者的瀏覽器快取中。 降低每個頁面載入的頻寬需求，會對網站回應速度與頁面載入時間造成重大影響。

通常，瀏覽器層級的快取是透過「Cache-Control： max-age=」回應標頭來完成。 maxage設定會告訴瀏覽器，在嘗試「重新驗證」或再次從網站要求之前，應該快取檔案的秒數。 這個快取max-age的概念，通常稱為「快取有效期」或TTL （「存留時間」）。 大規模提供商務體驗 — 使用Adobe Experience Manager、Commerce Integration Framework、Adobe Commerce 7

AEM/CIF/Adobe Commerce網站中可以設定為使用者端瀏覽器快取的某些區域包括：

- 影像(在AEM範本本身，例如網站標誌和範本設計影像 — 目錄產品影像將透過Fastly從Adobe Commerce呼叫，稍後將討論快取這些影像)
- HTML檔案（不常變更的頁面 — 條款與條件頁面等）
- CSS檔案
- 所有網站JavaScript檔案 — 包括CIF JavaScript檔案

## Dispatcher靜態檔案層級和寬限期最佳化

預設Dispatcher設定使用/statfilelevel &quot;0&quot;設定 — 這表示單一「.stat」檔案放置在htdocs目錄的根目錄（檔案根目錄）中。 如果對AEM中的頁面或檔案進行變更，則此single stat檔案的修改時間會更新為變更時間。 如果時間比資源的修改時間新，則Dispatcher會考慮所有資源都失效，並且任何對失效資源的後續請求都將觸發對發佈執行個體的呼叫。 所以基本上，使用此設定時，每次啟用都會讓整個快取失效。

對於任何網站，尤其是具有大量負載的商務網站，這會在AEM Publish層級上增加不必要的負載，使得整個網站結構在只有單一頁面更新時失效。

反之，statfilelevel設定可以修改成更高的值，對應於來自檔案根目錄的htdocs目錄的子目錄深度，這樣當位於特定層級的檔案失效時，只更新該.stat目錄層級或更低層級的檔案。

例如：假設您有一個產品頁面範本：

```
content/ecommerce/us/en/products/product-page.html
```

每個資料夾層級都有「stat層級」 — 如上表所劃分。

| 內容(docroot) | 電子商務 | us | en | 產品 | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

在此案例中，如果您將statfilelevel屬性設為預設值「0」，且product-page.html範本已更新並啟動並觸發失效，則會觸及從docroot到第4級的所有.stat檔案，並讓檔案失效，導致從AEM發佈執行個體針對網站上的所有頁面（包括其他網站、國家/地區和語言）從該單一變更進一步發出請求。

但是，如果statfilelevel屬性設定為level 4，而且已變更product-page.html — 則只會接觸該特定網站/國家/語言的products目錄中的.stat檔案。

請注意，.stat檔案層級不應設定得太高 — 超過20可能會影響效能。 在執行效能測試時執行大量檔案啟動，應可提供您應將統計層級調整到的正確層級。

在設定statfilelevel時要最佳化的另一個dispatcher設定是gracePeriod設定。 這定義在最後一次啟用後，仍然可以從快取中提供過時的、已自動失效的資源的秒數。 任何啟用都會讓自動失效的資源失效（當其路徑符合dispatcher /invalidate區段，以及符合statfileslevel屬性中指定的層級時）。 將gracePeriod設定設為2秒可防止發生多次要求持續傳送給發佈者的情況，即使發佈者仍在建立新頁面時亦然。

>[!NOTE]
>
> 有關此主題的更多詳細閱讀資訊，請參閱 [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub存放庫。

## CIF — 透過元件的GraphQL快取

AEM中的個別元件可設定為快取，這表示對Adobe Commerce的GraphQL請求會呼叫一次，然後後續請求（最多為設定的時間限制）會從AEM快取中擷取，不會將進一步載入至Adobe Commerce上。 例如，根據每個頁面上顯示的類別樹狀結構網站導覽，以及多面向搜尋功能中的選項，這些只是需要在Adobe Commerce上建立大量資源查詢的兩個區域，但不太可能定期變更，因此是快取很好的選擇。 舉例來說，如此一來，即使發佈商正在重建PDP或PLP，導覽組建的資源密集GraphQL請求也不會命中Adobe Commerce，而可從AEM CIF上的GraphQL快取中擷取。

以下範例是快取導覽元件，因為它會在網站的所有頁面上傳送相同的GraphQL查詢。 以下請求會針對導覽結構快取過去100個專案10分鐘：

```
venia/components/structure/navigation:true:100:600
```

以下範例會在搜尋頁面中快取過去100個多面向搜尋選項1小時：

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

請求（包括所有自訂http標頭和變數）必須完全相符，才能讓快取「點選」，並防止對Adobe Commerce的重複呼叫。 請注意，設定完成後，就很難手動讓此快取失效。 這可能表示，因此，如果在Adobe Commerce中新增新類別，則在上方快取中設定的到期時間過期且GraphQL請求重新整理之前，不會開始出現在導覽中。 搜尋Facet也一樣。 不過，鑑於此快取可帶來的效能優勢，這通常是可接受的折衷方案。

上述快取選項可在「GraphQL Client Configuration Factory」中使用AEM OSGi Configuration Console設定。 每個快取設定專案都可以以下列格式指定：

```
* NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## 混合式快取 — 快取Dispatcher頁面中的使用者端GraphQL請求

也可以使用混合方法快取頁面：CIF頁面可以包含永遠會直接從客戶的瀏覽器向Adobe Commerce要求最新資訊的元件。 這對於範本中頁面的特定區域非常有用，這些區域對於即時資訊保持最新非常重要：例如PDP中的產品價格。 如果價格因動態價格比對而經常變更，則該資訊可以設定為在Dispatcher上不進行快取，而是在客戶瀏覽器中，透過AEM CIF網頁元件的GraphQL API，直接從Adobe Commerce擷取使用者端價格。

這可以透過AEM元件設定進行設定 — 針對產品清單頁面上的價格資訊，這可以在產品清單範本中設定，在頁面設定上選取產品清單元件並勾選「載入價格」選項。 同樣的方法也適用於庫存水準。

只有在需要即時、持續最新的資訊時，才應該使用上述方法。 在上面的定價範例中，業務利害關係人可能會同意，僅在低流量時間每日更新價格，然後執行快取排清作業。 如此一來，在建置每個顯示定價資訊的頁面時，就不需要即時要求價格資訊，也無需隨後額外載入Adobe Commerce。

## 無法快取的GraphQL請求

不應快取頁面內的特定動態資料元件，且一律需要GraphQL呼叫Adobe Commerce，例如整個結帳頁面的購物車和呼叫。 此資訊是使用者專屬且會因客戶在網站上的活動而持續變更，例如將產品新增至購物車。

如果網站的設計會根據使用者的角色提供不同的回應，則不應為登入的客戶快取GraphQL查詢結果。 例如，您可以建立多個客戶群組，並為每個群組設定不同的產品價格或不同的產品類別可見度。 快取結果（例如此類結果）可能會導致客戶看到其他客戶群組的價格，或顯示錯誤的類別。

## 忽略AEM Dispatcher快取上的追蹤引數

電子商務網站可能會使用PPC搜尋廣告或社群媒體行銷活動來推動其網站的流量。

使用這些媒體表示追蹤ID會新增至該平台的對外連結上。 例如，Facebook會將Facebook點選ID (fbclid)新增至URL，而Google Adverts會新增Google點選ID (gclid)，這會讓您AEM前端的傳入連結如下所示：

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

Gclid和fbclid會隨著每個使用者點按廣告而變更，這是為了追蹤目的，但透過其預設設定，AEM會將每個請求視為一個唯一的頁面，這會繞過Dispatcher並在發佈者和Adobe Commerce上產生不必要的額外負載。

在突增事件期間，這甚至可能導致AEM發佈者超載且無回應。 當頁面的引數設定為忽略時，將會在第一次請求頁面時快取頁面。 無論請求中的引數值為何，都將為該頁面的後續請求提供快取頁面。

>[!NOTE]
>
>進一步瞭解設定的重要性 `ignoreUrlParams` 的可用區段 [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub存放庫。

因此，除了使用GET引數會變更頁面的HTML結構外，應將其設定為依預設忽略「ignoreUrlParams」中的所有引數。 這方面的範例會在搜尋頁面中，搜尋字詞在URL中作為GET引數，在此情況下，您應該手動設定ignoreUrlParams以忽略引數，例如gclid、fbclid以及您的廣告頻道正在使用的任何其他追蹤引數，讓一般網站作業所需的GET引數不受影響。

## MPM工作者對Dispatcher的限制

MPM Worker設定是進階Apache HTTP伺服器設定，需要徹底測試，以根據您的Dispatcher的可用CPU和RAM進行最佳化。 不過，在本白皮書的範圍內，我們建議ServerLimit和MaxRequestWorker應增加到伺服器可用的CPU和RAM支援的層級，然後MinSpareThreads和MaxSpareThreads應同時增加到符合MaxRequestWorker的層級。

此設定會讓Apache HTTP保持「完全整備設定」，這是針對具有大量RAM和多重CPU核心的伺服器的高效能設定。 此設定將透過維持隨時可處理請求的持續開啟連線，從Apache HTTP產生最佳回應時間，並將消除在產生新程式以回應突然流量激增的任何延遲，例如在快閃銷售期間。
