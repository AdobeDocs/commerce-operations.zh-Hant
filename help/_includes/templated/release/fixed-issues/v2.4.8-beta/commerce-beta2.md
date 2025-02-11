---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '9092'
ht-degree: 0%

---
# Adobe Commerce已修正問題(v2.4.8-beta2)

## 已修正v2.4.8-beta2中的問題

我們已修正Adobe Commerce 2.4.8核心程式碼中的206個問題。 此版本中包含的已修正問題子集說明如下。

### API

* _ACP2E-3236_：承載中缺少SKU時，非同步作業失敗
   * _修正附註_：如果承載中缺少sku，則非同步和同步作業先前會因產品儲存錯誤而失敗。 修正後，非同步和同步產品儲存rest api作業會失敗，並顯示相關的例外訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_： [CLOUD]無法使用REST API更新基本價格（「catalog_product_entity_decimal」中的「value_id」值未正確增加。）
   * _修正備註_：先前在此修正中，呼叫rest api /rest/default/V1/products/base-prices時，增量ID錯誤地增加，導致值之間出現間隙。 修正後，增量ID會依預期遞增。 此外， value_id欄位範圍也增加了。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_：產品RestAPI的日期和時間屬性未設定預設值
   * _修正附註_：預設值現在已透過RestAPI正確設定日期、日期及時間屬性
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### API、購物車和結帳

* _ACP2E-3343_：嚴重500錯誤：Magento\Framework\Webapi\Exception與Accept HTTP標頭有關
   * _修正附註_：修正後，指定「接受」標頭沒有問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>

### API， GraphQL

* _ACP2E-3348_：沒有可用於訂閱客戶獎勵點更新的graphQl
   * _修正附註_：先前要修正的問題，無法透過GraphQL突變和Rest API呼叫更新客戶屬性reward_warning_notification。 現在可更新與客戶屬性reward_update_notification相同的專案。

### 帳戶

* _AC-10886_：管理員密碼更新。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38352>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_：當URL大寫時重新導向回圈
   * _修正附註_：系統現在會自動將URL中的大寫字元轉換為小寫，以防止在存取首頁時發生重新導向回圈。 先前，在安全性基底URL中加入大寫字元會在嘗試存取首頁時造成持續的重新導向回圈。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38538>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38539>
* _AC-13000_：以客戶選擇加入身分登入核取方塊無法翻譯
   * _修正附註_：系統現在允許在「商店檢視」範圍中設定「以客戶身分登入」核取方塊和「以客戶身分登入」核取方塊工具提示」欄位，以啟用不同商店檢視的翻譯。 之前，這些欄位僅在「網站」範圍設定，無法翻譯個別商店檢視。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32329>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_：登入後，無法看到以訪客使用者身分新增至比較清單的產品。
   * _修正附註_：登入前已新增至產品比較清單的產品（以客戶身分登入）現在會在登入後保留。
先前，登入後，無法顯示以訪客使用者身分新增至比較清單的產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_：允許國家設定導致客戶地址設定發生問題
   * _修正附註_：現在選取[允許國家/地區]組態不會影響針對指定範圍以外顯示的國家/地區。 先前允許國家/地區組態影響指定範圍以外的客戶地址屬性
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_：共用禮品登入會將事件日期顯示為1天前
   * _修正附註_：店面現在已正確顯示贈品註冊日期

### 帳戶、API、GraphQL

* _ACP2E-3246_：客戶API — 成功登入後，無法重設為0的登入失敗次數
   * _修正附註_：客戶透過API端點成功登入後，客戶實體表格中的失敗編號現在會重設為零。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>

### 帳戶、管理員UI、B2B

* _ACP2E-3038_：受限制的管理員使用者無法一律看到自訂共用目錄
   * _修正附註_：受限制的管理員使用者現在可以一致地檢視及管理客戶及所有指派產品的共用目錄，前提是他們具有特定商店的存取權。 以前，有權存取特定商店的受限制管理員使用者無法總是看到指派了產品的所有共用目錄，或看到無法儲存的客戶，導致系統中的不一致。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>

### 帳戶、購物車及結帳

* _AC-2341_：「select」自訂客戶地址屬性未針對新客戶地址呈現
   * _GitHub問題_： <https://github.com/magento/magento2/issues/34950>

### 管理員UI

* _AC-10705_： [問題]針對「重新載入資料」資料按鈕新增許可權檢查
   * _修正附註_：系統現在包含「重新載入資料」按鈕的許可權檢查，確保只有具有適當許可權的使用者才能顯示和存取該按鈕。 以往，所有使用者都可以看見並點按「重新載入資料」按鈕，而在沒有必要許可權的使用者點按時，會導致「不允許」頁面。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38283>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38279>
* _AC-13131_： [問題]修正警告：未定義的陣列機碼「篩選器」
   * _修正附註_：系統現在會處理新使用者尚未與書籤互動的情況，防止記錄未定義的陣列索引鍵「篩選器」警告。 以前，當新使用者未與書籤互動時，系統會記錄此警告。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39013>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38996>
* _AC-13529_：因為Validate.php檔案中的程式碼變更，導致含有特殊字元的產品匯入csv檔案失敗
   * _修正備註_：系統現在可以正確驗證及匯入包含特殊字元的產品CSV檔案，允許成功傳輸資料。 先前，嘗試匯入包含特殊字元的產品CSV檔案會導致錯誤，阻礙匯入程式。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_：當「密碼重設要求數目上限」設定大於0時，例如： 3 ，「超過限制錯誤訊息會在重新達到限制之前傳送，即從第二次開始
* _AC-13768_：雖然「密碼重設要求數目上限」已設為0 （已停用） ，但「從第2次傳送超過限制的錯誤訊息」
* _AC-7962_：在行動電話檢視中結帳付款時，沒有運送連結
   * _修正附註_：系統現在可確保結帳標題/連結「送貨」和「檢閱與付款」一律顯示在行動檢視的頁面頂端，讓使用者能夠輕鬆地在步驟之間導覽，並進行必要的更正。 先前，這些標題/連結隱藏在行動檢視中，讓使用者難以瞭解他們目前的步驟或回到先前的步驟。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36856>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36982>
* _AC-8109_：客戶訂單查詢出貨註解created_at傳回時區為+0，不在商店設定的時區內
   * _修正附註_：使用客戶「訂單」查詢時，系統現在會正確顯示客戶設定時區中出貨註解的「created_at」欄位。 以前，「created_at」欄位會顯示在+0時區，無論客戶的時區設定為何。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36947>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_：送貨地址狀態不是自動更新
   * _修正備註_：修正前，送貨地址區域（或區域識別碼）與地址帳單資訊不同步。 現在，帳單地址資訊變更時，送貨地址區域和區域ID都會正確更新。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_：重設按鈕在新增/編輯管理員使用者上無法運作
   * _修正附註_：之前，在[新增/編輯管理員使用者]頁面上，[重設]按鈕無法運作。 現在，在「系統 — >許可權 — >所有使用者」下的「管理員」面板中，「新增/編輯管理員使用者」頁面上的「重設」按鈕將正確運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_：「購物車允許的最大數量」的驗證中斷
   * _修正附註_：先前我們將`Maximum Qty Allowed in Shopping Cart`置為空白時，雖然這裡不接受空白值，但是它並未擲回任何例外狀況。 此修正套用後，輸入空字串將會擲回例外狀況，而且不允許儲存產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_： [Pagebuilder預覽UI問題]頁面產生器欄中的按鈕未正確對齊
   * _修正附註_： 「頁面產生器」欄中的按鈕現在已正確對齊。 之前，這些量度在頁面產生器欄中不會對齊。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_：訂購的產品報告未匯出。 404錯誤。
   * _修正附註_：產品訂購報表匯出為CSV和XML，現在可如預期運作
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_：以生產模式啟用Js縮制後，主控台中出現TinyMCE JS錯誤
   * _修正附註_：之前，在管理面板中以生產模式啟用JavaScript縮制，導致瀏覽器主控台中出現與TinyMCE 7相關的JavaScript錯誤，影響功能和使用者體驗。 現在，此問題已解決，確保TinyMCE 7順利運作，不會產生任何錯誤，即使JS縮制已啟用。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_：要求其他變更以完全完成ACP2E-3375修正
   * _修正備註_： &#39;-
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>

### 管理員UI、付款/付款方法、訂單

* _AC-13520_： PayPal智慧型按鈕順序後，交易授權未顯示在[交易]索引標籤中
   * _修正附註_：使用PayPal智慧型按鈕下訂單後，系統現在會在「交易」標籤中正確顯示交易授權。 以前，在按一下「授權」按鈕後，授權交易未出現在Transaction標籤中，並且未建立「授權」型別的新交易。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>

### 管理UI、測試與預覽

* _ACP2E-3424_： [Cloud]移除遺失影像的範本導致pub/media被刪除
   * _修正附註_：在此修正之前，如果pagebuilder範本缺少預覽影像名稱，則會刪除pub/media資料夾。 修正後，只會刪除範本和預覽影像（如果找到）。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/報表

* _AC-9922_： Google Analytics CSP錯誤https://region1.analytics.google.com
   * _修正附註_：啟用Google Analytics時，系統現在可正確連線至&#39;https://region1.analytics.google.com&#39;&#39;，避免內容安全性原則(CSP)錯誤。 之前，若啟用Google Analytics並從歐盟檢視網站，會因為拒絕連線至「https://region1.analytics.google.com&#39;」而導致CSP主控台錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37750>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3146_： GTM針對具有自訂選項的可設定產品，在dataLayer中遺失addToCart事件
   * _修正附註_：先前並未針對可設定的產品觸發addToCart事件。 現在，事件已正確新增至GTM dataLayer變數。
* _ACP2E-3183_： NewRelic瀏覽器監視內嵌JS指令碼導致CSP錯誤
   * _修正附註_：應用程式現在會插入NewRelic瀏覽器監視指令碼，而非APM代理程式，以符合CSP （內容安全性原則）。 先前，APM代理程式插入的NewRelic瀏覽器監視指令碼與CSP不相容，並導致無法執行指令碼。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_：對sales_bestsellers_aggregated_daily資料表的INSERT查詢在銷售訂單數量很大的專案上變得緩慢
   * _修正附註_：以前，若訂購大量訂單，需花費大量時間才能產生最暢銷商品每日彙總報表。 現在會及時產生報表。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_：顯示錯誤貨幣符號的訂單報告
   * _修正備註_：訂單報表中訂單金額的貨幣符號不正確取自currency/options/base。 現在已更正為使用貨幣/選項/預設值，以便提供準確的報告。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_： [雲端]優惠券使用量報表中的計算不正確
   * _修正備註_：折價券報表格線中的銷售總計，現在會合併「折扣稅捐補償金額」與「送貨折扣稅捐補償金額」來精確計算。 以前，計算中缺少這些金額，導致銷售總額與銷售訂單資料之間出現差異。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_：共用的「&lt;project_id>/var/tmp」發生問題
   * _修正附註_： Analytics DataExport暫存檔將使用sys tmp目錄，更適合經常存取和變更。 為了避免同一伺服器上執行多個執行個體時發生衝突，臨時路徑已更新為使用執行個體的唯一ID
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/報表、雲端

* _ACP2E-3187_： NR中的量度可能對背景交易產生誤導 — ACP2E-3067的後續追蹤
   * _修正附註_：背景交易(cron)將使用組態設定中定義的New Relic應用程式名稱
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_： 2.4.8-beta102 Package Enterprise Edition因應用程式例外而失敗
* _AC-13816_：首次無法在後端管理中啟用b2b功能
* _ACP2E-2139_：執行部分索引時，指派給共用目錄的產品未反映在前端
   * _修正附註_：部分索引完成後，透過REST API指派給共用目錄的產品現在會立即顯示在店面上。 過去，產品只有在完全重新建立索引後才會顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_： sales_clean_quotes cron會從尚未核准的採購單刪除報價
   * _修正備註_： sales_clean_quotes cron工作不會刪除採購單中使用的報價
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_：下單按鈕在採購單詳細資料中消失
   * _修正備註_：修正當產品變數在卡片中指定了最小數目時，已核准採購單的「下訂單」按鈕隱藏的問題
* _ACP2E-3474_： [CLOUD]沒有識別碼= 0且具有b2b模組的此類實體
   * _修正附註_：啟用共用目錄功能時，登入的使用者可以將產品加入購物車。
先前將產品新增到購物車會導致「沒有ID = 0的這類實體」錯誤

### B2B、購物車和結帳

* _AC-13817_：啟用b2b所有功能時，無法在購物車上看到產品

### B2B、GraphQL

* _ACP2E-3391_： [雲端]透過graphql呼叫建立公司時無法設定custom_attributes
   * _修正附註_：修正後，可以使用graphql要求建立公司期間，為公司管理員設定「custom_attributes」屬性。

### 組合

* _AC-10826_：店面組合核取方塊驗證錯誤訊息計數超過1
   * _修正附註_：現在系統只顯示一則驗證錯誤訊息，當按一下[加入購物車]按鈕，而未選取套裝產品的任何核取方塊選項時。 以前，系統會為每個未選取的核取方塊顯示多個驗證錯誤訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_：在某些與順序相關的測試案例中擲回Magento例外狀況
   * _修正附註_：系統現在可正確處理各種測試案例中的「sendGuestPaymentInformation」步驟，避免擲回Magento例外狀況。 以前，這些例外是由於空值付款方法所造成，這會導致多個測試案例中的失敗。

### 購物車與結帳

* _AC-11914_： [問題]銷售規則CartFixed計算：折扣金額不正確
   * _修正備註_：系統現在會正確計算具有購物車固定金額之銷售規則的折扣金額，以確保不論購物車專案是否變更，都能套用正確的折扣。 以前，當購物車專案變更時，折扣金額可能會錯誤地變化，有時會導致比預期大得多的折扣。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38694>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_：條款與條件核取方塊不允許店面上的HTML
   * _修正附註_：系統現在支援店面之「條款與條件」核取方塊文字中的HTML格式，可加強自訂與可讀性。 以前，核取方塊文字會以純文字格式顯示，忽略使用的任何HTML標籤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_：為登入使用者建立的購物車價格規則未正確地套用於未登入使用者
   * _修正附註_：系統現在會在登入使用者因Cookie過期而自動登出時，正確移除購物車價格規則，確保折扣不會套用至非登入使用者。 先前，即使使用者已登出，仍會套用購物車價格規則，導致將錯誤的折扣套用至未登入的使用者。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38944>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_： [問題] [功能]效能最佳化大型購物車，防止……
   * _修正附註_：系統現在會防止重複的getActions呼叫，提升購物車操作的速度和效率，以最佳化大型購物車的效能。 之前，如果購物車有多個專案，系統會多次呼叫getActions函式，因而降低系統效能。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39292>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39290>
* _AC-13797_：禮品登入連結無法正常運作
* _ACP2E-3176_： [雲端]快速訂購大量SKU效能
   * _修正附註_：當購物車價格規則條件中使用的屬性未針對所有產品出現，且啟用MAP （最低廣告價格）功能時，結帳效能已改善。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_：購物車中有重複的專案
   * _修正附註_：系統現在可正確處理多個平行請求，以將相同產品加入購物車至單一條列專案，防止為相同的SKU建立個別條列專案。 以前，並行請求將相同產品新增到店面的購物車會導致同一SKU出現多個條列專案。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_：已將結帳訂單電子郵件確認傳送給以名字/姓氏輸入的電子郵件
   * _修正附註_：不再傳送結帳單電子郵件確認函，此確認函先前是在[名字]和[姓氏]欄位中輸入類似電子郵件的模式時傳送。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_：結帳送貨地址表單更新為錯誤的地址
   * _修正附註_： shippingAddressFromData現在已儲存至每個網站的本機儲存空間。 以前，如果在URL中使用商店代碼，且在同一個訪客工作階段中從多個網站起始結帳，則結帳時可能會將錯誤網站的位址自動填入送貨地址表單中。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_：啟用地址搜尋時，[雲端]簽出未保留選取的帳單地址
   * _修正附註_：啟用地址搜尋時，結帳付款頁面現在會保留選取的帳單地址。 先前，如果「客戶地址數限制」設定為1，而客戶有多個地址，則在重新載入頁面後，所選的帳單地址會消失。
* _ACP2E-3407_：禮卡產品 | 購物車合併正在合併禮品卡
   * _修正附註_： Giftcard產品現已正確合併到購物車中
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_：現有報價資料未更新/不可見，而是在trigger_recollect = 1時建立新的報價記錄
   * _修正附註_：客戶的購物車專案在加入購物車後，不會再因產品被刪除而消失。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 目錄

* _AC-11970_：無法透過選取自訂選項的核取方塊來重新排序可設定的產品
   * _修正附註_：系統現在會使用單一選取的核取方塊自訂選項，正確處理可設定產品的重新排序，以便成功建立購物籃。 之前，嘗試重新排序這類產品會導致錯誤，且無法將專案新增至購物車。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38736>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_：遺失下拉式清單選項
   * _修正附註_：現在當建立具有20個以上值的新屬性時，系統會在下拉式清單中正確顯示所有值。 以前，只顯示前20個值或其他選定的頁面值，導致剩餘的值遺失。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_： [問題]將目前的儲存區ID用於類別執行階段快取
   * _修正附註_：系統現在會正確使用類別執行階段快取目前的存放區ID，以防止使用模擬或自訂程式碼將類別儲存在不同存放區時覆寫資料。 先前，儲存在執行階段的物件可能來自錯誤的存放區，導致資料覆寫。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39310>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36394>
* _AC-13324_： bin/magento sampledata：deploy —no-update擲回例外狀況
   * _修正附註_：系統現在在使用sampledata：deploy命令中的 — no-update選項時，可以正確接受布林值，以防止在範例資料部署期間發生任何錯誤。 以前，使用此命令時會擲回錯誤，因為系統錯誤地預期了整數值。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39344>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39345>
* _AC-13355_： [問題]修正EAV快取型別的使用方式
   * _修正備註_：系統現在在所有相關位置正確使用EAV快取型別，確保資料快取的一致性和效率。 先前的EAV快取型別使用方式不一致，導致資料快取作業可能缺乏效率且不一致。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32322>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/31264>
* _AC-13596_：包含空白資料的目錄進階搜尋移至搜尋結果頁面[2.4.dev分支]
   * _修正備註_：系統現在會在[進階搜尋]頁面上正確保留使用者，並在使用者嘗試執行搜尋時顯示錯誤訊息，而不輸入任何資料。 以前，執行空白搜尋會將使用者重新導向至「目錄進階搜尋」頁面，並出現一則訊息，提示使用者修改其搜尋。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13786_：停用自訂主題的product_image_white_borders後，沒有移除白色邊框
* _ACP2E-3103_：由於快取，新產品RSS摘要未更新為新產品
   * _修正附註_：當產品設定為新產品且已儲存時，「新產品」的Rss摘要現在會更新
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_： [雲端]實際行動裝置上的雙指縮放和移動問題
   * _修正附註_：系統現在可確保行動裝置上的影像縮放功能一致，提供順暢且可預測的使用者體驗。 以前，影像縮放功能不一致，且在行動裝置上檢視特定時間點後會突然縮小。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_：從共用目錄取消指派產品時，不會清除願望清單產品
   * _修正附註_：現在，如果共用目錄中沒有產品，則願望清單中不會顯示任何專案。 先前，即使願望清單中實際上沒有專案，願望清單頁面也會錯誤地顯示「1專案」的計數。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_：相關產品選取全部/取消選取所有問題
   * _修正附註_：之前，如果手動選取產品，相關產品的「全選」/「取消全選」按鈕無法正常運作。 修正後，這些按鈕現在即使手動選取也運作一致，確保所有產品皆已正確選取或取消選取。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_： [雲端]庫存警示電子郵件翻譯成錯誤的語言
   * _修正附註_：針對使用不同語言的多個商店檢視的網站，傳送庫存/價格警示時，建立警示的商店檢視語言將會用於電子郵件。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>，<https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_：已停用的類別在類別樹狀結構中的名稱不再為灰色
   * _修正附註_：之前，已停用的類別在類別樹狀結構中不會呈現灰色。 現在，它們會以灰顯效果顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_：可設定的產品編輯表單載入導致逾時和記憶體耗盡
   * _Fix備註_：在Fix可設定的產品變數之前，是根據所有可能的屬性選項組合所建構。 如果屬性有許多選項，這將導致冗長且耗用的資源作業。 現在，可設定的產品變數是根據現有的子產品屬性來建構。 如此可大幅減少計算，進而改善資源的使用狀況。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_：使用色票時Fotorama未正確載入視訊，並已透過URL預先選取選項
   * _修正附註_：如果URL包含選取的選項，產品影片現在會在可設定的產品詳細資料頁面上正確轉譯。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_： PageBuilder Carousel Widget顯示不符合條件的產品
   * _修正附註_： Widget中使用的產品清單現在遵循類別條件
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_：當群組中所有產品的數量無效時，就會觸發驗證錯誤
   * _修正附註_：現在，當一個產品具有無效數量（先前未發生）時，群組中的所有產品都會正確觸發驗證錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_：如果處理程式終止，索引子暫存資料表將不會清除
   * _修正附註_：如果索引器處理序已終止，現在會清除CatalogRule索引器暫存資料表
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_： [QUANS] 2.4.7-p3中的核心單元測試失敗
   * _修正附註_：此測試不需要發行說明，因為這是單元測試改進。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 目錄，內容

* _ACP2E-3063_： [雲端]快取未失效。
   * _修正附註_：以更新的設計配置儲存CMS頁面時，該頁面先前未正確反映於前端。 套用此修正後，當我們變更設計版面並儲存CMS頁面時，前端會看到合適的設計版面。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_： [雲端]錨點/非錨點類別在內容Widget中反轉
   * _修正附註_：先前我們選取「顯示於 — >錨點類別」時，會顯示所有未反映錨點與非錨點之間父子關係的類別。 套用此修正後，「顯示於 — >錨點類別」只會顯示「錨點類別」（可選取），而「顯示於 — >非錨點類別」則會顯示「非錨點類別」（可選取）
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_：無法使用Widget的類別
   * _修正附註_：之前，如果我們為不同的錨點/非錨點類別儲存CMS區塊，則無法在前端顯示時用於子類別。 套用此修正後，區塊會顯示在不同類別的前端。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d01ee51e>

### 目錄， GraphQL

* _ACP2E-3312_：GraphQL產品中的層級價格傳回錯誤的值（相較於Storefront）
   * _修正備註_：修正之後，針對graphql要求傳回的產品層級價格會有一個專案的價格。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_： [雲端] B2B：透過GraphQL的類別問題
   * _修正附註_：修正之後，即使根類別沒有允許許可權，類別graphql查詢也會傳回具有允許許可權的類別。

### 目錄，搜尋

* _ACP2E-3345_：建立物件時發生型別錯誤： Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor例外狀況
   * _修正備註_：修正之後，可以建立Magento\CatalogSearch\Model\Indexer\Fulltext類別的執行個體，而不需指定$data。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_：在Magento Admin中儲存後，前端看不到產品的[雲端]問題
   * _Fix備註_：在修復可設定的產品之後，擁有長名稱子產品的店面將不會遺失。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 目錄，送貨

* _ACP2E-3195_：訂購禮品登入專案時送貨地址是空的
   * _修正附註_：之前，針對訪客使用者禮品登入專案，從電子郵件功能傳回時，會產生空白的位址，此位址不適用於下訂單。 套用此修正後，禮品登入會檢查已登入的使用者/訪客使用者以及指定的地址（如果存在）。

### 內容

* _AC-12692_： Widget類別樹狀結構未正確呈現
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39008>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_：變更設計設定頁面中的主題時，無法看到「使用預設值」訊息
   * _修正附註_：系統現在包含單獨的欄，以根據設計設定頁面中選取的主題顯示「使用預設值」訊息。 這可確保預設值狀態的清晰度和可見度。 以前，不會顯示「使用預設值」訊息，導致對所選主題狀態的混淆。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_： [問題]再次還原與TinyMCE外掛程式的回溯相容性(之後……
   * _修正附註_：系統現在恢復與TinyMCE外掛程式的回溯相容性，以便從其他位置使用介面工具時，可以呼叫外掛程式中定義的函式。 先前，由於TinyMCE版本有所變更，外掛程式不會將Widget傳回為物件，導致嘗試在Widget例項上呼叫某些函式時發生錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39262>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_： [雲端]上傳影像按鈕無法運作
   * _修正附註_：在PageBuilder中橫幅和滑桿的「上傳影像」按鈕未如預期運作，現在按一下按鈕時會開啟本機檔案管理員，以選取要上傳的影像。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_： [Cloud] - CMS滑桿未反映最新變更
   * _修正附註_：確保在編輯投影片熒幕上觸發儲存事件時，重新整理滑桿清單，已修正問題。 在過去，這會觸發並造成問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_：使用頁面產生器依特定順序插入CMS區塊時，CSM頁面中會發生錯誤
   * _修正附註_：先前在某些版本的PHP和OS (Linux)上，透過PageBuilder參考其他cms區塊的區塊轉譯會失敗並出現「發生未知錯誤」。 請再試一次。」 現在，Cms區塊的內容會在PageBuilder控制的內容中正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_： [雲端]動態區塊將無法正常運作
   * _修正附註_：登出後現在會清除登入的客戶區段，以防止來賓工作階段繼承先前登入的區段
* _ACP2E-3430_：TinyMCE 7遺失字型大小的最新安全性更新
   * _修正附註_： WYSIWYG編輯器中現在提供字型大小和字型系列選取器。 在此修正之前，使用TinyMCE 7時，這些無法在編輯器介面中使用。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>，<https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### 客戶/

* _AC-13060_：客戶區段>條件>產品歷史記錄* > 「已檢視產品」無法運作
   * _修正附註_：系統現在會在符合條件時，在「客戶區段」底下的「已檢視產品」條件下，正確顯示相符的註冊客戶。 過去，即使符合條件，符合的註冊客戶數仍維持為零。
* _AC-8499_：國家/地區下拉式清單變更時，區域文字欄位未重設
   * _修正附註_：系統現在會在下拉式選單中的國家/地區變更時重設區域文字欄位，確保先前的值不會持續存在。 之前，從下拉式清單變更國家/地區時不會重設地區欄位，導致保留最後儲存的值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_：刪除客戶並不會清除已登入及已刪除之客戶在店面上的所有瀏覽器工作階段資料
   * _修正附註_：刪除客戶現在會依預期清理店面登入和刪除之客戶的所有瀏覽器工作階段資料。 購物者可以繼續購物，他們的瀏覽器會將他們的工作階段視為訪客工作階段。 先前，當登入購物者的客戶帳戶從管理員中刪除時，購物者的瀏覽器會擲回JavaScript錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7d5e3906>

### 框架

* _AC-10738_：清漆設定未排除所有行銷引數
   * _修正附註_：系統現在已正確排除Varnish設定中的所有常見行銷引數，確保追蹤和分析準確。 之前，某些行銷引數（例如gad_source、srsltid和msclkid）未排除，導致資料收集可能不準確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38298>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39188>
* _AC-11592_： [問題]安裝期間只允許有效的偏好設定:di:編譯
   * _修正附註_：如果偏好設定是針對不存在的類別建立或明確排除的類別，系統現在會在安裝:di:編譯命令期間擲回錯誤，確保只允許有效的偏好設定。 以前，這些案例會無訊息地失敗，可能會使任何與原始類別關聯的外掛程式變成無用。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38517>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/33161>
* _AC-11809_： [問題]透過XML傳遞自訂屬性至目前的連結
   * _修正附註_：系統現在允許透過XML將自訂屬性傳遞至目前的連結，確保即使連結為目前頁面也能正確顯示這些屬性。 以前，由於getAttributesHtml()方法未用於目前連結，因此不會顯示目前頁面連結的自訂屬性。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38500>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/30070>
* _AC-12127_： [問題]避免設定錯誤的無限回圈
   * _修正備註_：系統現在避免虛擬型別組態中的自我參考對應，以避免無限回圈。 這可確保應用程式在嘗試取消參考自我參考節點時，不會陷入無休止的回圈中。 先前，如果虛擬型別設定是自我參照，則會導致應用程式無限期迴轉。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38822>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38794>
* _AC-12299_：物件管理員未用於Magento\Csp\Model\Mode\Data\ModeConfigured
   * _修正附註_：系統現在會在建立ModeConfigured物件時正確使用物件管理員，允許在此物件上使用外掛程式。 先前並未使用Object Manager，因此無法將外掛程式套用至ModeConfigured物件。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38875>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38886>
* _AC-12540_：產品庫存和價格警示中的檔案區塊註解不準確
   * _修正附註_：產品庫存和價格警示中deleteCustomer方法的doc區塊註解已更正，以正確反映該方法會刪除與指定客戶及網站（而非網站上的客戶）相關的所有庫存產品或價格警示。 以前，評論錯誤地指出方法用於從網站中刪除客戶。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38939>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39001>
* _AC-12857_： PHP 8.2.15已移除FTP副檔名
   * _修正附註_：系統現在將FTP擴充功能加入為composer.json檔案中的相依性，以確保透過FTP成功設定CSV匯入。 先前，由於PHP套件中缺少FTP副檔名，嘗試透過FTP設定CSV匯入時擲回錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39083>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_：可定義dev:di:info CLI命令的區域
   * _修正附註_：系統現在可讓開發人員定義dev:di:info CLI命令的區域，加強開發和偵錯程式。 以前，這個指令只能顯示GLOBAL區域的資訊。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38758>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38759>
* _AC-13247_：由於字元集和定序變更，MariaDB 11.4版的setup：upgrade失敗
* _AC-13279_： [問題]移除所有行銷get引數以將快取最小化
   * _修正附註_：系統現在會移除所有行銷取得引數，以最佳化快取使用率，映象使用Varnish時所使用的邏輯。 以前，這些引數可能會導致快取膨脹和效能降低。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39266>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39099>
* _AC-13345_： [問題] [PHPDOC]修正錯誤的phpdoc Magento\Directory\Model\AllowedCountries：：getAllowedCountries()
   * _修正附註_：已修正AllowedCountries：：getAllowedCountries()方法的PHPDoc，以提供精確資訊，提高檔案的清晰度和實用性。 以前，此方法的PHPDoc包含不正確的資訊，這可能會導致混淆或誤用方法。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39246>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39241>
* _AC-13348_： [問題]移除我們不再支援的PHP版本的部分程式碼。
   * _修正附註_：移除Magento不再支援之PHP版本的程式碼
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39361>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39202>
* _AC-13417_： [問題]使ImageMagick介面卡與php8相容（從浮點數到int的隱含轉換）
   * _修正附註_：系統現在藉由在計算影像尺寸時正確處理浮點數，確保與PHP8的相容性，避免因浮點數到int的隱含轉換而發生任何錯誤。 先前，影像尺寸的計算可能會產生浮點數，而隱含四捨五入時會造成錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39402>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37362>
* _AC-13537_： [問題] [PHPDOC]修正錯誤的phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _修正附註_：此更新會修正Magento\Framework\App\Config\ScopeConfigInterface中的PHPDoc註解，以正確反映getValue和isSetFlag方法的$scopeCode引數型別。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39492>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39199>
* _AC-8662_： [問題]改善cron錯誤記錄
   * _修正附註_：系統現在會擷取並記錄cron程式的STDERR和STDOUT，在cron程式失敗的情況下提供有價值的診斷資訊。 以前，cron處理程式內的任何錯誤訊息都不會被記錄，而且在不同處理程式中執行的cron群組的STDERR和STDOUT會遺失。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37453>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_：當有外來索引鍵時，無法透過db_schema.xml修改資料行長度
   * _修正附註_：透過宣告式結構描述修改含外部索引鍵的資料行現在不會在MariaDB中產生錯誤
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_：儲存訂單記錄時，會將部分關係記錄儲存至DB
   * _修正附註_：觸發不必要的修正之前UPDATE查詢可能會影響效能。 修正後，多餘的UPDATE查詢已消除。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_： [CLOUD]在管理員中，主控台中有許多javascript錯誤
   * _修正附註_：之前，在管理面板中，主控台有許多Javascript錯誤。 現在，在管理面板中，主控台中沒有JavaScript錯誤，所有預設JavaScript功能將順利執行且不會出現任何問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_： [雲端] Magento：佇列訊息已刪除
   * _修正附註_：佇列訊息現在已正確清除。 修正之前，假設正在使用SQL佇列系統，如果清除佇列訊息同時執行，則可能會刪除新訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>

### 框架， UI框架

* _ACP2E-3324_：即使設定值已鎖定，仍可覆寫設定值
   * _修正附註_：在此修正之前，無法透過bin/magento config：set命令設定設計組態，而且可以透過操作顯示它們的表單來變更鎖定的值。 修正後，從cli使用 — lock-env或 — lock-conf設定的鎖定值無法再更新。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_：客戶傳回屬性的轉譯未反映在個別StoreView的GraphQL API中
   * _修正附註_：客戶回訪屬性的轉譯會反映在個別StoreView的GraphQL API中。
先前個別StoreView的客戶傳回屬性不會反映在GraphQL API中。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_： [雲端]使用者在多網站設定中的驗證和跨網站權杖存取問題
   * _修正附註_：多網站設定中的GraphQl客戶資訊和購物車查詢會檢查非預設網站上的客戶是否存在。
先前的查詢可在不確認客戶存在於多網站設定的非預設網站的情況下運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_：取得customerCart時應指定[GRAPHQL]模型值
   * _修正附註_： GraphQL &#39;customerCart&#39;查詢現在可以建立空的購物車，即使報價在資料庫中無法使用。 之前，此作業在建立空白購物車時因為國家/地區驗證問題而失敗。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_： [GraphQl]可透過GraphQl看到但不顯示在店面上的願望清單專案
   * _修正附註_：透過GraphQL提出要求時，未正確列出願望清單產品。 現在，願望清單產品會根據提供的商店內容進行篩選。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_： [GraphQL]重設內容與主旨/連結之間的密碼電子郵件不一致
   * _修正附註_：在傳送密碼重設要求時，不論網站為何，藉由模擬客戶帳戶註冊的正確存放區，此問題已解決。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_： [Cloud]產品GraphQL查詢傳回未指派給目前網站的相關產品
   * _修正附註_：先前針對graphQL查詢，多商店相關產品無法正確針對產品查詢顯示。 套用此修正後，對於產品，graphQL會查詢多存放區相關產品並相應地顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_：在GraphQL標頭中使用錯誤的存放區識別碼會造成嚴重的記憶體錯誤
   * _修正附註_：在GraphQL要求中傳送錯誤的存放區代碼不會再導致記憶體耗用過多。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_： [Cloud] 2.4.7上對空白Graphql回應的500回應
   * _修正附註_：修正後，無效的graphql要求將不會記錄到exception.log檔案中。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _LYNX-600_：將預設GraphQL查詢的最大複雜度增加到1000

### GraphQL，搜尋

* _ACP2E-948_：產品清單GraphQL查詢僅限於total_count 10,000個產品
   * _修正備註_：修正後，搜尋結果不限於10000個產品，即使計數超過10000，仍可取得符合搜尋條件的所有產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL，測試架構

* _ACP2E-3363_： Magento\GraphQl\App\GraphQlCustomerMutationsTest.php整合測試失敗
   * _修正備註_： &#39;-
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### 匯入/匯出

* _ACP2E-3172_：缺少匯入按鈕
   * _修正附註_：解決CSV中有正確和不正確記錄的資料檢查後，匯入按鈕遺失的問題。 先前，透過CSV中的正確和不正確記錄檢查資料後，匯入按鈕不顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_：無法匯入匯出的客戶地址
   * _修正附註_：客戶地址匯入將如預期般進行。 先前，如果共用客戶帳戶=全域，則客戶地址匯入檔案不會通過驗證，而且有兩個網站的預設網站具有受限制國家/地區清單，而正在匯入的地址是用於另一個網站的允許國家/地區不同
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_： [雲端] CSV檔案中的錯誤數量未產生錯誤
   * _修正附註_：現在庫存來源匯入將會擲回數量欄中非數值的驗證錯誤。 先前，在數量欄中匯入非數值的庫存來源會導致數量設為0。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_：產品匯出導致OOM，即使有4G記憶體限制
   * _修正附註_：在此修正之前，如果產品屬性具有數千個選項值（即使有4G可用記憶體），產品匯出會失敗。 此項修正後，產品匯出應會完成csv檔案的匯出。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 匯入/匯出，效能

* _ACP2E-3476_： [雲端]產品匯入時間已大幅增加
   * _修正備註_：在修正之前，包含超過10,000個專案的目錄產品匯入發生顯著的時間降級。 修正後，會及時執行目錄產品的匯入。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/87d012e5>

### 安裝與管理

* _AC-13242_： Magento升級在MariaDB 11.4 + 2.4.8-beta1上失敗
   * _修正備註_：升級應該會發生，且沒有任何錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7b336d0a>

### 庫存/MSI

* _ACP2E-3335_：啟用MSI取貨商店時無法送出訂單
   * _修正附註_：改善存貨效能，可建立出貨並備有許多店內取貨的來源
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_： Cron重新索引無法在前端更新產品可用性
   * _修正附註_：之前，透過REST API更新延期交貨狀態後，產品在前端沒有庫存。 現在，透過REST API更新延交訂單狀態後，產品會以庫存顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_：啟用MSI時，將影像新增至可設定的功能無法運作。
   * _修正附註_：使用詳細目錄模組時，可設定產品的影像上傳現在會如預期般運作。 先前無法上傳影像
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/fdf409aa>

### 庫存/MSI、搜尋

* _ACP2E-3413_：當SKU未設為可搜尋的屬性時，所有產品都會使用[is_out_of_stock] = 1編制索引
   * _修正備註_：修正後，目錄搜尋索引中的「is_out_of_stock」是正確的，即使sku無法搜尋。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/5b21b7af>

### 訂購

* _ACP2E-3311_： [Cloud]若未設定預設帳單地址，則無法在單一商店的admin中建立訂單
   * _修正附註_：現在相關的錯誤訊息「具有相同電子郵件地址的客戶已存在於關聯的網站中。」 如果客戶沒有預設帳單地址，但嘗試在其他商店建立訂單，則會顯示訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_：已傳送管理員重複下單要求
   * _修正附註_：之前，在管理面板中的「提交訂單」按鈕可能會被多次點按，或是透過重複按下「Enter」鍵來啟動，導致重複提交或提交訂單有錯誤。 現在，會防止其他動作，直到完全處理完訂單為止，確保只提交一個訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_：即使沒有付款方式，管理員還是可以下訂單
   * _修正備註_：當付款方式重新出現在可用付款清單中時，現在會保留先前選取的付款方式。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>

### 訂單，付款

* _ACP2E-3233_：即使沒有付款方式，管理員還是可以下訂單
   * _修正附註_：以前，商家可以從管理員面板下訂單，而無需選取付款方式。 現在，商家需要一種付款方式才能繼續下訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/fd5cf3af>

### 其他

* _LYNX-426_：未針對具有動態價格的套件組合產品計算discount_percentage
* _LYNX-485_：當其中一個套件產品無存貨時，套件產品仍會顯示「IN_STOCK」
* _LYNX-486_： not_available_message和only_x_left_in_stock未顯示相同的可用庫存
* _LYNX-488_： original_row_total欄位傳回錯誤值
* _LYNX-503_：應根據組態顯示群組的產品縮圖     .
* _LYNX-510_：在OrderAddress中查詢selected_options時發生錯誤
* _LYNX-512_：原始專案價格不含折扣
* _LYNX-530_：沒有可用的訊息未顯示可用的存貨數量
* _LYNX-532_：「Simple with custom options products with multi select options」會傳回「OUT_OF_STOCK」狀態
* _LYNX-533_：錯誤(GQL)： cart.itemsV2.items.product.custom_attributesV2傳回伺服器錯誤
* _LYNX-536_：訂單/date_of_first_order一律傳回null
* _LYNX-544_：客戶不能取消部份出貨的訂單
* _LYNX-548_：根據錯誤訊息取消訂單的錯誤碼
* _LYNX-581_：將Cookie相關屬性從私人移回受保護的

### 其他開發人員工具

* _AC-12731_：與dev/css/use_css_critical_path結合的CSP問題
   * _修正附註_：系統現在會在結帳頁面上以非同步方式正確載入CSS檔案，即使啟用&#39;dev/css/use_css_critical_path&#39;設定亦然，以確保這些頁面以正確的CSS樣式呈現。 以前，受限的內容安全性原則(CSP)會導致內嵌JavaScript無法執行，導致CSS檔案無法如預期載入。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39020>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39040>
* _AC-13398_：使用虛擬型別來設定外掛程式，無法在安裝程式:di:編譯命令中正確產生攔截器方法
   * _修正附註_：系統現在會在使用虛擬型別設定外掛程式時正確產生攔截器方法，確保不論是預先編譯還是執行階段編譯的結果都一致。 以前，與執行階段編譯相比，系統會在預先編譯時產生不正確的結果。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/33980>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_：無法從資料收集器下載檔案
   * _修正附註_：下載備份不再顯示空白頁面而非下載檔案。

### 付款

* _ACP2E-3143_： PayPal訂單退款導致重複銷退折讓單
   * _修正備註_：修正PayPal付款服務IPN建立的銷退折讓單並行處理的問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_：購物車價格規則不適用於Paypal
   * _修正備註_：以付款方式套用折扣時，PayPal端會顯示正確的金額
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_： [雲端]具有特定角色的使用者無法登入
   * _修正附註_：具有僅包含PayPal區段存取權之角色的管理員使用者現在可以登入而不會發生錯誤
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>

### 效能

* _AC-11932_：預設產品屬性設定問題
   * _修正附註_：系統現在允許使用者取消選取產品屬性的預設選項，確保屬性並非總是有預設集。 先前，一旦設定了產品屬性的預設值，就無法取消選取該屬性，導致屬性一律會有預設集。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38703>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_：支援Magento CLI中的Symfony CommandLoaderInterface
   * _修正附註_：此變更允許延遲初始化命令，以縮短Magento CLI應用程式的初始化時間，直到需要命令時為止。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/29266>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/29355>

### 產品

* _AC-13173_： [問題]修正PHPDoc區塊中的錯字
   * _修正附註_：系統現在會正確移除$helper變數宣告在PHPDoc中未知的參考變數，以提高程式碼清晰度和準確性。 先前，PHPDoc中這個未知的參考變數會造成程式碼中的混淆和潛在的不準確性。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38961>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38940>
* _AC-13423_： [問題]修正Magento >= 2.4.7中損壞的套件組合和可下載的產品頁面配置
   * _修正附註_：已修正套件組合及可下載產品頁面的配置，確保所有裝置顯示一致且正確。 先前，由於產品資訊媒體區塊重新排列，這些頁面會遇到版面問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39403>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3471_：類別中的[雲端]產品 — 新增產品 — 指派 — 全部選取
   * _修正附註_：使用者現在可以使用切換功能來選取或取消選取產品。

### 促銷活動

* _ACP2E-3139_：具有折扣數量步驟（購買X）屬性的銷售規則導致不套用其他規則
   * _修正附註_：如果購物車中的產品數量不足以套用規則，購物車價格規則不會取消先前套用的規則。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_：購物車價格規則上的效能問題 — 進階銷售規則模組
   * _修正附註_：已新增AdvancedSalesRule篩選器中遺漏的DB索引
* _ACP2E-3332_：以固定金額折扣和「套用數量折扣上限」發行銷售規則
   * _修正備註_：修正購物車規則折扣的問題，當購物車設定為對有限數量的產品套用固定金額折扣時。 先前，「套用折扣數量上限」值是用來計算購物車中目前專案的價格，而非僅用於計算規則的折扣。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_： [雲端] Magento升級導致抵用券區分大小寫
   * _修正備註_：修正前，您必須輸入與優惠券設定完全相同的代碼，並考量大寫或小寫。 現在，無論程式碼設定是大寫還是小寫，都將在後端驗證抵用券。
* _ACP2E-3349_：購物車規則「整個購物車的固定金額折扣」  動作套用折扣不正確
   * _修正備註_：從管理區域建立訂單時，無論大寫或小寫為何，都將正確驗證優惠券代碼。 之前，如果優惠券代碼與設定購物車規則代碼的字母大小寫不符，系統不會驗證優惠券代碼。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_：在後端，預設產品屬性的存放區值（而不是預期的管理員值）
   * _修正附註_：現在在後端，會使用管理員值，而非產品屬性的預設商店值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_：新增套件組合產品時，購物車規則「整個購物車的固定金額折扣」動作套用折扣不正確
   * _修正附註_：未正確套用套件組合產品的固定數量購物車規則。 現在，在計算總折扣金額時，會考慮捆綁子產品，從而產生適當的折扣計算。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_：購物車價格規則計算折扣錯誤
   * _修正備註_：正在正確計算固定金額折扣。 修正前，套件組合產品的固定金額折扣總計不正確。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_：規則條件中的巢狀類別未顯示
   * _修正附註_：修正層級3類別的巢狀類別未顯示在類別條件的行銷規則中的問題
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_： usage_limit和uses_per_customer未在salesrule_coupon資料表中更新
   * _修正備註_：更新購物車價格規則中每個優惠券的使用次數和每個客戶的使用次數，現在會影響現有的自動產生優惠券。 以前，新值只影響新抵用券
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_：購物車價格規則使用「等於或大於」條件時，不會將父類別列入考量。
   * _修正備註_：當在進階狀況中使用父類別時，購物車價格規則現在會正確考慮父類別
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_：優先順序的折扣計算無效
   * _修正備註_：在套用整個購物車折扣型別的固定金額的情況下，先前促銷已折扣的購物車專案無法正確計算金額。 現在，折扣總和已相當恰當。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3498_：同時套用多個購物車價格規則與折扣/特價產品時，折扣值不正確
   * _修正備註_：修正前，如果套用多個購物車規則，則整個購物車規則的固定金額未正確套用。 現在，已正確套用固定金額折扣購物車規則。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 傳回

* _ACP2E-3330_： [雲端]受限制的管理員使用者可以看到傳回功能表和按鈕
   * _修正附註_：受限制的管理員使用者現在無法存取RMA相關控制項（功能表和按鈕）。
先前受限制的管理員使用者可以看到傳回功能表和按鈕。
* _ACP2E-3443_：重新整理熒幕時傳回熒幕發生問題
   * _修正附註_：使用者可以重新整理頁面，而不發生熒幕扭曲的情況。

### 銷售

* _AC-13750_：總計與基本總計與測試結果步驟不相符
* _AC-13751_：如果已套用第一個購物車規則，則未套用第二個購物車價格規則

### 搜尋

* _AC-13053_：正在取得「輸入搜尋字詞，然後再試一次」。 2.4.8-beta1店面進階搜尋頁面上的錯誤
   * _修正附註_：產品屬性設為「否」時，系統現在會在「進階搜尋」頁面上正確顯示搜尋結果。 以前，將產品屬性設定為「否」並執行搜尋會導致錯誤訊息，「請輸入搜尋詞並再試一次。」
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_： magento/module-open-search依存於不存在的opensearch-php分支
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_： search_query資料表若為巨型，對載入時間前端有重大影響
   * _修正附註_：已改善搜尋清單頁面載入時間。 修正前，搜尋清單頁面因未最佳化的查詢而延遲。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/55615e61>

### 安全性

* _ACP2E-3273_： ReCaptcha V2在德文語言簽出時顯示不正確
   * _修正附註_：先前來自結帳電子郵件地址下方的recaptcha對於長字如德文的語言顯示為無樣式。 之後，recaptcha看起來會像其他區域的所有recaptcha元素一樣。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_：管理員登入的驗證碼不需要與某些使用者互動
   * _修正附註_：已如預期驗證管理員登入的ReCaptcha

### 送貨

* _AC-12938_： UPS REST devdoc中的「沙箱」和「prod」安裝指示更新
* _ACP2E-3340_： FedEx追蹤API無法搭配REST認證使用
   * _修正附註_：先前的FedEx整合不需要額外的API金鑰來追蹤API。 現已新增新設定，以支援追蹤API金鑰。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_： [雲端] FedEx交涉費率未傳回REST
   * _修正備註_：在修正之前，FedEx帳戶的特定費率未在回應時傳送，即使根據FedEx檔案他們本應傳送也一樣。 修正後，帳戶特定費率會透過變更我們這邊的請求在回應中傳送。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/55615e61>

### 測試和預覽

* _ACP2E-3453_：使用唯一自訂類別屬性時無法更新排定的更新
   * _修正附註_：修正如果類別具有唯一屬性，則無法更新類別排程更新的問題
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>

### 稅金

* _ACP2E-3193_：固定產品稅(FPT)無法使用可設定的產品
   * _修正附註_：可設定產品變數正常運作的FPT。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>

### 測試架構

* _AC-13362_： [問題] PHPDoc更正拼字
   * _修正附註_：系統現在可正確辨識IDE中已棄用的方法，因為PHPDoc有拼字校正。 之前，PHPDoc中的拼字錯誤會導致IDE無法辨識某些已棄用的方法。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/31399>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/31398>
* _AC-13478_： MAGETWO-95118：在工作階段過期後，檢查永久購物車的行為
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_：整合測試失敗Magento\NegotiableQuote\Controller\Quote\DownloadTest：：testCompanyManagerDownloadWithNQSubPermission
* _ACP2E-3458_： [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _修正附註_：修正mftfs
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>

### UI框架

* _AC-12432_： Ui元件檔案欄位
   * _修正附註_：系統現在可正確驗證UI元件表單中的檔案欄位，以便在選取檔案時提交表單而不會發生錯誤。 以前，即使選擇了檔案，驗證也會失敗，阻止表單提交。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38908>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39004>
* _AC-12645_： [問題] js主控台中的日期格式已改良：從12小時切換至24小時……
   * _修正附註_：改進js主控台中的日期格式：從12小時切換為24小時
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38983>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38972>
* _AC-12650_： [問題]在開發人員模式中為較少的檔案新增sourceMap產生
   * _修正附註_：系統現在會在開發人員模式中產生較少檔案的來源對應，更易於識別樣式的來源。 以前，在較少伺服器端編譯的開發人員模式下執行系統時，要識別樣式的來源非常困難。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38982>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38977>
* _AC-13459_：「無庫存」排序有最小庫存臨界值的不一致行為
   * _修正備註_：系統現在會根據存貨層次正確排序目錄中的產品，遵循設定的「最小存貨臨界值」，並一致地將無存貨專案移至清單底部。 先前，排序行為不一致，專案根據其庫存量並非總是以正確順序出現，而且在儲存、重新整理或修改類別階層後，排序的變更可能無法預測地發生。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_：針對require.js載入問題，建議改善錯誤報告功能
   * _修正附註_：此PR可改善必要專案無法載入元件時的錯誤訊息。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36761>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38971>
* _AC-9168_： [問題]移除不必要的指令碼檢閱摘要
   * _修正附註_：系統現在會從評等區段中移除不必要的JavaScript指令碼，而使用內嵌CSS樣式以獲得更有效率、更可讀的程式碼，藉此最佳化頁面載入時間。 以往，針對評分割槽段使用JavaScript指令碼可能會導致頁面載入時間變慢。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37776>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_：網站標題 | 破壞客戶歡迎區段的特殊字元
   * _修正備註_：修正後，特殊字元在客戶歡迎區段中會正確顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
