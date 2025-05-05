---
source-git-commit: 53b2494d848c027e32f1493bbc7a9f204677afaa
workflow-type: tm+mt
source-wordcount: '27958'
ht-degree: 0%

---
# Adobe Commerce已修正問題(v2.4.8)

## 已修正v2.4.8中的問題

我們已修正Adobe Commerce 2.4.8核心程式碼中的582個問題。 此版本中包含的已修正問題子集說明如下。

### API

* 當parent_txn_id = txn_id __時，__/V1/交易REST API傳回錯誤
系統現在會正確處理父交易ID與交易ID相同的父項和子項概念交易，防止在查詢/V1/transactions REST API端點時發生無限回圈。 以前，此情況會導致嚴重錯誤，因為超過最大執行時間。
  _AC-10042 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bafc571)_
* 2.4.7 __中的__[ Graphql]型別問題
系統現在會在執行GraphQL查詢時正確處理GetCustomSelectedOptionAttributes函式中的整數值，防止任何與型別相關的錯誤。 之前，啟動使用具有整數引數的GetCustomSelectedOptionAttributes的GraphQL查詢會導致型別錯誤。
  _AC-11878 - [GitHub問題](https://github.com/magento/magento2/issues/38662) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38663)_
* __類別url_key中的特殊字元（透過REST API建立時）__
舊版在category_url_key中，修正後特殊字元不在category_url_key中顯示特殊字元
  _AC-3223 - [GitHub問題](https://github.com/magento/magento2/issues/35577) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c699c206)_
* __REST API顯示來自其他網站的訂單。 __
系統現在支援REST API管理員權杖和Magento_Sales端點的範圍授權存取，確保REST API僅顯示管理員有權存取的訂單。 以前，無論管理員使用者指派的網站為何，REST API都會顯示所有網站的訂單。
  _ACP2E-2703_
* 啟用2FA Duo後出現rest api __問題__
含Duo安全性選項的2FA現在會為Rest API產生正確的簽章
  _ACP2E-2755 - [GitHub程式碼貢獻](https://github.com/magento/security-package/commit/412fa642)_
* __[REST API]：為可設定的產品新增設定後，在存放區檢視中使用預設值時不會維持檢查狀態__
已透過確保非預設存放區之可自訂選項的正確資料庫專案來修正此問題。 由於資料庫專案不正確，即使自訂商店的選項標題與預設商店相同，「管理員>目錄>產品編輯>可自訂選項」區段中自訂商店的核取方塊先前未勾選。
  _ACP2E-2927 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3056e9cb)_
* 使用Oauth1 __時，__REST API無法在SKU中以斜線(/)提出要求
在修正之前，您無法對SKU中具有「/」的產品發出成功的API呼叫。 現在，即使其SKU中有正斜線，您仍可以發出成功的API取得產品詳細資料的要求。
  _ACP2E-2969 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b21e5d91)_
* 如果啟用[validateDefaultAddress]，透過REST API更新時，__客戶地址更新失敗__
API裝載中缺少ID金鑰的問題解決後，API端點現在會如預期運作。
  _ACP2E-3079 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9af794a4)_
* __[雲端]正在階層價格Api中建立重複的網站群組價格客戶群組。__
現在，Tier Price Rest Api不允許建立「重複」網站群組價格客戶群組。
之前，您可以在層級價格Api中建立重複網站群組價格客戶群組，以免在產品儲存期間透過管理員驗證。
  _ACP2E-3091 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/148c3ead)_
* __無法透過REST API新增具有狀態的訂單註解__
若問題僅來自目前狀態，則允許變更訂單狀態，此問題已解決。 之前，它不會遵循訂單狀態並防止任何訂單狀態中的變更，即使它來自相同狀態亦然。
  _ACP2E-3130 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/93d50f8d)_
* 承載&#x200B;__中缺少SKU時，__非同步作業失敗
如果承載中缺少sku，則非同步和同步作業先前會失敗，因為產品儲存錯誤。 修正後，非同步和同步產品儲存rest api作業會失敗，並顯示相關的例外訊息。
  _ACP2E-3236 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/66dea0de)_
* __[CLOUD]無法使用REST API更新基本價格（「catalog_product_entity_decimal」中「value_id」的值未正確增加。）__
在此修正之前，呼叫rest api /rest/default/V1/products/base-prices時，增量id會錯誤地增加，導致值之間出現間隙。 修正後，增量ID會依預期遞增。 此外， value_id欄位範圍也增加了。
  _ACP2E-3376 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d50f6b5d)_
* __在API POST V1/order/：orderId/refall的銷退折讓單電子郵件中看不到訂單專案__
以前，在此修正之前，當客戶從通知send_email的API請求建立銷退折讓單時，它不包含產品詳細資料格線。 此修正套用後，客戶傳送銷退折讓單API請求，並會找到出現在電子郵件中的產品專案詳細資料。
  _ACP2E-3460 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3f12d152)_
* __未設定產品RestAPI的日期和時間屬性的預設值__
現在透過RestAPI正確設定日期、日期和時間屬性的預設值
  _ACP2E-3486 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_

### API、購物車和結帳

* __嚴重500錯誤： Magento\Framework\Webapi\Exception與Accept HTTP標頭有關__
修正後，指定「Accept」標頭沒有問題。
  _ACP2E-3343 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1366ae5e)_

### API， GraphQL

* __沒有可用於訂閱客戶獎勵點更新的graphQl__
在此修正之前，無法透過GraphQL變異和Rest API呼叫更新客戶屬性reward_warning_notification 。 現在可更新與客戶屬性reward_update_notification相同的專案。
  _ACP2E-3348_

### API、GraphQL、稅務

* __僅提供郵遞區號時，Luma (Rest API)和Graphql都不會計算稅額。__
現在，系統只提供郵遞區號時，就能正確計算稅捐，確保Luma (Rest API)和GraphQL的稅捐估計正確無誤。 以前，只提供郵遞區號時，只會計算運費預估，而不包含稅金。
  _AC-12060_

### 帳戶

* __客戶地址表單允許在名稱欄位中使用隨機碼__
系統現在會驗證客戶地址表單中「名字」和「姓氏」欄位的輸入，避免使用隨機代碼。 之前，系統允許在這些欄位中使用隨機程式碼，而不會擲回錯誤。
  _AC-10782 - [GitHub問題](https://github.com/magento/magento2/issues/38331) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38345)_
* __管理員密碼更新。__
  _AC-10886 - [GitHub問題](https://github.com/magento/magento2/issues/38352) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4bca5dfe)_
* __我的帳戶新增位址儲存時當機__
系統現在即使未顯示「地區」欄位，仍可正確儲存客戶地址，以防止在儲存過程中當機。 先前，嘗試新增或編輯沒有顯示區域欄位的地址會導致例外錯誤。
  _AC-10990 - [GitHub問題](https://github.com/magento/magento2/issues/38406) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38407)_
* __當URL大寫時，重新導向回圈__
系統現在會自動將URL中的大寫字元轉換為小寫，以防止在存取首頁時出現重新導向回圈。 先前，在安全性基底URL中加入大寫字元會在嘗試存取首頁時造成持續的重新導向回圈。
  _AC-11718 - [GitHub問題](https://github.com/magento/magento2/issues/38538) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38539)_
* 未為來賓帳戶儲存&#x200B;__middlename(&#39;s)__
系統現在會在結帳時正確儲存訪客帳戶的中間名稱，使其可在電子郵件範本中存取。 之前，中間名未儲存在報價表中，且無法在來賓帳戶的電子郵件範本中存取。
  _AC-11755 - [GitHub問題](https://github.com/magento/magento2/issues/38593) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39067)_
* __管理員：頁面動作按鈕向左浮動而非向右__
現在，系統可正確地將頁面動作按鈕對齊管理面板中粘性標題的右側，讓專業外觀與感覺更佳。 以前，這些按鈕錯誤地浮動到粘性標題的左側。
  _AC-11919 - [GitHub問題](https://github.com/magento/magento2/issues/38701) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/44cef3a9)_
* magento 2.4.7 __中的__`dev:di:info`錯誤
系統現在會在執行`dev:di:info`命令時正確顯示建構函式引數，避免發生任何錯誤。 以前，執行此命令會導致錯誤，因為引數中的型別不相符。
  _AC-11999 - [GitHub問題](https://github.com/magento/magento2/issues/38740) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0c53bbf7)_
* __以客戶選擇加入身分登入核取方塊無法翻譯__
系統現在允許在「商店檢視」範圍中設定「以客戶身分登入核取方塊」和「以客戶身分登入」核取方塊工具提示」欄位，從而啟用不同商店檢視的翻譯。 之前，這些欄位僅在「網站」範圍設定，無法翻譯個別商店檢視。
  _AC-13000 - [GitHub問題](https://github.com/magento/magento2/issues/32329) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32359)_
* __我的設定檔下拉式清單中的前端UI首頁按鈕不存在。（斷斷續續）__
  _AC-14299_
* __客戶已登入，但在前端顯示404錯誤。__
店面客戶儀表板頁面現在會在客戶登入時依預期載入。 客戶以前可以登入，但此頁面顯示404錯誤。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)
  _AC-6071 - [GitHub問題](https://github.com/magento/magento2/issues/35838) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36263)_
* __無法在管理員編輯客戶區段中儲存客戶屬性資訊；__
現在，根據管理員客戶編輯表單的網站範圍，已正確實施客戶的商店ID。
  _ACP2E-2791 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/488c1034)_
* 啟用私人銷售時，__[雲端]無法透過API建立客戶__
現在，在啟用網站限制時，客戶可由已驗證的管理員使用者建立，也可透過REST API使用已驗證的整合權杖建立。
  _ACP2E-3115_
* __登入後，無法顯示以訪客使用者身分新增至比較清單的產品。__
現在以客戶身分登入前已新增至產品比較清單的產品，在登入後仍會保留。
先前，登入後，無法顯示以訪客使用者身分新增至比較清單的產品。
  _ACP2E-3329 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* __允許國家/地區設定造成客戶地址設定發生問題__
現在選取「允許國家/地區」組態不會影響針對指定範圍以外顯示的國家/地區。 先前允許國家/地區組態影響指定範圍以外的客戶地址屬性
  _ACP2E-3433 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* __共用禮品登入會將活動日期顯示為1天前__
現在店面已正確顯示贈品註冊日期
  _ACP2E-3445_
* __VAPT：商業邏輯錯誤 — 未來日期為客戶出生日期__
客戶的出生日期不能設定在今天之後
  _ACP2E-3501 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_

### 帳戶、API、GraphQL

* __客戶API — 成功登入後，登入失敗次數無法重設為0__
現在，客戶透過API端點成功登入後，客戶實體表格中的失敗編號會重設為零。
  _ACP2E-3246 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec7e32a9)_

### 帳戶、管理員UI、B2B

* __受限制的管理員使用者無法一律看見自訂共用目錄__
受限制的管理員使用者現在可以一致地檢視和管理客戶及指派產品的所有共用目錄，前提是他們有權存取特定商店。 以前，有權存取特定商店的受限制管理員使用者無法總是看到指派了產品的所有共用目錄，或看到無法儲存的客戶，導致系統中的不一致。
  _ACP2E-3038 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7377de59)_

### 帳戶、購物車及結帳

* __&quot;select&quot;自訂客戶地址屬性未針對新客戶地址呈現__
  _AC-2341 - [GitHub問題](https://github.com/magento/magento2/issues/34950)_

### 管理員UI

* __[問題]針對「重新載入資料」資料按鈕__新增許可權檢查
系統現在包含「重新載入資料」按鈕的許可權檢查，確保資料只會顯示給具有適當許可權的使用者，以供他們存取。 以往，所有使用者都可以看見並點按「重新載入資料」按鈕，而在沒有必要許可權的使用者點按時，會導致「不允許」頁面。
  _AC-10705 - [GitHub問題](https://github.com/magento/magento2/issues/38283) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38279)_
* __[問題]行銷規則中屬性的標籤不一致__
系統現在會針對購物車價格規則中的類別和屬性選項，正確填入一致的標籤
  _AC-11427 - [GitHub問題](https://github.com/magento/magento2/issues/31232) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/31231)_
* __資料驗證成功，在以「取代」行為匯入產品時出現「匯入」按鈕__
系統現在會正確驗證資料，並在產品匯入過程中以「取代」行為隱藏「匯入」按鈕，防止任何非預期的資料取代。 以前，系統錯誤地驗證資料並顯示「匯入」按鈕，導致潛在的資料不一致。
  _AC-11588 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0574ac23)_
* __[錯誤] Magento 2.4.7不允許產品像片的副檔名為大寫字母。__
系統現在接受具有大寫字母副檔名的產品影像上傳，以確保順暢的產品建立過程。 之前，以大寫字母副檔名的影像上傳遭到拒絕，迫使使用者將副檔名變更為小寫。
  _AC-12167 - [GitHub問題](https://github.com/magento/magento2/issues/38831) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8f87c25)_
* __網格中含選取動作的隱藏下拉式清單（例如「內容>元素>頁面」）__
現在，系統已修復所有網格的所有類似下拉式清單。
  _AC-12319 - [GitHub問題](https://github.com/magento/magento2/issues/38891) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39371)_
* __[問題]修正警告：未定義的陣列索引鍵「篩選器」__
系統現在會處理新使用者尚未與書籤互動的情況，防止記錄未定義的陣列索引鍵「篩選器」警告。 以前，當新使用者未與書籤互動時，系統會記錄此警告。
  _AC-13131 - [GitHub問題](https://github.com/magento/magento2/issues/39013) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38996)_
* __由於Validate.php檔案中的程式碼變更，導致含有特殊字元的產品匯入csv檔案失敗__
系統現在可以正確驗證及匯入包含特殊字元的產品CSV檔案，進而允許成功傳輸資料。 先前，嘗試匯入包含特殊字元的產品CSV檔案會導致錯誤，阻礙匯入程式。
  _AC-13529 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __當「密碼重設要求的最大數量」設定大於0時，例如： 3 ，「超過限制錯誤訊息會在重新達到限制之前傳送，即從第二次開始__
  _AC-13767_
* __雖然「密碼重設要求數目上限」已設為0 （已停用），但「超過限制的錯誤訊息是從第2次傳送」__
  _AC-13768_
* __必要的電話號碼欄位沒有紅色星號__
電話號碼未顯示較早的紅色星號，但是  電話號碼是強制性的。 現在已修正紅色星號，可在電話號碼上顯示為強制欄位。
  _AC-13850 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c699c206)_
* __在管理員中，當我們嘗試重新排序提交訂單按鈕時，無法點選。 （斷斷續續）__
  _AC-14300_
* __[問題]將預設索引子模式設定為「排程」__
所有新索引子預設為&#x200B;**[!UICONTROL Update by Schedule]**&#x200B;模式。  先前預設模式為&#x200B;**[!UICONTROL Update on Save]**。 現有的索引器不受影響。 [GitHub-36419](https://github.com/magento/magento2/issues/36419)
  _AC-6975 - [GitHub問題](https://github.com/magento/magento2/issues/36419) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0b410856)_
* __[問題]在mview取消訂閱上卸除索引子變更記錄檔表格__
現在，當索引從「依排程更新」切換到「儲存時更新」時，系統會自動移除未使用的變更記錄表，將索引標籤為無效，以確保沒有遺漏任何專案。 以前，將索引切換為「儲存時更新」會在系統中保留未使用的變更記錄檔表格，並將所有變更的索引標籤為「有效」。
  _AC-7700 - [GitHub問題](https://github.com/magento/magento2/issues/29789) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/25859)_
* __在行動電話檢視中結帳付款時沒有運送連結__
系統現在可確保結帳標題/連結「運送」和「檢閱與付款」在行動檢視中一律顯示在頁面頂端，讓使用者能夠輕鬆地在步驟之間導覽，並進行必要的更正。 先前，這些標題/連結隱藏在行動檢視中，讓使用者難以瞭解他們目前的步驟或回到先前的步驟。
  _AC-7962 - [GitHub問題](https://github.com/magento/magento2/issues/36856) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36982)_
* __客戶訂單查詢出貨註解created_at傳回的+0時區不在商店設定的時區中__
使用客戶「訂單」查詢時，系統現在會正確顯示客戶設定時區之出貨備註中的「created_at」欄位。 以前，「created_at」欄位會顯示在+0時區，無論客戶的時區設定為何。
  _AC-8109 - [GitHub問題](https://github.com/magento/magento2/issues/36947) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37642)_
* __i18n：collect-phrases中斷轉譯完整性__
`bin/magento i18n:collect-phrases -o`命令現在可以正確從JavaScript和.phtml檔案收集及新增新片語，確保翻譯檔案能正確反映翻譯。 以前，系統無法在翻譯檔案中包含來自JavaScript檔案的多行翻譯短語以及來自.phtml檔案的短語，導致翻譯不完整或不正確。
  _AC-9843 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0c53bbf7)_
* 存取動態區塊的&#x200B;__許可權問題__
之前，對於受限管理員，新增動態區塊會擲回錯誤。 實作此修正後，受限制的管理員可以成功新增動態區塊，並編輯區塊沒有任何錯誤
  _ACP2E-2687_
* 存放區檢視名稱中的&#x200B;__單引號已由&amp;#039；__取代
格線的存放區檢視篩選器現在會正確顯示單引號
  _ACP2E-2787 - [GitHub問題](https://github.com/magento/magento2/issues/38395) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/39d54c2d)_
* __Favicon上傳無法驗證.ico檔案__
檔案驗證錯誤已更新為「檔案驗證失敗。 請驗證存放區設定中的影像處理設定。」 以前只是「檔案驗證失敗」。
  _ACP2E-2847 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/39d54c2d)_
* __PageBuilder中的相簿顯示舊的影像縮圖，而非新上傳的影像__
針對透過頁面產生器內容中的媒體集刪除並重新上傳的相同名稱影像，重新產生影像預覽。
  _ACP2E-2957 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/001e5188)_
* __由具有不同角色範圍的管理員使用者儲存產品會覆寫/刪除產品中現有的相關產品資訊__
以前，在修正之前，當二級管理員使用者點選儲存按鈕時，相關產品會重設並變為空白，而不會變更相關產品。 此項修正後，次要管理員使用者按一下儲存按鈕，產品未重設且儲存成功。
  _ACP2E-2978 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3056e9cb)_
* __無法匯出超過200個訂單__
已忽略先前提交之選定ID的伺服器要求大小限制，方法是將GET的HTTP要求變更為POST，以修正問題。 之前，由於GET請求大小的伺服器限制，因此會發生問題。
  _ACP2E-3033 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/93d50f8d)_
* __簽出頁面驗證訊息不正確。__
如果有任何必填欄位留空（例如「address」），伺服器端驗證將不會顯示訊息。 使用者端驗證將確保必填欄位錯誤通知出現，指出「這是必填欄位」。 以前，如果任何必填欄位留空，除了使用者端驗證訊息之外，還會顯示「需要地址」訊息。
  _ACP2E-3037 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9af794a4)_
* __管理員使用者的密碼重設範本問題__
問題已透過使用正確金鑰解決，現在在電子郵件範本中包含管理員使用者名稱，並正確完成主題。 以前，該問題源自所使用的過時的鍵值。
  _ACP2E-3125 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/93d50f8d)_
* __客戶區段URL中的雙斜線__
在格線中按一下「重設篩選器」時，URL中不會出現雙斜線。
  _ACP2E-3149 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8459b17d)_
* __COD不適用於允許的特定國家__
現在，允許的特定國家/地區隨時可以使用「貨到付款」功能，並且   AC-3216如預期運作。
  _ACP2E-3171 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6f4805f8)_
* __無法更新自訂建立的訂單狀態__
「我們現在可以更新自訂建立的訂單狀態，而之前唯有當目前的狀態是」處理「或」詐騙「時，才能變更狀態。」
  _ACP2E-3178 - [GitHub問題](https://github.com/magento/magento2/issues/38659) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8459b17d)_
* __送貨地址狀態不是自動更新__
修正前，送貨地址區域（或區域ID）與地址帳單資訊不同步。 現在，帳單地址資訊變更時，送貨地址區域和區域ID都會正確更新。
  _ACP2E-3294 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/581b7ef1)_
* __重設按鈕無法在新增/編輯管理員使用者上運作__
之前，重設按鈕在新增/編輯管理員使用者頁面上無法運作。 現在，在「系統 — >許可權 — >所有使用者」下的「管理員」面板中，「新增/編輯管理員使用者」頁面上的「重設」按鈕將正確運作。
  _ACP2E-3364 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5184c067)_
* __Magento管理員URL路由錯誤偵測和CORS錯誤__
修正後，如果自訂管理網域是主網域的子網域，則只能從已設定的子網域存取管理員。
  _ACP2E-3373 - [GitHub問題](https://github.com/magento/magento2/issues/37663) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3f12d152)_
* __「購物車允許的最大數量」的驗證中斷__
先前，當我們將`Maximum Qty Allowed in Shopping Cart`設為空白時，它不會擲回任何例外狀況，不過這裡不接受空白值。 此修正套用後，輸入空字串將會擲回例外狀況，而且不允許儲存產品。
  _ACP2E-3392 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Pagebuilder預覽UI問題] Page Builder欄中的按鈕未正確對齊__
頁面產生器欄中的按鈕現在已正確對齊。 之前，這些量度在頁面產生器欄中不會對齊。
  _ACP2E-3408 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_
* __訂購的產品報告未匯出。 404錯誤。__
產品已訂購報表匯出為CSV和XML，現在可如預期運作
  _ACP2E-3431 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/88660e79)_
* 以生產模式啟用Js縮制後，主控台中出現&#x200B;__TinyMCE JS錯誤__
先前，在管理員面板中以生產模式啟用JavaScript縮制，會導致瀏覽器主控台中出現與TinyMCE 6相關的JavaScript錯誤，進而影響功能和使用者體驗。 現在，此問題已解決，確保TinyMCE 6順利運作，不會產生任何錯誤，即使JS縮制已啟用。
  _ACP2E-3457 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/56463d5e)_
* __要求其他變更以完整完成ACP2E-3375修正__
&#39;-
  _ACP2E-3459 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d50f6b5d)_
* __自動啟用新的ACL許可權__
除非明確設定，否則新增至自訂模組的新許可權將不再自動授予所有現有使用者角色的存取權。
  _ACP2E-3503 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3f12d152)_
* __管理員動作記錄使用者報告未顯示admin_user_delete__的詳細資料
adminhtml_user_delete現在會正確記錄重要詳細資訊。 以前，不會為使用者刪除產生記錄。
  _ACP2E-3509 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4de008a9)_
* 從管理員下訂單時&#x200B;__未套用送貨條件的購物車規則__
先前，如果購物車價格規則具有附優惠券的送貨方法折扣，則無法透過管理員UI套用。 套用此修正後，系統將會從管理員UI成功套用特定送貨方法的購物車價格規則折扣及優惠券。
  _ACP2E-3536 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a52ff98f) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/11ce816b)_
* __[新增]十六進位程式碼未在色票__中正確更新
使用者在視覺色票檢色器中手動輸入的HEX程式碼不再由系統變更。 以前，由於色彩模型之間的轉換錯誤，某些HEX程式碼會經歷一些細微的調整。
  _ACP2E-3559 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/344fce23) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/1ef984c0)_

### 管理員UI、B2B

* __B2B以客戶標題登入仍具有Magento品牌__
較早的店面標題顯示「您現在在&lt;商店名稱>上以&lt;客戶名稱>連線」與Magento品牌。 此問題現已修正，且標題會顯示為ADOBE品牌。
  _AC-13628 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/96dec499)_

### 管理UI，目錄

* __無法以受限制的管理員使用者身分變更允許網站中類別產品的位置__
允許受限管理員使用者在受限網站下指派的根類別所包含的類別下，新增及排序產品。
  _ACP2E-2708_

### 管理員UI、付款/付款方法、訂單

* __交易授權未顯示在PayPal智慧型按鈕順序之後的交易索引標籤中__
使用PayPal智慧型按鈕下訂單後，系統現在會在「交易」標籤中正確顯示交易授權。 以前，在按一下「授權」按鈕後，授權交易未出現在Transaction標籤中，並且未建立「授權」型別的新交易。
  _AC-13520 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6cfb9b6b)_

### 管理員UI、效能

* __更新為2.4.5-p8後，從管理員建立訂單時發生500錯誤__
先前，啟用HTML縮制時，無法下達管理員的訂單。 現在，啟用HTML縮制後，管理員的訂單就可以成功下達。
  _ACP2E-3169 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b21e5d91)_

### 管理UI，運送

* __優惠券代碼計數不會在   如果訂單是多次出貨，則會顯示「管理優惠券代碼」標籤中的「使用時間」欄。__
之前，當訂購多批運送的訂單時，優惠券代碼計數沒有在管理優惠券代碼索引標籤的「使用時間」欄中更新。 現在，正確計數會顯示在兩個「使用時間」中，以反映多重送貨的所需值。
  _ACP2E-2519 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4745100c)_

### 管理UI、測試與預覽

* __[雲端]移除缺少影像的範本會導致pub/media被刪除__
在此修正之前，如果pagebuilder範本缺少預覽影像名稱，則會刪除pub/media資料夾。 修正後，只會刪除範本和預覽影像（如果找到）。
  _ACP2E-3424 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/報表

* __Google Analytics CSP錯誤https://region1.analytics.google.com__
Google Analytics啟用時，系統現在會正確允許連線至「https://region1.analytics.google.com&#39;」，避免內容安全性原則(CSP)錯誤。 之前，若啟用Google Analytics並從歐盟檢視網站，會因為拒絕連線至「https://region1.analytics.google.com&#39;」而導致CSP主控台錯誤。
  _AC-9922 - [GitHub問題](https://github.com/magento/magento2/issues/37750) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38991)_
* __進階報告無法運作__
系統現在支援以10,000批次載入和寫入報表，為超大型資料集產生進階報表資料檔案。 以前，進階報告模組無法為超大型資料集產生資料檔案，導致在執行analytics_collect_data cron作業期間出現「MySQL伺服器已消失」錯誤。
  _ACP2E-2570 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a12063bd)_
* __管理員訂購產品報告日期範圍可見性問題。__
使用者可從訂購產品報表中選取任何日期。 先前，重新整理表格後，選取「起始」日期會重設「截止」日期。
  _ACP2E-3080 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6f4805f8)_
* __不正確的curl標頭，導致`newrelic:create:deploy-marker`無法運作__
系統現在能正確設定curl標題的格式，讓`newrelic:create:deploy-marker`命令在New Relic中成功建立部署標籤。 之前，不正確的curl標題無法在New Relic中建立部署標籤。
  _ACP2E-3096 - [GitHub問題](https://github.com/magento/magento2/issues/37641) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6a185204)_
* __GTM遺失dataLayer中的addToCart事件（針對具有自訂選項的可設定產品）__
之前，不會為可設定產品觸發addToCart事件。 現在，事件已正確新增至GTM dataLayer變數。
  _ACP2E-3146_
* __NewRelic瀏覽器監視內嵌JS指令碼導致CSP錯誤__
應用程式現在會插入NewRelic瀏覽器監控指令碼，而不是APM代理程式，以符合CSP （內容安全性原則）。 先前，APM代理程式插入的NewRelic瀏覽器監視指令碼與CSP不相容，並導致無法執行指令碼。
  _ACP2E-3183 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/66dea0de)_
* 針對銷售訂單量大的專案，對sales_bestsellers_aggregated_daily資料表的&#x200B;__插入查詢變慢__
以前，針對大量下單訂單，最佳銷售者彙總的每日報表需要大量時間才能產生。 現在會及時產生報表。
  _ACP2E-3189 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7377de59)_
* __顯示錯誤貨幣符號的訂單報告__
訂單報表中訂單金額的貨幣符號錯誤地取自貨幣/選項/基準。 現在已更正為使用貨幣/選項/預設值，以便提供準確的報告。
  _ACP2E-3276 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[雲端]優惠券使用量報告__中的計算不正確
折價券報表網格中的銷售總計，現在會合併「折扣稅捐補償金額」與「出貨折扣稅捐補償金額」來精確計算。 以前，計算中缺少這些金額，導致銷售總額與銷售訂單資料之間出現差異。
  _ACP2E-3302 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d75cff27)_
* __共用的「&lt;project_id>/var/tmp」發生問題__
Analytics DataExport暫存檔將使用sys tmp目錄，該目錄更適合經常存取和變更。 為了避免同一伺服器上執行多個執行個體時發生衝突，臨時路徑已更新為使用執行個體的唯一ID
  _ACP2E-3339 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/報表，B2B

* __B2B - Sitemap包含未指派給共用目錄的產品/類別__
將Sitemap產生的類別和產品限製為僅指派給公用共用目錄和/或目錄類別許可權設定的類別和產品。
  _ACP2E-2300 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/報表、雲端

* __Magento捨棄大部分的New Relic cron交易#34108__
AC正在向NewRelic正確報告cron作業相關的交易。 以前，某些cron工作相關交易在NR中顯示為「OtherTransaction/Action/unknown」
  _ACP2E-3067 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/35b1b1da)_
* NR中的&#x200B;__量度可能對背景交易產生誤導 — ACP2E-3067__的後續追蹤
背景交易(cron)將使用組態設定中定義的New Relic應用程式名稱
  _ACP2E-3187 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

* __2.4.8-beta102 Package Enterprise Edition失敗，發生應用程式例外狀況__
  _AC-13501_
* __執行部分索引時，指派給共用目錄的產品未反映在前端__
部分索引完成後，透過REST API指派給共用目錄的產品現在會立即顯示在店面上。 過去，產品只有在完全重新建立索引後才會顯示。
  _ACP2E-2139 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7377de59)_
* __[行動版和案頭版的]雲端價格顯示方式與「我的報價」不同__
當型錄總價區段展開時，「可轉讓報價」中不再顯示「不需要的包含稅捐明細行」。
  _ACP2E-2873_
* __我的訂單區段上有不必要的邊框__
先前已建立其他套用其他CSS類別的容器（訂單參考），而造成不必要的框線出現在「我的訂單」區段內的訂單編號下方，而現在無法顯示。
  _ACP2E-3044 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9af794a4)_
* __sales_clean_quotes cron會從尚未核准的採購單刪除報價__
sales_clean_quotes cron工作現在不會刪除採購單中使用的報價單
  _ACP2E-3247 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/581b7ef1)_
* __下單按鈕在採購單詳細資料中消失__
修正當產品變數在卡片中指定的最小數量時，已核准採購單的「下訂單」按鈕隱藏的問題
  _ACP2E-3465_
* __[CLOUD]沒有識別碼= 0且具有b2b模組__的這類實體
啟用共用目錄功能時，登入的使用者可以將產品新增到購物車。
先前將產品新增到購物車會導致「沒有ID = 0的這類實體」錯誤
  _ACP2E-3474_
* __從請購單清單大量新增時，沒有針對我們的庫存產品顯示錯誤訊息__
在修正之前，無論無法新增至購物車的產品數量為何，都會顯示成功訊息。 現在，對於成功新增到購物車的產品以及失敗的產品，將顯示單獨的訊息。
  _ACP2E-3562_
* __排程更新後SKU更新發生問題，導致產品許可權不正確（–2拒絕）__
使用過去排程的更新修改產品的SKU時，不會再導致有權檢視產品的共用目錄客戶無法存取產品。
  _ACP2E-3628_

### B2B，目錄

* 使用NoDDL和類別許可權時，在重新索引期間顯示&#x200B;__產品/類別__
執行目錄許可權索引時，避免在店面受限制的類別及其內容上顯示。
  _ACP2E-2860_

### B2B，框架

* __篩選公司網格，然後嘗試網格CSV匯出將失敗並擲回例外狀況__
現在，系統允許成功將管理面板中的公司格線資料以CSV匯出，即使套用「未結餘額」和「公司型別」等篩選器也是如此。 以前，套用特定篩選條件並嘗試匯出網格資料會導致失敗並擲回例外狀況。
  _AC-9607 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B、GraphQL

* __[雲端]透過graphql呼叫__建立公司時無法設定custom_attributes
修正後，可在使用graphql要求建立公司期間，為公司管理員設定「custom_attributes」屬性。
  _ACP2E-3391_

### Braintree

* __Admin Express簽出按鈕已停用。__
  _AC-14293_
* __透過LPM付款__
系統現在會在初次載入時正確轉譯本機付款方法(LPM)，即使登入客戶的送貨地址與帳單地址不符亦然，以確保順利的結帳程式。 先前，客戶的送貨地址與帳單地址不符會導致LPM無法呈現，進而在結帳時造成潛在中斷。
  _BUNDLE-3367_
* __可設定為虛擬子產品__
系統現在允許擁有虛擬子產品之可設定產品的快速付款方法，以確保順暢的結帳程式。 以前，將具有虛擬子產品的可設定產品新增到購物車時，無法使用快速付款方法。
  _BUNDLE-3368_
* __CVV驗證失敗錯誤__
  _BUNDLE-3369_
* __透過帳戶區域存放問題247__
系統現在可讓客戶儲存跨多個網站的新卡片或PayPal帳戶資訊，而不會發生授權錯誤。 以前，客戶無法跨不同網站儲存新的付款方式，且收到授權錯誤訊息。
  _BUNDLE-3370_
* __從不同的國家/地區寄送地址__
系統現在可讓異動在從不同國家/地區運送至地址時順利處理，以確保順利結帳。 以前，嘗試從不同的國家/地區傳送地址會導致主控台錯誤，儘管前端沒有明顯的錯誤。
  _BUNDLE-3371_
* __信用卡 — Teardown功能__
現在，當客戶從付款頁面導覽回送貨頁面時，系統可正確處理Braintree PayPal元件的拆卸作業，避免任何錯誤，並確保PayPal Express按鈕可正確轉譯。 先前，從付款頁面導覽回送貨頁面時，有時會因嘗試拆卸Braintree PayPal元件而發生錯誤。
  _BUNDLE-3372_
* __PayPal Express的送貨回撥__
系統現在會在PayPal Express強制回應視窗中正確顯示可用的送貨方法，讓客戶在繼續檢閱頁面或完成交易前，能夠選取他們偏好的送貨方法。 之前，在PayPal Express強制回應視窗中無法選取送貨方法，因此客戶必須先在個別的稽核頁面上選取送貨方法，才能完成交易。
  _BUNDLE-3373_

### 組合

* __店面套件組合核取方塊驗證錯誤訊息計數超過1__
現在當按一下「加入購物車」按鈕時，系統只顯示一個驗證錯誤訊息，而未選取套件產品的任何核取方塊選項。 以前，系統會為每個未選取的核取方塊顯示多個驗證錯誤訊息。
  _AC-10826 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ea26621)_
* __在某些與順序相關的測試案例中擲回Magento例外狀況__
系統現在可正確處理各種測試案例中的「sendGuestPaymentInformation」步驟，避免擲回Magento例外狀況。 以前，這些例外是由於空值付款方法所造成，這會導致多個測試案例中的失敗。
  _AC-13321_

### 購物車與結帳

* 在比較產品頁面中將產品加入購物車時，__未正確處理例外狀況__
現在，當從比較產品頁面將產品加入購物車時，系統可正確處理例外狀況，並在控制器中顯示訊息管理員訊息。 在過去，例外狀況會導致傳回JSON編碼頁面，而非正確擷取和處理。
  _AC-10660 - [GitHub問題](https://github.com/magento/magento2/issues/38200) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38257) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0c53bbf7)_
* __GTag未傳送交易價格與總計。__
現在，系統會在啟用GTag時，正確地將交易價格和總計傳送至Google Tag，以確保準確追蹤電子商務資料。 以前，貨幣會不正確地作為「所有」訂單的一部分傳送，而不是與個別訂單相關聯。
  _AC-10698 - [GitHub問題](https://github.com/magento/magento2/issues/37348) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37504) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37349)_
* __[問題] [簽出] Depend指示已在失敗的付款電子郵件範本中更新__
系統現在會從虛擬產品的失敗付款電子郵件範本中正確忽略送貨地址和送貨方法，確保電子郵件中僅包含相關資訊。 以前，虛擬產品付款失敗的電子郵件錯誤地包含送貨地址和送貨方法。
  _AC-11641 - [GitHub問題](https://github.com/magento/magento2/issues/32781) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32511)_
* __現有客戶的Magento 2登入在簽出內會在Firefox瀏覽器中發生主控台錯誤__
系統現在可讓使用者在結帳過程中登入，而不會在Firefox瀏覽器中遇到任何主控台錯誤。 之前，在結帳期間嘗試以現有客戶身分登入，會導致Firefox發生主控台錯誤。
  _AC-11717 - [GitHub問題](https://github.com/magento/magento2/issues/38557) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39509)_
* __[問題] 2.4.7__中的銷售規則回歸
現在，系統可正確驗證銷售規則，避免在產品條件不符合任何產品名稱時，將優惠券代碼套用到購物車。 以前，即使產品狀況與任何產品名稱不符，也可以套用銷售規則，並針對運費金額提供折扣。
  _AC-11876 - [GitHub問題](https://github.com/magento/magento2/issues/38671) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0574ac23)_
* __[問題]銷售規則CartFixed計算：不正確的折扣金額__
系統現在會正確計算具有購物車固定金額之銷售規則的折扣金額，以確保無論購物車專案如何變更，都套用準確的折扣。 以前，當購物車專案變更時，折扣金額可能會錯誤地變化，有時會導致比預期大得多的折扣。
  _AC-11914 - [GitHub問題](https://github.com/magento/magento2/issues/38694) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/581b7ef1)_
* __[問題]載入器在郵遞區號變更後封鎖送貨方法，送貨費率驗證規則__
系統現在可正確處理自訂送貨方法，而不使用送貨費率驗證規則，確保載入器在結帳期間變更送貨地址中的郵遞區號後，不會封鎖送貨方法。 先前，在結帳期間變更送貨地址中的郵遞區號，會導致載入程式封鎖送貨方法，而且在使用沒有運費驗證規則的自訂送貨方法時無法消失。
  _AC-11993 - [GitHub問題](https://github.com/magento/magento2/issues/38742) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bafc571)_
* __優惠券代碼功能在Magento 2.4.7__上的結帳頁面中無法正常運作
系統現在會針對虛擬及可下載的產品，啟用結帳頁面上的折扣代碼/優惠券輸入欄位，讓使用者如預期套用折扣代碼。 之前已停用折扣代碼/優惠券輸入，且按鈕標題文字顯示為「取消優惠券」，以防止使用者套用折扣代碼。
  _AC-12170 - [GitHub問題](https://github.com/magento/magento2/issues/38826) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bafc571)_
* __條款與條件核取方塊不允許店面上的HTML__
現在，系統支援店面的「條款與條件」核取方塊文字中的HTML格式，可加強自訂和可讀性。 以前，核取方塊文字會以純文字格式顯示，忽略使用的任何HTML標籤。
  _AC-12479 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __為登入使用者建立的購物車價格規則未正確地套用為未登入使用者__
現在，系統會在登入使用者因Cookie過期而自動登出時，正確移除購物車價格規則，確保折扣不會套用至非登入使用者。 先前，即使使用者已登出，仍會套用購物車價格規則，導致將錯誤的折扣套用至未登入的使用者。
  _AC-12541 - [GitHub問題](https://github.com/magento/magento2/issues/38944) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7d5e3906)_
* __[問題] [功能]效能最佳化大型購物車，防止……__
系統現在會防止重複的getActions呼叫，提升購物車操作的速度和效率，藉此最佳化大型購物車的效能。 之前，如果購物車有多個專案，系統會多次呼叫getActions函式，因而降低系統效能。
  _AC-13302 - [GitHub問題](https://github.com/magento/magento2/issues/39292) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39290)_
* __禮品登入產品未正確顯示__
  _AC-13797_
* __禮品登入產品未正確顯示__
  _AC-13841_
* __地址轉譯程式中的翻譯VAT__
系統現在允許翻譯地址轉譯器中的「VAT」、「T」、「F」文字，讓使用者可以將這些字詞翻譯成商店的特定語言。 以前，這些術語無法翻譯，迫使使用者採用因應措施。
  _AC-8103 - [GitHub問題](https://github.com/magento/magento2/issues/36942) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36943)_
* __同時重複具有相同報價識別碼的訂單，但時間差異不大__
修正Adobe Commerce客戶遇到使用相同QuoteID下重複訂單的問題
  _ACP2E-2055 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f89a447e)_
* __永久購物車已在結帳步驟中清除__
修正後，在未登入時結帳時選取付款方式並不會終止持續工作階段。
  _ACP2E-2470 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_
* __重新排序會將未指派的產品加入購物車__
以前，對於不同的商店，產品可以從其他商店重新排序。 僅套用此修正後，若啟用客戶帳戶共用，可對相同範圍產品重新排序
  _ACP2E-2518 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f89a447e)_
* __在管理員中，選取專案時，左側的「購物車」沒有更新，並從右側的「移至購物車」__
選擇專案時，左側的「購物車」會更新，並從管理員側的右側「移至購物車」。 以前，此功能無法運作，因為轉換的購物車專案不會從工作階段中變空白。
  _ACP2E-2620 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/39d54c2d)_
* __[雲端]銷售規則未套用至多重出貨的第一筆訂單__
修正後，相同多送貨報價的每筆訂單都會正確顯示折扣。
  _ACP2E-2646 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f89a447e)_
* __[雲端]將相同產品加入購物車的生產平行要求導致購物車API中出現兩個個別的專案__
系統現在可以正確處理多個平行請求，以將相同產品加入購物車到單一條列專案，防止為同一SKU建立個別條列專案。 以前，透過REST API並行請求將相同產品新增到購物車會導致同一SKU出現多個條列專案。
  _ACP2E-2664 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f89a447e)_
* __從禮品登入Magento 2.4.4 Enterprise/Commerce訂購時發生問題__
已解決無法從禮品註冊處成功購買產品的問題，可以下訂單，並適當地更新禮品註冊處。 之前，嘗試從贈品註冊處下訂單時發生錯誤，導致購買無法完成。
  _ACP2E-2676 - [GitHub問題](https://github.com/magento/magento2/issues/35432)_
* __正在取得無法傳送Cookie。 嘗試重新排序時&#39;mage-messages&#39;的大小__
重新排序程式現在不會產生自己的錯誤。 它將依賴購物車列出內建專案檢查。
  _ACP2E-2704 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ba25af8a)_
* __結帳時未選取預設送貨地址__
在啟用的地址搜尋內容中，預設送貨地址現在為選取事件。
  _ACP2E-2798 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7e0e5582)_
* 使用自訂選項的&#x200B;__[雲端] graphql addProductsToCart api問題__
GraphQL使用不同的自訂選項將相同的產品正確地新增至購物車
  _ACP2E-2897 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c971859e)_
* 變更商店檢視時&#x200B;__[雲端]相關產品規則無法運作__
已透過確認在購物車頁面上成功收到自訂屬性值來修正問題。 先前，在店面購物車頁面上的商店之間切換時，無法正確擷取該資料。
  _ACP2E-2917_
* __結帳為新客戶時，已將多個地址新增至帳戶__
現在，系統只會在訂單無法建立時儲存一次新的客戶地址，以防止在訂單放置錯誤時建立多個相同的地址。 以前，每次嘗試下訂單時，系統都會儲存新地址，無論是否成功建立訂單。
  _ACP2E-2923 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/001e5188) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/2ebcef39)_
* __透過訪客訂單重新訂購客戶訂單導致空購物車__
先前，當透過「訂購與退貨」頁面進行重新訂購時，客戶會重新導向至登入頁面。 套用此修正後，進行重新訂購時，註冊的客戶會被正確重新導向至「檢視購物車」頁面。 此流程的運作方式與訪客客戶相同。
  _ACP2E-3004 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6a185204)_
* __角色資源有限的管理員使用者無法檢視購物車__
以前，受限制的管理員無法從相關網站的管理員面板中看到捨棄的購物車。 套用此修正後，受限制的管理員可以從管理員面板檢視捨棄的購物車。
  _ACP2E-3025 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d1f7dc95)_
* __[雲端]快速訂購大量SKU效能__
當購物車價格規則條件中使用的屬性未針對所有產品出現，且已啟用MAP （最低廣告價格）功能時，結帳效能已有所改善。
  _ACP2E-3176 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/66dea0de)_
* 購物車中有&#x200B;__個重複的專案__
系統現在可以正確處理多個平行請求，以將相同產品加入購物車到單一條列專案，防止為同一SKU建立個別條列專案。 以前，並行請求將相同產品新增到店面的購物車會導致同一SKU出現多個條列專案。
  _ACP2E-3211 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/66dea0de)_
* __已將結帳訂單電子郵件確認傳送至以名字/姓氏輸入的電子郵件__
結帳訂單電子郵件確認函已不再傳送。此確認函先前於在「名字」和「姓氏」欄位中輸入類似電子郵件的模式時傳送。
  _ACP2E-3296 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5184c067)_
* __結帳送貨地址表單更新為錯誤的地址__
shippingAddressFromData現在會儲存至每個網站的本機儲存空間。 以前，如果在URL中使用商店代碼，且在同一個訪客工作階段中從多個網站起始結帳，則結帳時可能會將錯誤網站的位址自動填入送貨地址表單中。
  _ACP2E-3402 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* 啟用地址搜尋時，__[雲端]簽出未保留選取的帳單地址__
啟用地址搜尋時，結帳付款頁面現在會保留選取的帳單地址。 先前，如果「客戶地址數限制」設定為1，而客戶有多個地址，則在重新載入頁面後，所選的帳單地址會消失。
  _ACP2E-3405_
* __禮卡產品 | 購物車合併正在合併禮品卡__
現在已正確合併購物車中的資訊卡產品
  _ACP2E-3407 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/88660e79)_
* __登出時未遵循購物車持續性__
新增從客戶登入到驗證快顯視窗和簽出登入的記住我的功能。
  _ACP2E-3415 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/344fce23)_
* __現有報價資料未更新/不可見，請在trigger_recollect = 1__時建立新的報價記錄
客戶的購物車專案不會再因產品在加入購物車後遭刪除而消失。
  _ACP2E-3488 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_
* __購買禮品登入專案時，客戶會看到其登入上沒有的專案__
贈品登入更新不再包含不屬於贈品登入的專案。
  _ACP2E-3495_
* __[雲端] 「移除全部」確認快顯視窗在未確認的情況下移除購物車專案的問題__
現在，對於需要注意的產品，按一下「全部移除」按鈕會提示出現確認快顯視窗，以確保只有在確認後才會移除專案。 以前，專案會立即移除而不需要任何確認
  _ACP2E-3510_
* __[雲端]重新排序按鈕功能__
從管理員區域重新訂購的訂單現在會在報價中新增有庫存的產品，即使原始訂單中有些產品不再有庫存。 修正前，如果原始訂單中沒有庫存的產品，則不會將任何產品新增至新報價單。
  _ACP2E-3618 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a52ff98f)_
* __搜尋存放區無法依郵遞區號運作__
依郵遞區號搜尋取車位置時，荷蘭語本地化無法正常運作。 修正後，取車地點搜尋會根據郵遞區號提供結果。
  _ACP2E-3622 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/344fce23)_

### 購物車與結帳、結帳/單頁結帳

* __[隨機錯誤]電子郵件欄位未呈現，或需要很長時間才能顯示在結帳送貨或付款頁面__
Commerce現在會依預期在結帳送貨與付款頁面上轉譯&#x200B;**[!UICONTROL Email]**&#x200B;欄位。 之前，此欄位不存在或呈現緩慢。
  _AC-9386 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e1babcfd)_

### 購物車與結帳、訂購

* 從管理員下訂單時，__產品的Datepicker包含多個日期欄位無效的可自訂選項__
在管理訂單建立程式中設定具有多個可自訂日期選項的產品時，系統現在會正確顯示所有日期欄位的日期選擇器。 以前，日期選擇器只顯示第一個日期欄位，而其餘欄位則沒有日期選擇器。
  _ACP2E-3097 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b21e5d91)_

### 購物車與結帳、送貨

* __可設定產品的「最便宜的運費」立即購買中斷__
即時購買功能針對可設定組態的產品錯誤地選取了較昂貴的店內交貨選項，而不是最便宜的統一費率方法。 此修正可確保根據實際價格選擇正確的送貨方法。」
  _AC-12119 - [GitHub問題](https://github.com/magento/magento2/issues/38811) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38819) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/29fe9097)_

### 目錄

* __清除cron_schedule資料庫資料表時沒有清除不存在的工作__
系統現在會自動清除cron_schedule資料庫表格，移除系統中已不存在的作業專案。 這可透過在表格中維持最少列數來確保最佳效能。 以前，非作用中模組或已移除模組的工作專案不會清除，導致cron_schedule表格中發生不必要的資料累積。
  _AC-10910 - [GitHub問題](https://github.com/magento/magento2/issues/38217) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38693)_
* 未從可設定的產品中刪除&#x200B;__層級價格__
現在，當產品從簡單產品轉換為可設定產品時，系統可正確移除產品的層級價格，以確保前端可準確顯示價格。 以前，將產品從簡單產品轉換為可設定產品時，不會刪除可設定產品的層級價格，從而導致顯示的價格不符。
  _AC-10953 - [GitHub問題](https://github.com/magento/magento2/issues/38390) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38427)_
* __非預設storeview上的類別描述WYSIWYG是空的__
現在，系統在商店檢視層級編輯類別時，可在WYSIWYG編輯器中正確儲存並顯示類別說明。 以前，在商店檢視層級儲存類別說明後，WYSIWYG編輯器會顯示為空白。
  _AC-11804 - [GitHub問題](https://github.com/magento/magento2/issues/38622) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38623)_
* __無法透過選取一個核取方塊來重新排序可設定的產品__
系統現在會使用單一選取的核取方塊自訂選項，以正確處理可設定產品的重新排序，從而允許成功建立購物籃。 之前，嘗試重新排序這類產品會導致錯誤，且無法將專案新增至購物車。
  _AC-11970 - [GitHub問題](https://github.com/magento/magento2/issues/38736) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1d144bce)_
* __[問題]修正分層導覽上的篩選器專案用詞__
系統現在會在階層式導覽濾鏡專案中正確使用「專案」和「專案」等字詞，提高濾鏡說明的清晰度和準確性。 以前，這些字詞的使用不正確，導致導覽篩選選項的使用者可能混淆。
  _AC-12076 - [GitHub問題](https://github.com/magento/magento2/issues/38789) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37852)_
* __自訂選項的日期和時間格式無法運作__
系統現在會正確將設定的日期格式套用至日期型別的產品自訂選項，確保日期格式會在前端正確顯示。 先前，日期格式設定的變更不會反映在日期型別的產品自訂選項的前端。
  _AC-12164 - [GitHub問題](https://github.com/magento/magento2/issues/32990) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38925)_
* __下拉式清單選項遺失__
現在，在建立具有超過20個值的新屬性時，系統會在下拉式清單中正確顯示所有值。 以前，只顯示前20個值或其他選定的頁面值，導致剩餘的值遺失。
  _AC-13068 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47b448e2)_
* __[問題]使用類別執行階段快取目前的儲存區ID__
系統現在會正確地將目前的存放區ID用於類別執行階段快取，以防止在使用模擬或自訂程式碼將類別儲存在不同存放區時覆寫資料。 先前，儲存在執行階段的物件可能來自錯誤的存放區，導致資料覆寫。
  _AC-13296 - [GitHub問題](https://github.com/magento/magento2/issues/39310) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36394)_
* __bin/magento sampledata：deploy —no-update擲回例外狀況__
在sampledata：deploy命令中使用 — no-update選項時，系統現在可以正確接受布林值，以防止在範例資料部署期間發生任何錯誤。 以前，使用此命令時會擲回錯誤，因為系統錯誤地預期了整數值。
  _AC-13324 - [GitHub問題](https://github.com/magento/magento2/issues/39344) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39345)_
* __[問題]修正EAV快取型別的使用方式__
系統現在會在所有相關位置正確使用EAV快取型別，確保資料快取的一致性和有效性。 先前的EAV快取型別使用方式不一致，導致資料快取作業可能缺乏效率且不一致。
  _AC-13355 - [GitHub問題](https://github.com/magento/magento2/issues/32322) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/31264)_
* __包含空白資料的目錄進階搜尋移至搜尋結果頁面[2.4.dev分支]__
系統現在會在「進階搜尋」頁面上正確保留使用者，並在使用者嘗試執行搜尋時顯示錯誤訊息，而不輸入任何資料。 以前，執行空白搜尋會將使用者重新導向至「目錄進階搜尋」頁面，並出現一則訊息，提示使用者修改其搜尋。
  _AC-13596 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __[問題]產品配置基於attribute_set__
此系統現在允許根據屬性集調整產品版面，提供更實用且有效率的方式，以管理前端商店中的產品顯示。 之前，版面配置只能根據SKU或產品型別進行調整，這對於許多產品或特定文章而言並不總是可行的。
  _AC-13622 - [GitHub問題](https://github.com/magento/magento2/issues/38790) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36244)_
* __eav_attribute_option_value資料表__上缺少唯一索引鍵
現在，系統在「eav_attribute_option_value」表格的「option_id」和「store_id」欄中包含唯一索引鍵，以防止同一個存放區檢視出現多個值的選項。 以前，錯誤的程式碼可能會導致選項針對相同的商店檢視擁有多個值，進而在編輯產品或屬性時造成問題。
  _AC-6738 - [GitHub問題](https://github.com/magento/magento2/issues/24718) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/28796)_
* __[問題]使用類別產品索引器的可見性類別，而非硬式編碼值__
系統現在使用類別產品索引器的可見度類別，而不是硬式編碼值，以增強模組化程度。 以前，在類別產品索引器中會使用硬式編碼值，這會限制靈活性和適應性。
  _AC-8297 - [GitHub問題](https://github.com/magento/magento2/issues/37200) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37199)_
* __新產品Widget中的貨幣代碼未變更__
現在，系統會在前端貨幣變更時，正確更新新產品小工具中的貨幣代碼，以確保網站間貨幣顯示的一致性。 之前，變更前端中的貨幣不會影響新產品介面工具集中顯示的貨幣代碼。
  _AC-9375 - [GitHub問題](https://github.com/magento/magento2/issues/37898) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37899)_
* 可設定產品的&#x200B;__一般價格未顯示在PLP上__
產品清單頁面現在會顯示可設定產品的正常價格，這些產品具有具有具有特殊價格的子產品。
  _ACP2E-2224 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_
* __庫存資訊未直接顯示在Visual Merchandising格線上__
庫存現在會根據選取的商店顯示。
  _ACP2E-2478 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/bdbf97ea)_
* __Widget內容未在cms頁面__上更新
現在，當產品設定為新產品並儲存時，系統會更新CMS頁面上的Widget內容，確保頁面會顯示更新的產品集合。 以前，由於快取中Widget使用的快取身分不正確，頁面未更新以顯示新產品。
  _ACP2E-2621 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f89a447e)_
* __儲存套件組合產品的進階定價時發生問題__
捆綁產品儲存效能改善。
  _ACP2E-2630 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b2286ecf)_
* 建立目錄價格規則時，__[內部部署]重新索引程式效率低__
現在儲存目錄價格規則不會使索引子失效，而是只會重新索引受影響的產品
  _ACP2E-2652 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f89a447e)_
* __正在透過CSV匯入更新日期和時間型別產品屬性的時間__
現在，日期時間屬性在匯出的資料中會有時間部分。 也可以使用匯入來更新此類屬性的時間。 此外，如果已啟用「欄位附件」，「additional_attributes」欄中的屬性值將會用雙引號括住。
  _ACP2E-2679 - [GitHub問題](https://github.com/magento/magento2/issues/38306) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ea79f7dd)_
* __當要求的網站ID錯誤時，沒有適當的錯誤訊息__
現在已新增適當的錯誤訊息，以在請求中的網站ID錯誤時顯示。 先前，要求中的網站ID錯誤時不會進行驗證。
  _ACP2E-2689 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/39d54c2d)_
* 刪除不會影響影像的現有排定更新後，__產品影像遺失__
刪除中繼更新時不會移除產品影像。
  _ACP2E-2785 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8931218)_
* __[雲端]搭配層級價格使用時捆綁產品的價格錯誤__
先前，在計算四捨五入為2個小數點的某些百分比折扣時，會產生不同的最終價格，以用於購物車和產品清單頁面/產品詳細資訊頁面。 套用此修正後，套裝產品的最終價格與產品詳細資料頁面、產品清單頁面和迷你購物車頁面中的價格相同。
  _ACP2E-2799 - [GitHub問題](https://github.com/magento/magento2/issues/38091) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b2286ecf)_
* __目錄促銷活動規則不適用於quantity_and_stock_status屬性__
現在，型錄促銷規則會考慮quantity_and_stock_status屬性，而之前從管理員端產生新產品時，不會考慮該屬性。
  _ACP2E-2805 - [GitHub問題](https://github.com/magento/magento2/issues/35627) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/cf34971d)_
* 透過REST API更新價格時，__產品實體updated_at欄值未更新__
透過REST API更新現有產品時，管理員的產品「上次更新時間」欄會更新適當的日期時間。 之前「上次更新時間」欄未正確更新。
  _ACP2E-2837 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/39d54c2d)_
* __可以透過產品匯入設定非唯一值__
系統現在會在產品匯入期間，正確執行唯一產品屬性的唯一值限制，以防止該屬性的值重複。 以前，如果產品屬性是透過產品匯入設定為具有唯一值，您就可以為產品屬性設定非唯一值。
  _ACP2E-2840 - [GitHub問題](https://github.com/magento/magento2/issues/38445) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7e0e5582)_
* __啟用單一存放區模式時，前端上的產品會使用存放區特定資料__
之前，當我們針對預設商店檢視啟用單一商店模式時，變更未移轉至網站層級的範圍。 套用此修正後，當我們啟用單一商店模式時，預設商店檢視特定資料將與網站層級特定資料同步，並將解決產品和類別之間可能出現的衝突。
  _ACP2E-2843 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8931218)_
* __無法使用Rest API在類別中設定[預設排序依據]__
透過REST / SOAP API請求正確更新類別上的default_sort_by
  _ACP2E-2857 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/57a32313)_
* __[雲端]商家面臨願望清單計數問題__
將產品新增至一家商店的願望清單中，不會再增加在同一瀏覽器中開啟之其他商店的願望清單計數。 先前，如果兩個存放區都載入同一個瀏覽器，另一個存放區的願望清單計數也會增加。
  _ACP2E-2871 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3a7c4d17)_
* 使用套件組合產品時，前端的&#x200B;__類別頁面會顯示空白槽__
在目前存放區內容中不可銷售的套件組合產品不再編制索引。
  _ACP2E-2874 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/bc37ec76)_
* __[說明]套件組合產品序號表問題__
現在當刪除「套件」產品或刪除「套件」產品選項時，會移除「套件」產品序號表格(sequence_product_bundle_option， sequence_product_bundle_selection)中的記錄。
之前，未移除套件組合產品序號表格中的記錄。
  _ACP2E-2888_
* __[雲端]多網站架構中的報價問題__
以前，使用不同貨幣和客戶群組的多網站架構無法正確將折扣套用至商店。 實施此修正後，具有不同客戶群組價格折扣的多網站架構將成功套用至不同的商店。
  _ACP2E-2905 - [GitHub問題](https://github.com/magento/magento2/issues/38506) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_
* __dynamic-rows.js：658編輯套件組合產品時未攔截到的TypeError： dataRecord.slice__
從套件產品中刪除選項時，瀏覽器主控台中沒有javascript錯誤。
  _ACP2E-2909 - [GitHub問題](https://github.com/magento/magento2/issues/38505) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/93d50f8d)_
* __[雲端]套件組合產品訂單確認中的定價錯誤__
使用基礎貨幣以外的貨幣時，會依序在Storefront顯示套件組合選項的正確數量。
  _ACP2E-2950 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_
* __YouTube影片新增錯誤__
產品影像和視訊是在全域範圍中設定。 由於您無法在一個領域擁有產品影片，而不能在另一個領域擁有，因此Youtube API金鑰設定已設定為全域範圍。
  _ACP2E-2956 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_
* __[只有store_id=0__&#x200B;才更新Cloud] URL
「URL路徑」現在會以正確的存放區ID儲存。 以前，商店ID不正確，導致在移動類別時資料庫中保留不正確的URL路徑。
  _ACP2E-2964 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9af794a4)_
* __async.operations.all已執行並建立錯誤。__
REST API呼叫中錯誤的產品連結資料不再導致嚴重錯誤。
  _ACP2E-3009 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_
* __[雲端]行動裝置問題僅無法在PDP影像上捏合__
系統現在支援Chrome上行動檢視中產品詳細資料頁面影像的縮放夾功能，可增強行動使用者體驗。 之前，在Chrome上的行動檢視中連按兩下影像時，系統無法如預期放大影像。
  _ACP2E-3029 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/148c3ead)_
* __選項名稱為0__的LayeredNavigation中遺漏標籤
已透過略過屬性值0的空值檢查器來解決問題。 之前，該維度會被視為空白並導致問題。
  _ACP2E-3058 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3a7c4d17)_
* __客戶看到其他客戶群組的價格__
修正客戶群組相關資訊因請求中X-Magento-Vary的舊值而儲存在錯誤區段的問題
  _ACP2E-3069 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d1f7dc95)_
* __刪除組合選項時發生錯誤__
系統現在可以正確刪除套件組合選項，而不會觸發錯誤或導致頁面無回應。 先前，嘗試刪除套件組合選項會導致「頁面無回應」錯誤並阻止產品儲存。
  _ACP2E-3076 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6a185204)_
* __類別許可權記憶體不足瀏覽器問題__
類別許可權UI經過重新設計，可使用現成的UI元件和分頁來呈現大量許可權。 先前類別許可權會導致瀏覽器當機，並會將大量許可權指派給類別。
  _ACP2E-3094_
* __[Cloud]影像檔案不存在於New Relic錯誤記錄檔中__
系統現在會將自訂預留位置影像同步至本機儲存體，確保在使用遠端儲存體(例如AWS S3)時可正確轉譯。 先前，自訂預留位置影像在使用遠端儲存空間時無法轉譯，導致影像顯示中斷和錯誤記錄。
  _ACP2E-3100 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d1f7dc95)_
* __由於快取__，新產品RSS摘要未更新為新產品
當產品設定為新產品並儲存時，新產品的Rss摘要現在會更新
  _ACP2E-3103 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d01ee51e)_
* __[雲端]產品媒體庫GQL回應未依影像位置排序__
系統現在會依在GraphQL回應中的位置正確排序媒體集中的專案，確保顯示順序準確。 先前，媒體集中的專案並未依位置排序，導致顯示順序不正確。
  _ACP2E-3126 - [GitHub問題](https://github.com/magento/magento2/issues/37671) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b21e5d91)_
* __[雲端]子類別專案未顯示在管理員後端的Widget編輯上__
在新Widget頁面上的類別樹狀結構載入第5級以上的類別時，應該不會再發生問題。 以前，在載入超過第5級類別的樹狀結構時，會遺漏某些類別。
  _ACP2E-3136 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/148c3ead)_
* __[雲端]實際行動裝置上的雙指縮放和移動問題__
系統現在可確保行動裝置上的影像縮放功能一致，提供流暢且可預測的使用者體驗。 以前，影像縮放功能不一致，且在行動裝置上檢視特定時間點後會突然縮小。
  _ACP2E-3198 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1366ae5e)_
* __從共用目錄取消指派產品時，未清除願望清單產品__
現在，如果共用目錄中沒有產品，則願望清單中不會顯示任何專案。 先前，即使願望清單中實際上沒有專案，願望清單頁面也會錯誤地顯示「1專案」的計數。
  _ACP2E-3282 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5184c067)_
* __相關產品選取全部/取消選取所有問題__
先前，如果手動選取產品，相關產品的「全選」/「取消全選」按鈕無法正常運作。 修正後，這些按鈕現在即使手動選取也運作一致，確保所有產品皆已正確選取或取消選取。
  _ACP2E-3286 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[雲端]庫存警示電子郵件翻譯成錯誤的語言__
針對使用不同語言進行多次商店檢視的網站傳送庫存/價格警報時，建立警報的商店檢視語言將用於電子郵件。
  _ACP2E-3336 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4cf5e62) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/9f3e63d1)_
* __已停用的類別在類別樹狀結構中的名稱不再為灰色__
過去，已停用的類別不會在類別樹狀結構中呈現灰色。 現在，它們會以灰顯效果顯示。
  _ACP2E-3350 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d75cff27)_
* __可設定的產品編輯表單載入導致逾時和記憶體耗盡__
在修正之前，可設定的產品變數是根據所有可能的屬性選項組合來建構。 如果屬性有許多選項，這將導致冗長且耗用的資源作業。 現在，可設定的產品變數是根據現有的子產品屬性來建構。 如此可大幅減少計算，進而改善資源的使用狀況。
  _ACP2E-3410 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* 使用色票時，__Fotorama未正確載入視訊，並已透過URL預先選取選項__
如果URL包含選取的選項，產品影片現在可在可設定的產品詳細資料頁面上正確轉譯。
  _ACP2E-3454 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* __PageBuilder轉盤Widget顯示不符合條件的產品__
Widget中使用的產品清單現在會遵守類別條件
  _ACP2E-3461 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* 當群組中所有產品的數量無效時，便會觸發&#x200B;__驗證錯誤__
現在，當一個產品的數量無效時（之前未發生），群組中所有產品都會正確觸發驗證錯誤。
  _ACP2E-3469 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/56463d5e)_
* __[雲端]特殊價格未顯示在可設定的產品中__
修正後，變更「用於產品清單」中特殊價格屬性的值將不會影響可設定產品的特殊價格的顯示。
  _ACP2E-3513 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_
* __如果處理程式已終止，則不會清除__索引子暫存資料表
現在，如果索引器處理序已終止，則會清除CatalogRule索引器暫存資料表
  _ACP2E-3516 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_
* 在2.4.7-p3 __中的__[ QUANS]核心單元測試失敗
此測試不需要發行說明，因為這是單元測試改進。
  _ACP2E-3520 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_
* 具有多個來源的分組產品的庫存數量擷取中有&#x200B;__個效能問題__
現在當指派的產品具有大量庫存來源時，已最佳化群組產品和套件產品編輯頁面。
  _ACP2E-3533 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/0208e433)_
* __重新修正ACP2E-3389__
改善大量錨點類別時管理類別頁面的效能
  _ACP2E-3641 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/982b1c42)_

### 目錄，內容

* __[雲端]快取未失效。__
先前，儲存具有更新設計版面的CMS頁面時，該頁面未在前端正確反映。 套用此修正後，當我們變更設計版面並儲存CMS頁面時，前端會看到合適的設計版面。
  _ACP2E-3063 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/66dea0de)_
* __[雲端]錨點/非錨點類別在內容Widget__中反轉
先前，當我們選取「顯示於 — >錨點類別」時，會顯示所有未反映錨點與非錨點之間父子關係的類別。 套用此修正後，「顯示於 — >錨點類別」只會顯示「錨點類別」（可選取），而「顯示於 — >非錨點類別」則會顯示「非錨點類別」（可選取）
  _ACP2E-3131 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7377de59)_
* __類別無法使用Widget__
先前，如果我們為不同的錨點/非錨點類別儲存CMS區塊，那麼當它顯示在前端時，對子類別沒有作用。 套用此修正後，區塊會顯示在不同類別的前端。
  _ACP2E-3152 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d01ee51e)_

### 目錄，框架

* __訂單get(Shipments|Creditmemos|Invoice)集合 — 集合不應載入__
系統現在會確保從訂單中擷取出貨與銷退折讓單時，不會預先載入收貨，允許對這些收貨套用額外的過濾條件或訂單。 以前，這些集合會自動載入，以防止進行任何進一步的修改。
  _AC-9111 - [GitHub問題](https://github.com/magento/magento2/issues/37561) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37562)_
* __[雲端]後續追蹤：檢查資料是否有變更時，資料比較不符__
過去，儲存物件會在每次沒有任何資料變更的情況下呼叫（適用於任何數值資料欄位，例如int/float/double）。 它會觸發標幟_hasDataChanges設為true並呼叫save函式。 它也不會檢查由字串封裝的浮動數字。 此修正套用後，只有在資料變更時，儲存函式才會呼叫。 int/float/double-check的資料值，其值會傳遞至函式，且會執行嚴格的型別比對
  _ACP2E-2949 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8931218)_

### 目錄， GraphQL

* __在GraphQL中處理類別篩選器： includeDirectChildrenOnly和category_uid__
依category_uid篩選時，只會擷取直接子類別。
  _ACP2E-3090 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/93d50f8d)_
* __[雲端] Graphql產品排序無法運作__
在變數中傳遞欄位時，GraphQl產品依多個欄位排序現在可如預期運作。
  _ACP2E-3166 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8459b17d)_
* __GraphQL產品中的層級價格傳回錯誤的值（相較於店面）__
修正後，針對graphql請求傳回的產品層級價格會有一個專案的價格。
  _ACP2E-3312 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1366ae5e)_
* __[雲端] B2B：透過GraphQL的類別問題__
修正後，即使根類別沒有允許許可權，類別graphql查詢也會傳回具有允許許可權的類別。
  _ACP2E-3385_

### 目錄、定價、測試和預覽

* 同時更新大量產品時，__[雲端]特殊價格API端點傳回錯誤__
現在，特殊價格大量更新API將為每個日期範圍建立單一行銷活動，而不是為每個產品和日期範圍建立多個排程更新。 此外，它也會支援並行API請求，以更快處理大量SKU。
  _ACP2E-2672 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f89a447e)_

### 目錄、產品

* 編輯產品中的&#x200B;__類別選擇樹狀結構順序與目錄 — >類別__中的設定順序不同
系統現在會依照在目錄 — >類別中設定的順序，在產品編輯區段中正確顯示類別選取樹狀結構，讓產品管理在大型目錄中更容易。 以前，產品編輯區段中的類別樹狀結構會以類別建立的順序顯示，無論在目錄 — >類別中設定的顯示順序為何。
  _AC-7050 - [GitHub問題](https://github.com/magento/magento2/issues/36101) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36104)_

### 目錄，SEO

* __頁面> 1__時類別的規範URL不正確
先前，多頁內容的標準URL無法正常運作，只會持續顯示基礎URL。 不過，實施修正後，多頁內容的標準URL現在會正確顯示具有頁面ID的URL。
  _ACP2E-3653 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/982b1c42)_

### 目錄，搜尋

* __類別和搜尋上未顯示產品，但直接連結正常運作__
先前，具有price_* attribute_code的「是/否」自訂屬性不適用於索引。 進行此修正後，「是/否」自訂屬性會如預期運作。
  _ACP2E-2757 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ba25af8a)_
* __[雲端]某些類別頁面上的彈性搜尋錯誤__
先前，當我們提及設定票證時，將多個產品的價格定為0，會在前端類別頁面擲回例外狀況。 套用此修正後，當多個產品價格0且我們在前端載入類別頁面時，不會擲回任何例外狀況，並將成功載入類別頁面。
  _ACP2E-3053 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8931218)_
* 建立物件時發生&#x200B;__型別錯誤： Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor例外狀況__
修正後，不需指定$data即可建立Magento\CatalogSearch\Model\Indexer\Fulltext類別的執行個體。
  _ACP2E-3345 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1366ae5e)_
* 儲存至Magento Admin __後，__[&#x200B;產品的CLOUD]問題在前端看不到
在修正後，擁有長名稱子產品的可設定產品不會在店面中遺失。
  _ACP2E-3521 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_

### 目錄，送貨

* __訂購禮品登入專案時送貨地址為空白__
以前，對於訪客使用者禮品註冊專案，當從電子郵件功能傳回時，會產生空白地址，這對於下訂單而言是不正確的。 套用此修正後，禮品登入會檢查已登入的使用者/訪客使用者以及指定的地址（如果存在）。
  _ACP2E-3195_

### 雲端

* __[雲端] PHPSESSID正在變更每個POST要求__
如果已啟用L2 Redis快取並且客戶已從後端更新，則PHPSESSID不再針對登入客戶的前端區域重新產生POST請求
  _ACP2E-3010 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6a185204)_
* __Sitemap產生警告__
修正後，Sitemap會在系統tmp目錄中產生，並複製到最終目的地。
  _ACP2E-3532 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_

### 內容

* __[問題]與「最近檢視的」Widget__中的價格顯示問題
系統現在會在「最近檢視的產品」Widget中正確顯示無庫存簡單產品的價格，確保所有元件和產品清單頁面的一致性。 以往，由於價格載入範本中的條件，無存貨簡易產品的價格不會顯示在「最近檢視的產品」Widget中。
  _AC-10539 - [GitHub問題](https://github.com/magento/magento2/issues/38167) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38159)_
* __[問題] acl.xsd檔案中的錯字與文法正確__
系統現在會更正acl.xsd檔案中的拼寫錯誤和文法錯誤，提高說明檔案的清晰度和準確性。 以前，acl.xsd檔案包含拼寫錯誤和錯誤的語法，這可能會造成混淆。
  _AC-10596 - [GitHub問題](https://github.com/magento/magento2/issues/38061) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38046)_
* __相簿中的__Pagebuilder橫幅影像不可見
系統現在可以正確顯示上傳到Pagebuilder相簿中新建立資料夾中的橫幅影像，消除之前的主控台錯誤。 在此修正之前，如果橫幅影像上傳到新資料夾，則無法在相簿中顯示，進而造成主控台錯誤。
  _AC-10845 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8f87c25)_
* 更新至2.4.5-p8 __後__「區碼未設定」
現在，當Magento_CSP模組啟用且「dev/js/translate_strategy」設為「embedded」時，系統可成功完成靜態內容部署程式，而不會觸發「未設定區碼」錯誤。 以前，在這些情況下，靜態內容部署程式會失敗並出現「未設定區碼」錯誤。
  _AC-12283 - [GitHub問題](https://github.com/magento/magento2/issues/38845) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38922)_
* __Widget類別樹狀結構未正確轉譯__
  _AC-12692 - [GitHub問題](https://github.com/magento/magento2/issues/39008) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/58e40ceb)_
* __變更設計設定頁面中的主題時，無法看到「使用預設值」訊息__
系統現在包含單獨的欄，以根據設計設定頁面中選取的主題顯示「使用預設值」訊息。 這可確保預設值狀態的清晰度和可見度。 以前，不會顯示「使用預設值」訊息，導致對所選主題狀態的混淆。
  _AC-13054 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47b448e2)_
* __[問題]再次恢復與TinyMCE外掛程式的回溯相容性(之後……__
系統現在恢復與TinyMCE外掛程式的回溯相容性，當從其他位置使用Widget時，可呼叫外掛程式中定義的函式。 先前，由於TinyMCE版本有所變更，外掛程式不會將Widget傳回為物件，導致嘗試在Widget例項上呼叫某些函式時發生錯誤。
  _AC-13569 - [GitHub問題](https://github.com/magento/magento2/issues/39262) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39258)_
* 產品頁面上的WYSIWYG編輯器出現&#x200B;__[問題]檔案上傳問題__
現在，系統可正確顯示資料夾樹狀結構，並允許影像在產品頁面上的WYSIWYG編輯器中上傳，即使先展開「影像和影片」索引標籤後亦然。 先前，展開「影像和影片」索引標籤後，導致資料夾樹狀結構未顯示，以及嘗試在WYSIWYG編輯器中上傳影像時出現錯誤訊息。
  _AC-9638 - [GitHub問題](https://github.com/magento/magento2/issues/38026) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38025)_
* __[內部部署]動態區塊問題__
動態區塊中的小工具現在已正確轉譯。
  _ACP2E-2392 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a12063bd)_
* __YouTube Nocookie URL在頁面產生器中無法運作__
現在pagebuilder允許在驗證規則的表單元素設定中使用youtube無Cookie url。 之前，youtube非Cookie URL無法在pagebuilder中運作。
  _ACP2E-2606_
* __[雲端]前端未載入，因為新聞稿範本有問題__
透過CMS頁面內容區段新增區塊不會再導致例外狀況
  _ACP2E-2693 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ea79f7dd)_
* __ACP2E-2836： [Cloud]在記錄檔中發現調查例外狀況： InvalidArgumentException：類別不存在於vendor/magento/module-rule/Model/ConditionFactory.php__
移除PageBuilder產品內容設定的條件時，記錄檔中不會再記錄例外狀況。 先前，移除PageBuilder產品內容設定的條件會導致記錄中記錄嚴重例外狀況，而不會在前端造成任何問題。
  _ACP2E-2836 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_
* __切換到單一存放區模式 — 不再顯示全域內容__
系統現在會在啟用單一商店模式時，將商店檢視設計設定與網站設計設定同步，確保前端可看到內容更新。 以前，切換到單一商店模式會防止內容更新反映在店面上。
  _ACP2E-2842 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7e0e5582)_
* 嘗試新增連結和其他可用性問題時，__頁面產生器會取代影像。__
現在按一下影像，頁面產生器文字元素中wysiwyg編輯器中的連結會在連結設定對話方塊中的影像載入適當資料。 現在，在編輯器中新增影像連結也可正常運作。 之前，影像已更換為連結。
  _ACP2E-2903 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* 將0位元組影像置入目錄時，__舊媒體集無法轉譯影像__
系統現在可以在不中斷功能的情況下處理媒體集中的0位元組影像，讓目錄中的其他影像可以如預期顯示和選取。 以前，如果媒體集中有0位元組的影像，將無法顯示或選取目錄中的所有影像。
  _ACP2E-2970 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/35b1b1da)_
* 編輯CMS區塊時&#x200B;__頁面產生器發生錯誤__
系統現在會使用頁面產生器正確儲存管理員區域中所做的變更，而不會擲回「頁面產生器只呈現5秒而沒有釋放鎖定」錯誤。 在瀏覽器主控台中。 以前，嘗試儲存變更時會發生此錯誤，導致內容無法成功更新。
  _ACP2E-3064 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __[雲端]購物車區段上沒有結帳或編輯購物車的按鈕__
現在，套件組合產品已透過Widget新增至購物車，且未發生錯誤。
  _ACP2E-3092 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b21e5d91) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_
* __類別頁面上的內容測試預覽未顯示產品Widget__
此問題已透過確保連結至CMS區塊的其他類別的產品專案已準確記錄到資料庫中來修正。 先前，請求類別預覽頁面時，它會傳回空白的結果集。
  _ACP2E-3113_
* __[雲端]上傳影像按鈕無法運作__
在PageBuilder中Banner和Slider的「上傳影像」按鈕未如預期運作之前，現在按一下按鈕時會開啟本機檔案管理員，以選取要上傳的影像。
  _ACP2E-3122 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_
* __imagecreatetruecolor()：引數#2 ($height)必須大於0。 無法上傳特定影像__
已解決透過媒體集上傳高度為0的影像時，導致管理員發生錯誤的問題，並使用sync命令成功同步資產。 先前無法透過媒體集上傳影像，當特定影像在媒體集中時，同步命令也會失敗。
  _ACP2E-3127 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6f4805f8)_
* __Prototype.js Array.from與Google Maps API發生衝突__
Google地圖現在會在PageBuilder編輯器中正確轉譯。 以前，Javascript錯誤會導致Google地圖無法正確呈現。
  _ACP2E-3154 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/148c3ead)_
* __[雲端] - CMS滑桿未反映最新變更__
此問題已透過確保在編輯投影片熒幕上觸發儲存事件時重新整理滑桿清單來修正。 在過去，這會觸發並造成問題。
  _ACP2E-3275 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __使用頁面產生器以特定順序插入CMS區塊時，CSM頁面中發生錯誤__
先前，在某些PHP和OS (Linux)版本中，透過PageBuilder參考其他cms區塊的區塊轉譯會失敗並出現「發生未知錯誤」。 請再試一次。」 現在，Cms區塊的內容會在PageBuilder控制的內容中正確呈現。
  _ACP2E-3326 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __[雲端]動態區塊將無法正常運作__
現在，在登出後，已登入的客戶區段會被清除，以防止來賓工作階段繼承先前登入的區段
  _ACP2E-3388_
* __大型內容的Pagebuilder範本預覽失敗__
大型內容導致畫布元素超過瀏覽器的限制，並傳回不正確的值，這會破壞後端程式碼（無法正確解碼影像）。 已修正將畫布大小限製為通用瀏覽器上限的問題。
  _ACP2E-3428 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/adfb1747)_
* __TinyMCE 7遺失字型大小的最新安全性更新__
WYSIWYG編輯器中現在提供字型大小和字型系列選取器。 在此修正之前，使用TinyMCE 7時，這些無法在編輯器介面中使用。
  _ACP2E-3430 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d50f6b5d) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_
* __TinyMCE 7編輯器在PT的管理員字型大小，而不是PX，請澄清__
修正前，您無法在WYSIWYG區域中指定以畫素為單位的字型大小。 現在您可以以px格式設定字型大小，而非pt格式。
  _ACP2E-3483 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3f12d152) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __頁面產生器中的產品內容型別已摺疊，沒有正確的訊息__
修正前，當Widget中沒有產品時，預覽版html未正確產生。 現在，空白回應已正確產生，且產品Widget在預覽中可正常顯示。
  _ACP2E-3490 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3f12d152) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __[頁面產生器]新增產品清單以封鎖導致錯誤__
現在透過頁面產生器將套件組合產品清單新增至區塊不會產生錯誤
  _ACP2E-3534 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/344fce23)_

### 內容， SEO

* __CMS頁面階層可能會導致URL重寫問題__
先前，針對非網站根頁面的自訂永久URL重寫，會無限期重新導向，且不會載入頁面。 套用此修正後，非網站根頁面的自訂URL重寫會如預期運作，不會發生重新導向回圈。
  _ACP2E-2870_

### 內容、測試和預覽

* __目錄價格規則設定為使用動態區塊排程時未顯示__
系統現在會在產品詳細資料頁面上正確顯示與已排程型錄價格規則相關聯的動態內容。 先前，在排程型錄價格規則時，無法載入動態內容。
  _ACP2E-2979_

### 客戶/

* __前端 — 客戶建立頁面中的出生日期驗證失敗__
確保所有驗證都應該在moment.js系統相依性升級至最新的次要版本後運作
  _AC-12162 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/de4dfb8e)_
* __客戶區段>條件>產品歷程記錄* > 「已檢視產品」無法運作__
系統現在會在符合條件時，在「客戶區段」底下的「已檢視產品」條件下，正確顯示相符的註冊客戶。 過去，即使符合條件，符合的註冊客戶數仍維持為零。
  _AC-13060_
* __國家/地區下拉式清單變更時，__區域文字欄位未重設
現在，當下拉式選單中的國家/地區變更時，系統會重設區域文字欄位，以確保先前的值不會持續存在。 之前，從下拉式清單變更國家/地區時不會重設地區欄位，導致保留最後儲存的值。
  _AC-8499 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ea26621)_
* __刪除客戶時不會清除Storefront上登入和刪除客戶的所有瀏覽器工作階段資料__
刪除客戶現在會依預期清除店面中登入和刪除客戶的所有瀏覽器工作階段資料。 購物者可以繼續購物，他們的瀏覽器會將他們的工作階段視為訪客工作階段。 先前，當登入購物者的客戶帳戶從管理員中刪除時，購物者的瀏覽器會擲回JavaScript錯誤。
  _AC-9240 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7d5e3906)_

### 框架

* __[問題]`app/code/Magento/Translation/etc/di.xml`__中未使用的型別設定
系統現在會移除設定中未使用的相依性，進而增強整體程式碼潔淨度及效率。 之前，設定中有未使用的相依性，這些相依性不會貢獻任何功能。
  _AC-10037 - [GitHub問題](https://github.com/magento/magento2/issues/38030) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38064)_
* __V1/customers/password端點問題/問題__
現在透過API處理密碼變更請求時，系統會遵守在管理GUI中設定的限制，以防止可能濫用密碼重設功能。 以前，API可以在管理GUI中定義的規則之外處理密碼變更請求，在已知有效電子郵件時，可能會允許不斷重設電子郵件。
  _AC-10654 - [GitHub問題](https://github.com/magento/magento2/issues/38238) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0c53bbf7)_
* __清漆設定未排除所有行銷引數__
系統現在會正確排除Varnish設定中的所有常見行銷引數，確保準確追蹤和分析。 之前，某些行銷引數（例如gad_source、srsltid和msclkid）未排除，導致資料收集可能不準確。
  _AC-10738 - [GitHub問題](https://github.com/magento/magento2/issues/38298) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39188)_
* __目錄搜尋索引程式錯誤索引程式__
無論使用PHP編譯的libxml版本為何，系統現在都能順利完成重新索引指令，而不會發生任何錯誤。 以前，當使用特定版本的libxml編譯PHP時，執行「重新索引」命令會導致「索引處理期間目錄搜尋索引處理錯誤」錯誤。
  _AC-10838 - [GitHub問題](https://github.com/magento/magento2/issues/38254) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38553) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0574ac23)_
* __已將created_at、status和grand_total篩選器新增至客戶訂單查詢，並修正多個篩選器失敗__
系統現在支援在客戶「訂單」查詢中使用created_at、status和grand_total篩選器，並已解決多個篩選器未正確套用的問題。 以前，系統不支援這些篩選器，且無法在查詢中使用多個篩選器時套用所有篩選器。
  _AC-10941 - [GitHub問題](https://github.com/magento/magento2/issues/38392) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36949)_
* __從相關/向上銷售/交叉銷售區塊和價格索引中隨機填入查詢__
系統現在會最佳化相關、向上銷售和交叉銷售區塊的查詢，提升效能並防止網站因過多查詢而停止運作。 以前，系統可能會因這些區塊中的查詢而變得超載，導致速度大幅減慢，並可能導致網站關閉。
  _AC-10991 - [GitHub問題](https://github.com/magento/magento2/issues/36667) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38050)_
* __例外狀況：警告：正在嘗試存取陣列位移，位置在…… -> Calendar.php，因為升級至ICU 74.1 (PHP Intl)__
每當購物者或商家造訪店面或管理員時，Commerce不會再於exception.log中記錄下列例外狀況： `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`。 [GitHub-38214](https://github.com/magento/magento2/issues/38214)
  _AC-11423 - [GitHub問題](https://github.com/magento/magento2/issues/38214) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38364)_
* __[問題]當表單包含名稱為`method`__的元素時，修正客戶資料的問題
現在，即使表單中存在名為「method」的元素，系統仍可在表單提交中正確識別「method」屬性。 這可確保準確處理客戶資料。 先前，如果表單元素命名為「method」，則會干擾表單提交中「method」屬性的識別，導致客戶資料處理的潛在問題。
  _AC-11476 - [GitHub問題](https://github.com/magento/magento2/issues/38484) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38449)_
* __[問題]修正\Magento\Framework\Data\Collection：：getItemById__的PHPDocs
\Magento\Framework\Data\Collection：：getItemById方法的PHPDocs已更新，可能包含null作為傳回型別，解決靜態分析工具的問題。 先前，方法的PHPDocs並未指定null作為可能的傳回型別，導致在條件陳述式中使用方法時，靜態分析中出現警告或錯誤。
  _AC-11489 - [GitHub問題](https://github.com/magento/magento2/issues/38485) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38439)_
* __[問題]僅允許在`setup:di:compile`__期間使用有效的偏好設定
現在，如果偏好設定是針對不存在的類別建立或明確排除的類別，則系統會在`setup:di:compile`命令期間擲回錯誤，以確保只允許有效的偏好設定。 以前，這些案例會無訊息地失敗，可能會使任何與原始類別關聯的外掛程式變成無用。
  _AC-11592 - [GitHub問題](https://github.com/magento/magento2/issues/38517) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33161)_
* __Magento嘗試修改LoggerProxy __的__喚醒方法中的唯讀屬性
現在，系統允許修改LoggerProxy的__wakeUp方法中先前唯讀的屬性，確保順利操作而不會強迫使用者採取因應措施。 先前，嘗試重新指派LoggerProxy的__wakeUp方法中唯讀屬性的值會造成問題。
  _AC-11651 - [GitHub問題](https://github.com/magento/magento2/issues/38526) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8f87c25)_
* __[問題] AC-2039 AC-1667升級TinyMCE參考__
更新composer.json中的tinymce最新版本
  _AC-11681 - [GitHub問題](https://github.com/magento/magento2/issues/38533) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36543) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b34c0a75)_
* __ChangelogBatchWalker無法在多個執行緒中運作__
系統現在支援MView索引的處理程式分支，以防止在多個執行緒上執行索引器時發生錯誤。 以前，在多個執行緒上執行ChangelogBatchWalker會導致刪除其他執行緒使用的表格，進而在索引器執行期間造成錯誤。
  _AC-11696 - [GitHub問題](https://github.com/magento/magento2/issues/38246) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38248)_
* __[問題]重新命名名稱錯誤的變數__
系統現在會正確命名包含仍可退款的金額的變數，以防止在偵錯期間產生混淆。 之前，此變數被錯誤地命名為totalReturn，這可能導致開發人員誤解。
  _AC-11781 - [GitHub問題](https://github.com/magento/magento2/issues/38609) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36205)_
* __[問題]透過XML傳遞自訂屬性至目前的連結__
系統現在允許透過XML將自訂屬性傳遞到目前的連結，確保即使連結是目前的頁面，這些屬性也能正確顯示。 以前，由於getAttributesHtml()方法未用於目前連結，因此不會顯示目前頁面連結的自訂屬性。
  _AC-11809 - [GitHub問題](https://github.com/magento/magento2/issues/38500) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/30070)_
* __某些組態的內建FPC快取在2.4.7中損毀__
系統現在會在MAGE_RUN_CODE引數設定時正確快取頁面，確保最佳效能。 以前，在這些情況下不會快取頁面，這可能會導致潛在的效能問題。
  _AC-11819 - [GitHub問題](https://github.com/magento/magento2/issues/38626) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38646) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0c53bbf7)_
* __[問題]修正開發人員和生產模式之間處理例外狀況的不一致__
系統現在會一致地處理開發人員和生產模式之間的例外狀況，避免在擲回例外狀況時意外重新導向登入頁面。 以前，例外狀況處理的不一致性可能會導致重新導向到生產模式的登入頁面，而不是顯示例外狀況訊息。
  _AC-11829 - [GitHub問題](https://github.com/magento/magento2/issues/38639) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37712)_
* __取代token_list.phtml中的「PayPal帳戶」翻譯__
系統現在會在「儲存的付款方法」頁面中，將可代幣帳戶付款方法的區段標示為「帳戶」，而非「PayPal帳戶」，使其更能代表其功能。 之前，此區段特別標示為「PayPal帳戶」，當新增其他可權杖化的帳戶付款方法時，會造成誤導。
  _AC-11852 - [GitHub問題](https://github.com/magento/magento2/issues/35622) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37959)_
* __已遺失Magento\Catalog\Model\ProductRepository類別的回溯相容性__
ProductRepository類別現在會將Initialization Helper類別還原為第二個引數，維持回溯相容性，確保從此類別擴充的模組能如預期般運作。 先前，移除ProductRepository類別中建構函式的Initialization Helper會導致回溯相容性遺失，迫使使用者不得不採取因應措施。
  _AC-11874 - [GitHub問題](https://github.com/magento/magento2/issues/38669)_
* __[問題]靜態內容部署 — 型別錯誤__
系統現在會在靜態內容部署期間正確處理空的LESS檔案，並顯示「LESS檔案是空的」錯誤訊息。 以前，在部署期間遇到空的LESS檔案時，會擲回不正確的型別錯誤。
  _AC-11905 - [GitHub問題](https://github.com/magento/magento2/issues/38682) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38683)_
* __[問題] [檢視]已移除連結和指令碼標籤中的額外空間__
系統現在可確保連結和指令碼標籤中沒有額外的空格，提供更乾淨且更有效率的程式碼。 之前，連結和指令碼標籤中的屬性之間可能會出現雙空格字元。
  _AC-12002 - [GitHub問題](https://github.com/magento/magento2/issues/32920) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32919)_
* __[問題]避免設定錯誤的無限回圈__
系統現在會藉由防止虛擬型別設定中的自我參考對應來避免無限回圈。 這可確保應用程式在嘗試取消參考自我參考節點時，不會陷入無休止的回圈中。 先前，如果虛擬型別設定是自我參照，則會導致應用程式無限期迴轉。
  _AC-12127 - [GitHub問題](https://github.com/magento/magento2/issues/38822) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38794)_
* __物件管理員未用於Magento\Csp\Model\Mode\Data\ModeConfigured__
系統現在會在建立ModeConfigured物件時正確使用物件管理員，允許在此物件上使用外掛程式。 先前並未使用Object Manager，因此無法將外掛程式套用至ModeConfigured物件。
  _AC-12299 - [GitHub問題](https://github.com/magento/magento2/issues/38875) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38886)_
* __產品庫存和價格警示中的檔案區塊註解不準確__
產品庫存和價格警示中deleteCustomer方法的檔案區塊註解已更正，以正確反映該方法會刪除與指定客戶及網站（而非網站上的客戶）相關的所有庫存產品或價格警示。 以前，評論錯誤地指出方法用於從網站中刪除客戶。
  _AC-12540 - [GitHub問題](https://github.com/magento/magento2/issues/38939) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39001)_
* __[問題]針對產生的資料使用編譯的設定，而非一般設定__
系統現在會針對產生的資料使用已編譯的組態，而非一般組態，減少依賴特定程式碼版本的網路傳輸和資料開銷。 這項變更可防止在容器交換期間在共用執行個體中覆寫快取，進而改善穩定性並減少停機時間。 以前，某些核心類別使用共用設定型別，這可能會導致快取覆寫或應用程式停機，因為多個伺服器的程式碼版本不同。
  _AC-12594 - [GitHub問題](https://github.com/magento/magento2/issues/38785) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/29954)_
* __[問題]從e1ccdb中移除的extjs移除檔案參考……__
系統現在會從先前已移除的extjs移除檔案參考，消除瀏覽器主控台和系統記錄檔中的錯誤。 以前，由於缺少參照的檔案，這些參照會導致錯誤。
  _AC-12597 - [GitHub問題](https://github.com/magento/magento2/issues/38960) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38951)_
* __[問題]次要清除：修正sprintf的錯誤用法，此處只需要2個預留位置，而w...__
系統現在會正確使用sprintf函式，搭配適當數量的預留位置，以提升程式碼清潔度和一致性。 先前，sprintf函式與額外的引數搭配使用不正確，這不會導致任何重大問題，但使用方式不正確。
  _AC-12778 - [GitHub問題](https://github.com/magento/magento2/issues/39062) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38628)_
* __PHP 8.2.15已移除FTP延伸模組__
系統現在將FTP擴充功能加入為composer.json檔案中的相依性，以確保透過FTP成功設定CSV匯入。 先前，由於PHP套件中缺少FTP副檔名，嘗試透過FTP設定CSV匯入時擲回錯誤。
  _AC-12857 - [GitHub問題](https://github.com/magento/magento2/issues/39083) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47b448e2)_
* __[問題]修正Magento模組中參考的不正確類別。__
系統現在會正確參考模組中的類別，確保作業更順暢，並防止因不存在類別而當機。 這包括Indexer和Creditmemo模組中的錯誤修正，以及PrintAction類別中HttpGetActionInterface的實作。 以前，不正確的類別引用會導致錯誤和潛在的系統當機，並且某些功能(例如creditmemo PDF檔案的檔案名稱和庫存的重新索引)無法按預期運作。
  _AC-12869 - [GitHub問題](https://github.com/magento/magento2/issues/39126) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37784)_
* __可定義`dev:di:info` CLI命令的Area__
系統現在可讓開發人員定義`dev:di:info` CLI命令的區域，以強化開發和偵錯程式。 以前，這個指令只能顯示GLOBAL區域的資訊。
  _AC-12964 - [GitHub問題](https://github.com/magento/magento2/issues/38758) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38759)_
* __[問題]新增isMultipleFiles屬性至影像表單元素範本__
此修正可防止將影像新增至多個檔案影像表單元素時，「在此瀏覽以尋找或拖曳影像」按鈕消失。
  _AC-13149 - [GitHub問題](https://github.com/magento/magento2/issues/39219) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36325)_
* __安裝：升級因charset和定序變更而失敗MariaDB 11.4版本__
  _AC-13247_
* __[問題]移除所有行銷取得引數以將快取最小化__
系統現在會移除所有Marketing Get引數，以最佳化快取使用率，鏡射Varnish使用時所使用的邏輯。 以前，這些引數可能會導致快取膨脹和效能降低。
  _AC-13279 - [GitHub問題](https://github.com/magento/magento2/issues/39266) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39099)_
* __[問題] [PHPDOC]修正錯誤的phpdoc Magento\Directory\Model\AllowedCountries：：getAllowedCountries()__
AllowedCountries：：getAllowedCountries()方法的PHPDoc已經過修正，以提供精確資訊，提高檔案的清晰度和實用性。 以前，此方法的PHPDoc包含不正確的資訊，這可能會導致混淆或誤用方法。
  _AC-13345 - [GitHub問題](https://github.com/magento/magento2/issues/39246) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39241)_
* __[問題]移除我們不再支援的PHP版本的部分程式碼。__
移除Magento不再支援之PHP版本的程式碼
  _AC-13348 - [GitHub問題](https://github.com/magento/magento2/issues/39361) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39202)_
* __[問題]讓ImageMagick介面卡與php8相容（從浮點數到int的隱含轉換）__
系統現在藉由在計算影像尺寸時正確處理浮點數，確保與PHP8的相容性，防止因浮點數到int的隱含轉換而發生任何錯誤。 先前，影像尺寸的計算可能會產生浮點數，而隱含四捨五入時會造成錯誤。
  _AC-13417 - [GitHub問題](https://github.com/magento/magento2/issues/39402) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37362)_
* __[問題] [PHPDOC]修正錯誤的phpdoc Magento\Framework\App\Config\ScopeConfigInterface__
此更新會更正Magento\Framework\App\Config\ScopeConfigInterface中的PHPDoc註解，以正確反映getValue和isSetFlag方法的$scopeCode引數型別。
  _AC-13537 - [GitHub問題](https://github.com/magento/magento2/issues/39492) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39199)_
* __Magento\Framework\Filesystem\Driver\Http取決於原因片語OK__
已從Magento\Framework\Filesystem\Driver\Http：：isExists移除「確定」片語檢查
  _AC-13725 - [GitHub問題](https://github.com/magento/magento2/issues/39546) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39558)_
* __Customer Grid索引子在[依排程更新]模式中無法正常運作__
先前的「客戶」格線已立即更新，但在修正後，「客戶」格線會在cron執行後更新，但不會立即反映。
  _AC-13810 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1da9ba6f)_
* js檔案發生&#x200B;__拼寫錯誤。__
系統現在會在JavaScript檔案中正確使用「訂閱者」一詞，確保相關功能可正常運作。 之前，JavaScript檔案中的印刷錯誤會導致「subscribers」一詞使用錯誤。
  _AC-6754 - [GitHub問題](https://github.com/magento/magento2/issues/36163) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36171)_
* __[問題]移除禁止的`@author`標籤__
系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，確保程式碼更乾淨且標準化。 以前，`@author`標籤存在於某些模組中，這違反了既定的編碼標準。
  _AC-8353 - [GitHub問題](https://github.com/magento/magento2/issues/37253) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37003)_
* __[問題]從`Magento_Customer` （第2部分）__&#x200B;移除禁止的`@author`標籤
系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，確保程式碼更乾淨且標準化。 以前，`@author`標籤存在於某些模組中，這違反了既定的編碼標準。
  _AC-8356 - [GitHub問題](https://github.com/magento/magento2/issues/37250) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37000)_
* __editorconfig語法中的空格中斷[{composer，auth}.json]__的規則
修正editorconfig中的語法錯誤後，系統現在可正確將4空格縮排套用至composer和auth.json檔案。 先前，由於editorconfig語法中有空格，這些檔案的格式不正確，有2個空格的縮排。
  _AC-8659 - [GitHub問題](https://github.com/magento/magento2/issues/37394) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37395)_
* __[問題]改善cron錯誤記錄__
系統現在會擷取並記錄cron流程的STDERR和STDOUT，在cron流程失敗的情況下提供有價值的診斷資訊。 以前，cron處理程式內的任何錯誤訊息都不會被記錄，而且在不同處理程式中執行的cron群組的STDERR和STDOUT會遺失。
  _AC-8662 - [GitHub問題](https://github.com/magento/magento2/issues/37453) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32690)_
* __[問題]在某些安裝程式cli命令的輸出中新增一些色彩__
系統現在會為某些安裝程式命令列介面(CLI)指令的輸出增加更多色彩，增強可讀性和使用者體驗。 以前，由於缺少色彩差異，這些指令的輸出比較難以讀取。
  _AC-8984 - [GitHub問題](https://github.com/magento/magento2/issues/29335) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/29298)_
* __當新增具有必要州/地區的新國家/地區時，升級Magento會重設一般/地區/州_required。__
系統現在只會在新增具有必要狀態的新國家/地區時，將修改過的國家新增到「一般/地區/州_必要」設定，以防止假設地區已停用的自訂程式碼發生任何中斷。 以前，新增具有必要狀態的國家會將「一般/地區/州_必要」設定重設為具有必要狀態的預設國家/地區，這可能會中斷業務。
  _AC-9630 - [GitHub問題](https://github.com/magento/magento2/issues/37796) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38076)_
* __具有複雜`calc`運算式的php &amp; nodejs程式庫(grunt)之間較少編譯的差異__
在更新wikimedia/less.php：^5.x後，修正php &amp; nodejs程式庫(grunt)之間較少編譯的差異
  _AC-9712 - [GitHub問題](https://github.com/magento/magento2/issues/37841) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b34c0a75)_
* 執行部分索引時發生&#x200B;__「找不到基底資料表或檢視」錯誤__
在次要db連線的情況下，部分重新索引現在可搭配大型變更記錄檔正常運作
  _ACP2E-2692 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ba25af8a)_
* __將MariaDB升級至10.5.1或更新版本後發生的問題__
修正Mysql升級後，DB中的datetime值將轉換為0000-00-00 00:00:00的問題
  _ACP2E-2844 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a12063bd)_
* 檢查資料是否變更時，__資料比較中的型別不符__
過去，儲存物件會在每次沒有任何資料變更的情況下呼叫（適用於任何數值資料欄位，例如int/float/double）。 它會觸發標幟_hasDataChanges設為true並呼叫save函式。 此修正套用後，只有在資料變更時，儲存函式才會呼叫。 int/float/double-check的資料值，其值會傳遞至函式，且會執行嚴格的型別比對。
  _ACP2E-2855 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/57a32313)_
* __[雲端]匯入無法與目錄var__搭配使用
不論檔案名稱為何，產品都能成功匯入。
  _ACP2E-2959 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3a7c4d17)_
* __在ipad mini中，功能表和標題會以行動裝置載入，而應該以桌上型電腦載入。__
系統現在會將寬度為768px的裝置視為桌上型電腦，確保功能表和標題正確載入。 過去，寬度為768px的裝置會視為行動裝置，導致功能表和標題載入行動檢視。
  _ACP2E-2966 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __執行mview cron時發生DDL作業__時發生Base資料表或檢視找不到錯誤
系統現在會在背景執行mview更新時，正確處理資料庫更新作業，避免出現「找不到基底資料表或檢視」錯誤。 以前，如果同時執行檢視更新，某些資料庫更新操作可能會導致「找不到基底資料表或檢視」錯誤。
  _ACP2E-3046_
* __若是外部索引鍵__，透過db_schema.xml修改資料行長度將無法運作
透過宣告式結構描述修改具有外部索引鍵的欄現在不會在MariaDB中產生錯誤
  _ACP2E-3230 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/581b7ef1)_
* __儲存訂單記錄時，會將部分關係記錄儲存至DB__
觸發修復之前不必要的UPDATE查詢，這會影響效能。 修正後，多餘的UPDATE查詢已消除。
  _ACP2E-3361 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1366ae5e)_
* __[雲端]在管理員中，主控台中有許多Javascript錯誤__
之前，在管理面板中，主控台出現許多JavaScript錯誤。 現在，在管理面板中，主控台中沒有JavaScript錯誤，所有預設JavaScript功能將順利執行且不會出現任何問題。
  _ACP2E-3375 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d75cff27)_
* __[雲端] Magento：佇列訊息已刪除__
佇列訊息現在已正確清除。 修正之前，假設正在使用SQL佇列系統，如果清除佇列訊息同時執行，則可能會刪除新訊息。
  _ACP2E-3387 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d50f6b5d)_
* __快取標籤中沒有對應的快取金鑰專案，因此快取清除無法正常運作__
Redis快取記憶體記憶體回收行程現在預設啟用LUA模式，以防止競爭情況
  _ACP2E-3537 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a52ff98f)_
* 已忽略&#x200B;__MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK值__
修正後，設為「false」的ENV變數會視為bool false，而非字串「false」。
  _ACP2E-3681 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/982b1c42)_

### 框架，GraphQL

* __[問題]引入對GraphQL結構描述的自訂純量型別的支援__
系統現在支援GraphQL架構的自訂純量型別，讓開發人員可定義自訂純量型別和實作。 此功能在表達需要驗證的值時特別有用，例如HTML、電子郵件、URL、日期等，以及在更進階的情況下，例如EAV屬性。 之前，系統不支援在GraphQL中處理自訂純量型別。
  _AC-7976 - [GitHub問題](https://github.com/magento/magento2/issues/36877) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/34651) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0574ac23)_

### 框架、產品

* __2.4.8-beta1 EE報告因magento例外狀況而未產生__
  _AC-13011_

### 框架， UI框架

* __可能覆寫設定值，即使它已鎖定__
以前，無法透過bin/magento config：set指令設定設計組態，而且可以透過操作顯示它們的表單來變更鎖定的值。 修正後，從cli使用 — lock-env或 — lock-conf設定的鎖定值無法再更新。
  _ACP2E-3324 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

* 即使標頭值未通過驗證，__Magento_GraphQl也會執行標頭處理__
現在，系統確保只有在標頭值通過驗證時，才執行一次標頭處理，以增強安全性並防止潛在漏洞。 以前，即使標頭值未通過驗證，也會執行標頭處理，由於重複處理標頭值，導致潛在漏洞和意外行為。
  _AC-11729 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8f87c25)_
* __實體Giftcard選項沒有正確的排序順序__
系統現在透過GraphQL查詢時，可以正確排序實體禮卡產品的選項，確保呈現方式與Luma主題一致。 先前，排序順序根據Luma主題不正確，導致顯示和排序選項不正確，例如寄件者姓名、收件者姓名和金額。
  _AC-8951 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bafc571)_
* 建立/編輯/移動/刪除中繼更新時，__[GraphQL]解析器快取失效__
系統現在會確保在建立、編輯、移動或刪除中繼更新時，解析器快取不會失效，但前提是中繼更新已套用至實體。 以前，解析器快取會在套用中繼更新之前過早失效，導致不必要的快取失效。
  _AC-9157 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0c53bbf7)_
* __未針對內容暫存更新清除Fastly快取__
現在，當更新PageBuilder內容相關的實體時，具有PageBuilder內容回應快取的GraphQL會失效。
  _ACP2E-2642 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ba25af8a)_
* __停用階層導覽 — 不會從Graphql__移除彙總
當使用「目錄>分層導覽>顯示類別篩選器」的管理員組態設定時，透過GraphQL查詢請求具有類別彙總的產品搜尋時套用檢查後，問題已獲得修正。
  _ACP2E-2653 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/12e071c3)_
* 包含價格篩選器{from：&quot;0&quot;}的&#x200B;__GraphQL產品通話未傳回任何結果__
先前，使用零價格篩選條件搜尋的graphql產品由於擲回例外狀況，完全沒有傳回任何結果。 現在，搜尋會如預期傳回結果。
  _ACP2E-2928 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c971859e)_
* __個別StoreView的GraphQL API未反映客戶傳回屬性的翻譯__
客戶回訪屬性的翻譯會反映在個別StoreView的GraphQL API中。
先前個別StoreView的客戶傳回屬性不會反映在GraphQL API中。
  _ACP2E-2974 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec7e32a9)_
* 使用節點引號&#x200B;__的getPurchaseOrder的__[&#x200B;雲端]中斷GraphQL呼叫
購買訂單GraphQL呼叫將能夠執行工作，而不會遇到任何內部伺服器錯誤。
  _ACP2E-3128 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6f4805f8)_
* 如果產品未在「所有商店檢視」__中啟用，生產網站中就不會顯示__[&#x200B;雲端]可設定的產品
現在，即使產品未在「所有商店檢視」中啟用，但在特定商店檢視範圍內啟用，系統仍可在網站中正確顯示可設定的產品。
先前，如果產品在「所有商店檢視」中停用，並只在特定商店檢視範圍中啟用，則產品屬性在GraphQL回應中無法正確顯示，導致產品無法正確顯示。
  _ACP2E-3184 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/3f300077)_
* __[Cloud]當相同的簡單產品指派給多個可設定的產品時，產品graphql發生錯誤__
先前，對於具有相同簡單產品的個別可設定產品，grapQL會傳回錯誤。 此修正套用後，不同可設定產品具有相同的簡單產品，grapQL會傳回沒有錯誤的結果。
  _ACP2E-3190 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/148c3ead)_
* 多網站設定中的使用者驗證和跨網站權杖存取出現&#x200B;__[雲端]問題__
多網站設定中的GraphQl客戶資訊和購物車查詢會檢查非預設網站上的客戶是否存在。
先前的查詢可在不確認客戶存在於多網站設定的非預設網站的情況下運作。
  _ACP2E-3215 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/581b7ef1)_
* __GraphQL購物車專案V2分頁無法正常運作__
通過在集合查詢中傳遞目前頁面引數的正確值，已修正此問題。 之前，傳遞錯誤值以設定目前頁面，導致問題。
  _ACP2E-3253 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8459b17d)_
* 取得customerCart __時應指定__[ GRAPHQL]模型值
GraphQL「customerCart」查詢現在可以建立空的購物車，即使報價在資料庫中無法使用。 之前，此作業在建立空白購物車時因為國家/地區驗證問題而失敗。
  _ACP2E-3255 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[GraphQl]願望清單專案可透過GraphQl看到，但不顯示在店面__
透過GraphQL提出請求時，未正確列出的願望清單產品。 現在，願望清單產品會根據提供的商店內容進行篩選。
  _ACP2E-3380 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/55615e61)_
* __[GraphQL]重設內容與主旨/連結之間的密碼電子郵件不一致__
不論網站商店為何，在傳送密碼重設請求時，模擬客戶帳戶註冊的正確商店即可解決此問題。
  _ACP2E-3404 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5184c067)_
* __[雲端]產品GraphQL查詢傳回未指派給目前網站的相關產品__
先前，針對graphQL查詢，多商店相關的產品無法正確針對產品查詢顯示。 套用此修正後，對於產品，graphQL會查詢多存放區相關產品並相應地顯示。
  _ACP2E-3419 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* __在GraphQL標頭中使用錯誤的存放區識別碼會造成嚴重的記憶體錯誤__
在GraphQL請求中傳送錯誤的存放區代碼不會再導致記憶體耗用過多。
  _ACP2E-3447 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d50f6b5d)_
* 在2.4.7 __上對空白Graphql回應的__[ Cloud] 500回應
修正後，無效的graphql請求將不會記錄到exception.log檔案中。
  _ACP2E-3467 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_
* Graphql API有&#x200B;__[Cloud]問題__
在使用Graphql應用程式伺服器修正之前，客戶地址請求未傳回最新資料。
  _ACP2E-3492 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3f12d152)_
* __停用的產品仍然出現在grpahQL查詢中的相關、向上銷售、交叉銷售專案中__
Graphql現在為停用的相關、追加銷售和交叉銷售產品提供正確的回應
  _ACP2E-3505 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_
* __[雲端]： GraphQl錯誤內部伺服器錯誤placeOrder突變__
請求中包含優惠券代碼資訊的「placeOrder」變異不再擲回內部錯誤例外狀況，訂單已成功下達。 之前，它失敗並出現「內部伺服器錯誤」。
  _ACP2E-3647 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/982b1c42)_
* __未針對具有動態價格的套件組合產品計算discount_percentage__
針對product.price_details的discount_percentage新增的修正，無法針對已啟用動態價格且套用折扣券的套件組合產品顯示正確值。
  _LYNX-426_
* 當其中一項捆綁產品無庫存&#x200B;__時，__捆綁產品仍顯示「IN_STOCK」
解決即使其中一個套件產品無庫存，套件產品仍顯示「IN_STOCK」的問題。
  _LYNX-485_
* __not_available_message和only_x_left_in_stock未顯示相同的可用存量__
解決not_available_message和only_x_left_in_stock顯示不一致的庫存可用性的問題
  _LYNX-486_
* __original_row_total欄位傳回錯誤值__
解決original_row_total欄位在選取自訂選項時傳回錯誤值的問題
  _LYNX-488_
* __應根據設定顯示群組的產品縮圖     .__
已解決問題以確保根據配置設定顯示分組的產品縮圖
  _LYNX-503_
* __查詢OrderAddress__中的selected_options時發生錯誤
已將AttributeSelectedOptions更新為custom_attributesV2 (在訂單地址GraphQL回應中)。
  _LYNX-510_
* __original_item_price不包含折扣__
更新original_item_price以包含折扣。
  _LYNX-512_
* __沒有可用的訊息未顯示可用的存貨數量__
解決AddProductsToCart突變的錯誤訊息和錯誤碼，以符合「無法使用」訊息設定
  _LYNX-530_
* __「OUT_OF_STOCK」狀態傳回「簡單，包含自訂選項的產品，包含多重選取選項__」
更新庫存套件中的StockStatusProvider解析程式，以修正具有自訂選項的簡單產品的stock_status。
  _LYNX-532_
* __錯誤(GQL)： cart.itemsV2.items.product.custom_attributesV2傳回伺服器錯誤__
解決當購物車查詢包含產品的自訂屬性時發生的伺服器錯誤，方法是新增沒有任何自訂屬性的產品。
  _LYNX-533_
* __訂單/date_of_first_order一律傳回null__
解決訂單> date_of_first_order一律傳回null的問題。
  _LYNX-536_
* __客戶必須無法取消部分出貨的訂單__
已新增驗證，以限制客戶取消部份出貨的訂單。
  _LYNX-544_
* __根據錯誤訊息取消訂單的錯誤碼__
訂單取消的錯誤碼現在是以特定錯誤訊息為基礎。
  _LYNX-548_
* __將Cookie相關屬性從私人移回受保護的__
將Magento\Framework\App\PageCache\Version類別建構函式屬性的可見性從私有還原為受保護
  _LYNX-581_
* __將預設GraphQL查詢的最大複雜度增加到1000__
將預設的最大GraphQL查詢複雜性從300提高至1000。
  _LYNX-600_
* __GQL - itemsV2 >原始資料列總計，針對具有個別價格之檔案選項的可下載產品，價格範圍價格會傳回$0.00。__
解決已啟用個別連結購買選項的可下載產品針對itemsV2傳回$0 >原始列總計，而針對具有個別價格之檔案選項的產品，傳回的價格範圍為$0.00的問題。
  _LYNX-620_
* __資料表建立時與升級時不同的結構描述__
解決將新的VARCHAR欄新增到現有表格時，由於全新安裝和升級之間的結構描述差異，導致測試失敗的問題。 modifyColumn()方法現在會設定預設字元集和定序，正確處理VARCHAR欄。
  _LYNX-711_
* __PHP-8.4版本__的GraphQl相容性
已修正多個解析器間GraphQL與PHP 8.4的相容性問題，以確保順暢的功能。 更新CatalogRule、Customer、GiftMessage、GiftCard和GiftWrapping模組中受影響的檔案。
  _LYNX-772_

### GraphQL、詳細目錄/MSI

* 當來源和目的地購物車有相同的組合專案時，__MergeCart變異擲回例外狀況__
&#39;-
  _ACP2E-2607 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c971859e) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL、庫存/MSI、效能

* 升級後&#x200B;__網站已關閉__
改善透過GraphQl擷取套件組合產品的效能。
  _ACP2E-1716 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ba25af8a) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL，效能

* __[GraphQL解析器]匯入的客戶解析器資料並未失效__
透過匯入編輯或刪除客戶時，GraphQL客戶解析器快取現在會如預期失效。 之前，快取不會失效，且客戶資料可在匯入期間編輯或刪除。
  _AC-9569 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL，搜尋

* __依多個引數排序的GraphQL產品清單無法運作__
GraphQl中依多個欄位排序的產品現在能如檔案所述運作
  _ACP2E-2809 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c971859e)_
* __產品清單GraphQL查詢限製為僅total_count 10,000個產品__
修正後，搜尋結果不再侷限於10000個產品，即使計數超過10000，仍可取得符合搜尋條件的所有產品。
  _ACP2E-948 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL，測試架構

* __Magento\GraphQl\App\GraphQlCustomerMutationsTest.php整合測試失敗__
&#39;-
  _ACP2E-3363 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4cf5e62)_

### 匯入/匯出

* __當產品匯入時提供自訂選項型別時發生問題： file （建立的產品不包含自訂選項的價格，並且只顯示提供的第一個檔案型別副檔名）__
系統現在會正確匯入具有「檔案」型別自訂選項的產品資料，確保所有提供的副檔名都會顯示，並包含自訂選項的價格。 先前，在產品匯入期間，如果「file」型別的自訂選項有多個副檔名，則只會顯示第一個副檔名，且遺漏自訂選項的價格。
  _AC-12172 - [GitHub問題](https://github.com/magento/magento2/issues/38805) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38926)_
* __匯入歷程記錄網格中匯入作業的執行時間錯誤__
匯入報表執行時間會正確顯示，不受管理員地區設定影響。
  _ACP2E-2710 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ea79f7dd)_
* __使用匯入__以相同電子郵件地址建立的重複客戶
在「帳戶共用」設定為「全域」時匯入客戶，系統會更新系統中存在的匯入客戶。
先前匯入的客戶重複。
  _ACP2E-2737 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c971859e)_
* __在重複可自訂選項的產品上新增/更新匯入__
在產品選項CSV匯入期間，透過將正確的存放區指派給產品選項，此問題已解決。
先前指派給管理員存放區，而非其個別存放區。
  _ACP2E-2902 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3a7c4d17)_
* __客戶「created_at」日期未在匯出時轉換為存放區時區__
「created_at」欄的日期值會根據客戶匯出CSV區段中的商店時區轉換為適當的日期格式。
  _ACP2E-2990 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3056e9cb)_
* __[雲端]使用CSV檢查匯入資料中的資料時發生錯誤__
在CSV匯入期間檢查資料時沒有錯誤。 先前，顯示的錯誤訊息為：「使用管理員的CSV檢查匯入區段中的資料時，我們在列：1中找不到符合此電子郵件和網站代碼的客戶」。
  _ACP2E-3165 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8459b17d)_
* __匯入按鈕遺失__
解決在資料檢查CSV中的正確和不正確記錄後， 「匯入」按鈕遺失的問題。 先前，透過CSV中的正確和不正確記錄檢查資料後，匯入按鈕不顯示。
  _ACP2E-3172 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1819fe73)_
* __無法匯入匯出的客戶地址__
客戶地址匯入將如預期般進行。 先前，如果共用客戶帳戶=全域，則客戶地址匯入檔案不會通過驗證，而且有兩個網站的預設網站具有受限制國家/地區清單，而正在匯入的地址是用於另一個網站的允許國家/地區不同
  _ACP2E-3382 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[雲端] CSV檔案中的錯誤數量未產生錯誤__
現在，庫存來源匯入將會擲回數量欄中非數值的驗證錯誤。 先前，在數量欄中匯入非數值的庫存來源會導致數量設為0。
  _ACP2E-3448 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5b21b7af)_
* __匯入產品時產生的URL金鑰重複錯誤訊息（當URL金鑰已屬於類別__時）不正確
當客戶嘗試匯入產品時（產品的URL金鑰已屬於類別），在產品匯入檢查期間顯示正確的錯誤訊息。
  _ACP2E-3455 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_
* __產品匯出導致OOM即使有4G記憶體限制__
在此修正之前，如果產品屬性具有數千個選項值（即使具有4G可用記憶體），產品匯出會失敗。 此項修正後，產品匯出應會完成csv檔案的匯出。
  _ACP2E-3475 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_
* __[雲端]匯入程式互相干擾__
如果相同的管理員使用者使用相同的使用者工作階段執行兩個或多個匯入操作，則會顯示正確的訊息。
  _ACP2E-3527 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_

### 匯入/匯出，效能

* __[雲端]產品匯入時間已大幅增加__
在此修正之前，包含超過10,000個專案的目錄產品匯入會出現顯著的時間降低。 修正後，會及時執行目錄產品的匯入。
  _ACP2E-3476 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/87d012e5)_

### 安裝與管理

* __Magento升級在MariaDB 11.4 + 2.4.8-beta1__上失敗
升級應該不會發生任何錯誤。
  _AC-13242 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7b336d0a)_
* __管理面板中沒有Varnish 7的匯出VCL按鈕__
「Export VCL for Varnish 7」按鈕已新增至「管理」面板。
  _ACP2E-2102 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_

### 庫存/MSI

* 資料庫使用首碼時，__可設定產品的詳細目錄更新失敗__
現在，當資料庫使用首碼時，系統會正確更新可設定產品的詳細目錄，避免任何錯誤訊息，並確保儲存正確的數量。 以前，如果資料庫使用前置詞，則在嘗試儲存可設定產品中簡單產品的庫存數量時會發生錯誤。
  _AC-10750 - [GitHub問題](https://github.com/magento/magento2/issues/38045)_
* 新增具有屬性的地圖時，__Google google API金鑰無法運作__
系統現在支援最新的Google Maps API 3.56版，可讓使用者從PageBuilder功能表成功將地圖內容區塊新增到舞台，不會發生任何錯誤。 之前，由於Google地圖API版本的相容性問題，使用者無法新增地圖內容區塊，導致出現「發生錯誤」錯誤訊息。
  _AC-11593 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0574ac23)_
* __無法為具有多個來源且SKU損毀的訂單專案建立出貨__
之前，當透過資料庫錯誤地在SKU中新增空格時，會導致出貨頁面發生錯誤，該錯誤現在已修正，並且自動修剪被視為人性化的錯誤，未找到任何影響。因此，出貨已成功建立。
  _AC-13922 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/c18eb5fa)_
* __[測試]在商店前方顯示存貨為0的套件組合產品__
套件組合產品未使用其他庫存顯示於其他網站上。
  _ACP2E-1411_
* __[雲端]產品清單的關鍵問題包含空白空間__
當產品設定為「無庫存」時，系統現在可正確顯示產品清單，不含空白字元，確保可用產品顯示一致且準確。 之前，將產品設為「無庫存」會導致產品清單中出現空白字元，中斷版面配置，並可能讓客戶感到困惑。
  _ACP2E-2794 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ea79f7dd) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/b59e48ca)_
* __啟用MSI取貨商店時無法送出訂單__
改善存貨效能，可建立出貨方案，以備有眾多店內取貨來源時使用
  _ACP2E-3335 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/9f3e63d1)_
* __Cron重新索引無法在前端更新產品可用性__
先前，透過REST API更新延期交貨狀態後，產品在前端保持無庫存。 現在，透過REST API更新延交訂單狀態後，產品會以庫存顯示。
  _ACP2E-3355 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/e6fe0aa7)_
* __啟用MSI時，將影像新增至可設定的功能無法運作。__
使用詳細目錄模組時，可設定產品的影像上傳現在會如預期運作。 先前無法上傳影像
  _ACP2E-3357 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/fdf409aa)_
* 清除M2.4.7-p3 __中的套件組合產品+ MSI有__個問題
先前，對於與相同簡單產品重複之後的庫存套件產品，無法儲存簡單產品。 套用此修正後，簡單產品便可順利儲存，不會有任何例外。
  _ACP2E-3470 - [GitHub問題](https://github.com/magento/magento2/issues/39358) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/0208e433)_

### 庫存/MSI、搜尋

* __未將SKU設為可搜尋屬性時，所有產品都會以[is_out_of_stock] = 1編制索引__
修正後，即使無法搜尋sku，目錄搜尋索引中的「is_out_of_stock」也是正確的。
  _ACP2E-3413 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5b21b7af)_

### 訂購

* __後端訂單總覽畫面：訂單料號層次__上未顯示延期交貨數量
系統現在會在後端訂單概要畫面的「數量」欄位中顯示延期交貨料號的數目。 這可確保使用者可以準確地追蹤順序中所有專案的狀態。 以前，「數量」欄位只會顯示已訂購、已開立商業發票及已出貨的料號數目，而不會顯示延期交貨的料號數目。
  _AC-10828 - [GitHub問題](https://github.com/magento/magento2/issues/38252) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38320)_
* __[問題]訂單位址轉譯器__中使用的存放區識別碼錯誤
系統現在會在轉譯訂單位址時，正確使用與訂單相關聯的商店ID，確保位址會根據其各自的商店ID正確格式化。 先前，系統未正確使用目前的商店ID，若需要傳送來自不同商店的多份訂單電子郵件，可能導致地址格式不正確。
  _AC-10994 - [GitHub問題](https://github.com/magento/magento2/issues/38412) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37932)_
* __加入處理器快取問題__
系統現在會正確地將聯結處理器套用至每個反複專案，即使連續呼叫亦然，確保資料擷取準確。 以前，JoinProcessor錯誤地標籤為已在連續反複專案中套用，導致資料擷取錯誤。
  _AC-11690 - [GitHub問題](https://github.com/magento/magento2/issues/27504) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37550)_
* __[問題]送貨價格在列印的pdf__中顯示不同的價格
系統現在會根據稅捐組態設定，以列印的PDF正確顯示出貨價格，確保銷售訂單商業發票檢視頁面與列印商業發票之間的一致性。 以前，無論稅捐組態設定為何，列印PDF中顯示的運費都會排除稅捐。
  _AC-11798 - [GitHub問題](https://github.com/magento/magento2/issues/38608) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38595) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bafc571)_
* __使用已刪除的父可設定產品重新排序__
現在，使用已刪除的產品重新排序時，系統不會顯示要重新排序的重新排序按鈕
  _AC-13839 - [GitHub問題](https://github.com/magento/magento2/issues/39568) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39601)_
* __[問題]修正錯誤\Magento\Sales\Model\Order\Email\Container\Template：：$id屬性__
這會修正\Magento\Sales\Model\Order\Email\Container\Template：：$id的錯誤phpdoc，實際上$id是type int，但實際上是string。
  _AC-13924 - [GitHub問題](https://github.com/magento/magento2/issues/39151) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39150)_
* __無法在現有訂單詳細資料中儲存電話號碼的變更__
現在，使用者可以在訂單地址的電話欄位中新增國際首碼00
  _ACP2E-2622 - [GitHub問題](https://github.com/magento/magento2/issues/38201) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/12e071c3)_
* __電子郵件無法傳送__
系統現在包含設定選項async_sending_attempts ，以指定在停止前嘗試傳送電子郵件的次數，改善啟用「非同步傳送」時失敗的電子郵件傳送處理。 先前，如果電子郵件無法傳送，系統會持續嘗試重新傳送，導致系統記錄中出現無休止的錯誤訊息回圈。
  _ACP2E-2734 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b2286ecf)_
* 部份出貨訂單退款時，__[雲端]訂單狀態已變更為完成__
當簽發銷退折讓單時，如果料號尚未出貨，則訂單狀態不再變更為「已完成」。
  _ACP2E-2756 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7e0e5582)_
* __[雲端]無法停用從管理員UI傳送電子郵件，因為開發檔案顯示__
現在，系統可正確防止在電子郵件通訊停用時傳送銷售電子郵件。 重新啟用電子郵件通訊時，將不再傳送這些電子郵件。 以往，在電子郵件通訊停用時起始的銷售電子郵件，在電子郵件通訊重新啟用後仍會傳送。
  _ACP2E-3002 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8931218)_
* __未全額退款的訂單已結__
當具有未擷取付款的訂單已建立出貨時，系統現在會正確維護訂單狀態為「處理」，而商業發票狀態為「暫緩」。 這可確保在全額退款後只將訂單標籤為「已結」。 先前，若為具有待處理商業發票的訂單建立出貨，則會錯誤地將訂單狀態變更為「已關閉」。
  _ACP2E-3045 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6a185204)_
* __[Cloud]若未設定預設帳單地址，則無法在一個商店的admin中建立訂單__
現在，相關的錯誤訊息「具有相同電子郵件地址的客戶已存在於相關網站中。」 如果客戶沒有預設帳單地址，但嘗試在其他商店建立訂單，則會顯示訂單。
  _ACP2E-3311 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d75cff27)_
* __已傳送管理員重複下單要求__
以前，您可以按多次管理面板中的「提交訂單」按鈕，或重複按下「Enter」鍵來啟動，導致重複提交或提交訂單時發生錯誤。 現在，會防止其他動作，直到完全處理完訂單為止，確保只提交一個訂單。
  _ACP2E-3416 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5184c067)_
* __即使沒有付款方式，管理員仍然可以下訂單__
現在當付款方式重新出現在可用付款清單中時，會保留先前選取的付款方式。
  _ACP2E-3425 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d50f6b5d)_
* 當我們從Admin建立訂單後，在 — Mozilla Firefox瀏覽器&#x200B;__上複製了__個專案
在Admin中建立訂單時，使用「依SKU新增產品」新增的產品在Firefox中不再重複。
  _ACP2E-3518_

### 訂單，付款

* __即使沒有付款方式，管理員仍然可以下訂單__
以往，商家不需選取付款方式，即可從管理員面板下訂單。 現在，商家需要一種付款方式才能繼續下訂單。
  _ACP2E-3233 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fd5cf3af)_

### 訂購，退貨

* __訂單退款導致重複銷退折讓單__
當同時執行兩個相同的請求時，透過REST API發出退款將不再建立重複的「銷退折讓單」。
  _ACP2E-2982 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a4fbf702)_

### 訂購，稅金

* __[CLOUD]啟用跨境交易並套用優惠券折扣時，RESTFUL訂單API中的base_row_total不正確__
現在，當啟用跨境交易並套用優惠券折扣時，會從RESTFUL訂單API傳回正確的base_row_total。
  _ACP2E-3003 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9af794a4)_

### 其他

* __[Braintree]退款線上儲存交易為transactionid-refall__
  _BUNDLE-3394_
* __[Braintree] + [雲端] Braintree （信用卡）訂單無法分割費用__
  _BUNDLE-3421_
* __[Braintree] [雲端]Braintree SSL憑證將於6月30日前到期__
  _BUNDLE-3422_
* GQL查詢中傳回&#x200B;__private_content_version Cookie__
修正GraphQL查詢中傳回private_content_version Cookie （即使工作階段Cookie已停用）的問題。 工作階段如預期般停用時，GraphQL回應中不再包含Cookie。
  _LYNX-339_
* __實體禮卡查詢中電子郵件prop的伺服器錯誤__
修正實體禮品卡上sender_email和recipient_email查詢導致伺服器錯誤的問題。 這些Prop現在可正確傳回虛擬禮品卡，且查詢行為一致。
  _LYNX-366_
* CartItemInterface中的&#x200B;__is_available屬性對於可設定的產品一律傳回false__
修正CartItemInterface中的is_available屬性針對庫存中可設定產品一律傳回false的問題。 現在，在適用的情況下，它會將可用性正確反映為true。
  _LYNX-380_
* CartItemInterface中的&#x200B;__is_available屬性會傳回true，即使可銷售存貨低於產品數量__亦然
修正CartItemInterface中的is_available屬性不正確地傳回true （即使購物車專案數量超過可銷售存貨）的問題。
  _LYNX-382_
* ProductInterface中的&#x200B;__only_x_left_in_stock屬性在可設定的產品上不準確__
修正ProductInterface中only_x_left_in_stock屬性未正確反映購物車中可設定產品變體的可用庫存的問題。 現在，only_x_left_in_stock值正確對應至實際變動存貨層次，確保在Cart GQL查詢中傳回正確的存貨資料。
  _LYNX-395_
* __當簡單產品新增到分組產品內的購物車時，會傳回預留位置縮圖__
修正將簡單產品（分組產品的一部分）新增到購物車時，即使產品已指派影像，仍會傳回預留位置縮圖影像的問題。
修正詳細資料：
* 產品縮圖現在可以正確顯示指派的影像（若有）。
* 縮圖選取專案依照下的管理員設定：
商店>設定>銷售>結帳>購物車>分組產品影像。
這可確保根據商店設定分組產品的一致縮圖行為。
  _LYNX-399_
* __客戶的自訂選項屬性無法使用整數值__
修正當傳回值為整數時，客戶的自訂選項屬性無法運作的問題。 自訂選項現在可正確處理並按預期傳回整數值。
  _LYNX-400_
* __嘗試取得具有動態價格的套件組合產品的priceDetails時發生內部伺服器錯誤__
解決透過GraphQL查詢具有動態定價的套件組合產品的price_details時，導致內部伺服器錯誤的問題。 此增強功能使用設定了動態定價的套件組合產品時，可確保穩定的購物車查詢。
  _LYNX-402_
* 可設定產品的&#x200B;__only_x_left_in_stock一律傳回0__
解決使用具有選項的父SKU新增可設定產品時，only_x_left_in_stock屬性一律傳回0的問題。
修正詳細資料：
* only_x_left_in_stock值現在會正確反映所選子變體而非父SKU的庫存。
* 這可確保在購物車和產品頁面中針對可設定的產品變化正確顯示庫存量。
  _LYNX-403_
* __GraphQL錯誤：可自訂選項查詢__中不支援的「檔案」型別
修正GraphQL針對購物車專案中的型別「檔案」的可自訂選項傳回錯誤的問題。 現在，查詢可正確傳回所有可自訂選項型別的詳細資料，包括檔案型選項，而不會導致錯誤。
  _LYNX-405_
* __GraphQL查詢未傳回可自訂產品的正確計算正常價格__
修正GraphQL未傳回可自訂產品的正確計算正常價格的問題。 現在，查詢會正確包含計算出的正常價格，並在價格屬性中套用可自訂的值（例如$125），以反映基本價格和任何其他自訂成本。
  _LYNX-411_
* 透過EstimatedTotals的&#x200B;__AppliedTaxes會持續存在更新的變動__
修正即使更新地區或郵遞區號後，購物車仍持續存在套用稅捐的EstimatedTotals突變問題。 現在突變會在地區與郵遞區號值之間變更時，正確更新套用的稅捐，確保根據目前的購物車資料，僅套用正確的稅捐規則。
  _LYNX-412_
* CartItemInterface中的&#x200B;__is_available屬性會傳回true，即使可銷售存貨低於產品數量__亦然
修正CartItemInterface中的is_available屬性不正確地傳回true的問題，即使可銷售存貨低於請求的產品數量亦然。 現在，當產品的數量超過可用庫存時， is_available欄位會正確傳回false 。
  _LYNX-420_
* __無法新增優惠券至購物車，只提供運費折扣__
修正優惠券無法套用至購物車僅限運送折扣的問題。 使用不含產品條件的銷售規則時，抵用券現在可正確套用至出貨金額，確保將預期折扣套用至出貨成本。
  _LYNX-421_
* __產品正常價格，12位小數且值錯誤__
修正當套用多個稅率時，product.price_range.maximum_price和minimum_price GraphQL路徑中的regular_price值不符合目錄價格的問題。 regular_price現在會一致地反映所有稅捐組態的型錄價格，確保「購物車摘要」中的單位訂價、總列成本計算及折扣檢查正確無誤。
  _LYNX-425_
* 購物車上的&#x200B;__GraphQL伺服器錯誤（捆綁產品無庫存）__
修正在擷取購物車時，GraphQL傳回內部伺服器錯誤的問題，該購物車包含具有無庫存專案的捆綁產品，尤其是當查詢包含itemsV2屬性時。 GraphQL現在會如預期正確傳回專案清單，並將相關的錯誤訊息附加至隨附的產品專案專案。
  _LYNX-430_
* __無法建立具有自訂屬性的位址__
修正createCustomerAddress突變的問題，此突變無法以必要的自訂屬性建立地址。 變異現在會在提供適當的裝載時，正確處理自訂位址屬性。
  _LYNX-441_
* 隨附產品上只有_x_left_in_stock的購物車發生&#x200B;__GraphQL伺服器錯誤__
修正了擷取購物車時，購物車中包含GraphQL查詢中具有only_x_left_in_stock欄位的捆綁產品，導致內部伺服器錯誤的問題。 GraphQL現在會正確傳回only_x_left_in_stock欄位的浮點數或null，而不會出現錯誤。
  _LYNX-447_
* 移除購物車&#x200B;__中其他可設定產品不足的產品時，__GraphQL發生錯誤
修正了當購物車也包含庫存不足的可設定產品時，嘗試從購物車移除庫存產品會導致「請求數量無法使用」GraphQL錯誤的問題。 移除現在可如預期運作，不會觸發錯誤。
  _LYNX-464_
* __因為SKU的變異區分大小寫，所以無法新增產品__
解決使用具有不同大小寫的SKU時，addProductsToCart突變傳回「PRODUCT_NOT_FOUND」錯誤的問題。 變異現在會以不敏感的方式處理SKU，確保與目錄服務查詢和PDP行為一致。
  _LYNX-469_
* __Product attribute > trademark short form &amp;amp；trade；傳回為&amp;amp；trade；__
解決GraphQL API產品名稱中的字元編碼問題
  _LYNX-603_
* __updateCustomerEmail突變問題__
解決updateCustomerEmail突變的問題，此問題導致沒有必要自訂屬性的客戶（在建立帳戶後新增）無法更新其電子郵件。
  _LYNX-619_
* 使用pickup_location_code __時，__突變setShippingAddressesOnCart擲回錯誤
修正使用pickup_location_code而未指定customer_address_id或address時，setShippingAddressesOnCart突變傳回錯誤的問題。 變異現在可正確設定只包含pickup_location_code的送貨地址。
  _LYNX-626_
* __CustomerOrder.items_eligible_for_return清單必須與訂單專案__一致
解決訂單中退貨資格的不一致：
1. CustomerOrder.items_eligible_for_return清單現在與實際訂單料號一致。
2. 若已傳回完整數量，OrderItemInterface.eligible_for_return欄位會正確傳回false。
3. CustomerOrder.items_eligible_for_return現在只包含尚未在退回處理中的料號。
   _LYNX-627_
* __新增quantity_return_requested欄位__
將quantity_return_requested欄位新增至OrderItemInterface，讓您識別已提交退貨的料號數量。 這樣會增強現有quantity_returned欄位的回訪追蹤功能。
  _LYNX-628_
* __所有專案全部建立退貨之後，訂單可用動作不得包含RETURN__
修正GraphQL customer.orders查詢中available_actions欄位在為所有專案建立完整退貨後錯誤包含RETURN的問題。 現在當傳回程式完成後，就會正確移除RETURN動作。
  _LYNX-634_
* __店面相容性 — 更新邏輯以取得含有前置詞的資料表名稱以及其他次要的改善專案__
更新邏輯以擷取含有首碼的表格名稱（與SCP變更相關）。
  _LYNX-637_
* 使用setBillingAddressOnCart GQL的same_as_shipping欄位&#x200B;__時，__儲存在通訊錄中無法運作
修正使用setBillingAddressOnCart GraphQL突變（將same_as_shipping欄位設為true）時，傳送地址未儲存至客戶通訊錄的問題。 現在，送貨地址已如預期正確儲存。
  _LYNX-643_
* __標準化變動中的order_id__
標準化order_id的變動輸入，並更新訂單取消確認電子郵件範本，以公開增量id而非訂單id。
  _LYNX-650_
* __CustomerOrder未顯示訂單評論__
解決CustomerOrder的問題，在訪客和客戶訂單GraphQL查詢中包含訂單評論。
  _LYNX-651_
* __original_item_price不得包含任何折扣__
更新GraphQL購物車專案價格中original_item_price的邏輯，以排除折扣。
  _LYNX-652_
* 當其中一項捆綁產品無庫存&#x200B;__時，__捆綁產品仍顯示「IN_STOCK」
解決即使其中一個套件專案無庫存，套件產品的product.stock_status仍顯示「IN_STOCK」的問題。
  _LYNX-681_
* 如果客戶的已刪除自訂屬性值存在，__客戶查詢傳回內部伺服器錯誤__
修正當刪除的自訂屬性仍有儲存值時，客戶查詢傳回內部伺服器錯誤的問題。 現在，如果要求不存在的屬性，則會傳回適當的錯誤訊息。 刪除客戶自訂屬性時，必要的快取會失效。
  _LYNX-686_
* 傳回和取消確認連結的&#x200B;__動作引數__
已針對傳回和取消確認電子郵件相關連結新增動作引數
  _LYNX-687_
* __訪客使用者確認URL已重新導向至訂購狀態頁面，因為它遺失orderRef （針對GuestRMA）__
新增orderRef引數至來賓RMA確認電子郵件中的連結
  _LYNX-688_
* __訪客使用者確認URL已重新導向至訂購狀態頁面，因為它遺失orderRef__
新增orderRef引數至來賓訂單取消確認電子郵件中的連結
  _LYNX-689_
* __RMA停用時客戶查詢發生問題__
更新GraphQL邏輯，確保即使全域停用RMA，仍可存取先前建立的傳回。 已移除錯誤訊息以改善店面UX，確保客戶仍可檢視其過往回報。
  _LYNX-690_
* __套用衝突優惠券時，__GraphQL未傳回更新的購物車資料
修正套用優先順序較高的衝突抵用券時，導致錯誤訊息未傳回更新購物車資料的問題。 現在，當新的抵用券使現有抵用券失效時，突變會正確傳回套用有效抵用券的購物車。
  _LYNX-696_
* __無法為placeOrder GQL__上不可為空的欄位「TaxItem.title」傳回null
修正因不可為空的欄位TaxItem.title為null值而導致placeOrder突變失敗並出現內部伺服器錯誤的問題。 現在，欄位一律會傳回有效值，確保成功下訂單。
  _LYNX-699_
* __EstimateTotals：虛擬產品型別的折扣為Null__
解決將折扣代碼套用至包含虛擬產品的購物車時，estimateTotal突變針對折扣傳回null的問題。
  _LYNX-702_
* __組合產品未傳回正確的折扣百分比與金額__
針對型錄料號價格，已引入新屬性「catalog_discount」及「row_catalog_discount」，以便在資料列與單一料號層次顯示正確的折扣金額與百分比。
  _LYNX-703_
* 產品等級&#x200B;__上的__禮品訊息設定
修正全域停用時，未在產品層級套用禮品訊息的問題。 現在，如果針對特定產品啟用贈品訊息，則可使用updateCartItems變異來成功新增贈品訊息，且將正確地儲存和反映贈品訊息。
  _LYNX-714_
* __從購物車專案移除禮品包裝時發生問題__
修正使用updateCartItems突變從購物車專案移除禮品包裝未如預期運作的問題。 現在，套用和移除贈品包裝的功能皆正確無誤。
  _LYNX-717_
* __符合的註冊客戶功能在Boilerplate中無法運作，需要為來賓啟用trackViewedProduct突變。__
公開trackViewedProduct突變，以追蹤客戶和來賓的產品檢視事件
  _LYNX-751_
* 如果沒有套用作用中的購物車規則，__cart.rules查詢傳回錯誤而非空白陣列__
修正cart.rules查詢的問題，該查詢在沒有套用作用中購物車規則時傳回空陣列，而非錯誤。
  _LYNX-757_
* __擷取購物車專案的贈品包裝時發生問題__
更新擷取邏輯，以便在全域停用但在產品層級啟用時，傳回購物車專案的贈品包裝選項
  _LYNX-758_
* 安裝adobe-commerce/storefront-compatibility套件時，使用OPTIONS方法的&#x200B;__GraphQL呼叫傳回500回應代碼__
修正安裝adobe-commerce/storefront-compatibility套件時，使用OPTIONS方法的GraphQL呼叫傳回500內部伺服器錯誤的問題。 端點現在會如預期正確傳回200/204回應。
  _LYNX-778_

### 其他開發人員工具

* __[問題] visual.phtml中的HTML語法錯誤__
系統現在會正確關閉visual.phtml檔案中的開始標籤，確保採用正確的HTML語法。 之前，啟動標籤未正確關閉，導致HTML語法錯誤。
  _AC-10658 - [GitHub問題](https://github.com/magento/magento2/issues/38247) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37457)_
* __[問題]在bin/magento maintenance：status命令__中將「作用中」變更為「已啟用」
系統現在為維護模式命令提供更準確的狀態訊息，將狀態從「作用中」變更為「已啟用」，以及從「非作用中」變更為「已停用」。 之前，維護模式命令的狀態訊息會顯示為「作用中」或「非作用中」，這可能會造成混淆。
  _AC-11474 - [GitHub問題](https://github.com/magento/magento2/issues/38486) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38410)_
* __在類別樹狀結構中導覽會導致Redis中出現錯誤：「Redis工作階段超過並行連線」__
  _AC-12571 - [GitHub問題](https://github.com/magento/magento2/issues/38851) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0611e750)_
* 與dev/css/use_css_critical_path結合的&#x200B;__CSP問題__
系統現在會在結帳頁面上以非同步方式正確載入CSS檔案，即使啟用「dev/css/use_css_critical_path」設定亦然，確保這些頁面以正確的CSS樣式呈現。 以前，受限的內容安全性原則(CSP)會導致內嵌JavaScript無法執行，導致CSS檔案無法如預期載入。
  _AC-12731 - [GitHub問題](https://github.com/magento/magento2/issues/39020) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39040)_
* __使用虛擬型別來設定外掛程式，無法在`setup:di:compile`命令__中正確產生攔截器方法
系統現在會在使用虛擬型別來設定外掛程式時正確產生攔截器方法，確保不論是預先編譯還是執行階段編譯，結果都一致。 以前，與執行階段編譯相比，系統會在預先編譯時產生不正確的結果。
  _AC-13398 - [GitHub問題](https://github.com/magento/magento2/issues/33980) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38141)_
* __無法從資料收集器下載檔案__
下載備份不再顯示空白頁面而非下載檔案。
  _ACP2E-3441_
* __Adobe Commerce 2.4.7-p3單元測試失敗__
不需要發行說明。
  _ACP2E-3631 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/982b1c42)_

### 付款/付款方式、訂單

* __儲存供日後使用的紙幣付款流程信用卡詳細資料未顯示在儲存的付款方式頁面__
先前的Payal Payflow儲存供稍後使用的信用卡詳細資料未顯示在儲存的付款方式頁面上，而現在固定信用卡詳細資料顯示在儲存的付款方式頁面上。
  _AC-13699 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/96dec499)_

### 付款

* __信用卡（付款流程連結）付款無法運作__
較早取得錯誤（拒絕付款），在成功下訂固定訂單後，使用信用卡下訂單。
  _AC-13414 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a68324bc)_
* __Payflow每次在檢視交易畫面上按一下擷取按鈕時，都會建立新交易__
現在，每次在檢視交易畫面上按一下擷取按鈕時，系統都會正確擷取交易資訊，而不會建立新的付款交易。 先前，按一下「擷取」按鈕會錯誤地為已支付的訂單建立新的付款交易。
  _ACP2E-2841 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b2286ecf)_
* 加拿大Paypal商家帳戶的&#x200B;__Paylater訊息未顯示在PDP中__
現在系統會在產品詳細資料頁面(PDP)上正確顯示加拿大PayPal商家帳戶的PayLater訊息，而可從帳戶帳單地址或出貨來決定買方的國家/地區。 以前，由於缺少引數，不會顯示PayLater訊息，這會導致瀏覽器主控台發生錯誤。
  _ACP2E-3028 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6a185204)_
* __PayPal訂單退款導致重複銷退折讓單__
修正PayPal付款服務IPN建立的銷退折讓單並行處理的問題。
  _ACP2E-3143 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d01ee51e)_
* __購物車價格規則不適用於Paypal__
以付款方式套用折扣時，PayPal端會顯示正確的金額
  _ACP2E-3163 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7377de59)_
* 具有特定角色的&#x200B;__[雲端]使用者無法登入__
角色只包含PayPal區段存取權的管理員使用者現在可以順利登入
  _ACP2E-3208 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/66dea0de)_

### 效能

* __預設產品屬性設定問題__
系統現在可讓使用者取消選取產品屬性的預設選項，確保該屬性並非總是有預設集。 先前，一旦設定了產品屬性的預設值，就無法取消選取該屬性，導致屬性一律會有預設集。
  _AC-11932 - [GitHub問題](https://github.com/magento/magento2/issues/38703) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7d5e3906)_
* __[問題]程式碼清理並新增重要標題區塊，並將重要css移至資產之前__
系統現在包含新的關鍵標題區塊，並在資產之前移動關鍵CSS，允許在前端進行更多自訂和效能最佳化。 過去，關鍵CSS並不位於資產之前，限制了自訂和最佳化機會。
  _AC-12000 - [GitHub問題](https://github.com/magento/magento2/issues/38748) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/35580)_
* __當mysql主機包含連線埠資訊時，主題編譯中斷__
系統現在可以正確處理包含連線埠資訊的MySQL主機組態，確保主題編譯成功。 以前，如果資料庫連線中的MySQL主機組態包含連線埠資訊，主題編譯將會失敗。
  _AC-12176 - [GitHub問題](https://github.com/magento/magento2/issues/38799) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38842)_
* __支援Magento CLI中的Symfony CommandLoaderInterface__
這項變更允許延遲初始化命令，以縮短Magento CLI應用程式的初始化時間，直到需要命令為止。
  _AC-13471 - [GitHub問題](https://github.com/magento/magento2/issues/29266) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/29355)_
* __在購物車規則中載入產品屬性時出現效能問題__
改善銷售規則的查詢效能 — 從大約150毫秒提升至一位數ms。
  _ACP2E-2494 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ba25af8a)_
* __部分索引效能價格__
透過最佳化索引過程中使用的一些刪除查詢，已改善價格部分索引效能。
  _ACP2E-2673 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ba25af8a)_
* 使用非同步訂單處理+條款與條件時，__多存放區設定拒絕訂單__
系統現在會處理來自啟用條款與條件之非預設網站的訂單。
在自動拒絕之前。
  _ACP2E-2850 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/57a32313)_
* __Order Rest API呼叫需要很長時間才能執行__
系統現在會在合理的時間範圍內執行Order Rest API呼叫，以提升擷取大量訂單時的效能。 先前，Order Rest API呼叫執行時間過長，導致擷取大量訂單時發生延遲。
  _ACP2E-2910 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/001e5188)_

### 績效、促銷活動

* __銷售規則索引器已停止執行__
系統現在即使有大量合併的篩選器群組，仍可成功完成銷售規則索引器，確保購物車規則條件能如預期套用至購物車。 以前，當合併的篩選器群組數量很大時，銷售規則索引子將無法完成，導致出現錯誤訊息並阻止套用購物車規則條件。
  _ACP2E-2617_

### 定價

* __Magento2.4.6-p4訂單API簡單專案遺漏價格__
系統現在會在透過Order API查詢時正確顯示簡單產品的價格，確保資料呈現準確。 先前，簡單產品的價格在API回應中錯誤地顯示為零。
  _AC-11810 - [GitHub問題](https://github.com/magento/magento2/issues/38603)_
* 目錄規則&#x200B;__中有__尾數舍入錯誤
  _AC-13855 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/276e0acd)_

### 產品

* __可設定之關聯產品名稱中的特殊字元正在轉換成HTML實體。__
系統現在會在編輯可設定產品時，正確保留關聯產品名稱中的特殊字元，以防止這些字元轉換為HTML實體。 先前，在編輯可設定產品時，關聯產品名稱中的特殊字元會轉換為HTML實體。
  _AC-10535 - [GitHub問題](https://github.com/magento/magento2/issues/38146) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38447)_
* __ProductRepository函式GetById未建立正確的快取金鑰__
系統現在會在ProductRepository的GetById函式中正確建立快取索引鍵，無論儲存ID是以字串還是整數傳入。 這可確保在後續呼叫時從記憶體中擷取產品，進而改善效能。 以前，由於不正確的快取金鑰建立，系統會在每次呼叫函式時從資料庫擷取產品，即使引數相同。
  _AC-10947 - [GitHub問題](https://github.com/magento/magento2/issues/38384) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38433)_
* __[問題] [MFTF]已新增AdminClickAddOptionForBundleItemsActionGroup__
系統現在包含AdminClickAddOptionForBundleItemsActionGroup，增強管理面板的功能。 之前，無法使用此動作群組。
  _AC-11992 - [GitHub問題](https://github.com/magento/magento2/issues/30857) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/30838)_
* __[問題]修正PHPDoc區塊中的錯字__
系統現在可以正確移除$helper變數宣告中PHPDoc未知的參考變數，提高程式碼清晰度和準確性。 先前，PHPDoc中這個未知的參考變數會造成程式碼中的混淆和潛在的不準確性。
  _AC-13173 - [GitHub問題](https://github.com/magento/magento2/issues/38961) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38940)_
* __[問題]修正Magento >= 2.4.7__中的無效套件組合和可下載產品頁面配置
已修正套件組合及可下載產品頁面的版面配置，確保所有裝置顯示方式一致且正確。 先前，由於產品資訊媒體區塊重新排列，這些頁面會遇到版面問題。
  _AC-13423 - [GitHub問題](https://github.com/magento/magento2/issues/39403) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __AlertProcessor — 引數#2數($storeId)必須是int型別，字串必須是__
系統現在會透過確保商店識別碼為正確的資料型別，正確觸發產品警報電子郵件。 以前，由於商店識別碼中的型別不符，不會傳送產品警報電子郵件。
  _AC-5969 - [GitHub問題](https://github.com/magento/magento2/issues/35602) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0574ac23)_
* __[雲端] addFilterToMap函式無法用於某些資料行__
現在，自訂模組可用於順序格線中。 先前使用自訂模組時發生錯誤。
  _ACP2E-2944 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3a7c4d17)_
* 類別中的&#x200B;__[雲端]產品 — 新增產品 — 指派 — 全選__
使用者現在可以使用切換開關來選取或取消選取產品。
  _ACP2E-3471_

### 促銷活動

* 從邀請建立帳戶時看不到&#x200B;__客戶屬性__
從邀請建立帳戶時，可以使用客戶屬性。
  _ACP2E-2602 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/39d54c2d)_
* __未釋出每個優惠券使用次數限制的優惠券代碼以進行付款失敗，訂單取消__
系統現在會在建立或取消訂單時立即更新優惠券使用方式，並將規則使用方式新增到佇列中，以防止潛在的死結。 這可確保釋放具有「每張優惠券的使用次數」限制的優惠券代碼，並且可在訂單因付款失敗而取消時重複使用。 之前，系統未發行優惠券代碼以供在此類情況下重複使用，導致出現錯誤訊息，指出優惠券代碼無效。
  _ACP2E-2627 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c971859e)_
* __[雲端]重新索引目錄規則產品索引器擲回SQLSTATE[HY000]：一般錯誤： 2006 MySQL伺服器已消失。__
系統現在可正確處理「Magento\CatalogRule\Model\Indexer\IndexBuilder」在di.xml中的自訂「batchCount」值，以防止在目錄規則產品索引器重新索引期間，由於大型目錄上的批次大小不正確，出現「一般錯誤： 2006 MySQL伺服器已消失」等SQL錯誤
  _ACP2E-2811 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b2286ecf)_
* 訪客客戶區段的&#x200B;__[雲端]購物車價格規則未在購物車上套用折扣__
現在，即使規則未使用抵用券，系統仍可對訪客客戶區段正確套用購物車價格規則，以確保將適當的折扣套用至購物車。 之前，除非購物車價格規則使用抵用券，否則不會將折扣套用至訪客客戶區段的購物車。
  _ACP2E-2926_
* __在相關產品規則的「產品相符」索引標籤中缺少「Type」屬性__
「Type」屬性現在可在「相關產品規則」模組的「要比對的產品」索引標籤中作為篩選選項使用，允許更精確的規則定義。 之前，「要比對的產品」索引標籤中缺少此屬性，這會限制建立準確比對准則的能力。
  _ACP2E-3024_
* 具有折扣數量步驟（購買X）屬性的&#x200B;__銷售規則導致未套用其他規則__
如果購物車中的產品數量不足以套用規則，購物車價格規則不會取消先前套用的規則。
  _ACP2E-3139 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d01ee51e)_
* __購物車價格規則上的效能問題 — 進階銷售規則模組__
新增AdvancedSalesRule篩選器的遺漏DB索引
  _ACP2E-3331_
* __以固定金額折扣和「套用數量折扣上限」發放銷售規則__
修正購物車規則折扣的問題，當購物車設定為套用有限產品數量的固定金額折扣時。 先前，「套用折扣數量上限」值是用來計算購物車中目前專案的價格，而非僅用於計算規則的折扣。
  _ACP2E-3332 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/581b7ef1)_
* __[雲端] Magento升級導致優惠券區分大小寫__
修正前，您必須輸入與設定完全相同的抵用券代碼，並考量大寫或小寫。 現在，無論程式碼設定是大寫還是小寫，都將在後端驗證抵用券。
  _ACP2E-3342_
* __購物車規則「整張購物車的固定金額折扣」  動作套用折扣不正確__
從管理區域建立訂單時使用抵用券代碼時，無論大小寫為何，都能正確驗證。 之前，如果優惠券代碼與設定購物車規則代碼的字母大小寫不符，系統不會驗證優惠券代碼。
  _ACP2E-3349 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/581b7ef1)_
* __在後端，產品屬性的預設存放區值（而不是預期的管理員值）__
現在在後端，會使用管理員值，而非產品屬性的預設商店值。
  _ACP2E-3374 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5184c067)_
* __新增套件組合產品時，購物車規則「整個購物車的固定金額折扣」動作套用折扣不正確__
捆綁產品未正確套用固定數量的購物車規則。 現在，在計算總折扣金額時，會考慮捆綁子產品，從而產生適當的折扣計算。
  _ACP2E-3377 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1366ae5e)_
* __購物車價格規則計算折扣錯誤__
目前正在正確計算固定金額折扣。 修正前，套件組合產品的固定金額折扣總計不正確。
  _ACP2E-3403 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0b488dd1)_
* __規則條件中的巢狀類別未顯示__
修正層級3類別的巢狀類別未顯示在類別條件的行銷規則中的問題
  _ACP2E-3406 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/88660e79)_
* __usage_limit和uses_per_customer未在salesrule_coupon資料表__中更新
更新購物車價格規則中的每張優惠券使用情形和每名客戶使用情形，現在將影響現有的自動產生優惠券。 以前，新值只影響新抵用券
  _ACP2E-3432 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/88660e79)_
* __當購物車價格規則使用「等於或大於」條件時，未將父類別列入考量。__
現在，當在進階條件中使用購物車價格規則時，會正確考慮父類別
  _ACP2E-3456 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/93359343)_
* __優先順序的折扣計算無效__
在套用至整個購物車折扣型別的固定金額的情況下，金額未正確針對先前促銷已折扣的購物車專案計算。 現在，折扣總和已相當恰當。
  _ACP2E-3463 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_
* __[雲端]送貨計算未考慮購物車規則__
在此修正之前，具有地區條件的購物車規則未一致地套用。 修正後，正確套用具有區域條件的購物車規則。
  _ACP2E-3472 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_
* __發票的購物車規則SKU條件失敗。__
具有動態價格的組合產品折扣現在會正確反映在發票中。 以前，折扣不會反映在發票上。
  _ACP2E-3491 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3f12d152)_
* __當同時套用多個購物車價格規則時若同時套用折扣/特價產品，則折扣值不正確__
在此修正前，如果套用多個購物車規則，則整個購物車規則的固定金額未正確套用。 現在，已正確套用固定金額折扣購物車規則。
  _ACP2E-3498 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1984c61c)_

### 傳回

* __[雲端]受限制的管理員使用者可以看到傳回功能表和按鈕__
受限管理員使用者現在無法存取與RMA相關的控制項（功能表和按鈕）。
先前受限制的管理員使用者可以看到傳回功能表和按鈕。
  _ACP2E-3330_
* 重新整理熒幕時，__傳回熒幕發生問題__
使用者可以重新整理頁面，而不會遇到熒幕扭曲的情況。
  _ACP2E-3443_

### SEO

* __以重音符號新增URL重寫會造成無限載入__
系統現在已成功建立並功能具有重音的URL重寫，以防止在儲存過程中無限載入。 之前，以重音符號新增URL重寫會造成無限載入問題。
  _AC-11907 - [GitHub問題](https://github.com/magento/magento2/issues/38692) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/44cef3a9)_
* __第三層級類別的多重存放區錯誤類別URL重寫__
使用自訂範圍的url索引鍵為具有父系的子系產生正確的url重寫
  _ACP2E-2641 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ea79f7dd)_
* 產品名稱欄位中的&#x200B;__雙位元組字元（特殊字元）會封鎖後端中的產品建立__
已新增一項設定，可讓您將音譯套用至產品URL。 設定可在以下位置使用：商店>設定>目錄>目錄>搜尋引擎最佳化：「為產品URL套用音譯」
  _ACP2E-2770 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b2286ecf)_
* __在一個商店群組中建立多個商店的url_rewrite專案不正確__
在此修正之前，您只能在編輯產品時在網站層級產生URL重寫。 修正中引進了新的設定（商店>設定>目錄>目錄>搜尋引擎最佳化，「產品URL重寫範圍」搭配選項「商店檢視」、「網站」），可讓您在商店檢視或網站層級產生URL重寫。
  _ACP2E-3383 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2d627301)_

### 銷售

* 如果已套用第一個購物車規則，則不套用&#x200B;__第二個購物車價格規則__
  _AC-13751_

### 搜尋

* __取得[輸入搜尋字詞，然後再試一次]。 2.4.8-beta1__中店面的進階搜尋頁面發生錯誤
產品屬性設為「否」時，系統現在會在「進階搜尋」頁面上正確顯示搜尋結果。 以前，將產品屬性設定為「否」並執行搜尋會導致錯誤訊息，「請輸入搜尋詞並再試一次。」
  _AC-13053 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ea26621)_
* __magento/module-open-search依存於不存在的opensearch-php分支__
  _AC-13721 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/05dc0bbf)_
* __search_query資料表若為大型時，對載入時間前端有巨大影響__
改善搜尋清單頁面載入時間。 修正前，搜尋清單頁面因未最佳化的查詢而延遲。
  _ACP2E-3362 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/55615e61)_

### 安全性

* __[問題]遺失字型CSP付款器快顯視窗__
系統現在允許載入字型&#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;，而不違反內容安全性原則指示，以確保正確顯示播放器快顯視窗。 先前，由於違反內容安全性原則指示，導致播放器快顯視窗顯示問題，因此拒絕載入字型。
  _AC-11855 - [GitHub問題](https://github.com/magento/magento2/issues/38624) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37401)_
* __[問題]更新js.js DOM文字重新解譯為HTML__
藉由使用innerText，這可避免HTML插入的風險，因為這些屬性會自動逸出所提供文字中的任何HTML特殊字元。 此修正將輸入視為純文字而非解譯的HTML，有助於防止跨網站指令碼(XSS)漏洞。
  _AC-12035 - [GitHub問題](https://github.com/magento/magento2/issues/38767)_
* __ReCaptcha V2在德文語言的簽出時顯示不正確__
先前，來自結帳電子郵件地址下方的recaptcha對長字的語言（例如德文）顯示為無樣式。 之後，recaptcha看起來會像其他區域的所有recaptcha元素一樣。
  _ACP2E-3273 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7377de59)_
* __管理員登入時的驗證碼不需要與某些使用者互動__
用於管理員登入的ReCaptcha已如預期驗證
  _ACP2E-3300 - [GitHub程式碼貢獻](https://github.com/magento/security-package/commit/8f64ab3c)_

### 送貨

* __[問題]修正tracking.phtml中的錯字 — 將JS函式的&quot;currier&quot;重新命名為&quot;carrier&quot;__
現在，系統在順序追蹤範本中使用的JavaScript處理常式功能中，正確使用「carrier」一詞，而非拼錯的「currier」，以確保正確功能命名和程式碼清晰度。 先前，我們使用拼字錯誤的辭彙「currier」，這可能會導致程式碼基底的混淆和不一致。
  _AC-10757 - [GitHub問題](https://github.com/magento/magento2/issues/34523) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33414)_
* __UPS REST「出貨不能以KGS/IN、LBS/CM或OZS/CM作為測量單位」__
請確定結帳和購物車中應該顯示UPS費率。
  _AC-11938 - [GitHub問題](https://github.com/magento/magento2/issues/38618) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/493e01f5)_
* __UPS REST在devdoc__中的「沙箱」和「prod」安裝指示更新
  _AC-12938_
* __[問題]客戶地址的變數拼字正確__
系統現在會正確拼寫客戶地址的變數，以確保前端帳戶區域的正確顯示。 以前，這些變數的拼字錯誤可能會導致本機程式碼審查期間發生錯誤。
  _AC-13172 - [GitHub問題](https://github.com/magento/magento2/issues/32817) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32815)_
* __追蹤視窗顯示錯誤的預期傳送日期__
顯示Fedex承運人的正確交貨日期。
  _ACP2E-2738 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/57a32313)_
* 即使套用免運費，仍顯示&#x200B;__表格費率__
現在會顯示表格費率送貨方法，即使套用優惠券後可使用「免運費」
  _ACP2E-2763 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b2286ecf)_
* __MFTF測試AdminCreatingShippingLabelTest失敗，因為Jenkins環境中未新增認證__
mftf測試修正
  _ACP2E-2765 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ea79f7dd)_
* __FedEx追蹤API不使用REST認證__
先前，FedEx整合不需要額外的API金鑰即可追蹤API。 現已新增新設定，以支援追蹤API金鑰。
  _ACP2E-3340 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] FedEx交涉費率未在REST__上傳回
在修正之前，FedEx帳戶特定的費率未在回應時傳送，即使根據FedEx檔案他們本應傳送也一樣。 修正後，帳戶特定費率會透過變更我們這邊的請求在回應中傳送。
  _ACP2E-3354 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/55615e61)_

### 測試和預覽

* __如果原本是由執行更新所新增，則未儲存排定的更新設定__
現在，當在目前執行的更新中修改此類屬性時，系統會在後續排程更新中正確清除產品屬性值。 先前，當產品屬性被執行的排程更新修改時，無法在建立新的排程更新時清除此類屬性值，這要求使用者在建立後重新編輯它們。
  _ACP2E-2901_
* __開始日期和結束日期的購物車價格規則未與中繼更新同步__
日期會根據「購物車價格規則分段」的更新儲存。
  _ACP2E-2999_
* 中繼預覽&#x200B;__中出現__JS錯誤
現在form-mini-stub.js檔案已成功載入，開發人員工具中沒有任何Js語法錯誤。
  _ACP2E-3104_
* __無法更新產品特殊價格階段內容__
系統現在允許在價格更新促銷活動開始後編輯其結束日期，以確保使用者可以對其促銷活動進行必要的調整。 先前，嘗試更新作用中行銷活動的結束日期時擲回錯誤，導致使用者無法進行變更。
  _ACP2E-3162_
* 使用唯一自訂類別屬性時，__無法更新排定的更新__
修正類別具有唯一屬性時，無法更新類別排程更新的問題
  _ACP2E-3453 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_

### 目標定位

* __[問題]允許在維護允許清單中使用CIDR範圍__
系統現在支援在維護模式允許IP清單中使用CIDR範圍，啟用一系列IP位址以略過維護模式。 以前，維護模式僅允許IP清單允許個人IP地址繞過維護模式。
  _AC-9432 - [GitHub問題](https://github.com/magento/magento2/issues/37943) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/30699)_

### 稅金

* __[問題] Feature/php8.1建構函式屬性升級wee圖形ql__
將模組中的所有屬性全部取代為建構函式屬性升級wee graph ql：
  _AC-13295 - [GitHub問題](https://github.com/magento/magento2/issues/39309) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36975)_
* __固定產品稅(FPT)無法使用可設定的產品__
可設定產品變體的FPT可正常運作。
  _ACP2E-3193 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec7e32a9)_

### 測試架構

* __整合測試因JSON資料行型別而失敗testDbSchemaUpToDate__
系統現在可在整合測試期間正確辨識資料庫結構描述中的JSON欄型別，避免因資料庫結構描述與宣告式結構描述不符而導致測試失敗。 以前，系統錯誤地將JSON欄型別識別為MariaDB中的LONGTEXT，導致整合測試失敗。
  _AC-11654 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ef81f5a2)_
* __[問題] PHPDoc更正拼字__
由於PHPDoc中的拼字校正，系統現在可以正確辨識IDE中已棄用的方法。 之前，PHPDoc中的拼字錯誤會導致IDE無法辨識某些已棄用的方法。
  _AC-13362 - [GitHub問題](https://github.com/magento/magento2/issues/31399) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/31398)_
* __MAGETOW-95118：在工作階段過期後，檢查永久購物車的行為__
  _AC-13478 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7d5e3906)_
* __整合測試失敗Magento\NegotiableQuote\Controller\Quote\DownloadTest：：testCompanyManagerDownloadWithNQSubPermission__
  _AC-13716_
* __[資料庫比較]如果資料庫包含無條件的Target規則相關記錄，會發生嚴重錯誤__
先前若資料庫包含目標規則的記錄，且沒有任何條件，則會發生嚴重錯誤，但修正後資料庫比較工具順利通過且沒有嚴重錯誤。
  _AC-13722_
* __修正靜態測試，以啟用協力廠商擴充功能的使用方式__
  _AC-13848 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9e383b4d)_
* 在執行期間或記錄檔中未顯示&#x200B;__[內部]夾具套用失敗__
&#39;-
  _ACP2E-3334 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d4de4726)_
* __[MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest__
固定mftfs
  _ACP2E-3458 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/078c387e)_

### UI框架

* __Prototype.js安全性弱點修正CVE-2020-27511__
系統已更新，以解決Prototype.js 1.7.3中的安全性弱點CVE-2020-27511，加強系統的整體安全性。 在此更新之前，系統可能會因為移除精心製作的HTML標籤而遭受規則運算式拒絕服務(ReDOS)攻擊。
  _AC-12128 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Grunt Less使用pub/前置詞作為sourcemaps__
使用grunt時，系統現在為路徑產生較少/css來源地圖（不含/pub前置詞），因此不需要在Web伺服器設定中進行因應措施。 之前，在原始碼對應路徑中使用/pub首碼時，需要在Web伺服器中指定特定的設定才能正常運作。
  _AC-12189 - [GitHub問題](https://github.com/magento/magento2/issues/38837) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38840)_
* __Ui元件檔案欄位__
系統現在可以正確驗證UI元件表單中的檔案欄位，以在選取檔案時提交表單而不會發生錯誤。 以前，即使選擇了檔案，驗證也會失敗，阻止表單提交。
  _AC-12432 - [GitHub問題](https://github.com/magento/magento2/issues/38908) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39004)_
* __[問題] js主控台中的日期格式已改良：從12小時切換為24小時……__
改進js控制檯中的日期格式：從12小時切換至24小時
  _AC-12645 - [GitHub問題](https://github.com/magento/magento2/issues/38983) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38972)_
* __[問題]在開發人員模式中為較少的檔案新增sourceMap產生__
系統現在會在開發人員模式中產生較少檔案的來源對應，更易於識別樣式的來源。 以前，在較少伺服器端編譯的開發人員模式下執行系統時，要識別樣式的來源非常困難。
  _AC-12650 - [GitHub問題](https://github.com/magento/magento2/issues/38982) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38977)_
* __正在為已停用的模組部署靜態內容__
系統現在會從最終CSS輸出檔案中排除與已停用模組相關的CSS，以確保不會載入不必要的樣式。 以前，與已停用模組相關的CSS會包含在最終的CSS輸出檔案中，導致載入額外且不必要的樣式。
  _AC-1306 - [GitHub問題](https://github.com/magento/magento2/issues/24666) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32922)_
* __以最低庫存臨界值排序時，「無庫存」中的行為不一致__
系統現在會根據庫存量來正確排序目錄中的產品，遵守設定的「最小庫存量臨界值」，並一致地將無庫存專案移至清單底部。 先前，排序行為不一致，專案根據其庫存量並非總是以正確順序出現，而且在儲存、重新整理或修改類別階層後，排序的變更可能無法預測地發生。
  _AC-13459 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47b448e2)_
* __針對require.js載入問題改善錯誤報告的建議__
此PR可改善必要專案無法載入元件時的錯誤訊息。
  _AC-13472 - [GitHub問題](https://github.com/magento/magento2/issues/36761) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38971)_
* __PHP 8.4淘汰錯誤導致2.4-develop__中的組建失敗
  _AC-14004 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1da9ba6f)_
* __[問題]請勿在前端載入後端區塊內容__
系統現在會確保前端不會載入後端區塊內容，以防止建立不必要的後端工作階段和潛在的工作階段鎖定。 以前，系統在前端錯誤載入後端區塊內容，導致建立後端工作階段和潛在的工作階段鎖定。
  _AC-9007 - [GitHub問題](https://github.com/magento/magento2/issues/37617) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36368)_
* __[問題]移除不必要的指令碼檢閱摘要__
系統現在會從評等區段移除不必要的JavaScript指令碼，藉此最佳化頁面載入時間，而非使用內嵌CSS樣式，以獲得更有效且可讀的程式碼。 以往，針對評分割槽段使用JavaScript指令碼可能會導致頁面載入時間變慢。
  _AC-9168 - [GitHub問題](https://github.com/magento/magento2/issues/37776) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/34643)_
* __啟用Recaptcha時檢查禮品卡餘額時發生例外狀況__
使用者將可以在檢視和編輯購物車畫面中擷取禮品卡餘額。 以往，啟用reCAPTCHA時不會顯示這些詳細資料。
  _ACP2E-2529 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_
* __[說明]功能要求ADA合規性__
系統現在會移除不支援的CSS屬性，並以print.css檔案中支援的屬性取代，以確保ADA法規遵循。 以往，使用不受支援的CSS屬性會導致瀏覽器相容性問題。
  _ACP2E-2729 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud] AC 2.4.4-p8__的effect-drop.js中的混淆程式庫程式碼
系統現在可以正確實作effect-drop.js程式庫，確保jQuery UI效果正常運作。 之前，effect-drop.js程式庫錯誤地以effect-clip.js程式庫覆寫，導致jQuery UI效果可能發生問題。
  _ACP2E-3061 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/35b1b1da)_
* __網站頁首 | 特殊字元打斷客戶歡迎區段__
修正後，特殊字元可在客戶歡迎區段中正確顯示。
  _ACP2E-3367 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1366ae5e)_
* __客戶區段版本因日期範圍而失敗__
如果只編輯了一個日期，則可以使用日期範圍條件儲存客戶區段。
  _ACP2E-3561 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a52ff98f)_
