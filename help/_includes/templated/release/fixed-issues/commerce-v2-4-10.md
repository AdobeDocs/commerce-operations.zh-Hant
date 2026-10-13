---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '10868'
ht-degree: 0%
---
# Adobe Commerce已修正問題(v2.4.10-alpha1)

## 已修正v2.4.10-alpha1中的問題

我們已修正Adobe Commerce 2.4.10-alpha1核心程式碼中的169個問題。 此版本中包含的已修正問題子集說明如下。

### API

#### [問題] Creditmemo\Validation\QuantityValidator中的TypeError是由字串數量為min()所造成

為了穩定財務記錄管道並防止在大量自動訂單退款期間發生API請求失敗，在內部銷售銷退折讓單工廠和驗證層新增了資料型別鑄造護欄。

_AC-16056 - [GitHub問題](https://github.com/magento/magento2/issues/40302) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40429) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40303)_

#### 在沒有attribute_id的情況下，REST API屬性更新失敗

修正未提供attribute_id時，透過REST API更新現有產品屬性失敗的問題。 API現在能使用URL中的attribute_code正確識別屬性，並成功更新。

_AC-16424 - [GitHub問題](https://github.com/magento/magento2/issues/40458) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c10554e1)_

#### 當Adobe Stock認證無效時顯示驗證錯誤

當Adobe Stock認證無效時，管理員現在會看到驗證錯誤。

_AC-17123_

#### 透過REST API更新選項時刪除視覺化色票

為了保護目錄資料完整性並簡化自動化整合，已解決EAV色票管理層中的錯誤，在標準選項更新期間，現有的視覺或文字色票值不慎遭到清除。

_AC-9199 - [GitHub問題](https://github.com/magento/magento2/issues/37794) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40872)_

#### 遺失一個SKU時，大量層級價格API會失敗整個批次

先前，當裝載中的任何SKU不存在時，大量層級價格更新API (POST /V1/products/tier-prices)會失敗整個請求，留下沒有更新的有效SKU。 現在，系統會成功處理有效的SKU，同時將遺失的SKU回報為每個專案錯誤，因此單一錯誤專案不再中止整個批次。

_ACP2E-4998 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/51f6d191)_

#### 屬性更新失敗，且標籤值與現有的選項值ID相符

修正標籤與現有選項ID相符時，無法透過REST API建立新下拉式清單/多選產品屬性選項的問題。 之前，即使可透過管理員UI成功建立相同選項，API仍傳回「已存在」錯誤（且可能傳回錯誤的選項ID）。

_ACP2E-5107 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4d0357d7)_

### API、匯入和匯出

#### REST API允許負產品價格，但管理員UI會加以封鎖

透過REST API端點匯入的產品現在會拒絕價格型別屬性（price、special_price、cost及相關MSRP欄位）的負值，這符合管理員UI匯入的行為。 以前，API會在無訊息的情況下接受負值價格並將其儲存下來。

_ACP2E-4941 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/08b91f1a)_

### API、順序

#### 訂單速率限制功能與Valkey快取後端不相容

之前對此固定速率限制的限制會無訊息地略過，而且無論設定多少限制，每個請求都可允許通過。 修正後，若要求超過設定的限制，系統會使用HTTP 429正確加以拒絕。

_ACP2E-4899 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9b6a8bd9)_

### 帳戶

#### [問題]修正：登入表單密碼標籤不正確

修正客戶登入頁面上「密碼」欄位的標籤關聯不正確的問題。 密碼標籤現在可正確鎖定密碼欄位，讓自動測試工具可正確識別密碼。

_AC-16193 - [GitHub問題](https://github.com/magento/magento2/issues/40353) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64eb754d)_

#### [問題]驗證檔案上傳的前端輸入型別

客戶位址檔案上傳現在會在處理前驗證目標屬性的輸入型別是檔案或影像，因此文字和其他非檔案屬性不能濫用為上傳目標。 無效的上傳嘗試會傳回清除驗證錯誤，而不是無法預測地失敗或接受不允許的檔案型別。

_AC-17076 - [GitHub問題](https://github.com/magento/magento2/issues/40795) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40583)_

#### 在網站A上產生的客戶權杖可用於網站B上網站範圍內的客戶設定

為了在多網站例項上強制實施嚴格的客戶資料隔離，已解決GraphQL驗證層中的安全性差距，該層中的權杖在個別邊界上被錯誤驗證。

_AC-17299 - [GitHub問題](https://github.com/magento/magento2/issues/40847) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40858)_

#### [問題]修正PHP 8.5淘汰：使用null作為array_key_exists()的索引鍵引數

修正PHP 8.5上客戶在來賓簽出期間登入失敗，因為使用null索引鍵的已棄用array_key_exists()呼叫的問題。 客戶登入現在可順利運作，而不會產生淘汰錯誤。

_AC-17395 - [GitHub問題](https://github.com/magento/magento2/issues/40875) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/515d3dd3)_

#### [問題] magento/magento2：新增i18轉譯至requestPasswordResetEmail和resetPassword GraphQL變動

為了確保完全本地化的Headless店面體驗，客戶帳戶復原API端點已新增國際化(i18n)翻譯功能

_AC-9356 - [GitHub問題](https://github.com/magento/magento2/issues/29658) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/28950)_

### 管理員UI

#### 使用彙總資料時，儀表板預設會顯示過去7天

修正啟用彙總銷售資料時，控制面板預設為顯示今天的問題。 使用彙總資料時，控制面板現在預設會顯示過去7天。

_AC-13799 - [GitHub問題](https://github.com/magento/magento2/issues/28152) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 對於簡單產品的相同設定，購物車頁面和產品頁面中的FPT值不同

修正固定產品稅(FPT)值在產品與購物車頁面上針對相同稅務設定顯示不同的問題。 FPT值現在會在產品、目錄、迷你購物車和購物車頁面上以一致的方式顯示。

_AC-17007 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ecbeba3a)_

#### 延遲設定實施

效能最佳化，可藉由延遲解析範圍系統組態資料，同時保留現有的組態行為，改善組態載入效能。

_ACP2E-4751 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/65f660bd)_

#### GegRTE編輯器封鎖emoji - javascript驗證失敗

修正在PageBuilder內容型別模組（文字、橫幅、幻燈片）內編輯時，GegRTE封鎖儲存包含utf8mb4表情符號（例如🔵⚪🔴）的內容的問題。 先前，這些模型表單的wysiwyg驗證設定會將`allowUtf8mb4`解析為`false`，導致編輯器拒絕4位元組UTF-8字元，即使資料庫完全支援utf8mb4的安裝亦然。

_ACP2E-4822 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### 受限制的管理員無法在升級後刪除客戶

已修正受限管理員在升級後無法刪除客戶的問題，在客戶格線頂端會有一個紅色橫幅，指出：「需要更多許可權才能檢視此專案。」

_ACP2E-4838_

#### 在管理面板的客戶編輯頁面中檢視擁有大型通訊錄的客戶時，管理員會登出

修正管理員在管理面板的客戶編輯頁面中檢視擁有大型通訊錄的客戶時，遭登出的問題

_ACP2E-4875 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

#### 訂單未出現在銷售網格中

修正在啟用非同步網格索引時，新訂單延遲出現在Sales網格中的問題，這是因為調解游標在趕上最新實體後會重設。 新專案現在會在下次cron執行時出現在格線中。

_ACP2E-4893 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

#### 啟用Magento_VisualMerchandiser時，[雲端]在類別產品格線中遺失指派的產品篩選器

修正啟用Visual Merchandiser時， Add Products強制回應視窗搜尋All Products格線中缺少「已指派」篩選器的問題。 以前，管理員使用者無法依在該強制回應視窗中的已指派/未指派狀態來篩選產品，導致難以識別哪些產品已在類別中。

_ACP2E-4974_

#### 動作記錄不會顯示與傳回相關動作的傳回編號/傳回ID

修正退貨編號/退貨ID未顯示在退貨相關管理動作的動作記錄專案的問題。 以前，檢視或儲存RMA等動作會記錄在動作記錄中，不會傳回任何識別碼，這與正確顯示訂單編號的訂單相關動作不同。

_ACP2E-5050_

#### 針對在商店檢視範圍儲存的管理員產品上的價格和稅捐類別，取消勾選「使用預設值」

受限制的管理員使用者現在可以在商店檢視範圍儲存產品，而不會遺失「價格」、「狀態」和「稅捐類別」屬性的「使用預設值」狀態。 先前，將產品儲存為受限制的管理員（拒絕價格與狀態編輯功能）時，系統會無訊息地取消勾選這些欄位的「使用預設值」，導致系統撰寫存放區檢視層級覆寫，即便您原本沒有想要這麼做。

_ACP2E-5081_

### 管理員UI，訂購

#### 當兩個分組產品共用相同的簡單產品時，「管理員建立訂單」中分組產品的價格顯示不正確

修正當共用相同簡單產品的兩個分組產品都設定而未新增至購物車時，「管理員建立訂單」中分組產品的價格計算錯誤的問題。

_ACP2E-4965 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/08b91f1a)_

### 管理員UI、UI架構

#### Magento2重新導向至首頁，而非顯示錯誤選單宣告的錯誤

為了最佳化擴充功能開發工作流程並確保穩定的後端載入，已解決結構路由缺陷，其中無效的管理功能表宣告會觸發無訊息瀏覽器回圈失敗，而非顯示可操作的診斷訊息。

_AC-7543 - [GitHub問題](https://github.com/magento/magento2/issues/36632) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40881)_

### Analytics/報表

#### [QUANS]是否可以在進階報告底下的客戶KPI表格中顯示客戶電子郵件ID和名稱

Adobe Commerce現在於匯出至進階報告的資料中包含客戶名字、中間名和姓氏，可讓客戶KPI表格顯示客戶名稱。 先前只會匯出編碼的客戶識別碼，因此商家無法在進階報表中依名稱識別客戶。

_ACP2E-3928 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4d0357d7)_

#### 大量插入於sales_bestsellers_aggregated_monthly

改善aggregate_sales_report_bestsellers_data cron的效能。

_ACP2E-4559 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 加入購物車事件承載是舊版Universal Analytics增強型電子商務格式，而非GA4電子商務格式。

修正前，透過Google Tag Manager傳送至Google Analytics 4的電子商務事件使用舊版Universal Analytics格式，且遺失數個結帳事件。 修正後，所有電子商務事件都使用正確的GA4格式，並追蹤完整簽出funnel。

_ACP2E-5176 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/24667df1)_

### B2B

#### placeNegotialQuoteOrderV2傳回total.total_shipping = null （針對來自可轉讓報價的訂單）

修正placeNegotiableQuoteOrderV2針對來自可轉讓報價且已付運的訂單，傳回Null出貨總計的問題。 API現在會正確傳回運送金額，符合訂單總計中包含的運送費用。

_AC-18083_

#### 報價轉換為訂單後，[B2B]報價詳細資料中遺失套件選項價格

修正了在報價轉換為訂單後，可轉讓報價詳細資訊頁面上遺失捆綁產品選項價格的問題。

_ACP2E-5055_

### B2B，訂購

#### 清除59M以上報價表的相關說明（sales_clean_quotes無法執行）

修正`sales_clean_quotes` cron工作在含有大型報價表的執行個體上逾時的問題。 以前，清理查詢不必要地從`negotiable_quote`表格中選取了所有資料行，導致MySQL在數百萬個資料列上執行完整的檔案匯入；而且每個引號都透過PHP模型層個別刪除，增加了效能成本。

_ACP2E-4891 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

### 購物車與結帳

#### 新增至相關產品的購物車通知

修正當新增產品及其相關產品時，「新增至購物車」通知未包含相關產品的問題。
通知現在會顯示新增至購物車的兩個產品名稱。

_AC-11976 - [GitHub問題](https://github.com/magento/magento2/issues/27164) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/515d3dd3)_

#### [問題]更新CartRepositoryInterface.php

更新CartRepositoryInterface.php以宣告儲存購物車時可能擲回的例外狀況。 這可讓介面與基礎購物車儲存實作保持一致。

_AC-13323 - [GitHub問題](https://github.com/magento/magento2/issues/39328) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/29a7cdbe)_

#### [錯誤]在結帳出貨步驟中新增地址時，送貨地址中的公司欄位在多商店設定中設為Null

修正在多商店設定中結帳時客戶新增運送地址時，「公司」欄位未儲存的問題。 公司值現在已正確儲存在報價單、下單和客戶通訊錄中。

_AC-13456 - [GitHub問題](https://github.com/magento/magento2/issues/39424) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/515d3dd3)_

#### Paypal >客戶資料不符（首碼、名字、姓氏）

修正在PayPal SEPA結帳流程中，客戶名稱詳細資料對應錯誤的問題。 字首、名字和姓氏現在會以正確順序填入，不會有任何不符。

_AC-15366 - [GitHub問題](https://github.com/magento/magento2/issues/39061) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ecbeba3a)_

#### 虛擬產品的free_shipping旗標不正確

修正將多個專案新增至購物車時，虛擬產品的free_shipping旗標設定不正確的問題。 套用適用的免運費規則時，所有專案的標幟現在都已正確設定。

_AC-15648 - [GitHub問題](https://github.com/magento/magento2/issues/40184) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c10554e1)_

#### 訪客加入購物車：迷你購物車/客戶資料「購物車」區段在報告購物車下顯示為空白，儘管專案已正確持續存在

修正訪客迷你購物車在將產品新增至購物車後未立即反映專案的問題。 迷你購物車計數器和下拉式清單現在會正確更新，而且新增的產品會如預期顯示在購物車中。

_AC-17973 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2b218686)_

#### AJAX加入購物車內嵌錯誤訊息遺失role=&quot;alert&quot;語意

修正店面顯示AJAX購物車加值錯誤訊息，但熒幕助讀程式未公告的問題。 加入購物車錯誤現在會顯示在accessible role=&quot;alert&quot;區域中，以取得適當的協助工具支援。

_AC-18036 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2b218686)_

#### 捨棄送貨金額的後續規則

為確保促銷定價準確且嚴格遵守設定的折扣規則，已解決購物車價格規則計算器中的瑕疵，其中低優先順序的送貨折扣套用不正確

_AC-9612 - [GitHub問題](https://github.com/magento/magento2/issues/37985) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40869)_

#### 即使觸發錯誤，仍會建立重複的訂單

修正仍然可能以無效客戶地址下訂單的問題

_ACP2E-4774 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 可設定產品對結帳的效能影響(totals-information、estimate-shipping-modules)

修正之前，當第一個可銷售子項出現在子項清單中較晚時，對於包含許多子項產品的可設定產品而言，像是總計資訊和預估送貨方法的結帳請求可能會顯著變慢。 修正後，此效能降級不會再發生，且回應時間會維持一致，無論第一個可銷售子系的位置為何。

_ACP2E-4805 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/30fbdb0f)_

#### 在每次購物車頁面檢視時重新計算購物車總次數

已最佳化購物車頁面上的購物車總計請求。 每個購物車頁面檢視會重新計算購物車總金額兩次。

_ACP2E-4817 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

#### 客戶地址屬性(EAV)城市和街道驗證規則與硬式編碼驗證規則衝突。

修正城市驗證器錯誤地拒絕長度超過100個字元的有效城市名稱（資料庫限製為255），以及在資料庫中長度超過255個字元的街道地址可能會無訊息截斷但無訊息的問題\
傳回驗證錯誤。 現在，兩個驗證器都會強制所有位址表格中符合最窄資料庫資料行限制條件的限制。

_ACP2E-4861 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

#### [店面]加入購物車「要求的數量無法使用」訊息間歇性地未在PDP上呈現

修正庫存無法使用訊息（「無法取得請求數量，請減少數量」）的問題。 在嘗試新增至購物車失敗後，間歇性地未顯示在產品詳細資料頁面上。 以前，如果購物者針對購物車中已完全保留可用存貨的產品，重複按一下「加入購物車」，頁面可能會自動重新整理，且沒有錯誤回饋。

_ACP2E-5071 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8d70f246)_

#### 當登出時清除持續性=是時，在自然工作階段到期時清除持續性購物車

修正瀏覽器工作階段過期時，永久購物車被清除的問題。 先前，在啟用「登出時清除持續性」後，過期的作業階段會清空購物車並移除持續性Cookie，即使購物者未登出亦然。

_ACP2E-5088 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/597c7211)_

#### 重試結帳時，restoreQuote()之後未從帳單地址重新同步來賓報價customer_email

修正重試失敗的訪客結帳時，使用先前輸入的電子郵件（而非更新的電子郵件）下達訂單的問題。

_ACP2E-5188 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL的「購物車與結帳」

#### Quote GraphQL API可能會將貨幣物件（而非ISO貨幣代碼）指派給報價欄位

更新Quote GraphQL API，將ISO貨幣代碼指派給報價的存放區和報價貨幣欄位，而非指派貨幣物件。

_ACP2E-5229 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/24667df1)_

### 目錄

#### [問題] Magento_ConfigurableProductGraphQl、Magento_MsrpConfigurableProduct、Magento_NewRelicReporting和Magento_Swatches模組的module.xml檔案改良。

從四個核心子模組中移除多餘的Magento_Catalog相依性，以最佳化模組宣告架構。 此清理可解決相依性樹狀結構中不必要的重複、簡化模組載入順序計算，並改善長期框架可維護性而不會引入重大變更。

_AC-10762 - [GitHub問題](https://github.com/magento/magento2/issues/30675) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/30638)_

#### 可設定專案的getUsedProducts函式中可能發生記憶體洩漏

修正處理多個可設定產品導致執行時間和記憶體使用量隨時間增加的問題。
現在可設定的產品無需漸進式減速與記憶體增加即可處理。

_AC-10942 - [GitHub問題](https://github.com/magento/magento2/issues/37639) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/8c058c2e)_

#### 非錨點類別上可見的「依類別購買」篩選器

修正即使在「管理員」中停用類別篩選器，仍會在非錨點類別上顯示「依類別購買」篩選器的問題。
現在已根據設定的設定，在店面隱藏該篩選器。

_AC-10945 - [GitHub問題](https://github.com/magento/magento2/issues/38379) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64eb754d)_

#### 報價和報價專案中applied_rule_ids的資料型別不同

為確保絕對資料庫結構描述一致性，並防止高流量促銷商店上嚴重的購物車資料不相符，已在父結帳結構中展開資料欄以追蹤作用中的促銷定義。

_AC-14518 - [GitHub問題](https://github.com/magento/magento2/issues/39838) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40540)_

#### 如果價格是全域範圍，則無法取得產品集合範圍設定的`decimal`屬性

為確保國際設定上的店面定價和屬性呈現精確，解決儲存區特定小數值被預設全域值錯誤取代的核心資料收集錯誤。

_AC-15806 - [GitHub問題](https://github.com/magento/magento2/issues/40218) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40419)_

#### 不正確處理GET引數

為了改善平台穩定性及保障結帳funnel，新增了區塊層級的輸入驗證層，以防止格式錯誤的URL查詢當機造成店面產品頁面。

_AC-16262 - [GitHub問題](https://github.com/magento/magento2/issues/40405) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes：：afterGetProductAttributes已在所有購物車查詢上觸發

為了減少資料庫執行壓力，並消除客戶結帳期間未最佳化的資料庫點選，銷售規則產品設定外掛程式已最佳化，以便有條件地執行並利用快取結構。

_AC-16559 - [GitHub問題](https://github.com/magento/magento2/issues/40226) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40251)_

#### [問題] [PHPDOC]修正函式Magento\Sales\Model\Order中的orderComment

為了消除嚴格的輸入限制、增強靜態分析準確性並改善開發人員在嚴格內嵌引擎(如PHPStan （第5級或以上）)下的體驗，內嵌結構檔案區塊已在銷售訂單核心子系統中標準化。

_AC-16759 - [GitHub問題](https://github.com/magento/magento2/issues/39575) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39572)_

#### [問題] [錯誤] GraphQL SearchCriteriaValidator未載入 — 已由module-graph-ql di.xml陣列覆寫移除

為了保留健全的查詢驗證並強制執行平台護欄，已解決無意中停用SearchCriteriaValidator層的相依性插入(DI)設定瑕疵。

_AC-16959 - [GitHub問題](https://github.com/magento/magento2/issues/40762) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40742)_

#### strpos()預期引數1為字串，指定陣列 | magento/module-eav

為了保護店面的穩定性並提供不間斷的客戶探索體驗，進階目錄搜尋處理引擎中已經解決了一個嚴重的型別不符問題。

_AC-1706 - [GitHub問題](https://github.com/magento/magento2/issues/33588) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40422)_

#### 客戶造訪頁面時正在建立空白的報價記錄

造訪店面的產品頁面在某些情況下不會建立空白的報價記錄。
先前當客戶造訪店面的產品頁面時，會建立空白的報價記錄

_ACP2E-4682 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 產品詳細資訊頁面「重量」屬性未在「其他資訊」區段中顯示單位尾碼

修正店面產品頁面的「重量」屬性在「其他資訊」或「更多資訊」區段中僅顯示原始數值而沒有設定測量單位（磅或公斤）的問題。

_ACP2E-4808 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

#### [雲端]目錄價格規則啟用直到下次強制重新同步才會反映在即時搜尋中 — 價格摘要同步延遲

修正啟用目錄價格規則時，在稍後強制重新同步前，不會更新「即時搜尋」中的價格的問題。 價格摘要索引子可能會在其所依賴的目錄規則索引子完成之前執行，因此會匯出過時的價格。 具有未完成相依性的索引器現在會延遲到下次cron執行，因此價格摘要一律會針對最新價格執行。

_ACP2E-5029 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec436b10)_

#### [CLOUD] Adobe Commerce Cloud類別規則或運運算元邏輯問題

Contains運運算元現在接受多個逗號分隔值，以OR比對評估。 因此，單一規則列可比對數個辭彙中的任何一個，而非一個。

_ACP2E-5061_

#### 沒有為新新增的產品影像儲存替代文字（標籤）

修正上傳的檔案在儲存時因媒體收藏集中的檔案名稱衝突而重新命名時，新上傳產品影像的替代文字（標籤）未儲存的問題。 先前，影像角色屬性(image、small_image、thumbnail)已正確儲存，但是它們對應的*_label屬性會以無訊息的方式刪除，使店面搜尋和清單頁面上的替代文字保持空白。 相簿建立處理常式現在會將重新命名的檔案解析回其原始影像專案，因此所有指派的影像角色都會保留標籤。 因此，在產品建立期間輸入的替代文字會可靠地儲存並在店面中呈現。

_ACP2E-5216 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/24667df1)_

#### PHP 8.5「null as array offset」在使用者缺少「編輯產品狀態」資源時，在admin中開啟「新增產品」頁面時出現過時錯誤

先前，沒有「編輯產品狀態」許可權的管理員使用者在開啟「新增產品」頁面時，可能會遇到「null as array offset」的過時錯誤。 此問題已修正，因此無論使用者的產品狀態許可權為何，頁面都會正確載入。

_ACP2E-5248 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/24667df1)_

### 目錄， GraphQL

#### [GraphQl]產品查詢價格篩選器問題，與在adminHTML中輸入的淨價有關

修正GraphQL產品查詢在套用價格篩選器時未考量稅金的問題。
價格篩選器現在會使用顯示的含稅價格，因此系統只會傳回指定價格範圍內的產品。

_AC-6883 - [GitHub問題](https://github.com/magento/magento2/issues/36337) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8b67e8ed)_

### 目錄，效能

#### 目錄許可權索引管道不遵循[CLOUD] customer_group_excluded_website

目錄許可權索引現在會排除從客戶群組排除的網站。

_ACP2E-5223_

### 目錄，SEO

#### 所有商店檢視的類別url_path未在url_key變更時同步

以往，在「所有商店檢視」範圍變更類別的URL索引鍵，可能會讓商店範圍內的子類別保留過時或首碼不正確的url_path，而使用類別自己的商店特定url_path覆寫來編輯類別，可能會挑選其預先編輯的URL索引鍵，而不是新輸入的URL索引鍵。 此問題現在已修正 — URL索引鍵變更會以正確的階層順序，正確地重疊至所有店面範圍子代，並具有正確的父路徑，而類別自己的店面範圍url_path覆寫會使用剛剛變更的URL索引鍵重新計算，因此店面範圍的URL在儲存後會立即保持準確。

_ACP2E-5113 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/597c7211)_

### 雲端、框架

#### 啟用SymfonyL2的效能回歸與不正確的快取儲存

修正將L1快取儲存路徑設定為絕對路徑（例如/dev/shm）時，導致其無訊息地重新導向至var/目錄的問題，以及另一個使大型目錄上的快取標籤失效的效能問題，可能會因為封鎖Redis作業而造成顯著的回應時間延遲。

_ACP2E-4989 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/51f6d191)_

### 內容

#### 為不同網站建立的CMS頁面在前端顯示錯誤的頁面

先前，在多網站設定中，若未針對每個網站設定Website Restriction登陸頁面快取索引鍵的範圍，導致在次要網站店面提供錯誤的CMS頁面。 WebsiteRestriction/Controller/Index/Stub.php中的快取索引鍵現在正確包含透過商店管理員解析的目前網站ID。

_ACP2E-4593_

#### 啟用全域客戶共用時，客戶區段評估僅會從第一個網站傳回客戶，而非所有指派的網站

修正啟用「全域客戶共用」時，「客戶區段」評估僅會從第一個網站傳回客戶，而非所有指派網站傳回客戶的問題。

_ACP2E-5079_

#### 頁面產生器ajax預覽請求傳回500錯誤，並停用翻譯快取

無論已啟用或停用轉譯快取，PageBuilder預覽現在都能正確轉譯。 先前，停用轉譯快取時，PageBuilder預覽無法呈現。

_ACP2E-5118 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### 啟用「啟用舊媒體集」時，動畫GIF上傳會轉換為PNG

修正啟用舊版媒體集時，透過媒體集上傳的GIF動畫影像會轉換為PNG的問題。 先前，當「啟用前端調整大小」開啟時，透過舊媒體集上傳的動畫GIF會遺失動畫，並儲存為靜態PNG檔案。 動畫GIF現在會以原始格式上傳和儲存。

_ACP2E-5232 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/24667df1)_

### 內容/CMS

#### [問題]當影像屬性標籤包含單引號時，請修正產品庫標籤

為了確保管理面板中的目錄管理體驗可靠且不會中斷，已解決JavaScript格式問題，此問題已完全中斷後端產品工作區介面

_AC-16474 - [GitHub問題](https://github.com/magento/magento2/issues/40519) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40870)_

#### [問題]當已存取調整大小的影像URL但尚未存在時，改善效能。

為了最大化資產傳送回應速度、大幅減少伺服器磁碟I/O並防止嚴重的伺服器處理器尖峰，目錄影像產生子系統已最佳化，以嚴格依需求處理遺失的媒體URL。

_AC-16547 - [GitHub問題](https://github.com/magento/magento2/issues/40399) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40388)_

#### 回歸：非UTF-8編碼的URI元件仍在2.4.7-p5的CatalogWidget中擲回「無法序列化值」

為了消除因不良生產Web流量導致的嚴重演算失敗，已增強目錄Widget區塊，以適當地處理請求URL內的非UTF-8資料序列。

_AC-17264 - [GitHub問題](https://github.com/magento/magento2/issues/40824) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40825)_

#### 編輯全域設計設定範圍時`Using null as an array offset is deprecated, use an empty string instead`

修正由於已棄用的null陣列位移，在「內容>設計>設定」下編輯全域範圍時，在PHP 8.5上傳回HTTP 500錯誤的問題。 全域設計設定現在已成功開啟且沒有錯誤。

_AC-17456 - [GitHub問題](https://github.com/magento/magento2/issues/40886) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/515d3dd3)_

### 框架

#### 當媒體資料庫儲存裝置未使用或停用時，從media_storage_file_storage選取

為了減少不必要的資料庫查詢開銷並消除雜訊系統例外狀況，媒體檔案同步處理層已經過最佳化，可在系統明確設定為使用本機檔案系統時，略過資料庫儲存檢查

_AC-10586 - [GitHub問題](https://github.com/magento/magento2/issues/38116) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40480)_

#### 當Cookie存放區為陣列時，例外狀況建構函式擲回嚴重錯誤

修正無效的商店Cookie值造成PHP嚴重錯誤的問題。
當存放區Cookie包含無效值時，Magento現在會正確擲回「無效的存放區引數」例外狀況。

_AC-10888 - [GitHub問題](https://github.com/magento/magento2/issues/38365) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [問題]在Magento\Customer\Model\Address\Config中使用靜態常數

修正自訂位址設定類別必須複製getFormats()才能使用自訂位址範本路徑的問題。 自訂位址設定現在可以使用靜態常數定義自己的範本路徑，而不需要複製方法。

_AC-12906 - [GitHub問題](https://github.com/magento/magento2/issues/39135) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 無法在產品集合上使用processFilter

修正使用FilterProcessor將多個篩選器套用至產品集合時導致PHP錯誤的問題。 現在可以使用多個篩選條件正確篩選產品集合。

_AC-15018 - [GitHub問題](https://github.com/magento/magento2/issues/40014) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7aecc9f1)_

#### 大型目錄可能的索引器效能問題 — 大量插入並鎖定整個CL表格以識別最新版本

為了保護大型企業規模目錄上的資料庫效能，系統資料庫索引器管線已經過強化，可以剖析限制批次中排程的資料修改，消除高壓資料庫鎖定。

_AC-16238 - [GitHub問題](https://github.com/magento/magento2/issues/40331) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40546)_

#### [問題]效能改善

為了消除不必要的記憶體配置並降低執行階段處理負荷，已重構數個核心字串操作常式，以利用最佳化的PHP原生行為。

_AC-16565 - [GitHub問題](https://github.com/magento/magento2/issues/40383) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40375)_

#### [問題]非GNU Linux系統上的GLOB_BRACE修正支援

為了保證輕量級虛擬化環境間的順暢部署功能，已修正一個關鍵路徑探索錯誤，以完全還原對使用非GNU程式庫（例如Alpine Linux Docker映像）之系統的執行支援。

_AC-16568 - [GitHub問題](https://github.com/magento/magento2/issues/40552) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40538)_

#### 行銷引數新增回用於建立內建FPC識別碼的查詢

為了改善快取命中率並消除伺服器效能回歸，原生內建全頁快取(FPC)系統中已修正結構缺陷，其中行銷和追蹤查詢引數意外地重新引入快取識別碼簽章中。

_AC-16583 - [GitHub問題](https://github.com/magento/magento2/issues/40350) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40349)_

#### 在訊息佇列通訊中新增對具有升級屬性的純物件的支援

為了支援現代PHP開發實踐並簡化非同步架構工作流程，已增強框架反射引擎，以利用公用、提升和唯讀建構函式屬性原生處理資料傳輸物件(DTO)。

_AC-16672 - [GitHub問題](https://github.com/magento/magento2/issues/36660) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40457)_

#### [問題]修正：實數欄型別內部檢查略過未簽署/可空值的處理器，使用預設值

為了確保準確的系統設定追蹤，已解決資料庫抽象化缺陷，其中宣告式結構描述驗證命令會持續報告缺少明確精確度或比例屬性的DOUBLE UNSIGNED欄的暫止修改變更。

_AC-16758 - [GitHub問題](https://github.com/magento/magento2/issues/40646) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40582)_

#### [功能]支援admin config中個別選取選項的「已停用」狀態

為提高後端表單的彈性，並為開發人員提供精細的版面配置控制，我們引進了架構層級的支援，將個別選項標籤標示為表單元素內無法選取。

_AC-16761 - [GitHub問題](https://github.com/magento/magento2/issues/40564) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40565)_

#### ⚡效能：遺失StoreManager中的記憶體以及存放區模組中的外掛程式額外負荷

為了大幅降低CPU執行壓力並將不必要的應用程式記憶體流失降至最低，已實施關鍵設定值快取常式，以攔截冗餘存放區檢查流程。

_AC-16838 - [GitHub問題](https://github.com/magento/magento2/issues/40706) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40732)_

#### [問題]修正：移除JwkFactory中廢棄的openssl_free_key()程式碼路徑

為了清理結構性技術債務並將加密工具與現代執行設定檔對齊，已從JSON Web Key公用程式後端清除舊版的資源釋放鉤點。

_AC-16958 - [GitHub問題](https://github.com/magento/magento2/issues/40761) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40688)_

#### [問題] PHPDoc更正拼字

為了維持高程式碼品質標準並改善整合式開發環境(IDE)程式碼提示的正確性，已在核心框架模組中的內嵌程式碼檔案層套用結構清理。

_AC-16960 - [GitHub問題](https://github.com/magento/magento2/issues/40763) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40745)_

#### [問題] perf(di:compile)：快取Type、Config/Reader和ClassReader中的ReflectionClass具現化

為了大幅加快編譯時間並最大化持續整合(CI)部署輸送量，已最佳化內部相依性插入編譯器後端(`setup:di:compile`)，以消除多餘的PHP反射週期。

_AC-17077 - [GitHub問題](https://github.com/magento/magento2/issues/40796) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40615)_

#### [問題]更新Filter.php以允許`{{block template="Magento_Module::path/to/template.phtml"}}`並將\Magento\Framework\View\Element\Template設定為預設類別

為了簡化內容建立並將CMS指令與範本配置標準保持一致，核心標籤標籤處理系統已增強，以支援沒有明確類別定義的區塊宣告。

_AC-17078 - [GitHub問題](https://github.com/magento/magento2/issues/38477) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38469)_

#### [問題] perf(di:compile)：在編譯期間將攔截設定範圍讀取記憶體

為了大幅加快網站部署和自動化後端編譯，已最佳化相依性插入編譯器(`setup:di:compile`)，以消除多餘的XML剖析作業。

_AC-17313 - [GitHub問題](https://github.com/magento/magento2/issues/40852) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40614)_

#### 將underscore.js升級至1.13.8以防止出現安全性弱點

套件式Underscore.js程式庫(lib/web/underscore.js)已從1.13.7升級至1.13.8。不需變更設定。

_AC-17349 - [GitHub問題](https://github.com/magento/magento2/issues/40857) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/12d0be1e)_

#### 當部署目的地為symlink時，magento-composer-installer會自動取消填入設定/ （和其他對應的目錄）

修正magento-composer-installer在部署目標設定為符號連結時，無法自動填入setup/和其他Composer對應目錄的問題。 這可能會導致檔案遺失和不完整的Commerce部署。

_AC-17360 - [GitHub問題](https://github.com/magento/magento2/issues/40864)_

#### 使用Symfony快取配接器時，快取預先載入金鑰不再需要識別碼首碼

現在可以設定Symfony快取配接器的預先載入金鑰(preload_keys)，而不需要快取id_prefix。 先前，依照記錄的設定並在每個索引鍵上加上前置詞（例如061_SYSTEM_DEFAULT），導致不會預先載入索引鍵。 您現在可以指定與應用程式要求完全相同的金鑰（例如，SYSTEM_DEFAULT），而Adobe Commerce會自動套用id_prefix。

_AC-17407 - [GitHub問題](https://github.com/magento/magento2/issues/40877) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3a6b9667)_

#### [問題]當類別屬性有「frontend_input」時，修正PHP 8.5的過時問題……

修正在「管理員」面板中開啟類別時，類別屬性將frontend_input設定為null時，PHP 8.5上發生錯誤的問題。 類別頁面現在會開啟，而且可以成功編輯，而不會出現棄用錯誤。

_AC-17499 - [GitHub問題](https://github.com/magento/magento2/issues/40908) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [問題]取代已棄用的PHPUnit宣告和test-stub設定

更新Magento 2的核心單元測試套件，以取代七項過時的PHPUnit使用方式，以供日後PHPUnit升級之用。 這些變更會處理測試stub上的`isType()`宣告和`with*()`設定，這些模式會在目前的PHPUnit版本中觸發淘汰通知，並預定在PHPUnit 13或更新版本中移除。

_AC-17750 - [GitHub問題](https://github.com/magento/magento2/issues/41040) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/41033)_

#### GraphQL order_date和comment時間戳記在非en_US地區設定下傳回錯誤的行事曆日期(IntlDateFormatter misparse) — AC-14431修正不完整

修正GraphQL訂單日期可能針對法文和德文地區設定顯示錯誤行事曆日期的問題。
訂單日期和相關的註解時間戳記現在會傳回正確的日期和時間。
改善日期格式，讓應用程式能夠可靠地剖析GraphQL日期值。
en_US語言環境的現有行為保持不變。

_AC-18084 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d10ab92b)_

#### [問題]移除禁止使用的@author標籤

為確保與核心技術准則嚴格保持一致，已完成增量程式碼維護清理，以清理多個系統模組間的內嵌資原始檔區塊。

_AC-8366 - [GitHub問題](https://github.com/magento/magento2/issues/37248) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36993)_

#### [問題]從`Magento_Catalog`移除禁止的`@author`標籤（第2部分）

為確保完全符合Magento的統一程式碼傳送准則，已執行累加清理通過，以系統化地移除核心店面資源模型中不符合規範的檔案註解。

_AC-8370 - [GitHub問題](https://github.com/magento/magento2/issues/37247) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36988)_

#### 階層價格儲存介面刪除錯誤不會刪除所有階層價格

解決TierPriceStorage中，刪除多個網站上的產品層級價格時，無法更新價格ID比對邏輯來說明指派的網站ID，進而刪除所有價格的問題。

_AC-9738 - [GitHub問題](https://github.com/magento/magento2/issues/37949) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40557)_

#### [B2B]採購單未透過ActiveMQ自動轉換為銷售訂單

修正搭配STOMP通訊協定使用ActiveMQ時，由cron啟動的使用者未處理訊息的問題。 因此，自動核准的採購單不會轉換為銷售訂單。 STOMP佇列的訊息處理現在更可靠，且與DB和AMQP佇列實作一致。

_ACP2E-4349 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/08b91f1a) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/239464da)_

#### 使用已設定的AWS S3儲存空間匯出失敗

現在起，設定AWS S3遠端儲存空間時，產品匯出可正常運作。 以前，因為儲存驅動程式中的路徑解析無效，所以無法將匯出的檔案寫入S3。

_ACP2E-4786 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 索引子卡在具有&#39;use_application_lock&#39;和&#39;file&#39;提供者的自我鎖定回圈中

修正當索引器use_application_lock設定與檔案鎖定提供者一起啟用時，在重新索引期間索引器無限期擱置的問題。 重新索引作業現在如預期般完成。

_ACP2E-5027 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec436b10)_

#### 在雲端UI下設定MAGENTO_DC變數，導致效能緩慢

修正後，每當要求的索引鍵不存在且已定義某些環境變數時，都不會重新載入部署設定。

_ACP2E-5094 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2b9e8316)_

#### [雲端]格式錯誤的URL路徑在URL重寫路由器中傳回HTTP 500而非404

修正格式錯誤的店面URL傳回HTTP 500錯誤頁面，而非標準404 「找不到」的問題。 以前，某些格式錯誤的請求路徑會在URL重寫解析期間導致未攔截到的錯誤。

_ACP2E-5154 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4d0357d7)_

#### [CLOUD] PHP 8.5相容性 — ComponentRegistrar：：getPath() null陣列位移當機設定:static-content:在2.4.9上部署（壓縮策略）

修正編譯使用//@magento_import指令的模組LESS檔案時，`setup:static-content:deploy`在PHP 8.5上失敗並出現「使用null作為陣列位移」錯誤的問題。 靜態內容部署現在已於PHP 8.5成功完成。

_ACP2E-5183 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS]使用錨點href及後面跟著另一個屬性儲存CMS區塊時，出現誤判「提供的HTML內容無效」

包含標準錨點連結（例如`&lt;a href="https://example.com/page" target="_blank" rel="noopener">`）的CMS內容在啟用cms/wysiwyg/force_valid時，不再觸發誤判的「提供的HTML內容無效」驗證警告或儲存失敗。

_ACP2E-5203 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/24667df1)_

### 框架，GraphQL

#### 如果稍後設定使用數值索引鍵，則會取代di.xml陣列專案

為了保護架構資料完整性及改善模組擴充性，相依性插入(DI) XML剖析引擎中的核心錯誤已經解決，其中使用數值索引鍵「0」的陣列設定在模組編譯期間被自動覆寫或捨棄。

_AC-8102 - [GitHub問題](https://github.com/magento/magento2/issues/36861) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### 如果屬性程式碼為模型，addProductsToCart會對custom_attributesV2擲回錯誤

修正當產品具有包含程式碼模型的自訂屬性時，addProductsToCart傳回內部伺服器錯誤的問題。 現在可以透過custom_attributesV2正確擷取自訂屬性。

_AC-16987 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/809ba93c)_

#### 當stock_status為IN_STOCK時，GQL數量Null

產品GraphQL查詢中的數量欄位對自訂MSI庫存中的產品錯誤地傳回null。 解析程式在擷取實際存貨數量之前，會將cataloginventory/options/not_available_message設定值的回應閘道，而且此設定的XML預設值（2 — 「沒有足夠的料號可供銷售」）會導致在任何新存放區傳回null，而沒有明確的系統管理員覆寫。
可銷售數量解析後，現在會評估檢查。 只有當產品沒有可用存貨(saleableQty &lt;= 0)且商店明確設定了「沒有足夠的商品可供銷售」時，才會傳回null。 無論此組態設定為何，有庫存的產品一律會傳回其實際可銷售數量。 設定讀取也會更正為使用存放區範圍，以便遵循存放區層級的覆寫。

_ACP2E-4840 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price會在目錄價格範圍=網站時忽略網站範圍的價格

修正GraphQL中網站範圍的套件選項價格：解決當目錄價格範圍設定為網站時，透過GraphQL查詢套件產品選項會傳回全域「所有商店檢視」價格，而非網站範圍的價格。 Magento\BundleGraphQl\Model\Resolver\Links\Collection解析程式現在會正確檢查價格範圍，並根據要求的商店範圍加入網站特定的選取價格。

_ACP2E-5057 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/597c7211)_

#### 由於並行的customerCart GraphQL請求競爭條件，為客戶建立的重複作用中購物車

系統現在會確保每個客戶僅建立一個作用中的購物車，無論請求併發情況為何。 先前，如果同一個已驗證的客戶同時執行兩個customerCart GraphQL查詢或POST /V1/carts/我的REST請求，而沒有作用中的購物車，可能會在資料庫中產生重複的作用中的購物車記錄。

_ACP2E-5077 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8d70f246)_

#### [雲端]已處理記錄到exception.log的QuoteGraphQl中的GraphQlNoSuchEntityException，導致記錄成長無限制

修正預期GraphQlNoThocEntityException錯誤（例如針對過期或無效的購物車ID傳回的錯誤）會寫入var/log/exception.log的問題。 這些已處理的錯誤仍會以一般GraphQL錯誤回應的形式傳回給使用者端，但不再填入例外狀況記錄檔。

_ACP2E-5122 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL、詳細目錄/MSI

#### GraphQL：在ProductStock：：isProductAvailable中作為網站ID傳遞的存放區ID導致「找不到網站」錯誤

先前，由於在需要網站ID的情況下會使用商店ID，因此有些店面在將專案新增至購物車時，檢查產品庫存可用性時，可能會發生「找不到網站」錯誤。 此問題已修正，因此庫存可用性檢查會使用正確的網站內容，以防止錯誤。

_ACP2E-5242 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL，訂購

#### [功能要求]在變更運送公司時，清除商店取貨資料中的多餘專案

從店內取貨方式切換為到家交貨方式時，取貨地點和相關商店地址會從購物車中移除。 訂購前必須提供有效的送貨地址。

_ACP2E-4973 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL，產品

#### 願望清單值資料中缺少索引鍵\&quot;model\&quot;

修正透過GraphQL查詢願望清單詳細資料時傳回內部伺服器錯誤的問題。
願望清單查詢現在會成功傳回，並沒有「願望清單值資料中缺少索引鍵模型」錯誤。

_AC-8062 - [GitHub問題](https://github.com/magento/magento2/issues/36909) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/515d3dd3)_

### 匯入和匯出

#### [問題]修正匯入iframe可見性

為確保Magento Admin面板中的使用者介面整潔光潔，已解決範本配置瑕疵，在資料驗證期間，存放區管理員可看到內部背景執行iframe

_AC-13250 - [GitHub問題](https://github.com/magento/magento2/issues/39267) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39265)_

#### [問題]修正：產品匯入中的硬式編碼xxh128雜湊演演算法

為了清理內部子系統並利用現代系統最佳化基準，產品匯入元件已簡化為使用單一永久雜湊演演算法。

_AC-16967 - [GitHub問題](https://github.com/magento/magento2/issues/40770) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40687)_

#### 當驗證策略設為「發生錯誤時停止」時，發生驗證錯誤後匯入按鈕仍可使用

修正當驗證策略設為「發生錯誤時停止」時，在資料驗證失敗後，匯入按鈕仍顯示在驗證結果中的問題。 以前，即使所有記錄都未通過驗證，按鈕仍出現並可以點選，因此嘗試的匯入立即終止。

_ACP2E-5124 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2b9e8316)_

### 安裝與管理

#### [雲端]更正過時的現有ISO細分代碼

更新13個國家的區域代碼以符合ISO 3166-2標準。 先前，部分地區代碼不符合標準，這可能會造成協力廠商整合和國際法規遵循問題。 比利時、哥倫比亞、西班牙、法國、義大利和拉脫維亞新增地區。 奧地利、哥倫比亞、哥斯大黎加、德國、愛沙尼亞、西班牙、芬蘭、法國、印度、冰島和拉脫維亞的地區代碼已更新。

_ACP2E-4495 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9b6a8bd9)_

### 庫存/MSI

#### [CLOUD]禮卡和相關不可銷售的WF-1688

使用非預設存貨/來源並儲存相關（相關或向上銷售或交叉銷售）產品時，產品不會消失。

_ACP2E-4741 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/30fbdb0f)_

#### 套件組合產品庫存狀態不一致

先前，當店舖管理員從管理員面板手動更新套件組合產品的庫存狀態時，對於設定了多個庫存來源的店舖，該變更未反映在店面上。 儘管管理員有所變更，客戶仍會繼續看見過時的庫存狀態。

此問題已修正。 在「管理員」面板中所做的套裝產品庫存狀態變更，現在可以正確傳播到所有已設定的庫存來源和庫存位置，確保客戶一律可在店面看到準確的庫存可用性。

_ACP2E-4866 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/db712a46)_

#### GetStockIdForCurrentWebsite.php擲回NoSuchEntityException「找不到要求的存放區」

修正使用無效的？store=查詢引數造訪店面頁面，導致每個這類請求在CRITICAL層級記錄NoThocEntityException的問題。 先前，MSI Stock資料外掛程式將原始存放區代碼直接傳遞至StoreManager：：getStore()，而未處理存放區不存在的情況，導致例外狀況記錄混亂。

_ACP2E-5003 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/1bf25e46)_

### 訂購

#### 範圍為前端或webapi_rest範圍時未執行取消訂單觀察器

修正從店面或透過webapi_rest範圍取消訂單未正確執行取消觀察器的問題。 現在訂單取消時，禮品卡金額會還原為客戶的商店貸方。

_AC-16353 - [GitHub問題](https://github.com/magento/magento2/issues/40414) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64eb754d)_

#### 在Admin中編輯現有訂單時，不會套用使用量有限的購物車價格規則（例如「每個客戶的使用量= 1」）

修正在「管理員」中編輯現有訂單時，購物車價格規則折扣與使用限制遭移除的問題。 現在，編輯訂單時，即使達到使用量限制，仍會保留原始折扣。

_AC-16671 - [GitHub問題](https://github.com/magento/magento2/issues/40624) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c10554e1)_

#### 套件產品管理面板中的最小數量驗證錯誤

為了改善後端訂購體驗並在產生手動報價單時移除功能區塊，已解決在建立管理訂單期間子專案引數評估不正確的驗證錯誤。

_AC-17193 - [GitHub問題](https://github.com/magento/magento2/issues/40812) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40863)_

#### 在前端訂單檢視中捆綁產品子專案數量不一致

店面訂單詳細資訊頁面現在會顯示每個搭售產品選項的總訂購數量。 以前，每個子選項的數量欄會顯示父系束的訂購數量，而不是每個選項的總訂購數量。

_ACP2E-4820 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex：：execute()遺失DeadlockException重試造成永久的ShipOrder/InvoiceOrder失敗 — 

ShipOrder與InvoiceOrder作業現在已順利解決，以防發生死結。
先前的ShipOrder與InvoiceOrder作業會因死結而永久失敗

_ACP2E-4913 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/51f6d191)_

#### 在產生商業發票期間，上階可設定專案的FPT/WEEE資料列層次計算不正確

可設定產品之商業發票與銷退折讓單的總計，現在會正確包含「固定產品稅捐」金額。 以前，FPT資料列層次金額不會傳播至上階可設定訂單專案，導致商業發票與銷退折讓單總計低於訂單總計FPT金額。

_ACP2E-4977 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/51f6d191)_

#### 從管理員建立訂單時，在頁面重新整理時修改的產品數量

解決重新整理頁面可能會導致多次新增相同SKU的問題。

_ACP2E-5046 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec436b10)_

#### 同時非同步電子郵件Cron工作者會針對相同訂單傳送重複的訂單確認電子郵件

解決並行電子郵件工作者可能針對相同訂單傳送重複訂單確認電子郵件的問題。

_ACP2E-5059 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8d70f246)_

#### [CLOUD] sales_clean_quotes cron工作記憶體不足

修正在清除大量過期報價時，sales_clean_quotes cron工作的記憶體不足的問題。 以前，作業會保留記憶體中每個已處理的引號，並在移除所有過期的引號之前以嚴重的記憶體耗盡錯誤終止。

_ACP2E-5137 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4d0357d7)_

### 訂購，促銷活動

#### [雲端]新增多張優惠券以重新排序的問題

解決無效優惠券嘗試失敗後，有效優惠券不再套用至訂單的問題。 現在，如果輸入了無效的優惠券，任何先前套用的有效優惠券將維持正確套用。

_ACP2E-4810_

#### 固定金額類別購物車價格規則會在規則符合組合父項時，對不相符的動態組合子項進行折扣

修正當規則僅符合組合父項時，具有類別條件的固定金額購物車價格規則錯誤地將折扣套用至動態價格組合的所有子項的問題。 以前，不屬於目標類別的套件子系會收到按比例分攤的折扣，而非零。

_ACP2E-5075 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2b9e8316)_

### 付款

#### 在較新版本中，config:show命令無法搭配部分路徑使用

`config:show`命令現在接受部分設定路徑，例如付款，並顯示該路徑下的設定值。 以前，執行`php bin/magento config:show`付款傳回錯誤： `The "payment" path doesn't exist. Verify and try again.`，而不是顯示正確的值。

_AC-13908 - [GitHub問題](https://github.com/magento/magento2/issues/39610) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40432)_

### 效能

#### 安裝程式:upgrade正在將索引器模式從`schedule`變更為`save`，大幅減緩其速度

解決了一個長期存在的問題，即執行bin/magento設定:upgrade會不小心將索引器模式從「依排程儲存」變更為「依排程儲存」，並且不必要地捨棄並重新建立資料庫觸發程式，大幅減少停機時間，並防止在大型目錄上進行部署期間出現效能瓶頸。

_AC-2423 - [GitHub問題](https://github.com/magento/magento2/issues/33386) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40643)_

#### Valkey LAYOUT快取鍵會消耗大量空間存放大型產品目錄

之前，每個產品會在每個商店檢視中產生其專屬的LAYOUT快取專案，導致大型目錄的Redis/Valkey中過度消耗記憶體。 現在，LAYOUT快取專案會在具有相同型別、屬性集和存放區檢視的產品之間共用，無論目錄大小為何，都會限制快取成長。

_ACP2E-4908 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### 產品查詢出現死結錯誤

修正具有依類別篩選的CatalogWidget產品清單之頁面上的InnoDB死結問題，此問題發生在排程模式價格索引器同時執行時。

_ACP2E-5052 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] Adobe Commerce URL解析度查詢效能降低

修正GraphQL路由查詢一律轉譯完整CMS頁面內容的問題，包括頁面產生器Widget執行和產品集合載入，即使僅要求URL路由中繼資料(relative_url、redirect_code、type)亦然。 以前，這會對包含頁面產生器Widget的CMS頁面造成不必要的Widget/產品轉譯，以及大幅增加每個請求的資料庫查詢。

_ACP2E-5143 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/597c7211)_

#### 「客戶帳戶共用」設為「全域」時，「管理客戶編輯」效能會降低

修正「管理員客戶編輯」頁面上，當「共用客戶帳戶」設為「全域」時，載入時間和HTTP回應大小呈二次增加時的效能問題。

_ACP2E-5164 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/24667df1)_

### 產品

#### 「價格點選」快顯視窗中的「新增至購物車」按鈕無法運作。

修正產品清單頁面上「點選以取得價格」快顯視窗中的「加入購物車」按鈕未將產品加入購物車的問題。
產品現在可以從快顯視窗成功新增到購物車。

_AC-11896 - [GitHub問題](https://github.com/magento/magento2/issues/30356) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/29a7cdbe)_

#### BundleGraphQL解析器會建立個別的延遲產品執行個體，取消查詢批次處理程式(N+1)

為了大幅加快API回應輸送量並將伺服器開銷降至最低，GraphQL解析層已經過最佳化，以針對套件產品強制執行真正的查詢批次處理程式，進而消除會消耗效能的N+1資料庫漏洞。

_AC-16647 - [GitHub問題](https://github.com/magento/magento2/issues/40595) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40867)_

#### EAV Select與Multiselect屬性驗證錯誤地拒絕值為「0」的選項標籤

為了改善資料完整性並消除客戶和目錄表單間的非預期提交錯誤，已解決驗證瑕疵，其中包含「0」精確字串值的選項標籤遭到EAV核心架構的錯誤拒絕

_AC-16986 - [GitHub問題](https://github.com/magento/magento2/issues/40634) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40827)_

#### 當使用者的角色限制在特定範圍時，無法儲存可自訂選項標籤和可自訂選項標題

修正由存取許可權僅限於特定商店範圍的管理員使用者編輯時，可自訂選項標籤和標題會回覆的問題。
現在已針對選取的範圍正確儲存更新的標籤和標題。

_AC-2684 - [GitHub問題](https://github.com/magento/magento2/issues/35210)_

#### 禮卡價格在願望清單中顯示不正確

修正願望清單中設定之禮卡最低價格顯示為$0.00的問題。
正確的最低禮卡價格現在會顯示在「我的願望清單」頁面和「願望清單」側邊欄Widget上。

_AC-8037_

#### 產品警示消費者忽略商店範圍的系統/stmp/disable

產品警示消費者現在會說明商店範圍的系統/stmp/disable設定。

_ACP2E-4870 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec436b10)_

#### 前端比較頁面顯示不正確的簡短說明標籤翻譯

先前，在比較產品頁面上，可比較的屬性標籤（例如簡短說明）可能會從不同的商店檢視顯示翻譯，而不是目前的商店檢視。 現在，會顯示正確的商店特定翻譯。

_ACP2E-4929 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/08b91f1a)_

#### 頁面產生器產品輪播會忽略類別位置排序順序，而以entity_id DESC順序顯示產品

修正頁面產生器輪播中顯示的產品設定為依類別位置排序時，在店面顯示為錯誤順序的問題。 產品現在會依管理員→目錄→類別→產品索引標籤中設定的順序顯示。

_ACP2E-4980 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/51f6d191)_

### 推進規則

#### 當其中一個套用的購物車價格規則具有「折扣數量步驟」值時，折扣計算錯誤

修正套用多個購物車價格規則時，折扣計算錯誤的問題，且一個規則具有折扣數量步驟（購買X）值。
現在已正確計算所有合格數量的折扣。

_AC-12307 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c10554e1)_

### 促銷活動、目標定位

#### 正在自動移除相關產品

修正當產品屬性變更且停止符合Target規則時，相關產品未移除的問題。 以前，mview索引器無法刪除過時的規則 — 產品關聯，並在重新索引期間發出PHP警告（未定義的陣列索引鍵）。

_ACP2E-4836_

### 傳回

#### RMA — 新增回訪評論API — 會觸發傳送者（銷售代表）而不是客戶收到的電子郵件

修正透過Returns API傳送的回訪評論電子郵件會傳送給銷售代表，而非傳送給客戶的問題。
客戶現在會在透過API新增回訪評論時收到電子郵件通知，並啟用客戶通知。

_AC-1138 - [GitHub問題](https://github.com/magento/magento2/issues/33985)_

### 銷售

#### 從rest api V1/orders或V1/orders/create endpoints下訂單時，`[Order][REST]`個sales_order_items product_options欄遺漏資料

修正透過REST API建立的訂單專案未包含完整product_options資料的問題。 透過REST API建立的訂單，現在可以正確儲存自訂選項標籤和相關選項詳細資訊。

_AC-15187 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8b67e8ed)_

#### 當非同步格線索引因繫結的updated_at時間戳記而啟用時，銷售訂單格線會永久卡在過時狀態

修正啟用非同步網格索引時，銷售訂單網格可能因過時訂單狀態而停滯的問題。 訂單格線狀態現在會正確更新，以符合目前的訂單狀態，包括同一秒內發生多個訂單更新的情況。

_AC-17118 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/478f8e7c)_

### 安全性

#### [問題]更新js.phtml DOM文字重新解譯為HTML

為加強平台的安全性基準線，並將惡意輸入執行的風險降至最低，處理動態DOM更新的主要內嵌指令碼範本已重構為消除跨網站指令碼(XSS)插入向量。

_AC-12118 - [GitHub問題](https://github.com/magento/magento2/issues/38821) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38804)_

### 送貨

#### USPS REST API問題，最大套件重量的比率不正確

修正訂單分割為多個套件時，運費預估不正確（例如，高於「最大套件重量」）。 該電信業者現在會要求每個套件的費率，並依據舊版的「網站工具」流程總計該金額。

_ACP2E-4813 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6c67a9b5)_

### 測試和預覽

#### 排程更新預覽模式中的主控台錯誤

修正兩個更新共用相同開始時間時，測試更新的預覽頁面無法正確載入且JavaScript主控台錯誤的問題。 先前，簽署的預覽URL使用的遞增版本ID不符合預覽JavaScript所衍生的時間戳記，導致簽名不符，並妨礙頁面在預覽模式中正確載入。

_ACP2E-4828_

#### 安裝:upgrade在Magento_CatalogStaging資料修補程式上所花的時間太長，因為儲存檢閱和類別太多

修正CE-to-EE資料移轉修補程式未正確移轉已排程的類別設計更新和產品特殊價格至中繼更新的問題。 由於不正確的測試內容方法，具有已排程設計日期的類別會產生空白的測試更新。 PHP 8.1+在先前移轉執行中有NULL日期時間值時無訊息地略過產品。 也透過僅載入受影響的類別和產品來改善移轉效能，而不是迭代完整目錄。

_ACP2E-5009_

#### 內容暫存控制面板型錄價格規則網格會顯示重複資料

「型錄價格規則」網格現在會正確顯示指定給暫存更新的每個「型錄價格規則」的唯一明細。 先前，將兩個或兩個以上「型錄價格規則」指派給同一個分段更新時，「內容分段控制面板」中該更新頁面上的「型錄價格規則」格線會顯示正確的列數，但每一列都會不正確地顯示相同（最後一個）規則的資料，而非每個規則自己的詳細資料。

_ACP2E-5097_

### 稅金

#### 未針對上階產品設定base_wee_tax_applied_amount

現在會針對資料庫表格（如sales_order_item、sales_invoice_item、sales_creditmemo_item）中的可設定產品植入base_weee_tax_applied_amount值，而不只是針對其子項

_ACP2E-4922 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/08b91f1a)_

### 測試架構

#### [問題]更新GraphQL測試Client.php以進行不區分大小寫的子字串比較

修正當標題使用不同的字母大小寫時，GraphQL API測試無法辨識Set-Cookie標題的問題。 測試現在可以正確處理Set-Cookie、set-Cookie和SET-COOKIE標頭。

_AC-15337 - [GitHub問題](https://github.com/magento/magento2/issues/39713) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c10554e1)_

#### 極慢的WebAPI GraphQL功能測試

為了最佳化建置傳遞設定及加速持續整合(CI)環境，將快取清除行為從外部系統命令呼叫轉換為原生處理序內記憶體處理，已解決測試基礎結構的瓶頸。

_AC-15395 - [GitHub問題](https://github.com/magento/magento2/issues/39725) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40804)_

### UI框架

#### Minicart不能在同一個頁面中使用兩次

為了向前端開發人員提供更大的版面配置彈性，已解決長期存在的核心UI限制，允許多個minicart區塊（例如，一個在頁首和另一個在頁尾）在單一頁面版面配置上獨立存在和更新。

_AC-12579 - [GitHub問題](https://github.com/magento/magento2/issues/38958) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [問題]修正(pagecache)：將PATCH識別為Varnish VCL中的有效HTTP方法

Magento的預設Varnish VCL現在會將PATCH辨識為有效的HTTP方法，因此REST API部分更新請求（例如PATCH /rest/V1/products/:sku）會傳遞至後端而非管道傳輸。 此修正當完整頁面快取設定為Varnish時，PATCH呼叫失敗或行為不正確的問題。

_AC-16954 - [GitHub問題](https://github.com/magento/magento2/issues/40757) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40657)_

#### [問題]取代VCL中的所有gad_*引數

為了消除動態廣告促銷活動造成的效能回歸，應用程式的快取層級已更新，以主動忽略所有Google Ads gad_*查詢字串。 這可防止外部促銷活動連結讓頁面快取失效，並減緩目標頁面的速度

_AC-16980 - [GitHub問題](https://github.com/magento/magento2/issues/40781) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40780)_

#### [問題]修正：將Bootstrap中的PHP版本檢查下限更新為8.3

為了防止混淆執行階段錯誤並改善開發人員安裝疑難排解，系統啟動程式架構內的原生PHP環境驗證器已符合應用程式的實際核心需求。

_AC-17312 - [GitHub問題](https://github.com/magento/magento2/issues/40851) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40686)_

#### 安裝`igbinary`且使用預設檔案快取時，`health_check.php`傳回500 （清漆503）

修正安裝igbinary搭配預設檔案快取後端時，health_check.php傳回HTTP 500的問題。 健康情況檢查現在接受沒有明確後端金鑰的有效快取設定，防止Varnish將後端標示為不健康並傳回HTTP 503。

_AC-17400 - [GitHub問題](https://github.com/magento/magento2/issues/40876) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [問題]修正：更新gzip型別並移除nginx設定中的IE6因應措施

為了改善頁面載入速度並最佳化網路資產傳遞，遞補伺服器設定已進行現代化改造，以更妥善支援現代化店面元件，並移除舊版技術負荷

_AC-17498 - [GitHub問題](https://github.com/magento/magento2/issues/40774) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40681)_

#### [問題]嘗試修正不穩定的graphql OrderStatusChangeDateTest。

為了改善持續整合(CI)可靠性並減少誤判的建置失敗，已在WebAPI功能測試套件中解決競爭條件。 GraphQL訂單狀態驗證測試(OrderStatusChangeDateTest)先前由於PHP記憶體和MySQL時間戳記之間細微的時機差異而發生間歇性失敗

_AC-17959 - [GitHub問題](https://github.com/magento/magento2/issues/41126) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40618)_
