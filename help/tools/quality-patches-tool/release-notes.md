---
title: 發行說明
description: 了解適用於Adobe Commerce的修補程式及其解決的問題。
source-git-commit: e9ba2d0ad8568c40335e8643ef0070d9e2bb9b3f
workflow-type: tm+mt
source-wordcount: '9581'
ht-degree: 0%

---

# 發行說明

此 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source社區開發的單個補丁。 它允許您應用、恢復和查看有關所有單個修補程式的一般資訊，這些修補程式可用於已安裝的Adobe Commerce版本或Magento Open Source。 您可以將修補程式應用到Adobe Commerce和Magento Open Source項目，而不管誰開發了修補程式。 例如，您可以將社群開發的修補程式套用至Adobe Commerce專案。

>[!INFO]
>
>請參閱 [應用修補程式](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) 以取得將修補程式套用至Adobe Commerce或Magento Open Source專案的說明。 請參閱 [可用修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ，查看已發佈修補程式的完整清單。

>[!INFO]
>
>如需有關 [!DNL quality patches] 由社群建立以供Magento Open Source，請參閱 [發行說明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3) — 修正 _嘗試訪問類型bool的值上的陣列偏移_ 在PHP 7.4上訪問已知產品的某些非現有類別路徑時出錯。
* **ACSD-47332** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修正cron因錯誤而失敗的問題，此錯誤僅在執行00:00至00:59 UTC時回報。
* **ACSD-47280** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修正在特定範圍上停用共用目錄功能無法正確運作的問題。
* **ACSD-47106** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修正無法將值儲存在公司建立頁面上新自訂屬性中的問題。
* 更新的修補程式：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (針對Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修正指派大量產品來源時，使用者發生錯誤的問題。
* **ACSD-46856** (針對Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 通過「系統」>「配置」>「導入」>「高級定價」改進效能更新層價。
* **ACSD-46541** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修正刪除訂單項目時，管理員使用者無法建立貸項通知單的問題。
* **ACSD-46581** (針對Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修正在購物車中選取國家/地區後，預估稅金總計未更新的問題。
* **ACSD-46618** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修正產品清單介面工具集針對登入客戶顯示錯誤快取價格的問題。
* **ACSD-46674** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修正客戶電子郵件中影像類型的自訂選項顯示為HTML的問題。
* **ACSD-46988** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修正GraphQL「貨幣」API請求傳回自訂貨幣NULL值的問題。
* **ACSD-47076** (適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5) — 修正店面上無法播放Vimeo影片的問題。
* **ACSD-45071** (適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4) — 修正匯入期間新增預設來源至產品的問題。
* **AC-3023** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 將DHL配置更新為最新版本10.0。
* 更新的修補程式：MDVA-42584。
* 替換的修補程式：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修正使用商店信用證退款時，使用者收到錯誤訂單狀態的問題。
* **ACSD-46703** (*適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修正無法在產品編輯頁面上拖放自訂選項的問題。
* **ACSD-44851** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 修正具有子類別的類別無法開啟或展開的問題。
* **ACSD-46815** (*適用於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6*) — 修正類別樹請求限制為20個類別的問題。
* **ACSD-45675** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 修正產品匯出使用 *預設商店視圖* 範圍。
* **ACSD-46869** (*適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修正購物車中可設定產品未透過 *PUTREST API* 請求，而不變更產品數量。
* **MDVA-42768-V2** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正可設定產品將一般價格顯示為 *0* when *顯示無存貨* is *是*.
* 更新的修補程式：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 已廢止的修補程式：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正類別樹請求限制為20個類別的問題。
* **ACSD-45781** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.2*) — 修正行動裝置上未顯示商店前端搜尋欄位的問題。
* **ACSD-46192** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;2.4.5*) — 修正使用 `async/bulk/V1/configurable-products/bySku/options` 端點。
* **ACSD-46404** (*適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修正管理員使用者在升級至2.4.4後無法登入的問題。
* 更新的修補程式：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正特定存放區的GraphQL產品變異會傳回所有可設定變體（包括未指派給請求存放區的變體）的問題。
* **ACSD-46146** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修正向管理員下訂單後，會傳送兩封訂單確認電子郵件的問題。
* **ACSD-45255** (*適用於Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修正受限管理員使用者的「低庫存報表」頁面上的例外狀況。
* **ACSD-45488** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6*) — 修正具有多個來源的可設定產品未自動傳回至In Stock的問題。
* **ACSD-45754** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修正將抵用券套用至購物車後，未新增獎勵點數的問題。
* **ACSD-45849** (*適用於Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修正套用測試更新後視訊中繼資料遺失的問題。
* **ACSD-45257** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 修正GraphQL無法正確顯示購物車折扣的問題。
* **ACSD-44938** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修正 `VAT_ID` 無法套用至來賓使用者的GraphQL請求。
* 更新的修補程式：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修正建立貸項通知單後，虛擬產品的庫存量計算錯誤的問題。
* **ACSD-43887** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正啟用公司的「採購訂單」時，結帳付款頁面上顯示錯誤詳細資料的問題。
* **ACSD-45143** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修正 `setShippingAddressesOnCart` 變異不允許將數字區域代碼設定為 *地區*.
* **ACSD-44591** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6*) — 修正未確認驗證碼就下訂單時發生的錯誤。
* **ACSD-45520** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修正使用者從購物車編輯可設定產品時，產品詳細資料頁面上未預先選取色票選項的問題。
* **ACSD-45169** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6*) — 修正 [!DNL Visual Merchandiser] 套用測試更新後，無法顯示可設定產品的正確庫存和價格。
* **ACSD-45424** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.6*) — 修正部分退款（貸項通知單）後建立錯誤保留報酬的問題。
* **MDVA-42807** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修正自訂貨幣符號未顯示在商店前端的問題。
* 更新的修補程式：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正限制管理員使用者誤算「訂購」報表中訂單總計的問題。
* **MDVA-44940** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正從管理員儲存類別時發生的SQL錯誤。
* **MDVA-44562** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2-p2*) — 修正儘管GraphQL請求源自非預設商店檢視，但報價項目的非預設商店ID仍由預設商店ID覆寫的問題。
* **MDVA-43167** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正管理員使用者選取所有訂單時，管理員訂單格線大量動作不適用於多頁的問題。
* **MDVA-44044** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.2-p2*) — 修正將產品指派給新網站後，類別頁面上未顯示產品的問題。
* **MDVA-42509** (*適用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.4*) — 修正CSV無法上傳以取得快速訂單，導致 *無法傳送Cookie* 錯誤。
* 更新的修補程式：MDVA-41061、MDVA-42584。
* 新 [!DNL Quality Patches Tool] 修補程式將從 *MDVA* to *ACSD* 因內部程式變更。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正當購物車中已有最小數量的項目時，無法新增其他項目的問題。
* **MDVA-44887** (*適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修正 *未捕獲的語法錯誤：意外的代號「const」* 「管理」面板中出現錯誤。
* **MDVA-43718** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正 *用戶無權訪問%資源。* 從自訂整合存取共用目錄時顯示的錯誤。
* **MDVA-44660** (*適用於Adobe Commerce和Magento Open Source>=2.4.2-p1 &lt;2.4.5*) — 修正重音字元出現的問題 ``` ` ``` 無法用於客戶的名字和姓氏。
* **MDVA-40896** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正 *錯誤：類型錯誤：引數3傳遞至Magento* 非同步產品大量API中出現錯誤。
* **MDVA-38559** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修正 */V1/customers/search API* 有多個訂閱的客戶出現錯誤。
* **MDVA-44533** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.4*) — 修正將折扣錯誤套用至套件子產品的問題。
* 更新的修補程式：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正產品 *不會個別顯示* 仍顯示在「目錄進階搜尋結果」中。
* **MDVA-44100** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正所有FPT均指派給購物車中最後一項產品，並重設其他產品的問題。
* **MDVA-43605** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修正使用Rest API時，訂單資料在列總計中傳回負值的問題。
* **MDVA-43102** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修正透過REST API完成退款時，可售數量未正確更新的問題。
* **MDVA-43178** (*適用於Adobe Commerce和Magento Open Source>=2.4.3-p2 &lt;2.4.5*) — 修正無法在GraphQL中擷取自訂商店的客戶代號的問題。
* **MDVA-43859** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修正錯誤 *沒有具有customerId =的實體* 已刪除的客戶嘗試登入時，系統會將其記錄。
* **MDVA-44147** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正GraphQL請求未傳回申請清單的問題。
* **MDVA-44505** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修正GraphQL套用獎勵點不會更新總量，以及在下單期間多次套用商店評分的問題。
* 更新的修補程式：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修正「相關產品規則」僅在「客戶區段」設為「 *全部*.
* **MDVA-39605** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修正密碼快取TTL（到期日）有錯誤值的問題。
* **MDVA-43862** (*適用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修正客戶因GraphQL而無法更新購物車項目的問題 *UpdateCartItems突變* 錯誤。
* **MDVA-43824** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 修正取消含有折扣的訂單時出現錯誤的問題。
* **MDVA-43451** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正錯誤 *未找到請求的儲存。 驗證儲存並重試。* 為特定網站設定共用目錄時，就會顯示。
* **MDVA-43491** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修正為多商店網站匯入產品時，基本影像標籤未更新的問題。
* **MDVA-43601** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正完整重新索引後缺少觸發器的問題。
* **MDVA-42046** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修正更新產品時，為具有日期輸入欄位的產品屬性指派錯誤值的問題。
* **MDVA-43935** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修正向上銷售產品顯示兩次的問題。
* **MDVA-44188** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正系統發出的電子郵件 `.-` 不會傳送位址。
* **MDVA-42283** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正法文地區設定之管理順序格線中的日期 — 時間格式無效的問題。
* 更新的修補程式：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 為 [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修正使用者無法編輯作用中已排程更新之開始時間的問題。
* **MDVA-42410** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正優惠券報表只顯示預設基本貨幣的問題。
* **MDVA-41136** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正 `mage-cache-sessid` 未延伸，導致客戶資料清理。
* **MDVA-39993** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修正透過API完成的庫存變更未反映在前端產品頁面上的問題。
* **MDVA-42855** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正結帳期間新客戶地址未儲存至通訊簿的問題。
* **MDVA-42645** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正當商店信用功能停用時，管理員無法退款獎勵點的問題。
* **MDVA-43414** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2*) — 修正執行 `inventory.reservations.updateSalabilityStatus` 數值SKU上的佇列消費者。
* **MDVA-41628** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修正新增模組時，現有受限制管理員使用者可存取新資源的問題。
* **MDVA-43348** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正禮品卡GraphQL請求在 `gift_card_options` cont *uid*.
* **MDVA-39546** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正在編輯期間，測試更新的開始日期可設為比目前日期更早的問題。
* **MDVA-42950** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正產品頁面上影片未播放的問題。
* **MDVA-42689** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正Adobe Commerce擲回 *完整性約束違反* 導入期間更新產品類別時出錯。
* **MDVA-41229** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正可設定產品匯入後，後端可用影像未顯示在前端的問題。
* **MDVA-43731** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正 *搜索同義詞* 在中新增值時，將無法繼續運作 *要符合的最低詞語*.
* **MDVA-43232** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修正中排序產品的問題 [!DNL Visual Merchandiser] 按「特價至底部/頂端」會在儲存類別時造成錯誤。
* **MDVA-43726** (*適用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.3*) — 修正部分重新索引後，根據儲存層級屬性比對的目錄價格規則無法套用的問題。
* 更新的修補程式：MDVA-36464、MDVA-37478、MDVA-38608。
* 為 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正無法透過REST API針對特定網站更新產品價格屬性的問題。
* **MDVA-41350** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正當具有限制存取權的管理員使用者依訂單的SKU在其角色範圍之外新增產品時，會擲回例外狀況的問題。
* **MDVA-42269** (*適用於Adobe Commerce和Magento Open Source>=2.4.3-p1 &lt;2.4.5*) — 修正管理員使用者因 *類型錯誤：strtotime()預期參數1為字串，為null* 錯誤。
* **MDVA-40830** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正在下單期間多次套用商店評分的問題。
* **MDVA-42237** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正子產品價格變更後，無法更新可設定產品特殊價格的問題。
* **MDVA-42520** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正在 *啟用跨境貿易* 中所有規則的URL區段。
* 更新的修補程式：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已廢止的修補程式：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*適用於Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.5*) — 修正大量屬性更新僅在變更後，才會為預設商店建立URL重寫的問題 *產品可見度*.
* **MDVA-43091** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正從後端的管理員排序套件產品時發生錯誤的問題 *您不能對此產品使用小數量*.
* **MDVA-40816** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正相關產品規則顯示規則條件中未定義之類別產品的問題。
* **MDVA-41305** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正GraphQL變異新增至願望清單後未傳回可設定產品選項的問題。
* **MDVA-39181** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修正相關產品規則顯示規則條件中未定義之類別產品的問題。
* **MDVA-42584** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正透過匯入或API變更數量和庫存狀態後，後端的可設定庫存狀態未更新的問題。
* **MDVA-40175** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修正 *按一下以更改發運方法* 在重新排序期間不顯示用於在管理員中選擇發運方法的單選按鈕。
* **MDVA-42768** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修正當 *顯示無存貨* 是。
* **MDVA-43201** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正搭配特定地區設定使用DOB屬性時，客戶登入發生錯誤的問題。
* 更新的修補程式：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正當Adobe Commerce時區與本機環境時區不同時，日期篩選器無法正常運作的問題。
* **MDVA-42657** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修正管理員使用者無法在客戶區段條件中選取類別的問題。
* **MDVA-42806** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正 *新公司註冊* 每次透過REST API更新現有公司時，都會傳送電子郵件。
* **MDVA-37984** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修正 [!DNL Visual Merchandiser] *依規則比對產品* 功能無法正確篩選含有測試更新的產品。
* **MDVA-40488** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正無庫存子產品的可設定產品無法以正確價格範圍顯示的問題。
* **MDVA-42507** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正針對購物車規則套用測試更新後，已清理整頁快取的問題。
* **MDVA-39163** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修正註冊新使用者且購物車中的產品來自訪客工作階段時，無法使用運送方法的問題。
* **MDVA-38626** (*適用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修正管理員使用者無法使用 [!DNL PayPal Payflow Pro] 付款。
* **MDVA-38666** (*適用於Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.3.6*) — 修正管理員使用者無法變更客戶購物車中可設定產品選項的問題。
* **MDVA-38526** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修正管理員使用者無法存取 [!DNL Site-Wide Analysis tool].
* 更新的修補程式：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正使用者在設定 *mage-messages* cookie（若已存在），但沒有新訊息。
* **MDVA-41139** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正簡單產品的qty=0（其來源）匯入產品後，可設定產品變成無存貨的問題。
* **MDVA-42326** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正即使啟用永久性購物車，客戶在工作階段逾時後仍發生結帳錯誤的問題。
* **MDVA-42341** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正 `categoryList` 如果請求具有「儲存」標題，GraphQL查詢不會篩選結果。
* **MDVA-38393** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正如簡單產品重新命名，可設定產品的目錄規則停止運作的問題。
* **MDVA-39153** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正在管理員重新排序期間，折扣金額計算不正確的問題。
* 更新的修補程式：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.3*) — 修正管理員使用者刪除網站後無法存取客戶格線的問題。
* **MDVA-40311** (*適用於Adobe Commerce和Magento Open Source>=2.4.2-p2 &lt;2.4.4*) — 修正管理員使用者收到錯誤訊息的問題 *安全性或表單密鑰無效。 請刷新頁面* 登入管理員後（若已設定自訂管理員路徑且已啟用機密金鑰）。
* **MDVA-41631** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修正使用者嘗試擷取訂單資訊時，未選用 *電話* 值。
* **MDVA-27239** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修正未顯示交叉銷售產品的問題。
* 更新的修補程式：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修正重新索引期間前端缺少產品的問題。
* **MDVA-40120** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修正依DESC/ASC排序的GraphQL無法用於具有相同關聯性或價格的產品的問題。
* **MDVA-41399** (*適用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.2*) — 修正管理員使用者無法存取 *管理購物車* 頁面（如果客戶將產品新增至願望清單）。
* **MDVA-40609** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正中缺少已停用產品資料的問題 `cataloginventory_stock_status` 索引表，顯示不正確的禁用產品數量。
* **MDVA-39031** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修正即使產品未指派給目標網站，仍可透過GraphQL新增產品至購物車的問題。
* **MDVA-41597** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正使用者使用GraphQL將多個可設定產品新增至購物車時，發生錯誤的問題。
* **MDVA-27456** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.3.7*) — 修正使用者嘗試載入時發生錯誤的問題 [!DNL Swagger].
* **MDVA-32776** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2*) — 修正下訂單但未裝運時未更新庫存狀態的問題。
* **MDVA-30862** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.0*) — 修正已打印PDF發票上訂單日期不正確的問題。
* 改善 [!DNL Quality Patch Tool]. 為 [!DNL quality patches] 工具的最新版本。
* 更新的修補程式：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正先前已移除「結束日期」時，無法建立新產品或編輯產品現有排程更新的問題。
* **MDVA-41046** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正可指派給可設定/分組產品的簡單產品及自訂選項的問題。
* **MDVA-40545** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正即使同一頁面有多個節點，仍只擷取頁面的第一個節點的問題。
* **MDVA-41164** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3-p1*) — 修正管理員使用者無法儲存或編輯具有檔案或影像類型自訂客戶屬性之公司的問題。
* **MDVA-39229** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正更新目錄規則測試更新開始時間後，出現下列錯誤的問題： *Cron Job staging_synchronize_entities_period有錯誤：無法刪除活動更新。*
* **MDVA-40619** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正嘗試在CMS頁面上執行內嵌編輯時，變更CMS頁面階層會造成500錯誤的問題。
* **MDVA-41061** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正從管理員儲存產品時，庫存狀態重設為可出售的問題。
* **MDVA-31763** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正在手動重新索引前，目錄價格規則遭還原（或未套用）的問題。
* **MDVA-37748** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正GraphQL查詢傳回未指派至共用目錄的產品的問題。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正無法透過REST API同時建立相同訂單之部分發票的問題。
* **MDVA-40101** (*適用於Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.0*) — 修正成功下單後，項目無法從迷你購物車移除的問題，使用 [!DNL PayPal Express] 結帳。
* **MDVA-40401** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正即使下單失敗，抵用券使用值仍會變更的問題。
* **MDVA-40537** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.0-p1*) — 修正若數個CMS頁面具有相同URL索引鍵時，使用者建立商店檢視時發生錯誤的問題。
* **MDVA-37725** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.4.3-p1*) — 修正從非預設網站傳送的非同步訂購電子郵件包含預設網站標誌URL的問題。
* **MDVA-39482** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正啟用延交訂單時，如果以「0」數量匯入的產品無存貨的問題。
* **MDVA-40435** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 修正透過GraphQL套用時，具有動態價格的套件產品折扣不正確的問題。
* **MC-42528** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;=2.4.3-p1*) — 修正 `categoryList` GraphQL查詢會同時傳回已指派和未指派的類別。
* **MDVA-29400** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修正透過 [!DNL PayPal Express Checkout].
* **MDVA-26005** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2*) — 修正無法為購物車價格規則條件在類別樹中選取類別的問題。
* **MDVA-25631** (*適用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;=2.3.5-p2*) — 改善編輯和儲存包含大量客戶之客戶區段的效能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正GraphQL搜尋查詢未顯示於「管理員」中常用搜尋詞的問題。
* **MDVA-40601** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.4.2-p2*) — 修正使用者嘗試透過GraphQL排程更新而變更類別的相關資訊時，發生錯誤的問題。
* **MDVA-37234** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修正針對相同SKU多次新增項目至購物車（平行請求），為相同購物車ID建立重複條列項目的問題。
* **MDVA-33606** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;=2.4.2-p2*) — 修正使用者取得 *唯一約束違反* 保存分配給層次結構的CMS頁時出錯。
* **MDVA-31590** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.1-p1*) — 修正使用者無法使用MySQL非同步佇列大量更新屬性的問題。
* **MDVA-36309** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修正管理格線中依屬性搜尋產品速度緩慢的問題。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正從商店信用支付訂單時，具有FPT的發票顯示錯誤「總量」的問題。
* **MDVA-37364** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.3*) — 修正日期類型的自訂客戶屬性中斷客戶格線UI的問題。
* **MDVA-39195** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修正 *新增至購物車* 重新導向至購物車啟用時，「 」按鈕在類別頁面上非作用中。
* **MDVA-37115** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修正不必要的 *僅剩0個* 通知會顯示在可設定的產品頁面上。
* **MDVA-39521** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修正使用者無法透過GraphQL以空電話號碼在購物車上設定運送地址的問題。
* **MDVA-39384** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修正公司使用者的自訂客戶屬性未儲存的問題。
* **MDVA-39043** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.3*) — 修正具有有限存取權的管理員使用者嘗試新增 *產品* 介面工具集到CMS頁面。
* **MDVA-39966** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 修正部署錯誤地區設定的問題。
* **MDVA-38852** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.5-p2*) — 修正設計目錄清單鎖定表格以進行更新的問題，若有數個平行訂單，這會大幅降低效能。
* **MDVA-39986** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修正使用者無法使用Safari瀏覽器在MacOS上的「管理員」中下訂單的問題。
* **MDVA-38447** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正兩個問題：其中 *不單獨顯示* 可配置的子產品在GraphQL響應中返回，並使用類別篩選器優化GraphQL產品查詢的MySQL查詢。
* **MDVA-40134** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正啟用共用目錄時GraphQL未傳回相關產品的問題。
* **MDVA-39935** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修正GraphQL傳回可設定子產品時，網站層級會停用的問題。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修正 *呼叫成員函式getId()* 錯誤會顯示在「管理」的「訂單詳細資訊」頁面上。
* **MDVA-34948** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修正長時間執行的查詢的問題，例如 `GET_LOCK`.
* **MDVA-39305** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.2-p1*) — 修正註冊客戶無法以啟用Google ReCaptcha登入的問題。
* **MDVA-37897** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正當客戶嘗試從最近查看的介面工具集新增具有選項的產品時，錯誤重新導向的問題。

## v1.1.0 {#v1-1-0}

* 引入了修補程式類別，以改進用戶體驗，並使客戶更輕鬆地搜索所需的修補程式。
* 此 `patches.json` 檔案已重新命名為 `support-patches.json`.
* **MDVA-38799** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正建立測試更新後未儲存可下載產品的問題。
* **MDVA-37592** (*適用於Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修正為共用目錄指派零價格的產品，依價格排序無法正確運作的問題。
* **MDVA-38827** (*適用於Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) — 修正客戶收到包含錯誤訊息的訂單裝運電子郵件的問題。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*適用於Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修正儲存CMS頁面時的錯誤： *具有相同ID的項目PAGE_ID已存在*.
* **MDVA-34680** (*適用於Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修正客戶帳戶建立時間無法在客戶格線中正確篩選的問題。
* **MDVA-37068** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.4*) — 修正當購物車只有虛擬產品時，顯示錯誤稅率的問題。
* **MDVA-38608** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正當重新索引未成功完成時，暫時表格未刪除的問題。
* **MDVA-38308** (*適用於Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) — 修正與新增相關的問題 [!DNL Vimeo] 產品的影片。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*適用於Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修正使用 [!DNL Paypal Payment Advanced] 方法。
* **MDVA-37082** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正儲存分組產品的自訂庫存時，造成產品在前端顯示無庫存的問題。
* **MDVA-36572** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修正貸項通知單更新不再導致資料庫中重複產品保留更新的問題。
* **MDVA-38132** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修正因 *太多重新導向* 錯誤。
* **MDVA-38270** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正GraphQL訂單總計中遺失禮品卡資訊的問題。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*適用於Adobe Commerce >=2.4.2 &lt;=2.4.4*) — 修正當網站ID與商店ID不符時，透過GraphQL將可設定產品新增至購物車的問題。
* **MDVA-36832** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修正檢視寬度為768px時影像在頁面上重複的問題。
* **MDVA-37874** (*適用於Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 修正 *整個購物車的固定折扣金額* 套用至包含多個選項的套件產品時，會發生錯誤。
* **MDVA-37913** (*適用於Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) — 修正可下載產品透過API更新時，可下載連結消失的問題。
* **MDVA-34330** (*適用於Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) — 修正「訂單」格線中的訂單未根據「管理時區」篩選的問題。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.7*) — 修正Adobe Commerce為使用下拉式清單所下的訂單建立部分發票時，擲回錯誤的問題 *帳戶付款* 透過REST API支付方法。
* **MDVA-37362** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修正GraphQL回應中可設定產品選項值和變體屬性值空白的問題。
* **MDVA-37288** (*適用於Adobe Commerce 2.4.2*) — 修正GraphQL要求後傳回錯誤層級價格的問題。
* **MDVA-37225** (*適用於Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) — 修正匯入的SKU中有整數值時，上傳程式在快速建立訂單期間卡住的問題。
* **MDVA-37224** (*適用於Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) — 修正客戶無法透過 [!DNL PayFlow Pro] 購物車中的其他產品。
* **MDVA-36286** (*適用於Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修正相同SKU在子類別中的位置不同時，頁面產生器產品介面工具集預覽會中斷的問題。
* **MDVA-30186** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) — 修正GraphQL回應中，屬性選項會依選項值排序，而非屬性項目計數的問題。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*適用於Adobe Commerce >=2.3.0 &lt;=2.4.2*) — 修正透過API變更後，舊自訂選項會保留的問題。
* **MDVA-35773** (*適用於Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) — 修正折扣為100%的訂單的發票上「總量」未顯示為零的問題。
* **MDVA-36833** (*適用於Adobe Commerce 2.4.2*) — 修正搜尋結果在將部分產品排除在共用目錄之外後，每頁顯示隨機數量的問題。
* **MDVA-37182** (*適用於Adobe Commerce >=2.4.1 &lt;=2.4.2*) — 修正兩者中收到錯誤搜尋結果的問題 [!DNL Elasticsearch] 第6版和第7版。
* **MDVA-36253** (*適用於Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) — 修正刪除項目後，迷你購物車中顯示錯誤小計的問題。
* **MDVA-36853** (*適用於Adobe Commerce 2.4.2*) — 修正載入大型媒體集時未顯示影像的問題。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修正類別頁面上缺少套件產品的問題。
* **MDVA-36615** (*適用於Adobe Commerce 2.4.2*) — 修正「管理產品」格線中產品計數錯誤的問題。
* **MDVA-36464** (*適用於Adobe Commerce >=2.4.0 &lt;=2.4.2*) — 修正電子郵件通知設定無法在商店檢視層級運作的問題。
* **MDVA-36138** (*適用於Adobe Commerce ^2.3.2*) — 修正未調整運送價格且如果購物車中並非所有項目均符合免費運送購物車規則，則向客戶顯示完整運送價格的問題。
* **MDVA-36424** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — 修正當後端基本URL與店面基本URL不同時，重複編輯內容時，附加至頁面產生器元素的媒體影像消失的問題。
* **MDVA-35984** (*適用於Adobe Commerce ^2.4.0*) — 修正針對相同產品建立多個同時發運後，產品數量和可售數量不正確的問題。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 這可修正GraphQL查詢未透過類別快取標籤進行快取的問題。
* **MDVA-33168** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正透過API更新產品屬性時，所有其他屬性變更為空白值的問題。
* **MDVA-19640** (*適用於Adobe Commerce >=2.3.0*) — 修正 [!DNL Advanced Reporting] 未顯示任何資料。
* **MDVA-11189** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正匯入CSV檔案以更新產品庫存後， `cataloginventory_stock` 表格。
* **MDVA-26639** (*適用於Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) — 修正建立新訂單確認電子郵件範本時，訂單郵件中缺少訂單項目的問題。
* **MDVA-15546** (*適用於Adobe Commerce >=2.3.0*) — 修正建立訂單後， *列entity_id其中子句不明確* 異常日誌中顯示錯誤。
* **MDVA-21095** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正查詢時的問題 `INSERT INTO search_tmp` 不會在大量屬性值更新後結束。
* **MDVA-23845** (*適用於Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修正啟用JavaScript縮制後無法預覽電子郵件範本的問題。
* **MDVA-22026** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正從CSV檔案匯入產品（包括來自外部URL的影像）失敗的問題。
* **MDVA-22383** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正儲存產品需花很長時間且分頁的問題。
* **MC-41359** (*適用於Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) — 修正錯誤的SameSite Cookie參數設定的問題。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*適用於Adobe Commerce 2.4.1*) — 修正頁面產生器擲回下列錯誤的問題： *啟動頁面產生器時發生錯誤。 請洽詢您的技術支援聯絡人。*
* **MDVA-35356** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正部分開票訂單取消後，商店信用退貨不正確的問題。
* **MDVA-33289** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修正結帳期間，原始JavaScript程式碼顯示在帳單地址UI(若 [!DNL Google Tag Manager] 啟用。
* **MDVA-35982** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正管理員使用者限制至特定網站時，無法為相同網站上的訂單建立裝運的問題。
* **MDVA-35155** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正選項標題變更時無法購買套件組合產品的問題。
* **MDVA-35910** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正停用「以客戶身分登入」功能後無法建立新客戶帳戶的問題。
* **MDVA-34474** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正使用API將產品新增至申請清單的問題。
* **MDVA-34591** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正的購物車規則折扣計算不正確的問題 *最大數量折扣適用於* 和 *折扣數量步驟（購買X）*.
* **MDVA-33704** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修正 *在商店取貨* 未顯示運送選項，但已設定為可用。
* **MDVA-34928** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修正從付款中移除商店評分後，頁面載入器無限期顯示的問題。
* **MDVA-35254** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正結帳期間驗證碼的問題。
* **MDVA-35569** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正 *固定產品稅* 指定狀態時，欄位不會填入GraphQL回應中。
* **MDVA-35847** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正B2B問題，若使用自訂客戶屬性，公司使用者表單會中斷。
* **MDVA-31307** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正 *記憶體不足* 因為快取區塊的動態CSP白名單有問題，導致某些類別發生錯誤。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正錯誤 *進行中* 消息狀態為正確 *complete* 消費者訊息 `quoteItemCleaner` 刪除數個產品後。
* **MDVA-34102** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正「產品格線」和「編輯產品」頁面上「管理」區域中，已停用產品的「預設庫存」數量為零。
* **MDVA-35286** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正客戶在購物車中已套裝產品，並從「多個位址」結帳切換為「單頁」結帳時發生錯誤的問題。
* **MDVA-35312** (*適用於Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) — 修正空的GraphQL請求時的回應代碼500。
* **MDVA-34189** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修正上503的第一個位元組逾時 [!DNL Visual Merchandiser] 查詢。
* **MDVA-34695** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正負面 `children_count` 刪除類別之後。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正 *使用預設值* 套用排程變更後，核取方塊會被清除。 排程的變更不再有效時，就會顯示問題。
* **MDVA-35064** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修正不會針對透過API建立的可設定產品產生URL重新寫入的問題。
* **MDVA-34943** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正快速訂購快取先前輸入之SKU的問題。
* **MDVA-35197** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.0*) — 修正先前新增的產品無存貨時，使用GraphQL新增至購物車時發生錯誤的問題。
* **MDVA-34850** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.0*) — 修正可設定產品的無庫存選項未顯示，而非顯示為點進的問題。
* **MDVA-34867** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正排程更新的條件欄位集值未儲存的問題。
* **MDVA-35092** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修正使用者無法新增的問題 [!DNL Vimeo] 視訊已過時 [!DNL Vimeo] API。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*適用於Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修正當相符的產品每個網站的價格不同時，頁面產生器產品內容類型預覽中斷的問題。
* **MDVA-32634** (*適用於Adobe Commerce ^2.3.1*) — 修正 `url_path` 在階層中移動類別後，指派給所有存放區的類別仍維持不變。
* **MDVA-33344** (*適用於Adobe Commerce ^2.3.0*) — 修正硬式編碼的問題 `rma_item` 使用實體預設屬性集ID，而非資料庫中的值。
* **MDVA-34192** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修正無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。
* **MDVA-34847** (*適用於Adobe Commerce ^2.3.0*) — 針對具有自訂權限的管理員使用者，在管理員集合中針對SQL條件，修正儲存ID類型轉換為整數的問題。
* **MDVA-34886** (*適用於Adobe Commerce ^2.3.2*) — 修正搜尋若 *權重* 產品屬性設為可搜尋。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正 [!DNL PayPal Payflow Pro] 付款失敗，出現重新導向參數清單格式錯誤。
* **MDVA-34023** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正錯誤 *沒有具有addressId的實體* 在訪客的瀏覽器上隨機顯示。
* **MDVA-32759** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3，含B2B擴充功能*) — 修正共用目錄刪除現有層級定價的問題。
* **MDVA-33482** (*適用於Adobe Commerce ^2.3.5*) — 修正針對部分發票生成貸項通知單導致對總訂單徵稅，而非對該部分發票徵稅的問題。
* **MDVA-33393** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正錯誤 *提供的countryId不存在*.
* **MDVA-33632** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.7*) — 提供例外訊息所在的修正 *此產品無存貨* 現在會在嘗試重新訂購無庫存產品時顯示給管理員使用者。
* **MDVA-34469** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.2*) — 修正使用多個商店檢視時，客戶購物車上的GraphQL突變失敗的問題。
* **MDVA-33976** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修正從套件產品中移除第二個選項後，店面上的套件產品顯示無存貨的問題。
* **MDVA-33894** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1，含B2B擴充功能*) — 修正快速訂購功能的多個問題，包括新增和移除多個產品及SKU區分大小寫。
* **MDVA-27664** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正客戶註冊表單中造成顯示錯誤的問題： *錯誤 — 出生日期不應大於今天。*
* **MDVA-33970** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正當價格屬性的範圍設為網站時，貸項通知單中出現錯誤貨幣符號的問題。
* **MDVA-33992** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正結帳期間B2B特殊定價顯示不正確的問題。
* **MDVA-34100** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2搭配B2B擴充功能*) — 修正無法從公司結構頁面建立公司帳戶的問題。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) — 修正從CSV檔案匯入產品後，影像重複的問題。
* **MDVA-33382** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正從類別移除產品後，索引器失效的問題。
* **MDVA-28511** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修正無法完成的問題 [!DNL PayPal] 如果「名稱」欄位包含某些字元（如帶重音的大寫字母），則結帳。
* **MDVA-31519** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修正使用全網站銷售規則時，訪客結帳的等待逾時問題。
* **MDVA-33281** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正 `inventory:reservation:list-inconsistencies` 因為SKU參數類型錯誤。
* **MDVA-24201** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正價格在手動重新編列索引之前，無法反映已排程購物車價格規則的問題。
* **MDVA-32694** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修正管理員使用者無法將產品新增至可轉讓報價（如果產品與非預設商店相關）的問題。
* **MDVA-33516** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正編輯申請清單中的套件組合產品會導致錯誤的問題。
* **MDVA-33975** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正GraphQL請求中與價格計算相關的多個問題。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正 [!DNL PayPal] 未在下面提供結算報告 **報表** > **銷售** > **[!DNL PayPal]** 如預期般解決。
* **MCP-87** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.2*) — 改善大型設定檔的類別產品和庫存索引器的索引時間。
* **MDVA-33106** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正重新排程的產品變更在cron後遭清除的問題 `run` 命令。
* **MDVA-19391** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正 `analytics_collect_data` 會擲回錯誤，因為 `catalog_category_entity_text` 表格。
* **MDVA-20376** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正 *沒有具有customerId = 1的實體* 錯誤 `exception.log` 訂購後登入的客戶。
* **MDVA-23764** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正 `JsFooterPlugin.php` 會影響動態區塊的顯示。
* **MDVA-13203** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正 *完整性約束違規search_tmp_表* 完全重新索引後出現錯誤。
* **MDVA-23426** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5*) — 修正Adobe Commerce傳送的通知電子郵件內含空白內文，內容新增為附件的問題。
* **MDVA-22150** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.4*) — 修正客戶若在「管理員」中停用可設定產品，而購物車中具有可設定產品且已套用抵用券時無法登入的問題。
* **MDVA-32545** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正從管理員建立訂單時，發票未自動送出的問題。
* **MDVA-32714** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.1*) — 修正GraphQL產品查詢中客戶群組價格無法運作的問題。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*適用於Adobe Commerce >=2.3.2 &lt;2.4.2*) — 新增 *小計(包括 稅)* 為規則條件定價的選項。
* **MDVA-31236** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正具有自訂資源存取權的管理員無法設定2FA或登入的問題。
* **MDVA-30845** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.7*) — 修正 *很抱歉，此訂單目前沒有報價* 無法連接到UPS XML/USPS/DHL時，將顯示錯誤，並且沒有其它運送方法可用。
* **MDVA-32133** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正特定情況下，媒體集館未從頁面產生器載入的問題。
* **MDVA-12304** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 將Cookie數上限從50增加至200。
* **MDVA-32632** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正訂單出現在付款系統，但未出現在Adobe Commerce的問題。
* **MDVA-32449** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2，含B2B擴充功能*) — 修正訂單記錄載入緩慢或完全未載入的問題。
* **MDVA-32739** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正啟用「非同步電子郵件通知」會傳送舊銷售電子郵件的問題。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*適用於Adobe Commerce 2.3.6、2.4.1*) — 修正 *建立帳戶* 更正中的無效資料後，按鈕會保持停用狀態 *建立新客戶帳戶* 表單。
* **MDVA-31006** (*Adobe Commerce 2.3.0、2.3.1*) — 修正下訂單後，使用 [!DNL Paypal Express] 付款。
* **MDVA-25602** (*適用於Adobe Commerce 2.3.0*) — 修正 [!DNL PayPal Payflow Pro] 付款方法將cookie視為 `SameSite=Lax` 依預設，在Chrome 80瀏覽器和API回應中，重新導向至客戶登入頁面。

## v1.0.10 {#v1-0-10}

修補程式版本的微幅修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*適用於Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修正當 *整個購物車的固定金額折扣* 動作。
* **MDVA-30889** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正以虛擬和簡單產品作為選項開票套件後發生錯誤的問題。
* **MDVA-31791** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.5*) — 使用目標規則或連結產品時，改善產品頁面的效能。
* **MDVA-31168** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正產品匯出CSV檔案未顯示，且記憶體分配錯誤的問題。
* **MDVA-32313** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正可設定產品可新增至包含錯誤設定選項之願望清單的問題。
* **MDVA-31759** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正產品未以 *下拉式清單* 和 *textarea* 屬性值。
* **MDVA-32012** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正無法驗證韓國和阿根廷郵遞區號的問題。
* **MDVA-31640** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 修正無法透過REST API更新特殊價格的問題。
* **MDVA-28651** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0（含B2B擴充功能）*) — 修正透過REST API載入可轉讓報價時的效能問題。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1，具有B2B擴充功能*) — 修正「貸項通知單」格線中顯示錯誤貨幣符號的問題。
* **MDVA-31295** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正完成部分訂單並徵稅項目時，不會計算獎勵點數的問題。
* **MDVA-30112** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正訂單數超過 *束團大小* 值，Adobe Commerce會將 *擱置* 狀態不一致。
* **MDVA-31150** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正當發票由Rest API呼叫過帳，而訂單部分由商店信用卡和禮品卡帳戶支付時，GET發票餘額API呼叫未返回商店信用卡和禮品卡餘額的問題。
* **MDVA-30963** (*適用於Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修正產品篩選結果集僅包含指定之值的問題 *所有商店檢視* 範圍中，包含在商店檢視層級上值被覆寫的產品。
* **MDVA-29954** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2，含B2B擴充功能*) — 修正 *新公司註冊請求* 和 *你被連結到公司* 從錯誤的地址發送電子郵件。
* **MDVA-28357** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 針對 [!DNL ElasticSearch] 索引，讓萬用字元搜尋查詢可與包含連字型大小(&quot;-&quot;)的SKU搭配使用。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正自訂訂單狀態變更為 *處理* 使用WebApi建立部分裝運後。
* **MDVA-30428** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修正如果將產品指派給自訂庫存來源，客戶無法將產品新增至願望清單的問題。
* **MDVA-30594** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正設定FPT時，結帳期間無法儲存具有多個位址的訂單的問題。
* **MDVA-29148** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正透過API呼叫(產品自訂屬性， `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如多選）如果有效負載中未提供任何值，則類型不會使用其預設值。
* **MDVA-30837** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.5*) — 新增組態設定 *包括稅額：是/否* （在免運費方法配置中）。 當 *包括稅額* 設為 *是*，最小訂單金額按小計+稅計算。 當 *包括稅額* 設為 *否*，最小訂單金額計算為小計
* **MDVA-25028** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) — 修正使用 [!DNL PayPal Payflow Pro] 觸發欺詐篩選時，未設為「懷疑欺詐」狀態。
* **MDVA-31224** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5*) — 改善 `catalog_product_price` 對捆綁產品重新索引操作。
* **MDVA-31321** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正空白頁面（錯誤）的時機 *全部顯示* 中所有規則的URL。 [!DNL Elasticsearch] 傳回大型產品id清單。 在此情況下， order by子句將轉換為不正確的SQL格式。
* **MDVA-30815** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正當您變更搜尋結果頁面上應顯示多少搜尋結果時，Adobe Commerce會顯示空白頁面的問題。 [!DNL Elasticsearch] 現在，當您變更每頁檢視的搜尋結果數量時，可正確顯示類別頁面的結果。
* **MDVA-30782** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修正無論購物車規則為何，都會顯示動態區塊的問題。
* **MDVA-31021** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正中出現效能問題的問題 `module-catalog-import-export/Model/Import/Product/Option.php`. 如果中有超過10萬筆記錄 `catalog_product_option` 表格中，單一產品的新CSV需少於10秒才能驗證。
* **MDVA-31007** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正自訂位址屬性無法正確顯示在帳戶區域和後端之訂單詳細資料頁面中的問題。
* **MDVA-29389** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正進階報告中， `analytics_collect_data` cronjob表示： *必須在主機參數內配置埠（如localhost:3306）*.
* **MDVA-31343** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正已移除內文類別的問題 `page-layout-category-full-width` 排程類別時。
* **MDVA-30945** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正更新購物車時收到嚴重錯誤訊息的問題 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.0*) — 實作 *最小值應符合* 功能和部分搜索 [!DNL Elasticsearch] 引擎。 解決搜尋查詢中連字型大小的問題。
* **MDVA-30102** (*適用於Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修正Redis快取因配置快取沒有TTL而快速成長的問題。
* **MDVA-30599** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.0*) — 修正使用API建立的訪客引號，錯誤標示為登入客戶的引號的問題。
* **MDVA-29446** (*適用於Adobe Commerce >=2.3.3 &lt;=2.4.0*) — 修正結帳期間，不適用運送方法的價格顯示為零的問題。
* **MDVA-30357** (*適用於Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修正透過cron產生Sitemap時，建立錯誤影像URL的問題。
* **MDVA-30565** (*適用於Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) — 修正 *沒有具有cartid = 0的此類實體* 如果啟用永久性購物車，在storefront結帳時會為訪客客戶顯示錯誤。
* **MDVA-29787** (*適用於Adobe Commerce >=2.3.0 &lt;=2.4.0*) — 修正相關產品的目標規則無法運作(當 *是* 條件用來定義要顯示的產品。
* **MDVA-30977** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) — 修正重新索引後，類別中遺失隨機產品的問題。
* **MDVA-28202** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.2*) — 修正使用MSI時，分層導覽無法正確篩選可設定產品的問題。
* **MDVA-28300** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正GQL要求未反映目錄價格規則價格變更的問題。
* **MDVA-31006** (*適用於Adobe Commerce >=2.3.2 &lt;=2.4.2*) — 修正下訂單後，使用 [!DNL Paypal Express] 付款。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正分層導覽的問題，其中 *否* 若 [!DNL Elasticsearch] 用作搜尋引擎。
* **MDVA-28191** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正透過管理員建立訂單期間未載入任何付款方法的問題。
* **MDVA-29959** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.3-p1，具有B2B擴充功能*) — 修正限制管理員使用者(使用 *公司* 權限無法刪除公司帳戶。
* **MDVA-30265** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正發票建立後，發運追蹤連結停止運作的問題。
* **MDVA-28409** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正 `sales_clean_quotes` cron作業失敗 *記憶體不足* 資料庫中過期引號數量巨大時出錯。
* **MDVA-30593** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正根據「報價期限」設定而過期的報價未清理的問題。
* **MDVA-30107** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正如果商店檢視使用不同的基本URL，商店切換器無法如預期運作的問題。
* **MDVA-28763** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正使用REST API多次更新產品資訊後，產品影像重複的問題。
* **MDVA-30284** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正目錄搜尋索引器因下列原因而失敗的問題 *[!DNL Elasticsearch]錯誤：已超出索引中總欄位的限制。*
* **MDVA-29042** (*適用於Adobe Commerce >=2.3.3 &lt;=2.3.4-p2，具有B2B擴充功能*) — 修正目錄權限變更為 *允許* 將新產品新增至共用目錄後自動執行。
* **MDVA-30428** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正如果將產品指派給自訂庫存來源，客戶無法將產品新增至願望清單的問題。
* **MDVA-28661** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2搭配B2B擴充功能*) — 修正變更公司管理員後，「公司使用者」公司帳戶區段中擲回錯誤的問題。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*Adobe Commerce 2.3.1 - 2.3.4-p2*) — 修正當資料庫名稱太長，導致前端未更新類別時，cron作業失敗的問題。
* **MDVA-30106** (*適用於Adobe Commerce ^2.3.0*) — 修正結帳付款期間未載入的問題 *無法讀取Null的屬性&#39;length&#39;* JS主控台發生錯誤。
* **MDVA-28656** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) — 修正下單時若未提供任何付款資訊（例如，折扣為100%），且已為訂單建立發票，則訂單狀態會變更為 *已關閉* 而非完成。
* **MDVA-30209** (*適用於Adobe Commerce 2.3.0 - 2.3.3-p1*) — 修正客戶更新其帳戶資訊時，客戶群組變更為預設的問題。
* **MDVA-30123** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正GraphQL查詢的屬性選項標籤未正確轉譯的問題。
* **MDVA-29996** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正啟用類別權限後，類別頁面未被完整頁面快取快取的問題。
* **MDVA-30164** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修正如有自訂客戶屬性，無法從「客戶」格線匯出客戶記錄的問題。
* **MDVA-30444** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正使用GraphQL下單時未傳送任何確認電子郵件的問題。
* **MDVA-30490** (*Adobe Commerce 2.3.4 - 2.3.5-p2*) — 修正當其中一項產品有空的簡短說明時，產品比較會擲回500錯誤頁面的問題。
* **MDVA-30232** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.1*) — 修正原始訂單包含禮品卡時無法重新訂購的問題。
* **MDVA-29965** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.0*) — 修正客戶新增產品至購物車時出現「表單金鑰無效」錯誤的問題。
* **MDVA-30008** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正無法透過Admin API針對公開目錄中的產品下單的B2B問題。
* **MDVA-22469** (*Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) — 修正升級至Adobe Commerce 2.3.3後，「頁面產生器」無法在「管理面板」中運作，且部分JS和CSS檔案未載入的問題。
* **MC-35984** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正商家在為退貨授權(RMA)建立出貨標籤後，無法與退貨頁面上任何頁面元素互動的問題。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*適用於Adobe Commerce 2.3.0 - 2.3.4*) — 修正 [!DNL PayPal Payflow Pro] 付款方法將cookie視為 `SameSite=Lax` 依預設，在Chrome 80瀏覽器和API回應中，重新導向至客戶登入頁面。
* **MDVA-26694** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) — 修正產品和目錄快取每日到期的問題，不過排程的過期時間不同。
* **MDVA-27825** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正因記憶體洩漏而匯出大量資料失敗的問題。
* **MDVA-29085** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) — 修正B2B問題，若公司是由API建立，則系統不會傳送任何必要的新公司電子郵件。
* **MDVA-29344** (*適用於Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) — 修正將文字從標題元素複製到文字元素後，頁面產生器卡住的問題。
* **MDVA-29835** (*適用於Adobe Commerce >2.3.1 &lt;2.4.2*) — 修正禮品卡訂單包含兩個代碼而非一個的問題。
* **MDVA-30052** (*適用於Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修正私人內容（本機儲存）未正確填入，而導致效能問題的問題。
* **MDVA-30131** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正分層導覽的問題，其中 *否* 若 [!DNL Elasticsearch] 用作搜尋引擎。
* **MDVA-35514** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正在「建立套件」強制回應視窗中建立發運標籤和新增已訂購產品至套件的問題。
