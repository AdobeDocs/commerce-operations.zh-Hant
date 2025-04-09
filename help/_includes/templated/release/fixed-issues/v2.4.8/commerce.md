---
source-git-commit: 3f6776e5dbbf167bbb7b4f831f9a7d4cfbfc0b74
workflow-type: tm+mt
source-wordcount: '28398'
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_：未為產品 RestAPI 的日期和時間屬性設定預設值
   * _修正附註_：預設值現在已透過RestAPI正確設定日期、日期及時間屬性
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### API、購物車和結帳

* _ACP2E-3343_：嚴重500錯誤：Magento\Framework\Webapi\Exception與Accept HTTP標頭有關
   * _修正附註_：修正後，指定「接受」標頭沒有問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>

### API， GraphQL

* _ACP2E-3348_：沒有可用於訂閱客戶獎勵點更新的graphQl
   * _修正說明_：在修正之前，客戶屬性 reward_warning_通知 無法通過 GraphQL 突變和 Rest API 調用進行更新。 現在可以更新客戶屬性 reward_update_通知。

### API、GraphQL、稅務

* _AC-12060_：當僅提供郵遞區編碼時，Luma （Rest API） 和 Graphql 都不會計算稅費。
   * _修正說明_：現在，當僅提供郵遞區號編碼時，系統會正確計算稅款，從而確保 Luma （Rest API） 和 GraphQL 的稅務估算準確。 以前，僅計算運費估算值，僅提供郵遞區號時不包括稅費。

### 帳戶

* _AC-10782_：客戶地址表單允許在名稱欄位中使用隨機碼
   * _修正附註_：系統現在會驗證客戶地址表單中「名字」和「姓氏」欄位的輸入，避免使用隨機代碼。 之前，系統允許在這些欄位中使用隨機程式碼，而不會擲回錯誤。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38331>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38345>
* _AC-10886_：管理員密碼更新。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38352>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_：我的帳戶添加地址在保存時崩潰
   * _修正說明_：系統現在可以在未顯示區域字段時正確保存客戶地址平均，防止在保存過程中崩潰。 先前，嘗試新增或編輯沒有顯示區域欄位的地址會導致例外錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38406>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38407>
* _AC-11718_：當URL大寫時重新導向回圈
   * _修正附註_：系統現在會自動將URL中的大寫字元轉換為小寫，以防止在存取首頁時發生重新導向回圈。 以前，在安全基本URL中使用大寫字元會在嘗試訪問主頁時導致連續的重新導向迴圈。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38538>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38539>
* _AC-11755_： middlename(&#39;s)未儲存給來賓帳戶
   * _修正附註_：系統現在會在結帳時正確儲存來賓帳戶的中間名，使其可在電子郵件範本中存取。 之前，中間名未儲存在報價表中，且無法在來賓帳戶的電子郵件範本中存取。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38593>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/39067>
* _AC-11919_：管理員：頁面作按鈕向左浮動而不是向右浮動
   * _修復說明_：系統現在可以將頁面作按鈕正確對齊到管理面板中粘性標題的右側，從而增強專業外觀。 以前，這些按鈕會錯誤地浮動到粘性標題的左側。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38701>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_： Magento 2.4.7 中的開發:di:信息錯誤
   * _修正說明_：系統現在在執行dev:di:info 命令時會正確顯示構造函數參數，防止發生任何錯誤。 以前，由於參數中的類型不匹配，執行此命令會導致錯誤。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38740>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_：以客戶選擇加入身分登入核取方塊無法翻譯
   * _修正附註_：系統現在允許在「商店檢視」範圍中設定「以客戶身分登入」核取方塊和「以客戶身分登入」核取方塊工具提示」欄位，以啟用不同商店檢視的翻譯。 之前，這些欄位僅在「網站」範圍設定，無法翻譯個別商店檢視。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32329>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32359>
* _AC-14299_：我的設定檔下拉式清單中的前端UI首頁按鈕不存在。（斷斷續續）
* _AC-6071_：客戶已登錄，但在前端顯示404錯誤。
   * _修正說明_：現在，當客戶登錄時，店面客戶控制面板頁面會按預期載入。 先前客户可以登入，但此頁面显示 404 錯誤。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/35838>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/36263>
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
   * _修正說明_：受限管理員用戶現在可以一致地視圖和管理客戶以及產品分配到的所有共享目錄，前提是他們有權訪問特定商店。 以前，有權訪問特定商店的受限管理員用戶無法始終查看產品分配到的所有共享目錄，或者無法查看無法保存的客戶，從而導致系統不一致。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>

### 帳戶、購物車和結帳

* _AC-2341_：“選擇”自定義 客戶 地址屬性不會呈現為新的 客戶 地址
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
   * _修正說明_：系統現在可以正確驗證數據，並以“取代”行為隱藏產品導入過程中的“匯入”按鈕，從而防止任何意外的數據替換。 以前，系統錯誤地驗證資料並顯示「匯入」按鈕，導致潛在的資料不一致。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_： [錯誤] Magento 2.4.7 不允許使用帶有大寫字母檔擴展名的產品照片。
   * _修正附註_：系統現在接受具有大寫字母副檔名的產品影像上傳，以確保順利的產品建立程式。 以前，帶有大寫字母檔擴展名的圖像上傳被拒絕，迫使使用者將檔擴展名更改為小寫。
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
   * _修復說明_：系統現在可以正確驗證和導入包含特殊字元的產品CSV檔，從而成功傳輸數據。 以前，嘗試導入具有特殊字元的產品CSV檔會導致錯誤，從而阻止導入過程。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_：當密碼重設請求的最大數量“設置為大於 0 時，例如：3 ，”在取消限制之前發送超過限制錯誤消息，即從第二次開始
* _AC-13768_：雖然密碼重設請求的最大數量“設置為 0（ diabled）、”從第 2 次發送超出限制的錯誤消息”
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
* _ACP2E-2787_：商店視圖名稱中的撇號替換為”
   * _修正注意_：網格的商店視圖篩選器現在可以正確显示撇号
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38395>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_：圖示上傳無法驗證.ico文件
   * _修復說明_：文件驗證錯誤已更新為“檔案驗證失敗。 請驗證存儲配置中的影像處理設定。 以前，它只是“檔案失敗驗證”。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_:P ageBuilder 中的圖庫顯示舊圖像縮略圖，而不是新上傳的圖像
   * _修正備註_：通過構建器內容中的圖庫，重新生成已刪除並重新上傳的同名媒體頁面圖片圖像預覽。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/60140cd2>， <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_：通過具有不同角色範圍覆蓋/刪除產品中現有相關產品信息的管理員用戶保存產品
   * _修復說明_：以前，在修復之前，當輔助管理員用戶按下保存按鈕而不更改相關產品時，相關產品已重置並變為空。 修復后，輔助管理員用戶按下保存按鈕，產品不會重置並成功保存。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_：無法匯出超過200個訂單
   * _修正說明_：已忽略先前提交的選定 ID 請求大小的伺服器限制，將HTTP 要求從GET更改為POST以修復該問題。 以前，由於伺服器對GET 要求大小的限制，遇到了此問題。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_： 結帳頁面驗證消息不正確。
   * _修正說明_：如果任何必填字段留空，例如“地址”，伺服器端驗證將不會顯示該消息。 用戶端驗證將確保显示必填字段錯誤通知，並指出“這是必填字段”。 以前，如果任何必填欄位留空，除了使用者端驗證訊息之外，還會顯示「需要地址」訊息。
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
* _ACP2E-3294_：送貨地址狀態未自動更新
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
* _ACP2E-3408_： [建页器預覽UI問題] “頁面生成器”列中的按鈕未正確排列
   * _修正說明_：頁面生成器列中的按鈕現在已正確對齊。 之前，這些量度在頁面產生器欄中不會對齊。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_：訂購的產品報告未匯出。 404錯誤。
   * _修正注意_：「已訂購產品」報表從 CSV 和 XML 匯出後，現在按預期工作
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_：在生產模式下啟用 Js 縮小后，在控制台中錯誤 TinyMCE JS
   * _修復說明_：以前在管理面板中在生產模式下啟用JavaScript縮小會導致瀏覽器控制台中出現與 TinyMCE 6 相關的JavaScript錯誤，從而影響功能和使用者體驗。 現在，這個問題已經解決，確保TinyMCE 6順利運行而不會產生任何錯誤，平均啟用JS縮小時。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_：請求其他更改以完全完成ACP2E-3375修復
   * _修復註釋_：“-
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_：自動啟用新的 ACL 許可權
   * _修正說明_：除非明確配置，否則添加到自定義模組新許可權將不再自動授予對所有現有使用者角色的訪問許可權。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_：管理員作日誌用戶報告不顯示 adminhtml_用戶_delete 的詳細資訊
   * _修正注意_： adminhtml_用戶_delete 現在可以正確記錄重要的詳細資訊。 以前，不會為用戶刪除生成日誌。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_：從管理員下訂單時未套用送貨條件的購物車規則
   * _修正附註_：以前，如果購物車價格規則具有附帶優惠券的送貨方式折扣，則無法透過管理員UI套用。 应用此修復程序后，將從管理員UI成功應用具有特定運輸方式抵用券的購物車價格規則折扣。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/a52ff98f>， <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_： [SWATCH] 中新的十六進位代碼未正確更新
   * _修復註釋_：用戶在 Visual Swatch 顏色選取器中手動輸入的十六進位代碼不再由系統更改。 以前，由於色彩模型之間的轉換錯誤，某些HEX程式碼會經歷一些細微的調整。
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
   * _修正說明_：現在，在使用PayPal智能按鈕下訂單后，系統現在可以在交易標籤中正確顯示交易授權。 以前，按兩下“授權”按鈕後，授權交易不會顯示在交易標籤中，並且不會創建“授權”類型的新交易。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>

### 管理員UI、效能

* _ACP2E-3169_：更新至2.4.5-p8後，從管理員建立訂單時發生500錯誤
   * _修正附註_：先前，啟用HTML縮制時，無法下管理員的訂單。 現在，啟用HTML縮制後，管理員的訂單就可以成功下達。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>

### 管理UI，運輸

* _ACP2E-2519_：如果使用多配送下訂單，則“管理優惠券代碼”標籤的“已用時間”列中的抵用券代碼計數不會更新。
   * _修正說明_：之前，當使用多配送下訂單時，“管理優惠券代碼”標籤的“已用時間”列中的抵用券代碼計數不會更新。 現在，正確的計數顯示在「已使用時間」中，反映了多運輸所需的值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/4745100c>

### 管理UI、測試與預覽

* _ACP2E-3424_： [Cloud]移除遺失影像的範本導致pub/media被刪除
   * _修正說明_：在進行此修正之前，如果頁面建置器範本缺少預覽影像名稱，則 pub/媒體 資料夾會被刪除。 修復后，將僅刪除範本和預覽映射（如果找到）。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/報表

* _AC-9922_： Google Analytics CSP錯誤https://region1.analytics.google.com
   * _修正附註_：啟用Google Analytics時，系統現在可正確連線至&#39;https://region1.analytics.google.com&#39;&#39;，避免內容安全性原則(CSP)錯誤。 以前，從歐盟啟用Google Analytics和查看網站會導致 CSP 控制台錯誤，因為拒絕連接到“https://region1.analytics.google.com”。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/37750>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_：預報不起作用
   * _修正說明_：系統現支援批量載入10,000個報表，從而為超大型數據集生成高級報告數據檔。 以前，高級報告模組無法為超大型數據集生成數據文件，從而導致在執行 分析_collect_data cron 作業期間出現“MySQL 伺服器已消失”錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_：管理員訂購產品報告日期範圍可見性問題。
   * _修正附註_：使用者將能夠從「訂購產品」報表中選取任何日期。 以前，重新整理表格後，選取「起始」日期將重設「結束」日期。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_：不正確的curl標頭，導致newrelic:create:deploy-marker無法運作
   * _修正附註_：系統現在已正確設定curl標頭的格式，允許newrelic:create:deploy-marker命令在New Relic中成功建立部署標籤。 之前，不正確的curl標題無法在New Relic中建立部署標籤。
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
   * _修正注意_：訂購報告中訂單金額的貨幣符號錯誤地取自貨幣/期權/基數。 現在已更正為使用貨幣/期權/預設值以獲得準確的報告。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_： [優惠券使用方式報告中的雲] 計算不正確
   * _修正說明_：現在，通過合併「折扣稅補償金額」和「運費折扣稅補償金額」，可以準確計算抵用券報表網格中的銷售總額。 以前，計算中缺少這些金額，導致銷售總額與銷售訂單數據之間存在差異。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_：共用的「&lt;project_id>/var/tmp」發生問題
   * _修正附註_： Analytics DataExport暫存檔將使用sys tmp目錄，更適合經常存取和變更。 為了避免同一伺服器上執行多個執行個體時發生衝突，臨時路徑已更新為使用執行個體的唯一ID
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/報告，B2B

* _ACP2E-2300_：B2B - Sitemap包括未分配到共用目錄的產品/類別
   * _修正注意事項_：將生成的類別和產品Sitemap限制為僅分配給公共共享目錄和/或目錄類別權限設置的類別和產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/報表、雲端

* _ACP2E-3067_： Magento會捨棄大部分的New Relic cron交易#34108
   * _修正附註_： AC正在向NewRelic正確報告cron工作相關交易。 以前，某些cron工作相關交易在NR中顯示為「OtherTransaction/Action/unknown」
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_：NR 中的指標可能對後台事務產生誤導 - ACP2E-3067 的跟進
   * _修正說明_：背景事務 （cron） 將使用設定設置中定義的新 Relic 應用名稱
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_：2.4.8-beta102 軟體包企業版失敗，出現應用程式異常
* _ACP2E-2139_：執行部分索引時，分配給共用目錄的產品不會反映在前端
   * _修正說明_：通過 REST API 分配到共用目錄的產品現在在部分索引完成後立即顯示在店面上。 以前，產品只有在完全重新編製索引后才能看到。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-2873_： [移動版和桌面版的雲] 價格顯示在“我的報價”中不同
   * _修復注意事項_：當目錄總價部分支出時，不需要的包含稅行不再顯示在可轉讓報價中。
* _ACP2E-3044_：“我的訂單”部分上不必要的邊框
   * _修復說明_：以前創建了一個額外的容器（訂單引用）來應用其他 CSS 類，這會導致不必要的邊框行顯示在“我的訂單”部分中的訂單號下方，現在不可見。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_： sales_clean_quotes cron會從尚未核准的採購單刪除報價
   * _修正備註_： sales_clean_quotes cron工作不會刪除採購單中使用的報價
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_：下單按鈕在採購單詳細資料中消失
   * _修正注意_：修正了當產品變體在指定卡片中具有最小數量時，已批准的採購訂單隱藏下單按鈕的問題
* _ACP2E-3474_： [雲] 沒有 id = 0 的此類實體，模組 b2b
   * _修正說明_：啟用共享目錄功能后，已登錄用戶能夠將產品添加到購物車。先前將產品新增至 購物車 會導致錯誤「無此類實體，ID = 0」
* _ACP2E-3562_：從申請清單批量添加時，未顯示庫存產品的錯誤消息
   * _修正說明_：在修正之前，無論未能添加到購物車的產品數量如何，都會顯示成功消息。 現在，對於已成功添加到購物車的產品和失敗的產品，將顯示單獨的消息。
* _ACP2E-3628_：計劃更新後的SKU更新問題導致產品許可權不正確（-2 拒絕）
   * _修正說明_：使用過去的計劃更新修改產品的SKU不再會導致有權查看該產品的共享目錄客戶無法訪問該產品。

### B2B，目錄

* _ACP2E-2860_：使用 NoDDL 和類別許可權時重新索引期間可見的產品/類別
   * _修正附註_：在執行目錄許可權索引時，避免在店面受限制的類別及其內容上顯示。

### B2B，框架

* _AC-9607_：篩選公司格線，然後嘗試格線CSV匯出會失敗並擲回例外狀況
   * _修正附註_：系統現在允許管理面板中的公司格線資料成功CSV匯出，即使套用「未結餘額」和「公司型別」等篩選條件亦然。 以前，套用特定篩選條件並嘗試匯出網格資料會導致失敗並擲回例外狀況。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/44cef3a9>

### B2B、GraphQL

* _ACP2E-3391_： [雲端]透過graphql呼叫建立公司時無法設定custom_attributes
   * _修正附註_：修正後，可以使用graphql要求建立公司期間，為公司管理員設定「custom_attributes」屬性。

### Braintree

* _AC-14293_: Admin express checkout button is disabled.
* _套件–3367_：透過LPM付款
   * _修正附註_：系統現在會在初次載入時正確轉譯本機付款方法(LPM)，即使登入客戶的送貨與帳單地址不符亦然，以確保順利結帳。 先前，客戶的送貨地址與帳單地址不符會導致LPM無法呈現，進而在結帳時造成潛在中斷。
* _BUNDLE-3368_：可設定為虛擬子產品
   * _修正附註_：系統現在允許擁有虛擬子產品之可設定產品的快速付款方式，以確保順利結帳。 以前，將具有虛擬子產品的可設定產品新增到購物車時，無法使用快速付款方法。
* _捆綁 3369_：CVV 驗證失敗錯誤
* _BUNDLE-3370_：通過帳戶區域進行保險存儲問題 247
   * _修正說明_：系統現在允許客戶跨多個網站保存新卡片或PayPal帳戶資訊，而不會遇到授權錯誤。 以前，客戶無法跨不同網站保存新的付款方式，並收到授權錯誤消息。
* _BUNDLE-3371_：從不同國家寄送地址
   * _修正備註_：系統現在允許從不同國家/地區運送至地址時，處理交易而不會發生錯誤，以確保順利結帳。 以前，嘗試從不同的國家/地區傳送地址會導致主控台錯誤，儘管前端沒有明顯的錯誤。
* _BUNDLE-3372_：信用卡 — Teardown函式
   * _修正附註_：系統現在會在客戶從付款頁面導覽回送貨頁面時，正確處理Braintree PayPal元件的拆卸，避免任何錯誤，並確保PayPal Express按鈕正確呈現。 先前，從付款頁面導覽回送貨頁面時，有時會因嘗試拆卸Braintree PayPal元件而發生錯誤。
* _BUNDLE-3373_： PayPal Express的送貨回呼
   * _修正說明_：系統現在可以在 PayPal Express 模式中正確顯示可用的配送方式，允許客戶在繼續審核頁面或完成交易之前選擇他們喜歡的配送方式。 以前，PayPal Express 模式中沒有可供選擇的運輸方式，要求客戶在單獨的評論頁面中選擇一種運輸方式，然後才能完成交易。

### 捆

* _AC-10826_：店面捆綁包複選框驗證錯誤消息計數大於 1
   * _修復說明_：當按兩下「添加到購物車」按鈕而不為捆綁產品選擇任何複選框選項時，系統現在僅顯示一條驗證錯誤消息。 以前，系統會針對每個未選中的複選框顯示多則驗證錯誤訊息。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_：Magento在與測試案例相關的某些順序中引發異常
   * _修正說明_：系統現在可以在各種測試情況下正確處理“sendGuestPaymentInformation”步驟，防止拋出Magento異常。 以前，這些異常是由於無效付款方式而發生的，導致測試多種情況失敗。

### 購物車和結帳

* _AC-10660_：在比較產品頁面中將產品添加到購物車時，異常處理不正確
   * _修正注意_：從比較產品頁面將產品添加到購物車時，系統現在可以正確處理異常，並在控制器中顯示消息管理器消息。 以前，異常會導致傳回 JSON 編碼頁面，而不是正確捕獲和處理。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38200>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38257>， <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_：GTag不發送交易價格和總額。
   * _修正說明_：啟用GTag時，系統現在可以將交易價格和總金額正確發送到Google代碼，從而確保準確跟蹤電子商務數據。 以前，貨幣被錯誤地作為“所有”訂單的一部分發送，而不是與單個訂單相關聯。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/37348>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/37504>， <https://github.com/magento/magento2/pull/37349>
* _AC-11641_：[在][失敗的付款電子郵件範本中更新了結帳]相關指令
   * _修正說明_：系統現在會從虛擬產品的失敗付款電子郵件範本中正確省略送貨位址和送貨方式，確保電子郵件中僅包含相關信息。 以前，虛擬產品的失敗付款電子郵件錯誤地包含送貨位址和送貨方式。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/32781>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/32511>
* _AC-11717_：在結帳Magento 2 登入，現有客戶在 Firefox 瀏覽器中給出控制台錯誤
   * _修正說明_：系統現在允許使用者在結帳程式期間登錄，而不會在 Firefox 瀏覽器中遇到任何控制台錯誤。 以前，在結帳時嘗試以現有客戶身分登入會導致 Firefox 發生控制台錯誤。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38557>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/39509>
* _AC-11876_： [在 2.4.7 中發佈] 銷售規則回歸
   * _修正注意_：系統現在可以正確驗證銷售規則，防止在產品狀況與任何產品名稱不匹配時將抵用券代碼應用程式到購物車。 以前，當產品狀況與任何產品名稱不匹配時，可以應用銷售規則並平均運費金額提供折扣。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38671>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_： [發行] 銷售規則購物車固定計算：折扣金額不正確
   * _修正附注_：系統現在可以正確計算具有固定金額的銷售規則購物車折扣金額，確保無論購物車物料如何變化，都應用準確的折扣。 以前，當購物車商品更改時，折扣金額可能會錯誤地變化，有時會導致折扣明顯大於預期。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38694>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_： [問題] 在更改郵政編碼、運費驗證規則后，載入工具阻止運輸方式
   * _修正說明_：系統現在可以正確處理自定義送貨方式，而無需驗證運費規則，確保在結帳時更改送貨地址中的郵遞區號後，載入工具不會阻止送貨方式。 以前，在結帳時更改送貨地址中的郵政編碼會導致載入程序阻止送貨方式，並且在使用沒有運費驗證規則的自定義送貨方式時不會消失。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38742>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_：Magento 2.4.7 結帳頁面中的優惠券代碼功能無法正常工作
   * _修正說明_：系統現在在虛擬和可下載產品的結帳頁面上啟用折扣代碼/抵用券輸入欄位，允許使用者按預期應用折扣代碼。 以前，折扣代碼/抵用券輸入被禁用，按鈕標題文本顯示為“取消抵用券”，從而阻止使用者應用折扣代碼。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38826>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_：「條款與條件」複選框不允許在店面使用 HTML
   * _修正注意_：系統現在支持店面“條款與條件”複選框文本中的 HTML 格式，從而增強自定義和可讀性。 以前，複選框文字以純文本格式顯示，忽略使用的任何 HTML 標記。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_：為已登錄用戶創建的購物車價格規則錯誤地應用於未登錄用戶
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_：重新訂購會將未分配的產品添加到購物車
   * _修復說明_：以前，對於不同的商店，可以從其他商店重新訂購產品商店。 應用此修復后，只有相同的商店，當啟用客戶帳戶共享時，可以重新排序相同的範圍產品
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_：在管理中，選擇專案時左側的「購物車」和右側的「移至購物車」時不會更新
   * _修正附註_：選取專案時，左邊的「購物車」會更新，而管理員端右側的「移至購物車」則會更新。 以前，此功能不起作用，因為轉換后的購物車項未從會話中變空。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_： [雲] 銷售規則不適用於多發貨的第一個訂單
   * _修正說明_： 修正後，相同多運報價單的每個訂單的折扣將正確顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_： [Cloud]將相同產品加入購物車的生產平行要求會在購物車REST API中產生兩個個別的專案
   * _修正附註_：系統現在可正確處理多個平行請求，以將相同產品加入購物車至單一條列專案，防止為相同的SKU建立個別條列專案。 以前，透過REST API並行請求將相同產品新增到購物車會導致同一SKU出現多個條列專案。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2676_：從禮品登入Magento 2.4.4 Enterprise/Commerce訂購時發生問題
   * _修正備註_：無法從禮品登入成功購買產品的問題已解決，可以下訂單並適當地更新禮品登入。 之前，嘗試從贈品註冊處下訂單時發生錯誤，導致購買無法完成。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35432>
* _ACP2E-2704_：正在取得無法傳送Cookie。 嘗試重新排序時的「影像訊息」大小
   * _修正備註_：重新排序程式現在不會產生自己的錯誤。 它將依賴於購物車列表內置項目檢查。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_：結帳時未選擇預設送貨位址
   * _修正注意_：現在事件在啟用的地址搜尋的上下文中選擇預設送貨地址。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_： [CLOUD] graphql addProductsToCart 自定義選項的 API 問題
   * _修復說明_：GraphQL 使用不同的自定義選項正確購物車同一產品
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2917_： [更改] 商店視圖時，雲相關產品規則不起作用
   * _修正注意_：此問題已通過確認在購物車頁面上成功接收到自定義屬性值來修復。 之前，在店面購物車頁面的商店之間切換時，無法正確擷取。
* _ACP2E-2923_：結帳時將多個地址作為新客戶添加到帳戶
   * _修正附註_：系統現在只會在訂單無法建立時儲存一次新的客戶地址，以防止在訂單放置錯誤時建立多個相同的地址。 以前，每次嘗試下訂單時，系統都會儲存新地址，無論是否成功建立訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/001e5188>，<https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_：透過訪客訂單重新排序客戶訂單導致出現空購物車
   * _修正說明_：以前，通過“訂單和退貨”頁面下訂單時，客戶被重定向到登入頁面。 套用此修正後，進行重新訂購時，註冊的客戶會被正確重新導向至「檢視購物車」頁面。 該流程的工作方式與按讚訪客客戶相同。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_：角色資源有限的管理員使用者無法檢視購物車
   * _修正附註_：以前，受限制的管理員無法從相關網站的管理員面板中看到捨棄的購物車。 套用此修正後，受限制的管理員可以從管理員面板檢視捨棄的購物車。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_： [雲] 快速訂購量SKU性能
   * _修正注意_：當並非所有產品都存在購物車價格規則條件中使用的屬性以及啟用了 MAP（最低廣告價格）功能時，結帳性能得到了改善。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_：購物車中有重複的專案
   * _修正說明_：系統現在可以正確處理多個並行請求，將同一產品添加到條列項目購物車中，從而避免為同一SKU創建單獨的訂單項。 以前，在店面上並行請求將同一產品添加到購物車會導致同一SKU出現多個訂單項。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_：結帳訂單電子郵件確認將發送到以名字/姓氏輸入的電子郵件
   * _修正注意_：結帳訂單電子郵件確認（以前在“名字”和“姓氏”字段中輸入電子郵件按讚模式時發送）不再發送。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_：結帳送貨位址表單使用錯誤的位址進行更新
   * _修正附註_： shippingAddressFromData 現已儲存到每個網站的本地儲存中。 以前，如果在URL中使用商店代碼，且在同一個訪客工作階段中從多個網站起始結帳，則結帳時可能會將錯誤網站的位址自動填入送貨地址表單中。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_： [啟用地址 Search 時，雲] 簽出不會保留所選的 帳單 地址
   * _修正注意_：啟用地址搜尋時，結帳付款頁面現在將保留所選的帳單地址。 以前，如果“客戶地址數量限制”配置為 1，並且客戶有多個地址，則重新載入頁面後，所選的帳單地址將消失。
* _ACP2E-3407_： 禮品卡產品 |購物車合併正在合併禮品卡
   * _修正說明_：禮品卡產品現已在 購物車 中正確合併
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_：註銷時未考慮購物車持久性
   * _修正備註_：從客戶登入到身份驗證彈出窗口和簽出登錄，添加了缺少的功能記住我。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_：現有報價數據不更新/不可見，而是在 trigger_recollect = 1 時創建新的報價記錄
   * _修正說明_：客户的購物車專案在添加到購物車后不再因產品被刪除而消失。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3495_：購買禮品登記項時，客戶會看到不在其登記中的項
   * _修正說明_：禮品註冊表更新不再包含不屬於禮品註冊表的專案。
* _ACP2E-3510_： [“全部移除”確認彈出視窗的雲] 問題 未經確認移除購物車商品
   * _修復說明_：現在，按兩下需要注意的產品的“全部移除”按鈕會提示一個確認彈出視窗，以確保僅在確認後刪除專案。 之前，項目在沒有任何確認的情況下會立即刪除
* _ACP2E-3618_： [雲] 重新排序按鈕功能
   * _修復說明_：從管理員區域重新訂購訂單現在會將有庫存的產品添加到報價平均，儘管原始訂單中有一些產品不再有庫存。 在修復之前，如果原始訂單中沒有庫存的產品，則不會將任何產品添加到新報價單中。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_：Search商店不按郵遞區編碼運作
   * _修正注意_：對於荷蘭文本地化，按郵政編碼搜索取件地點無法正常工作。 修復后，取件地點搜尋將根據郵遞區編碼提供結果。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/344fce23>

### 購物車和結帳，結帳/ 一頁面結帳

* _AC-9386_： [隨機錯誤] 電子郵件欄位未呈現或需要花費大量時間顯示在結帳發貨或付款頁面
   * _修正注意_：Commerce 現在按 **[!UICONTROL Email]** 預期呈現結帳、發貨和付款頁面上的字段。 之前，此欄位不存在或呈現緩慢。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/e1babcfd>

### 購物車與結帳、訂購

* _ACP2E-3097_：產品的Datepicker具有多個「可自訂選項」，且日期欄位在從管理員下訂單時無法運作
   * _修正附註_：在管理訂單建立程式中設定具有多個可自訂日期選項的產品時，系統現在會正確顯示所有日期欄位的日期選擇器。 以前，日期選擇器只顯示第一個日期欄位，而其餘欄位則沒有日期選擇器。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>

### 購物車和結帳，運輸

* _AC-12119_：可配置產品的即時購買“最便宜的運費”中斷
   * _修正說明_：即時購買功能錯誤地為可配置產品選擇了更昂貴的店內配送選項，而不是最便宜的統一費率方法。 此修復可確保根據實際價格選擇正確的運輸方式。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38811>
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
* _AC-11804_：類別說明 所見即所得在非預設商店視圖上為空
   * _修正說明_：現在，在 商店 視圖 級別编辑類別時，系統現在可以在 WYSIWYG 編輯者中正確保存並顯示類別描述。 以前，在商店檢視層級儲存類別說明後，WYSIWYG編輯器會顯示為空白。
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_： [問題]將目前的儲存區ID用於類別執行階段快取
   * _修正附註_：系統現在會正確使用類別執行階段快取目前的存放區ID，以防止使用模擬或自訂程式碼將類別儲存在不同存放區時覆寫資料。 先前，儲存在執行階段的物件可能來自錯誤的存放區，導致資料覆寫。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39310>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36394>
* _AC-13324_： bin/magento sampledata：deploy —no-update擲回例外狀況
   * _修正說明_：現在，使用sampledata：部署 命令中的 --no-update 選項時，系統可以正確接受布爾值，從而防止在示例數據部署期間出現任何錯誤。 以前，使用此命令時會擲回錯誤，因為系統錯誤地預期了整數值。
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
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
* _ACP2E-2905_: [Cloud] Issue of Quote in multi-website architecture
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
   * _修正說明_：系統現在支持在鉻黃上對產品細節頁面移動視圖圖像進行捏合縮放功能，增強了移動使用者體驗。 以前，在 鉻黃 上的行動視圖中兩次點擊影像時，並不會如預期的那樣放大影像。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_：選項名稱為0的LayeredNavigation中遺漏標籤
   * _修正附註_：已略過屬性值0的空值檢查器來解決問題。 之前，該維度會被視為空白並導致問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_：客戶看到其他客戶群組的價格
   * _修正附註_：修正客戶群組相關資訊因請求中X-Magento-Vary的舊值而儲存在錯誤區段的問題
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_：刪除捆綁包選項時錯誤
   * _修正附註_：系統現在會正確刪除套件組合選項，而不會觸發錯誤或造成頁面無回應。 先前，嘗試刪除套件組合選項會導致「頁面無回應」錯誤並阻止產品儲存。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_：類別許可權記憶體不足的瀏覽器問題
   * _修正附註_：類別許可權UI經過重新設計，允許使用現成的UI元件和分頁產生大量許可權。 先前類別許可權會導致瀏覽器當機，並會將大量許可權指派給類別。
* _ACP2E-3100_： [雲端]影像檔案不存在於New Relic錯誤記錄檔中
   * _修正附註_：系統現在會將自訂預留位置影像同步至本機儲存體，以確保在使用AWS S3等遠端儲存體時，這些影像可正確轉譯。 先前，自訂預留位置影像在使用遠端儲存空間時無法轉譯，導致影像顯示中斷和錯誤記錄。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_：新產品 RSS 摘要由於緩存而未更新新產品
   * _修正說明_：當產品設置為新品並保存時，新產品的 Rss 摘要現在會更新
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_： [雲] 產品媒體庫 GQL 回應不按圖像位置排序
   * _修正說明_：系統現在可以按 GraphQL 回應中的位置正確排序媒體庫中的專案，確保準確的顯示順序。 先前，媒體集中的專案並未依位置排序，導致顯示順序不正確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37671>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_： [雲端]子類別專案未顯示在管理後端的Widget編輯上
   * _修正注意_：新小部件頁面上的類別樹在載入 5+ 級類別時應該不再有問題。 以前，在載入超過第 5 級類別的樹時，會遺漏某些類別。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3198_： [在真實行動裝置上雲端] 雙指縮放和移動問題
   * _修正說明_：系統現在可確保在移動裝置上實現一致的圖像縮放功能，從而提供流暢且可預測的使用者體驗。 以前，圖像縮放功能不一致，在行動裝置上查看時會在某個點後突然縮小。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_：從共用目錄取消指派產品時，不會清除願望清單產品
   * _修正附註_：現在，如果共用目錄中沒有產品，則願望清單中不會顯示任何專案。 先前，即使願望清單中實際上沒有專案，願望清單頁面也會錯誤地顯示「1專案」的計數。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_： 相關產品全選/取消全選問題
   * _修復說明_：以前，如果手動選擇產品，相關產品的“全選”/“取消全選”按鈕無法正常工作。 修復后，這些按鈕現在功能一致，平均手動選擇后，確保正確選擇或取消選擇所有產品。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_： [雲端]庫存警示電子郵件翻譯成錯誤的語言
   * _修正附註_：針對使用不同語言的多個商店檢視的網站，傳送庫存/價格警示時，建立警示的商店檢視語言將會用於電子郵件。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>，<https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_：已停用的類別在類別樹狀結構中的名稱不再為灰色
   * _修正附註_：之前，已停用的類別在類別樹狀結構中不會呈現灰色。 現在，它們以灰色效果顯示。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_：可配置的產品編輯表單載入導致超時和記憶體耗盡
   * _修正說明_：在修正之前，可配置的產品變體是根據所有可能的屬性選項組合構建的。 在屬性具有大量選項的情況下，這會導致冗長且消耗資源的作。 現在，您可以根據現有的子產品屬性構造可配置的產品變體。 這導致更少的計算 – 從而改善了資源的使用。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_：使用色票時Fotorama未正確載入視訊，並已透過URL預先選取選項
   * _修正說明_：如果URL包含選定的選項，產品視頻現在將在可配置的產品詳細資訊頁面上正確呈現。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_： 頁面建立工具輪播Widget顯示不符合條件的產品
   * _修正附註_： Widget中使用的產品清單現在遵循類別條件
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_：當群組中所有產品的數量無效時，就會觸發驗證錯誤
   * _修正附註_：現在，當一個產品具有無效數量（先前未發生）時，群組中的所有產品都會正確觸發驗證錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_： [可配置產品中未顯示雲] 特價
   * _修正說明_：修正後，更改特殊價格屬性的“用於商品詳情”值不會影響可配置商品的特價顯示。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_：索引器 如果進程終止，則不會清理臨時表
   * _修正注意_：如果索引器進程終止，現在會清理 CatalogRule 索引器臨時表
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
   * _修復註釋_：系統現在確保從訂單檢索時不會預先載入裝運和貸項通知單的收款，從而允許將其他篩選器或訂單應用於這些收款。 之前，這些集合會自動載入，防止任何進一步修改。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37561>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_： [雲端]後續追蹤：檢查資料是否有變更時，資料比較中的不相符
   * _修正附註_：以往，儲存物件在每次都呼叫時不會有任何資料變更（針對任何數值資料欄位，如int/float/double）。 它會觸發標幟_hasDataChanges設為true並呼叫save函式。 它也不會檢查由字串封裝的浮點數。 此修正套用後，只有在資料變更時，儲存函式才會呼叫。 int/float/double-check的資料值，其值會傳遞至函式，且會執行嚴格的型別比對
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>

### 目錄， GraphQL

* _ACP2E-3090_：在GraphQL中處理類別篩選器： includeDirectChildrenOnly和category_uid
   * _修正附註_：依category_uid篩選時，只會擷取直接子類別。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_： [雲端] Graphql產品排序無法運作
   * _修正附註_：在變數中傳遞欄位時，GraphQl產品會依多個欄位排序，現在會如預期般運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_：GraphQL產品中的層級價格傳回錯誤的值（相較於Storefront）
   * _修正說明_：修正後，針對 graphql 請求返回的產品層價格具有每個項目的價格。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_： [雲] B2B：通過 GraphQL 類別問題
   * _修復說明_：修復后，如果根類別沒有允許權限，類別 graphql 查詢將返回具有允許權限平均的類別。

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

* _ACP2E-3653_：當頁面> 1 時，類別的規範URL不正確
   * _修正說明_：以前，多頁面內容的規範URL無法正常運行，無法始終顯示基本URL。 不過，在實施此修正後，多頁面內容的規範URL現在會正確顯示具有頁面 ID 的URL。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/982b1c42>

### 目錄，Search

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
   * _修復注意事項_：以前，對於來賓用戶禮品登記項，當從電子郵件功能返回時，會生成一個空的空白位址，這對於下訂單不正確。 應用此修復程式后，禮品註冊表將檢查登錄的用戶/來賓使用者和分配的位址（如果存在）。

### 雲

* _ACP2E-3010_： [Cloud] PHPSESSID 正在更改每個 POST 請求
   * _修正注意_：如果啟用了 L2 Redis 緩存並從後端更新了客戶，則 PHPSESSID 不再在登錄客戶的前端區域的POST請求上重新生成
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_：網站地圖生成警告
   * _修正說明_：修正後，系統會在系統 tmp 目錄中生成Sitemap並複製到最終目的地。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>

### 內容

* _AC-10539_：[]“最近查看”小部件中的價格顯示問題
   * _修正說明_：系統現在在「最近查看的產品」小部件中正確顯示缺貨簡單產品的價格，確保所有小部件和產品清單頁面的一致性。 以前，由於價格載入範本中的條件，缺貨簡單產品的價格不會顯示在“最近查看的產品”小部件中。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38167>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38159>
* _AC-10596_： [更正] acl.xsd 檔中的拼寫錯誤和語法
   * _修復說明_：系統現在更正了 acl.xsd 檔中的拼寫錯誤和語法錯誤，從而提高了文檔的清晰度和準確性。 以前，acl.xsd 檔包含拼寫錯誤和不正確的語法，這可能會導致混淆。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38061>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38046>
* _AC-10845_：建頁器橫幅圖片在圖庫中不可見
   * _修正說明_：系統現在可以正確顯示上傳到頁面構建器庫中新創建的資料夾中橫幅圖像，從而消除了以前的控制台錯誤。 在此修復之前，如果將橫幅圖像上傳到新資料夾中，則在庫中不可見，從而導致主控台錯誤。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_：更新到 2.4.5-p8 後“未設置區號
   * _修正說明_：啟用 Magento_CSP 模組 且“dev/js/translate_strategy”設置為“嵌入”時，系統現在成功完成靜態內容部署過程，而不會觸發“未設置區號”錯誤。 以前，在這些情況下，靜態內容部署過程將失敗並顯示「未設置區號」錯誤。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38845>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38922>
* _AC-12692_：Widget類別樹狀結構未正確呈現
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/39008>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_：變更設計設定頁面中的主題時，無法看到「使用預設值」訊息
   * _修復說明_：系統現在包含一個單獨的列，用於顯示“使用預設值”消息，具體取決於設計配置頁面中選擇的主題。 這可確保預設值狀態的清晰性和可見性。 以前，不會顯示“使用預設值”消息，從而導致對所選主題的狀態感到困惑。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_： [問題] 再次恢復與TinyMCE外掛程式的向後相容性（之後...
   * _修復說明_：系統現在恢復了與 TinyMCE 外掛程式的向後相容性，允許在從其他位置使用小部件時調用外掛程式內定義的函數。 以前，由於 TinyMCE 版本的更改，外掛程式不會將小部件作為物件返回，從而導致在嘗試調用小部件執行個體上的某些函數時出錯。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39262>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39258>
* _AC-9638_： [問題]產品頁面上WYSIWYG編輯器中的檔案上傳問題
   * _修正附註_：系統現在可正確顯示資料夾樹狀結構，並允許在產品頁面上的WYSIWYG編輯器中上傳影像，即使先展開「影像和視訊」索引標籤亦然。 先前，展開「影像和影片」索引標籤後，導致資料夾樹狀結構未顯示，以及嘗試在WYSIWYG編輯器中上傳影像時出現錯誤訊息。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38026>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_： [內部部署]動態區塊問題
   * _修正附註_：動態區塊中的Widget現在已正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_： YouTube nocookie url在頁面產生器中無法運作
   * _修正附註_：現在pagebuilder允許在驗證規則的表單元素設定中使用youtube無cookie url。 之前，youtube非Cookie URL無法在pagebuilder中運作。
* _ACP2E-2693_： [雲端]前端未載入，因為新聞稿範本有問題
   * _修正附註_：透過CMS頁面內容區段新增區塊不會再導致例外狀況
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_：ACP2E-2836： [日誌中發現雲] 調查異常：無效參數異常：供應商/洋紅色/模組-規則/型號/ConditionFactory.php中不存在類
   * _修正注意事項_：移除 PageBuilder 產品內容設置上的條件不再會導致異常記錄在日誌文件中。 以前，刪除 PageBuilder 產品內容設置上的條件會導致在日誌中記錄關鍵異常，儘管不會在前端引起任何問題。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_：切換到單商店模式 - 不再显示全域內容
   * _修正附註_：系統現在會在啟用單一商店模式時，將商店檢視設計設定與網站設計設定同步，確保內容更新會顯示在前端。 以前，切換到單一商店模式會防止內容更新反映在店面上。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_：頁面產生器在嘗試新增連結和其他可用性問題時取代影像。
   * _修正附註_：現在按一下影像，頁面產生器文字元素中wysiwyg編輯器中的連結會在影像的連結設定對話方塊中載入適當的資料。 現在，在編輯器中新增影像連結也可正常運作。 之前，影像已更換為連結。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_：將0位元組影像放在目錄中時，舊媒體集無法轉譯影像
   * _修正備註_：系統現在可以處理媒體集中的0位元組影像，而不會中斷功能，讓目錄中的其他影像可以如預期顯示和選取。 以前，如果媒體集中有0位元組的影像，將無法顯示或選取目錄中的所有影像。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_：编辑 CMS 塊時錯誤頁面生成器
   * _修復說明_：系統現在使用 頁面 生成器正確保存管理區域中所做的更改，而不會引發錯誤“頁面生成器正在渲染 5 秒而不釋放鎖”。 在瀏覽器主控台中。 以前，嘗試儲存變更時會發生此錯誤，導致內容無法成功更新。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>，<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_： [雲端]購物車區段上沒有結帳或編輯購物車的按鈕
   * _修正注意_：捆綁產品現在通過小部件添加到購物車，沒有錯誤。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>， <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3113_：類別頁面上的內容暫存預覽不顯示產品介面工具集
   * _修正說明_：已通過確保連結到 CMS 塊的其他類別的產品條目已準確記錄到資料庫中，修復了此問題。 以前，當請求類別預覽頁面時，它會返回一個空的結果集。
* _ACP2E-3122_： [雲] 上傳圖像按鈕不起作用
   * _修復說明_：在從PageBuilder上傳橫幅和滑塊影像按鈕之前無法按預期工作，現在按下它時會打開本地檔管理員以選擇要上傳的所需圖像。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_： imagecreatetrueColor（）： 參數 #2 （$height） 必須大於 0。 無法上傳特定影像
   * _修正注意事項_：解決了通過媒體庫上傳高度為 0 的圖片時導致管理員出錯的問題，並使用 同步 命令成功資產同步。 以前無法通過媒體庫上傳圖像，當特定映像位於庫中時，同步 命令也會失敗。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_： Prototype.js Array.from 與 Google Maps API 衝突
   * _修正附注_：Google 地圖現在可以在 PageBuilder 編輯者中正確呈現。 之前，JavaScript 錯誤會讓 Google 地圖無法正確呈現。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_： [Cloud] - CMS滑桿未反映最新變更
   * _修正說明_：此問題已通過確保在編輯幻燈片屏幕上觸發保存事件時刷新滑桿清單來修復。 之前，它會觸發併導致問題。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_：使用構建器按特定順序插入 CMS 塊時頁面 CSM 頁面發生錯誤
   * _修正說明_：以前在某些版本的 PHP 和作系統 （Linux） 上，通過頁面構建器引用其他 cms 塊的塊的呈現會失敗，並顯示「發生未知錯誤。 請再試一次。」 現在，cms塊的內容在PageBuilder控制的內容中正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_： [雲端]動態區塊將無法正常運作
   * _修正附註_：登出後現在會清除登入的客戶區段，以防止來賓工作階段繼承先前登入的區段
* _ACP2E-3428_：大型內容的Pagebuilder範本預覽失敗
   * _修正附註_：大型內容導致畫布元素超過瀏覽器的限制，並傳回不正確的值，這會破壞後端程式碼（無法正確解碼影像）。 已修正將畫布大小限製為通用瀏覽器上限的問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_：TinyMCE 7遺失字型大小的最新安全性更新
   * _修正附註_： WYSIWYG編輯器中現在提供字型大小和字型系列選取器。 在此修復之前，在TinyMCE 7中，這些在編輯者介面中不可用。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d50f6b5d>， <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_：TinyMCE 7 在 PT 而不是 PX 中的管理員中編輯者字型大小，請澄清
   * _修正注意_：在修復之前，您無法在所見即所得區域中以 px 為單位指定字型大小。 現在，您可以以 px 而不是 pt 為單位設置字型大小。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>， <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_：頁面生成器中的產品內容類型在沒有正確消息的情況下摺疊
   * _修正附註_： 在修正之前，當小部件中沒有產品時，預覽 html 無法正確生成。 現在，空回應已正確生成，產品小部件在預覽中正常顯示。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>， <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_： [頁面生成器]添加產品列表以阻止會導致錯誤
   * _修正說明_：現在，通過頁面構建器將捆綁商品清單添加到阻止不會導致錯誤
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/344fce23>

### 內容、SEO

* _ACP2E-2870_：CMS 頁面階層可能會導致URL重寫問題
   * _修復說明_：以前，對於非網站根頁面的自定義永久URL重寫，無限重新導向，並且從未載入頁面。 應用此修復程式後，非網站根目錄頁面的自定義URL重寫將按預期工作，並且不會發生重定向迴圈。

### 內容、測試和預覽

* _ACP2E-2979_：當目錄價格規則設定為使用動態區塊排程時未顯示
   * _修正備註_：系統現在會在產品詳細資料頁面上正確顯示與排程型錄價格規則相關的動態內容。 先前，在排程型錄價格規則時，無法載入動態內容。

### 客戶/

* _AC-12162_：前端 - 客户創建頁面中驗證的出生日期失敗
   * _修正說明_：確保將系統依賴項升級到最新的次要版本后，所有驗證都應moment.js工作
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-13060_：客戶區段>條件>產品歷史記錄* >“已查看產品”不起作用
   * _修正說明_：現在，當滿足匹配的註冊客戶時，系統會在「客戶區段」下的「已查看產品」條件下正確顯示匹配的註冊客戶。 以前，平均滿足條件時，匹配的註冊客戶計數仍為零。
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
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38298>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/39188>
* _AC-10838_：目錄搜尋索引過程錯誤索引過程
   * _修正說明_：無論使用 PHP 編譯的 libxml 版本如何，系統現在都能成功完成重新索引命令，而不會遇到任何錯誤。 以前，運行 re-index 命令會導致在使用某些版本的 libxml 編譯 PHP 時出現「索引過程中的目錄Search索引進程錯誤」錯誤。
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
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38485>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38439>
* _AC-11592_： [問題] 在安裝:di:編譯期間僅允許有效的首選項
   * _修復說明_：如果為不存在或明確排除的類創建了首選項，系統現在會在 setup:di:編譯命令期間拋出錯誤，從而確保只允許有效的首選項。 以前，這些方案會以靜默方式失敗，可能會使與原始類關聯的任何外掛程式都無用。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38517>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/33161>
* _AC-11651_：Magento嘗試在 LoggerProxy 方法中修改只讀屬性__wakeup
   * _修復說明_：系統現在允許在LoggerProxy的 __wakeup方法中修改以前只讀的屬性，確保平穩運行，而無需強制使用者採用解決方法。 以前，嘗試在 LoggerProxy 的 __wakeup 方法中重新分配只讀屬性的值會導致問題。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38526>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_： [問題] AC-2039 AC-1667升級TinyMCE參考
   * _修正附註_：已更新composer.json中的tinymce最新版本
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38533>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36543>，<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_： ChangelogBatchWalker無法在多個執行緒中運作
   * _修正附註_：系統現在支援MView索引的處理程式復本，以防止在多個執行緒上執行索引器時出現錯誤。 以前，在多個線程上運行 ChangelogBatchWalker 銷售機會刪除其他線程使用的表，從而導致索引器執行期間出錯。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38246>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38248>
* _AC-11781_： [問題] 命名錯誤重新命名變數
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
* _AC-11829_: [Issue] Fix exception handling inconsistency between developer and production modes
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
* _AC-13810_：客戶網格索引器在“按計劃更新”模式下無法正常工作
   * _修正備註_：先前的客戶格線已立即更新，但修正後客戶格線會在cron執行後更新，但不會立即反映。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_：js 檔案上的拼寫錯誤。
   * _修正說明_：系統現在在JavaScript文件中正確使用術語「訂閱者」，確保相關功能正常運行。 以前，JavaScript檔中的印刷錯誤導致「訂閱者」一詞使用不正確。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/36163>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/36171>
* _AC-8353_： [問題]移除禁止的`@author`標籤
   * _修正附註_：系統現在會從某些模組移除禁止的`@author`標籤，以遵守編碼標準，確保程式碼更乾淨且標準化。 以前，`@author`標籤存在於某些模組中，這違反了既定的編碼標準。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37253>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/37003>
* _AC-8356_： [問題] 移除 `@author` 禁止標記（ `Magento_Customer` 第 2 部分）
   * _修復說明_：系統現在通過從某些模組中刪除 `@author` 禁止的標記來遵守編碼標準，確保代碼更乾淨、更標準化。 以前， `@author` 標記存在於某些模組中，這違反了既定的編碼標準。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/37250>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/37000>
* _AC-8659_： editorconfig語法中的空格中斷[{composer，auth}.json]的規則
   * _修正附註_：系統現在會將4個空格縮排正確套用至composer和auth.json檔案，接著修正editorconfig中的語法錯誤。 先前，由於editorconfig語法中有空格，這些檔案的格式不正確，有2個空格的縮排。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37394>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/37395>
* _AC-8662_： [問題]改善cron錯誤記錄
   * _修正附註_：系統現在會擷取並記錄cron程式的STDERR和STDOUT，在cron程式失敗的情況下提供有價值的診斷資訊。 以前，不會記錄 cron 進程中的任何錯誤消息，並且在單獨進程中運行的 cron 組的 STDERR 和 STDOUT 丟失。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37453>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32690>
* _AC-8984_： [問題]在某些安裝程式cli命令的輸出中新增一些顏色
   * _修正附註_：系統現在會為某些安裝程式命令列介面(CLI)命令的輸出加入更多色彩，增強可讀性和使用者體驗。 以前，由於缺乏顏色區分，這些命令的輸出更難讀取。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/29335>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/29298>
* _AC-9630_：升級Magento在添加具有所需州/區域的新國家/地區時會重置常規/區域/state_required。
   * _修正說明_：現在，僅當添加具有所需州的新國家/地區時，系統才會將修改後的國家/地區添加到“常規/區域/state_required”配置中，從而防止假定區域已禁用自定義代碼的任何中斷。 以前，添加具有所需州的新國家/地區會將“常規/區域/state_required”配置重置為具有所需州的默認國家/地區，這可能會破壞商店。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/37796>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38076>
* _AC-9712_：具有複雜 `calc` 表達式的php和nodejs 資料庫（grunt）之間較少編譯的差異
   * _修復註釋_：修復更新wikimedia/less.php：^5.x後php和nodejs 資料庫（grunt）之間編譯較少的差異
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/37841>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_： 執行部分索引時發生“找不到基表或視圖”錯誤
   * _修正附註_：部分重新索引現在可正確搭配大型變更記錄檔使用，以備次要資料庫連線時使用
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_：將 MariaDB 升級到 10.5.1 或更高版本后出現的問題
   * _修復註釋_：修復了 Mysql 升級后資料庫中的日期時間值轉換為 0000-00-00 00:00:00 的問題
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_：檢查數據是否有更改時，數據比較中的類型不匹配
   * _修正說明_：以前，每次調用保存物件時都不會發生任何數據更改（對於任何數值數據欄位 - 按讚 int/float/兩次）。 它會觸發 標幟 _hasDataChanges為 true 並調用 save 函數。 套用此修正後，只有在數據發生變更時，才會呼叫save函數。 int/float/兩次-check 的數據值與傳遞給函數的值一起執行嚴格類型匹配。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_： [雲] 導入不能與目錄 var 一起使用
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
* _ACP2E-3537_：緩存標記中沒有相應的緩存鍵條目，因此緩存清理無法正常工作
   * _修復說明_：現在預設為 Redis 緩存垃圾回收器啟用 LUA 模式，以防止出現爭用情況
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_： 忽略MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK值
   * _修復說明_：修復后，設置為 「false」 的 ENV 變數將被視為布爾值 false，而不是字串 『false』。
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
   * _修復說明_：在此修復之前，無法通過 bin/magento config：set 命令設置設計配置，並且可以通過作顯示它們的表單來更改鎖定的值。 修正後，從cli使用 — lock-env或 — lock-conf設定的鎖定值無法再更新。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/55615e61>

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
   * _修復說明_：當管理配置設置為“目錄>分層導航>顯示類別篩選”時，通過 GraphQL 查詢請求具有類別聚合的產品搜尋時應用檢查后，此問題已得到修復。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_： 包含價格篩選器 {from：“0”} 的 GraphQL 產品呼叫未返回任何結果
   * _修復說明_：以前，由於拋出異常，帶有零價格過濾器的 graphql 產品搜尋根本沒有返回任何結果。 現在，搜尋會按預期返回結果。
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_： [Graphql API 的雲] 問題
   * _修正備註_：在使用Graphql應用程式伺服器修正之前，客戶地址要求未傳回最近的資料。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_：停用的產品仍會出現在grpahQL查詢中的相關、向上銷售、交叉銷售專案中
   * _修正說明_：Graphql 現在為已禁用的關聯、向上銷售和交叉銷售產品提供正確的回應
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_： [雲]： 圖形 Ql 錯誤 內部伺服器錯誤 放置訂單突變
   * _修正說明_：請求中帶有抵用券代碼資訊的“placeOrder”突變不再引發內部錯誤異常，訂單已成功下單。 以前，它因「內部伺服器錯誤」而失敗。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/982b1c42>
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
* _LYNX-530_：不可用消息未显示可用庫存數量
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>， <https://github.com/magento/inventory/commit/db0620da>

### 圖表QL， 庫存/ MSI， 性能

* _ACP2E-1716_：升級后網站關閉
   * _修正說明_：通過 GraphQl 獲取捆綁產品的性能得到了改進。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>， <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL， 性能

* _AC-9569_： [GraphQL 解析程序客戶解析程序] 數據不會因匯入而失效
   * _修正說明_：噹通過導入编辑或刪除客戶時，GraphQL 客戶解析程序緩存現在按預期失效。 以前，緩存不會失效，並且客戶數據可以在導入過程中編輯或刪除。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL，搜尋

* _ACP2E-2809_：按多個参数排序的 GraphQL 產品清單不起作用
   * _修正說明_：在 GraphQl 中按多個字段對產品進行排序現在按照文檔中的說明工作
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_：產品列表 GraphQL 查詢僅限於 total_count 10,000 個產品
   * _修復說明_：修復后，搜尋結果不限於 10000 個產品，如果計數超過 10000，則可以獲取符合搜尋條件的所有產品平均。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL，測試架構

* _ACP2E-3363_： Magento\GraphQl\App\GraphQlCustomerMutationsTest.php整合測試失敗
   * _修正備註_： &#39;-
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4cf5e62>

### 匯入/匯出

* _AC-12172_：提供自訂選項型別時，產品匯入發生問題： file （已建立的產品不包含自訂選項的價格，並且僅顯示提供的第一個檔案型別副檔名）
   * _修正附註_：系統現在會正確匯入具有「檔案」型別之自訂選項的產品資料，確保顯示所有提供的副檔名且包含自訂選項的價格。 先前，在產品匯入期間，如果「file」型別的自訂選項有多個副檔名，則只會顯示第一個副檔名，且遺漏自訂選項的價格。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38805>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_：歷史記錄網格中導入作的執行時間錯誤匯入
   * _修正附註_：匯入報告執行時間正確顯示，不受管理員地區設定影響。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_：使用匯入以相同電子郵件地址建立的重複客戶
   * _修正附註_：在[帳戶共用]設定為[全域]時匯入客戶，已更新系統中存在的匯入客戶。
先前匯入的客戶重複。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_：在複製可自定義選項的產品上添加/更新匯入
   * _修正注意_：此問題已通過在產品選項CSV導入期間為產品選項分配正確的商店得到解決。先前指派給管理員商店，而非其各自的商店。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_：客戶「created_at」日期未在匯出時轉換為存放區時區
   * _修正附註_：根據客戶匯出CSV區段中的存放區時區，「created_at」欄的日期值會轉換為適當的日期格式。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_： [雲端]使用CSV檢查匯入資料中的資料時發生錯誤
   * _修正附註_：在CSV匯入期間檢查資料時沒有錯誤。 先前，顯示的錯誤訊息為：「使用管理員的CSV檢查匯入區段中的資料時，我們在列：1中找不到符合此電子郵件和網站代碼的客戶」。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_：缺少匯入按鈕
   * _修正說明_：使用CSV中正確和不正確的記錄進行數據檢查后，解決了匯入按鈕缺失的問題。 以前，在CSV中使用正確和不正確的記錄進行數據檢查后，不會顯示導入按鈕。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_：無法導入導出的客戶地址
   * _修正說明_：客戶位址導入將按預期進行。 以前，如果「共用客戶帳戶 = 全球」，則客戶地址導入檔不會傳遞驗證，並且有兩個網站的默認網站具有受限制的國家/地區清單，並且要導入的地址用於允許的國家/地區不同的另一個網站
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_： [雲端] CSV檔案中的錯誤數量未產生錯誤
   * _修復註釋_：現在，股票來源導入將在數量列中為非數值值拋出驗證錯誤。 以前，導入數量列中值不數值的庫存來源會導致數量設置為 0。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_：當URL密鑰已屬於類別時，導入產品時生成的重複URL密鑰錯誤消息不正確
   * _修復說明_：當產品的 url 金鑰已屬於類別時，客戶嘗試導入產品時，在產品導入檢查期間顯示正確的錯誤消息。
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_：管理面板中的清漆 7 按鈕無導出 VCL
   * _修復說明_：「導出清漆 7 的 VCL」按鈕已添加到管理面板。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>

### 庫存/微星

* _AC-10750_：資料庫使用首碼時，可設定產品的詳細目錄更新失敗
   * _修正說明_：現在，當資料庫使用前綴時，系統會正確更新可配置產品的庫存，從而防止任何錯誤消息並確保保存正確的數量。 以前，如果資料庫使用前綴，則嘗試保存可配置產品中簡單產品的庫存數量時會發生錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38045>
* _AC-11593_：添加包含屬性的地圖時，Google Google API 金鑰不起作用
   * _修正附註_：系統現在支援最新的Google Maps API 3.56版，可讓使用者從PageBuilder功能表成功將地圖內容區塊新增到舞台，不會發生任何錯誤。 之前，由於Google地圖API版本的相容性問題，使用者無法新增地圖內容區塊，導致出現「發生錯誤」錯誤訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_：無法為具有多個來源且SKU損毀的訂單專案建立出貨
   * _修正附註_：先前透過資料庫錯誤地在SKU中新增空格時，會導致出貨頁面發生錯誤，該錯誤現已修正，且自動修剪被視為人性化的錯誤，未發現影響。因此已成功建立出貨。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_： [測試] 捆綁商品，正面顯示0個庫存商店
   * _修正說明_：捆綁商品不會顯示在使用額外庫存的其他網站上。
* _ACP2E-2794_： [具有空白空間的產品清單的雲] 關鍵問題
   * _修正說明_：現在，當產品設置為“未Stock”時，系統可以正確顯示沒有空白的產品清單，從而確保一致且準確地顯示可用產品。 以前，將產品設置為「未Stock」會導致產品清單中出現空白區域，從而破壞佈局並可能使客戶感到困惑。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>， <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_：啟用MSI取貨商店時無法送出訂單
   * _修正附註_：改善存貨效能，可建立出貨並備有許多店內取貨的來源
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_： Cron重新索引無法在前端更新產品可用性
   * _修正附註_：之前，透過REST API更新延期交貨狀態後，產品在前端沒有庫存。 現在，透過REST API更新延交訂單狀態後，產品會以庫存顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_：啟用MSI時，將影像新增至可設定的功能無法運作。
   * _修正附註_：使用詳細目錄模組時，可設定產品的影像上傳現在會如預期般運作。 先前無法上傳影像
   * _GitHub 代碼貢獻_： <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_：清潔M2.4.7-p3中的套件組合產品+ MSI發生問題
   * _修正附註_：之前，對於與相同簡單產品重複之後的存貨組合產品，無法儲存簡單產品。 套用此修正後，簡單產品便可順利儲存，不會有任何例外。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39358>
   * _GitHub程式碼貢獻_： <https://github.com/magento/inventory/commit/0208e433>

### 庫存/微星，Search

* _ACP2E-3413_：當SKU未設置為可搜索屬性時，所有產品的索引 [is_out_of_stock] = 1
   * _修正說明_：修正後，目錄搜尋索引中的「is_out_of_stock」正確，平均 SKU 不可搜尋時。
   * _GitHub 代碼貢獻_： <https://github.com/magento/inventory/commit/5b21b7af>

### 次序

* _AC-10828_：後端訂單概覽屏幕：訂單項目級別上看不到缺貨數量
   * _修正說明_：系統現在在後端訂單概覽屏幕的數量列中顯示缺貨商品的數量。 這可確保使用者可以準確跟蹤訂單中所有項目的狀態。 以前，“數量”列僅顯示已訂購、已開票和已發貨的物料數量，但不顯示延期交貨物料的數量。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38252>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/38320>
* _AC-10994_： [問題]訂單地址轉譯器中使用的存放區識別碼錯誤
   * _修正附註_：系統現在會在轉譯訂單位址時，正確使用與訂單相關聯的商店ID，確保位址已根據其各自的商店ID正確格式化。 先前，系統未正確使用目前的商店ID，若需要傳送來自不同商店的多份訂單電子郵件，可能導致地址格式不正確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38412>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/37932>
* _AC-11690_：加入處理器快取問題
   * _修正附註_：系統現在可正確套用每個反複專案的JoinProcessor，即使連續呼叫亦然，確保資料擷取準確。 以前，JoinProcessor錯誤地標籤為已在連續反複專案中套用，導致資料擷取錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/27504>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37550>
* _AC-11798_： [問題]送貨價格在列印的pdf中顯示不同
   * _修正備註_：系統現在會根據稅捐組態設定，以列印的PDF正確顯示出貨價格，確保銷售訂單商業發票檢視頁面與列印商業發票之間的一致性。 以前，無論稅捐組態設定為何，列印PDF中顯示的運費都會排除稅捐。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38608>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38595>，<https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_：使用已刪除的父可設定產品重新排序
   * _修復說明_：現在，在使用已刪除的產品重新訂購時，系統將不會顯示重新訂購按鈕重新排序
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/39568>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/39601>
* _AC-13924_： [問題] 修正 錯誤的\Magento\銷售\模型\訂單\電子郵件\容器\範本：：$id 屬性
   * _修正備註_：這修正了\Magento\Sales\Model\Order\Email\Container\Template：：$id的錯誤phpdoc，實際上$id是type int，但實際上是string。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39151>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_：無法保存對現有訂單詳細資訊中電話號碼的更改
   * _修正附註_：現在，使用者可以在訂單地址的電話欄位中新增國際首碼00
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38201>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_：無法傳送電子郵件
   * _修正附註_：系統現在包含組態選項async_sending_attempts，可指定在停止前嘗試傳送電子郵件的次數，改善啟用「非同步傳送」時失敗的電子郵件傳送處理。 先前，如果電子郵件無法傳送，系統會持續嘗試重新傳送，導致系統記錄中出現無休止的錯誤訊息回圈。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_： [Cloud]部分退款部份出貨的訂單狀態已變更為完成
   * _修正備註_：發行銷退折讓單時，如果料號尚未出貨，則訂單狀態不再變更為「已完成」。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_： [如開發文檔所示，CLOUD] 無法停用從管理員UI發送電子郵件
   * _修正注意_：現在，當電子郵件通信被禁用時，系統可以正確阻止發送銷售電子郵件。 重新啟用電子郵件通訊後，將不再傳送這些電子郵件。 以前，在禁用電子郵件通信時啟動的銷售電子郵件仍將在重新啟用電子郵件通信後發送。
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
   * _修正附註_： 修正了庫存可配置產品的 CartItemInterface 中的 is_available 屬性總是返回 false 的問題。 現在，它會在適用時正確地將可用性反映為 true。
* _LYNX-382_： 當可售庫存低於產品數量時，CartItemInterface 中的is_available屬性會傳回 true 平均
   * _修正注意_：修正當購物車專案數量超過可售庫存時，購物車專案介面中的 is_available 屬性錯誤地返回 true 平均的問題。
* _LYNX-395_： only_x_left_in_stock組態產品上 ProductInterface 的屬性不準確
   * _修正注意_：修正了 ProductInterface 中的 only_x_left_in_stock 属性無法準確反映購物車中可配置產品變型的可用庫存的問題。 現在，only_x_left_in_stock值與實際多屬性庫存水準正確對應，確保在購物車 GQL 查詢中返回準確的庫存數據。
* _LYNX-399_：將簡單產品添加到分組產品中的購物車時返回占位符縮略圖
   * _修正注意_：修復了將簡單產品（分組產品的一部分）添加到購物車時返回佔位元縮略圖圖像的問題，平均產品具有分配的圖像時。修正詳情：
• 產品縮圖現在可正確顯示分配的影像 （如果有）。• 縮圖選擇遵循以下管理員設定：
商店>配置>銷售>結帳>購物車>分組產品影像。這可確保基於商店設定的分組產品的縮圖行為一致。
* _LYNX-400_：客戶的自定義選項屬性不適用於整數值
   * _修正附註_：修正當傳回的值為整數時，客戶的自訂選項屬性無法運作的問題。 自訂選項現在可正確處理並按預期傳回整數值。
* _LYNX-402_：嘗試取得具有動態價格的套件組合產品的priceDetails時發生內部伺服器錯誤
   * _修正附註_：解決透過GraphQL查詢具有動態定價之套件組合產品的price_details時，導致內部伺服器錯誤的問題。 此增強功能使用設定了動態定價的套件組合產品時，可確保穩定的購物車查詢。
* _LYNX-403_： only_x_left_in_stock可設定產品的傳回值一律為0
   * _修正附註_：解決使用具有選項的父SKU新增時，可設定產品的only_x_left_in_stock屬性一律傳回0的問題。
修正詳細資料：
· only_x_left_in_stock值現在會正確反映所選子變體而非父SKU的庫存。
·這可確保在購物車和產品頁面中，針對可設定的產品變數正確顯示庫存量。
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
   * _修正附註_：修正GraphQL customer.orders查詢中available_actions欄位在為所有專案建立完整退貨後錯誤包含RETURN的問題。 現在，一旦返回過程完成，RETURN作就會被正確刪除。
* _LYNX-637_：店面相容性 - 更新邏輯以獲取帶有前綴的錶名稱和其他小改進
   * _修正說明_：更新了檢索帶有前綴的錶名的邏輯（與 SCP 更改相關）。
* _LYNX-643_：使用 setBillingAddressOnCart GQL 的same_as_shipping字段時，保存在通訊簿中不起作用
   * _修正注意_：修正使用 setBillingAddressOnCart GraphQL 突變且same_as_shipping字段設為 true 時，送貨地址未保存到客戶通訊簿中的問題。 現在，送貨位址已按預期正確存儲。
* _LYNX-650_：標準化突變中的order_id
   * _修正說明_：標準化了突變中的order_id輸入，並更新了訂單取消確認電子郵件範本，以顯示增量id而不是訂單ID。
* _LYNX-651_：客户訂單未显示訂單評論
   * _修正注意_：解決了 CustomerOrder 在訪客和客戶訂單 GraphQL 查詢中包含訂單評論的問題。
* _LYNX-652_：original_item_price不得包含任何折扣
   * _修正注意_：更新了 GraphQL 購物車項目價格中original_item_price的邏輯，以排除折扣。
* _LYNX-681_：捆綁產品之一缺貨時，捆綁產品仍顯示“IN_STOCK”
   * _修正附註_：解決即使其中一個套件專案無庫存，套件產品的product.stock_status仍顯示「IN_STOCK」的問題。
* _LYNX-686_：如果某個客戶存在已刪除自定義屬性的值，客戶查詢會傳回內部伺服器錯誤
   * _修正備註_：修正刪除的自定義屬性仍有儲存值時，客戶查詢返回內部伺服器錯誤的問題。 現在，如果請求不存在的屬性，將返回正確的錯誤消息。 刪除自定義屬性后，必要的客戶緩存失效。
* _LYNX-687_：返回和取消確認連結的作參數
   * _修正備註_：已為退貨和取消確認郵件相關連結新增動作參數
* _LYNX-688_：訪客用戶確認 url 被重定向到訂單狀態 頁面，因為它缺少 orderRef（適用於訪客 RMA）
   * _修正附註_： 在訪客 RMA 確認電子郵件的連結中新增了 orderRef 参數
* _LYNX-689_：訪客用戶確認 url 被重定向到訂單狀態 頁面，因為它缺少 orderRef
   * _修正備註_：在訪客訂單取消確認電子郵件的連結中添加了 orderRef 參數
* _LYNX-690_：禁用 RMA 時客戶查詢問題
   * _修正說明_：更新了 GraphQL 邏輯，以確保在全域禁用 RMA 時，以前創建的退貨仍可平均訪問。 已刪除錯誤消息以改善店面用戶體驗，確保客戶仍然可以視圖他們過去的退貨。
* _LYNX-696_：套用衝突的優惠券時，GraphQL 不會傳回更新購物車數據
   * _修正注意_：修正了以下問題：應用優先順序較高的衝突抵用券會導致錯誤消息，而不返回更新的購物車數據。 現在，當新抵用券使現有無效時，突變會正確返回應用有效抵用券的購物車。
* _LYNX-699_：對於 placeOrder GQL 上的不可為空欄位「TaxItem.title」，無法傳回 null
   * _修正注意_：修正 placeOrder 變更失敗並顯示內部伺服器錯誤的問題，原因是不可為空欄位 TaxItem.title 的空值。 現在，該欄位始終返回有效值，從而確保訂單刊登成功。
* _LYNX-702_：估計總計：虛擬產品類型的折扣為空
   * _修正注意_：解決了將折扣代碼應用於包含虛擬產品的購物車時 estimateTotals 突變返回折扣空值的問題。
* _LYNX-703_：捆綁商品未返回正確的折扣百分比和金額
   * _修正注意事項_：目錄項價格引入了新屬性“catalog_discount”和“row_catalog_discount”，以便在行和單個專案級別顯示正確的折扣金額和百分比。
* _LYNX-714_：產品級別的禮品贈言配置
   * _修正附註_： 修正全域停用時，禮品訊息無法在產品層級套用的問題。 現在，如果為特定產品啟用了禮品贈言，則可以使用 updateCartItems 突變成功添加它們，並且它們將被正確保存和反映。
* _LYNX-717_：從商品上取下禮品包裝購物車問題
   * _修正注意_： 修正使用 updateCartItems 突變從購物車專案移除贈品包裝未如預期般運作的問題。 現在，應用和刪除禮品包裝功能都可以正確無誤。
* _LYNX-751_：匹配的註冊客戶功能在樣板中不起作用，需要為來賓啟用 trackViewedProduct 突變。
   * _修正注意事項_：公開 trackViewedProduct 突變，用於跟蹤客戶和來賓的產品視圖事件
* _LYNX-757_：購物車.rules 查詢在未应用活動購物車規則的情況下返回錯誤而不是空数組
   * _修正註釋_：修正 購物車.rules 查詢，以便在未應用活動購物車規則時返回空数組而不是錯誤。
* _LYNX-758_：為檢索購物車物品的禮品包裝發出問題
   * _修正備註_：更新了檢索邏輯，以便在全域禁用但在產品級別啟用時返回購物車項目的贈品包裝選項
* _LYNX-778_：安裝 adobe-commerce/storefront-compatibility 套件時，具有 OPTIONS 方法 的 GraphQL 呼叫傳回 500 回應代碼
   * _修正注意_：修正安裝 adobe-commerce/storefront-compatibility 包時，使用 OPTIONS 方法 的 GraphQL 調用會傳回 500 個內部伺服器錯誤的問題。 終結點現在按預期正確返回 200/204 回應。

### 其他開發人員工具

* _AC-10658_： [問題] ：修正visual.phtml中的HTML語法錯誤
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
* _AC-12731_：CSP 問題與 dev/css/use_css_關鍵_path 結合
   * _修正注意事項_：系統現在可以在結帳頁面上異步正確載入 CSS 檔，平均啟用“dev/css/use_css_關鍵_path”設置時，確保這些頁面以正確的 CSS 樣式呈現。 以前，受限內容安全策略 （CSP） 阻止執行內聯JavaScript，從而導致 CSS 檔無法按預期載入。
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
   * _修復注意事項_：修復后使用信用卡下訂單時收到錯誤（付款被拒絕） 成功下訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_：每次在檢視交易畫面上按一下擷取按鈕時，Payflow都會建立新交易
   * _修正附註_：系統現在會正確擷取交易資訊，而不需在每次按一下檢視交易畫面上的擷取按鈕時建立新的付款交易。 先前，按一下「擷取」按鈕會錯誤地為已支付的訂單建立新的付款交易。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_：加拿大貝寶商家帳戶的PDP中未顯示Paylater訊息
   * _修正備註_：系統現在會在「產品詳細資料頁面(PDP)」上正確顯示加拿大PayPal商家帳戶的PayLater訊息，而可從帳戶帳單地址或出貨來決定買方的國家/地區。 以前，由於缺少引數，不會顯示PayLater訊息，這會導致瀏覽器主控台發生錯誤。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_：PayPal訂單退款結果重複貸項通知單
   * _修正注意_：修復了IPN為PayPal付款服務創建的貸項通知單的併發問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_： 購物車價格規則不適用於PayPal
   * _修正注意_：通過付款方式應用折扣時PayPal一側會顯示正確的金額
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_： [具有特定角色的雲] 用戶無法登入
   * _修正注意_：具有僅包含PayPal區域訪問許可權的角色的管理員用戶現在可以登入而不會出錯
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/66dea0de>

### 性能

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
* _ACP2E-2926_: [CLOUD]Cart Price Rule for Visitors Customer Segment not applying discount on cart
   * _Fix note_: The system now correctly applies Cart Price Rules for Visitor Customer Segments, even if the rule does not use a coupon, ensuring that the appropriate discounts are applied to the cart. Previously, discounts were not being applied to the cart for Visitor Customer Segments unless the Cart Price Rule used a coupon.
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
   * _修復說明_：在修復之前，您需要完全按照配置鍵入抵用券代碼考量大寫或小寫。 現在，無論程式碼設定是大寫還是小寫，都將在後端驗證抵用券。
* _ACP2E-3349_：購物車規則“整購物車固定金額折扣”作錯誤地應用折扣
   * _修正備註_：從管理區域建立訂單時，無論大寫或小寫為何，都將正確驗證優惠券代碼。 之前，如果優惠券代碼與設定購物車規則代碼的字母大小寫不符，系統不會驗證優惠券代碼。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_：在後端，預設產品屬性的存放區值（而不是預期的管理員值）
   * _修正說明_：現在在後端中，使用管理員值代替產品屬性的預設商店值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_：購物車規則“整購物車固定金額折扣”作在添加捆綁商品時錯誤地應用折扣
   * _修正附注_： 固定數量購物車規則未正確套用至捆綁商品。 現在，在計算總折扣金額時，捆綁子產品會考量，從而產生適當的折扣計算。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_：購物車價格規則計算折扣錯誤
   * _修正備註_：正在正確計算固定金額折扣。 修正前，套件組合產品的固定金額折扣總計不正確。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_：規則條件中的巢狀類別未顯示
   * _修正附註_：修正層級3類別的巢狀類別未顯示在類別條件的行銷規則中的問題
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_：usage_limit和 uses_per_客戶 在 salesrule_抵用券 表格中未更新
   * _修正說明_：現在，更新每張優惠券的使用次數和每張客戶的使用次數購物車價格規則將影響現有的自動生成優惠券。 以前，新值只會影響新優惠券
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_：購物車價格 規則 在使用“等於或大於”條件時不考慮父類別。
   * _修正備註_：當在進階狀況中使用父類別時，購物車價格規則現在會正確考慮父類別
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_：優先順序的折扣計算無效
   * _修正備註_：在套用整個購物車折扣型別的固定金額的情況下，先前促銷已折扣的購物車專案無法正確計算金額。 現在，折扣得到了適當的總結。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3472_： [雲] 發貨計算未考慮購物車規則
   * _修正說明_：在修正之前，區域條件的購物車規則並未一致地套用。 修正後，購物車具有區域条件的規則將正確套用。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_：發票的購物車規則SKU條件失敗。
   * _修正注意_：具有動態價格的捆綁商品的折扣現在可以正確反映在發票中。 以前，折扣不會反映在發票上。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_：當多個購物車價格規則同時應用於折扣/特價產品時，折扣值不正確
   * _修正備註_：修正前，如果套用多個購物車規則，則整個購物車規則的固定金額未正確套用。 現在，已正確套用固定金額折扣購物車規則。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1984c61c>

### 返回

* _ACP2E-3330_： [雲端]受限制的管理員使用者可以看到傳回功能表和按鈕
   * _修正附註_：受限制的管理員使用者現在無法存取RMA相關控制項（功能表和按鈕）。
先前受限制的管理員使用者可以看到傳回功能表和按鈕。
* _ACP2E-3443_：重新整理熒幕時傳回熒幕發生問題
   * _修復注意_：用戶可以刷新頁面而不會遇到屏幕失真。

### SEO

* _AC-11907_：使用重音符號添加URL重寫會導致無限載入
   * _修復說明_：系統現在已成功創建並使用重音重寫URL防止在保存過程中無限載入。 以前，添加帶有重音符號的URL重寫會導致無限載入問題。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38692>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_：多存儲錯誤類別 url 重寫為第三級類別
   * _修正注意_：使用自定義作用域 URL 鍵為具有父級的子項生成正確的 url 重寫
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_：產品名稱欄位中的雙位元組位元（特殊字元）阻止後端中的產品創建
   * _修正說明_：添加了一個新設置，允許您是否對產品URL應用音譯。 設定可在此處取得： 儲存>設定 > 目錄 > 目錄> Search引擎優化： 「產品URL的套用音譯」
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_：在一個商店群組中建立多個商店的url_rewrite專案不正確
   * _修正附註_：修正前，您只能在編輯產品時產生網站層級的URL重寫。 修正中引進了新的設定（商店>設定>目錄>目錄>搜尋引擎最佳化，「產品URL重寫範圍」搭配選項「商店檢視」、「網站」），可讓您在商店檢視或網站層級產生URL重寫。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/2d627301>

### 銷售

* _AC-13751_：如果已應用第一個購物車規則，則不應用第二個購物車價格規則

### 搜索

* _AC-13053_：獲取“輸入搜尋術語，然後重試”。 2.4.8-beta1 中店面中高级搜尋頁面錯誤
   * _修正附注_： 現在，當產品屬性設置為“否”時，系統會在進階Search頁面上正確顯示搜尋結果。 以前，將產品屬性設置為「否」並執行搜尋會導致錯誤消息「輸入搜尋詞，然後重試」。
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
   * _GitHub 代碼貢獻_： <https://github.com/magento/security-package/commit/8f64ab3c>

### 送貨

* _AC-10757_： [問題] 修正 tracking.phtml 中的錯字 - 將 JS 函數「currier」重新命名為「carrier」
   * _修正說明_：系統現在在訂單跟蹤範本中使用的JavaScript處理程式函數中正確使用術語“carrier”，而不是拼寫錯誤的“currier”，從而確保正確的函數命名和代碼清晰度。 以前，使用拼寫錯誤的術語“currier”，導致代碼庫中潛在的混淆和不一致。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/34523>
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
* _ACP2E-2763_：即使應用了免費送貨，仍顯示表格費率
   * _修正注意_：如果應用后平均免費送貨抵用券可用，現在會顯示表格費率送貨方式
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
   * _修正說明_：現在，在當前運行的更新中修改後續計劃更新中的產品屬性值時，系統會正確清除此類值。 以前，當正在運行的計劃更新修改產品屬性時，在創建新的計劃更新時無法清除此類屬性值，這需要用戶在創建后重新編輯它們。
* _ACP2E-2999_：購物車價格規則起始日期和截止日期問題未與分段更新同步
   * _修正注意_：會根據「購物車價格規則暫存」的更新來儲存日期。
* _ACP2E-3104_：暫存預覽中的 JS 錯誤
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
   * _修正說明_：由於 PHPDoc 中的拼寫更正，系統現在可以正確識別 IDE 中已棄用的方法。 以前，PHPDoc 中的拼寫錯誤導致 IDE 無法將某些方法識別為已棄用。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/31399>
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/pull/31398>
* _AC-13478_：MAGETWO-95118：會話過期后，使用持久性購物車檢查行為
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_：集成測試失敗 Magento\協商報價\控制器\報價\下載測試：：testCompanyManagerDownloadWithNQSubPermission
* _AC-13722_： [如果資料庫包含有關Target規則而不帶條件的記錄，則資料庫比較] 致命錯誤
   * _修復說明_：早些時候，如果資料庫包含有關目標的記錄，則沒有任何條件規則出現致命錯誤，但在修復資料庫比較后，工具成功通過而沒有致命錯誤。
* _AC-13848_：修復靜態測試以允許第三方擴展使用
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_： [執行期間或日誌中未顯示內部] 夾具應用失敗
   * _修復註釋_：“-
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_： [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _修正說明_：修復了 mftfs
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/078c387e>

### UI框架

* _AC-12128_： Prototype.js安全性弱點修正CVE-2020-27511
   * _修正附註_：系統已更新，以解決Prototype.js 1.7.3中的安全性弱點CVE-2020-27511，進而加強系統的整體安全性。 在此更新之前，系統可能會因為移除精心製作的HTML標籤而遭受規則運算式拒絕服務(ReDOS)攻擊。
   * _GitHub 代碼貢獻_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_：咕嚕咕嚕少使用發佈/前綴作為源地圖
   * _修復說明_：系統現在在使用 grunt 時生成較少的路徑沒有 /pub 前置綴的 /css 源映射，無需在 Web 伺服器配置中提供解決方法。 以前，在源映射路徑中使用 /pub 前置碼需要 Web 伺服器中的特定配置才能正常運行。
   * _GitHub 問題_： <https://github.com/magento/magento2/issues/38837>
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
   * _修正說明_：系統現在會從最終的 CSS 輸出檔中排除與禁用模組相關的 CSS，確保不會載入不必要的樣式。 以前，與禁用模組相關的 CSS 包含在最終的 CSS 輸出檔中，從而導致載入額外的、不必要的樣式。
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
