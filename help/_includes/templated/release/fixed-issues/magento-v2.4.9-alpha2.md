---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4173'
ht-degree: 0%

---
# Magento Open Source發行說明(v2.4.9-alpha2)

## 已修正v2.4.9-alpha2中的問題

我們已修正Magento Open Source 2.4.9-alpha2核心程式碼中的109個問題。 此版本中包含的已修正問題子集說明如下。

### API

#### 套用SpecialPrice時的特殊價格截止日期驗證錯誤

有關特殊價格的系統運作正常，而產品特殊價格將在管理員或第三方系統透過REST API設定的日期到期

_AC-13130 - [GitHub問題](https://github.com/magento/magento2/issues/39169) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39690)_

#### 格式錯誤的請求本文或引數會造成「內部伺服器錯誤」

_AC-746 - [GitHub問題](https://github.com/magento/magento2/issues/32784) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f1adb44e)_

#### 訂單「base_row_total」和「row_total」會在REST API回應中顯示單一料號價格

訂購詳細資料的REST API回應現在包含「base_row_total」和「row_total」屬性的正確值，以備有多個相同專案訂購時使用

_ACP2E-3874 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

### API、順序

#### [雲端]訂單000075568料列總計外觀的訂單資訊問題

修正當專案完全折扣時，訂單API回應中的row_total_incl_tax值會以接近零的殘值傳回，而非0.00的問題。

_ACP2E-3950 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

### 帳戶

#### 在具有o和.swiss網域的Admin Panel中更新客戶電子郵件時出現問題

_AC-13409 - [GitHub問題](https://github.com/magento/magento2/issues/39394) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d3ea191d)_

#### Newsletter訂閱啟用的切換器無法依網站/商店運作

當我們在全域層級停用多個網站/商店評論時，系統可正確處理電子報訂閱

_AC-14283 - [GitHub問題](https://github.com/magento/magento2/issues/39751) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39752)_

#### [問題]已移除電子郵件洩漏

現在，系統顯示「如果不需要輸入電子郵件來確認帳戶，則顯示錯誤訊息，指出不正確的電子郵件，無論客戶是否存在。

_AC-14561 - [GitHub問題](https://github.com/magento/magento2/issues/39574) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39570)_

### 管理員UI

#### 對於簡單產品的相同設定，購物車頁面和產品頁面中的FPT值不同

_AC-13066 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8953613e)_

#### 色票模組停用時，無法儲存多選/選取屬性選項

_AC-13071 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8953613e)_

#### 對於動態產品的相同設定，購物車頁面和產品頁面中的FPT值不同

_AC-13075 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8953613e)_

#### 在管理員中，浮動顏色未套用至靜態格點

「管理」靜態格點的列現在會依預期套用游標停留顏色。[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub問題](https://github.com/magento/magento2/issues/35358) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/35384)_

#### [Staging2]已儲存的卡片在管理面板上不可見

修正升級後，「預存卡」付款選項不再出現在後端訂購表單的問題。

_ACP2E-3830 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### 來賓簽出時公司欄位驗證失敗

_AC-14987 - [GitHub問題](https://github.com/magento/magento2/issues/40011) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f1adb44e)_

### 組合

#### 從跨主題的套件輸出中排除Hugerte Editor JS檔案

_AC-15128 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/43648891) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2bc584af)_

### 購物車與結帳

#### 缺少已分組的產品前端數量驗證

系統現在運作正常，並在我們嘗試新增負數和最大數時顯示驗證錯誤

_AC-13524 - [GitHub問題](https://github.com/magento/magento2/issues/39479) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39480)_

#### 未儲存到報價位址2.4.8的訪客首碼

_AC-14705 - [GitHub問題](https://github.com/magento/magento2/issues/39915) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f1adb44e)_

#### [問題]設定報價專案的價格，而非base_price

如果您在前端的一個網站中有多個貨幣，系統會正確處理報價專案的價格集，使其設為base_price，而不是價格

_AC-9985 - [GitHub問題](https://github.com/magento/magento2/issues/38094) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36878)_

#### 如果訂單是建立在一個商店檢視上，則[雲端]最近訂購未出現在其他商店檢視中

解決「我的帳戶」頁面未顯示同一商店中其他商店檢視之最近訂單的問題。 已更新訂單擷取邏輯，以確保所有商店檢視的訂單可見度一致，並與「我的訂單」頁面的行為一致。

_ACP2E-3807 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 數量顯示為  新增BUNDLE產品時，管理員客戶購物車區段中的0  

客戶活動中的購物車區段現在會顯示正確的數量。 以前，數量顯示為0。

_ACP2E-3872 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL的「購物車與結帳」

#### 透過GraphQL下訂單時將訊息對應到錯誤碼時發生錯誤

GraphQL呼叫對不存在或非使用中的購物車下訂單，現在會在所有商店檢視中正確傳回CART_NOT_ACTIVE或CART_NOT_FOUND錯誤碼，修正先前翻譯錯誤訊息導致「未定義」代碼的問題。

_ACP2E-3942 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

### 購物車與結帳、GraphQL、詳細目錄/MSI

#### CartItemInterface中的is_available屬性會傳回false，即使可銷售庫存很高

當可售庫存較高時，is_available屬性會傳回true。 之前，一律會傳回false。

_ACP2E-3885 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

### 目錄

#### 目錄URL資源(_getCategories)中的範圍錯誤

如果類別URL資源的存放區範圍未定義任何值，此PR會新增遞補至預設範圍。

_AC-11011 - [GitHub問題](https://github.com/magento/magento2/issues/38393) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38394)_

#### [問題]檢查OpenGraph是否可顯示價格

當我們使用隱藏價格的外掛程式，而具有此變更價格的外掛程式不會顯示在OG標籤中時，系統可正常運作。

_AC-11635 - [GitHub問題](https://github.com/magento/magento2/issues/38512) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38510)_

#### [錯誤] REST API：更新特殊價格未設定所有商店檢視的值

_AC-13671 - [GitHub問題](https://github.com/magento/magento2/issues/39521) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP錯誤未通知

此PR會變更回圈變數名稱，以便在指定的產品上正確新增「_cache_instance_product_ids」資料，以用於後續呼叫。

_AC-14159 - [GitHub問題](https://github.com/magento/magento2/issues/39641) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39642)_

#### [Mainline] [雲端]影像大小調整耗用超過400GB的磁碟空間

修正後，搭配 — skip_hidden_images旗標使用的`catalog:images:resize`命令將不會針對沒有影像的網站產生影像快取。

_ACP2E-3869 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9ad7d277)_

#### 提供的CountryID不存在 — 愛爾蘭(IE)

修正後，愛爾蘭郵遞區號可用於搜尋取車地點。

_ACP2E-3932 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/d2f1d6c6)_

### 目錄，效能

#### 管理員中的類別載入速度非常慢

類別載入效能已大幅改善。 之前，載入類別所花的時間過長，導致逾時問題。

_ACP2E-3891 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

### 目錄，定價

#### 套用至子產品的目錄價格規則折扣錯誤

修正兩個規則具有相同優先順序的情況下，上層可設定產品會覆寫變數的目錄價格規則的問題。

_ACP2E-3693 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a20a6ff2)_

### 目錄，搜尋

#### RestApi要求&#39;/rest/default/V1/categories？searchCriteria%5Bpage_size%5D=1&#39;因逾時錯誤而失敗

_AC-13358 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

### 內容

#### 升級到magento 2.4.7後，p2無法看到新上傳的檔案媒體集

_AC-13262 - [GitHub問題](https://github.com/magento/magento2/issues/39275)_

#### 將相簿影像完全移除後，會保留設定範圍的角色/型別（基底/小型/縮圖），並在重新新增「舊」角色/型別後顯示

系統在存放區範圍中如預期般運作，影像會根據預設範圍繼承新新增影像的角色/型別

_AC-13556 - [GitHub問題](https://github.com/magento/magento2/issues/39481) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39680)_

#### [小錯誤]當欄位值包含`listing component`時，無法點選管理面板`\`的篩選器

當我們篩選含有斜線的頁面標題時(例如： Magento\Store)，系統可正常運作

_AC-13661 - [GitHub問題](https://github.com/magento/magento2/issues/39513) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39535)_

#### ID為「0」的CMS頁面不存在，記錄泛濫

建立管理員使用者後以及建立新頁面時，系統如預期般運作。log沒有任何錯誤訊息

_AC-14254 - [GitHub問題](https://github.com/magento/magento2/issues/39743) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39746)_

#### 目錄連結Widget使用不正確的URL

新增目錄產品連結和目錄類別連結後，系統現在可以正確處理Widget，並在HTML來源中顯示正確的URL

_AC-14437 - [GitHub問題](https://github.com/magento/magento2/issues/39464) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39710)_

#### 如果使用者沒有Widget許可權，頁面產生器的產品元件就無法運作

修正前，存取沒有許可權的Widget時，頁面擲回一般錯誤並顯示「載入」GIF。 現在，修正後，強制回應視窗會顯示「很抱歉，您需要許可權才能檢視此內容」。 訊息。

_ACP2E-3664 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### GraphQL中未套用頁面產生器產品Widget順序

修正GraphQL「路由」查詢回應未傳回頁面產生器產品內容型別中正確排序順序的產品的問題。

_ACP2E-3898 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### 因ICU資料庫版本而在非英文店面顯示定價問題

修正後，產品價格會以希伯來文（以色列）地區設定正確顯示。

_ACP2E-3938 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

#### 更新存放區代碼已清除設計設定

修正由於設定快取未正確更新而更新存放區檢視程式碼會清除「設計組態」設定的問題。

_ACP2E-3941 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

### 框架

#### 使用自訂DB觸發程式執行命令安裝程式:upgrade時發生錯誤

_AC-11487 - [GitHub問題](https://github.com/magento/magento2/issues/38481)_

#### 網站/群組/存放區實體表單無法延伸為擴充功能屬性的多個值表單元素

此PR允許多值表單元素將資料提交至網站/群組/商店表單。

_AC-11657 - [GitHub問題](https://github.com/magento/magento2/issues/24070) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/24094)_

#### [問題]移除領域解析器使用情形

此PR會全域解析管理員URL設定，而非目前的商店

_AC-11736 - [GitHub問題](https://github.com/magento/magento2/issues/38566) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38554)_

#### 透過設定路由使用預設Nginx設定的Magento版本公開

系統目前如預期般運作，不會公開網站執行中的確切Magento版本

_AC-13205 - [GitHub問題](https://github.com/magento/magento2/issues/39227) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39228)_

#### [問題]重構報價地址確實驗證方法

此PR包含doValidate方法的可讀性改善。

_AC-13214 - [GitHub問題](https://github.com/magento/magento2/issues/38230) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38219)_

#### Magento選項 — 執行cli時從未使用過magento-init-params？

_AC-13231 - [GitHub問題](https://github.com/magento/magento2/issues/39248) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue型別宣告錯誤

現在，系統在getItemsByColumnValue函式中，將輸入引數$value正確定義為基本型別，而非陣列，確保該函式傳回預期的集合。 以前，如果使用具有單一值的陣列作為輸入引數，該函式將傳回null，並且IDE會將其標籤為錯誤。

_AC-13240 - [GitHub問題](https://github.com/magento/magento2/issues/33070) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33120)_

#### Magento 2.4.7多商店實作中與FPC相關的快取金鑰

_AC-13719 - [GitHub問題](https://github.com/magento/magento2/issues/39456) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ae6f305b)_

#### Magento Rest API公開PII

_AC-13904 - [GitHub問題](https://github.com/magento/magento2/issues/39336)_

#### 部分索引已停止對有大量更新的客戶運作

_AC-14424 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 在模組內部不需要調查「使用嚴格」

_AC-14517 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/77c589a6)_

#### MView機制會在執行觸發程式時無訊息地忽略錯誤

_AC-14567 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ae6f305b)_

#### [問題]避免在版面XML合併載入期間發生許多不必要的例外狀況

此PR引入新函式（對於B/C元件，我們不會覆寫受保護的_loadXmlString）以載入且不會擲回例外狀況

_AC-14580 - [GitHub問題](https://github.com/magento/magento2/issues/39877) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37570)_

#### [問題]在模組Vault圖形Ql中使用建構函式屬性升級

此PR會以VaultGraphQl模組中的屬性升級來取代建構函式屬性

_AC-14616 - [GitHub問題](https://github.com/magento/magento2/issues/39900) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36996)_

#### [問題]已移除模組前端配置的程式碼備援。

此PR會移除Magento_Msrp、Magento_LoginAsCustomerAssistance、Magento_Newsletter和Magento_Sitemap模組前端版面配置之主題版面的程式碼備援。

_AC-14625 - [GitHub問題](https://github.com/magento/magento2/issues/30673) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/30644)_

#### [問題]移除與Microsoft IIS相關的程式碼

此PR會依照Magento系統需求檔案清理與Microsoft IIS相關的程式碼，其中指出不支援Microsoft Windows作業系統

_AC-14702 - [GitHub問題](https://github.com/magento/magento2/issues/39910) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js語法錯誤

系統Magnifier功能應該保持以前的工作方式，而且不應該在全域範圍中使用magnifierOptions

_AC-14722 - [GitHub問題](https://github.com/magento/magento2/issues/36200) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39321)_

#### `setup:db:status` CLI命令中的反向連線詳細模式

_AC-14807 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 使用tls和2.4.8傳送SMTP郵件

_AC-14883 - [GitHub問題](https://github.com/magento/magento2/issues/39947) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8b453942) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d3ea191d)_

#### [問題]修正靜態內容部署中的並行問題

此PR修正多個同時處理程式向上旋轉以處理相同主題套件的錯誤，具體取決於主題與其父項的定義方式。

_AC-14944 - [GitHub問題](https://github.com/magento/magento2/issues/39990) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39954)_

#### [問題]移除PHP版本&lt; 8.1的舊版相容性代碼

此提取請求會移除設計在PHP &lt;8.1上執行的程式碼。
此外，已移除對PHP_VERSION_ID連絡人可用性的檢查，因為它可在所有PHP版本中使用

_AC-14971 - [GitHub問題](https://github.com/magento/magento2/issues/39891) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39882)_

#### 登入時FPC無法運作

_AC-14999 - [GitHub問題](https://github.com/magento/magento2/issues/40007) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/)_

#### [問題]改善處理SchemaBuilder的錯誤

此PR可改善資料庫架構的錯誤訊息處理方式。 它有助於我們識別問題，而不需要大量偵錯。

_AC-15020 - [GitHub問題](https://github.com/magento/magento2/issues/39816) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39799)_

#### 由於CliStateTest修改，2.4.9-alpha2-develop的SYNC PR整合測試失敗

_AC-15136 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2d0f8066)_

#### PHP8.1型別bugfix

現在，當嚴格處理模式非作用中或產品資訊可用時，關聯的產品會初始化為空陣列，而非false。 此變更可確保後續邏輯處理相關產品的行為一致，改善產品準備程式的穩定性和可預測性。

_AC-6017 - [GitHub問題](https://github.com/magento/magento2/issues/35808) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/35842)_

#### [問題]從架構（第3部分）移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8343 - [GitHub問題](https://github.com/magento/magento2/issues/37270) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37020)_

#### [問題]在模組send friend圖形ql中使用建構函式屬性升級

系統現在會在「send friend」GraphQL模組中利用建構函式屬性升級，增強程式碼可讀性並降低複雜性。 過去，模組使用佔據許多行的屬性，使程式碼更複雜且不易讀取。

_AC-8346 - [GitHub問題](https://github.com/magento/magento2/issues/37235) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37197)_

#### [問題]從`@author`移除禁止的`Magento_Downloadable`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8355 - [GitHub問題](https://github.com/magento/magento2/issues/37251) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37001)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，提高程式碼品質和一致性。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8358 - [GitHub問題](https://github.com/magento/magento2/issues/37264) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37014)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8360 - [GitHub問題](https://github.com/magento/magento2/issues/37261) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37011)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，確保程式碼更乾淨且標準化。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8361 - [GitHub問題](https://github.com/magento/magento2/issues/37260) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37010)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8363 - [GitHub問題](https://github.com/magento/magento2/issues/37258) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37008)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8375 - [GitHub問題](https://github.com/magento/magento2/issues/37257) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37007)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8376 - [GitHub問題](https://github.com/magento/magento2/issues/37256) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37006)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8400 - [GitHub問題](https://github.com/magento/magento2/issues/37254) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37004)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8401 - [GitHub問題](https://github.com/magento/magento2/issues/37255) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37005)_

#### [問題]改善服務URL產生的可擴充性

系統現在允許透過外掛程式自訂服務URL產生函式，以推動更易於維護的修改方法。 以前，此功能的自訂功能是透過偏好設定來完成，這可能不太有效率或無法維護。

_AC-8813 - [GitHub問題](https://github.com/magento/magento2/issues/37404) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37403)_

#### 由於新增驗證，因此與升級2.4.7-p5有關的問題

修正SchemaBuilder類別中，未定義的陣列索引鍵「欄」在結構描述建立或更新期間當機的問題。 處理不包含「欄」索引鍵的表格資料時，就會發生此問題。

_ACP2E-3871 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9ad7d277)_

#### PHP8.4淘汰錯誤：升級至Adobe Commerce 2.4.8後出現E_USER_ERROR

針對客戶的案例不會受到此修正的影響。

_ACP2E-3963 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

### 框架，搜尋

#### 單一定價類別的Opensearch 2.19.1 illegal_argument_exception

Opensearch不再對包含所有相同價格產品的類別擲回illegal_argument_exception。 之前，它有此例外狀況&quot;[from]引數不能為負數&quot;。

_ACP2E-3896 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### 在GraphQL要求中，願望清單專案不會在單一網站的商店檢視之間共用

在修正前，會依存放區ID篩選願望清單專案。 現在，修正後，願望清單專案會依網站篩選。

_ACP2E-3987 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL，產品

#### MediaGalleryInterface中的產品graphql缺少media_type

MediaGallery GraphQL要求現在包含產品影像型別的「型別」欄位。 之前，此「型別」欄位不存在於MediaGallery GraphQL請求中。

_ACP2E-3880 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

### 庫存/MSI

#### 重新導向至首頁並結帳後，沒有可用的存放區

如果客戶導覽至付款頁面，然後返回首頁，最後返回結帳頁面，則先前選取的商店現在會在「店內撿料」配送中預先選取。 先前，在重複回到結帳頁面後，系統會清除「取用商店」中選取的商店。

_ACP2E-3793 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/62c0d79b)_

### 訂購

#### AbstractAddress setData(&#39;custom_attributes&#39;， AttributeValue[])中斷customAttributes

_AC-10568 - [GitHub問題](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento重新排序–1訂單編號

系統如預期般運作，從後端重新排序後，訂單編號將是8位數的唯一值

_AC-12854 - [GitHub問題](https://github.com/magento/magento2/issues/39089) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39399)_

#### 使用Adobe信用卡付款方式結帳時，產品自訂選項檔案上傳遺失

_AC-14306 - [GitHub問題](https://github.com/magento/magento2/issues/39647)_

#### 訂單狀態卡在處理中

修正前，當訂購啟用「一併送貨」選項的套件組合產品時，訂單狀態在發票和送貨後不會自動切換為「完成」。 現在，修正之後，訂單狀態會在開立商業發票並出貨後，自動切換為「完成」。

_ACP2E-3947 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a252ae6)_

#### [雲端]Magento OOTB程式碼 — 電子郵件範本設定問題

修正前，使用非同步電子郵件傳送時，出貨電子郵件與商店訂單不一致。 現在，修正後，適當的商店出貨電子郵件訂單已送達。

_ACP2E-3998 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

### 其他開發人員工具

#### [問題]受保護成員$_urlHelper的型別提示錯誤

系統現在會以正確的提示來修正錯誤的型別提示，建構函式中也會使用這個提示

_AC-10716 - [GitHub問題](https://github.com/magento/magento2/issues/32503) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32496)_

### 效能

#### [問題]更新Store.php

此PR會略過目前的商店解析度，進而改善效能。

_AC-14791 - [GitHub問題](https://github.com/magento/magento2/issues/39949) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38717)_

### 定價

#### Order Rest API中，沒有動態價格的套件組合產品專案的價格一律為0

_AC-11925 - [GitHub問題](https://github.com/magento/magento2/issues/38687) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7da46f52)_

### 產品

#### 依原始價格計算的層級價格與型錄價格規則的折扣百分比（不含選取的選項）。

_AC-12004 - [GitHub問題](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minAllowed遺失產品訂單數量

系統運作正常，頁面來源正確顯示產品的最低數量

_AC-12909 - [GitHub問題](https://github.com/magento/magento2/issues/39142) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39480)_

#### 管理面板中產品頁面上的可自訂選項格線問題

使用型別下拉式清單建立可自訂選項時，系統可如預期運作

_AC-14003 - [GitHub問題](https://github.com/magento/magento2/issues/39640) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39694)_

#### 來自其他客戶比較清單的所有專案在透過管理員登入後都會指派給客戶

先前，當管理員在後端使用「以客戶身分登入」功能時，先前登入的客戶比較清單中的產品會錯誤指派給目前模擬的客戶。  修正後，比較清單會正確載入正確登入的客戶。

_ACP2E-3818 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### 透過REST API更新產品url_key不會產生301 URL重寫

透過REST API更新產品的URL金鑰時，如果將「如果URL金鑰變更，請為URL建立永久重新導向」設定設為「是」，產品URL重寫會建立從舊URL到新URL的重新導向。

_ACP2E-3900 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

### 安全性

#### 套件式/合併式JS不屬於SRI雜湊

在修正之前，產生的套件組合或合併的檔案並未新增至SRI雜湊清單。 現在，檔案已適當地新增至SRI雜湊。

_ACP2E-3854 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

### 送貨

#### [QUANS] - Magento_Fedex核心模組在傳送要求以取得新權杖之前，是否會檢查有效的作用中權杖？

Adobe Commerce很快會向FedEx API服務提出許多要求來取得存取權杖。 先前，即使存取權杖仍然有效，Adobe Commerce一律會向FedEx API提出新請求，導致速率限制問題。

_ACP2E-3930 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

### 測試和預覽

#### 無法在啟用類別許可權的情況下預覽排程的產品更新

在修正之前，要啟用的未來產品不會以預覽模式顯示。 現在，即使目前狀態為停用，也會顯示它。

_ACP2E-3786 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

#### 缺少目錄價格規則折扣金額欄位的驗證

之前，使用目前驗證規則時，暫存排程更新中的discount_amount欄位無法正確驗證。 不過，在套用修正之後，將會適當地驗證discount_amount欄位。

_ACP2E-3867 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

### 稅金

#### 錯誤訂單總計，舍入不會套用至價格計算。

系統現在可在計算price_after_discount、discount_amount及稅額時正確處理。
訂單的實際總計

_AC-11389 - [GitHub問題](https://github.com/magento/magento2/issues/38455) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39687)_

### 測試架構

#### [問題]忽略lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

系統現在會忽略執行單元測試時產生的&#39;env.php&#39;檔案，確保Git狀態在執行測試後保持乾淨。 以前，執行單元測試會產生新檔案&#39;env.php&#39;，導致Git狀態顯示找到的新檔案，並使其看起來很髒。

_AC-13293 - [GitHub問題](https://github.com/magento/magento2/issues/39304) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37631)_

#### [問題]修正攔截器的整合測試問題

系統現在可以在整合測試中正確識別及處理\Magento\TestFramework\App\Config\Interceptor ，確保測試可以存取必要的資料，即使類別上有外掛程式存在。 之前，系統無法考慮\Magento\TestFramework\App\Config成為\Magento\TestFramework\App\Config\Interceptor的可能性，導致在嘗試存取$data屬性時發生錯誤。

_AC-13305 - [GitHub問題](https://github.com/magento/magento2/issues/39324) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37187)_

#### [問題] MFTF：正在將電子郵件提交至已啟用驗證碼的Friend表單

測試案例會在啟用驗證碼時，說明「傳送電子郵件給朋友」表單的功能，確保表單提交程式可在驗證碼值不正確和正確的情況下正常運作。

_AC-13492 - [GitHub問題](https://github.com/magento/magento2/issues/39462) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] TestCase：：getTestResultObject的使用方式無效，因為phpunit v10

_AC-13502 - [GitHub問題](https://github.com/magento/magento2/issues/39463)_

#### AC 2.4.7-p3中的環境特定單元測試失敗

此問題會修正未在所有版本和環境上重製的單元測試失敗。 以前，為了修正此問題，部分單元測試會因為不同程式庫版本或因較新版本新增的功能遺失而失敗。

_ACP2E-3712 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9ad7d277)_

### UI框架

#### 動態列中的WYSIWYG是空的

_AC-12336 - [GitHub問題](https://github.com/magento/magento2/issues/38893) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [問題]修正MIME型別錯字

系統可正確處理並修正gif影像的mime型別和拼寫錯誤

_AC-8001 - [GitHub問題](https://github.com/magento/magento2/issues/36899) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36669)_

#### [問題]避免直接存取檢閱清單Ajax

系統可正確處理並避免直接存取檢閱清單Ajax

_AC-9381 - [GitHub問題](https://github.com/magento/magento2/issues/37920) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33876)_

### 升級 — 升級相容性工具

#### 已棄用的功能：建立動態屬性Magento\Framework\Acl：：$_roleRegistry

_AC-12343 - [GitHub問題](https://github.com/magento/magento2/issues/37469)_
