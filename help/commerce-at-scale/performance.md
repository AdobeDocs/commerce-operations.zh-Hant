---
title: 性AEM能優化
description: 優化預設的Adobe Experience Manager配置以支援Adobe Commerce的高負載。
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# AEM效能優化

調度AEM程式是反向代理，可幫助提供快速且動態的環境。 它作為靜態HTML伺服器（如Apache HTTP Server）的一部分工作，目的是以靜態資源的形式儲存（或「快取」）盡可能多的站點內容。 此方法旨在盡可能減少對頁面呈AEM現功能和Adobe CommerceGraphQL服務的訪問。 將大部分頁面作為靜態HTML、CSS和JS提供的結果為用戶帶來了效能優勢，並減少了對環境的基礎架構要求。 任何可能在用戶之間重複相同的頁面或查詢都應考慮進行快取。

以下各節高度顯示了建議的技術重點領域，以便在CIF/Adobe Commerce環境中AEM進行有效快取。

## 基於TTL的調度器緩AEM存

在調度程式上盡可能多地快取站點是任何項目的最佳AEM做法。 使用基於時間的快取失效將快取伺服器端呈現的CIF頁，其時間限制為一定量。 在設定時間過期後，下一個請求將從發佈者和AEMAdobe CommerceGraphQL重建該頁，並將其再次儲存到調度程式快取中，直到下次失效。

TTL快取功能可與ACS AEMAEM Commons包中的「Dispatcher TTL」元件一起配置，並在dispatcher.any配置檔案中設定/enableTTL &quot;1&quot;。

如果啟用，調度程式將評估來自後端的響應標頭，如果它們包含快取控制最大使用期或過期日期，則會建立快取檔案旁的輔助空檔案，修改時間等於到期日期。 在修改時間之後請求快取檔案時，會自動從後端重新請求該檔案。 這提供了一種有效的快取機制，一旦產品更新延遲(TTL)被業務相關方確認和接受，就無需人工干預或維護。

## 瀏覽器快取

上述調度程式TTL方法將大大減少請求並載入到發佈伺服器上，但有些資產很不可能更改，因此，通過在用戶瀏覽器上本地快取相關檔案，甚至可以減少對調度程式的請求。 例如，站點的徽標在站點模板中站點上的每一頁上顯示，不需要每次請求調度程式。 這可以儲存在用戶的瀏覽器快取中。 減少每頁載入的頻寬需求將對站點響應和頁面載入時間產生很大影響。

瀏覽器級別的快取通常通過「快取控制：max-age=&quot;響應標頭。 最大值設定告訴瀏覽器在嘗試「重新驗證」或再次從站點請求檔案之前，應快取檔案的秒數。 快取最大使用期的概念通常稱為「快取過期」或TTL（「生存時間」）。 規模化提供商務體驗 — 與Adobe Experience Manager,Adobe Commerce7

可以設定AEM為在客戶端瀏覽器中快取的/CIF/Adobe Commerce站點的某些區域包括：

- 影像(在模AEM板本身內，例如站點徽標和模板設計影像 — 通過Appiest從Adobe Commerce調用目錄產品影像，稍後將討論快取這些影像)
- HTML檔案（不常更改的頁面 — 條款和條件頁面等）
- CSS檔案
- 所有站點JavaScript檔案 — 包括CIF JavaScript檔案

## Dispatcher statfilelevel anbd寬限期優化

預設調度程式配置使用/statfilelevel &quot;0&quot;設定 — 這意味著單個&quot;。stat&quot;檔案放置在htdocs目錄（文檔根目錄）的根目錄下。 如果對中的頁面或檔案進行更改AEM，則此單個stat檔案的修改時間將更新為更改時間。 如果時間晚於資源的修改時間，則調度程式將考慮所有資源都無效，並且任何後續對無效資源的請求都將觸發對發佈實例的調用。 因此，基本上，通過此設定，每次激活都會使整個快取無效。

對於任何站點，特別是負載較重的商業站點，這會給AEM發佈層帶來不必要的負載量，使整個站點結構僅通過一次頁面更新而失效。

相反，可以將statfilelevel設定修改為更高的值，該值與文檔根目錄的htdocs目錄下子目錄的深度相對應，這樣，當位於某一級別的檔案失效時，只更新該.stat目錄級別及以下檔案。

例如：假設您有產品頁面模板，位於：

```
content/ecommerce/us/en/products/product-page.html
```

每個資料夾級別都將具有「stat level」，如上表中所示。

| 內容(docroot) | 電子商務 | 美國 | 恩 | 產品 | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

在這種情況下，如果將statfilelevel屬性設定為預設「0」，並且product-page.html模板被更新並激活以觸發無效，則從docroot到4級的每個.stat檔案都將被觸碰，而檔案被失效，這將導致從該更改再次從網站（包括其他網站、國家和語言）的所有頁面發佈實例請求。

但是，如果statfilelevel屬性設定為4級，並且對product-page.html進行了更改，則只會訪問該特定網站/國家/語言的產品目錄中的.stat檔案。

請注意，.stat檔案級別不應設定為過高級別 — 超過20可能會對效能產生影響。 在運行效能test時執行批量檔案激活，應該為您提供將狀態級別調整到的正確級別。

配置statfilelevel時要優化的另一個調度程式設定是gracePeriod設定。 這定義了在上次激活後快取中仍然可以提供失效的自動失效資源的秒數。 自動失效的資源由任何激活（當其路徑與調度程式/失效部分匹配，並且與statfilelevel屬性中指定的級別匹配時）而失效。 將gracePeriod設定設定為2秒可用於防止出現這樣的情況：即使發佈者仍在構建新頁面的過程中，也會持續向發佈者發送多個請求。

>[!NOTE]
>
> 有關此主題的更詳細閱讀，請參見 [aem調度器實驗](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub儲存庫。

## CIF — 通過元件進行GraphQL快取

可以將AEM內的各個元件設定為快取，這意味著調用一次GraphQL到Adobe Commerce的請求，然後從快取中檢索到後續請求，直到配置的時間限制，並且不會將進一步的負載AEM載入到Adobe Commerce。 例如，基於分類樹的站點導航以及多面搜索功能中的選項 — 這兩個區域需要在Adobe Commerce上構建資源密集型查詢，但不太可能定期更改，因此是快取的好選擇。 這樣，例如，即使發佈者重建PDP或PLP時，導航生成的資源密集型GraphQL請求也不會命中Adobe Commerce，並且可以從AEMCIF上的GraphQL快取中檢索。

下面的示例是要快取的導航元件，因為它在站點中的所有頁面上發送了相同的GraphQL查詢。 以下請求將過去100個條目快取10分鐘，用於導航結構：

```
venia/components/structure/navigation:true:100:600
```

下面的示例將過去100個多面搜索選項快取到搜索頁中1小時：

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

請求（包括所有自定義的http標頭和變數）必須完全匹配，才能使快取「命中」並防止對Adobe Commerce的重複調用。 應該注意，一旦設定，就沒有簡單的方法手動使此快取失效。 這可能意味著，如果在Adobe Commerce添加了新類別，則在上述快取中設定的到期時間已過期並刷新GraphQL請求之前，該類別不會開始出現在導航中。 搜索小平面也是如此。 但是，鑑於此快取將實現的效能優勢，這通常是可接受的折衷。

可以使用「GraphQL客戶端配置工AEM廠」中的OSGi配置控制台設定上述快取選項。 可以使用以下格式指定每個快取配置項：

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## 混合快取 — 快取調度程式頁中的客戶端GraphQL請求

也可以採用混合方法來快取頁：CIF頁面可能包含始終從客戶瀏覽器直接請求Adobe Commerce最新資訊的元件。 這對於模板中頁面的特定區域非常有用，這些區域對於即時資訊保持最新非常重要：例如，PDP內的產品價格。 如果由於動態價格匹配而價格經常變化，則可以將該資訊配置為不快取在調度程式上，而是可以通過帶AEMCIF Web元件的GraphQL API直接從客戶瀏覽器的客戶端獲取價格。

這可以通過元件設定AEM進行配置 — 對於產品清單頁上的「價格」資訊，可以在產品清單模板中配置，在頁面設定中選擇產品清單元件並檢查「裝貨價格」選項。 同樣的方法也適用於股票水準。

只有在需要即時、不斷更新資訊的情況下才應使用上述方法。 在上例的定價中，可以與業務利益相關方商定，僅在低通信時間每天更新價格，然後執行快取刷新操作。 這樣，在構建顯示定價資訊的每頁時，就不再需要即時定價資訊請求以及隨後給Adobe Commerce帶來的額外負載。

## 不可執行的GraphQL請求

不應快取頁面中的特定動態資料元件，並且始終需要對Adobe Commerce進行GraphQL調用，例如對購物車和整個結帳頁面的調用。 此資訊特定於用戶，並且由於客戶在站點上的活動而不斷變化 — 例如，通過將產品添加到其購物車。

如果站點的設計會根據用戶的角色給出不同的響應，則不應為登錄的客戶快取GraphQL查詢結果。 例如，您可以建立多個客戶組，並為每個組設定不同的產品價格或不同的產品類別可見性。 快取這些結果可能會導致客戶查看另一個客戶組的價格或顯示不正確的類別。

## 忽略調度程式快取上AEM的跟蹤參數

電子商務網站可能會使用PPC搜索廣告或社交媒體活動將流量驅動到其網站。

使用這些介質意味著跟蹤ID將添加到該平台的出站鏈路上。 例如，Facebook將在URL中添加一個Facebook點擊ID(fbclid),Google廣告將添加一個Google點擊ID(gclid)AEM，這將使到前端的傳入連結如下所示，例如：

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

gclid和fbclid將隨按一下廣告的每個用戶而改變，這是為了跟蹤目的，但使用其預設設定AEM，會將每個請求視為唯一的頁面，這樣會繞過調度程式並在發佈者和Adobe Commerce上產生不必要的額外負載。

在電湧事件期間，這甚至會導致AEM發行商超負荷且無響應。 如果將某個參數設定為忽略某頁，則首次請求該頁時會快取該頁。 對該頁的後續請求被提供給快取的頁，而不管該請求中的參數的值如何。

>[!NOTE]
>
>再讀&quot;設定&quot;的重要性 `ignoreUrlParams` 在 [aem調度器實驗](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub儲存庫。

因此，在「ignoreUrlParams」中，預設情況下應將其配置為忽略所有參數，但使用GET參數會更改頁面的HTML結構的情況除外。 例如，在搜索頁中，搜索項作為GET參數在URL中 — 在這種情況下，您應手動配置ignoreUrlParams以忽略廣告渠道正在使用的gclid、fbclid和任何其他跟蹤參數等參數，使正常站點操作所需的GET參數不受影響。

## MPM工作人員對調度員的限制

MPM工作程式設定是高級Apache HTTP伺服器配置，需要進行徹底測試，才能根據Dispatcher的可用CPU和RAM進行優化。 但是，在本白皮書的範圍中，我們建議將ServerLimit和MaxRequestWorkers增加到伺服器可用CPU和RAM支援的級別，然後將MinSpareThreads和MaxSpareThreads都增加到與MaxRequestWorkers匹配的級別。

此配置將使Apache HTTP處於「完全就緒性設定」中，該設定是針對具有大量RAM和多個CPU內核的伺服器的高效能配置。 此配置將通過維護持久的開放連接來為請求提供服務，從Apache HTTP生成盡可能最佳的響應時間，並消除在生成新進程時因突發通信量激增而出現的任何延遲。
