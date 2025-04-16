---
source-git-commit: 934fe621356c45bcefd2f84b7d01986b4995b061
workflow-type: tm+mt
source-wordcount: '28390'
ht-degree: 0%

---
# Adobe Commerce已修正問題(v2.4.8)

## 已修正v2.4.8中的問題

我們已修正Adobe Commerce 2.4.8核心程式碼中的582個問題。 此版本中包含的已修正問題子集說明如下。

### API

* _AC-10042_： /V1/transactions REST API在parent_txn_id = txn_id時傳回錯誤
   * _修正附註_：系統現在會正確處理父項交易ID與交易ID相同的父項和子項概念交易，避免在查詢/V1/transactions REST API端點時發生無限回圈。 以前，此情況會導致嚴重錯誤，因為超過最大執行時間。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_： 2.4.7中的[Graphql]型別問題
   * _修正附註_：系統現在會在執行GraphQL查詢時，正確處理GetCustomSelectedOptionAttributes函式中的整數值，避免任何與型別相關的錯誤。 之前，啟動使用具有整數引數的GetCustomSelectedOptionAttributes的GraphQL查詢會導致型別錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38662>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38663>
* _AC-3223_：類別url_key中的特殊字元（透過REST API建立時）
   * _修正附註_：修正後在category_url_key中找不到特殊字元，它在category_url_key中顯示特殊字元
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35577>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2703_：顯示其他網站訂單的REST API。 
   * _修正附註_：系統現在支援REST API管理員權杖和Magento_Sales端點的範圍授權存取，確保REST API僅顯示管理員有權存取的訂單。 以前，無論管理員使用者指派的網站為何，REST API都會顯示所有網站的訂單。
* _ACP2E-2755_：啟用2FA Duo後rest api發生問題
   * _修正附註_：含Duo安全性選項的2FA現在會產生Rest API的正確簽章
   * _GitHub程式碼貢獻_： <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_： [REST API]：為可設定的產品新增組態後，在存放區檢視中使用預設值不會維持勾選狀態
   * _修正附註_：確保非預設存放區之可自訂選項的資料庫專案正確無誤，已修正問題。 由於資料庫專案不正確，即使自訂商店的選項標題與預設商店相同，「管理員>目錄>產品編輯>可自訂選項」區段中自訂商店的核取方塊先前未勾選。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_：使用Oauth1時，REST API無法在SKU中以斜線(/)提出要求
   * _修正備註_：修正前，您無法對SKU中具有「/」的產品進行成功的API呼叫。 現在，即使其SKU中有正斜線，您仍可以發出成功的API取得產品詳細資料的要求。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_：如果啟用「validateDefaultAddress」，透過REST API更新時，客戶地址更新失敗
   * _修正附註_： API裝載中遺失ID金鑰的問題解決後，API端點現在可如預期運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_： [Cloud]在層級價格Api中建立重複的網站群組價格客戶群組。
   * _修正附註_：現在Tier Price Rest Api不允許建立Duplicate網站群組價格客戶群組。
之前，您可以在層級價格Api中建立重複網站群組價格客戶群組，以免在產品儲存期間透過管理員驗證。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_：無法透過REST API新增具有狀態的訂單註解
   * _修正附註_：若訂單狀態僅來自目前狀態，則允許變更訂單狀態，此問題已解決。 之前，它不會遵循訂單狀態並防止任何訂單狀態中的變更，即使它來自相同狀態亦然。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_：承載中缺少SKU時，非同步作業失敗
   * _修正附註_：如果承載中缺少sku，則非同步和同步作業先前會因產品儲存錯誤而失敗。 修正後，非同步和同步產品儲存rest api作業會失敗，並顯示相關的例外訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_： [CLOUD]無法使用REST API更新基本價格（「catalog_product_entity_decimal」中的「value_id」值未正確增加。）
   * _修正備註_：先前在此修正中，呼叫rest api /rest/default/V1/products/base-prices時，增量ID錯誤地增加，導致值之間出現間隙。 修正後，增量ID會依預期遞增。 此外， value_id欄位範圍也增加了。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_：訂單專案不會顯示在API POST V1/order/：orderId/refall的銷退折讓單電子郵件中
   * _修正備註_：以前，在此修正之前，當客戶從通知send_email的API請求建立銷退折讓單時，它不包含產品詳細資料格線。 此修正套用後，客戶傳送銷退折讓單API請求，並會找到出現在電子郵件中的產品專案詳細資料。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
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

### API、GraphQL、稅務

* _AC-12060_：僅提供郵遞區號時，Luma (Rest API)和Graphql都不會計算稅額。
   * _修正備註_：系統現在只提供郵遞區號時，就能正確計算稅捐，確保Luma (Rest API)和GraphQL的稅捐預估正確無誤。 以前，只提供郵遞區號時，只會計算運費預估，而不包含稅金。

### 帳戶

* _AC-10782_：客戶地址表單允許在名稱欄位中使用隨機碼
   * _修正附註_：系統現在會驗證客戶地址表單中「名字」和「姓氏」欄位的輸入，避免使用隨機代碼。 之前，系統允許在這些欄位中使用隨機程式碼，而不會擲回錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38331>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38345>
* _AC-10886_：管理員密碼更新。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38352>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_：儲存時我的帳戶新增位址當機
   * _修正附註_：系統現在即使未顯示地區欄位，仍可正確儲存客戶地址，避免在儲存過程中當機。 先前，嘗試新增或編輯沒有顯示區域欄位的地址會導致例外錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38406>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38407>
* _AC-11718_：當URL大寫時重新導向回圈
   * _修正附註_：系統現在會自動將URL中的大寫字元轉換為小寫，以防止在存取首頁時發生重新導向回圈。 先前，在安全性基底URL中加入大寫字元會在嘗試存取首頁時造成持續的重新導向回圈。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38538>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38539>
* _AC-11755_： middlename(&#39;s)未儲存給來賓帳戶
   * _修正附註_：系統現在會在結帳時正確儲存來賓帳戶的中間名，使其可在電子郵件範本中存取。 之前，中間名未儲存在報價表中，且無法在來賓帳戶的電子郵件範本中存取。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38593>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39067>
* _AC-11919_：管理員：頁面動作按鈕會向左浮動，而非向右
   * _修正附註_：系統現在會將「頁面動作」按鈕正確地對齊管理面板中粘性標題的右側，強化專業的外觀和風格。 以前，這些按鈕錯誤地浮動到粘性標題的左側。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38701>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_： magento 2.4.7中有`dev:di:info`個錯誤
   * _修正備註_：系統現在會在執行`dev:di:info`命令時正確顯示建構函式引數，避免發生任何錯誤。 以前，執行此命令會導致錯誤，因為引數中的型別不相符。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38740>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_：以客戶選擇加入身分登入核取方塊無法翻譯
   * _修正附註_：系統現在允許在「商店檢視」範圍中設定「以客戶身分登入」核取方塊和「以客戶身分登入」核取方塊工具提示」欄位，以啟用不同商店檢視的翻譯。 之前，這些欄位僅在「網站」範圍設定，無法翻譯個別商店檢視。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32329>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32359>
* _AC-14299_：我的設定檔下拉式清單中的前端UI首頁按鈕不存在。（斷斷續續）
* _AC-6071_：客戶已登入，但在前端顯示404錯誤。
   * _修正附註_： storefront客戶儀表板頁面現在會在客戶登入時依預期載入。 客戶以前可以登入，但此頁面顯示404錯誤。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35838>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_：無法在管理員編輯客戶區段中儲存客戶屬性資訊；
   * _修正附註_：現在已針對管理員客戶編輯表單的網站範圍，正確實作客戶的商店ID。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3115_： [雲端]啟用私人銷售時，無法透過API建立客戶
   * _修正附註_：現在客戶可由已驗證的管理員使用者建立，並在啟用網站限制時，透過REST API使用已驗證的整合權杖建立。
* _ACP2E-3329_：登入後，無法看到以訪客使用者身分新增至比較清單的產品。
   * _修正附註_：登入前已新增至產品比較清單的產品（以客戶身分登入）現在會在登入後保留。
先前，登入後，無法顯示以訪客使用者身分新增至比較清單的產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_：允許國家設定導致客戶地址設定發生問題
   * _修正附註_：現在選取[允許國家/地區]組態不會影響針對指定範圍以外顯示的國家/地區。 先前允許國家/地區組態影響指定範圍以外的客戶地址屬性
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_：共用禮品登入會將事件日期顯示為1天前
   * _修正附註_：店面現在已正確顯示贈品註冊日期
* _ACP2E-3501_： VAPT：商業邏輯錯誤 — 未來日期作為客戶出生日期
   * _修正附註_：客戶的出生日期不能設定在今天之後
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>

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
* _AC-11427_： [問題]行銷規則中屬性的標籤不一致
   * _修正附註_：系統現在會以一致的方式為購物車價格規則中的類別和屬性選項填入標籤
   * _GitHub問題_： <https://github.com/magento/magento2/issues/31232>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/31231>
* _AC-11588_：資料驗證成功，且在具有取代行為的匯入產品期間出現匯入按鈕
   * _修正附註_：系統現在會正確驗證資料，並在產品匯入程式期間以「取代」行為隱藏「匯入」按鈕，以防止任何非預期的資料取代。 以前，系統錯誤地驗證資料並顯示「匯入」按鈕，導致潛在的資料不一致。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_： [錯誤] Magento 2.4.7不允許產品像片的副檔名為大寫字母。
   * _修正附註_：系統現在接受具有大寫字母副檔名的產品影像上傳，以確保順利的產品建立程式。 之前，以大寫字母副檔名的影像上傳遭到拒絕，迫使使用者將副檔名變更為小寫。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38831>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_：在網格中隱藏的下拉式清單，具有選取的動作（例如「內容>元素>頁面」）
   * _修正附註_：現在系統已修正所有網格的所有類似下拉式清單。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38891>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39371>
* _AC-13131_： [問題]修正警告：未定義的陣列機碼「篩選器」
   * _修正附註_：系統現在會處理新使用者尚未與書籤互動的情況，防止記錄未定義的陣列索引鍵「篩選器」警告。 以前，當新使用者未與書籤互動時，系統會記錄此警告。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39013>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38996>
* _AC-13529_：因為Validate.php檔案中的程式碼變更，導致含有特殊字元的產品匯入csv檔案失敗
   * _修正備註_：系統現在可以正確驗證及匯入包含特殊字元的產品CSV檔案，允許成功傳輸資料。 先前，嘗試匯入包含特殊字元的產品CSV檔案會導致錯誤，阻礙匯入程式。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_：當「密碼重設要求數目上限」設定大於0時，例如： 3 ，「超過限制錯誤訊息會在重新達到限制之前傳送，即從第二次開始
* _AC-13768_：雖然「密碼重設要求數目上限」已設為0 （已停用） ，但「從第2次傳送超過限制的錯誤訊息」
* _AC-13850_：必要的電話號碼欄位沒有紅色星號
   * _修正附註_：電話號碼未顯示較早的紅色星號，但是  電話號碼是強制性的。 現在已修正紅色星號，可在電話號碼上顯示為強制欄位。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c699c206>
* _AC-14300_：在Admin中，當我們嘗試重新排序提交訂單按鈕時，無法點選。 （斷斷續續）
* _AC-6975_： [問題]將預設索引子模式設定為「排程」
   * _修正備註_：所有新索引子預設為&#x200B;**[!UICONTROL Update by Schedule]**&#x200B;模式。  先前預設模式為&#x200B;**[!UICONTROL Update on Save]**。 現有的索引器不受影響。 [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36419>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_： [問題]在mview取消訂閱上卸除索引子變更記錄檔表格
   * _修正備註_：系統現在會在索引從「依排程更新」切換為「儲存時更新」時，自動移除未使用的變更記錄檔表格，將索引標籤為無效，以確保不會遺漏任何專案。 以前，將索引切換為「儲存時更新」會在系統中保留未使用的變更記錄檔表格，並將所有變更的索引標籤為「有效」。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/29789>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/25859>
* _AC-7962_：在行動電話檢視中結帳付款時，沒有運送連結
   * _修正附註_：系統現在可確保結帳標題/連結「送貨」和「檢閱與付款」一律顯示在行動檢視的頁面頂端，讓使用者能夠輕鬆地在步驟之間導覽，並進行必要的更正。 先前，這些標題/連結隱藏在行動檢視中，讓使用者難以瞭解他們目前的步驟或回到先前的步驟。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36856>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36982>
* _AC-8109_：客戶訂單查詢出貨註解created_at傳回時區為+0，不在商店設定的時區內
   * _修正附註_：使用客戶「訂單」查詢時，系統現在會正確顯示客戶設定時區中出貨註解的「created_at」欄位。 以前，「created_at」欄位會顯示在+0時區，無論客戶的時區設定為何。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36947>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37642>
* _AC-9843_： i18n：collect-phrases中斷翻譯完整性
   * _修正附註_： `bin/magento i18n:collect-phrases -o`命令現在可以正確從JavaScript和.phtml檔案收集並新增新片語，確保翻譯檔案能正確反映翻譯。 以前，系統無法在翻譯檔案中包含來自JavaScript檔案的多行翻譯短語以及來自.phtml檔案的短語，導致翻譯不完整或不正確。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2687_：存取動態區塊的許可權問題
   * _修正附註_：先前針對受限制的管理員新增動態區塊時擲回錯誤。 實作此修正後，受限制的管理員可以成功新增動態區塊，並編輯區塊沒有任何錯誤
* _ACP2E-2787_：存放區檢視名稱中的縮寫符號已取代為&#39;
   * _修正附註_：格線的存放區檢視篩選器現在會正確顯示單引號
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38395>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_： Favicon上傳無法驗證.ico檔案
   * _修正附註_：檔案驗證錯誤已更新為「檔案驗證失敗」。 請驗證存放區設定中的影像處理設定。」 以前只是「檔案驗證失敗」。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_： PageBuilder中的相簿顯示舊的影像縮圖，而非新上傳的影像
   * _修正附註_：透過頁面產生器內容中的媒體集，重新產生已刪除及重新上傳之相同名稱影像的影像預覽。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/60140cd2>，<https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_：由具有不同角色範圍的管理員使用者儲存產品會覆寫/刪除產品中現有的相關產品資訊
   * _修正備註_：之前，修正前，當次要管理員使用者按一下「儲存」按鈕，而相關產品未變更時，相關產品會重設並變成空白。 此項修正後，次要管理員使用者按一下儲存按鈕，產品未重設且儲存成功。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_：無法匯出超過200個訂單
   * _修正附註_：為了修正問題，將GET的HTTP要求變更為POST，已略過先前提交之選定ID的要求大小伺服器限制。 之前，由於GET請求大小的伺服器限制，因此會發生問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_：結帳頁面驗證訊息不正確。
   * _修正附註_：如果任何必要欄位留空（例如「位址」），伺服器端驗證將不會顯示訊息。 使用者端驗證將確保必填欄位錯誤通知出現，指出「這是必填欄位」。 以前，如果任何必填欄位留空，除了使用者端驗證訊息之外，還會顯示「需要地址」訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_：管理員使用者的密碼重設範本問題
   * _修正附註_：問題已透過使用正確金鑰解決，現在電子郵件範本中包含管理員使用者名稱，並正確完成主旨。 以前，該問題源自所使用的過時的鍵值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_：客戶區段URL中有雙斜線
   * _修正附註_：在格線中按一下「重設篩選器」時，URL中不會出現雙斜線。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_： COD不適用於允許的特定國家/地區
   * _修正附註_：現在只要有需要，且允許的特定國家/地區可以使用「貨到付款」   AC-3216如預期運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_：無法更新自訂建立的訂單狀態
   * _修正備註_： &#39;
我們現在可以更新自訂建立的訂單狀態，而先前只有在目前狀態為「處理」或「詐騙」時，才能變更狀態。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38659>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_：送貨地址狀態不是自動更新
   * _修正備註_：修正前，送貨地址區域（或區域識別碼）與地址帳單資訊不同步。 現在，帳單地址資訊變更時，送貨地址區域和區域ID都會正確更新。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_：重設按鈕在新增/編輯管理員使用者上無法運作
   * _修正附註_：之前，在[新增/編輯管理員使用者]頁面上，[重設]按鈕無法運作。 現在，在「系統 — >許可權 — >所有使用者」下的「管理員」面板中，「新增/編輯管理員使用者」頁面上的「重設」按鈕將正確運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_： Magento管理員URL路由錯誤偵測與CORS錯誤
   * _修正附註_：修正後，如果自訂管理網域是主網域的子網域，則只能從設定的子網域存取管理員。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37663>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
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
   * _修正附註_：之前，在管理面板中以生產模式啟用JavaScript縮制，導致瀏覽器主控台中出現與TinyMCE 6相關的JavaScript錯誤，影響功能和使用者體驗。 現在，此問題已解決，確保TinyMCE 6順利運作，不會產生任何錯誤，即使JS縮制已啟用。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_：要求其他變更以完全完成ACP2E-3375修正
   * _修正備註_： &#39;-
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_：自動啟用新的ACL許可權
   * _修正附註_：新增至自訂模組的許可權將不再自動授與存取所有現有使用者角色，除非明確設定。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_：管理動作記錄使用者報告未顯示adminhtml_user_delete的詳細資料
   * _修正附註_： adminhtml_user_delete現在會正確記錄重要詳細資料。 以前，不會為使用者刪除產生記錄。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_：從管理員下訂單時未套用送貨條件的購物車規則
   * _修正附註_：以前，如果購物車價格規則具有附帶優惠券的送貨方式折扣，則無法透過管理員UI套用。 套用此修正後，系統將會從管理員UI成功套用特定送貨方法的購物車價格規則折扣及優惠券。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a52ff98f>，<https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_： [FRESH] HEX程式碼未在色票中正確更新
   * _修正附註_：使用者在視覺色票檢色器中手動輸入的HEX代碼不再由系統變更。 以前，由於色彩模型之間的轉換錯誤，某些HEX程式碼會經歷一些細微的調整。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/344fce23>，<https://github.com/magento/inventory/commit/1ef984c0>

### 管理員UI、B2B

* _AC-13628_： B2B登入作為客戶標題仍具有Magento品牌
   * _修正附註_：店面標題先前顯示「您現在在&lt;店面名稱>上以&lt;客戶名稱>連線」並帶有Magento品牌。 此問題現已修正，且標題會顯示為ADOBE品牌。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/96dec499>

### 管理UI，目錄

* _ACP2E-2708_：無法以受限制的管理員使用者身分變更允許網站中類別產品的位置
   * _修正附註_：允許受限管理員使用者在受限網站下指派的根類別所包含的類別下，新增及排序產品。

### 管理員UI、付款/付款方法、訂單

* _AC-13520_： PayPal智慧型按鈕順序後，交易授權未顯示在[交易]索引標籤中
   * _修正附註_：使用PayPal智慧型按鈕下訂單後，系統現在會在「交易」標籤中正確顯示交易授權。 以前，在按一下「授權」按鈕後，授權交易未出現在Transaction標籤中，並且未建立「授權」型別的新交易。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>

### 管理員UI、效能

* _ACP2E-3169_：更新至2.4.5-p8後，從管理員建立訂單時發生500錯誤
   * _修正附註_：先前，啟用HTML縮制時，無法下管理員的訂單。 現在，啟用HTML縮制後，管理員的訂單就可以成功下達。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>

### 管理UI，運送

* _ACP2E-2519_：優惠券代碼計數不會在   如果訂單是多次出貨，則會顯示「管理優惠券代碼」標籤中的「使用時間」欄。
   * _修正附註_：先前當以多筆運送方式下訂單時，在[管理優惠券代碼]索引標籤的[使用時間]欄中，優惠券代碼計數未更新。 現在，正確計數會顯示在兩個「使用時間」中，以反映多重送貨的所需值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/4745100c>

### 管理UI、測試與預覽

* _ACP2E-3424_： [Cloud]移除遺失影像的範本導致pub/media被刪除
   * _修正附註_：在此修正之前，如果pagebuilder範本缺少預覽影像名稱，則會刪除pub/media資料夾。 修正後，只會刪除範本和預覽影像（如果找到）。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/報表

* _AC-9922_： Google Analytics CSP錯誤https://region1.analytics.google.com
   * _修正附註_：啟用Google Analytics時，系統現在可正確連線至&#39;https://region1.analytics.google.com&#39;&#39;，避免內容安全性原則(CSP)錯誤。 之前，若啟用Google Analytics並從歐盟檢視網站，會因為拒絕連線至「https://region1.analytics.google.com&#39;」而導致CSP主控台錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37750>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_：進階報告無法運作
   * _修正附註_：系統現在支援以10,000批次載入和寫入報表，為超大型資料集產生進階報表資料檔案。 以前，進階報告模組無法為超大型資料集產生資料檔案，導致在執行analytics_collect_data cron作業期間出現「MySQL伺服器已消失」錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_：管理員訂購產品報告日期範圍可見性問題。
   * _修正附註_：使用者將能夠從「訂購產品」報表中選取任何日期。 先前，重新整理表格後，選取「起始」日期會重設「截止」日期。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_：不正確的CURL標頭導致`newrelic:create:deploy-marker`無法運作
   * _修正附註_：系統現在已正確設定curl標頭的格式，允許`newrelic:create:deploy-marker`命令在New Relic中成功建立部署標籤。 之前，不正確的curl標題無法在New Relic中建立部署標籤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37641>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
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

### Analytics/報表，B2B

* _ACP2E-2300_： B2B - Sitemap包含未指派給共用目錄的產品/類別
   * _修正附註_：將Sitemap產生的類別和產品限製為僅指派給公用共用類別和/或類別許可權設定的類別和產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/報表、雲端

* _ACP2E-3067_： Magento會捨棄大部分的New Relic cron交易#34108
   * _修正附註_： AC正在向NewRelic正確報告cron工作相關交易。 以前，某些cron工作相關交易在NR中顯示為「OtherTransaction/Action/unknown」
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_： NR中的量度可能對背景交易產生誤導 — ACP2E-3067的後續追蹤
   * _修正附註_：背景交易(cron)將使用組態設定中定義的New Relic應用程式名稱
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_： 2.4.8-beta102 Package Enterprise Edition因應用程式例外而失敗
* _ACP2E-2139_：執行部分索引時，指派給共用目錄的產品未反映在前端
   * _修正附註_：部分索引完成後，透過REST API指派給共用目錄的產品現在會立即顯示在店面上。 過去，產品只有在完全重新建立索引後才會顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-2873_： [Cloud]行動版和案頭版的價格顯示與「我的報價」不同
   * _修正備註_：當目錄總價區段已展開時，「可轉讓報價」中不再顯示「不需要的包含稅捐」明細行。
* _ACP2E-3044_：「我的訂單」區段上有不必要的框線
   * _修正附註_：先前已建立其他套用其他CSS類別的容器（訂單參考），導致不必要的框線出現在「我的訂單」區段內的訂單編號下方，而現在未顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_： sales_clean_quotes cron會從尚未核准的採購單刪除報價
   * _修正備註_： sales_clean_quotes cron工作不會刪除採購單中使用的報價
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_：下單按鈕在採購單詳細資料中消失
   * _修正備註_：修正當產品變數在卡片中指定了最小數目時，已核准採購單的「下訂單」按鈕隱藏的問題
* _ACP2E-3474_： [CLOUD]沒有識別碼= 0且具有b2b模組的此類實體
   * _修正附註_：啟用共用目錄功能時，登入的使用者可以將產品加入購物車。
先前將產品新增到購物車會導致「沒有ID = 0的這類實體」錯誤
* _ACP2E-3562_：從請購單清單大量新增時，沒有針對我們的庫存產品顯示錯誤訊息
   * _修正附註_：修正前，無論無法新增至購物車的產品數量為何，都會顯示成功訊息。 現在，對於成功新增到購物車的產品以及失敗的產品，將顯示單獨的訊息。
* _ACP2E-3628_：排程更新後的SKU更新問題，導致不正確的產品許可權（–2拒絕）
   * _修正附註_：使用過去的排程更新修改產品的SKU時，不會再造成有權檢視產品的共用目錄客戶無法存取產品。

### B2B，目錄

* _ACP2E-2860_：使用NoDDL和類別許可權時重新索引期間可見的產品/類別
   * _修正附註_：在執行目錄許可權索引時，避免在店面受限制的類別及其內容上顯示。

### B2B，框架

* _AC-9607_：篩選公司格線，然後嘗試格線CSV匯出會失敗並擲回例外狀況
   * _修正附註_：系統現在允許管理面板中的公司格線資料成功CSV匯出，即使套用「未結餘額」和「公司型別」等篩選條件亦然。 以前，套用特定篩選條件並嘗試匯出網格資料會導致失敗並擲回例外狀況。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/44cef3a9>

### B2B、GraphQL

* _ACP2E-3391_： [雲端]透過graphql呼叫建立公司時無法設定custom_attributes
   * _修正附註_：修正後，可以使用graphql要求建立公司期間，為公司管理員設定「custom_attributes」屬性。

### Braintree

* _AC-14293_： Admin Express簽出按鈕已停用。
* _套件–3367_：透過LPM付款
   * _修正附註_：系統現在會在初次載入時正確轉譯本機付款方法(LPM)，即使登入客戶的送貨與帳單地址不符亦然，以確保順利結帳。 先前，客戶的送貨地址與帳單地址不符會導致LPM無法呈現，進而在結帳時造成潛在中斷。
* _BUNDLE-3368_：可設定為虛擬子產品
   * _修正附註_：系統現在允許擁有虛擬子產品之可設定產品的快速付款方式，以確保順利結帳。 以前，將具有虛擬子產品的可設定產品新增到購物車時，無法使用快速付款方法。
* _BUNDLE-3369_： CVV驗證失敗錯誤
* _BUNDLE-3370_：透過帳戶區域存放問題247
   * _修正附註_：系統現在可讓客戶跨多個網站儲存新卡片或PayPal帳戶資訊，而不會發生授權錯誤。 以前，客戶無法跨不同網站儲存新的付款方式，且收到授權錯誤訊息。
* _BUNDLE-3371_：從不同國家寄送地址
   * _修正備註_：系統現在允許從不同國家/地區運送至地址時，處理交易而不會發生錯誤，以確保順利結帳。 以前，嘗試從不同的國家/地區傳送地址會導致主控台錯誤，儘管前端沒有明顯的錯誤。
* _BUNDLE-3372_：信用卡 — Teardown函式
   * _修正附註_：系統現在會在客戶從付款頁面導覽回送貨頁面時，正確處理Braintree PayPal元件的拆卸，避免任何錯誤，並確保PayPal Express按鈕正確呈現。 先前，從付款頁面導覽回送貨頁面時，有時會因嘗試拆卸Braintree PayPal元件而發生錯誤。
* _BUNDLE-3373_： PayPal Express的送貨回呼
   * _修正附註_：系統現在會在PayPal Express強制回應視窗中正確顯示可用的送貨方式，讓客戶在繼續檢閱頁面或完成交易前，能夠選取他們偏好的送貨方式。 之前，在PayPal Express強制回應視窗中無法選取送貨方法，因此客戶必須先在個別的稽核頁面上選取送貨方法，才能完成交易。

### 組合

* _AC-10826_：店面組合核取方塊驗證錯誤訊息計數超過1
   * _修正附註_：現在系統只顯示一則驗證錯誤訊息，當按一下[加入購物車]按鈕，而未選取套裝產品的任何核取方塊選項時。 以前，系統會為每個未選取的核取方塊顯示多個驗證錯誤訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_：在某些與順序相關的測試案例中擲回Magento例外狀況
   * _修正附註_：系統現在可正確處理各種測試案例中的「sendGuestPaymentInformation」步驟，避免擲回Magento例外狀況。 以前，這些例外是由於空值付款方法所造成，這會導致多個測試案例中的失敗。

### 購物車與結帳

* _AC-10660_：在比較產品頁面中將產品加入購物車時，未正確處理例外狀況
   * _修正附註_：系統現在會正確處理從比較產品頁面將產品加入購物車時的例外狀況，並在控制器中顯示訊息管理員訊息。 在過去，例外狀況會導致傳回JSON編碼頁面，而非正確擷取和處理。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38200>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38257>，<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_： GTag未傳送交易價格與總計。
   * _修正附註_：系統現在會在啟用GTag時，正確傳送交易價格與總計至Google Tag，以確保電子商務資料的正確追蹤。 以前，貨幣會不正確地作為「所有」訂單的一部分傳送，而不是與個別訂單相關聯。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37348>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37504>，<https://github.com/magento/magento2/pull/37349>
* _AC-11641_： [問題] [結帳] Depend指示詞已在失敗的付款電子郵件範本中更新
   * _修正附註_：系統現在會從虛擬產品的失敗付款電子郵件範本中正確忽略送貨地址和送貨方法，確保電子郵件中僅包含相關資訊。 以前，虛擬產品付款失敗的電子郵件錯誤地包含送貨地址和送貨方法。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32781>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32511>
* _AC-11717_：現有客戶的Magento 2登入在簽出內時，在Firefox瀏覽器中發生主控台錯誤
   * _修正附註_：系統現在可讓使用者在結帳程式期間登入，而不會在Firefox瀏覽器中遇到任何主控台錯誤。 之前，在結帳期間嘗試以現有客戶身分登入，會導致Firefox發生主控台錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38557>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39509>
* _AC-11876_： [問題] 2.4.7中的銷售規則回歸
   * _修正備註_：系統現在可正確驗證銷售規則，當產品狀況不符合任何產品名稱時，無法套用優惠券代碼至購物車。 以前，即使產品狀況與任何產品名稱不符，也可以套用銷售規則，並針對運費金額提供折扣。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38671>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_： [問題]銷售規則CartFixed計算：折扣金額不正確
   * _修正備註_：系統現在會正確計算具有購物車固定金額之銷售規則的折扣金額，以確保不論購物車專案是否變更，都能套用正確的折扣。 以前，當購物車專案變更時，折扣金額可能會錯誤地變化，有時會導致比預期大得多的折扣。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38694>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_： [問題]郵遞區號變更後，載入程式會封鎖送貨方法、送貨費率驗證規則
   * _修正附註_：系統現在會正確處理自訂送貨方法，而不使用送貨費率驗證規則，確保載入器在結帳期間變更送貨地址中的郵遞區號後，不會封鎖送貨方法。 先前，在結帳期間變更送貨地址中的郵遞區號，會導致載入程式封鎖送貨方法，而且在使用沒有運費驗證規則的自訂送貨方法時無法消失。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38742>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_：優惠券代碼功能在Magento 2.4.7上的結帳頁面中無法正常運作
   * _修正備註_：系統現在會在虛擬和可下載產品的結帳頁面上啟用折扣代碼/優惠券輸入欄位，讓使用者如預期套用折扣代碼。 之前已停用折扣代碼/優惠券輸入，且按鈕標題文字顯示為「取消優惠券」，以防止使用者套用折扣代碼。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38826>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
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
* _AC-13797_：禮品登入產品未正確顯示
* _AC-13841_：禮品登入產品未正確顯示
* _AC-8103_：地址轉譯程式中的轉譯VAT
   * _修正附註_：系統現在允許翻譯地址轉譯器中的「VAT」、「T」、「F」文字，讓使用者可以將這些字詞翻譯成商店的特定語言。 以前，這些術語無法翻譯，迫使使用者採用因應措施。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36942>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_：同時有相同報價識別碼的重複訂單，幾乎沒有時間差異
   * _修正附註_：修正Adobe Commerce客戶使用相同QuoteID下重複訂單的問題
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_：結帳步驟中永久性的購物車已清除
   * _修正附註_：修正後，在未登入時結帳時選取付款方式並不會終止持續工作階段。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_：重新訂購將未指派的產品加入購物車
   * _修正附註_：之前，不同商店的產品可以從其他商店重新排序。 僅套用此修正後，若啟用客戶帳戶共用，可對相同範圍產品重新排序
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_：在admin中，選取專案時左側的「購物車」未更新，並從右側選取「移至購物車」
   * _修正附註_：選取專案時，左邊的「購物車」會更新，而管理員端右側的「移至購物車」則會更新。 以前，此功能無法運作，因為轉換的購物車專案不會從工作階段中變空白。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_： [Cloud]銷售規則未套用至多重出貨的第一筆訂單
   * _修正備註_：修正之後，會正確顯示相同多送貨報價單之每筆訂單的折扣。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_： [Cloud]將相同產品加入購物車的生產平行要求會在購物車REST API中產生兩個個別的專案
   * _修正附註_：系統現在可正確處理多個平行請求，以將相同產品加入購物車至單一條列專案，防止為相同的SKU建立個別條列專案。 以前，透過REST API並行請求將相同產品新增到購物車會導致同一SKU出現多個條列專案。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2676_：從禮品登入Magento 2.4.4 Enterprise/Commerce訂購時發生問題
   * _修正備註_：無法從禮品登入成功購買產品的問題已解決，可以下訂單並適當地更新禮品登入。 之前，嘗試從贈品註冊處下訂單時發生錯誤，導致購買無法完成。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35432>
* _ACP2E-2704_：正在取得無法傳送Cookie。 嘗試重新排序時的「影像訊息」大小
   * _修正備註_：重新排序程式現在不會產生自己的錯誤。 它將依賴購物車列出內建專案檢查。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_：結帳時未選取預設送貨地址
   * _修正附註_：預設送貨地址正在啟用地址搜尋的內容中選取事件。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_： [CLOUD] graphql addProductsToCart api問題包含自訂選項
   * _修正附註_： GraphQL使用不同的自訂選項，將相同的產品正確地新增至購物車
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2917_：變更商店檢視時[雲端]相關產品規則無法運作
   * _修正附註_：此問題已透過確認在購物車頁面上已成功收到自訂屬性值而修正。 先前，在店面購物車頁面上的商店之間切換時，無法正確擷取該資料。
* _ACP2E-2923_：結帳為新客戶時，有多個地址新增至帳戶
   * _修正附註_：系統現在只會在訂單無法建立時儲存一次新的客戶地址，以防止在訂單放置錯誤時建立多個相同的地址。 以前，每次嘗試下訂單時，系統都會儲存新地址，無論是否成功建立訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/001e5188>，<https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_：透過訪客訂單重新排序客戶訂單導致出現空購物車
   * _修正附註_：先前透過「訂單與退貨」頁面進行重新排序時，會將客戶重新導向至登入頁面。 套用此修正後，進行重新訂購時，註冊的客戶會被正確重新導向至「檢視購物車」頁面。 此流程的運作方式與訪客客戶相同。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_：角色資源有限的管理員使用者無法檢視購物車
   * _修正附註_：以前，受限制的管理員無法從相關網站的管理員面板中看到捨棄的購物車。 套用此修正後，受限制的管理員可以從管理員面板檢視捨棄的購物車。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
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
* _ACP2E-3415_：登出時未遵循購物車持續性
   * _修正附註_：新增遺漏的功能從客戶登入到驗證快顯視窗和簽出登入記住我。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_：現有報價資料未更新/不可見，而是在trigger_recollect = 1時建立新的報價記錄
   * _修正附註_：客戶的購物車專案在加入購物車後，不會再因產品被刪除而消失。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3495_：購買禮品登入專案時，客戶看到其登入上沒有的專案
   * _修正備註_：贈品登入更新不再包含不屬於贈品登入的專案。
* _ACP2E-3510_： [雲端]在未確認的情況下移除購物車專案的「移除全部」確認快顯視窗問題
   * _修正附註_：現在，針對需要注意的產品按一下[全部移除]按鈕，會提示確認快顯視窗，以確保專案僅會在您的確認後移除。 以前，專案會立即移除而不需要任何確認
* _ACP2E-3618_： [雲端]重新排序按鈕功能
   * _修正附註_：重新排序管理員區域的訂單現在會將有庫存的產品加入報價單，即使原始訂單中有些產品不再有庫存。 修正前，如果原始訂單中沒有庫存的產品，則不會將任何產品新增至新報價單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_：搜尋存放區無法依郵遞區號運作
   * _修正附註_：依郵遞區號搜尋取車地點無法正確進行荷蘭文本地化。 修正後，取車地點搜尋會根據郵遞區號提供結果。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/344fce23>

### 購物車與結帳、結帳/單頁結帳

* _AC-9386_： [隨機錯誤]電子郵件欄位未轉譯，或需要很長時間才能顯示在結帳送貨或付款頁面
   * _修正附註_： Commerce現在會依預期在結帳送貨與付款頁面上轉譯&#x200B;**[!UICONTROL Email]**&#x200B;欄位。 之前，此欄位不存在或呈現緩慢。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/e1babcfd>

### 購物車與結帳、訂購

* _ACP2E-3097_：產品的Datepicker具有多個「可自訂選項」，且日期欄位在從管理員下訂單時無法運作
   * _修正附註_：在管理訂單建立程式中設定具有多個可自訂日期選項的產品時，系統現在會正確顯示所有日期欄位的日期選擇器。 以前，日期選擇器只顯示第一個日期欄位，而其餘欄位則沒有日期選擇器。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>

### 購物車與結帳、送貨

* _AC-12119_：可設定產品的「最便宜運費」立即購買中斷
   * _修正附註_：「立即購買」功能針對可設定組態的產品錯誤地選取了較昂貴的店內交貨選項，而不是最便宜的統一費率方法。 此修正可確保根據實際價格選擇正確的送貨方法。」
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38811>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38819>，<https://github.com/magento/magento2/commit/29fe9097>

### 目錄

* _AC-10910_：清除cron_schedule資料庫資料表時沒有清除不存在的工作
   * _修正附註_：系統現在會自動清除cron_schedule資料庫表格，移除系統中已不存在的作業專案。 這可透過在表格中維持最少列數來確保最佳效能。 以前，非作用中模組或已移除模組的工作專案不會清除，導致cron_schedule表格中發生不必要的資料累積。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38217>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38693>
* _AC-10953_：未從可設定的產品中刪除層級價格
   * _修正備註_：系統現在會在產品從簡單產品轉換為可設定產品時，正確移除產品的層級價格，確保前端顯示正確的價格。 以前，將產品從簡單產品轉換為可設定產品時，不會刪除可設定產品的層級價格，從而導致顯示的價格不符。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38390>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38427>
* _AC-11804_：類別描述WYSIWYG在非預設存放區上為空白
   * _修正附註_：在商店檢視層級編輯類別時，系統現在會在WYSIWYG編輯器中正確儲存並顯示類別說明。 以前，在商店檢視層級儲存類別說明後，WYSIWYG編輯器會顯示為空白。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38622>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38623>
* _AC-11970_：無法透過選取自訂選項的核取方塊來重新排序可設定的產品
   * _修正附註_：系統現在會使用單一選取的核取方塊自訂選項，正確處理可設定產品的重新排序，以便成功建立購物籃。 之前，嘗試重新排序這類產品會導致錯誤，且無法將專案新增至購物車。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38736>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_： [問題]修正分層導覽上的篩選器專案用詞
   * _修正附註_：系統現在會在階層式導覽篩選專案中正確使用「item」和「items」等字詞，提高篩選說明的清晰度和準確性。 以前，這些字詞的使用不正確，導致導覽篩選選項的使用者可能混淆。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38789>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37852>
* _AC-12164_：自訂選項的日期和時間格式無法運作
   * _修正附註_：系統現在可正確將設定的日期格式套用至日期型別的產品自訂選項，確保日期格式可在前端正確顯示。 先前，日期格式設定的變更不會反映在日期型別的產品自訂選項的前端。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32990>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38925>
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
* _AC-13622_： [問題]基於attribute_set的產品配置
   * _修正附註_：系統現在允許根據屬性集調整產品版面，提供更實用且有效率的方式，以管理前端商店中的產品顯示。 之前，版面配置只能根據SKU或產品型別進行調整，這對於許多產品或特定文章而言並不總是可行的。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38790>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36244>
* _AC-6738_：在eav_attribute_option_value資料表中遺失唯一索引鍵
   * _修正附註_：系統現在在&#39;eav_attribute_option_value&#39;表格的&#39;option_id&#39;和&#39;store_id&#39;欄中包含唯一的索引鍵，以防止同一個存放區檢視可能有多重值的選項。 以前，錯誤的程式碼可能會導致選項針對相同的商店檢視擁有多個值，進而在編輯產品或屬性時造成問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/24718>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/28796>
* _AC-8297_： [問題]使用類別產品索引器的可見性類別，而非硬式編碼值
   * _修正備註_：系統現在會使用類別產品索引子的可見度類別，而非硬式編碼值，以強化模組化。 以前，在類別產品索引器中會使用硬式編碼值，這會限制靈活性和適應性。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37200>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37199>
* _AC-9375_：新產品Widget中的貨幣代碼未變更
   * _修正備註_：系統現在會在前端貨幣變更時，正確更新新產品小工具中的貨幣代碼，以確保網站間貨幣顯示的一致性。 之前，變更前端中的貨幣不會影響新產品介面工具集中顯示的貨幣代碼。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37898>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_：可設定產品的PLP上未顯示一般價格
   * _修正附註_：產品清單頁面現在會顯示可設定產品的正常價格，這些產品具有具有具有特殊價格的子產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_：庫存資訊未直接顯示在Visual Merchandising網格上
   * _修正附註_：已根據選取的商店顯示庫存。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_： Widget內容未在cms頁面上更新
   * _修正附註_：系統現在會更新CMS頁面上的Widget內容（當產品設定為新產品且已儲存時），以確保該頁面顯示更新的產品集合。 以前，由於快取中Widget使用的快取身分不正確，頁面未更新以顯示新產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_：儲存套件組合產品的進階定價時發生問題
   * _修正附註_：組合產品儲存效能改善。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_： [內部部署]重新索引程式在建立目錄價格規則時效率低
   * _修正附註_：現在儲存目錄價格規則將不會使索引子失效，而是只會重新索引受影響的產品
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_：正在透過CSV匯入更新日期和時間型別產品屬性的時間
   * _修正附註_：現在，日期時間屬性在匯出的資料中會有時間部分。 也可以使用匯入來更新此類屬性的時間。 此外，如果已啟用「欄位附件」，「additional_attributes」欄中的屬性值將會用雙引號括住。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38306>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_：要求中的網站ID錯誤時，沒有適當的錯誤訊息
   * _修正附註_：現在已新增適當的錯誤訊息，以便在要求中的網站ID錯誤時顯示。 先前，要求中的網站ID錯誤時不會進行驗證。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_：刪除不會影響影像的現有排程更新後，產品影像遺失
   * _修正附註_：刪除中繼更新時未移除產品影像。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_： [Cloud]搭配層級價格使用時套裝產品的價格錯誤
   * _修正備註_：先前在計算四捨五入為2個小數點的某些百分比折扣時，會產生購物車與產品清單頁面/產品詳細資料頁面的不同最終價格。 套用此修正後，套裝產品的最終價格與產品詳細資料頁面、產品清單頁面和迷你購物車頁面中的價格相同。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38091>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_：目錄促銷規則不適用於quantity_and_stock_status屬性
   * _修正附註_：目錄促銷規則現在會考慮quantity_and_stock_status屬性，而之前從管理員端產生新產品時，不會考慮該屬性。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35627>
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_：透過REST API更新價格時，產品實體updated_at欄值未更新
   * _修正附註_：透過REST API更新現有產品時，管理員的產品「上次更新時間」欄會更新適當的日期時間。 之前「上次更新時間」欄未正確更新。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_：可以透過產品匯入設定非唯一值
   * _修正附註_：系統現在會在產品匯入期間，正確執行唯一產品屬性的唯一值限制，以防止該屬性的值重複。 以前，如果產品屬性是透過產品匯入設定為具有唯一值，您就可以為產品屬性設定非唯一值。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38445>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_：啟用單一存放區模式時，前端上的產品會使用存放區特定資料
   * _修正附註_：先前為預設商店檢視啟用單一商店模式時，變更未移轉至網站層級的範圍。 套用此修正後，當我們啟用單一商店模式時，預設商店檢視特定資料將與網站層級特定資料同步，並將解決產品和類別之間可能出現的衝突。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_：無法使用rest API在類別中設定「預設排序依據」
   * _修正附註_：透過REST / SOAP APi要求正確更新類別上的default_sort_by
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_： [雲端]商家面臨願望清單計數問題
   * _修正附註_：將產品新增至某家商店的願望清單，不會再增加相同瀏覽器中開啟之其他商店的願望清單計數。 先前，如果兩個存放區都載入同一個瀏覽器，另一個存放區的願望清單計數也會增加。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_：使用套件產品時，前端的「類別頁面」會顯示空的插槽
   * _修正附註_：在目前存放區內容中無法銷售的套件組合產品不再編制索引。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2888_： [說明]套件組合產品順序表問題
   * _修正附註_：現在刪除組合產品或刪除組合產品選項時，會移除組合產品序號表格(sequence_product_bundle_option、sequence_product_bundle_selection)中的記錄。
之前，未移除套件組合產品序號表格中的記錄。
* _ACP2E-2905_： [雲端]多網站架構中的報價問題
   * _修正備註_：之前，使用不同貨幣和客戶群組的多網站架構無法正確將折扣套用至商店。 實施此修正後，具有不同客戶群組價格折扣的多網站架構將成功套用至不同的商店。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38506>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_： dynamic-rows.js：658編輯套件組合產品時未擷取的TypeError： dataRecord.slice
   * _修正附註_：從套件產品刪除選項時，瀏覽器主控台中沒有JavaScript錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38505>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_： [雲端]套件組合產品訂單確認中的定價錯誤
   * _修正備註_：使用基礎貨幣以外的貨幣時，Storefront上會依序顯示組合選項的正確金額。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_： YouTube視訊新增錯誤
   * _修正附註_：產品影像和視訊已設定於全域範圍。 由於您無法在一個領域擁有產品影片，而不能在另一個領域擁有，因此Youtube API金鑰設定已設定為全域範圍。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_： [僅適用於store_id=0的Cloud] URL更新
   * _修正附註_：「URL路徑」現在已使用正確的存放區ID儲存。 以前，商店ID不正確，導致在移動類別時資料庫中保留不正確的URL路徑。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_： async.operations.all已執行並建立錯誤。
   * _修正附註_： REST API呼叫中錯誤的產品連結資料不再導致嚴重錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_： [雲端]行動問題僅無法夾緊PDP影像
   * _修正附註_：系統現在支援Chrome上行動檢視中產品詳細資料頁面影像的縮放夾功能，可增強行動使用者體驗。 之前，在Chrome上的行動檢視中連按兩下影像時，系統無法如預期放大影像。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_：選項名稱為0的LayeredNavigation中遺漏標籤
   * _修正附註_：已略過屬性值0的空值檢查器來解決問題。 之前，該維度會被視為空白並導致問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_：客戶看到其他客戶群組的價格
   * _修正附註_：修正客戶群組相關資訊因請求中X-Magento-Vary的舊值而儲存在錯誤區段的問題
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_：刪除套件組合選項時發生錯誤
   * _修正附註_：系統現在會正確刪除套件組合選項，而不會觸發錯誤或造成頁面無回應。 先前，嘗試刪除套件組合選項會導致「頁面無回應」錯誤並阻止產品儲存。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_：類別許可權記憶體不足的瀏覽器問題
   * _修正附註_：類別許可權UI經過重新設計，允許使用現成的UI元件和分頁產生大量許可權。 先前類別許可權會導致瀏覽器當機，並會將大量許可權指派給類別。
* _ACP2E-3100_： [雲端]影像檔案不存在於New Relic錯誤記錄檔中
   * _修正附註_：系統現在會將自訂預留位置影像同步至本機儲存體，以確保在使用AWS S3等遠端儲存體時，這些影像可正確轉譯。 先前，自訂預留位置影像在使用遠端儲存空間時無法轉譯，導致影像顯示中斷和錯誤記錄。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_：由於快取，新產品RSS摘要未更新為新產品
   * _修正附註_：當產品設定為新產品且已儲存時，「新產品」的Rss摘要現在會更新
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_： [Cloud]產品媒體庫GQL回應未依影像位置排序
   * _修正附註_：系統現在會依在GraphQL回應中的位置正確排序媒體集中的專案，確保顯示順序準確。 先前，媒體集中的專案並未依位置排序，導致顯示順序不正確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37671>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_： [雲端]子類別專案未顯示在管理後端的Widget編輯上
   * _修正附註_：在新Widget頁面上的類別樹狀目錄應該不會再有載入5級以上類別的問題。 以前，在載入超過第5級類別的樹狀結構時，會遺漏某些類別。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
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
* _ACP2E-3513_： [雲端]特殊價格未顯示在可設定的產品中
   * _修正備註_：修正之後，變更特殊價格屬性的[用於產品清單]值不會影響顯示可設定產品的特殊價格。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_：如果處理程式終止，索引子暫存資料表將不會清除
   * _修正附註_：如果索引器處理序已終止，現在會清除CatalogRule索引器暫存資料表
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_： [QUANS] 2.4.7-p3中的核心單元測試失敗
   * _修正附註_：此測試不需要發行說明，因為這是單元測試改進。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_：使用多個來源的分組產品的庫存量擷取出現效能問題
   * _修正附註_：當指派的產品具有大量庫存來源時，群組產品和套件產品編輯頁面現在已最佳化。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_：重新修正https://jira.corp.adobe.com/browse/ACP2E-3389
   * _修正附註_：若有大量錨點類別，可改善管理類別頁面的效能
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/982b1c42>

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

### 目錄，框架

* _AC-9111_：訂單取得（出貨|Creditmemos|發票）集合 — 集合不應載入
   * _修正備註_：系統現在可確保從訂單擷取時，不會預先載入出貨與銷退折讓單的收貨，允許對這些收貨套用額外的過濾條件或訂單。 以前，這些集合會自動載入，以防止進行任何進一步的修改。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37561>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_： [雲端]後續追蹤：檢查資料是否有變更時，資料比較中的不相符
   * _修正附註_：以往，儲存物件在每次都呼叫時不會有任何資料變更（針對任何數值資料欄位，如int/float/double）。 它會觸發標幟_hasDataChanges設為true並呼叫save函式。 它也不會檢查由字串封裝的浮動數字。 此修正套用後，只有在資料變更時，儲存函式才會呼叫。 int/float/double-check的資料值，其值會傳遞至函式，且會執行嚴格的型別比對
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>

### 目錄， GraphQL

* _ACP2E-3090_：在GraphQL中處理類別篩選器： includeDirectChildrenOnly和category_uid
   * _修正附註_：依category_uid篩選時，只會擷取直接子類別。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_： [雲端] Graphql產品排序無法運作
   * _修正附註_：在變數中傳遞欄位時，GraphQl產品會依多個欄位排序，現在會如預期般運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_：GraphQL產品中的層級價格傳回錯誤的值（相較於Storefront）
   * _修正備註_：修正之後，針對graphql要求傳回的產品層級價格會有一個專案的價格。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_： [雲端] B2B：透過GraphQL的類別問題
   * _修正附註_：修正之後，即使根類別沒有允許許可權，類別graphql查詢也會傳回具有允許許可權的類別。

### 目錄、定價、測試和預覽

* _ACP2E-2672_： [Cloud]特殊價格API端點同時更新大量產品時傳回錯誤
   * _修正附註_：現在特殊價格大量更新API將為每個日期範圍建立單一行銷活動，而不是為每個產品和日期範圍建立多個排程更新。 此外，它也會支援並行API請求，以更快處理大量SKU。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>

### 目錄、產品

* _AC-7050_：編輯產品中的類別選擇樹狀結構順序與目錄 — >類別中的設定順序不同
   * _修正附註_：系統現在會以目錄 — >類別中設定的相同順序，在產品編輯區段中正確顯示類別選取樹狀結構，讓大型目錄中的產品管理更容易。 以前，產品編輯區段中的類別樹狀結構會以類別建立的順序顯示，無論在目錄 — >類別中設定的顯示順序為何。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36101>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36104>

### 目錄，SEO

* _ACP2E-3653_：頁面> 1時類別的規範URL不正確
   * _修正附註_：之前，多頁內容的標準URL無法正常運作，只會顯示基礎URL。 不過，實施修正後，多頁內容的標準URL現在會正確顯示具有頁面ID的URL。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/982b1c42>

### 目錄，搜尋

* _ACP2E-2757_：產品未顯示在類別和搜尋上，但直接連結正常運作
   * _修正附註_：以往，具有price_* attribute_code的Yes/No自訂屬性無法與索引搭配使用。 進行此修正後，「是/否」自訂屬性會如預期運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_： [雲端]某些類別頁面上的彈性搜尋錯誤
   * _修正附註_：先前已提及組態票證，當我們為多個產品定價0時，會在前端類別頁面擲回例外狀況。 套用此修正後，當多個產品價格0且我們在前端載入類別頁面時，不會擲回任何例外狀況，並將成功載入類別頁面。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_：建立物件時發生型別錯誤： Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor例外狀況
   * _修正備註_：修正之後，可以建立Magento\CatalogSearch\Model\Indexer\Fulltext類別的執行個體，而不需指定$data。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_：在Magento Admin中儲存後，前端看不到產品的[雲端]問題
   * _Fix備註_：在修復可設定的產品之後，擁有長名稱子產品的店面將不會遺失。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 目錄，送貨

* _ACP2E-3195_：訂購禮品登入專案時送貨地址是空的
   * _修正附註_：之前，針對訪客使用者禮品登入專案，從電子郵件功能傳回時，會產生空白的位址，此位址不適用於下訂單。 套用此修正後，禮品登入會檢查已登入的使用者/訪客使用者以及指定的地址（如果存在）。

### 雲端

* _ACP2E-3010_： [Cloud] PHPSESSID正在變更每個POST要求
   * _修正附註_：如果已啟用L2 Redis快取，且客戶已從後端更新，則PHPSESSID不再針對登入客戶的前端區域重新產生POST請求
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_： Sitemap產生警告
   * _修正備註_：修正後，Sitemap會在系統tmp目錄中產生，並複製到最終目的地。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>

### 內容

* _AC-10539_： [問題]，與「最近檢視的Widget」中的價格顯示有關
   * _修正附註_：系統現在會在「最近檢視的產品」Widget中正確顯示無庫存簡單產品的價格，確保所有介面工具集和產品清單頁面的一致性。 以往，由於價格載入範本中的條件，無存貨簡易產品的價格不會顯示在「最近檢視的產品」Widget中。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38167>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38159>
* _AC-10596_： [問題] acl.xsd檔案中的錯字與文法正確
   * _修正備註_：系統現在修正acl.xsd檔案中的錯字與文法錯誤，提高檔案的清晰度與正確性。 以前，acl.xsd檔案包含拼寫錯誤和錯誤的語法，這可能會造成混淆。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38061>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38046>
* _AC-10845_：相簿中看不到Pagebuilder橫幅影像
   * _修正附註_：系統現在可正確顯示上傳到Pagebuilder相簿中新建立資料夾中的橫幅影像，消除了之前的主控台錯誤。 在此修正之前，如果橫幅影像上傳到新資料夾，則無法在相簿中顯示，進而造成主控台錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_：更新至2.4.5-p8後「未設定區碼」
   * _修正附註_：系統現在會在Magento_CSP模組啟用且「dev/js/translate_strategy」設為「embedded」時，成功完成靜態內容部署程式，而不會觸發「未設定區碼」錯誤。 以前，在這些情況下，靜態內容部署程式會失敗並出現「未設定區碼」錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38845>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38922>
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
* _AC-9638_： [問題]產品頁面上WYSIWYG編輯器中的檔案上傳問題
   * _修正附註_：系統現在可正確顯示資料夾樹狀結構，並允許在產品頁面上的WYSIWYG編輯器中上傳影像，即使先展開「影像和視訊」索引標籤亦然。 先前，展開「影像和影片」索引標籤後，導致資料夾樹狀結構未顯示，以及嘗試在WYSIWYG編輯器中上傳影像時出現錯誤訊息。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38026>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_： [內部部署]動態區塊問題
   * _修正附註_：動態區塊中的Widget現在已正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_： YouTube nocookie url在頁面產生器中無法運作
   * _修正附註_：現在pagebuilder允許在驗證規則的表單元素設定中使用youtube無cookie url。 之前，youtube非Cookie URL無法在pagebuilder中運作。
* _ACP2E-2693_： [雲端]前端未載入，因為新聞稿範本有問題
   * _修正附註_：透過CMS頁面內容區段新增區塊不會再導致例外狀況
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_： ACP2E-2836： [Cloud]調查記錄中發現的例外狀況： InvalidArgumentException：類別不存在於vendor/magento/module-rule/Model/ConditionFactory.php中
   * _修正附註_：移除PageBuilder產品內容設定的條件時，記錄檔中不會再記錄例外狀況。 先前，移除PageBuilder產品內容設定的條件會導致記錄中記錄嚴重例外狀況，而不會在前端造成任何問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_：切換到單一存放區模式 — 不再顯示全域內容
   * _修正附註_：系統現在會在啟用單一商店模式時，將商店檢視設計設定與網站設計設定同步，確保內容更新會顯示在前端。 以前，切換到單一商店模式會防止內容更新反映在店面上。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_：頁面產生器在嘗試新增連結和其他可用性問題時取代影像。
   * _修正附註_：現在按一下影像，頁面產生器文字元素中wysiwyg編輯器中的連結會在影像的連結設定對話方塊中載入適當的資料。 現在，在編輯器中新增影像連結也可正常運作。 之前，影像已更換為連結。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_：將0位元組影像放在目錄中時，舊媒體集無法轉譯影像
   * _修正備註_：系統現在可以處理媒體集中的0位元組影像，而不會中斷功能，讓目錄中的其他影像可以如預期顯示和選取。 以前，如果媒體集中有0位元組的影像，將無法顯示或選取目錄中的所有影像。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_：編輯CMS區塊時出現錯誤頁面產生器
   * _修正附註_：系統現在會使用頁面產生器正確地儲存管理區域中所做的變更，而不會擲回「頁面產生器呈現了5秒鐘，但未釋放鎖定」錯誤。 在瀏覽器主控台中。 以前，嘗試儲存變更時會發生此錯誤，導致內容無法成功更新。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>，<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_： [雲端]購物車區段上沒有結帳或編輯購物車的按鈕
   * _修正附註_：套件組合產品現在已透過Widget加入購物車，且未發生錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>，<https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3113_：類別頁面上的內容測試預覽未顯示產品Widget
   * _修正附註_：透過確保連結至CMS區塊的其他類別的產品專案已準確記錄到資料庫中，此問題已修正。 先前，請求類別預覽頁面時，它會傳回空白的結果集。
* _ACP2E-3122_： [雲端]上傳影像按鈕無法運作
   * _修正附註_：在PageBuilder中橫幅和滑桿的「上傳影像」按鈕未如預期運作，現在按一下按鈕時會開啟本機檔案管理員，以選取要上傳的影像。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_： imagecreatetruecolor()：引數#2 ($height)必須大於0。 無法上傳特定影像
   * _修正附註_：解決透過媒體集上傳高度為0的影像時，造成管理員發生錯誤的問題，並成功使用sync命令同步資產。 先前無法透過媒體集上傳影像，當特定影像在媒體集中時，同步命令也會失敗。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_： Prototype.js Array.from與Google Maps API發生衝突
   * _修正附註_： Google地圖現在會在PageBuilder編輯器中正確轉譯。 以前，Javascript錯誤會導致Google地圖無法正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_： [Cloud] - CMS滑桿未反映最新變更
   * _修正附註_：確保在編輯投影片熒幕上觸發儲存事件時，重新整理滑桿清單，已修正問題。 在過去，這會觸發並造成問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_：使用頁面產生器依特定順序插入CMS區塊時，CSM頁面中會發生錯誤
   * _修正附註_：先前在某些版本的PHP和OS (Linux)上，透過PageBuilder參考其他cms區塊的區塊轉譯會失敗並出現「發生未知錯誤」。 請再試一次。」 現在，Cms區塊的內容會在PageBuilder控制的內容中正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_： [雲端]動態區塊將無法正常運作
   * _修正附註_：登出後現在會清除登入的客戶區段，以防止來賓工作階段繼承先前登入的區段
* _ACP2E-3428_：大型內容的Pagebuilder範本預覽失敗
   * _修正附註_：大型內容導致畫布元素超過瀏覽器的限制，並傳回不正確的值，這會破壞後端程式碼（無法正確解碼影像）。 已修正將畫布大小限製為通用瀏覽器上限的問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_：TinyMCE 7遺失字型大小的最新安全性更新
   * _修正附註_： WYSIWYG編輯器中現在提供字型大小和字型系列選取器。 在此修正之前，使用TinyMCE 7時，這些無法在編輯器介面中使用。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>，<https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_： TinyMCE 7編輯器在PT的管理員字型大小，而不是PX，請澄清
   * _修正附註_：修正前，您無法在WYSIWYG區域中以px指定字型大小。 現在您可以以px格式設定字型大小，而非pt格式。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>，<https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_：頁面產生器中的產品內容型別已摺疊，沒有正確的訊息
   * _修正附註_：修正前，當Widget中沒有產品時，預覽版HTML未正確產生。 現在，空白回應已正確產生，且產品Widget在預覽中可正常顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>，<https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_： [頁面產生器]新增產品清單以封鎖導致錯誤
   * _修正附註_：現在透過頁面產生器新增套件組合產品清單以封鎖，不會產生錯誤
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/344fce23>

### 內容， SEO

* _ACP2E-2870_： CMS頁面階層可能會導致URL重寫問題
   * _修正附註_：之前，針對非網站根頁面的自訂永久URL重寫，會無限期重新導向，且不會載入頁面。 套用此修正後，非網站根頁面的自訂URL重寫會如預期運作，不會發生重新導向回圈。

### 內容、測試和預覽

* _ACP2E-2979_：當目錄價格規則設定為使用動態區塊排程時未顯示
   * _修正備註_：系統現在會在產品詳細資料頁面上正確顯示與排程型錄價格規則相關的動態內容。 先前，在排程型錄價格規則時，無法載入動態內容。

### 客戶/

* _AC-12162_：前端 — 客戶建立頁面中的出生日期驗證失敗
   * _修正附註_：確認所有驗證都應該在upgrade moment.js系統相依性升級至最新的次要版本之後運作
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-13060_：客戶區段>條件>產品歷史記錄* > 「已檢視產品」無法運作
   * _修正附註_：系統現在會在符合條件時，在「客戶區段」底下的「已檢視產品」條件下，正確顯示相符的註冊客戶。 過去，即使符合條件，符合的註冊客戶數仍維持為零。
* _AC-8499_：國家/地區下拉式清單變更時，區域文字欄位未重設
   * _修正附註_：系統現在會在下拉式選單中的國家/地區變更時重設區域文字欄位，確保先前的值不會持續存在。 之前，從下拉式清單變更國家/地區時不會重設地區欄位，導致保留最後儲存的值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_：刪除客戶並不會清除已登入及已刪除之客戶在店面上的所有瀏覽器工作階段資料
   * _修正附註_：刪除客戶現在會依預期清理店面登入和刪除之客戶的所有瀏覽器工作階段資料。 購物者可以繼續購物，他們的瀏覽器會將他們的工作階段視為訪客工作階段。 先前，當登入購物者的客戶帳戶從管理員中刪除時，購物者的瀏覽器會擲回JavaScript錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7d5e3906>

### 框架

* _AC-10037_： [問題]在`app/code/Magento/Translation/etc/di.xml`中未使用的型別設定
   * _修正備註_：系統現在會移除組態中未使用的相依性，提升整體程式碼清潔度和效率。 之前，設定中有未使用的相依性，這些相依性不會貢獻任何功能。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38030>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38064>
* _AC-10654_： V1/customers/password端點問題/問題
   * _修正附註_：現在透過API處理密碼變更請求時，系統會遵守管理GUI內設定的限制，避免可能濫用密碼重設功能。 以前，API可以在管理GUI中定義的規則之外處理密碼變更請求，在已知有效電子郵件時，可能會允許不斷重設電子郵件。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38238>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_：清漆設定未排除所有行銷引數
   * _修正附註_：系統現在已正確排除Varnish設定中的所有常見行銷引數，確保追蹤和分析準確。 之前，某些行銷引數（例如gad_source、srsltid和msclkid）未排除，導致資料收集可能不準確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38298>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39188>
* _AC-10838_：目錄搜尋索引程式錯誤索引程式
   * _修正附註_：系統現在會順利完成重新索引命令，不會發生任何錯誤，無論使用PHP編譯的libxml版本為何。 以前，當使用特定版本的libxml編譯PHP時，執行「重新索引」命令會導致「索引處理期間目錄搜尋索引處理錯誤」錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38254>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38553>，<https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_：已將created_at、status和grand_total篩選器新增至客戶「訂單」查詢，並修正多個篩選器失敗
   * _修正附註_：系統現在支援在客戶「訂單」查詢中使用created_at、status和grand_total篩選器，並已解決多個篩選器未正確套用的問題。 以前，系統不支援這些篩選器，且無法在查詢中使用多個篩選器時套用所有篩選器。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38392>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36949>
* _AC-10991_：從相關/向上銷售/交叉銷售區塊和價格索引隨機收到大量查詢
   * _修正附註_：系統現在會最佳化相關、向上銷售和交叉銷售區塊的查詢，提升效能並防止網站因過多查詢而停止運作。 以前，系統可能會因這些區塊中的查詢而變得超載，導致速度大幅減慢，並可能導致網站關閉。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36667>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38050>
* _AC-11423_：例外狀況：警告：正在嘗試存取陣列位移，位於…… -> Calendar.php，因為升級至ICU 74.1 (PHP Intl)
   * _修正附註_： Commerce不再於購物者或商家造訪店面或管理員時，於exception.log中記錄下列例外狀況： `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`。 [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38214>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38364>
* _AC-11476_： [問題]當表單包含名稱為`method`的元素時，修正客戶資料的問題
   * _修正附註_：系統現在會在表單提交中正確識別&#39;method&#39;屬性，即使表單中存在名為&#39;method&#39;的元素。 這可確保準確處理客戶資料。 先前，如果表單元素命名為「method」，則會干擾表單提交中「method」屬性的識別，導致客戶資料處理的潛在問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38484>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38449>
* _AC-11489_： [問題]修正\Magento\Framework\Data\Collection：：getItemById的PHPDocs
   * _修正附註_： \Magento\Framework\Data\Collection：：getItemById方法的PHPDocs已更新，可能包含null作為傳回型別，解決靜態分析工具的問題。 先前，方法的PHPDocs並未指定null作為可能的傳回型別，導致在條件陳述式中使用方法時，靜態分析中出現警告或錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38485>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38439>
* _AC-11592_： [問題]安裝期間只允許有效的偏好設定:di:編譯
   * _修正附註_：如果偏好設定是針對不存在的類別建立或明確排除的類別，系統現在會在安裝:di:編譯命令期間擲回錯誤，確保只允許有效的偏好設定。 以前，這些案例會無訊息地失敗，可能會使任何與原始類別關聯的外掛程式變成無用。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38517>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/33161>
* _AC-11651_： Magento嘗試修改LoggerProxy的__wakeUp方法中的唯讀屬性
   * _修正附註_：系統現在允許修改LoggerProxy的__wakeUp方法中先前唯讀的屬性，以確保順利運作，而不會強制使用者採用因應措施。 先前，嘗試重新指派LoggerProxy的__wakeUp方法中唯讀屬性的值會造成問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38526>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_： [問題] AC-2039 AC-1667升級TinyMCE參考
   * _修正附註_：已更新composer.json中的tinymce最新版本
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38533>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36543>，<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_： ChangelogBatchWalker無法在多個執行緒中運作
   * _修正附註_：系統現在支援MView索引的處理程式復本，以防止在多個執行緒上執行索引器時出現錯誤。 以前，在多個執行緒上執行ChangelogBatchWalker會導致刪除其他執行緒使用的表格，進而在索引器執行期間造成錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38246>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38248>
* _AC-11781_： [問題]重新命名錯誤的變數
   * _修正附註_：系統現在會正確命名包含仍可退款的金額的變數，以防止在偵錯期間產生混淆。 之前，此變數被錯誤地命名為totalReturn，這可能導致開發人員誤解。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38609>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36205>
* _AC-11809_： [問題]透過XML傳遞自訂屬性至目前的連結
   * _修正附註_：系統現在允許透過XML將自訂屬性傳遞至目前的連結，確保即使連結為目前頁面也能正確顯示這些屬性。 以前，由於getAttributesHtml()方法未用於目前連結，因此不會顯示目前頁面連結的自訂屬性。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38500>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/30070>
* _AC-11819_：某些組態的內建FPC快取在2.4.7中損毀
   * _修正附註_：系統現在會在MAGE_RUN_CODE引數設定時正確快取頁面，確保最佳效能。 以前，在這些情況下不會快取頁面，這可能會導致潛在的效能問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38626>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38646>，<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_： [問題]修正開發人員與生產模式之間處理不一致的例外狀況
   * _修正附註_：系統現在會一致地處理開發人員和生產模式之間的例外狀況，避免在擲回例外狀況時意外重新導向至登入頁面。 以前，例外狀況處理的不一致性可能會導致重新導向到生產模式的登入頁面，而不是顯示例外狀況訊息。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38639>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37712>
* _AC-11852_：取代token_list.phtml中的「PayPal帳戶」翻譯
   * _修正附註_：系統現在會在「儲存的付款方法」頁面中，將可記號化帳戶付款方法的區段標示為「帳戶」，而非「PayPal帳戶」，使其更能代表其功能。 之前，此區段特別標示為「PayPal帳戶」，當新增其他可權杖化的帳戶付款方法時，會造成誤導。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35622>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37959>
* _AC-11874_： Magento\Catalog\Model\ProductRepository類別已失去回溯相容性
   * _修正附註_： ProductRepository類別現在會將Initialization Helper類別還原為第二個引數，確保從此類別擴充的模組如預期般運作，藉此維持回溯相容性。 先前，移除ProductRepository類別中建構函式的Initialization Helper會導致回溯相容性遺失，迫使使用者不得不採取因應措施。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38669>
* _AC-11905_： [問題]靜態內容部署 — 型別錯誤
   * _修正附註_：系統現在會在靜態內容部署期間正確處理空白的LESS檔案，並顯示「LESS檔案是空白的」錯誤訊息。 以前，在部署期間遇到空的LESS檔案時，會擲回不正確的型別錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38682>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38683>
* _AC-12002_： [問題] [檢視]已移除連結和指令碼標籤中的額外空間
   * _修正附註_：系統現在可確保連結和指令碼標籤中沒有額外的空格，提供更乾淨且更有效率的程式碼。 之前，連結和指令碼標籤中的屬性之間可能會出現雙空格字元。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32920>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32919>
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
* _AC-12594_： [問題]針對產生的資料使用已編譯的設定，而非一般設定
   * _修正備註_：系統現在會使用已編譯的組態來產生資料，而非一般組態，減少依賴特定程式碼版本的網路傳輸和資料開銷。 這項變更可防止在容器交換期間在共用執行個體中覆寫快取，進而改善穩定性並減少停機時間。 以前，某些核心類別使用共用設定型別，這可能會導致快取覆寫或應用程式停機，因為多個伺服器的程式碼版本不同。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38785>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/29954>
* _AC-12597_： [問題]從e1ccdb中移除的extjs移除檔案參考……
   * _修正附註_：系統現在會從先前移除的extjs移除檔案參考，消除瀏覽器主控台和系統記錄檔中的錯誤。 以前，由於缺少參照的檔案，這些參照會導致錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38960>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38951>
* _AC-12778_： [問題]次要清除：修正sprintf的錯誤使用，此處只需要2個預留位置，而w...
   * _修正附註_：系統現在正確使用sprintf函式以及適當數量的預留位置，以提升程式碼清潔度和一致性。 先前，sprintf函式與額外的引數搭配使用不正確，這不會導致任何重大問題，但使用方式不正確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39062>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38628>
* _AC-12857_： PHP 8.2.15已移除FTP副檔名
   * _修正附註_：系統現在將FTP擴充功能加入為composer.json檔案中的相依性，以確保透過FTP成功設定CSV匯入。 先前，由於PHP套件中缺少FTP副檔名，嘗試透過FTP設定CSV匯入時擲回錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39083>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_： [問題]修正Magento模組中參考的不正確類別。
   * _修正附註_：系統現在會正確參考模組中的類別，確保作業更順暢，並防止因不存在類別而當機。 這包括Indexer和Creditmemo模組中的錯誤修正，以及PrintAction類別中HttpGetActionInterface的實作。 以前，不正確的類別引用會導致錯誤和潛在的系統當機，並且某些功能(例如creditmemo PDF檔案的檔案名稱和庫存的重新索引)無法按預期運作。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39126>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37784>
* _AC-12964_：可定義dev:di:info CLI命令的區域
   * _修正附註_：系統現在可讓開發人員定義dev:di:info CLI命令的區域，加強開發和偵錯程式。 以前，這個指令只能顯示GLOBAL區域的資訊。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38758>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38759>
* _AC-13149_： [問題]新增isMultipleFiles屬性至影像表單元素範本
   * _修正附註_：此修正可防止「瀏覽以尋找或拖曳影像到此處」按鈕在多個檔案影像表單元素中新增影像時消失。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39219>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36325>
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
* _AC-13725_： Magento\Framework\Filesystem\Driver\Http取決於原因片語OK
   * _修正附註_：已移除Magento\Framework\Filesystem\Driver\Http：：isExists中的[確定]片語檢查
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39546>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39558>
* _AC-13810_： Customer Grid Indexer在「依排程更新」模式中無法正常運作
   * _修正備註_：先前的客戶格線已立即更新，但修正後客戶格線會在cron執行後更新，但不會立即反映。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_： js檔案出現錯字錯誤。
   * _修正附註_：系統現在會在JavaScript檔案中正確使用「訂閱者」一詞，確保相關功能可正常運作。 之前，JavaScript檔案中的印刷錯誤會導致「subscribers」一詞使用錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36163>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36171>
* _AC-8353_： [問題]移除禁止的`@author`標籤
   * _修正附註_：系統現在會從某些模組移除禁止的`@author`標籤，以遵守編碼標準，確保程式碼更乾淨且標準化。 以前，`@author`標籤存在於某些模組中，這違反了既定的編碼標準。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37253>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37003>
* _AC-8356_： [問題]從`Magento_Customer`移除禁止的`@author`標籤（第2部分）
   * _修正附註_：系統現在會從某些模組移除禁止的`@author`標籤，確保程式碼更乾淨且更標準化，以遵守編碼標準。 以前，`@author`標籤存在於某些模組中，這違反了既定的編碼標準。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37250>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37000>
* _AC-8659_： editorconfig語法中的空格中斷[{composer，auth}.json]的規則
   * _修正附註_：系統現在會將4個空格縮排正確套用至composer和auth.json檔案，接著修正editorconfig中的語法錯誤。 先前，由於editorconfig語法中有空格，這些檔案的格式不正確，有2個空格的縮排。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37394>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37395>
* _AC-8662_： [問題]改善cron錯誤記錄
   * _修正附註_：系統現在會擷取並記錄cron程式的STDERR和STDOUT，在cron程式失敗的情況下提供有價值的診斷資訊。 以前，cron處理程式內的任何錯誤訊息都不會被記錄，而且在不同處理程式中執行的cron群組的STDERR和STDOUT會遺失。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37453>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32690>
* _AC-8984_： [問題]在某些安裝程式cli命令的輸出中新增一些顏色
   * _修正附註_：系統現在會為某些安裝程式命令列介面(CLI)命令的輸出加入更多色彩，增強可讀性和使用者體驗。 以前，由於缺少色彩差異，這些指令的輸出比較難以讀取。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/29335>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/29298>
* _AC-9630_：當新增具有必要州/地區的新國家時，升級Magento會重設general/region/state_required。
   * _修正附註_：系統現在只會在新增具有必要狀態的新國家/地區時，將修改過的國家新增至「一般/區域/州_必要」設定，以防止假設該區域已停用的自訂程式碼發生任何中斷。 以前，新增具有必要狀態的國家會將「一般/地區/州_必要」設定重設為具有必要狀態的預設國家/地區，這可能會中斷業務。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37796>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38076>
* _AC-9712_：具有複雜`calc`運算式的php &amp; nodejs程式庫(grunt)之間較少編譯的差異
   * _修正附註_：在更新wikimedia/less.php：^5.x之後，修正php與nodejs程式庫(grunt)之間較少編譯的差異
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37841>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_：執行部分索引時發生「找不到基底資料表或檢視」錯誤
   * _修正附註_：部分重新索引現在可正確搭配大型變更記錄檔使用，以備次要資料庫連線時使用
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_：將MariaDB升級至10.5.1或更新版本後發生問題
   * _修正附註_：修正Mysql升級後，資料庫中的datetime值會轉換為0000-00-00 00:00:00的問題
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_：檢查資料是否有變更時，資料比較中的型別不相符
   * _修正附註_：以往，儲存物件在每次都呼叫時不會有任何資料變更（針對任何數值資料欄位，如int/float/double）。 它會觸發標幟_hasDataChanges設為true並呼叫save函式。 此修正套用後，只有在資料變更時，儲存函式才會呼叫。 int/float/double-check的資料值，其值會傳遞至函式，且會執行嚴格的型別比對。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_： [雲端]匯入無法與目錄var搭配使用
   * _修正附註_：不論檔案名稱為何，產品都能成功匯入。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_：在ipad mini中，功能表和標題會以行動裝置載入，而應該以桌上型電腦載入。
   * _修正附註_：系統現在會將寬度為768px的裝置視為案頭，確保功能表和標題正確載入。 過去，寬度為768px的裝置會視為行動裝置，導致功能表和標題載入行動檢視。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>，<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3046_：執行mview cron時發生DDL作業時找不到基底資料表或檢視錯誤
   * _修正附註_：系統現在會在背景執行mview更新時，正確處理資料庫更新作業，避免發生「找不到基底資料表或檢視」錯誤。 以前，如果同時執行檢視更新，某些資料庫更新操作可能會導致「找不到基底資料表或檢視」錯誤。
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
* _ACP2E-3537_：快取標籤中沒有對應的快取金鑰專案，因此快取清除無法正常運作
   * _修正附註_： Redis快取記憶體記憶體回收行程現在預設啟用LUA模式，以防止競爭情況
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_：已忽略MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK值
   * _修正備註_：修正之後，設為「false」的ENV變數將會視為bool false，而不是字串「false」。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/982b1c42>

### 框架，GraphQL

* _AC-7976_： [問題]已針對GraphQL結構描述推出自訂純量型別的支援
   * _修正附註_：系統現在支援GraphQL結構描述的自訂純量型別，可讓開發人員定義自訂純量型別和實作。 此功能在表達需要驗證的值時特別有用，例如HTML、電子郵件、URL、日期等，以及在更進階的情況下，例如EAV屬性。 之前，系統不支援在GraphQL中處理自訂純量型別。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36877>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/34651>，<https://github.com/magento/magento2/commit/0574ac23>

### 框架、產品

* _AC-13011_：由於magento例外狀況，未產生2.4.8-beta1 EE報告

### 框架， UI框架

* _ACP2E-3324_：即使設定值已鎖定，仍可覆寫設定值
   * _修正附註_：在此修正之前，無法透過bin/magento config：set命令設定設計組態，而且可以透過操作顯示它們的表單來變更鎖定的值。 修正後，從cli使用 — lock-env或 — lock-conf設定的鎖定值無法再更新。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_：即使標頭值未通過驗證，Magento_GraphQl也會執行標頭處理
   * _修正備註_：系統現在可確保標頭處理僅執行一次，且僅當標頭值通過驗證時才會執行，增強安全性並防止潛在漏洞。 以前，即使標頭值未通過驗證，也會執行標頭處理，由於重複處理標頭值，導致潛在漏洞和意外行為。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_：實體Giftcard選項沒有正確的排序順序
   * _修正附註_：系統現在會透過GraphQL查詢時，正確排序實體禮卡產品的選項，確保與Luma主題一致的呈現。 先前，排序順序根據Luma主題不正確，導致顯示和排序選項不正確，例如寄件者姓名、收件者姓名和金額。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_： [GraphQL]解析器快取在建立/編輯/移動/刪除中繼更新時失效
   * _修正附註_：系統現在可確保在建立、編輯、移動或刪除臨時更新時，解析程式快取不會失效，但只有在將臨時更新套用至實體時。 以前，解析器快取會在套用中繼更新之前過早失效，導致不必要的快取失效。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_：未針對內容分段更新清除Fastly快取
   * _修正附註_：現在當更新PageBuilder內容相關的實體時，具有PageBuilder內容回應快取的GraphQL會失效。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_：停用階層導覽 — 不會從Graphql移除彙總
   * _修正附註_：當管理員組態設定為「目錄>分層導覽>顯示類別篩選」時，透過GraphQL查詢請求具有類別彙總的產品搜尋時，在套用檢查後已修正問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_：包含價格篩選器{from：&quot;0&quot;}的GraphQL產品呼叫未傳回任何結果
   * _修正附註_：先前使用零價格篩選的graphql產品搜尋由於擲回例外狀況而完全未傳回任何結果。 現在，搜尋會如預期傳回結果。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_：客戶傳回屬性的轉譯未反映在個別StoreView的GraphQL API中
   * _修正附註_：客戶回訪屬性的轉譯會反映在個別StoreView的GraphQL API中。
先前個別StoreView的客戶傳回屬性不會反映在GraphQL API中。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_： [雲端]使用節點報價的getPurchaseOrder中斷GraphQL呼叫
   * _修正附註_： 「採購單GraphQL」呼叫將能夠執行工作，而不會發生任何內部伺服器錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_：如果「所有商店檢視」中未啟用產品，生產網站中未顯示[雲端]可設定的產品
   * _修正附註_：系統現在可在網站中正確顯示可設定的產品，即使產品未在[所有商店檢視]中啟用，但在特定商店檢視範圍中啟用。
先前，如果產品在「所有商店檢視」中停用，並只在特定商店檢視範圍中啟用，則產品屬性在GraphQL回應中無法正確顯示，導致產品無法正確顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_： [Cloud]當相同的簡單產品指派給多個可設定的產品時，產品graphql發生錯誤
   * _修正附註_：之前，若有具有相同簡單產品的個別可設定產品，grapQL會傳回錯誤。 此修正套用後，不同可設定產品具有相同的簡單產品，grapQL會傳回沒有錯誤的結果。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_： [雲端]使用者在多網站設定中的驗證和跨網站權杖存取問題
   * _修正附註_：多網站設定中的GraphQl客戶資訊和購物車查詢會檢查非預設網站上的客戶是否存在。
先前的查詢可在不確認客戶存在於多網站設定的非預設網站的情況下運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_： GraphQL購物車專案V2分頁無法正常運作
   * _修正附註_：已藉由傳遞集合查詢中目前頁面引數的正確值來修正問題。 之前，傳遞錯誤值以設定目前頁面，導致問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/8459b17d>
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
* _ACP2E-3492_： [雲端] Graphql API發生問題
   * _修正備註_：在使用Graphql應用程式伺服器修正之前，客戶地址要求未傳回最近的資料。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_：停用的產品仍會出現在grpahQL查詢中的相關、向上銷售、交叉銷售專案中
   * _修正附註_： Graphql現在為停用的關聯、追加銷售和交叉銷售產品提供正確的回應
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_： [CLOUD]： GraphQl錯誤內部伺服器錯誤placeOrder突變
   * _修正附註_：要求中包含優惠券代碼資訊的「placeOrder」變異不再引發內部錯誤例外狀況，訂單已成功下達。 之前，它失敗並出現「內部伺服器錯誤」。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_：未針對具有動態價格的套件組合產品計算discount_percentage
   * _修正備註_：針對product.price_details的discount_percentage新增的修正，未針對已啟用動態價格且套用折扣券的套件組合產品顯示正確值。
* _LYNX-485_：當其中一個套件產品無存貨時，套件產品仍會顯示「IN_STOCK」
   * _修正附註_：解決即使其中一個套件產品無庫存，套件產品仍顯示「IN_STOCK」的問題。
* _LYNX-486_： not_available_message和only_x_left_in_stock未顯示相同的可用庫存
   * _修正附註_：解決not_available_message和only_x_left_in_stock顯示不一致的可用存貨問題
* _LYNX-488_： original_row_total欄位傳回錯誤值
   * _修正附註_：解決original_row_total欄位的問題，此欄位在選取自訂選項時傳回不正確的值
* _LYNX-503_：應根據組態顯示群組的產品縮圖     .
   * _修正附註_：解決問題以確保根據組態設定顯示群組的產品縮圖
* _LYNX-510_：在OrderAddress中查詢selected_options時發生錯誤
   * _修正附註_：已在訂單地址GraphQL回應中將AttributeSelectedOptions更新為custom_attributesV2。
* _LYNX-512_：原始專案價格不含折扣
   * _修正備註_：已更新original_item_price以包含折扣。
* _LYNX-530_：沒有可用的訊息未顯示可用的存貨數量
   * _修正附註_：解決AddProductsToCart突變的錯誤訊息和錯誤碼，以符合「無法使用」訊息組態
* _LYNX-532_：「Simple with custom options products with multi select options」會傳回「OUT_OF_STOCK」狀態
   * _修正備註_：更新庫存套件中的StockStatusProvider解析程式，以修正具有自訂選項的簡單產品的stock_status。
* _LYNX-533_：錯誤(GQL)： cart.itemsV2.items.product.custom_attributesV2傳回伺服器錯誤
   * _修正附註_：藉由新增不含任何自訂屬性的產品，解決當購物車查詢包含產品的自訂屬性時發生的伺服器錯誤。
* _LYNX-536_：訂單/date_of_first_order一律傳回null
   * _修正附註_：解決orders > date_of_first_order一律傳回null的問題。
* _LYNX-544_：客戶不能取消部份出貨的訂單
   * _修正備註_：已新增驗證，以限制客戶取消部份出貨的訂單。
* _LYNX-548_：根據錯誤訊息取消訂單的錯誤碼
   * _修正備註_：訂單取消的錯誤碼現在是以特定錯誤訊息為基礎。
* _LYNX-581_：將Cookie相關屬性從私人移回受保護的
   * _修正附註_：將Magento\Framework\App\PageCache\Version類別建構函式屬性的可見性從私用還原為受保護
* _LYNX-600_：將預設GraphQL查詢的最大複雜度增加到1000
   * _修正附註_：將預設最大GraphQL查詢複雜性從300增加到1000。
* _LYNX-620_： GQL - itemsV2 >原始資料列總計，針對具有檔案選項的可下載產品，價格範圍價格會傳回$0.00，這些檔案選項具有個別價格。
   * _修正附註_：解決已啟用個別連結購買選項的可下載產品針對itemsV2傳回$0 >原始列總計，而針對具有個別價格之檔案選項的產品，傳回的價格範圍為$0.00的問題。
* _LYNX-711_：建立時資料表的結構描述與升級時不同
   * _修正附註_：解決新增新的VARCHAR資料行至現有資料表，導致測試失敗（因為全新安裝和升級之間的結構描述差異）的問題。 modifyColumn()方法現在會設定預設字元集和定序，正確處理VARCHAR欄。
* _LYNX-772_： PHP-8.4版的GraphQl相容性
   * _修正附註_：修正跨多個解析器的GraphQL與PHP 8.4的相容性問題，確保順利運作。 更新CatalogRule、Customer、GiftMessage、GiftCard和GiftWrapping模組中受影響的檔案。

### GraphQL、詳細目錄/MSI

* _ACP2E-2607_：當來源和目的地購物車有相同的組合專案時，MergeCart變異擲回例外狀況
   * _修正備註_： &#39;-
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>，<https://github.com/magento/inventory/commit/db0620da>

### GraphQL、庫存/MSI、效能

* _ACP2E-1716_：升級後網站關閉
   * _修正附註_：透過GraphQl擷取套件組合產品的效能已改善。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>，<https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL，效能

* _AC-9569_： [GraphQL解析器]匯入時未讓客戶解析器資料失效
   * _修正附註_：透過匯入編輯或刪除客戶時，GraphQL客戶解析程式快取現在會如預期失效。 之前，快取不會失效，且客戶資料可在匯入期間編輯或刪除。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL，搜尋

* _ACP2E-2809_： GraphQL產品清單無法依多個引數排序
   * _修正附註_： GraphQl中依多個欄位排序的產品現在能如檔案所述運作
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_：產品清單GraphQL查詢僅限於total_count 10,000個產品
   * _修正備註_：修正後，搜尋結果不限於10000個產品，即使計數超過10000，仍可取得符合搜尋條件的所有產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL，測試架構

* _ACP2E-3363_： Magento\GraphQl\App\GraphQlCustomerMutationsTest.php整合測試失敗
   * _修正備註_： &#39;-
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### 匯入/匯出

* _AC-12172_：提供自訂選項型別時，產品匯入發生問題： file （已建立的產品不包含自訂選項的價格，並且僅顯示提供的第一個檔案型別副檔名）
   * _修正附註_：系統現在會正確匯入具有「檔案」型別之自訂選項的產品資料，確保顯示所有提供的副檔名且包含自訂選項的價格。 先前，在產品匯入期間，如果「file」型別的自訂選項有多個副檔名，則只會顯示第一個副檔名，且遺漏自訂選項的價格。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38805>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_：「匯入歷程記錄」格線中匯入作業的執行時間錯誤
   * _修正附註_：匯入報告執行時間正確顯示，不受管理員地區設定影響。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_：使用匯入以相同電子郵件地址建立的重複客戶
   * _修正附註_：在[帳戶共用]設定為[全域]時匯入客戶，已更新系統中存在的匯入客戶。
先前匯入的客戶重複。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_：新增/更新產品匯入複製可自訂選項
   * _修正附註_：在產品選項CSV匯入期間，將正確的存放區指派給產品選項，此問題已解決。
先前指派給管理員存放區，而非其個別存放區。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_：客戶「created_at」日期未在匯出時轉換為存放區時區
   * _修正附註_：根據客戶匯出CSV區段中的存放區時區，「created_at」欄的日期值會轉換為適當的日期格式。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_： [雲端]使用CSV檢查匯入資料中的資料時發生錯誤
   * _修正附註_：在CSV匯入期間檢查資料時沒有錯誤。 先前，顯示的錯誤訊息為：「使用管理員的CSV檢查匯入區段中的資料時，我們在列：1中找不到符合此電子郵件和網站代碼的客戶」。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_：缺少匯入按鈕
   * _修正附註_：解決CSV中有正確和不正確記錄的資料檢查後，匯入按鈕遺失的問題。 先前，透過CSV中的正確和不正確記錄檢查資料後，匯入按鈕不顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_：無法匯入匯出的客戶地址
   * _修正附註_：客戶地址匯入將如預期般進行。 先前，如果共用客戶帳戶=全域，則客戶地址匯入檔案不會通過驗證，而且有兩個網站的預設網站具有受限制國家/地區清單，而正在匯入的地址是用於另一個網站的允許國家/地區不同
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_： [雲端] CSV檔案中的錯誤數量未產生錯誤
   * _修正附註_：現在庫存來源匯入將會擲回數量欄中非數值的驗證錯誤。 先前，在數量欄中匯入非數值的庫存來源會導致數量設為0。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_：匯入產品時產生的URL金鑰重複錯誤訊息（當URL金鑰已屬於類別時）不正確
   * _修正附註_：當客戶嘗試匯入產品，但產品的URL金鑰已屬於類別時，在產品匯入檢查期間顯示正確的錯誤訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_：產品匯出導致OOM，即使有4G記憶體限制
   * _修正附註_：在此修正之前，如果產品屬性具有數千個選項值（即使有4G可用記憶體），產品匯出會失敗。 此項修正後，產品匯出應會完成csv檔案的匯出。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_： [雲端]匯入程式互相干擾
   * _修正附註_：如果相同的管理員使用者使用相同的使用者工作階段執行兩個或多個匯入作業，則會顯示正確的訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>

### 匯入/匯出，效能

* _ACP2E-3476_： [雲端]產品匯入時間已大幅增加
   * _修正備註_：在修正之前，包含超過10,000個專案的目錄產品匯入發生顯著的時間降級。 修正後，會及時執行目錄產品的匯入。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/87d012e5>

### 安裝與管理

* _AC-13242_： Magento升級在MariaDB 11.4 + 2.4.8-beta1上失敗
   * _修正備註_：升級應該會發生，且沒有任何錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_：管理面板中沒有清漆7的匯出VCL按鈕
   * _修正附註_：「Export VCL for Varnish 7」按鈕已新增至「管理」面板。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>

### 庫存/MSI

* _AC-10750_：資料庫使用首碼時，可設定產品的詳細目錄更新失敗
   * _修正備註_：當資料庫使用首碼時，系統現在會正確更新可設定產品的詳細目錄，避免任何錯誤訊息，並確保儲存正確的數量。 以前，如果資料庫使用前置詞，則在嘗試儲存可設定產品中簡單產品的庫存數量時會發生錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38045>
* _AC-11593_：新增具有屬性的地圖時，Google google API金鑰無法運作
   * _修正附註_：系統現在支援最新的Google Maps API 3.56版，可讓使用者從PageBuilder功能表成功將地圖內容區塊新增到舞台，不會發生任何錯誤。 之前，由於Google地圖API版本的相容性問題，使用者無法新增地圖內容區塊，導致出現「發生錯誤」錯誤訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_：無法為具有多個來源且SKU損毀的訂單專案建立出貨
   * _修正附註_：先前透過資料庫錯誤地在SKU中新增空格時，會導致出貨頁面發生錯誤，該錯誤現已修正，且自動修剪被視為人性化的錯誤，未發現影響。因此已成功建立出貨。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_： [測試]在商店前端顯示存貨為0的套件組合產品
   * _修正附註_：此套件組合產品未使用其他庫存顯示於其他網站上。
* _ACP2E-2794_： [雲端]產品清單的關鍵問題為空白空間
   * _修正附註_：當產品設定為「無庫存」時，系統現在可正確顯示產品清單，不含空白字元，確保可用產品顯示一致且準確。 之前，將產品設為「無庫存」會導致產品清單中出現空白字元，中斷版面配置，並可能讓客戶感到困惑。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>，<https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_：啟用MSI取貨商店時無法送出訂單
   * _修正附註_：改善存貨效能，可建立出貨並備有許多店內取貨的來源
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_： Cron重新索引無法在前端更新產品可用性
   * _修正附註_：之前，透過REST API更新延期交貨狀態後，產品在前端沒有庫存。 現在，透過REST API更新延交訂單狀態後，產品會以庫存顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_：啟用MSI時，將影像新增至可設定的功能無法運作。
   * _修正附註_：使用詳細目錄模組時，可設定產品的影像上傳現在會如預期般運作。 先前無法上傳影像
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_：清潔M2.4.7-p3中的套件組合產品+ MSI發生問題
   * _修正附註_：之前，對於與相同簡單產品重複之後的存貨組合產品，無法儲存簡單產品。 套用此修正後，簡單產品便可順利儲存，不會有任何例外。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39358>
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/0208e433>

### 庫存/MSI、搜尋

* _ACP2E-3413_：當SKU未設為可搜尋的屬性時，所有產品都會使用[is_out_of_stock] = 1編制索引
   * _修正備註_：修正後，目錄搜尋索引中的「is_out_of_stock」是正確的，即使sku無法搜尋。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/5b21b7af>

### 訂購

* _AC-10828_：後端訂單總覽畫面：訂單料號層次上未顯示延期交貨數量
   * _修正備註_：系統現在會在後端訂單總覽畫面的quantity欄中顯示延期交貨料號的數目。 這可確保使用者可以準確地追蹤順序中所有專案的狀態。 以前，「數量」欄位只會顯示已訂購、已開立商業發票及已出貨的料號數目，而不會顯示延期交貨的料號數目。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38252>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38320>
* _AC-10994_： [問題]訂單地址轉譯器中使用的存放區識別碼錯誤
   * _修正附註_：系統現在會在轉譯訂單位址時，正確使用與訂單相關聯的商店ID，確保位址已根據其各自的商店ID正確格式化。 先前，系統未正確使用目前的商店ID，若需要傳送來自不同商店的多份訂單電子郵件，可能導致地址格式不正確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38412>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37932>
* _AC-11690_：加入處理器快取問題
   * _修正附註_：系統現在可正確套用每個反複專案的JoinProcessor，即使連續呼叫亦然，確保資料擷取準確。 以前，JoinProcessor錯誤地標籤為已在連續反複專案中套用，導致資料擷取錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/27504>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37550>
* _AC-11798_： [問題]送貨價格在列印的pdf中顯示不同
   * _修正備註_：系統現在會根據稅捐組態設定，以列印的PDF正確顯示出貨價格，確保銷售訂單商業發票檢視頁面與列印商業發票之間的一致性。 以前，無論稅捐組態設定為何，列印PDF中顯示的運費都會排除稅捐。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38608>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38595>，<https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_：使用已刪除的父可設定產品重新排序
   * _修正附註_：現在使用已刪除的產品重新排序時，系統不會顯示要重新排序的重新排序按鈕
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39568>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39601>
* _AC-13924_： [問題]修正錯誤\Magento\Sales\Model\Order\Email\Container\Template：：$id屬性
   * _修正備註_：這修正了\Magento\Sales\Model\Order\Email\Container\Template：：$id的錯誤phpdoc，實際上$id是type int，但實際上是string。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39151>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_：無法在現有訂單詳細資料中儲存電話號碼的變更
   * _修正附註_：現在，使用者可以在訂單地址的電話欄位中新增國際首碼00
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38201>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_：無法傳送電子郵件
   * _修正附註_：系統現在包含組態選項async_sending_attempts，可指定在停止前嘗試傳送電子郵件的次數，改善啟用「非同步傳送」時失敗的電子郵件傳送處理。 先前，如果電子郵件無法傳送，系統會持續嘗試重新傳送，導致系統記錄中出現無休止的錯誤訊息回圈。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_： [Cloud]部分退款部份出貨的訂單狀態已變更為完成
   * _修正備註_：發行銷退折讓單時，如果料號尚未出貨，則訂單狀態不再變更為「已完成」。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_： [CLOUD]無法如開發檔案所示停用從管理員UI傳送電子郵件
   * _修正附註_：系統現在會正確防止在電子郵件通訊停用時傳送銷售電子郵件。 重新啟用電子郵件通訊時，將不再傳送這些電子郵件。 以往，在電子郵件通訊停用時起始的銷售電子郵件，在電子郵件通訊重新啟用後仍會傳送。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_：未全額退款的訂單已結案
   * _修正備註_：當具有未擷取付款的訂單已建立出貨時，系統現在會正確地將訂單狀態維持為「處理中」，並將商業發票狀態維持為「待處理」。 這可確保在全額退款後只將訂單標籤為「已結」。 先前，若為具有待處理商業發票的訂單建立出貨，則會錯誤地將訂單狀態變更為「已關閉」。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_： [Cloud]若未設定預設帳單地址，則無法在單一商店的admin中建立訂單
   * _修正附註_：現在相關的錯誤訊息「具有相同電子郵件地址的客戶已存在於關聯的網站中。」 如果客戶沒有預設帳單地址，但嘗試在其他商店建立訂單，則會顯示訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_：已傳送管理員重複下單要求
   * _修正附註_：之前，在管理面板中的「提交訂單」按鈕可能會被多次點按，或是透過重複按下「Enter」鍵來啟動，導致重複提交或提交訂單有錯誤。 現在，會防止其他動作，直到完全處理完訂單為止，確保只提交一個訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_：即使沒有付款方式，管理員還是可以下訂單
   * _修正備註_：當付款方式重新出現在可用付款清單中時，現在會保留先前選取的付款方式。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3518_：從「管理員」建立訂單後，專案重複 — Mozilla Firefox瀏覽器
   * _修正附註_：在admin中建立訂單時，使用「Add Products by SKU」新增的產品在Firefox中不再重複。

### 訂單，付款

* _ACP2E-3233_：即使沒有付款方式，管理員還是可以下訂單
   * _修正附註_：以前，商家可以從管理員面板下訂單，而無需選取付款方式。 現在，商家需要一種付款方式才能繼續下訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/fd5cf3af>

### 訂購，退貨

* _ACP2E-2982_：訂單退款導致重複銷退折讓單
   * _修正備註_：當同時執行兩個相同的請求時，透過REST API發出退款，將不再建立重複的銷退折讓單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>

### 訂購，稅金

* _ACP2E-3003_： [CLOUD] RESTFUL訂單API中的base_row_total在啟用跨境交易並套用優惠券折扣時不正確
   * _修正備註_：現在，當啟用跨境交易並套用優惠券折扣時，會從RESTFUL訂單API傳回正確的base_row_total。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>

### 其他

* _BUNDLE-3394_： [Braintree]將交易儲存為transactionid-refall的線上退款
* _BUNDLE-3421_： [Braintree] + [雲端]Braintree （信用卡）訂單無法分割費用
* _BUNDLE-3422_： [Braintree] [雲端]Braintree SSL憑證將於6月30日前到期
* _LYNX-339_： GQL查詢中傳回的private_content_version Cookie
   * _修正附註_：修正在GraphQL查詢中傳回private_content_version Cookie （即使工作階段Cookie已停用）的問題。 工作階段如預期般停用時，GraphQL回應中不再包含Cookie。
* _LYNX-366_：實體禮卡查詢中電子郵件prop的伺服器錯誤
   * _修正附註_：修正實體禮品卡上sender_email和recipient_email查詢導致伺服器錯誤的問題。 這些Prop現在可正確傳回虛擬禮品卡，且查詢行為一致。
* _LYNX-380_： CartItemInterface中的is_available屬性會一律傳回false （針對可設定的產品）
   * _修正附註_：修正CartItemInterface中is_available屬性針對庫存中可設定產品一律傳回false的問題。 現在，在適用的情況下，它會將可用性正確反映為true。
* _LYNX-382_： CartItemInterface中的is_available屬性會傳回true，即使可銷售存貨低於產品的數量亦然
   * _修正附註_：修正CartItemInterface中is_available屬性不正確地傳回true （即使購物車專案數量超過可銷售存貨）的問題。
* _LYNX-395_： ProductInterface中的only_x_left_in_stock屬性在可設定產品上不準確
   * _修正附註_：修正ProductInterface中only_x_left_in_stock屬性未正確反映購物車中可設定產品變體的可用庫存的問題。 現在，only_x_left_in_stock值正確對應至實際變動存貨層次，確保在Cart GQL查詢中傳回正確的存貨資料。
* _LYNX-399_：將簡單產品新增到分組產品中的購物車時，會傳回預留位置縮圖
   * _修正附註_：修正將簡單產品（群組產品的一部分）新增至購物車時，即使產品已指派影像，仍傳回預留位置縮圖影像的問題。
修正詳細資料：
* 產品縮圖現在可以正確顯示指派的影像（若有）。
* 縮圖選取專案依照下的管理員設定：
商店>設定>銷售>結帳>購物車>分組產品影像。
這可確保根據商店設定分組產品的一致縮圖行為。
* _LYNX-400_：客戶的自訂選項屬性無法使用整數值
   * _修正附註_：修正當傳回的值為整數時，客戶的自訂選項屬性無法運作的問題。 自訂選項現在可正確處理並按預期傳回整數值。
* _LYNX-402_：嘗試取得具有動態價格的套件組合產品的priceDetails時發生內部伺服器錯誤
   * _修正附註_：解決透過GraphQL查詢具有動態定價之套件組合產品的price_details時，導致內部伺服器錯誤的問題。 此增強功能使用設定了動態定價的套件組合產品時，可確保穩定的購物車查詢。
* _LYNX-403_： only_x_left_in_stock可設定產品的傳回值一律為0
   * _修正附註_：解決使用具有選項的父SKU新增時，可設定產品的only_x_left_in_stock屬性一律傳回0的問題。
修正詳細資料：
* only_x_left_in_stock值現在會正確反映所選子變體而非父SKU的庫存。
* 這可確保在購物車和產品頁面中針對可設定的產品變化正確顯示庫存量。
* _LYNX-405_： GraphQL錯誤：自訂選項查詢中不支援的&#39;file&#39;型別
   * _修正附註_：修正GraphQL針對購物車專案中的型別「檔案」的可自訂選項傳回錯誤的問題。 現在，查詢可正確傳回所有可自訂選項型別的詳細資料，包括檔案型選項，而不會導致錯誤。
* _LYNX-411_： GraphQL查詢未傳回可自訂產品的正確計算正常價格
   * _修正附註_：修正GraphQL未傳回正確計算出的可自訂產品一般價格的問題。 現在，查詢會正確包含計算出的正常價格，並在價格屬性中套用可自訂的值（例如$125），以反映基本價格和任何其他自訂成本。
* _LYNX-412_：透過EstimatedTotals保留的AppliedTaxes具有更新的變動
   * _修正附註_：修正EstimatedTotals變異的問題，此問題導致即使更新地區或郵遞區號後，購物車仍持續存在套用的稅捐。 現在突變會在地區與郵遞區號值之間變更時，正確更新套用的稅捐，確保根據目前的購物車資料，僅套用正確的稅捐規則。
* _LYNX-420_： CartItemInterface中的is_available屬性會傳回true，即使可銷售存貨低於產品的數量亦然
   * _修正附註_：修正CartItemInterface中is_available屬性不正確地傳回true的問題，即使可銷售存貨低於要求的產品數量亦然。 現在，當產品的數量超過可用庫存時， is_available欄位會正確傳回false 。
* _LYNX-421_：無法新增優惠券至購物車，僅提供送貨折扣
   * _修正備註_：修正無法將優惠券套用至購物車以取得僅送貨折扣的問題。 使用不含產品條件的銷售規則時，抵用券現在可正確套用至出貨金額，確保將預期折扣套用至出貨成本。
* _LYNX-425_：產品正常價格，12位小數且值錯誤
   * _修正備註_：修正套用多個稅率時，product.price_range.maximum_price和minimum_price GraphQL路徑中的regular_price值與目錄價格不符的問題。 regular_price現在會一致地反映所有稅捐組態的型錄價格，確保「購物車摘要」中的單位訂價、總列成本計算及折扣檢查正確無誤。
* _LYNX-430_：購物車上的GraphQL伺服器錯誤，沒有存貨的套件產品
   * _修正附註_：修正當擷取購物車時，GraphQL傳回內部伺服器錯誤的問題，購物車包含具有無庫存專案的捆綁產品，尤其是當查詢包含itemsV2屬性時。 GraphQL現在會如預期正確傳回專案清單，並將相關的錯誤訊息附加至隨附的產品專案專案。
* _LYNX-441_：無法建立具有自訂屬性的位址
   * _修正附註_：修正createCustomerAddress突變無法建立具有必要自訂屬性的地址的問題。 變異現在會在提供適當的裝載時，正確處理自訂位址屬性。
* _LYNX-447_：隨附產品上只有_x_left_in_stock的購物車出現GraphQL伺服器錯誤
   * _修正附註_：修正擷取GraphQL查詢中包含only_x_left_in_stock欄位的套件式產品的購物車導致內部伺服器錯誤的問題。 GraphQL現在會正確傳回only_x_left_in_stock欄位的浮點數或null，而不會出現錯誤。
* _LYNX-464_：移除購物車中其他可設定產品不足的產品時，GraphQL發生錯誤
   * _修正附註_：修正嘗試從購物車移除庫存產品時，如果購物車也包含庫存不足的可設定產品，會導致「無法取得請求數量」GraphQL錯誤的問題。 移除現在可如預期運作，不會觸發錯誤。
* _LYNX-469_：由於SKU的變異區分大小寫，因此無法新增產品
   * _修正附註_：解決使用具有不同大小寫的SKU時，addProductsToCart突變傳回「PRODUCT_NOT_FOUND」錯誤的問題。 變異現在會以不敏感的方式處理SKU，確保與目錄服務查詢和PDP行為一致。
* _LYNX-603_： Product attribute > trademark short form ™傳回為™
   * _修正附註_：解決GraphQL API產品名稱的字元編碼問題
* _LYNX-619_： updateCustomerEmail突變問題
   * _修正附註_：解決updateCustomerEmail突變的問題，此問題導致沒有必要自訂屬性的客戶（在建立帳戶後新增）無法更新其電子郵件。
* _LYNX-626_：使用pickup_location_code時突變setShippingAddressesOnCart擲回錯誤
   * _修正附註_：修正使用pickup_location_code而未指定customer_address_id或address時，setShippingAddressesOnCart突變傳回錯誤的問題。 變異現在可正確設定只包含pickup_location_code的送貨地址。
* _LYNX-627_： CustomerOrder.items_eligible_for_return清單必須與訂單專案一致
   * _修正備註_：解決訂單中退貨資格的不一致：
1. CustomerOrder.items_eligible_for_return清單現在與實際訂單料號一致。
2. 若已傳回完整數量，OrderItemInterface.eligible_for_return欄位會正確傳回false。
3. CustomerOrder.items_eligible_for_return現在只包含尚未在退回處理中的料號。
* _LYNX-628_：新增quantity_return_requested欄位
   * _修正備註_：已將quantity_return_requested欄位新增至OrderItemInterface，讓您識別已提交退貨的料號數量。 這樣會增強現有quantity_returned欄位的回訪追蹤功能。
* _LYNX-634_：為所有專案建立完整數量的退貨之後，訂單可用動作不得包含RETURN
   * _修正附註_：修正GraphQL customer.orders查詢中available_actions欄位在為所有專案建立完整退貨後錯誤包含RETURN的問題。 現在當傳回程式完成後，就會正確移除RETURN動作。
* _LYNX-637_： Storefront相容性 — 更新邏輯以取得含有前置詞的資料表名稱和其他次要的改善
   * _修正附註_：已更新邏輯以擷取具有首碼的資料表名稱（與SCP變更相關）。
* _LYNX-643_：使用setBillingAddressOnCart GQL的same_as_shipping欄位時，無法儲存在通訊錄中
   * _修正附註_：修正使用setBillingAddressOnCart GraphQL突變（將same_as_shipping欄位設為true）時，送貨地址未儲存至客戶通訊錄的問題。 現在，送貨地址已如預期正確儲存。
* _LYNX-650_：標準化變異中的order_id
   * _修正附註_：標準化變動的order_id輸入，並更新訂單取消確認電子郵件範本，以公開增量id而非訂單id。
* _LYNX-651_： CustomerOrder未顯示訂單註解
   * _修正附註_：解決CustomerOrder的問題，在來賓與客戶訂單GraphQL查詢中包含訂單註解。
* _LYNX-652_： original_item_price不得包含任何折扣
   * _修正備註_：已更新GraphQL購物車專案價格中original_item_price的邏輯，以排除折扣。
* _LYNX-681_：當其中一個套件產品無存貨時，套件產品仍會顯示「IN_STOCK」
   * _修正附註_：解決即使其中一個套件專案無庫存，套件產品的product.stock_status仍顯示「IN_STOCK」的問題。
* _LYNX-686_：如果客戶存在已刪除的自訂屬性的值，則客戶查詢會傳回內部伺服器錯誤
   * _修正附註_：修正當刪除的自訂屬性仍有儲存值時，客戶查詢傳回內部伺服器錯誤的問題。 現在，如果要求不存在的屬性，則會傳回適當的錯誤訊息。 刪除客戶自訂屬性時，必要的快取會失效。
* _LYNX-687_：傳回和取消確認連結的動作引數
   * _修正附註_：已新增動作引數，以傳回和取消確認電子郵件相關連結
* _LYNX-688_：訪客使用者確認URL已重新導向至訂購狀態頁面，因為它遺失orderRef （針對GuestRMA）
   * _修正附註_：新增orderRef引數至來賓RMA確認電子郵件中的連結
* _LYNX-689_：訪客使用者確認URL已重新導向至訂購狀態頁面，因為它遺失orderRef
   * _修正附註_：已新增orderRef引數至來賓訂單取消確認電子郵件中的連結
* _LYNX-690_：停用RMA時客戶查詢發生問題
   * _修正附註_：已更新GraphQL邏輯，以確保即使全域停用RMA，也能存取先前建立的傳回。 已移除錯誤訊息以改善店面UX，確保客戶仍可檢視其過往回報。
* _LYNX-696_：套用衝突優惠券時，GraphQL未傳回更新的購物車資料
   * _修正附註_：修正套用優先順序較高的衝突抵用券時，導致錯誤訊息未傳回更新購物車資料的問題。 現在，當新的抵用券使現有抵用券失效時，突變會正確傳回套用有效抵用券的購物車。
* _LYNX-699_：無法為placeOrder GQL上不可為空的欄位「TaxItem.title」傳回null
   * _修正附註_：修正因不可為空的欄位TaxItem.title具有null值而導致placeOrder突變失敗並出現內部伺服器錯誤的問題。 現在，欄位一律會傳回有效值，確保成功下訂單。
* _LYNX-702_： EstimateTotals：虛擬產品型別的折扣為Null
   * _修正備註_：解決當折扣代碼套用至包含虛擬產品的購物車時，estimateTotal突變傳回null折扣的問題。
* _LYNX-703_：組合產品未傳回正確的折扣百分比和金額
   * _修正備註_：已針對目錄料號價格引入新屬性「catalog_discount」及「row_catalog_discount」，以在列與單一料號層次顯示正確的折扣金額與百分比。
* _LYNX-714_：產品層級的贈品訊息設定
   * _修正附註_：修正全域停用時，未在產品層級套用禮品訊息的問題。 現在，如果針對特定產品啟用贈品訊息，則可使用updateCartItems變異來成功新增贈品訊息，且將正確地儲存和反映贈品訊息。
* _LYNX-717_：從購物車專案移除禮品包裝時發生問題
   * _修正附註_：修正使用updateCartItems突變從購物車專案移除禮品包裝未如預期運作的問題。 現在，套用和移除贈品包裝的功能皆正確無誤。
* _LYNX-751_：符合的註冊客戶功能在Boilerplate中無法運作，而且需要為來賓啟用trackViewedProduct突變。
   * _修正附註_：公開trackViewedProduct突變，以追蹤客戶和來賓的產品檢視事件
* _LYNX-757_：若未套用作用中的購物車規則，cart.rules查詢會傳回錯誤而非空白陣列
   * _修正附註_：修正了cart.rules查詢，在沒有套用作用中購物車規則時，傳回空陣列而不是錯誤。
* _LYNX-758_：擷取購物車專案的贈品包裝時發生問題
   * _修正附註_：已更新擷取邏輯，當全域停用但在產品層級啟用時，可傳回購物車專案的贈品包裝選項
* _LYNX-778_：安裝adobe-commerce/storefront-compatibility套件時，使用OPTIONS方法的GraphQL呼叫傳回500回應代碼
   * _修正附註_：修正安裝adobe-commerce/storefront-compatibility套件時，使用OPTIONS方法的GraphQL呼叫傳回500內部伺服器錯誤的問題。 端點現在會如預期正確傳回200/204回應。

### 其他開發人員工具

* _AC-10658_： [問題]修正visual.phtml中的HTML語法錯誤
   * _修正附註_：系統現在會正確關閉visual.phtml檔案中的開始標籤，確保使用正確的HTML語法。 之前，啟動標籤未正確關閉，導致HTML語法錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38247>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37457>
* _AC-11474_： [問題]在bin/magento maintenance：status命令中將「作用中」變更為「已啟用」
   * _修正附註_：系統現在為維護模式命令提供更準確的狀態訊息，將狀態從「作用中」變更為「已啟用」，以及從「非作用中」變更為「已停用」。 之前，維護模式命令的狀態訊息會顯示為「作用中」或「非作用中」，這可能會造成混淆。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38486>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38410>
* _AC-12571_：導覽至類別樹狀結構會導致Redis發生錯誤：「Redis工作階段超過同時連線」
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38851>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0611e750>
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
* _ACP2E-3631_： Adobe Commerce 2.4.7-p3單元測試失敗
   * _修正附註_：不需要發行說明。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/982b1c42>

### 付款/付款方式、訂單

* _AC-13699_：儲存供日後使用的紙幣付款流程信用卡詳細資料未顯示在儲存的付款方式頁面上
   * _修正備註_：儲存供日後使用的舊版信用卡資料未顯示在儲存的付款方式頁面上，而現在已修正的信用卡資料顯示在儲存的付款方式頁面上。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/96dec499>

### 付款

* _AC-13414_：信用卡（Payflow連結）付款無法運作
   * _修正備註_：在成功完成修正訂單後，使用信用卡下訂單時出現較早取得錯誤（付款遭拒）。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_：每次在檢視交易畫面上按一下擷取按鈕時，Payflow都會建立新交易
   * _修正附註_：系統現在會正確擷取交易資訊，而不需在每次按一下檢視交易畫面上的擷取按鈕時建立新的付款交易。 先前，按一下「擷取」按鈕會錯誤地為已支付的訂單建立新的付款交易。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_：加拿大貝寶商家帳戶的PDP中未顯示Paylater訊息
   * _修正備註_：系統現在會在「產品詳細資料頁面(PDP)」上正確顯示加拿大PayPal商家帳戶的PayLater訊息，而可從帳戶帳單地址或出貨來決定買方的國家/地區。 以前，由於缺少引數，不會顯示PayLater訊息，這會導致瀏覽器主控台發生錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
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
* _AC-12000_： [問題]程式碼清理並新增重要標題區塊，以及在資產之前移動重要css
   * _修正附註_：系統現在包含新的關鍵Head區塊，並在資產之前移動關鍵CSS，以便在前端進行更多自訂和效能最佳化。 過去，關鍵CSS並不位於資產之前，限制了自訂和最佳化機會。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38748>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/35580>
* _AC-12176_：當mysql主機包含連線埠資訊時，主題編譯中斷
   * _修正備註_：系統現在可以正確處理包含連線埠資訊的MySQL主機組態，確保主題編譯成功。 以前，如果資料庫連線中的MySQL主機組態包含連線埠資訊，主題編譯將會失敗。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38799>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38842>
* _AC-13471_：支援Magento CLI中的Symfony CommandLoaderInterface
   * _修正附註_：此變更允許延遲初始化命令，以縮短Magento CLI應用程式的初始化時間，直到需要命令時為止。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/29266>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_：在購物車規則中載入產品屬性時出現效能問題
   * _修正備註_：改善銷售規則的查詢效能 — 從大約150毫秒提升至單位數字ms。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_：價格部分索引效能
   * _修正備註_：透過最佳化索引程式中所使用的一些刪除查詢，已改善價格部分索引效能。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_：使用非同步訂單處理+條款與條件時，多存放區設定會拒絕訂單
   * _修正附註_：現在會處理來自啟用條款與條件之非預設網站的訂單。
在自動拒絕之前。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_： Order Rest API呼叫需要很長時間才能執行
   * _修正附註_：系統現在會在合理的時間範圍內執行Order Rest API呼叫，提高擷取大量訂單時的效能。 先前，Order Rest API呼叫執行時間過長，導致擷取大量訂單時發生延遲。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/001e5188>

### 績效、促銷活動

* _ACP2E-2617_：銷售規則索引器已停止執行
   * _修正附註_：系統現在即使有大量合併的篩選器群組，也已成功完成銷售規則索引器，確保購物車規則條件如預期套用至購物車。 以前，當合併的篩選器群組數量很大時，銷售規則索引子將無法完成，導致出現錯誤訊息並阻止套用購物車規則條件。

### 定價

* _AC-11810_： Magento2.4.6-p4訂單API簡單專案遺漏價格
   * _修正備註_：系統現在會透過Order API查詢時，正確顯示簡單產品的價格，以確保資料呈現準確。 先前，簡單產品的價格在API回應中錯誤地顯示為零。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38603>
* _AC-13855_：目錄規則中有Penny舍入錯誤
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/276e0acd>

### 產品

* _AC-10535_：可設定的關聯產品名稱中的特殊字元正在轉換成HTML實體。
   * _修正附註_：系統現在會在編輯可設定產品時，正確保留關聯產品名稱中的特殊字元，以防止這些字元轉換為HTML實體。 先前，在編輯可設定產品時，關聯產品名稱中的特殊字元會轉換為HTML實體。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38146>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38447>
* _AC-10947_： ProductRepository函式GetById未建立正確的快取金鑰
   * _修正附註_：系統現在會在ProductRepository的GetById函式中正確建立快取金鑰，無論儲存ID是以字串還是整數傳遞。 這可確保在後續呼叫時從記憶體中擷取產品，進而改善效能。 以前，由於不正確的快取金鑰建立，系統會在每次呼叫函式時從資料庫擷取產品，即使引數相同。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38384>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38433>
* _AC-11992_： [問題] [MFTF]已新增AdminClickAddOptionForBundleItemsActionGroup
   * _修正附註_：系統現在包含AdminClickAddOptionForBundleItemsActionGroup，以增強Admin面板的功能。 之前，無法使用此動作群組。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/30857>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/30838>
* _AC-13173_： [問題]修正PHPDoc區塊中的錯字
   * _修正附註_：系統現在會正確移除$helper變數宣告在PHPDoc中未知的參考變數，以提高程式碼清晰度和準確性。 先前，PHPDoc中這個未知的參考變數會造成程式碼中的混淆和潛在的不準確性。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38961>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38940>
* _AC-13423_： [問題]修正Magento >= 2.4.7中損壞的套件組合和可下載的產品頁面配置
   * _修正附註_：已修正套件組合及可下載產品頁面的配置，確保所有裝置顯示一致且正確。 先前，由於產品資訊媒體區塊重新排列，這些頁面會遇到版面問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39403>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_： AlertProcessor — 引數#2數($storeId)必須是int型別，必須提供字串
   * _修正附註_：系統現在會確認商店識別碼為正確的資料型別，以正確觸發產品警示電子郵件。 以前，由於商店識別碼中的型別不符，不會傳送產品警報電子郵件。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35602>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_： [雲端] addFilterToMap函式無法用於某些資料行
   * _修正附註_：現在，可以在順序格線中使用自訂模組。 先前使用自訂模組時發生錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3471_：類別中的[雲端]產品 — 新增產品 — 指派 — 全部選取
   * _修正附註_：使用者現在可以使用切換功能來選取或取消選取產品。

### 促銷活動

* _ACP2E-2602_：從邀請建立帳戶時看不到客戶屬性
   * _修正附註_：從邀請建立帳戶時，可以使用客戶屬性。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_：無法釋出每個優惠券限制使用的優惠券代碼，因為訂單取消而付款失敗
   * _修正備註_：系統現在會在建立或取消訂單時，立即更新優惠券使用方式，並將規則使用方式新增至佇列，以防止可能的死結。 這可確保釋放具有「每張優惠券的使用次數」限制的優惠券代碼，並且可在訂單因付款失敗而取消時重複使用。 之前，系統未發行優惠券代碼以供在此類情況下重複使用，導致出現錯誤訊息，指出優惠券代碼無效。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_： [雲端]重新索引目錄規則產品索引器擲回SQLSTATE[HY000]：一般錯誤： 2006 MySQL伺服器已消失。
   * _修正附註_：系統現在可正確處理「Magento\CatalogRule\Model\Indexer\IndexBuilder」的di.xml中的自訂「batchCount」值，以防止在目錄規則產品索引器的重新索引期間，由於大型目錄的批次大小不正確，而發生「一般錯誤： 2006 MySQL伺服器已消失」等SQL錯誤
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2926_：訪客客戶區段的[CLOUD]購物車價格規則未在購物車上套用折扣
   * _修正附註_：系統現在會正確套用訪客客戶區段的購物車價格規則，即使規則未使用抵用券亦然，以確保將適當的折扣套用至購物車。 之前，除非購物車價格規則使用抵用券，否則不會將折扣套用至訪客客戶區段的購物車。
* _ACP2E-3024_：相關產品規則的「產品相符」索引標籤中缺少「Type」屬性
   * _修正附註_：「Type」屬性現在可在「相關產品規則」模組的「要比對的產品」索引標籤中作為篩選選項使用，以取得更精確的規則定義。 之前，「要比對的產品」索引標籤中缺少此屬性，這會限制建立準確比對准則的能力。
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
* _ACP2E-3472_： [雲端]送貨計算未考慮購物車規則
   * _修正備註_：修正前，含有地區條件的購物車規則未一致套用。 修正後，正確套用具有區域條件的購物車規則。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_：發票的購物車規則SKU條件失敗。
   * _修正備註_：具有動態價格的套件組合產品折扣現在會正確反映在發票中。 以前，折扣不會反映在發票上。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_：同時套用多個購物車價格規則與折扣/特價產品時，折扣值不正確
   * _修正備註_：修正前，如果套用多個購物車規則，則整個購物車規則的固定金額未正確套用。 現在，已正確套用固定金額折扣購物車規則。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 傳回

* _ACP2E-3330_： [雲端]受限制的管理員使用者可以看到傳回功能表和按鈕
   * _修正附註_：受限制的管理員使用者現在無法存取RMA相關控制項（功能表和按鈕）。
先前受限制的管理員使用者可以看到傳回功能表和按鈕。
* _ACP2E-3443_：重新整理熒幕時傳回熒幕發生問題
   * _修正附註_：使用者可以重新整理頁面，而不發生熒幕扭曲的情況。

### SEO

* _AC-11907_：以重音符號新增URL重寫會造成無限載入
   * _修正附註_：系統現在已成功建立並功能具有重音的URL重寫，以防止在儲存過程中無限載入。 之前，以重音符號新增URL重寫會造成無限載入問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38692>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_：多重存放區錯誤的類別URL重寫為第三層級類別
   * _修正附註_：使用自訂範圍URL索引鍵為父系的子系產生正確的URL重寫
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_：「產品名稱」欄位中的雙位元組字元（特殊字元）會封鎖後端中的產品建立
   * _修正附註_：已新增新設定，可讓您將音譯套用至產品URL。 設定可在以下位置使用：商店>設定>目錄>目錄>搜尋引擎最佳化：「為產品URL套用音譯」
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_：在一個商店群組中建立多個商店的url_rewrite專案不正確
   * _修正附註_：修正前，您只能在編輯產品時產生網站層級的URL重寫。 修正中引進了新的設定（商店>設定>目錄>目錄>搜尋引擎最佳化，「產品URL重寫範圍」搭配選項「商店檢視」、「網站」），可讓您在商店檢視或網站層級產生URL重寫。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/2d627301>

### 銷售

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

* _AC-11855_： [問題]遺失字型CSP付款器快顯功能表
   * _修正附註_：系統現在允許載入字型&#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;，而不違反內容安全性原則指令，確保正確顯示Paylater快顯視窗。 先前，由於違反內容安全性原則指示，導致播放器快顯視窗顯示問題，因此拒絕載入字型。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38624>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37401>
* _AC-12035_： [問題]更新js.js DOM文字重新解譯為HTML
   * _修正附註_：使用innerText可避免HTML插入的風險，因為這些屬性會自動逸出所提供文字中的任何HTML特殊字元。 此修正將輸入視為純文字而非解譯的HTML，有助於防止跨網站指令碼(XSS)漏洞。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_： ReCaptcha V2在德文語言簽出時顯示不正確
   * _修正附註_：先前來自結帳電子郵件地址下方的recaptcha對於長字如德文的語言顯示為無樣式。 之後，recaptcha看起來會像其他區域的所有recaptcha元素一樣。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_：管理員登入的驗證碼不需要與某些使用者互動
   * _修正附註_：已如預期驗證管理員登入的ReCaptcha
   * _GitHub程式碼貢獻_： <https://github.com/magento/security-package/commit/8f64ab3c>

### 送貨

* _AC-10757_： [問題]修正tracking.phtml中的錯字 — 將JS函式「currier」重新命名為「carrier」
   * _修正附註_：系統現在正確使用辭彙「carrier」，而不是在順序追蹤範本中使用的JavaScript處理常式函式中拼錯的「currier」，以確保正確的函式命名和程式碼明確無誤。 先前，我們使用拼字錯誤的辭彙「currier」，這可能會導致程式碼基底的混淆和不一致。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/34523>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/33414>
* _AC-11938_： UPS REST 「出貨不能以KGS/IN、LBS/CM或OZS/CM作為測量單位」
   * _修正附註_：請確定結帳和購物車中應該顯示UPS費率。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38618>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/493e01f5>
* _AC-12938_： UPS REST devdoc中的「沙箱」和「prod」安裝指示更新
* _AC-13172_： [問題]客戶地址的變數拼字正確
   * _修正附註_：系統現在會正確拼寫客戶地址的變數，以確保前端帳戶區域的正確顯示。 以前，這些變數的拼字錯誤可能會導致本機程式碼審查期間發生錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32817>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_：追蹤視窗顯示錯誤的預期傳送日期
   * _修正備註_：顯示Fedex電信業者的正確交貨日期。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_：即使套用免運費，仍顯示表格費率
   * _修正附註_：即使優惠券套用後免費送貨變為可用，現在仍會顯示表格費率送貨方法
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_： MFTF測試AdminCreatingShippingLabelTest失敗，因為Jenkins環境中未新增認證
   * _修正備註_： mftf測試修正
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_： FedEx追蹤API無法搭配REST認證使用
   * _修正附註_：先前的FedEx整合不需要額外的API金鑰來追蹤API。 現已新增新設定，以支援追蹤API金鑰。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_： [雲端] FedEx交涉費率未傳回REST
   * _修正備註_：在修正之前，FedEx帳戶的特定費率未在回應時傳送，即使根據FedEx檔案他們本應傳送也一樣。 修正後，帳戶特定費率會透過變更我們這邊的請求在回應中傳送。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/55615e61>

### 測試和預覽

* _ACP2E-2901_：如果原本是透過執行更新而新增，則未儲存排定的更新設定
   * _修正備註_：系統現在會在目前執行的更新中修改產品屬性時，正確清除後續排程更新中的產品屬性值。 先前，當產品屬性被執行的排程更新修改時，無法在建立新的排程更新時清除此類屬性值，這要求使用者在建立後重新編輯它們。
* _ACP2E-2999_：購物車價格規則開始日期和結束日期問題未與中繼更新同步
   * _修正備註_：根據購物車價格規則暫存的更新儲存日期。
* _ACP2E-3104_：中繼預覽中出現JS錯誤
   * _修正附註_：現在form-mini-stub.js檔案已成功載入，開發人員工具中沒有任何Js語法錯誤。
* _ACP2E-3162_：無法更新產品特殊價格階段內容
   * _修正附註_：系統現在允許在價格更新行銷活動開始後，編輯行銷活動的結束日期，確保使用者可以對其行銷活動進行必要的調整。 先前，嘗試更新作用中行銷活動的結束日期時擲回錯誤，導致使用者無法進行變更。
* _ACP2E-3453_：使用唯一自訂類別屬性時無法更新排定的更新
   * _修正附註_：修正如果類別具有唯一屬性，則無法更新類別排程更新的問題
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>

### 目標定位

* _AC-9432_： [問題]允許在維護允許清單中使用CIDR範圍
   * _修正附註_：系統現在支援在維護模式允許IP清單中使用CIDR範圍，讓一系列IP位址略過維護模式。 以前，維護模式僅允許IP清單允許個人IP地址繞過維護模式。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37943>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/30699>

### 稅金

* _AC-13295_： [問題] Feature/php8.1建構函式屬性升級wee圖形ql
   * _修正附註_：將模組中的所有屬性全部取代為建構函式屬性升級wee圖形ql：
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39309>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_：固定產品稅(FPT)無法使用可設定的產品
   * _修正附註_：可設定產品變數正常運作的FPT。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>

### 測試架構

* _AC-11654_：由於JSON欄型別，整合測試未通過testDbSchemaUpToDate
   * _修正附註_：系統現在會在整合測試期間正確辨識資料庫結構描述中的JSON資料行型別，避免因資料庫結構描述與宣告式結構描述不符而造成測試失敗。 以前，系統錯誤地將JSON欄型別識別為MariaDB中的LONGTEXT，導致整合測試失敗。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_： [問題] PHPDoc更正拼字
   * _修正附註_：系統現在可正確辨識IDE中已棄用的方法，因為PHPDoc有拼字校正。 之前，PHPDoc中的拼字錯誤會導致IDE無法辨識某些已棄用的方法。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/31399>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/31398>
* _AC-13478_： MAGETWO-95118：在工作階段過期後，檢查永久購物車的行為
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_：整合測試失敗Magento\NegotiableQuote\Controller\Quote\DownloadTest：：testCompanyManagerDownloadWithNQSubPermission
* _AC-13722_： [資料庫比較]如果資料庫包含有關無條件目標規則的記錄，會發生嚴重錯誤
   * _修正備註_：如果資料庫包含目標規則的記錄，且沒有任何條件，則較早前會收到嚴重錯誤，但在修正資料庫比較工具成功通過且沒有嚴重錯誤之後。
* _AC-13848_：修正靜態測試，以啟用3d方擴充功能的使用方式
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_： [執行期間或記錄中未顯示內部]夾具套用失敗
   * _修正備註_： &#39;-
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_： [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _修正附註_：修正mftfs
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>

### UI框架

* _AC-12128_： Prototype.js安全性弱點修正CVE-2020-27511
   * _修正附註_：系統已更新，以解決Prototype.js 1.7.3中的安全性弱點CVE-2020-27511，進而加強系統的整體安全性。 在此更新之前，系統可能會因為移除精心製作的HTML標籤而遭受規則運算式拒絕服務(ReDOS)攻擊。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_： Grunt Less使用pub/前置詞作為原始程式集
   * _修正備註_：系統現在會在使用grunt時，針對路徑產生較少/css來源地圖（不含/pub前置詞），因此不需要在Web伺服器設定中進行因應措施。 之前，在原始碼對應路徑中使用/pub首碼時，需要在Web伺服器中指定特定的設定才能正常運作。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38837>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38840>
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
* _AC-1306_：正在為停用的模組部署靜態內容
   * _修正附註_：系統現在會從最終的CSS輸出檔案中排除與已停用模組相關的CSS，確保不會載入不必要的樣式。 以前，與已停用模組相關的CSS會包含在最終的CSS輸出檔案中，導致載入額外且不必要的樣式。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/24666>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32922>
* _AC-13459_：「無庫存」排序有最小庫存臨界值的不一致行為
   * _修正備註_：系統現在會根據存貨層次正確排序目錄中的產品，遵循設定的「最小存貨臨界值」，並一致地將無存貨專案移至清單底部。 先前，排序行為不一致，專案根據其庫存量並非總是以正確順序出現，而且在儲存、重新整理或修改類別階層後，排序的變更可能無法預測地發生。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_：針對require.js載入問題，建議改善錯誤報告功能
   * _修正附註_：此PR可改善必要專案無法載入元件時的錯誤訊息。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36761>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38971>
* _AC-14004_： PHP 8.4取代錯誤導致2.4-develop中的組建失敗
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_： [問題]請勿在前端載入後端區塊內容
   * _修正附註_：系統現在會確保前端未載入後端區塊內容，防止建立不必要的後端工作階段和潛在的工作階段鎖定。 以前，系統在前端錯誤載入後端區塊內容，導致建立後端工作階段和潛在的工作階段鎖定。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37617>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36368>
* _AC-9168_： [問題]移除不必要的指令碼檢閱摘要
   * _修正附註_：系統現在會從評等區段中移除不必要的JavaScript指令碼，而使用內嵌CSS樣式以獲得更有效率、更可讀的程式碼，藉此最佳化頁面載入時間。 以往，針對評分割槽段使用JavaScript指令碼可能會導致頁面載入時間變慢。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37776>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_：啟用Recaptcha時檢查禮品卡餘額時發生例外狀況
   * _修正附註_：使用者將可以在檢視和編輯購物車畫面中擷取禮品卡餘額。 以往，啟用reCAPTCHA時不會顯示這些詳細資料。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_： [說明]功能要求ADA合規性
   * _修正附註_：系統現在會移除不支援的CSS屬性，並將它們取代為print.css檔案中支援的屬性，以確保ADA法規遵循。 以往，使用不受支援的CSS屬性會導致瀏覽器相容性問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_： [Cloud] AC 2.4.4-p8的effect-drop.js中的混淆程式庫程式碼
   * _修正附註_：系統現在正確實作effect-drop.js程式庫，確保jQuery UI效果正常運作。 之前，effect-drop.js程式庫錯誤地以effect-clip.js程式庫覆寫，導致jQuery UI效果可能發生問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_：網站標題 | 破壞客戶歡迎區段的特殊字元
   * _修正備註_：修正後，特殊字元在客戶歡迎區段中會正確顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_：客戶區段版本因日期範圍而失敗
   * _修正附註_：如果只編輯了一個日期，則可以儲存具有日期範圍條件的客戶區段。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a52ff98f>
