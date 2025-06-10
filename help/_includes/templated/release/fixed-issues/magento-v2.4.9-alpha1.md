---
source-git-commit: 6c7feee0cd23d397c40bb66593a79b59ac2f620a
workflow-type: tm+mt
source-wordcount: '2806'
ht-degree: 0%

---
# Magento Open Source發行說明(v2.4.9-alpha1)

## 已修正v2.4.9-alpha1中的問題

我們已修正Magento Open Source 2.4.9-alpha1核心程式碼中的67個問題。 此版本中包含的已修正問題子集說明如下。

### API

* __非同步大量作業仍處於async.magento.configurableproduct.api.optionrepositoryinterface.save.post的開啟狀態__
如果要求內文不是Array，大量API端點現在會擲回錯誤，因此需要大量專案索引鍵是從0開始的連續數字。 以前，由於批次請求中提交的任意專案鍵，未更新批次專案狀態。
  _ACP2E-3544 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_
* is_subscribed值上的&#x200B;__[雲端] API REST錯誤未從使用searchCriteria__的目前存放區考慮
API REST客戶查詢使用searchCriteria從正確的存放區擷取正確的「is_subscripted」值
先前，API REST客戶查詢在擷取is_subscribed&quot;值時不會考慮儲存。
  _ACP2E-3621 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_
* __async.operations.all可以為1個SKU建立多個專案__
儲存和更新相同產品的同時請求現在會序列化，以防止可能導致資料不一致或重複產品的競爭條件
  _ACP2E-3744 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

### 帳戶

* 在客戶帳戶建立期間，__[雲端]刪除操作因目前的區域錯誤而遭禁止__
修正儲存地址無效的客戶後，會傳回描述無效原因的訊息，而非無關的「目前區域禁止刪除操作」。
  _ACP2E-3791 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6ea61121)_

### 管理員UI

* __[問題]改善角色樹狀結構的使用者體驗__
此提取請求會新增按鈕，以收合全部、展開全部和展開具有選定專案的分支。 此功能類似於類別樹狀結構（「目錄 — >詳細目錄 — >類別」）中提供的功能
  _AC-14020 - [GitHub問題](https://github.com/magento/magento2/issues/39654) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36511)_
* __Symfony\Component\Mime\Exception\LogicException： 「Sender」標頭必須是「Symfony\Component\Mime\Header\MailboxHeader」的執行個體(取得「Symfony\Component\Mime\Header\MailboxListHeader」)__
  _AC-14520 - [GitHub問題](https://github.com/magento/magento2/issues/39823) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1e14bd72)_
* __提供使用格線大量刪除稅率的功能__
管理員使用者現在可以同時從「管理員稅率」網格中刪除多個稅率。  [GitHub-33399](https://github.com/magento/magento2/issues/33399)
  _AC-2238 - [GitHub問題](https://github.com/magento/magento2/issues/33399) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33484) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5cd64dd0)_
* __條件SKU的購物車價格規則不會考慮SKU中的「前導零」(sku： 01234與1234相同)__
系統現在會正確處理購物車價格規則，且條件SKU會考慮SKU中的「前導零」
  _AC-9428 - [GitHub問題](https://github.com/magento/magento2/issues/37919) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39525)_
* __多選__的預設屬性選項值行為問題
在修正預設值之前，多個選項屬性的預設值未正確儲存。 現在，修正之後，值會正確儲存在資料庫中。
  _ACP2E-3523 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_
* __將產品數量從管理員移回購物車時出現問題__
從管理員建立訂單時，側邊欄上客戶購物車中的產品新增到訂單時不會消失。
  _ACP2E-3563 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8ba4ab1)_

### 管理員UI、B2B

* __B2B以客戶標題登入仍具有Magento品牌__
較早的店面標題顯示「您現在在&lt;商店名稱>上以&lt;客戶名稱>連線」與Magento品牌。 此問題現已修正，且標題會顯示為ADOBE品牌。
  _AC-14361 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fadcfa8b)_

### 管理UI，內容

* __在影像插入期間發生「無法建立媒體資產路徑的轉譯」例外狀況__
移除「媒體集影像最佳化」設定的「最大寬度」和「最大高度」值時，影像最佳化程式期間不會再發生錯誤。
  _ACP2E-3781 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

### 管理員UI、安全性

* __弱密碼管理__
使用相同密碼時無法儲存管理員使用者。 之前，檔案會成功儲存，未經適當驗證。
  _ACP2E-3657 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

### 購物車與結帳

* __Magento 2.4.7更新（迷你）購物車不允許十進位數量__
現在，當我們從迷你購物車更新數量且地區設定為NL （荷蘭文）時，Magento可正確處理數量
  _AC-13238 - [GitHub問題](https://github.com/magento/magento2/issues/39236) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39669)_
* __[問題]更新subtotal.phtml__
系統會以正確的間距更新subtotal.phtml
  _AC-13907 - [GitHub問題](https://github.com/magento/magento2/issues/39619) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39612)_
* __無法向訪客下訂單__
  _AC-14241 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/27217d0e)_
* __已過期的永久性報價未由cron工作sales_clean_quotes清除__
&#39;persistent_clear_expired&#39; cron工作執行時，現在會清除過期的永久性引號。 在過去，過期的永久性引號不會由任何其他cron工作清除。
  _ACP2E-3493 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/11be3dff)_
* 為非作用中公司簽出&#x200B;__「發生錯誤」錯誤__
修正前，如果登入的使用者公司不再啟用，購物車頁面上的登出動作就無法正常完成。 現在，如果該公司不再可用，則會正確執行登出。
  _ACP2E-3541 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_
* 我們「使用多個地址簽出」時，__地址選擇未儲存__
在取消多重送貨選項時進行修正之前，當回覆為多重送貨時，不會預先選取地址。 現在，預設位址會取代為多送貨畫面中選取的其中一個位址。
  _ACP2E-3646 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6ea61121)_

### 購物車與結帳、送貨

* __[Mainline]購物車價格規則未遵守多重出貨__
在此修正實施之前，若套用子選取條件並啟用免運費，多送貨產品的購物車價格規則無法正確套用。 不過，由於已套用校正，多批出貨購物車的購物車價格規則現在會如預期運作。
  _ACP2E-3666 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

### 目錄

* __相同查詢的相同頁面有重複的快取fpc__
系統現在會正確識別並使用相同的完整頁面快取(FPC)來處理具有相同查詢引數的頁面，無論其順序或尾隨字元為何。 這可防止頁面快取資料夾大小不必要的增加。 以前，如果查詢引數的順序不同或如果存在尾隨字元，系統會為同一頁建立不同的FPC識別碼，從而導致頁快取資料夾大小增加。
  _AC-10722 - [GitHub問題](https://github.com/magento/magento2/issues/38269) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38270)_
* __缺少catalog_product_entity_int資料表中必要資料行的索引__
已新增catalog_product_entity_int表格中缺少之必要欄的索引
  _AC-10844 - [GitHub問題](https://github.com/magento/magento2/issues/38315) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38316)_
* __產品頁面因url重寫而發生錯誤__
現在，當我們進行URL重寫時，產品頁面就能成功載入
  _AC-2950 - [GitHub問題](https://github.com/magento/magento2/issues/35371) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39670)_
* __indexer_update_all_views cron錯誤與MAGE_INDEXER_THREADS_COUNT__
已修正MAGE_INDEXER_THREADS_COUNT > 2搭配客戶區段索引器的問題
  _ACP2E-3538 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_
* 在頁面產生器產品Widget條件&#x200B;__中新增「條件組合」時發生__例外狀況
已新增檢查以跳過缺少或不完整的條件，藉此修正問題。 以前，由於處理系統中的不完整條件，這會導致產生錯誤記錄。
  _ACP2E-3545 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/11be3dff)_
* __載入屬性集時瀏覽器當機__
如果產品屬性超過4千個，則瀏覽器不會再在屬性集編輯頁面上當機
  _ACP2E-3633 - [GitHub問題](https://github.com/magento/magento2/issues/38810) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_
* __[雲端]產品URL重寫未針對新存放區建立：上線封鎖程式__
已成功建立新商店的產品URL重新寫入。
先前作業因記憶體洩漏或逾時而結束。
  _ACP2E-3669 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_
* __選項無法運作的屬性預設值__
先前，當我們變更產品選取屬性的預設值時，它會顯示為具有先前值的陣列元素。 套用此修正後，當我們更新產品屬性值時，它將會儲存為eav_attribute表格中的單一元素。
  _ACP2E-3688 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

### 目錄、GraphQL、搜尋

* __產品graphql在類別彙總中傳回停用的類別__
修復後，產品GraphQl請求不會傳回已停用的類別。
  _ACP2E-2885 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

### 目錄、產品

* __[隨機錯誤]未載入Fotorama程式庫__
現在，系統可確保Fotorama程式庫已正確載入，讓所有附加的影像如預期般顯示在影像庫中。 之前，由於Fotorama資料庫未正確載入的問題，因此只會顯示第一個影像。
  _AC-12124 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/27217d0e)_

### 內容

* __將csp_whitelist.xml放在主題中無法運作，會產生間歇性問題__
已實施每個網站區域的CSP白名單快取。
  _AC-13069 - [GitHub問題](https://github.com/magento/magento2/issues/38933) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39672)_
* __錯誤：產品載入時，管理員內容pagebuilder的「Magento_Catalog/js/validate-product」出現指令碼錯誤__
此PR修正使用產品條件編輯pagebuilder時catalogAddToCart的指令碼錯誤
  _AC-13891 - [GitHub問題](https://github.com/magento/magento2/issues/39604) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39677)_
* __封鎖具有相同識別碼的Widget中的選取專案__
當我們有相同的識別碼區塊時，系統現在會在建立Widget時正確處理選取區塊
  _AC-14132 - [GitHub問題](https://github.com/magento/magento2/issues/39692) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39722)_
* __資料表首碼未列入考量__
  _AC-14556 - [GitHub問題](https://github.com/magento/magento2/issues/39847) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bc2d6d0)_
* __無法上傳寬度相對較小的影像__
系統不再無法以相對較小的寬度調整影像大小。
  _ACP2E-3558 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_
* __遠端儲存路徑樣式設定的設定路徑不正確__
修正後，設定遠端儲存路徑樣式設定將影響實際的AWS S3路徑樣式設定。
  _ACP2E-3734 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

### 框架

* __正在編譯已停用模組的程式碼。__
此提取請求會在程式碼編譯之前逸出已停用的模組。
  _AC-10933 - [GitHub問題](https://github.com/magento/magento2/issues/38241) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39723)_
* __Magento_Theme title.phtml範本對PHP 8.2__無效
此提取請求修正了使用null標題建立的CMS頁面(如Php 8.x將null傳遞至trim()時擲回例外狀況：已棄用功能： trim()：將null傳遞至字串型別的引數#1 ($string))的問題
  _AC-12856 - [GitHub問題](https://github.com/magento/magento2/issues/39092) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39398)_
* __當鎖定提供者使用檔案存放區時，我們會取得不斷成長的檔案目錄，而且不會進行任何清除__
此提取請求會引入每天執行一次的新cron作業，並搜尋過去24小時內未修改且可安全移除的鎖定檔案。 這會控制鎖定檔案目錄的內容。
只有當鎖定提供者設定為使用檔案時，此cron工作才會執行某些動作，而不是當使用其他檔案時（資料庫 — 預設、縮放管理員或快取）
  _AC-13367 - [GitHub問題](https://github.com/magento/magento2/issues/39369) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39372)_
* __[問題]清理：請勿使用方法呼叫的void傳回值。__
此PR會進行微幅清理。 有時我們呼叫未傳回任何內容(void)的方法，然後使用該結果值。 這確實不是必要。
  _AC-13664 - [GitHub問題](https://github.com/magento/magento2/issues/39524) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39516)_
* __[問題] [PHPDOC]修正Magento\Framework\Message\ManagerInterface__的錯誤phpdoc
此PR修正\Magento\Framework\Message\ManagerInterface的錯誤phpdoc，並移除\Magento\Framework\Message\Manager中所有重複的phpdoc （使用inheritdoc語法）。
  _AC-14312 - [GitHub問題](https://github.com/magento/magento2/issues/39593) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39153)_
* __已移除composer.json的beta最低穩定性__
移除composer.json的Beta版最低穩定性
  _AC-14450 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1cbbf187)_
* __allow_parallel_generation應透過環境變數__設定
修正後，「MAGENTO_DC_CACHE_ALLOW__PARALLEL_GENERATION」環境變數可用來設定「allow_parallel_generation」設定。
  _ACP2E-3673 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_
* __[Cloud]在Magento 2中使用db_schema.xml檔案將資料表資料行型別從Int變更為Decimal導致錯誤__
變更欄資料型別無法正常運作。 之前，它會擲回錯誤：不允許屬性「identity」。
  _ACP2E-3709 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_
* 在Adobe中支援&#x200B;__新貨幣(XCG)__
加勒比盾(XCG)已新增至貨幣清單。
  _ACP2E-3790 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

* __訂單位置的GraphQL回應不包含例外狀況訊息__
還原先前以不同格式傳回錯誤的變更。 現在系統會以一致的方式傳回潛在錯誤，而不會破壞GraphQL結構描述。 這應新增為已知的BIC，由ACP2E-3399中的PM核准
  _ACP2E-3399 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_
* __訂購位置的GraphQL回應已部分本地化__
placeOrder GraphQl突變傳回的錯誤未完全本地化。 現在，在多語言內容中，錯誤會正確翻譯。
  _ACP2E-3506 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_
* __同時呼叫以重新排序GraphQL API — 將相同的產品新增到不同的列__
修正同時呼叫重新排序GraphQL API導致相同產品新增為不同列，進而導致資料不一致的問題。
  _ACP2E-3774 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8ba4ab1)_
* __updateCustomerEmail GraphQL突變（變更電子郵件地址）未觸發電子郵件通知__
以往，成功更新客戶帳戶上的電子郵件地址後，系統不會傳送電子郵件給客戶。 套用修正後，客戶現在會在成功更新電子郵件地址後收到電子郵件通知。
  _ACP2E-3785 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8ba4ab1)_
* __動態屬性未透過updateGiftRegistry變異在贈品登入中更新__
之前，在透過updateGiftRegistry變異進行此修正之前，贈品登入的自訂屬性並未透過GraphQL變異進行修改或更新。 套用此修正後，可以透過updateGiftRegistry變異成功更新贈品登入的動態屬性。
  _ACP2E-3805 - [GitHub問題](https://mcstaging.briscoes.co.nz/)_

### 匯入/匯出

* __[問題] Copyedit：將「coping」變更為「coping」__
PR修正「複製」的次要拼字錯誤
  _AC-13300 - [GitHub問題](https://github.com/magento/magento2/issues/39311) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39307)_
* __REST端點產品匯入Json未驗證必要欄位__
透過匯入程式（管理員或API）建立新產品時，現在需要名稱欄位。 修正前，您可以建立沒有名稱的新產品，這會破壞管理員介面，並建立無效產品。
  _ACP2E-3660 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_
* __匯出程式中遺失網站篩選選項__
現在可在建立產品匯出時依網站篩選產品。
  _ACP2E-3720 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_
* __AC-13913重複 — 靜態屬性非同步清除。__
修正後，建立\Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType的許多執行個體時，不會出現「未定義的陣列索引鍵&quot;apply_to&quot; （套用至）」錯誤。
  _ACP2E-3752 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

### 庫存/MSI

* __結帳時變更地址時，__商店取貨未遵守搜尋半徑上限
現在，如果送貨地址變更，「店內撿料」中預先選取的商店將會更新。 以往，預先選取商店後，即使新送貨地址不在所選商店半徑內，也不會變更
  _ACP2E-3728 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/07620383)_

### 訂購

* __無法針對不可為空的欄位\&amp;amp；quot；AppliedCoupon.code\&amp;amp；quot；未預期的問題__傳回null
  _AC-14484 - [GitHub問題](https://github.com/magento/magento2/issues/39841) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/97b2ea42)_

### 訂單，定價

* __管理員在建立傳回時顯示不正確的貨幣符號__
在使用不同貨幣(EUR/USD/GBP)進行多網站設定時，admin中的退貨產品選擇頁面現在顯示正確的貨幣符號。 之前，它會顯示預設貨幣符號。
  _ACP2E-3658 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

### 其他開發人員工具

* __燈塔協助工具失敗__
系統現在通過測試，無障礙分數為100
  _AC-12783 - [GitHub問題](https://github.com/magento/magento2/issues/39054) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39164)_
* __停用captcha storefront設定仍載入captcha js檔案__
停用店面的驗證碼時，系統現在不會載入驗證碼js檔案
  _AC-14267 - [GitHub問題](https://github.com/magento/magento2/issues/32987) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39154)_

### 付款

* __[問題]修正離線發票擷取(404)__
它會修正從Magento管理員擷取離線付款方法發票時的404頁錯誤
  _AC-13336 - [GitHub問題](https://github.com/magento/magento2/issues/39298) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39297)_

### 產品

* __產品集合 — 當集合可能載入或將載入時，addMediaGalleryData呼叫getSize （可以使用count以避免額外的DB查詢）__
如果在呼叫產品圖形ql時已載入產品集合，且其中包含media_gallery欄位，此PR會減少使用count()的額外查詢呼叫。
  _AC-13055 - [GitHub問題](https://github.com/magento/magento2/issues/39111) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39681)_
* __[2.4.8]找不到cron工作catalog_product_alert__的回呼
  _AC-14494 - [GitHub問題](https://github.com/magento/magento2/issues/39800) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bc2d6d0)_
* __當產品Widget透過pagebuilder包含時執行緩慢查詢__
針對產品Widget建立（包括產品SKU）的查詢已最佳化。
  _ACP2E-3449 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_
* __產品影像新增為可設定產品時未調整大小__
以前，在管理面板中透過「設定」新增的影像未遵守上傳大小上限，這可能會導致不一致和管理挑戰。 現在，已實作修正，以確保在上傳期間自動調整影像大小，以符合大小上限，精簡程式和維護系統標準。
  _ACP2E-3504 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

### 送貨

* __[DHL] — 處理一般大小設定中的選用維度，以及REST與XML API整合之間的價格差異__
  _AC-14601 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1e3bde4c)_
* __建立UPS送貨標籤時發生例外狀況__
修正警告：在UPS出貨標籤建立期間陣列到字串的轉換
  _ACP2E-3676 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

### 測試和預覽

* __預覽排定的更新會依字母順序開啟第一個商店檢視，而非感興趣的商店檢視__
在修正之前，排程更新的預覽會依字母順序在第一個存放區檢視中開啟，而不是依指派的存放區檢視。
修正後，預覽現在會在指派給CMS區塊測試更新的存放區檢視中正確開啟。
  _ACP2E-3671 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_
