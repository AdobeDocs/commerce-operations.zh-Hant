---
source-git-commit: 0a22d08d6965c6abc288a1a171d25f4ff8bbd7ce
workflow-type: tm+mt
source-wordcount: '26969'
ht-degree: 0%

---
# Adobe Commerce已修正問題(v2.4.9-beta1)

## 已修正v2.4.9-beta1中的問題

我們已修正Adobe Commerce 2.4.9-beta1核心程式碼中的560個問題。 此版本中包含的已修正問題子集說明如下。

### API

#### 套用SpecialPrice時的特殊價格截止日期驗證錯誤

有關特殊價格的系統運作正常，而產品特殊價格將在管理員或第三方系統透過REST API設定的日期到期

_AC-13130 - [GitHub問題](https://github.com/magento/magento2/issues/39169) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39690)_

#### 透過WebAPI paradox的[WebAPI]客戶電子郵件確認

修正客戶由於在確認前需要權杖的授權悖論而無法透過WebAPI啟用其帳戶的問題。 此更新可讓未確認的客戶透過API成功啟用其帳戶，確保一致且有效的確認流程。

_AC-13281 - [GitHub問題](https://github.com/magento/magento2/issues/39255) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 透過僅包含付款資訊的REST API建立訂單時，管理員儀表板中出現「缺少帳單地址」錯誤

修正透過API建立訂單（沒有帳單地址）時，導致管理員儀表板當機的問題。
現在，沒有帳單地址的訂單受到限制，不再建立。

_AC-14049 - [GitHub問題](https://github.com/magento/magento2/issues/39651) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Rest API中的產品加入購物車問題

修正未指派至特定網站的產品仍可新增至購物車及購買的問題。
現在會顯示錯誤訊息：「您嘗試新增的產品無法使用。」

_AC-15054 - [GitHub問題](https://github.com/magento/magento2/issues/40029) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f5cc09fc)_

#### 更新商店標籤時會覆寫屬性選項標籤

修正透過REST API更新多選產品屬性會覆寫所有store_labels、移除現有商店特定標籤的問題。
現在，當更新預設商店檢視標籤時，Magento會將提供的標籤與現有標籤合併，而非完全覆寫。
這可確保在更新後，其他商店檢視的商店特定標籤將保持不變。

_AC-15208 - [GitHub問題](https://github.com/magento/magento2/issues/40093) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [問題]已釐清屬性選項已經存在的回應

系統現在以更清楚且文法正確的版本「取得新檔案名稱（若已存在）」取代尷尬的片語：「取得新檔案名稱（若已存在）」。 這可改善可讀性和使用者瞭解。
屬性選項回應也相同。

_AC-15473 - [GitHub問題](https://github.com/magento/magento2/issues/39943) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39941)_

#### /V1/products/special-price API端點發生內部伺服器錯誤

修正了對/V1/products/special-price和相關定價API的格式錯誤請求由於Null TypeError而傳回500內部伺服器錯誤的問題。
現在API可正確驗證輸入，並為無效負載傳回400錯誤，改善錯誤處理和API可靠性。

_AC-6419 - [GitHub問題](https://github.com/magento/magento2/issues/35934) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a7ef6300)_

#### `/V1/order/&lbrace;orderId&rbrace;/ship` API端點發生內部伺服器錯誤

系統現在修正`/V1/order/{orderId}/ship` API端點中的內部伺服器錯誤，並傳回400錯誤，因為要求的格式不正確。

_AC-6420 - [GitHub問題](https://github.com/magento/magento2/issues/35931) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38282)_

#### /V1/creditmemo API端點發生內部伺服器錯誤

修正對/V1/creditmemo API的格式錯誤請求傳回500內部伺服器錯誤的問題。
現在，API已正確驗證要求，並為無效負載傳回400錯誤，改善錯誤處理和穩定性。

_AC-6422 - [GitHub問題](https://github.com/magento/magento2/issues/35924) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a7ef6300)_

#### 建立新屬性時，Rest API和Magento後端會對attribute_code使用不同的驗證方法

修正Magento管理員允許在attribute_code中使用大寫字母，但REST API在建立產品屬性期間拒絕使用的不一致問題。
現在，Admin和REST API都遵循相同的驗證，以便成功建立具有大寫字母的屬性。

_AC-6660 - [GitHub問題](https://github.com/magento/magento2/issues/33138) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

#### 透過REST API在屬性建立和更新之間執行不同驗證

修正透過REST API建立屬性期間驗證不一致導致指派不正確backend_type的問題。
現在，系統會在有效時設定正確的後端型別、擲回無效值的例外狀況，如果未提供，則會適當地回覆，以確保一致的屬性行為。

_AC-6885 - [GitHub問題](https://github.com/magento/magento2/issues/36327) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64823f95)_

#### 格式錯誤的請求本文或引數會造成「內部伺服器錯誤」

格式錯誤的請求本文或引數現在會傳回清楚的「400錯誤請求」回應。
先前，將格式錯誤的請求內文或引數傳送至各種REST API端點（例如/V1/carts/search、/V1/orders、/V1/products等），會導致一般的「內部伺服器錯誤」(500)，導致難以診斷輸入問題。
現在，Adobe Commerce傳回「400個錯誤請求」回應，當請求無效時，可提供更清楚的回饋。

_AC-746 - [GitHub問題](https://github.com/magento/magento2/issues/32784) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders`（或`/orders/:id`）端點遺失「state」和「status」欄位

修正當資料庫值為Null時，`/orders`和`/orders/{id}` API回應省略狀態列位的問題。
現在，回應中會一致傳回這兩個欄位，確保符合API檔案，並提升資料可靠性。

_AC-9244 - [GitHub問題](https://github.com/magento/magento2/issues/37807) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/01cee3c3)_

#### 非同步大量作業對async.magento.configurableproduct.api.optionrepositoryinterface.save.post維持開啟狀態

如果要求內文不是Array，大量API端點現在會擲回錯誤，因此需要大量專案索引鍵是從0開始的連續數字。 以前，由於批次請求中提交的任意專案鍵，未更新批次專案狀態。

_ACP2E-3544 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_

#### is_subscribed值上的[雲端] API REST錯誤未考慮來自使用searchCriteria的目前存放區

API REST客戶查詢使用searchCriteria從正確的存放區擷取正確的「is_subscripted」值
先前，API REST客戶查詢在擷取is_subscribed&quot;值時不會考慮儲存。

_ACP2E-3621 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all可以為1個SKU建立多個專案

儲存和更新相同產品的同時請求現在會序列化，以防止可能導致資料不一致或重複產品的競爭條件

_ACP2E-3744 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

#### 訂單「base_row_total」和「row_total」會在REST API回應中顯示單一料號價格

訂購詳細資料的REST API回應現在包含「base_row_total」和「row_total」屬性的正確值，以備有多個相同專案訂購時使用

_ACP2E-3874 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

#### REST API端點export-stock-salable-qty傳回不正確的專案total_count

修正存貨匯出庫存可銷售數量API中total_count不正確限製為頁面大小的分頁問題。 先前，當使用/rest/all/V1/inventory/export-stock-salable-qty/website/base端點搭配page_size=5之類的分頁引數時，回應中的total_count欄位會傳回5，而非符合搜尋條件的實際產品總數。 進行此修正後， total_count欄位現在會正確反映可用的產品總數（不論page_size引數為何），確保所有的Magento REST API端點具有一致的分頁行為。

_ACP2E-4086 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5632fb5e)_

#### 購物車專案REST API中的自訂選項ID出現驗證問題。

REST API V1/guest-carts/&lt;cartId>/items/和V1/carts/mine/items/現在驗證「product_options.extension_attributes.custom_options」。*.option_id」以確保其參考購物車專案SKU的有效option_id。 之前，系統會在未經驗證的情況下處理此引數，並將其儲存在資料庫中。

_ACP2E-4138 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 從購物車擷取產品並變更商店標題語言時不會變更

GraphQL customerCart查詢現在會根據商店標題值傳回產品屬性值。 先前，透過GraphQL從購物車擷取產品時變更商店頁首語言並未反映更新後的語言，導致本地化不一致。

_ACP2E-4227 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6e134409)_

#### 禮卡產品的REST API /media端點失敗 — 傳回「無法儲存產品」

在修正之前，您可以建立不在全球範圍中包含金額的禮卡產品。 透過此修正，已新增檢查全域範圍中金額的驗證。

_ACP2E-4395 - [GitHub問題](https://mcstaging.panini.it/shp_ita_it/)_

### API、購物車和結帳

#### 針對送貨資訊，伺服器端驗證無法使用REST API運作

修正REST API中，運送地址資訊驗證不符合管理員後端所定義屬性設定的問題。 驗證現在會正確遵循設定的設定。

_ACP2E-4156 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45cbf9b6)_

### API，目錄

#### 刪除預設網站/商店折扣價格API端點

先前，刪除預設基本網站並使用次要網站作為預設網站時，會導致嘗試更新次要網站的層級價格時發生錯誤。 不過，套用此修正後，即使刪除或停用基本網站，層級價格仍可成功更新。

_ACP2E-4334 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a3b7032)_

### API、框架

#### 應用程式伺服器上的RedisRequestLogger\RedisClient （速率限制器）例外狀況

修正後，在安裝PHP Redis擴充功能的情況下，可搭配GraphQL應用程式伺服器使用速率限制功能。

_ACP2E-4237 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e885088b)_

### API，匯入/匯出

#### 非同步商業發票退款API會建立離線退款，而非線上退款

修正非同步退款作業，其中具有`is_online`引數的退款請求未正確處理。

_ACP2E-4394 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

### API、順序

#### [雲端]訂單000075568料列總計外觀的訂單資訊問題

修正當專案完全折扣時，訂單API回應中的row_total_incl_tax值會以接近零的殘值傳回，而非0.00的問題。

_ACP2E-3950 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

### 帳戶

#### [問題]修正目錄Widget範本選項中的錯字

系統現在會修正目錄Widget範本選項中的錯字。

_AC-11576 - [GitHub問題](https://github.com/magento/magento2/issues/38185) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38178)_

#### [問題]已移除後端格線上不必要的間距

系統現在會移除後端格點中不必要的間距。當有選取的專案時

_AC-11579 - [GitHub問題](https://github.com/magento/magento2/issues/38502) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32622)_

#### 使用多位元組字元時，儲存的客戶群組代碼與輸入不符

修正使用多位元組字元的客戶群組代碼遭截斷，且不符合輸入值的問題。 更新可確保完整輸入內容正確儲存，進而精確建立具有多位元組名稱的客戶群組。

_AC-13335 - [GitHub問題](https://github.com/magento/magento2/issues/39342) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a06a4a57)_

#### 在具有o和.swiss網域的Admin Panel中更新客戶電子郵件時出現問題

Admin Panel現在接受具有特殊字元和.swiss網域的客戶電子郵件。
之前，將客戶電子郵件更新至max@mostermann.swiss之類的地址時失敗，並出現有關無效主機名稱和TLD的錯誤。
AC-13409

_AC-13409 - [GitHub問題](https://github.com/magento/magento2/issues/39394) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d3ea191d)_

#### Newsletter訂閱啟用的切換器無法依網站/商店運作

當我們在全域層級停用多個網站/商店評論時，系統可正確處理電子報訂閱

_AC-14283 - [GitHub問題](https://github.com/magento/magento2/issues/39751) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39752)_

#### 棄用「已檢視產品」客戶區段條件

「已檢視產品」客戶區段條件現在已過時。
以前，使用此條件可能會由於MySQL查詢量大而導致網站中斷。 條件現在標籤為已棄用且不受支援。

_AC-14542_

#### [問題]已移除電子郵件洩漏

現在，系統顯示「如果不需要輸入電子郵件來確認帳戶，則顯示錯誤訊息，指出不正確的電子郵件，無論客戶是否存在。

_AC-14561 - [GitHub問題](https://github.com/magento/magento2/issues/39574) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39570)_

#### 無法透過`updateProductsInWishlist` GraphQL突變清除願望清單專案註解

修正未透過GraphQL變動更新願望清單註解的問題。
現在，註解會正確更新，並反映在API回應和店面中。

_AC-14682 - [GitHub問題](https://github.com/magento/magento2/issues/39911) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 在行動裝置上移除的產品仍會出現在網頁的迷你比較區段，直到重新登入為止

系統現在會移除產品，而產品會立即從行動裝置和網頁上的所有比較檢視中消失，包括迷你比較區段。

_AC-14703 - [GitHub問題](https://github.com/magento/magento2/issues/39905) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40023)_

#### 當設為「否」時，忽略顯示首碼/尾碼設定

修正即使在設定中停用時，客戶名稱首碼/尾碼仍繼續在訂單中顯示的問題。
現在，系統會根據組態設定，從訂單詳細資料中移除字首/字尾值。

_AC-15074 - [GitHub問題](https://github.com/magento/magento2/issues/40036) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront客戶帳戶註冊：電子郵件地址格式已轉換為不同的網域格式

此錯誤解決網域中包含特殊字元(例如tec55241@adòbe.com)的客戶電子郵件自動轉換為副檔名格式(tec55241@xn--adbe-mqa.com)的問題。
在Magento 2.4.9-alpha3中，此修正會確保這類電子郵件ID維持不變且有效，以避免傳送錯誤。

_AC-15177 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### 登錄檔單上缺少驗證訊息(mage-error)

修正客戶帳戶建立頁面上的必填欄位留空時未顯示驗證訊息的問題。
現在，所有空白或不正確的欄位會顯示適當的錯誤訊息。

_AC-15185 - [GitHub問題](https://github.com/magento/magento2/issues/40076) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 訂單取消模式標題缺少翻譯

系統現在會修正店面訂單取消模式中缺少的翻譯。 當客戶按一下「我的帳戶>我的訂單」頁面中的「取消」按鈕時，會出現強制回應視窗，詢問取消原因。 不過，強制回應視窗標題先前是硬式編碼且無法翻譯。 此變更可確保模型標題使用正確的翻譯方法。

_AC-15260 - [GitHub問題](https://github.com/magento/magento2/issues/40098) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40100)_

#### 登入magento 2.4.8-p1後的問題

修正Magento 2.4.8-p1登入後首頁上仍顯示「建立帳戶」連結的問題。
現在，與其他頁面一樣，連結在登入後會正確隱藏。

_AC-15292 - [GitHub問題](https://github.com/magento/magento2/issues/40120)_

#### 刪除客戶之前的[問題] Set isSecureArea

系統現在正常運作，此PR會將isSecureArea設為刪除程式，客戶可再次成功註冊。

_AC-15723 - [GitHub問題](https://github.com/magento/magento2/issues/40211) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38462)_

#### 建立客戶帳戶期間，發生目前區域錯誤，因此禁止執行[雲端]刪除操作

修正儲存地址無效的客戶後，會傳回描述無效原因的訊息，而非無關的「目前區域禁止刪除操作」。

_ACP2E-3791 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6ea61121)_

#### 已停用&#39;eav&#39;快取時，[B2B]已登入客戶的Webapi要求會進入無限回圈

修正後，停用EAV快取並不會在某些REST要求期間導致無限回圈。

_ACP2E-4191 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 載入某些地區設定時發生錯誤

修正使用阿拉伯地區設定及「出生日期」屬性設為顯示在店面時，建立客戶帳戶失敗的問題。 現在可以在此設定中成功建立帳戶。

_ACP2E-4311 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2687b487)_

#### 錯誤更新帳戶資訊時的日期無效

客戶現在可以使用阿拉伯地區設定成功更新其帳戶。 先前，由於日期錯誤導致出生日期無效，因此嘗試儲存帳戶資訊失敗。

_ACP2E-4344 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

#### 傳送邀請功能期間的警告訊息

修正當「允許客戶新增自訂訊息至邀請電子郵件」設定停用時，在「傳送邀請」頁面上新增電子郵件欄位時，未顯示「允許的最大X個電子郵件地址」警告訊息的問題。
以前，警告僅在啟用自訂訊息時出現，這會產生不一致的使用者體驗。 現在，無論自訂訊息組態設定為何，都會一致顯示電子郵件上限警告。

_ACP2E-4374_

### 帳戶，管理員UI

#### [Cloud]沒有cartId的實體

解決在同一工作階段中，以客戶的身分使用兩個公司管理員帳戶登入，會造成「沒有包含cartId的這類實體」錯誤的問題。

_ACP2E-4137 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e885088b)_

#### 客戶建立表單錯誤訊息未轉譯

修正客戶驗證錯誤訊息未正確翻譯及格式化的不同介面問題。 驗證錯誤現在會在應用程式的所有區域中顯示正確翻譯的訊息：storefront、adminhtml、rest api和graphql。

_ACP2E-4354 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

### 管理員UI

#### 類別產品格線>狀態和可見度欄在依名稱排序時是空的

修正依產品名稱排序時，類別產品格線中的「狀態」和「可見性」欄顯示為空白的問題。
格線現在會在排序後正確顯示所有欄資料，確保管理面板中的產品資訊準確無誤。

_AC-10659 - [GitHub問題](https://github.com/magento/magento2/issues/38233) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3cf1a106)_

#### 電子郵件範本存放區切換器

修正由於已棄用jQuery程式碼，在點選時，電子報電子郵件範本預覽中的商店切換器未開啟的問題。 更新載入事件可恢復正常功能，讓使用者如預期存取存放區切換器。

_AC-12334 - [GitHub問題](https://github.com/magento/magento2/issues/38892) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

#### 對於簡單產品的相同設定，購物車頁面和產品頁面中的FPT值不同

對於簡單產品，購物車和產品頁面之間的FPT值現在是一致的。
以前，即使套用了相同的設定，購物車和產品頁面之間的固定產品稅(FPT)值小數位數也有可能不同。
AC-13066

_AC-13066 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8953613e)_

#### 色票模組停用時，無法儲存多選/選取屬性選項

現在當色票模組停用時，可以儲存多選/選取屬性選項。
先前，停用「色票」模組會在建立新的多選/選取屬性選項時造成例外狀況。
AC-13071

_AC-13071 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8953613e)_

#### 對於動態產品的相同設定，購物車頁面和產品頁面中的FPT值不同

現在，動態產品的購物車和產品頁面之間的FPT值是一致的。
先前，對於相同設定，FPT （固定產品稅）值在購物車和產品頁面之間的小數位數可能會有所不同。
AC-13075

_AC-13075 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8953613e)_

#### 日期ui元件中未遵循日期格式

解決日期UI元件忽略已設定的格式並顯示不正確值的問題。 此修正可確保日期欄位現在遵循指定的格式（例如Y-m-d）來顯示和輸入。

_AC-13174 - [GitHub問題](https://github.com/magento/magento2/issues/39218) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/913bf1a6)_

#### 沒有可用來刪除來源的選項

在管理UI中新增了庫存來源的刪除選項，可讓管理員移除額外的來源，而非僅啟用或停用它們。 此增強功能透過提供對未使用來源的更佳控制來改善存貨管理。

_AC-13354 - [GitHub問題](https://github.com/magento/magento2/issues/32362) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### 管理中的類別樹狀結構未展開以顯示層級3中所有選取的巢狀類別

修正管理員類別樹狀結構未展開以顯示選取巢狀類別超過第3層的問題。 修復後，所有選取的類別都會自動展開，以改善類別相關條件的可見度和可用性。

_AC-13363 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/913bf1a6)_

#### [問題]改善角色樹狀結構的使用者體驗

此提取請求會新增按鈕，以收合全部、展開全部和展開具有選定專案的分支。 此功能類似於類別樹狀結構（「目錄 — >詳細目錄 — >類別」）中提供的功能

_AC-14020 - [GitHub問題](https://github.com/magento/magento2/issues/39654) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36511)_

#### 匯入/匯出動作記錄檔不會建立在系統>動作記錄>報表格線中

已實作匯入/匯出管理動作的記錄，因此現在會顯示在「系統>動作記錄>報表」中。 這可以記錄先前遺漏的匯入活動，以確保更好的稽核追蹤。

_AC-14266 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException： 「Sender」標頭必須是「Symfony\Component\Mime\Header\MailboxHeader」的例項(取得「Symfony\Component\Mime\Header\MailboxListHeader」)

現在當為SMTP設定自訂傳迴路徑位址時，Adobe Commerce會成功傳送註冊電子郵件。 先前，在system/smtp/set_return_path設為2、system/smtp/return_path_email設為自訂地址的vanilla Adobe Commerce 2.4.8上，客戶註冊已完成但未傳送註冊電子郵件，而Adobe Commerce記錄此錯誤：Symfony\Component\Mime\Exception\LogicException：「Sender」標頭必須是「Symfony\Component\Mime\Header\MailboxHeader」的例項(取得「Symfony\Component\Mime\Header\MailboxListHeader」)。

_AC-14520 - [GitHub問題](https://github.com/magento/magento2/issues/39823) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1e14bd72) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1514117f)_

#### 重新整理訂單未取得最新的自訂屬性資料

修正重新整理訂單頁面未顯示最新客戶自訂屬性資料的問題；修正後，現在會反映更新的屬性值，而無需取消並重新建立訂單。

_AC-14690 - [GitHub問題](https://github.com/magento/magento2/issues/30301)_

#### [問題]取代已棄用的逸出程式

移除已過時的getEscaper()，並透過建構函式插入將其新增。

_AC-15132 - [GitHub問題](https://github.com/magento/magento2/issues/40062) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38135)_

#### 歡迎訊息在行動檢視中重疊產品類別

修正使用者介面問題，此問題導致歡迎名稱與行動檢視中的產品類別重疊、阻礙點按。
現在，類別完全可見且可點按，沒有重疊問題。

_AC-15166 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Ui表單重設按鈕未按預期運作

按一下「重設」按鈕時，系統現在可以正常運作，而不需重新載入整個頁面，表單資料將會重設。

_AC-15204 - [GitHub問題](https://github.com/magento/magento2/issues/40092) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40094)_

#### [問題] PageCache/AccessList：加入CIDR支援

系統現在接受網路內的清除請求，比較容易只提供CIDR範圍。

_AC-15804 - [GitHub問題](https://github.com/magento/magento2/issues/39953) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37809)_

#### [問題]新增說明標題至快取管理按鈕

現在當您移動游標時，系統會新增說明標題至快取管理按鈕

_AC-16212 - [GitHub問題](https://github.com/magento/magento2/issues/38607) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38598)_

#### 提供使用網格來大量刪除稅率的功能

管理員使用者現在可以同時從「管理員稅率」網格中刪除多個稅率。  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub問題](https://github.com/magento/magento2/issues/33399) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33484) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/5cd64dd0)_

#### 在管理員中，浮動顏色未套用至靜態格點

「管理」靜態格點的列現在會依預期套用游標停留顏色。[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub問題](https://github.com/magento/magento2/issues/35358) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/35384)_

#### Google reCAPTCHA管理面板的exception.log中的「無法解析reCAPTCHA引數」專案

已解決Google V3 reCAPTCHA管理員登入之`var/log/exception.log`檔案中的reCaptcha錯誤，且未記錄任何錯誤訊息。 以前，當管理員使用者設定其&#x200B;**設定** > **安全性** > **Google reCAPTCHA管理員面板**&#x200B;設定時，每隔幾秒就會擲回下列錯誤： `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`。  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub問題](https://github.com/magento/magento2/issues/34975) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub程式碼貢獻](https://github.com/magento/security-package/commit/804dbc2a)_

#### 條件SKU的購物車價格規則不會考慮SKU中的「前導零」(sku： 01234與1234相同)

系統現在會正確處理購物車價格規則，且條件SKU會考慮SKU中的「前導零」

_AC-9428 - [GitHub問題](https://github.com/magento/magento2/issues/37919) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39525)_

#### 多選專案的預設屬性選項值行為問題

在修正預設值之前，多個選項屬性的預設值未正確儲存。 現在，修正之後，值會正確儲存在資料庫中。

_ACP2E-3523 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_

#### 後端管理選單字幕未顯示

主功能表群組的所有標題現在都會正確顯示。 以前，如果主選單的第二或第三欄只包含一組連結，則不會顯示該群組的標題。

_ACP2E-3540_

#### 從管理員將產品數量移回購物車時出現問題

從管理員建立訂單時，側邊欄上客戶購物車中的產品新增到訂單時不會消失。

_ACP2E-3563 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### 受限制的管理員使用者無法大量更新產品狀態

自訂管理員可以大量更新產品狀態，因為它是網站層級的屬性。 只有在受限制的管理員也有權存取的網站上才會更新狀態。

_ACP2E-3772_

#### [Staging2]已儲存的卡片在管理面板上不可見

修正升級後，「預存卡」付款選項不再出現在後端訂購表單的問題。

_ACP2E-3830 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

#### 受限的管理員使用者可以儲存/更新預設設定，儘管擁有商店特定的許可權

修正受限管理員使用者能夠檢視並嘗試更新「預設設定」範圍（儘管僅指派給特定網站範圍）的問題，這可能會導致混淆。

_ACP2E-4011 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 針對任何商店檢視範圍，將可設定的產品價格儲存在DB下，這會導致「類別中的產品」排序功能發生問題，其中儲存的價格與前端沒有關聯

已移除可設定產品的「使用預設值」核取方塊（當已設定每個網站的價格，且在管理員UI的可設定產品編輯頁面上已選取商店檢視時）。

_ACP2E-4036 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]管理員密碼原則不符合PCI DSS 4.0規範（至少12個字元）

管理員現在可以透過「商店>設定>進階>管理員>安全性」，設定管理員使用者的最低密碼長度要求。 此增強功能提供更大的安全性彈性，同時維持現有的密碼原則。 驗證會在管理員使用者建立/修改和設定儲存期間強制執行，並即時前端驗證以改善使用者體驗。

_ACP2E-4044 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47721be6)_

#### 管理介面語言為日文時的日期篩選器問題

生日篩選器和欄將使用統一格式M/d/y，與「客戶加入時間」篩選/欄相同

_ACP2E-4052 - [GitHub問題](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### 出現在Admin Grid標頭兩側的白色區塊

修正管理網格中的視覺對齊問題。 先前，在管理面板中水準捲動產品格線時，白色區塊會在格線標頭的左右兩側顯示為未對齊。 現在捲動時，網格標頭元素會維持正確的垂直對齊方式，為管理員管理大型產品目錄提供更簡潔的視覺體驗。

_ACP2E-4104 - [GitHub問題](https://mcprod.pap-store.acer.com/index.html)_

#### Ui元件檔案在2.4.8-p1/ 2.4-develop上無法正常運作

改善自訂UI元件的檔案上傳，透過多重選取可允許在上傳區域點選上傳。

_ACP2E-4162 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ee918f0d)_

#### [在Prem]新建立的訂單/公司/客戶在選取程式期間自動包含在「全部選取」範圍內

修正了在執行整批動作時，手動選取過時管理格線頁面上的所有記錄時，會無意中刪除所有記錄的問題。 以前，當選取的專案數符合總計數時，格線會在內部自動切換到「選取全部」模式，導致大量動作影響所有記錄，而不僅僅是明確選取的記錄。

_ACP2E-4202 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6e134409)_

#### ACP2E-3362的解決方案在MariaDB 10.6上運作緩慢

改善大量歷史搜尋請求時前端搜尋頁面的效能。

_ACP2E-4225 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ab891304)_

#### 日期篩選器無法根據銷退折讓單網格上的存放區時區運作

在依日期屬性修正篩選清單之前，由於選取的日期與儲存的日期之間的時區差異，導致遺漏專案現在，在修正日期篩選套用後。

_ACP2E-4239 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 安裝pagebuilder時，檔案上傳程式對話方塊會開啟兩次

在修復自訂元件之前上傳按鈕會觸發兩次。 修正後，上傳按鈕如預期運作。

_ACP2E-4241 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### 變更客戶資料時，已刪除的客戶屬性發生驗證錯誤。

修正前，如果客戶和客戶地址包含多個已刪除的屬性選項，儲存它們會失敗。 修正後，即使仍然存在多個屬性選項，仍可成功儲存兩者。

_ACP2E-4281 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 產品影像變更未記錄於動作記錄檔

修正管理動作記錄檔中未追蹤產品影像上傳和刪除的問題。 以前，當管理員將新影像新增到產品或從產品的媒體收藏館刪除現有影像時，這些變更不會記錄在記錄系統中。 僅記錄影像角色的變更（例如將影像指派為主要產品影像、縮圖或小影像）。 現在，所有媒體集變更（包括影像新增和刪除）都已正確記錄在管理員動作記錄檔中，為產品影像管理活動提供完整的稽核軌跡可見性。

_ACP2E-4302_

#### 管理員儀表板中的JS警告：「預期會啟動載入器，但在DOM中找不到載入器」

修正為管理控制面板啟用圖表時，瀏覽器主控台中顯示的JavaScript警告。 先前，在啟用圖表的情況下存取管理員儀表板時，過時的偵錯檢查會錯誤地警告「預期會啟動載入器，但在dom中找不到載入器」，即使功能正常運作。

_ACP2E-4336 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2687b487)_

#### 使用預設簽入存放區設定時，具有相依性設定的[雲端]設定可編輯

修正頁面載入後，儘管勾選「使用預設/網站」，「系統設定」欄位仍可能啟用的問題。

_ACP2E-4337 - [GitHub問題](https://mcstaging.pap-store.acer.com) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

#### 管理員儀表板順序圖表以動畫呈現最終大小

現在會立即顯示管理員儀表板順序圖表，不需要重新調整動畫大小。

_ACP2E-4398 - [GitHub問題](https://github.com/magento/magento2/issues/38860) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 頁面產生器無法儲存行動檢視中的內容，因為JS錯誤（TypeError：無法讀取未定義的屬性）

修正在行動檢視中新增橫幅時，頁面產生器無法儲存頁面的問題。

_ACP2E-4399 - [GitHub問題](https://github.com/magento/magento2/issues/38565) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### 管理員UI、B2B

#### B2B以客戶標題登入仍具有Magento品牌

較早的店面標題顯示「您現在在&lt;商店名稱>上以&lt;客戶名稱>連線」與Magento品牌。 此問題現已修正，且標題會顯示為ADOBE品牌。

_AC-14361 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fadcfa8b)_

### 管理UI，目錄

#### 目錄規則作用中且啟用即時模式時，產品儲存失敗

修正了目錄規則索引在產品儲存作業期間，透過將目錄規則索引與產品交易分離而可能因DDL交易錯誤而失敗的問題。

_ACP2E-4378 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 管理UI，內容

#### 插入影像期間發生例外狀況「無法為媒體資產路徑建立轉譯」

移除「媒體集影像最佳化」設定的「最大寬度」和「最大高度」值時，影像最佳化程式期間不會再發生錯誤。

_ACP2E-3781 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

### 管理員UI，訂購

#### 管理訂單建立：新增20多種產品時工作階段大小溢位（工作階段大小超過256KB限制）

解決在建立管理員訂單期間工作階段大小溢位的問題，方法是防止將大量HTML回應儲存在JSON請求的工作階段中，以確保大量產品新增能夠順利運作，而不會登出管理員。

_AC-15893_

### 管理員UI、安全性

#### 弱密碼管理

使用相同密碼時無法儲存管理員使用者。 之前，檔案會成功儲存，未經適當驗證。

_ACP2E-3657 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

### 管理UI、安全性、測試和預覽

#### 內容暫存的動作記錄

動作記錄現在會顯示測試更新活動。 之前，測試更新記錄檔不會記錄在管理動作記錄檔中。

_ACP2E-3679_

### 管理員UI、稅金

#### 稅率管理員UI錯誤

此票證修正了稅率管理員UI的問題，該問題導致切換國家/地區(例如從美國→英國)仍顯示先前選取的美國州別，誤導使用者。
在2.4.9-alpha3中，現在當選取的國家沒有狀態時，狀態列位會重設為*。

_AC-8440 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analytics/報表

#### [問題]如果您只使用Google Analytics，已新增Analytics的SCP允許清單

此PR將CSP白名單新增至Google Analytics模組，讓其獨立運作，而無Google Adwords相依性。 現在，即使Google Analytics Adwords模組停用，Google仍可正常運作。

_AC-16311 - [GitHub問題](https://github.com/magento/magento2/issues/40051) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40032)_

#### 管理動作記錄使用者報表未顯示套用篩選器時所用篩選器的詳細資訊

修正前，管理員活動報表中未記錄篩選引數。 修正之後，現在會記錄所有請求資料。

_ACP2E-4099_

#### 進階報表CSV檔案重複檔案標題會造成空白報表

修正後，針對進階報告功能產生的報告不再包含重複的標題列，以防止列計數超過批次大小。

_ACP2E-4187 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 捨棄的購物車報表包含無效字元

以CSV檔案匯出的捨棄購物車報表，現在包含在MS Excel中開啟時，適用於貨幣符號（例如印度盧比）的正確轉譯字元。

_ACP2E-4288 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 更新MDVA-19640，以符合2.4.8相容性

此修正會將Analytics Cron工作從預設群組移動至分析群組

_ACP2E-4309 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c135fc3a)_

#### 收入未顯示在Admin for Canada網站/貨幣的訂單/發票報表中

有些訂單相關報表未套用商店貨幣匯率。 修正後，報表會正確套用已設定的存放區速率。

_ACP2E-4361 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### 下單無法運作透過可轉讓報價進行結帳使用PayFlow Pro信用卡付款方式

Adobe Commerce現在在使用Payflow Pro信用卡付款方式從可轉讓報價單結帳時，可順利下訂單。 先前，啟用B2B功能後，當買家從可轉讓的報價單中結帳時，選取「Payflow Pro」並按一下「下訂單」會導致頁面無限期載入，且沒有錯誤訊息，因此永遠不會建立訂單。 AC-11973

_AC-11973_

#### 報價重新命名後的成功訊息會間歇性地消失

在店面重新命名可轉讓的報價或報價範本後，Adobe Commerce現在會一致顯示成功訊息。 先前，當買家重新命名可轉讓的報價時，成功訊息會斷斷續續地不出現（通常幾乎立即清除），即使重新命名作業本身成功，也會導致等候此訊息的自動測試失敗。 AC-13447

_AC-13447_

#### 來賓簽出時公司欄位驗證失敗

來賓簽出現在可正確驗證公司欄位。
先前，需要company屬性時，訪客簽出會失敗並出現錯誤：「Company為必填值」，即使填寫欄位亦然。
AC-14987

_AC-14987 - [GitHub問題](https://github.com/magento/magento2/issues/40011) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f1adb44e)_

#### 受限制的管理員無法將公司指派給共用目錄

已修正受限管理員使用者將公司指派至共用目錄時發生例外狀況的問題；更新可確保指派正常運作，而不會發生錯誤。

_AC-15662_

#### 啟用類別許可權時，將群組產品新增至請購單清單的例外狀況

修正將群組產品新增至具有類別許可權的請購單清單時所發生的TypeError，此類別許可權是透過確保產品選項可安全作為陣列處理，允許無例外新增所有產品型別。

_AC-15862_

#### Rest API products-render-info傳回登入客戶的最終價格有誤

票證已修正Rest API產品 — render-info針對登入的客戶傳回錯誤的最終價格

_AC-5979 - [GitHub問題](https://github.com/magento/magento2/issues/35757)_

#### 當我們嘗試從類別頁面新增請購單清單時，「新增至請購單清單」按鈕會消失

先前的「新增至請購單清單」按鈕在嘗試從分類頁面新增時消失，分類頁面現在已修正，我們可以看到分類頁面上的請購單按鈕

_AC-8575_

#### 總計計算不包含稅捐金額

若從已啟用跨境交易的現有採購單下單，訂單會包含正確的總計。

_ACP2E-3727_

#### 透過REST API取消指派B2B共用目錄中的類別緩慢

現在，在B2B中取消指派類別時，效能已大幅改善。 之前，取消指派B2B共用目錄中的類別需要很長時間。

_ACP2E-3796_

### B2B、購物車和結帳

#### 從管理員功能「以客戶身分登入」登入B2B公司使用者時，Storefront上不會顯示具有cartId = X錯誤的實體

現在，使用「以客戶身分登入」功能時，從管理員後端成功登入後，不會再出現「具有cartId = X的這類實體」錯誤。

_ACP2E-3994 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 缺少帳單地址導致無法使用「店內交貨」配送方式下訂單

解決當選取「店內取貨」作為配送方式時，結帳期間未自動填入帳單地址的問題。 如果沒有帳單地址，則無法完成簽出。

_ACP2E-4030 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/42d23211)_

### 購物車與結帳

#### Magento 2.4.7更新（迷你）購物車不允許小數數量

現在，當我們從迷你購物車更新數量且地區設定為NL （荷蘭文）時，Magento可正確處理數量

_AC-13238 - [GitHub問題](https://github.com/magento/magento2/issues/39236) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39669)_

#### [問題]新增EventPrefix和EventObject至簽出合約模型

系統現在包含簽出協定模型的EventPrefix和EventObject，允許使用事件首碼觸發事件。 此增強功能為開發人員提供處理簽出協定事件時的更多彈性。 先前，出庫協定模型不支援EventPrefix和EventObject，因此限制自訂事件處理的能力。

_AC-13252 - [GitHub問題](https://github.com/magento/magento2/issues/32510) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32451)_

#### [問題]開發人員經驗：引號AbstractItem程式碼樣式（SwiftOtter的SOP-348）

此提取要求修正了抽象專案方法的誤導性方法宣告。

_AC-13334 - [GitHub問題](https://github.com/magento/magento2/issues/39340)_

#### 缺少已分組的產品前端數量驗證

系統現在運作正常，並在我們嘗試新增負數和最大數時顯示驗證錯誤

_AC-13524 - [GitHub問題](https://github.com/magento/magento2/issues/39479) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39480)_

#### [問題]更新subtotal.phtml

系統會以正確的間距更新subtotal.phtml

_AC-13907 - [GitHub問題](https://github.com/magento/magento2/issues/39619) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39612)_

#### 無法與訪客下訂單

Adobe Commerce現在可讓訪客購物者在「管理員」中視需要設定中間名稱欄位時成功下訂單。 先前，在Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4)中，視需要設定中間名並以訪客身份出庫會防止下訂單，即使提供了中間名也會阻止出庫完成。 AC-14241

_AC-14241 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql]無法針對不可為null的欄位「SelectedCustomizableOption.label」傳回null

選取的選項不再存在時，系統現在不會擲回含有訊息的內部伺服器錯誤

_AC-14256 - [GitHub問題](https://github.com/magento/magento2/issues/39729) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39888)_

#### 當一個願望清單專案無效時，GraphQL addWishlistItemsToCart無法更新現有購物車專案的數量(Magento 2.4.7-p3)

修正發生無效的可設定產品時，GraphQL addWishlistItemsToCart突變停止處理的問題。 修正後，有效的願望清單專案會新增到購物車並更新數量，而無效專案會略過並傳回適當的錯誤。

_AC-14464 - [GitHub問題](https://github.com/magento/magento2/issues/39820) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8]無法在城市名稱中置入數字0-9、與號、句號或括弧的訂單

修正包含特殊字元（例如）的城市名稱簽出失敗的問題。、和，或括弧。
現在，已成功下具有此類城市名稱的訂單，且沒有驗證錯誤。

_AC-14495 - [GitHub問題](https://github.com/magento/magento2/issues/39854) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 未儲存到報價位址2.4.8的訪客首碼

訪客客戶首碼(Mr/Mrs)現在會在結帳時儲存。
以前，訪客客戶選擇的稱呼在到達最終訂單之前遺失，而所有其他位址列位則正確傳輸。
AC-14705

_AC-14705 - [GitHub問題](https://github.com/magento/magento2/issues/39915) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f1adb44e)_

#### Salesrule Subselect with Quantity條件無法套用

修正具有產品細選條件的購物車價格規則未在結帳時套用的問題。
現在，已根據設定的規則成功套用折扣。

_AC-14884 - [GitHub問題](https://github.com/magento/magento2/issues/39965) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fe72c407)_

#### [問題]移除類別屬性中的空間

系統現在會移除class屬性中的額外空間

_AC-14939 - [GitHub問題](https://github.com/magento/magento2/issues/39977) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39970)_

#### Graphql — 啟用延交訂單時，合併購物車無法正常運作

修正在透過GraphQL合併購物車時，訪客購物車專案未與客戶購物車合併的問題。
現在，客戶購物車可正確反映訪客和客戶購物車的合併數量。

_AC-15148 - [GitHub問題](https://github.com/magento/magento2/issues/40064) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [整合] [簽出] Depend指示已在失敗的付款電子郵件範本中更新

已更新失敗的付款電子郵件範本，以正確處理depend指示。
修正確保送貨地址和送貨方式在適用時正確顯示。
以往，失敗的付款電子郵件會遺漏這些欄位。

_AC-15363 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 登入後繼續到「結帳」重新導向「我的帳戶」頁面

修正工作階段到期後，系統會將使用者重新導向至「我的帳戶」登入頁面，而非結帳登入的問題，確保使用者使用登入表單正確結帳。

_AC-15962_

#### 啟用「固定產品稅捐」時，[購物車]購物車頁面未載入

修正啟用「固定產品稅」(FPT)時，購物車頁面輸入無限載入的問題。 此問題是因為與料號價格包含在相同HTML元素中的稅捐導致小計計算不正確，導致中央小計與彙總小計不符。 修正後，購物車會正確載入並顯示正確的總計。

_AC-16096 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/01cee3c3)_

#### 購物車價格規則動作「購物車中的價格」條件，在不應套用時套用

修正當購物車價格規則套用「購物車價格小於」條件為不符合資格的產品時，發生的問題。
現在，當購物車專案價格不符合設定的規則條件時，可正確驗證及拒絕優惠券。

_AC-6997 - [GitHub問題](https://github.com/magento/magento2/issues/36433) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/01cee3c3)_

#### [問題]設定報價專案的價格，而非base_price

如果您在前端的一個網站中有多個貨幣，系統會正確處理報價專案的價格集，使其設為base_price，而不是價格

_AC-9985 - [GitHub問題](https://github.com/magento/magento2/issues/38094) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36878)_

#### cron工作sales_clean_quotes不會清除過期的永久報價

&#39;persistent_clear_expired&#39; cron工作執行時，現在會清除過期的永久性引號。 以前，過期的永久性引號不會被任何其他cron作業清除。

_ACP2E-3493 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/11be3dff)_

#### 為非作用中公司簽出時出現「發生錯誤」錯誤

修正之前，如果不再啟用使用者公司中的長期專案，購物車頁面上的登出動作就無法正常完成。 現在，如果該公司不再可用，則會正確執行登出。

_ACP2E-3541 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

#### 「使用多個地址結帳」時未儲存地址選擇

在取消多重送貨選項時進行修正之前，當回覆為多重送貨時，不會預先選取地址。 現在，預設位址會取代為多送貨畫面中選取的其中一個位址。

_ACP2E-3646 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6ea61121)_

#### 如果訂單是建立在一個商店檢視上，則[雲端]最近訂購未出現在其他商店檢視中

解決「我的帳戶」頁面未顯示同一商店中其他商店檢視之最近訂單的問題。 已更新訂單擷取邏輯，以確保所有商店檢視的訂單可見度一致，並與「我的訂單」頁面的行為一致。

_ACP2E-3807 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 數量顯示為  新增BUNDLE產品時，管理員客戶購物車區段中的0  

客戶活動中的購物車區段現在會顯示正確的數量。 以前，數量顯示為0。

_ACP2E-3872 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

#### 當購物車不再符合要求時，[雲端]免運費折扣未正確移除

小計(不包括 Tax)在購物車價格規則中，現在會合併先前規則的折扣。

_ACP2E-3973 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 在多重送貨中發現相同客戶的重複訂單

同時請求以多個出貨地址下單時，不會再產生相同客戶的重複訂單

_ACP2E-4117 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 當達到無存貨臨界值時，[雲端]超過存貨限制通知訊息會顯示兩次

修正購物車更新可能顯示重複錯誤橫幅的問題。 先前，在AJAX驗證錯誤後，後端在表單提交期間再次新增相同的訊息，因此購物者會看到兩個相同的警報。 現在我們略過新增額外的後端訊息，將購物車頁面保留為單一清除錯誤橫幅。

_ACP2E-4192 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e885088b)_

#### 帳單資訊伺服器端驗證無法使用送貨資訊REST API來運作

已改善客戶地址資料驗證，以便在REST和GraphQl之間更一致地進行簽出。

_ACP2E-4223 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 購物車頁面上的[雲端]套件組合產品價格問題

修正多貨幣商店購物車頁面上的套件產品價格問題

_ACP2E-4245 - [GitHub問題](https://www.techbuyer.com/) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cbca0396)_

#### 管理購物車存放區範圍問題

現在，當管理員使用者管理已指派給非預設網站的客戶的購物車時，購物車錯誤將會顯示給他。 以前不會顯示錯誤。

_ACP2E-4348 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

#### 抵用券times_used會在部份商業發票取消後重設

部份取消訂單時，抵用券次數現在會正確更新。

_ACP2E-4365 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

### GraphQL的「購物車與結帳」

#### 透過GraphQL下訂單時將訊息對應到錯誤碼時發生錯誤

GraphQL呼叫對不存在或非使用中的購物車下訂單，現在會在所有商店檢視中正確傳回CART_NOT_ACTIVE或CART_NOT_FOUND錯誤碼，修正先前翻譯錯誤訊息導致「未定義」代碼的問題。

_ACP2E-3942 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

#### 虛擬報價單上的[GraphQl]購物車查詢購物車專案折扣問題

解決GraphQL購物車查詢針對虛擬報價傳回錯誤折扣金額的問題。 以前，折扣不正確地套用至不符合資格的特定虛擬產品。

_ACP2E-4248 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2產生另一個問題

當對數量不足的專案發出graphQL請求時，會傳回包含錯誤碼的正確錯誤訊息，而且如果有請求的數量可用，購物車更新就會成功。

_ACP2E-4404 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1c547060)_

### 購物車與結帳、GraphQL、詳細目錄/MSI

#### CartItemInterface中的is_available屬性會傳回false，即使可銷售庫存很高

當可售庫存較高時，is_available屬性會傳回true。 之前，一律會傳回false。

_ACP2E-3885 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

### 購物車與結帳、詳細目錄/MSI

#### 414具有大型購物車大小的「搜尋取車位置」端點發生錯誤

當購物車中有許多產品時，在結帳期間使用「在商店內挑選」選取商店不再因為URL過長而失敗。
之前，這會在選取商店期間產生過長的URL，進而觸發414錯誤，導致客戶無法完成結帳。

_ACP2E-4266 - [GitHub問題](https://mcstaging.casamyers.com.mx/) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/ae1f272f)_

### 購物車與結帳、訂購、產品

#### 即使訂單發票失敗，也會傳送禮品卡電子郵件

在此修正實施之前，禮品卡電子郵件會在發票建立後傳送。 不過，套用修正後，現在會在成功儲存及確認發票後，傳送禮品卡電子郵件。

_ACP2E-3905_

### 購物車與結帳、促銷活動

#### 禮卡顯示餘額不受網站範圍限制

已限制與已指派網站範圍的禮品卡餘額檢查。

_ACP2E-4379 - [GitHub問題](https://www.panini.it)_

### 購物車與結帳、SEO

#### 從次要網站購買時，電子郵件中的禮品卡代碼URL不正確

以前，非預設商店的多商店設定和禮品卡總是會將禮品卡申請重新導向到預設網站。 套用此修正後，電子郵件會將禮品卡宣告連結重新導向至正確的範圍或網站。

_ACP2E-3699_

### 購物車與結帳、安全性

#### 實施sri修補程式後第一次嘗試時，在簽出頁面上取得[CLOUD]的JS檔案404

啟用縮制和套件組合時，修正Mixin之前的版本將不會載入購物車和結帳。 修正後，所有mixin都應如預期載入。

_ACP2E-4128 - [GitHub問題](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

### 購物車與結帳、送貨

#### [Mainline]購物車價格規則未遵守多重出貨

在此修正實施之前，若套用子選取條件並啟用免運費，多送貨產品的購物車價格規則無法正確套用。 不過，由於已套用校正，多批出貨購物車的購物車價格規則現在會如預期運作。

_ACP2E-3666 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

### 目錄

#### 具有相同查詢的相同頁面出現重複的快取fpc

系統現在會正確識別並使用相同的完整頁面快取(FPC)來處理具有相同查詢引數的頁面，無論其順序或尾隨字元為何。 這可防止頁面快取資料夾大小不必要的增加。 以前，如果查詢引數的順序不同或如果存在尾隨字元，系統會為同一頁建立不同的FPC識別碼，從而導致頁快取資料夾大小增加。

_AC-10722 - [GitHub問題](https://github.com/magento/magento2/issues/38269) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38270)_

#### 缺少catalog_product_entity_int表格中必要欄的索引

已新增catalog_product_entity_int表格中缺少之必要欄的索引

_AC-10844 - [GitHub問題](https://github.com/magento/magento2/issues/38315) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38316)_

#### 目錄URL資源(_getCategories)中的範圍錯誤

如果類別URL資源的存放區範圍未定義任何值，此PR會新增遞補至預設範圍。

_AC-11011 - [GitHub問題](https://github.com/magento/magento2/issues/38393) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38394)_

#### [問題]檢查OpenGraph是否可顯示價格

當我們使用隱藏價格的外掛程式，而具有此變更價格的外掛程式不會顯示在OG標籤中時，系統可正常運作。

_AC-11635 - [GitHub問題](https://github.com/magento/magento2/issues/38512) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38510)_

#### 新增稅捐至顯示價格時，價格的舍入問題

系統現在會在新增稅捐至顯示價格時，修正價格的舍入問題

_AC-11725 - [GitHub問題](https://github.com/magento/magento2/issues/18025) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/35730)_

#### [問題]允許自訂目錄規則條件

解決因嚴格型別檢查而無法使用自訂目錄規則條件的問題。 此修正將類別相等檢查取代為instanceof，讓自訂條件類別正常運作，並啟用成功的規則驗證和索引。

_AC-13338 - [GitHub問題](https://github.com/magento/magento2/issues/39339) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/913bf1a6)_

#### 可設定的產品在新增至願望清單時遺失選項

修正將產品新增至願望清單後，可設定的產品選項遺失的問題。 現在，所選的選項仍會保留，這樣產品就可以順利加入購物車，而不會提示使用者重新選取選項。

_AC-13373 - [GitHub問題](https://github.com/magento/magento2/issues/39363) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cc0ec250)_

#### 無法正確顯示可設定產品的子產品（簡單產品）的特殊價格

修正當「用於產品清單」設為「否」時，可設定產品之子（簡單）產品的特殊價格未在產品清單頁面上正確顯示的問題。 現在，特殊價格會與一般價格一起適當顯示，確保各種產品型別的定價顯示一致。

_AC-13594 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3cf1a106)_

#### [錯誤] REST API：更新特殊價格未設定所有商店檢視的值

REST API現在會更新網站中所有商店檢視的特殊價格。
先前，透過REST API更新特殊價格只會影響指定的商店檢視，而不會影響網站中的所有商店檢視。
AC-13671

_AC-13671 - [GitHub問題](https://github.com/magento/magento2/issues/39521) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 價格範圍和config.php的問題

在Magento 2.4.2中，透過config.php變更價格範圍時，無法正確更新catalog_eav_attribute中price屬性的is_global值。
因此，產品價格會維持全球性，無法依網站儲存，即使價格範圍設定為網站亦然。
此因應措施需要手動更新資料庫中的is_global欄，這不適用於生產環境。
此行為與Magento的預設設計一致，其價格範圍為全域或網站，但並非根據商店檢視。

_AC-13857 - [GitHub問題](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP錯誤未通知

已變更回圈變數名稱，以便在指定的產品上正確新增「_cache_instance_product_ids」資料，以用於後續呼叫。

_AC-14159 - [GitHub問題](https://github.com/magento/magento2/issues/39641) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39642)_

#### 彈性搜尋會干擾產品的預設排序順序（從最新到最舊先變更）

系統現在會排序資料庫中最新的產品（具有最高entity_id的產品）會先顯示

_AC-14411 - [GitHub問題](https://github.com/magento/magento2/issues/31043) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36900)_

#### After store切換頁面來自2.4.8中的快取（Store switcher無法運作）

修正手動清除快取後，才能從店面標題切換商店檢視的問題。
現在，儲存區檢視切換可正常運作，不需要清除快取。

_AC-14426 - [GitHub問題](https://github.com/magento/magento2/issues/39806)_

#### 已忽略最小寬度的.less樣式： (@screen__l)

修正類別頁面上每列僅顯示三個產品的問題。
現在，每列會依預期顯示四個產品。

_AC-14463 - [GitHub問題](https://github.com/magento/magento2/issues/39817) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 除了客戶功能表的願望清單頁面外，願望清單計數不會顯示在首頁/其他頁面上

修正願望清單計數在非願望清單頁面上顯示為空白括弧的問題。
現在，所有頁面的「我的願望清單」旁都會顯示正確的願望清單專案計數。

_AC-14607 - [GitHub問題](https://github.com/magento/magento2/issues/39892) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b3774fbe)_

#### 使用不含存放區層級值的REST API時，catalog_product_save_before observer擲回與日期相關的錯誤(getFinalPrice()問題)

此PR會調整SpecialFromDate的處理，以確保當日期提供為DateTimeInterface例項時，能正確設定格式。 這可防止在某些情況下執行getFinalPrice()時發生錯誤。

_AC-14847 - [GitHub問題](https://github.com/magento/magento2/issues/39959) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40003)_

#### 緊急 — 當要新增的產品具有可自訂選項時，無法將產品新增到套件組合

修正具有可自訂選項的產品無法新增至套件組合產品的問題。
以前，在套件建立時，這類產品會從「將產品新增至選項」清單中排除。
現在，可以新增包含可自訂選項的產品至套件組合，而不需要包含其自訂選項，以便進行適當的庫存管理。
如此可建立套件組合，而不會複製產品或影響存貨層次。

_AC-14958 - [GitHub問題](https://github.com/magento/magento2/issues/39993)_

#### 負值`?p=`查詢字串導致Elasticsearch例外狀況

系統現在會處理類別分頁中的負？p=值，該值目前導致例外狀況，且被視為有效請求

_AC-15191 - [GitHub問題](https://github.com/magento/magento2/issues/40079) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40080)_

#### 針對具有單一選項的可設定產品，會顯示「最低」價格標籤

修正可設定產品在PDP/PLP上顯示具有不正確「最低」標籤之價格的問題。
現在，產品顯示正確的價格($500)，且沒有任何誤導的標籤。

_AC-15237 - [GitHub問題](https://github.com/magento/magento2/issues/40104) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 對「加入以比較」按鈕呼叫了錯誤的方法

修正\Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url：：collect()中使用的方法。
之前，錯誤地呼叫getAddToCartButton()而非getAddToCompareButton()。
此變更可確保產品清單中呈現「新增以比較」按鈕的正確行為。
未引入任何功能行為變更；更新改進了開發人員體驗和程式碼正確性。

_AC-15323 - [GitHub問題](https://github.com/magento/magento2/issues/39754) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 以不同貨幣在不同的商店檢視中，在購物車上顯示錯誤的產品價格

修正跨商店檢視使用不同貨幣時，購物車中顯示錯誤產品定價的問題。 修正後，購物車現在會根據設定的貨幣顯示正確的轉換價格，確保產品頁面與購物車之間的一致性。

_AC-15385 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a8cf637b)_

#### 啟用FPT時，可設定產品的「最低」價格顯示錯誤

已確認啟用FPT時，可設定產品的「最低」價格不正確，原因是套用兩次稅捐；此修正可確保最終價格計算會遵循稅捐組態，現在會顯示正確的價格。

_AC-15718 - [GitHub問題](https://github.com/magento/magento2/issues/40171) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a06a4a57)_

#### Eav\Model\Entity\Collection\AbstractCollection中_loadAttributes的時間複雜度會隨著購物車和屬性中的產品數量而增加

此PR已最佳化Eav\Model\Entity\Collection\AbstractCollection中的_loadAttributes，將巢狀回圈取代為陣列聯集(+)，並減少_setItemAttributeValue的呼叫，進而改善大型產品購物車的效能。

_AC-15833 - [GitHub問題](https://github.com/magento/magento2/issues/40216) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40217)_

#### 集合快取與可設定產品庫之間的互動發生錯誤

透過新增防禦型別檢查來確保media_gallery_images一律被視為集合，避免快取資料損毀所造成的嚴重錯誤，藉此解決可設定產品相簿的快取問題。

_AC-16066 - [GitHub問題](https://github.com/magento/magento2/issues/33965) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3b5ac075)_

#### 在產品頁面上建立屬性時，刪除下拉式選項無法運作

_AC-16437_

#### 產品頁面因url重寫而發生錯誤

現在，當我們進行URL重寫時，產品頁面就能成功載入

_AC-2950 - [GitHub問題](https://github.com/magento/magento2/issues/35371) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39670)_

#### 將產品新增至類別時出現[雲端]錯誤

現在，透過快顯視窗格線將產品新增至類別時，分頁和記錄計數標籤可正確運作。 以前，僅載入專案等於頁面大小的單一頁面會導致專案選取下拉式清單發生問題。

_ACP2E-3526_

#### indexer_update_all_views cron錯誤與MAGE_INDEXER_THREADS_COUNT

已修正MAGE_INDEXER_THREADS_COUNT > 2搭配客戶區段索引器的問題

_ACP2E-3538 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_

#### 在頁面產生器產品Widget條件中新增「條件組合」時發生例外

已新增檢查以跳過缺少或不完整的條件，藉此修正問題。 以前，由於處理系統中的不完整條件，這會導致產生錯誤記錄。

_ACP2E-3545 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/11be3dff)_

#### 載入屬性集時瀏覽器當機

如果產品屬性超過4千個，則瀏覽器不會再在屬性集編輯頁面上當機

_ACP2E-3633 - [GitHub問題](https://github.com/magento/magento2/issues/38810) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

#### [雲端]產品URL重寫未針對新商店建立：上線封鎖程式

已成功建立新商店的產品URL重新寫入。
先前作業因記憶體洩漏或逾時而結束。

_ACP2E-3669 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

#### 選項無法運作的屬性預設值

先前，當我們變更產品選取屬性的預設值時，它會顯示為具有先前值的陣列元素。 套用此修正後，當我們更新產品屬性值時，它將會儲存為eav_attribute表格中的單一元素。

_ACP2E-3688 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

#### 由於千位分隔符號，編輯時禮卡驗證失敗

修正當禮卡金額為1000或更多時，禮卡產品型別儲存的問題。

_ACP2E-3704_

#### [Mainline] [雲端]影像大小調整耗用超過400GB的磁碟空間

修正之後，搭配`catalog:images:resize`旗標使用的`--skip_hidden_images`命令將不會針對沒有影像的網站產生影像快取。

_ACP2E-3869 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9ad7d277)_

#### 動態影像產生會產生大量影像

修正後，系統只會針對指派產品的網站產生影像。

_ACP2E-3927 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fab20b00)_

#### 提供的CountryID不存在 — 愛爾蘭(IE)

修正後，愛爾蘭郵遞區號可用於搜尋取車地點。

_ACP2E-3932 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### 前端發生500錯誤，因為配置中快取的配置結構不正確

修正由於版面中快取了不正確的版面結構，頁面傳回500錯誤碼的問題

_ACP2E-4040 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47721be6)_

#### 產品檢視報告不正確 — 計數較GA低

修正report_viewed_product_index表格未顯示正確產品頁面檢視次數的錯誤。

_ACP2E-4045 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6e134409)_

#### 排定更新中「型錄價格規則」折扣金額欄位的驗證錯誤

先前，在修正此問題之前，針對型錄價格規則的排程更新，如果折扣金額為by_fixed，則因為驗證編號範圍規則而無法正確驗證。 套用此修正後，固定價格型錄價格規則的驗證即正常運作。

_ACP2E-4054 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### VAT驗證因VAT API比率限制而失敗 — 觸發誤判的客戶群組變更

最佳化Europa Vat驗證工具的請求，減少「比率限制」錯誤

_ACP2E-4072 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ee918f0d)_

#### 大量刪除核心索引器觸發生產環境上的最大寫入集大小錯誤

根據資料量實作兩種刪除策略，以最佳化目錄規則產品索引清理。

_ACP2E-4085 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a3b7032)_

#### 產品在停用後顯示為無庫存

修正後，停用的產品不存在於產品Widget中。

_ACP2E-4136 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [雲端]重複專案錯誤(temp_category_descendants_%)

針對巢狀類別數量高的環境，修正在建立期間，排程更新重複專案的問題

_ACP2E-4159 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [雲端]比較不同商店的產品計數不符問題

切換至其他商店後，比較產品清單現在可正常運作

_ACP2E-4249 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98f028ab)_

#### 在建立可設定產品期間，受限管理員使用者會看到「新增屬性」按鈕

「新增屬性」按鈕現在僅在可設定的產品建立期間顯示給一般管理員使用者。
之前顯示的「新增屬性」按鈕適用於受限制的管理員使用者

_ACP2E-4279_

#### 「影像和影片」沒有選項可「使用預設」進行影像角色指派

「使用預設值」選項已新增至產品影像和視訊區段，可繼承預設範圍的設定。

_ACP2E-4280 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

#### 客戶群組更新後，受限制的類別產品仍會計入願望清單

在修正之前，類別許可權未正確套用至客戶願望清單專案。 修正後，願望清單專案現在會在Web和GraphQL中正確顯示和分頁。

_ACP2E-4294 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c135fc3a)_

#### PDP和PLP上的[雲端]套件組合產品價格問題

若為非預設貨幣，則會在PDP/PLP上正確顯示一般價格的套裝產品價格

_ACP2E-4298 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a3b7032)_

#### 客戶群組變更後，客戶可訂購無法存取的產品

先前，從管理員變更客戶群組時，前端目錄和購物車未反映目錄許可權中的變更。 不過，套用此修正後，現在當客戶群組從管理員變更時，前端報價會根據更新的目錄許可權而變更。

_ACP2E-4300 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 由於記憶體使用量高，重新索引卡住

修正目錄規則索引器耗用過多記憶體且無法完成，導致不穩定和記憶體不足錯誤的問題。

_ACP2E-4303 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS]排程更新預覽連結會重新導向至維護頁面

已排程的可設定產品首頁連結更新預覽可正確顯示產品清單。 之前，它將使用者重新導向到維護頁面

_ACP2E-4401 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1c547060)_

#### 正在自動移除相關產品

符合目標規則的相關產品現在會在整個重新索引程式中正確關聯

_ACP2E-4430_

### 目錄， GraphQL

#### GraphQl無效的折扣計算

當目錄價格設定為包含稅捐時，GraphQL現在可以正確顯示折扣百分比和基本價格。 先前曾發生舍入錯誤，例如顯示19.99%而非20%。

_ACP2E-3993 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

#### GetCart GraphQL Media Gallery欄位在快取排清後傳回空白資料

修正後，產品的media_gallery會在購物車請求的GraphQL回應中如預期般傳回。

_ACP2E-4185 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45cbf9b6)_

### 目錄、GraphQL、搜尋

#### 產品graphql在類別彙總中傳回停用的類別

修復後，產品GraphQl請求不會傳回已停用的類別。

_ACP2E-2885 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

### 目錄，效能

#### 管理員中的類別載入速度非常慢

類別載入效能已大幅改善。 之前，載入類別所花的時間過長，導致逾時問題。

_ACP2E-3891 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

### 目錄，定價

#### 套用至子產品的目錄價格規則折扣錯誤

修正兩個規則具有相同優先順序的情況下，上層可設定產品會覆寫變數的目錄價格規則的問題。

_ACP2E-3693 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [雲端]套件組合產品價格問題

特殊價格的套件產品價格在非預設貨幣的PDP/PLP上正確顯示

_ACP2E-4110 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6e134409)_

### 目錄、產品

#### [隨機錯誤]未載入Fotorama程式庫

現在，系統可確保Fotorama程式庫已正確載入，讓所有附加的影像如預期般顯示在影像庫中。 之前，由於Fotorama資料庫未正確載入的問題，因此只會顯示第一個影像。

_AC-12124 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/27217d0e)_

#### 「手動新增產品」連結應一律可見

修正在建立沒有現有設定的可設定產品時，無法看到「手動新增產品」連結的問題。 現在會一律顯示連結，讓管理員可輕鬆關聯簡單產品，而不需建立虛擬設定。

_AC-13866 - [GitHub問題](https://github.com/magento/magento2/issues/39595) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ef666cd9)_

#### 編輯後端中的產品從產品選項定價中移除多餘的小數位數

修正管理員在編輯產品時，將產品選項定價截斷為兩位小數點的問題。 系統現在會以較高的小數精確度保留定價，以確保在儲存後仍保留精確值。

_AC-14050 - [GitHub問題](https://github.com/magento/magento2/issues/39655) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3b5ac075)_

#### 透過GraphQL的PDP中未出現透過相關產品規則顯示的相關產品

之前，在套用此修正之前，相對產品規則針對符合規則的產品傳回空白/空值。 套用此修正後，產品成功傳回相符產品的相對規則。

_ACP2E-3949_

### 目錄，傳回

#### 已自動取消選取套件產品列的[雲端]訂單退貨頁面

之前，針對管理面板格線檢視中的套件組合產品「一起出貨退貨」，我們有「選取專案」選項，這會造成套件組合產品「一起出貨」選項的混淆。 套用此修正後，套裝產品出貨不再有「選取料號」選項。

_ACP2E-4180_

### 目錄，搜尋

#### RestApi要求&#39;/rest/default/V1/categories？searchCriteria%5Bpage_size%5D=1&#39;因逾時錯誤而失敗

類別REST API請求不再因逾時錯誤而失敗。
先前，對/rest/default/V1/categories？searchCriteria[page_size]=1的請求會在某些程式碼變更後因逾時而失敗。
AC-13358

_AC-13358 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

### 內容

#### graphql (magento 2.4.6-p4 ) — 嘗試取得非作用中狀態的cms頁面時發生錯誤

修正停用CMS頁面的GraphQL查詢傳回內部伺服器錯誤的問題。
現在，查詢會擷取正確的回應，而不會發生錯誤。

_AC-12302 - [GitHub問題](https://github.com/magento/magento2/issues/38877) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 希望清單共用表單允許在名稱欄位中隨機編碼

修正願望清單共用表單中嚴重的伺服器端範本插入(SSTI)漏洞，此漏洞可在訊息欄位中輸入惡意程式碼並透過電子郵件傳送。 更新將輸入驗證新增至區塊範本指令和不安全模式，現在會在偵測到無效內容時顯示錯誤訊息。

_AC-12730 - [GitHub問題](https://github.com/magento/magento2/issues/39024) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/01cee3c3)_

#### 將csp_whitelist.xml放在主題中無法運作，會產生間歇性問題

已實施每個網站區域的CSP白名單快取。

_AC-13069 - [GitHub問題](https://github.com/magento/magento2/issues/38933) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39672)_

#### 升級到magento 2.4.7後，p2無法看到新上傳的檔案媒體集

升級後，新上傳的檔案現在會出現在媒體集中。
先前，升級至Magento 2.4.7 p2後，新上傳的影像要等到執行手動同步後，才會出現在「媒體集」中。
AC-13262

_AC-13262 - [GitHub問題](https://github.com/magento/magento2/issues/39275)_

#### 媒體集從名稱相同但大小寫不同的目錄顯示不正確的影像

現在，系統會解決上傳至Media Gallery中特定目錄的檔案，也會顯示在名稱相似但大小寫不同的目錄中的問題。

_AC-13489 - [GitHub問題](https://github.com/magento/magento2/issues/39382) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39502)_

#### 將相簿影像完全移除後，會保留設定範圍的角色/型別（基底/小型/縮圖），並在重新新增「舊」角色/型別後顯示

系統在存放區範圍中如預期般運作，影像會根據預設範圍繼承新新增影像的角色/型別

_AC-13556 - [GitHub問題](https://github.com/magento/magento2/issues/39481) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39680)_

#### [小錯誤]當欄位值包含`listing component`時，無法點選管理面板`\`的篩選器

當我們篩選含有斜線的頁面標題時(例如： Magento\Store)，系統可正常運作

_AC-13661 - [GitHub問題](https://github.com/magento/magento2/issues/39513) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39535)_

#### 錯誤：載入產品時，針對管理員內容Pagebuilder的「Magento_Catalog/js/validate-product」出現指令碼錯誤

此PR修正使用產品條件編輯pagebuilder時catalogAddToCart的指令碼錯誤

_AC-13891 - [GitHub問題](https://github.com/magento/magento2/issues/39604) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39677)_

#### 設定產品Widget時出現catalogAddToCart指令碼錯誤。

修正在頁面產生器中設定具有「條件組合」的產品Widget時發生的指令碼錯誤。 此問題是因為缺少前端JS檔案所導致，進而導致主控台錯誤。 修正後，Widget可正確載入，且沒有主控台錯誤。

_AC-13892 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/528af81a)_

#### 封鎖具有相同識別碼的小工具中的選取專案

當我們有相同的識別碼區塊時，系統現在會在建立Widget時正確處理選取區塊

_AC-14132 - [GitHub問題](https://github.com/magento/magento2/issues/39692) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39722)_

#### ID為「0」的CMS頁面不存在，記錄泛濫

建立管理員使用者後以及建立新頁面時，系統如預期般運作。log沒有任何錯誤訊息

_AC-14254 - [GitHub問題](https://github.com/magento/magento2/issues/39743) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl]路由查詢無限回圈

此票證修正具有相同請求路徑和目標路徑的GraphQL路由查詢造成無限回圈並最終逾時的問題。
在2.4.9-alpha3中，查詢現在會傳回正確的錯誤回應，而非回圈。

_AC-14269 - [GitHub問題](https://github.com/magento/magento2/issues/39707) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### 不存在的網站地圖會以產品影像回應

系統現在修正我們存取無現有的Sitemap回應產品影像，回應： 404 NOT FOUND

_AC-14295 - [GitHub問題](https://github.com/magento/magento2/issues/39756) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40135)_

#### 目錄連結Widget使用不正確的URL

新增目錄產品連結和目錄類別連結後，系統現在可以正確處理Widget，並在HTML來源中顯示正確的URL

_AC-14437 - [GitHub問題](https://github.com/magento/magento2/issues/39464) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39710)_

#### 未考慮表格首碼

現在在Admin中載入「設計>設定」主題格線時，Adobe Commerce會正確遵循資料庫表格首碼。 先前，在Adobe Commerce 2.4.8上以app/etc/env.php中設定的表格首碼導覽至「內容>設計>設定」會導致錯誤，因為未考量表格首碼，且未轉譯主題的格線。

_AC-14556 - [GitHub問題](https://github.com/magento/magento2/issues/39847) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 將常數IMAGE_FILE_NAME_PATTERN變更為公開可見，以獲得更大的彈性

GenerateRenditions.php中的常數IMAGE_FILE_NAME_PATTERN已公開，讓開發人員在處理影像轉譯時擁有更多彈性。 此修正包含在Magento 2.4.9-alpha3中，具有完整單位和整合測試涵蓋範圍。

_AC-15338 - [GitHub問題](https://github.com/magento/magento2/issues/39733) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### 多次出貨的檢閱訂單頁面中會顯示不正確的出貨方法

修正多重出貨結帳中，複查訂單頁面顯示不正確出貨成本（5 INR而非10 INR）的問題；更新可確保針對每個地址顯示正確的出貨金額。

_AC-15664 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento config:show（或set） design/theme/theme_id失敗

修正儘管存在設定，但設計/theme/theme_id路徑的CLI命令bin/magento config:show和config:set失敗的問題。
現在，命令成功執行，並允許檢視和設定主題ID，沒有錯誤。

_AC-5915 - [GitHub問題](https://github.com/magento/magento2/issues/35751) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64823f95)_

#### 無法上傳寬度相對較小的影像

系統不再無法以相對較小的寬度調整影像大小。

_ACP2E-3558 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_

#### 如果使用者沒有Widget許可權，頁面產生器的產品元件就無法運作

修正前，存取沒有許可權的Widget時，頁面擲回一般錯誤並顯示「載入」GIF。 現在，修正後，強制回應視窗會顯示「很抱歉，您需要許可權才能檢視此內容」。 訊息。

_ACP2E-3664 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### 遠端儲存路徑樣式設定的設定路徑不正確

修正後，設定遠端儲存路徑樣式設定將影響實際的AWS S3路徑樣式設定。

_ACP2E-3734 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

#### GraphQL中未套用頁面產生器產品Widget順序

修正GraphQL「路由」查詢回應未傳回頁面產生器產品內容型別中正確排序順序的產品的問題。

_ACP2E-3898 - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### 因ICU資料庫版本而在非英文店面顯示定價問題

修正後，產品價格會以希伯來文（以色列）地區設定正確顯示。

_ACP2E-3938 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

#### 更新存放區代碼已清除設計設定

修正由於設定快取未正確更新而更新存放區檢視程式碼會清除「設計組態」設定的問題。

_ACP2E-3941 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

#### 內容分段預覽不適用於搜尋結果

在測試預覽中搜尋現在會根據選取的範圍傳回產品。 以前，搜尋會傳回預設範圍內的結果，而不考慮所選存放區。

_ACP2E-4095_

#### 頁面產生器 — 產品條件邏輯問題（OR邏輯的行為未正確顯示較少產品）

現在，在「符合任何」條件中使用具有全域範圍的屬性時，頁面產生器產品Widget會傳回正確結果

_ACP2E-4096 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

#### 產品輪播會將不正確的產品新增到頁面產生器

在修正之前，如果可設定的產品有任何子項符合篩選條件，則該可設定的產品會自動包含在PageBuilder產品輪播清單中。 現在，修正後，只有當子產品本身不可見時，才會包含父產品。

_ACP2E-4341 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

#### 如果在類別條件中列出多個類別，產品清單Widget會傳回不正確的結果

現在，當多個類別列在條件「類別是其中之一」中時，「目錄產品清單」Widget會顯示準確的結果。 過去，系統只會處理清單中的第一個類別。

_ACP2E-4353 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a3b7032) - [GitHub程式碼貢獻](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [雲端]媒體集資料夾建立需要[新增媒體集]中的delete_folder許可權 — 僅具有create_folder的角色無法建立資料夾

以前，在實施此修正之前，僅具有內容建立資料夾許可權的管理員使用者無法在CMS媒體集中建立資料夾。 不過，修正之後，媒體集中的內容建立者現在可以只建立資料夾許可權來建立資料夾。

_ACP2E-4376 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS]複製CMS頁面

在此修正之前，複製具有自訂版面更新的cms頁面會失敗。 現在，包含自訂版面更新的CMS頁面可以重複使用，而不會發生錯誤。

_ACP2E-4449 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 具有網站層級許可權的管理員無法編輯動態區塊

現在，具有網站範圍許可權的管理員使用者可以在可存取的儲存檢視中編輯橫幅的內容。

_ACP2E-4468_

### 客戶/

#### 當管理員透過CMS頁面內容新增CustomerCustomAttribute區塊時，Storefront發生例外狀況

修正透過CMS頁面內容新增CustomerCustomAttribute區塊時，造成店面例外狀況，且頁面無法載入的問題。
現在，Storefront會正常顯示，並在無法轉譯內容時顯示有意義的訊息，以避免嚴重錯誤。

_AC-11004_

#### 客戶現在線上上「管理網格」會在每次使用者登入、登出及登入時顯示重複列

修正客戶登出並重新登入時，「客戶現線上上」管理格線顯示重複列的問題。
網格現在會以最新的活動更新現有記錄，而不是建立重複的專案，以確保準確的客戶工作階段追蹤。

_AC-11511 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/528af81a)_

#### 最小值和最大值驗證不適用於店面上的DOB屬性

此錯誤修正了出生日期(DOB)屬性的最小和最大日期驗證在店面中無法運作（儘管在管理員中運作正常）的問題。
在2.4.9-alpha3中，驗證現在會正確封鎖將DOB超出允許範圍的客戶儲存，並顯示錯誤訊息。

_AC-13535 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ajax 401錯誤在管理員面板的警告畫面中載入，同時以客戶許可權登入被撤銷

此錯誤修正已撤銷的客戶許可權登入問題，該問題導致警告快顯視窗中出現原始HTML的Ajax 401錯誤。
修正後，系統現在可以正確顯示一般警告訊息，而非原始HTML。
解決方案以Magento 2.4.9-alpha3提供

_AC-15336 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

### 框架

#### 正在完成已停用模組的程式碼。

此提取請求逸出在程式碼編譯之前已停用模組。

_AC-10933 - [GitHub問題](https://github.com/magento/magento2/issues/38241) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39723)_

#### 使用自訂DB觸發程式執行命令安裝程式:upgrade時發生錯誤

自訂資料庫觸發程式在安裝:upgrade期間不再造成錯誤。
先前，使用自訂資料庫觸發器執行bin/magento設定:upgrade （例如，在存放區表格上執行AFTER INSERT）可能會導致錯誤：
「警告：嘗試在vendor/magento/framework/Mview/View/Subscription.php第357行存取型別為null的值的陣列位移」
AC-11487

_AC-11487 - [GitHub問題](https://github.com/magento/magento2/issues/38481)_

#### [問題]讓方法簽章與介面一致

getAttributes的方法簽章現在與其介面一致，防止覆寫方法時發生任何錯誤。 先前，當嘗試覆寫getAttributes方法時，方法簽章中的不一致會導致錯誤。

_AC-11578 - [GitHub問題](https://github.com/magento/magento2/issues/38501) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/31955)_

#### 網站/群組/存放區實體表單無法延伸為擴充功能屬性的多個值表單元素

此PR允許多值表單元素將資料提交至網站/群組/商店表單。

_AC-11657 - [GitHub問題](https://github.com/magento/magento2/issues/24070) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/24094)_

#### [問題]修正UI元件的驗證電子郵件規則

系統現在可正確驗證在UI元件中輸入的多個電子郵件地址，確保每個電子郵件都正確裁剪和驗證。 以前，系統使用不正確的方法修剪電子郵件地址，這可能會導致驗證錯誤。

_AC-11719 - [GitHub問題](https://github.com/magento/magento2/issues/38528) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33470)_

#### [問題]移除領域解析器使用情形

此PR會全域解析管理員URL設定，而非目前的商店

_AC-11736 - [GitHub問題](https://github.com/magento/magento2/issues/38566) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38554)_

#### [問題]移除多餘的方法

程式碼品質：移除AsynchronousOperations和Sales元件中僅呼叫父方法而未新增功能的備援方法，進而改善程式碼可維護性。

_AC-11915 - [GitHub問題](https://github.com/magento/magento2/issues/29748) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml範本對PHP 8.2無效

此提取請求修正了使用null標題建立的CMS頁面(如Php 8.x將null傳遞至trim()時擲回例外狀況：已棄用功能： trim()：將null傳遞至字串型別的引數#1 ($string))的問題

_AC-12856 - [GitHub問題](https://github.com/magento/magento2/issues/39092) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39398)_

#### 在欄位專案底下包含註解的etc/adminhtml/system.xml檔案上，xsd驗證失敗。

此PR修正phpstorm中評論節點的XML結構描述定義

_AC-12945 - [GitHub問題](https://github.com/magento/magento2/issues/39148) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39867)_

#### 透過設定路由使用預設Nginx設定的Magento版本公開

系統目前如預期般運作，不會公開網站執行中的確切Magento版本

_AC-13205 - [GitHub問題](https://github.com/magento/magento2/issues/39227) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39228)_

#### [問題]將物件引數解除封裝為具名引數

系統現在利用PHP 8.1功能，使用具名引數來解壓縮陣列，因此不需要呼叫array_values，並有可能改善整體效能。 以前，系統需要array_values來解壓縮物件引數。

_AC-13210 - [GitHub問題](https://github.com/magento/magento2/issues/39233) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37411)_

#### [問題]重構報價地址確實驗證方法

此PR包含doValidate方法的可讀性改善。

_AC-13214 - [GitHub問題](https://github.com/magento/magento2/issues/38230) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38219)_

#### Magento選項 — 執行cli時從未使用過magento-init-params？

現在執行CLI命令時會使用 — magento-init-params選項。
先前，將 — magento-init-params傳遞給CLI命令對MAGE_MODE等引數沒有影響。
AC-13231

_AC-13231 - [GitHub問題](https://github.com/magento/magento2/issues/39248) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue型別宣告錯誤

現在，系統在getItemsByColumnValue函式中，將輸入引數$value正確定義為基本型別，而非陣列，確保該函式傳回預期的集合。 以前，如果使用具有單一值的陣列作為輸入引數，該函式將傳回null，並且IDE會將其標籤為錯誤。

_AC-13240 - [GitHub問題](https://github.com/magento/magento2/issues/33070) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33120)_

#### 當鎖定提供者使用檔案儲存時，我們會獲得不斷增加的檔案目錄，而不會進行任何清除

此提取請求會引入每天執行一次的新cronjob，並搜尋過去24小時內未修改且可安全移除的鎖定檔案。 這會控制鎖定檔案目錄的內容。
只有當鎖定提供者設定為使用檔案時，此cronjob才會執行某些動作，而不是當使用其他檔案之一時（資料庫 — 預設、縮放管理員或快取）

_AC-13367 - [GitHub問題](https://github.com/magento/magento2/issues/39369) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39372)_

#### [問題]清理：請勿使用方法呼叫的void傳回值。

此PR會進行微幅清理。 有時我們呼叫未傳回任何內容(void)的方法，然後使用該結果值。 這確實不是必要。

_AC-13664 - [GitHub問題](https://github.com/magento/magento2/issues/39524) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39516)_

#### Magento 2.4.7多商店實作中與FPC相關的快取金鑰

修正多存放區設定中的完整頁面快取(FPC)快取金鑰不包含MAGE_RUN_CODE和MAGE_RUN_TYPE，導致快取金鑰行為與舊版不一致的問題。 快取金鑰現在正確包含存放區內容，以確保在存放區之間有正確的快取隔離。

_AC-13719 - [GitHub問題](https://github.com/magento/magento2/issues/39456) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ae6f305b)_

#### [問題] [PHPDOC]修正Magento\Framework\Message\ManagerInterface的錯誤phpdoc

此PR修正\Magento\Framework\Message\ManagerInterface的錯誤phpdoc，並移除\Magento\Framework\Message\Manager中的所有重複phpdoc （使用inheritdoc syntaxe）。

_AC-14312 - [GitHub問題](https://github.com/magento/magento2/issues/39593) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39153)_

#### 部分索引已停止對有大量更新的客戶運作

部分索引現在適用於有大量更新的客戶。
先前，達到變更記錄檔表格中version_id欄的最大值，會導致索引更新停止。
AC-14424

_AC-14424 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8使用不遵循語意版本設定的開發套件

Magento 2.4.8需要pdein/pdepend和phpmd/phpmd (3.x-dev)的開發版本才能與PHP 8.4相容。
這些開發版本與協力廠商工具衝突，這些工具預期會符合SemVer的套件，因此無法進行某些升級。
暫時解決方法是為composer.json中的開發版本取名（例如「3.x-dev as 3.99.0」），以便在滿足語意版本化的同時提供相容性。
這可確保PHP 8.4的支援並避免衝突，直到穩定發行版本可用。

_AC-14519 - [GitHub問題](https://github.com/magento/magento2/issues/39796)_

#### 下載運費標籤後，我們可以看到一些與運費和包裝費不符的運費金額。

送貨標籤數量現在與運費和包裝費相符。
先前，下載送貨標籤後，顯示的金額與運費和包裝費不符。
AC-14560

_AC-14560_

#### MView機制會在執行觸發程式時無訊息地忽略錯誤

MView機制現在會正確報告觸發程式執行的錯誤。
以前，觸發執行期間的錯誤會被無訊息地忽略，這可能導致索引更新遺失，而不會發出任何通知。
AC-14567

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

#### [問題]包含建構函式以成為`CommandListInterface` API的一部分，擴充內嵌檔案

此PR更新將Magento\Framework\Console\CommandList標示為API，並將建構函式引入到CommandListInterface以獲得更好的擴充性。 它也改善了內嵌檔案，以增強擴充主控台命令之開發人員的清晰度和可維護性。

_AC-14680 - [GitHub問題](https://github.com/magento/magento2/issues/31102) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37901)_

#### [問題]移除與Microsoft IIS相關的程式碼

此PR會依照Magento系統需求檔案清理與Microsoft IIS相關的程式碼，其中指出不支援Microsoft Windows作業系統

_AC-14702 - [GitHub問題](https://github.com/magento/magento2/issues/39910) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js語法錯誤

系統Magnifier功能應該保持以前的工作方式，而且不應該在全域範圍中使用magnifierOptions

_AC-14722 - [GitHub問題](https://github.com/magento/magento2/issues/36200) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39321)_

#### `setup:db:status` CLI命令中的反向連線詳細模式

`setup:db:status` CLI命令現在支援詳細模式。
過去，您很難瞭解升級所需的資料庫變更。 現在，執行`bin/magento setup:db:status -v`可提供有關結構描述和資料差異的詳細資訊。
AC-14807

_AC-14807 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 使用tls和2.4.8傳送SMTP郵件

使用TLS傳送SMTP電子郵件現在可如預期運作。
以前，透過SMTP傳送包含TLS的電子郵件會導致錯誤： error:1408F10B:SSL常式:ssl3_get_record:版本號碼錯誤。
AC-14883

_AC-14883 - [GitHub問題](https://github.com/magento/magento2/issues/39947) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8b453942) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/d3ea191d)_

#### [問題]修正靜態內容部署中的並行問題

此PR修正多個同時處理程式向上旋轉以處理相同主題套件的錯誤，具體取決於主題與其父項的定義方式。

_AC-14944 - [GitHub問題](https://github.com/magento/magento2/issues/39990) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39954)_

#### [問題]移除PHP版本&lt; 8.1的舊版相容性代碼

此提取請求會移除設計在PHP &lt;8.1上執行的程式碼。
此外，已移除對PHP_VERSION_ID連絡人可用性的檢查，因為它可在所有PHP版本中使用

_AC-14971 - [GitHub問題](https://github.com/magento/magento2/issues/39891) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39882)_

#### 登入時FPC無法運作

完整頁面快取(FPC)現在可供登入的客戶正常運作。
先前，登入後，首頁不會從快取載入，且x-magento-cache-debug標題顯示MISS而非HIT。
AC-14999

_AC-14999 - [GitHub問題](https://github.com/magento/magento2/issues/40007)_

#### 在某些php類別中新增泛型型別，以改進靜態分析支援

系統現在使用泛型型別定義來大幅改善此狀況，方法是將其解譯為方法呼叫傳回的確切類別

_AC-15013 - [GitHub問題](https://github.com/magento/magento2/issues/40017) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40119)_

#### [問題]改善處理SchemaBuilder的錯誤

此PR可改善資料庫架構的錯誤訊息處理方式。 它有助於我們識別問題，而不需要大量偵錯。

_AC-15020 - [GitHub問題](https://github.com/magento/magento2/issues/39816) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39799)_

#### Rest API：在null上呼叫成員函式getVideoProvider()

修正子產品只有YouTube視訊且沒有其他影像時，呼叫可設定產品子項API傳回500內部伺服器錯誤的問題。
錯誤是由ExternalVideoEntryConverter中的null參考所造成。
現在，API可正確傳回含有媒體集專案的子產品，包括外部視訊資料，而不會擲回錯誤。
這可確保透過REST API正確擷取子項產品的所有媒體型別。

_AC-15046 - [GitHub問題](https://github.com/magento/magento2/issues/40021)_

#### [W3C]從Cookie指令碼標籤宣告中移除text/javascript

此PR已從Cookie指令碼標籤中移除不必要type=&quot;text/javascript&quot;屬性，以符合HTML5規範。

_AC-15061 - [GitHub問題](https://github.com/magento/magento2/issues/39982) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39983)_

#### [問題]修正PHPDoc註解中的幾個錯字

此PR修正phpdoc中的幾個錯字

_AC-15075 - [GitHub問題](https://github.com/magento/magento2/issues/40042) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38809)_

#### [問題]移除短語呼叫中的sprintf使用方式

此PR會移除Magento核心中短語函式呼叫中的sprintf使用情形。

_AC-15183 - [GitHub問題](https://github.com/magento/magento2/issues/40050) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40033)_

#### 無法在具有作用中應用程式鎖定的多執行緒索引器上重新索引所有無效專案

此問題修正啟用use_application_lock時多執行緒索引器失敗的問題。
之前，DB鎖定在平行處理期間遺失，導致索引器維持在「運作」狀態，並擲回SQL錯誤（找不到資料表）。
在Magento 2.4.9-alpha3中，此修正會在啟用應用程式鎖定的情況下，確保索引子可正確重新索引。

_AC-15270 - [GitHub問題](https://github.com/magento/magento2/issues/40102) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### Magento\Framework\Escaper中的傳回型別不清楚/無效

當在層級5使用phpstan執行靜態分析時，系統將接受逸出方法的型別

_AC-15272 - [GitHub問題](https://github.com/magento/magento2/issues/40012) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40114)_

#### [問題]允許佇列特定的設定超過預設的最大訊息值

系統現在允許佇列特定的設定超過預設的最大訊息值

_AC-15284 - [GitHub問題](https://github.com/magento/magento2/issues/40121) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40110)_

#### [問題]使用清漆時相同查詢的相同頁面出現重複的快取fpc

此PR透過標準化查詢引數順序來修正使用Varnish時重複的全頁快取專案，確保相同請求的一致快取金鑰。
改善快取命中率和效能，讓不同序列中的相同引數有URL。

_AC-15325 - [GitHub問題](https://github.com/magento/magento2/issues/39706) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39704)_

#### 社群主題包含Commerce版本模組的資源

將社群主題重新定位至各自的模組目錄，從社群主題中移除僅限Commerce的樣式資源。 這可防止未使用的CSS在Community Edition中捆綁，減少不必要的裝載並消除無效樣式規則，同時確保在啟用Commerce模組時具有適當的樣式。

_AC-15347 - [GitHub問題](https://github.com/magento/magento2/issues/21446) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9bcd880a)_

#### [問題]將存放區程式碼新增至Url應為全域

此PR解決的方法是確保使用核心程式碼中的全域範圍擷取「將存放區程式碼新增至URL」設定

_AC-15365 - [GitHub問題](https://github.com/magento/magento2/issues/40069) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40065)_

#### [問題]只有在未停用的情況下才記錄未宣告的外掛程式

此PR會修正並記錄實際未宣告且未使用的外掛程式（已啟用且遺漏執行個體）。

_AC-15386 - [GitHub問題](https://github.com/magento/magento2/issues/40086) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40081)_

#### [問題]小型清理，已從陣列中移除重複的金鑰

系統現在執行小型清理，發現陣列有2個重複索引鍵，其值為「Weight （及以上）」

_AC-15414 - [GitHub問題](https://github.com/magento/magento2/issues/39851) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2、magento/framework 103.0.8-p2版：呼叫不已存在方法的EmailMessage類別

EmailMessage類別現在可以正確處理電子郵件內文擷取。
之前，在搭配magento/framework 103.0.8-p2版的Magento 2.4.8-p2中，Magento\Framework\Mail\EmailMessage類別嘗試在Symfony郵件訊息物件上呼叫不存在的方法(getTextBody)。 當第三方模組或自訂依賴此方法處理電子郵件時，這會導致錯誤。
現在，EmailMessage類別不再呼叫未定義的方法，以防止這些錯誤。 AC-15446

_AC-15446 - [GitHub問題](https://github.com/magento/magento2/issues/40170) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/059fd469) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x]資料/結構描述修補程式getAliases()在`setup:upgrade`期間造成錯誤

getAliases()在安裝:upgrade期間造成錯誤，此PR修正了相同的

_AC-15559 - [GitHub問題](https://github.com/magento/magento2/issues/31396) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38239)_

#### 作業的定序混合不合法

_AC-15614 - [GitHub問題](https://github.com/magento/magento2/issues/40138) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/44329e9d)_

#### [問題] [PHPDOC]修正錯誤的phpdoc Magento\Framework\DB\Adapter\AdapterInterface：：quoteColumnAs()

此PR會更新\Magento\Framework\DB\Adapter\AdapterInterface：：quoteColumnAs()的PHPDoc，以正確反映$alias引數除了字串外也可以是Null。 如此可解決5級以上的PHPStan問題，並改善程式碼品質工具的相容性。

_AC-15626 - [GitHub問題](https://github.com/magento/magento2/issues/39598) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39581)_

#### Urlrewrite模組中歸類混合不合法

_AC-15647 - [GitHub問題](https://github.com/magento/magento2/issues/40189) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/44329e9d)_

#### `\Magento\Framework\Escaper::escapeScriptIdentifiers`從未符合條件

修正了\Magento\Framework\Escaper：：escapeScriptIdentifiers中無法連線的條件，將檢查false取代為null，使其與preg_replace傳回值對齊，並提高程式碼正確性而不影響功能。

_AC-15667 - [GitHub問題](https://github.com/magento/magento2/issues/40195) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cc0ec250)_

#### 亮漆7.3 （最新版本） — 預設類別的子類別連結/選項未顯示在商店首頁上

已確認使用Varnish 7.3時店面首頁上遺失子類別連結是由ESI要求處理和伺服器設定所造成，而非Magento程式碼缺陷；此問題可透過建議的Varnish設定調整來解決，不需要變更核心程式碼。

_AC-15674 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3cf1a106) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9a62604c)_

#### [問題]將額外的偵錯資料新增至`cache_invalidate`記錄檔

此PR增強了cache_invalidate記錄，加入完整快取清除的要求內容與棧疊追蹤，以改善偵錯與可見度。
這有助於識別未預期的完整快取無效判定的來源，而不會變更現有功能。

_AC-15719 - [GitHub問題](https://github.com/magento/magento2/issues/40204) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40196)_

#### [問題]稍微改善撰寫器的自動載入器排除清單。

此PR會精簡Composer自動載入器排除專案，以略過測試類別，減少不必要的類別對應專案，並防止PSR-4警告。

_AC-15743 - [GitHub問題](https://github.com/magento/magento2/issues/40109) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40107)_

#### [問題]防止含有`db_schema.xml`的`comment=""`宣告破壞零停機部署

系統現在會防止含有comment=&quot;&quot;的db_schema.xml宣告破壞零停機時間部署

_AC-15980 - [GitHub問題](https://github.com/magento/magento2/issues/40254) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40242)_

#### 無法清除`\Magento\Framework\Filesystem\Glob::glob(...)`快取

此PR更新引入了一種清除\Magento\Framework\Filesystem\Glob使用的內部靜態快取的方法，以確保在檔案結構變更時產生新鮮且準確的結果。 它改善了可靠性和開發人員體驗，尤其是在測試場景和長時間執行的流程中，其中glob結果必須保持最新。

_AC-15989 - [GitHub問題](https://github.com/magento/magento2/issues/35741) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/35742)_

#### ReadME Leaders連結URL具有永久重新導向

更新README Leaders連結，將永久重新導向和過期的URL取代為正確的工作連結，確保貢獻者和維護者頁面正確開啟。

_AC-16046 - [GitHub問題](https://github.com/magento/magento2/issues/40292) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/913bf1a6)_

#### [問題] [PHPDOC]修正錯誤的phpdoc Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

更正屬性集合中joinLeft()的PHPDoc註解，以允許正確的陣列定義，增強程式碼正確性及與PHPStan等工具的相容性。

_AC-16187 - [GitHub問題](https://github.com/magento/magento2/issues/40354) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39155)_

#### 確保單一命令失敗會記錄錯誤（檔案或stderr）而不會停止後續CLI命令的執行。

系統現在確保單一命令失敗會記錄錯誤（檔案或stderr）而不會停止後續CLI命令的執行

_AC-16244 - [GitHub問題](https://github.com/magento/magento2/issues/40006) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40063)_

#### [問題]將int型別新增至PageCache核心中的$maxAge

此PR會確保PageCache核心中的$maxAge引數嚴格輸入為整數，以改善型別安全性並防止在快取處理中出現PHPStan/靜態分析錯誤。

_AC-16313 - [GitHub問題](https://github.com/magento/magento2/issues/40438) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36600)_

#### 偽模組需要擴充功能存放庫中的dev/目錄

_AC-16487_

#### 新增至購物車事件：空價

修正在加入購物車程式期間，checkout_cart_product_add_after事件觀察程式中傳回產品價格為null的問題。
現在，可正確擷取基本價格和相關價格值，確保觀察者和自訂實施都可使用精確資料。

_AC-5966 - [GitHub問題](https://github.com/magento/magento2/issues/35638) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3b5ac075)_

#### PHP8.1型別bugfix

現在，當嚴格處理模式非作用中或產品資訊可用時，關聯的產品會初始化為空陣列，而非false。 此變更可確保後續邏輯處理相關產品的行為一致，改善產品準備程式的穩定性和可預測性。

_AC-6017 - [GitHub問題](https://github.com/magento/magento2/issues/35808) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/35842)_

#### 必須是型別&#39;Magento\Customer\Api\Data\GroupInterface&#39;。 找到&#39;Magento\Customer\Model\Group&#39;。

修正使用GroupFactory透過GroupRepositoryInterface儲存客戶群組時，造成型別錯誤的問題。
之前，存放庫需要GroupInterface，但傳遞了群組模型執行個體，導致嚴重錯誤。
現在，可以透過存放庫確保適當的介面實作，成功儲存客戶群組。
這樣便能以程式設計方式建立或更新客戶群組時，解決IDE警告和執行階段錯誤。

_AC-6909 - [GitHub問題](https://github.com/magento/magento2/issues/36269)_

#### 貸方通知的欄位驗證

修正即使在填寫必填自訂欄位後，銷退折讓單頁面上的欄位驗證仍無法提交的問題。
現在，驗證可正確運作，而且一旦完成所有必填欄位，就會啟用提交按鈕。

_AC-8308 - [GitHub問題](https://github.com/magento/magento2/issues/37182) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64823f95)_

#### [問題]從架構（第3部分）移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8343 - [GitHub問題](https://github.com/magento/magento2/issues/37270) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37020)_

#### [問題]在模組send friend圖形ql中使用建構函式屬性升級

系統現在會在「send friend」GraphQL模組中利用建構函式屬性升級，增強程式碼可讀性並降低複雜性。 過去，模組使用佔據許多行的屬性，使程式碼更複雜且不易讀取。

_AC-8346 - [GitHub問題](https://github.com/magento/magento2/issues/37235) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37197)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8349 - [GitHub問題](https://github.com/magento/magento2/issues/37266) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37016)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8350 - [GitHub問題](https://github.com/magento/magento2/issues/37265) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37015)_

#### [問題]從`@author`移除禁止的`Magento_Downloadable`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8355 - [GitHub問題](https://github.com/magento/magento2/issues/37251) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37001)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，提高程式碼品質和一致性。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8358 - [GitHub問題](https://github.com/magento/magento2/issues/37264) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37014)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8359 - [GitHub問題](https://github.com/magento/magento2/issues/37262) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37012)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8360 - [GitHub問題](https://github.com/magento/magento2/issues/37261) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37011)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，確保程式碼更乾淨且標準化。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8361 - [GitHub問題](https://github.com/magento/magento2/issues/37260) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37010)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8362 - [GitHub問題](https://github.com/magento/magento2/issues/37259) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37009)_

#### [問題]移除禁止的`@author`標籤

系統現在會從某些模組中移除禁止的`@author`標籤，以遵守編碼標準，進而提升整體程式碼品質。 先前，此標籤在某些模組中的存在違反了既定的編碼標準。

_AC-8363 - [GitHub問題](https://github.com/magento/magento2/issues/37258) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37008)_

#### [問題]從`@author`和`Magento_Backup`移除禁止的`Magento_Bundle`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8367 - [GitHub問題](https://github.com/magento/magento2/issues/37244) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36979)_

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

#### [問題]修正catalogsearch中的變數名稱

系統現在可以在搜尋引擎模組中正確地命名變數，藉此加強程式碼清晰度和可維護性。 先前在搜尋引擎模組中使用了不相關的變數名稱$defaultCountry，而造成混淆。

_AC-9215 - [GitHub問題](https://github.com/magento/magento2/issues/37810) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generation應透過環境變數設定

修正後，「MAGENTO_DC_CACHE_ALLOW__PARALLEL_GENERATION」環境變數可用來設定「allow_parallel_generation」設定。

_ACP2E-3673 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud]在Magento 2中使用db_schema.xml檔案將資料表資料行型別從Int變更為Decimal導致錯誤

變更欄資料型別無法正常運作。 之前，它會擲回錯誤：不允許屬性「identity」。

_ACP2E-3709 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

#### Adobe支援新貨幣(XCG)

加勒比盾(XCG)已新增至貨幣清單。

_ACP2E-3790 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

#### 由於新增驗證，因此與升級2.4.7-p5有關的問題

修正SchemaBuilder類別中，未定義的陣列索引鍵「欄」在結構描述建立或更新期間當機的問題。 處理不包含「欄」索引鍵的表格資料時，就會發生此問題。

_ACP2E-3871 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]伺服器問題可能是由無效的S3存取金鑰所造成

不正確的AWS S3憑證不會再導致頁面無限期地載入店面。

_ACP2E-3890 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [雲端] Minify js無法運作

下列JS檔案現在會在啟用JS縮制時完全且正確地縮制： mage/backend/tabs.min.j、jquery/jquery.validate.min.js和Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js。 因此，頁面產生器CSS類別欄位驗證會如運期般運作。

_ACP2E-3925 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4淘汰錯誤：升級至Adobe Commerce 2.4.8後出現E_USER_ERROR

*不需要發行說明*
針對客戶的案例不會受到此修正的影響。

_ACP2E-3963 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron工作未清除資料庫表格 — 造成Galera當機造成中斷

變更記錄檔表格清理目前正在批次執行，以避免大量的刪除作業。

_ACP2E-3995 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### 未縮制的JS有時會忽略「啟用js縮制」而載入

在修正前，即使您已啟用縮制，仍會請求部分JS檔案而沒有「min」首碼，導致404狀態代碼。 修正後，啟用縮制時，未要求非縮制的JS資源。

_ACP2E-4058 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 自訂屬性群組中的日期屬性無法在管理員中顯示日期選擇器

修正指派給自訂屬性群組時，日期屬性的行事曆快顯視窗會出現在畫面外的問題。

_ACP2E-4060 - [GitHub問題](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 生產ACL許可權檢查導致效能降低 — populateAcl方法是瓶頸

最佳化的ACL規則處理

_ACP2E-4114 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98f028ab)_

#### 使用AC-15867 + ACP2E-4296和SCD壓縮功能，簽出時未載入最新版本

在修正之前，透過head區段載入自訂JavaScript可能會導致問題。 匯入新設定後，這些指令碼會自動延遲，以確保與Magento 2框架有更大的相容性。

_ACP2E-4319 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1c547060)_

#### 棄用警告：使用moment.updateLocale(localeName， config)變更現有的地區設定。 moment.defineLocale(localeName， config)

修正前，瀏覽器主控台中擲回已棄用的警告。 現在，修正後，不會再顯示此類警告。

_ACP2E-4338 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2687b487)_

#### 透過REST API儲存產品變更時，[雲端]日期時區錯誤

在修正之前，如果沒有代碼為「default」的商店，則產品更新REST API請求會產生錯誤。 現在，修正後，產品更新請求可正常執行，無論「預設」存放區是否存在。

_ACP2E-4339_

#### 與MariaDB 10.11不相容

之前，使用MariaDB 10.11時，最新Magento 2版本的安裝失敗，無法完成設定程式。 此問題已透過更新資料庫相容性處理來解決，以便在安裝期間支援MariaDB 10.11.x。

_ACP2E-4367 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

### 框架，搜尋

#### 單一定價類別的Opensearch 2.19.1 illegal_argument_exception

Opensearch不再對包含所有相同價格產品的類別擲回illegal_argument_exception。 之前，它有此例外狀況&quot;[from]引數不能為負數&quot;。

_ACP2E-3896 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### 在GraphQL中下訂單成功，但送貨方法無效

修正可能透過GraphQL使用停用或無效的送貨方法下訂單的問題。
現在，系統會驗證選取的送貨方法，如果無法取得，系統會傳回錯誤，以防止建立訂單。

_AC-10472 - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38268) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a8cf637b)_

#### 執行GraphQl查詢時擲回例外狀況

修正GraphQL查詢因排序引數無效而擲回例外狀況的問題；修正後，查詢成功執行而不會產生錯誤或例外狀況記錄。

_AC-14835 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a8cf637b)_

#### 透過AddProductsToCart Mutation （包括custom_attributesV2）將禮品卡產品新增到購物車時出現內部伺服器錯誤

解決透過GraphQL使用custom_attributesV2新增禮品卡（及類似的自訂選項）產品至購物車時觸發的內部伺服器錯誤；此修正可正確處理複雜的屬性值，使得產品可以正常新增，而不會發生錯誤。

_AC-15856 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7fa400a7)_

#### `Country`查詢中有Null欄位

修正包含虛擬、已退款及已出貨料號的訂單仍在處理中的問題，方法是確保將虛擬料號納入出貨數量計算，讓訂單狀態正確轉換以完成。

_AC-7731 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ef666cd9)_

#### 具有「number」屬性的GraphQL查詢「customerOrders」導致內部伺服器錯誤

修正GraphQL customerOrders查詢在要求數字欄位時傳回內部伺服器錯誤的問題。
現在，解析程式會正確傳回訂單增量ID，讓查詢成功執行並擷取訂單編號。

_AC-8949 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3b5ac075)_

#### GraphQL對訂單位置的回應不包含例外訊息

還原先前以不同格式傳回錯誤的變更。 現在系統會以一致的方式傳回潛在錯誤，而不會破壞GraphQL結構描述。 此資訊應新增為已知的BIC，由PM核准，網址： https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_

#### 訂單放置的GraphQL回應已部分本地化

placeOrder GraphQl突變傳回的錯誤未完全本地化。 現在，在多語言內容中，錯誤會正確翻譯。

_ACP2E-3506 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9608ca21)_

#### 同時呼叫以重新排序GraphQL API — 將相同產品新增至不同列

修正同時呼叫重新排序GraphQL API導致相同產品新增為不同列，進而導致資料不一致的問題。

_ACP2E-3774 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL突變（變更電子郵件地址）未觸發電子郵件通知

以往，成功更新客戶帳戶上的電子郵件地址後，系統不會傳送電子郵件給客戶。 套用修正後，客戶現在會在成功更新電子郵件地址後收到電子郵件通知。

_ACP2E-3785 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### 動態屬性未透過updateGiftRegistry變異在Gift登入中更新

之前，在透過updateGiftRegistry變異進行此修正之前，贈品登入的自訂屬性並未透過GraphQL變異進行修改或更新。 套用此修正後，可以透過updateGiftRegistry變異成功更新贈品登入的動態屬性。

_ACP2E-3805 - [GitHub問題](https://mcstaging.briscoes.co.nz/)_

#### 刪除產品時customerOrders graphql傳回錯誤

即使訂單中的產品已刪除，customerOrders graphql請求也不再擲回錯誤。 之前，系統擲回「內部伺服器錯誤」錯誤。

_ACP2E-3936_

#### 客戶訂購GraphQL ：擷取關聯產品的產品類別「無法個別顯示」

在修正之前，如果訂單包含隱藏產品，則其類別會在客戶訂單GraphQl回應中顯示空白陣列。
現在，修正後，產品類別會包含在客戶訂單GraphQl請求的回應中，即使產品已隱藏。

_ACP2E-3945 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 在GraphQL要求中，願望清單專案不會在單一網站的商店檢視之間共用

在修正前，會依存放區ID篩選願望清單專案。 現在，修正後，願望清單專案會依網站篩選。

_ACP2E-3987 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a252ae6)_

#### [雲端] getRemoteAddress在生產環境中傳回127.0.0.1

在此修正之前，使用應用程式伺服器時，無法正確判斷遠端位址。 修正之後，遠端位址會適當地結合nginx中的適當標題設定和標題設定。

_ACP2E-3991 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS]確認GQL訂單放置例外狀況處理行為回覆

已處理placeOrder突變的回溯不相容變更。

_ACP2E-4031 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### 透過GraphQL下訂單時，將翻譯的訊息對應到錯誤碼的問題

修正使用轉譯的例外狀況訊息來對映GraphQL要求的錯誤碼時，導致未知錯誤碼的問題。

_ACP2E-4033 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fab20b00)_

#### [雲端]客戶訂單篩選器不適用於日期

修正後，使用日期範圍篩選器透過GraphQL擷取訂單，會傳回正確結果。

_ACP2E-4090 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 解決ACP2E-4031中提出的問題

在修正之前，錯誤節點位置未提供與2.4.7和2.4.9版本的無縫相容性。 現在，在修正之後，錯誤節點會正確放置以容納兩個版本。

_ACP2E-4115 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

#### 組合父項顯示無庫存，即使子項已在Graphql呼叫中插入

修正後，使用GraphQL請求產品清單會傳回套件組合產品的正確庫存狀態。

_ACP2E-4168 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5632fb5e)_

#### SWAT中的GraphQL例外狀況

修正後，GraphQL要求的回應會透過HTTP規格與GraphQL對齊。 當無法剖析請求、請求未獲授權或請求有另一個一般問題時，會傳回4XX回應代碼。 如果要求經過剖析且能處理，則會傳回200回應代碼。

_ACP2E-4194 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 將清單指派給客戶後，不會從比較清單中移除產品

將訪客使用者的比較清單指派給客戶帳戶後，客戶現在可以移除新增為訪客的產品。
之前，移除作業會失敗，因為指派後，訪客新增的專案未正確連結至客戶的帳戶。

_ACP2E-4244 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c135fc3a)_

#### updateCartItems GraphQL不正確的錯誤回應

先前，針對數量不足的料號提出graphQL請求時，即使料號無法使用，也會傳回包含錯誤碼的正確錯誤訊息，以及請求的數量與價格計算。 套用此修正後，現在會傳回包含錯誤碼的正確錯誤訊息，如果回應中無法使用專案，則會將專案的數量設定為舊值。

_ACP2E-4283 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cbca0396)_

#### MergeGuestOrder外掛程式中的跨網站訪客訂單指派錯誤

修正前，訪客訂單客戶指派未考慮帳戶共用選項。 現在，修正後，如果客戶與訂單商店相符（假設客戶帳戶共用選項設為「每個網站」），則會將訂單指派給客戶。

_ACP2E-4312 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL、詳細目錄/MSI

#### Magento 2 GraphQL中only_x_left_in_stock的問題 — 使用臨界值時計算不正確

修正only_x_left_in_stock GraphQL欄位因為MinQty的雙重扣除不正確而傳回null的問題；計算已修正，現在會根據臨界值傳回準確的庫存值。

_AC-15832 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/35458c7f)_

#### GraphQL mergeCart變異差異

修正後，合併購物車GraphQL請求會考量庫存設定，正確檢查產品數量。

_ACP2E-4184 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL，產品

#### MediaGalleryInterface中的產品graphql缺少media_type

MediaGallery GraphQL要求現在包含產品影像型別的「型別」欄位。 之前，此「型別」欄位不存在於MediaGallery GraphQL請求中。

_ACP2E-3880 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL，安全性

#### 透過GraphQL重設客戶密碼未遵守限制

解決透過GraphQL變動提出的客戶密碼重設請求不符合存放區>設定>客戶>客戶設定>密碼選項下設定的密碼重設限制的問題。 系統現在會正確強制執行這些設定。

_ACP2E-3992 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

### 匯入/匯出

#### [問題]修正引數型別

修正匯入/匯出模組中引數型別不符的問題，也就是先前定義的字串值現在會正確設為陣列。 這符合匯出控制器的預期輸入，並防止靜態分析警告。

_AC-11665 - [GitHub問題](https://github.com/magento/magento2/issues/38529) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64823f95)_

#### [問題] Copyedit：將「coping」變更為「coping」

PR修正「複製」的次要拼字錯誤

_AC-13300 - [GitHub問題](https://github.com/magento/magento2/issues/39311) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39307)_

#### REST端點產品匯入Json未驗證必填欄位

透過匯入程式（管理員或API）建立新產品時，現在需要名稱欄位。 修正前，您可以建立沒有名稱的新產品，這會破壞管理員介面，並建立無效產品。

_ACP2E-3660 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

#### 匯出程式中缺少網站篩選器選項

現在可在建立產品匯出時依網站篩選產品。

_ACP2E-3720 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

#### AC-13913重複 — 靜態屬性非同步清除。

修正後，建立\Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType的許多執行個體時，不會出現「未定義的陣列索引鍵&quot;apply_to&quot; （套用至）」錯誤。

_ACP2E-3752 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

#### Csv產品匯入：無法取消設定色票影像

修正前，您無法透過產品匯入更新產品的色票影像。 現在，修正後，如果您以設定的空白標籤標籤產品色票影像欄，影像將會設定為隱藏。

_ACP2E-3972 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 產品匯入為存放區範圍產生空白URL

如果匯入資料來源中的url_key有空白值，存放區檢視中的產品URL金鑰現在會繼承預設範圍中設定的值。 先前若將存放區檢視記錄的匯入資料來源中的url_key設定為空值，會導致該範圍中的url_key被空值覆寫。

_ACP2E-4038 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### 如果視需要設定多選屬性，則產品匯入程式會遇到錯誤

解決當包含多選型別的必要屬性時，產品匯入失敗的問題。 資料驗證現在可正確通過，讓產品匯入程式成功完成。

_ACP2E-4057 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD]未選取延交訂單的產品在管理庫存時，仍允許客戶在匯入時訂購超過庫存水準的商品

修正後，無法再為產品的「allow_backorders」屬性匯入無法接受的值。

_ACP2E-4116 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 產品匯入失敗，因為說明長度超過65,536個字元驗證

修正後，可匯入文字值超過65,536個字元的產品屬性。

_ACP2E-4119 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 匯出產品的篩選器是 — 否屬性未如預期運作

修正後，依「是/否」屬性篩選的匯出產品會包含遵循套用篩選器的預期產品。

_ACP2E-4160 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ee918f0d)_

#### 透過「匯入」更新每個網站的套件選項價格時發生問題

現在可以匯出和匯入每個網站的套件組合選項選取價格

_ACP2E-4243 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98f028ab)_

#### 無法匯入電子郵件地址為大寫的客戶

修正當「帳戶共用」設定為「全域」時，匯入具有大寫電子郵件的客戶時，未定義的陣列金鑰錯誤。 電子郵件標準化現在在整個匯入過程中保持一致，以確保無論電子郵件案例為何，都能匯入客戶。 網站層級的帳戶共用行為維持不變。

_ACP2E-4373 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

### 匯入/匯出，客戶/客戶

#### 管理員可匯入出生日期晚於目前日期的客戶

修正管理員可匯入出生日期設定在未來之客戶的問題。 系統現在會在匯入期間驗證DOB、顯示無效記錄的錯誤，並防止匯入具有未來出生日期的客戶，以確保準確的客戶資料。

_AC-13641 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

### 庫存/MSI

#### 結帳時變更地址時，商店取貨未遵守搜尋半徑上限

現在，如果送貨地址變更，「店內撿料」中預先選取的商店將會更新。 以往，預先選取商店後，即使新送貨地址不在所選商店半徑內，也不會變更

_ACP2E-3728 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/07620383)_

#### 重新導向至首頁並結帳後，沒有可用的存放區

如果客戶導覽至付款頁面，然後返回首頁，最後返回結帳頁面，則先前選取的商店現在會在「店內撿料」配送中預先選取。 先前，在重複回到結帳頁面後，系統會清除「取用商店」中選取的商店。

_ACP2E-3793 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/62c0d79b)_

#### 庫存刪除作業未完成

修正後，刪除來源專案並不會導致完全重新索引，而僅更新會影響產品以提高效能。

_ACP2E-3917 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] Admin中沒有指示是否已以非同步方式通知客戶訂單已準備好取貨

已新增至訂單歷史記錄通知中，該通知有關於客戶已準備好取貨的非同步通知

_ACP2E-3968 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/29653b1d)_

#### 報價載入時重複的庫存狀態查詢

修正在店面載入報價時，cataloginventory_stock_status查詢的重複執行，導致重複的DB呼叫。

_ACP2E-4102 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/fc15a9ae)_

#### 修補後ACP2E-4118：管理員中的庫存臨界值變更導致可銷售數量負值和庫存狀態不符

當透過匯入更新全域存貨組態「數量」、「延期交貨」及「缺貨臨界值」時，存貨存貨狀態現在會自動調整。

_ACP2E-4142 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5632fb5e)_

#### 更新詳細目錄時，[雲端]管理報告未顯示詳細資訊

記錄模組現在正在記錄產品詳細目錄來源變更。 修正前，儲存產品並執行庫存相關變更時，系統沒有記錄詳細資料。

_ACP2E-4167 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cbca0396) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/76b88f7c)_

#### 當標籤為有庫存時，捆綁產品無法新增到購物車

組合產品庫存狀態現在可以正確反映子產品預留和缺貨臨界值。
以前，即使一個或多個子產品缺少足夠的可銷售數量，套件產品也會標示為「庫存」。 當將套件組合新增至購物車時，這會導致「沒有足夠的專案可供銷售」錯誤。

_ACP2E-4220 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cbca0396) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/76b88f7c)_

#### 將子項指派給自訂來源/庫存時，若從CSV匯入後，已分組的產品在PDP上不正確地顯示為「無庫存」（在手動重新索引後修正）

修復後，使用匯入建立複合產品會自動執行坯件重新索引，使產品無需手動重新索引即可使用。

_ACP2E-4233 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98f028ab) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI]與最新主線變更相關的MFTF測試失敗。

在固定客人的前，選擇沒有運送地址的「店內取貨」時，他們的帳單地址會自動填入商店地址，而此地址無法變更，導致發票詳細資料不正確。 在修正帳單地址之後，此情境中現在可以編輯，讓來賓輸入自己的詳細資料。 註冊的使用者將會看到他們儲存的帳單地址，而不是商店的地址。

_ACP2E-4260 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ab891304) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/13e432a6)_

#### 為虛擬禮品卡建立的存貨預留不正確

在實施此修正之前，包含多個專案的虛擬禮品卡數量未準確地反映在存貨預訂中。 不過，套用修正後，存貨預留和存貨的數量會同步化。

_ACP2E-4267 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5704166a)_

#### 存貨預留補償命令因Null和不存在的產品參考而失敗

修正當處理的組合遺失訂單識別碼時，存貨預留補償CLI會擲回例外狀況的問題

_ACP2E-4301 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/76b88f7c)_

#### 變更SKU包裝盒後產品無庫存

修改SKU案例不會再造成店面無庫存。

_ACP2E-4375 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/0836c2ed)_

#### 具有無效資料的「依價格/價格」Facet排序

在修正之前，當子產品在自訂來源底下有存貨時，捆綁價格未正確編列索引。 現在，修正後，無論子產品庫存指派為何，都會正確編制套裝價格的索引。

_ACP2E-4380 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1c547060) - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/1f83ed24)_

#### 在中繼更新期間SKU變更後，庫存狀態錯誤地重設為具有數量的庫存

現在已禁止具有使用中排程更新的產品進行SKU變更；儲存將失敗並出現明確錯誤，並且在使用中更新期間會停用管理員SKU欄位。 這可防止在預備倒回期間，SKU變更所導致的MSI詳細目錄不一致。

_ACP2E-4389_

### 訂購

#### AbstractAddress setData(&#39;custom_attributes&#39;， AttributeValue[])中斷customAttributes

現在，在結帳和API作業期間，可正確處理位址上的自訂屬性。
以前，使用$address->setCustomAttributes(&#39;custom_attributes&#39;， $attributes)可能會中斷自訂屬性處理，導致屬性值結構不正確。
AC-10568

_AC-10568 - [GitHub問題](https://github.com/magento/magento2/issues/31644)_

#### 當客戶設定為報價單時，仍為客服訂單

_AC-11689 - [GitHub問題](https://github.com/magento/magento2/issues/38540)_

#### 混合虛擬、已退款及已出貨料號時，訂單未完成

修正包含虛擬、已退款及已出貨料號的訂單仍在處理中的問題，方法是確保將虛擬料號納入出貨數量計算，讓訂單狀態正確轉換以完成。

_AC-11691 - [GitHub問題](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento重新排序–1訂單編號

系統如預期般運作，從後端重新排序後，訂單編號將是8位數的唯一值

_AC-12854 - [GitHub問題](https://github.com/magento/magento2/issues/39089) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39399)_

#### 使用Adobe信用卡付款方式結帳時，產品自訂選項檔案上傳遺失

使用Adobe信用卡付款方式結帳時，現在會保留產品自訂選項檔案上傳。
以前，使用此付款方式時，檔案上傳會遺失，但與其他方式搭配使用。
AC-14306

_AC-14306 - [GitHub問題](https://github.com/magento/magento2/issues/39647)_

#### 管理員訂單 — 無法搜尋Will

修正在「管理訂單」格線中依客戶名稱（例如「Will」）搜尋訂單時，未傳回任何結果的問題。 修正後，若依客戶名稱篩選，系統則會正確顯示相關訂單。

_AC-14360 - [GitHub問題](https://github.com/magento/magento2/issues/36596) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL — 訂購專案order_date格式錯誤

修正GraphQL回應中的order_date欄位傳回yyyy-mm-dd格式的問題。
現在，order_date以dd-mm-yyyy格式正確顯示。

_AC-14431 - [GitHub問題](https://github.com/magento/magento2/issues/39805) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 無法為不可為空的欄位\&quot;AppliedCoupon.code\&quot;傳回null非預期的問題

Adobe Commerce現在會在查詢客戶訂單時，透過GraphQL正確傳回套用的優惠券代碼。 先前，在Adobe Commerce 2.4.8中，使用applied_coupons.code欄位（例如透過customer.orders查詢）擷取訂單可能會失敗，並出現內部伺服器錯誤，且訊息「無法針對不可為空的欄位「AppliedCoupon.code」傳回null，而applied_coupons是以[null]傳回，而非包含優惠券代碼的清單。 AC-14484

_AC-14484 - [GitHub問題](https://github.com/magento/magento2/issues/39841) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/97b2ea42)_

#### 儘管已在商店設定中啟用，但從管理員訂單檢視提交時仍不會傳送出貨電子郵件

系統現在會傳送出貨確認電子郵件，因為它已在下訂單的商店設定中啟用。

_AC-14563 - [GitHub問題](https://github.com/magento/magento2/issues/39861) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39897)_

#### 由於欄位名稱模稜兩可，日期篩選無法運作

在Magento 2.4.7-p6中，依日期篩選訂單格線會回報由於與Braintree模組的結合而造成錯誤。
該問題涉及在套用日期篩選器時聯結braintree_transaction_details和sales_order表格的查詢。
Adobe Commerce工程部門已檢閱此案例，但無法在環境中重現錯誤。
預期行為是依日期篩選應該會傳回符合篩選器的訂單，而不會發生錯誤。

_AC-15037 - [GitHub問題](https://github.com/magento/magento2/issues/40024)_

#### 若有多項產品在後台建立訂單，且其中至少一項包含自訂選項，會導致多餘的產品加入訂單

修正在Backoffice中使用多個產品（包括含有自訂選項的產品）、無意中新增額外產品並造成錯誤而建立訂單的問題。 系統現在只會新增選取的產品，以便建立訂單，而不會出現任何未預期的專案。

_AC-15286 - [GitHub問題](https://github.com/magento/magento2/issues/40122) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2：無法建立促銷活動規則

此PR修正，我們收到
\Magento\Catalog\Model\ResourceModel\Eav\Attribute模型，而不是\Magento\SalesRule\Model\Rule\Condition\Product：：loadAttributeOptions方法中的\Magento\Catalog\Model\ResourceModel\Eav\Attribute

_AC-15358 - [GitHub問題](https://github.com/magento/magento2/issues/12176) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/30479)_

#### Magento在呼叫$invoice = $this->_invoiceService->prepareInvoice($order)後變更了$order的實體型別；

修正編輯子類別的現有排程更新時，資料庫中父類別的children_count會不正確地增加的問題。 儲存更新後，問題導致不正確的類別階層資料。 修正後，子系計數保持正確且不再意外增加。

_AC-15401 - [GitHub問題](https://github.com/magento/magento2/issues/40154)_

#### 如果料號部份退款，則出貨後的訂單會維持在「處理」狀態

修正部份退款專案並出貨剩餘專案後，訂單仍處於「處理」狀態的問題。 當出貨與退款數量總計符合已開立商業發票的數量時，訂單狀態現在會正確更新為「完成」，以確保訂單生命週期管理正確無誤。

_AC-15419 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cc0ec250)_

#### 從後端傳送銷售電子郵件一律會有成功，在停用時也是如此

已修正後端銷售電子郵件通知，藉由驗證電子郵件服務結果來顯示正確的訊息，確保在訂單或發票電子郵件停用且未傳送時通知使用者。

_AC-16059 - [GitHub問題](https://github.com/magento/magento2/issues/40309) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 無法為指派給新網站和來源的產品建立請購單清單

修正啟用「將商店代碼新增至URL」時，無法為指派至新網站和來源的產品建立請購單清單的問題。 發生問題是因為從API請求中剝離存放區程式碼，導致未獲授權的錯誤。 修正之後，會保留正確的存放區內容，並成功建立請購單清單。

_AC-16226_

#### 自訂價格0會在重新訂購時重設為原始價格。

修正自訂價格為0的產品在重新訂購期間恢復為原始價格的問題。
現在，自訂價格可正確保留，確保重新排序專案時可正確定價。

_AC-8147 - [GitHub問題](https://github.com/magento/magento2/issues/36970) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/01cee3c3)_

#### 停用付款方式運作下的下單

修正可透過GraphQL以停用的付款方式下訂單的問題。
現在，當嘗試設定或使用無法使用的付款方式時，會傳回錯誤，導致無法建立訂單。

_AC-9605 - [GitHub問題](https://github.com/magento/magento2/issues/37983) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a8cf637b)_

#### [雲端]升級至magento 2.4.6-p7後，部分內嵌Javascript無法運作

按一下admin中「按SKU新增至訂單」中的「刪除」按鈕現在會移除SKU。 之前，按一下「依SKU新增至訂單」中的「刪除」按鈕並未移除SKU。

_ACP2E-3515_

#### gift_cards序列化資料在sales_order表格中不一致

sales_order表格中的gift_cards資料現在已正確序列化。 以前，每次更新訂單時都會序列化。

_ACP2E-3662_

#### 訂單狀態卡在處理中

修正前，當訂購啟用「一併送貨」選項的套件組合產品時，訂單狀態在發票和送貨後不會自動切換為「完成」。 現在，修正之後，訂單狀態會在開立商業發票並出貨後，自動切換為「完成」。

_ACP2E-3947 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a252ae6)_

#### [雲端]Magento OOTB程式碼 — 電子郵件範本設定問題

修正前，使用非同步電子郵件傳送時，出貨電子郵件與商店訂單不一致。 現在，修正後，適當的商店出貨電子郵件訂單已送達。

_ACP2E-3998 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

#### 取消商業發票重新導向至404

取消以「非擷取」型態開立的商業發票時，不會再產生第404頁。

_ACP2E-4001 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 銷售封存Cron工作造成資料庫鎖定問題

在修正之前，位於封存cron順序中的未繫結DELETE查詢導致Galera發生問題。 現在，更新後，刪除查詢的執行會受到限制。

_ACP2E-4010_

#### 使用REST API時可設定選項的更新訂單問題

透過rest api端點更新訂單時，保留銷售訂單專案上的現有產品選項。

_ACP2E-4061 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 禮品卡電子郵件不會使用商店特定寄件者

先前，當從其他商店建立發票後傳送禮品卡的電子郵件範本時，管理員組態設定中的擁有者名稱不會在客戶收到電子郵件時反映在電子郵件標題中。 套用此修正後，電子郵件標題現在會包含適當商店所有者的電子郵件資訊。

_ACP2E-4310_

#### 非同步銷售依ID插入限製為每個cron執行最多100個專案

改善銷售格線非同步插入的處理。 一個cron執行現在會以批次插入所有待處理列，而不是每次執行嚴格為100。

_ACP2E-4360 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/31258bf6)_

#### 錯誤訊息「ID為「1」的產品不存在。」 重複記錄在exception.log中

修正之前，在「上次訂購的專案」區段中遇到已刪除的產品時，會記錄嚴重錯誤。 修正後，商家可以設定是否要透過di.xml中的`skipDeletedProductLogging`引數記錄或略過已刪除的產品。 依預設，為了回溯相容性，行為保持不變，但商家可以將引數設定為`true`，以無訊息地跳過已刪除的產品，並防止記錄雜訊。

_ACP2E-4366 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

#### 針對第二筆銷退折讓單退款的雙重稅捐

在從訂單檢視頁面建立先前的銷退折讓單之後，從商業發票建立部份退款時，修正銷退折讓單中錯誤的稅捐計算。

_ACP2E-4384 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

### 訂單，定價

#### 管理員在建立退貨時顯示不正確的貨幣符號

在使用不同貨幣(EUR/USD/GBP)進行多網站設定時，admin中的退貨產品選擇頁面現在顯示正確的貨幣符號。 之前，它會顯示預設貨幣符號。

_ACP2E-3658 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

### 訂購，退貨

#### 建立離線退款的銷退折讓單時發生錯誤

修正以設定「動態價格=否」為組合產品建立銷退折讓單失敗的問題。 現在可以順利建立銷退折讓單而不會發生錯誤。

_ACP2E-4157 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45cbf9b6)_

### 其他

#### 無法將「將獎勵點數餘額限制在」的值留空 — 已儲存

Adobe Commerce現在可讓商戶將「上限獎勵點數餘額」欄位留空，同時仍設定「獎勵點數餘額兌換臨界值」。 先前，當在「商店>設定>客戶>獎勵點數」下設定獎勵點數時，為獎勵點數結餘贖回臨界值輸入正數，並將上限獎勵點數結餘保留為空白，則會觸發驗證錯誤：「上限」獎勵點數結餘無效。 餘額必須為正數或留空。 驗證並再試一次。」，以防止商家儲存沒有限制的設定。 ACP2E-3977

_ACP2E-3977_

### 其他開發人員工具

#### [問題]受保護成員$_urlHelper的型別提示錯誤

系統現在會以正確的提示來修正錯誤的型別提示，建構函式中也會使用這個提示

_AC-10716 - [GitHub問題](https://github.com/magento/magento2/issues/32503) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32496)_

#### [問題]正在清除未使用的程式碼。

系統現在會移除有關未使用匯入的未使用程式碼。

_AC-10980 - [GitHub問題](https://github.com/magento/magento2/issues/38424) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33499)_

#### Lighthouse協助工具失敗

系統現在通過測試，無障礙分數為100

_AC-12783 - [GitHub問題](https://github.com/magento/magento2/issues/39054) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39164)_

#### 停用captcha storefont設定仍載入captcha js檔案

停用驗證碼時，系統現在不會載入驗證碼js檔案
適用於storefont

_AC-14267 - [GitHub問題](https://github.com/magento/magento2/issues/32987) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39154)_

#### [問題]協助工具：功能表中的WAI-ARIA角色巢狀錯誤

系統現在產生Lighthouse協助功能，且WAI-ARIA角色在功能表錯誤中不會巢狀錯誤，報告應為綠色

_AC-15082 - [GitHub問題](https://github.com/magento/magento2/issues/40045) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38617)_

#### 在Magento管理員中預覽電子郵件時出現控制檯錯誤

預覽電子郵件範本時，系統不會擲回任何主控台錯誤

_AC-9245 - [GitHub問題](https://github.com/magento/magento2/issues/37820) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37933)_

### 付款/付款方法

#### 在後端成功設定時，Paylater訊息未顯示在店面

修正即使在後端設定PayPal Pay Later訊息，卻未在「首頁」和「購物車」頁面上顯示的問題。 當買家國家/地區對沒有預設地址的來賓或客戶為Null時，橫幅無法呈現。 修正之後，稍後付費訊息會在店面正確顯示。

_AC-12335 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/528af81a)_

### 付款

#### [問題]修正離線發票擷取(404)

它會修正從Magento管理員擷取離線付款方法發票時的404頁錯誤

_AC-13336 - [GitHub問題](https://github.com/magento/magento2/issues/39298) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39297)_

#### 來自PayPal的未知IPN濫用應用程式IPN處理器

IPN處理常式現在會忽略不支援或不明的IPN型別。 它會記錄問題並繼續處理，而不會傳回500錯誤，不會造成中斷。

_ACP2E-4049 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro儲存的卡片權杖付款時失敗

PayPal PayFlow Pro交易ID (PNREF)現在可在12個月的固定期間內用於參考交易。 一旦過期，已儲存的卡片將不再顯示，且必須重新新增。 以前，有效性取決於原始交易中使用的付款卡的到期日。

_ACP2E-4064 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### 對管理員下訂單時出現存放卡問題

將預存信用卡的訂單放置在具有不同付款動作設定的網站下，不會再導致錯誤或錯誤的交易型別

_ACP2E-4270 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [雲端] PayflowPro儲存的卡片（儲存庫）最後4位數的順序未顯示

現在，將已儲存的卡與「銷售」付款動作搭配使用時，卡資訊會適當地保留和顯示，符合對PayflowPro使用「授權」付款動作時的行為。

_ACP2E-4346 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a3b7032)_

### 效能

#### [問題]更新Store.php

此PR會略過目前的商店解析度，進而改善效能。

_AC-14791 - [GitHub問題](https://github.com/magento/magento2/issues/39949) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38717)_

#### [問題]靜態網站的更新使用快取控制不可變

此PR新增了效能改善，方法是在&amp;變更之前，不驗證每個頁面載入上的靜態內容。

_AC-15171 - [GitHub問題](https://github.com/magento/magento2/issues/39486) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39484)_

#### [問題]快取isCacheable呼叫的結果以提升效能

此PR為isCacheable()方法新增快取，導致版面配置轉譯程式減少多餘的檢查，並改善整體頁面轉譯效能。

_AC-16054 - [GitHub問題](https://github.com/magento/magento2/issues/40156) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40112)_

#### [問題]非同步順序格線處理的效能微幅改善

此PR將暫時的快取型last_updated_at查閱取代為儲存在標幟表格中的永續性DB支援標幟，藉此為Magento的非同步順序格線處理引入效能最佳化。 這可確保系統一致地保留上次處理的時間戳記，即使在快取排清或部署後也是如此，以防止對大型sales_order資料集進行不必要的完整表格掃描。 因此，非同步格線更新會變得更有效率且更可預測，尤其是在經常訂購活動的大量存放區中。

_AC-16109 - [GitHub問題](https://github.com/magento/magento2/issues/40282) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40271)_

#### 類別許可權模組可能會阻止快取

第三方控制器現在會與客戶區段正確快取

_ACP2E-3721_

#### [雲端]無法新增產品至類別

改善透過Visual Merchandiser將產品新增至類別時的效能。

_ACP2E-3946 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/29653b1d)_

#### [雲端]快取無效超過10K個記錄

之前，在每次進行PLP或購物車造訪時都會清除快取，造成不必要的效能額外負荷。 Target規則快取不再在這些頁面上失效，進而改善瀏覽效率。

_ACP2E-4059_

#### [雲端] php-fpm未遵守max_execution_time

部署設定現在會在單一請求中載入一次。

_ACP2E-4201_

#### ACP2E-3995之後的變更記錄檔清理效能問題

修正後， indexer_clean_all_changelogs cron作業會完全清除變更記錄檔，並保持批次處理。

_ACP2E-4211 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD] Fastly快取在升級至2.4.8後無法運作

解決無法正確儲存可快取頁面，或從Fastly快取提供可快取頁面，導致不一致的快取行為並降低效能的問題。

_ACP2E-4324 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2687b487)_

#### 調查增加redis金鑰和快取金鑰建立的原因

在修正之前，用於遠端儲存中繼資料的快取鍵不會到期。 現在，修正後，您可以透過相依性插入為此等快取金鑰設定TTL。

_ACP2E-4345 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a3b7032)_

### 定價

#### Order Rest API中，沒有動態價格的套件組合產品專案的價格一律為0

Order REST API現在會傳回組合產品專案的正確價格，而不會有動態價格。
先前，透過REST API匯出訂單時，未動態訂價的套件產品專案價格一律會傳回為0，而非套件頁面上顯示的實際價格。
AC-11925

_AC-11925 - [GitHub問題](https://github.com/magento/magento2/issues/38687) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7da46f52)_

#### 建立時指派給價格屬性的範圍不正確

修正無論設定為何，新建立的價格屬性皆未正確指派至「商店檢視」範圍的問題；修正後，屬性範圍現在預設會與「目錄價格範圍」設定（「全域」或「網站」）一致。

_AC-14945 - [GitHub問題](https://github.com/magento/magento2/issues/39986) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

#### 即使使用整批作業的「起始特殊價格日期」晚於「終止日期」，也會儲存產品

修正以無效的特殊價格日期範圍儲存產品卻未經驗證的問題。
現在，會顯示錯誤訊息：「請確定[截止]日期晚於或與[起始]日期相同。」

_AC-15252 - [GitHub問題](https://github.com/magento/magento2/issues/40113) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 完成可轉讓報價的Paypal Express結帳後，出貨詳細資料不符。

此問題修正了完成核准可轉讓報價的PayPal Express結帳時，運費不符的問題。
在修正前，運費錯誤地加倍（顯示$10而不是$5），導致總數膨脹。
Magento 2.4.9-alpha3中的修正可確保套用正確的運費

_AC-15280_

#### 以不同時區建立的網站則不考慮特別價格

在此修正之前，特殊價格日期有效性是在目前商店時間戳記的範圍內建立。 現在，修正後，會考量預設存放區時區。

_ACP2E-4002_

#### 即使套用特殊價格，一般價格仍不會顯示。

解決套用特殊價格時未顯示一般價格的問題。 一般價格現在會如預期正確地與特殊價格一起顯示。

_ACP2E-4100 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47721be6)_

### 產品

#### 前端有不良行為的可設定產品

修正當包含色票屬性時，可設定產品會顯示錯誤前端行為，導致定價、下拉式清單版面配置和必要欄位指標顯示錯誤的問題。
現在，可設定的產品可透過適當的定價、對齊的下拉式清單和預期的UI行為正確轉譯。

_AC-1014 - [GitHub問題](https://github.com/magento/magento2/issues/14296) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ef666cd9)_

#### 當可設定的產品指派給測試庫存和測試網站，並啟用顯示缺貨產品的選項時，價格判斷提示字串不符

更新失敗測試，以在所有子產品具有相同價格時，符合可設定產品的實際定價行為。
判斷提示現在可正確驗證顯示的價格，防止測試失敗而不會影響功能。

_AC-10843 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/1ccc786b)_

#### 測試案例AC-6158的可設定產品仍會顯示「最低」標籤

實作並驗證可設定的產品(P1-P7)具有各自的變數和類別指派。 已確保類別C下產品的店面價格顯示正確及「最低」標籤行為。

_AC-10847 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 依原始價格計算的層級價格與型錄價格規則的折扣百分比（不含選取的選項）。

層級價格和目錄價格規則的百分比折扣現在包含所選的自訂選項。
以前，在計算原始產品價格的百分比折扣時不會考慮所選的自訂選項，導致最終價格不正確。
AC-12004

_AC-12004 - [GitHub問題](https://github.com/magento/magento2/issues/38750)_

#### [問題]驗證評等無法運作，評論評等選擇器已變更

修正由於選取器變更而未觸發稽核評等驗證的問題。 以前，您無需選取評分即可儲存評論。 修正後，驗證可正常運作，且除非選取評分，否則無法儲存評論。

_AC-12686 - [GitHub問題](https://github.com/magento/magento2/issues/33424) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minAllowed遺失產品訂單數量

系統運作正常，頁面來源正確顯示產品的最低數量

_AC-12909 - [GitHub問題](https://github.com/magento/magento2/issues/39142) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39480)_

#### 產品集合 — 可能或將載入集合時，addMediaGalleryData呼叫getSize （可以使用count避免額外的DB查詢）

如果在呼叫產品圖形ql時已載入產品集合，且其中包含media_gallery欄位，此PR會減少使用count()的額外查詢呼叫。

_AC-13055 - [GitHub問題](https://github.com/magento/magento2/issues/39111) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39681)_

#### Magento中連結產品的SKU處理無效

修正由於SKU驗證無效，無法將SKU為「0」的產品連結為相關、向上銷售或交叉銷售專案的問題。 此更新可確保這些產品可成功連結，讓產品儲存時不會發生錯誤。

_AC-13311 - [GitHub問題](https://github.com/magento/magento2/issues/39329) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a8cf637b)_

#### 管理面板中產品頁面上的可自訂選項格線問題

使用型別下拉式清單建立可自訂選項時，系統可如預期運作

_AC-14003 - [GitHub問題](https://github.com/magento/magento2/issues/39640) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39694)_

#### 將所有產品屬性設為全域範圍時，出現管理產品頁面錯誤

修正將所有產品屬性設為全域範圍時，管理員產品編輯頁面顯示錯誤的問題。 錯誤是由空的資料庫查詢所造成，導致頁面無法使用。 修正後，產品頁面可正確轉譯，且產品可順利建立。

_AC-14011 - [GitHub問題](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8]找不到cron工作catalog_product_alert的回呼

產品警示cron工作重新命名為product_alert後，Adobe Commerce現在可正確防止排程錯誤的catalog_product_alert cron工作。 先前，在Adobe Commerce 2.4.8中，設定「存放區>設定>目錄>目錄>產品警示執行設定」 ，導致在core_config_data中建立catalog_product_alert cron專案，當cron執行時，會記錄錯誤Magento_Cron.CRITICAL：例外：即使有效的product_alert工作正常執行，仍找不到cron工作catalog_product_alert的回呼。

_AC-14494 - [GitHub問題](https://github.com/magento/magento2/issues/39800) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 請購單清單頁面列印選項無法運作

「請購單清單」頁面上的「列印」選項現在可以正確運作。
之前，按一下「列印」會產生錯誤：「應用程式執行期間發生錯誤。 如需詳細資訊，請參閱例外記錄。」
AC-14711

_AC-14711_

#### [產品比較]比較清單將無法使用

修正從不同商店檢視新增相同產品時，比較清單無法使用的問題；修正後，比較清單會正確載入並根據特定商店顯示專案。

_AC-14885 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

#### 透過存放庫請求產品失敗時產生的額外記錄

改善找不到SKU或ID時ProductRepository：：get和getById的錯誤訊息。
以前，例外不會提供關於哪個SKU或ID導致錯誤的上下文。
現在，例外狀況訊息會包含遺失的SKU或ID，有助於進行偵錯並改善開發人員體驗。
此變更不會影響API的任何功能行為。

_AC-15199 - [GitHub問題](https://github.com/magento/magento2/issues/40090) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 屬性集不存在錯誤中斷頁面

修正在URL中輸入無效的屬性集ID造成嚴重錯誤的問題；系統現在會顯示適當的錯誤訊息，指出屬性集不存在，而非中斷頁面。

_AC-15753 - [GitHub問題](https://github.com/magento/magento2/issues/40213) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a06a4a57)_

#### 退款，含負數總退款折扣

修正建立負數數量的銷退折讓單時，錯誤退款折扣金額的問題。
現在，負數量的折扣不會退款，且退款數量會正確設定為零。

_AC-9424 - [GitHub問題](https://github.com/magento/magento2/issues/37917) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ef666cd9)_

#### 透過Pagebuilder包含產品Widget時執行緩慢查詢

針對產品Widget建立（包括產品SKU）的查詢已最佳化。

_ACP2E-3449 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

#### 產品影像在新增為可設定產品時未調整大小

以前，在管理面板中透過「設定」新增的影像未遵守上傳大小上限，這可能會導致不一致和管理挑戰。 現在，已實作修正，以確保在上傳期間自動調整影像大小，以符合大小上限，精簡程式和維護系統標準。

_ACP2E-3504 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/df92debe)_

#### 來自其他客戶比較清單的所有專案在透過管理員登入後都會指派給客戶

先前，當管理員在後端使用「以客戶身分登入」功能時，先前登入的客戶比較清單中的產品會錯誤指派給目前模擬的客戶。  修正後，比較清單會正確載入正確登入的客戶。

_ACP2E-3818 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

#### 當可設定的產品由受限角色編輯時取消指派簡單產品

在此修正之前，如果受限制的管理員使用者將儲存包含管理員使用者無權存取的簡單產品的可設定產品，則會在儲存時從可設定產品中移除。 修復後，可設定的產品會保留為從完整許可權管理員儲存。

_ACP2E-4081_

#### [B2B]共用目錄儲存傳回已棄用的功能錯誤

管理員可以成功從共用目錄解除指派產品。
先前從共用目錄取消指派具有大量長產品SKU的產品會導致錯誤

_ACP2E-4097 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ab891304)_

#### [雲端] Sitemap產生效能大幅降低

針對含有影像的產品產生Sitemap不再發生指數式放緩。 以前，為已啟用影像包含功能的存放區產生Sitemap會導致處理時間過長。

_ACP2E-4153 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

#### 客戶區段排序順序不一致會導致X-Magento-Vary Cookie不斷在部分頁面上重新產生

X-Magento-Vary Cookie現在會在產品頁面上設定一次，之前會針對Cookie在PDP載入期間設定多次的客戶區段進行某些設定

_ACP2E-4261_

### 產品、稅金

#### 固定產品稅(FPT)無法與可設定產品分開顯示

修正在選取選項後，未針對可設定產品個別顯示「固定產品稅」(FPT)的問題。 現在，FPT劃分會在產品清單和詳細資料頁面上正確顯示，符合簡單產品的顯示格式。

_AC-13171 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b5e99d20)_

### 促銷活動

#### 購買X取得Y購物車價格規則在已套用其他規則時新增了錯誤的折扣

修正購買X取得Y購物車價格規則使用原始產品價格計算折扣的問題，即使其他規則已將其縮減。 此更新會確保第二個規則現在會將折扣套用至調整後的價格，以便在多個促銷有效時產生準確的總折扣。

_AC-12325 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

#### 透過GraphQl客戶請求取得客戶訂單的訂單料號折扣applied_to時發生錯誤

先前當透過GraphQl針對客戶訂單套用折扣_to時觀察到內部伺服器錯誤，此錯誤現在已修正，並且已擷取套用折扣的適當客戶訂單資料

_AC-14888 - [GitHub問題](https://github.com/magento/magento2/issues/39963) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fe72c407)_

#### 透過GraphQl客戶請求取得客戶訂單的訂單專案優惠券代碼時發生錯誤

修正透過GraphQL擷取含有優惠券詳細資料的訂單時，傳回內部伺服器錯誤的問題。
現在，查詢已成功執行，並在回應中傳回正確的優惠券資訊。

_AC-14889 - [GitHub問題](https://github.com/magento/magento2/issues/39962) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fe72c407)_

#### 修正ACP2E-2926後，每個結帳請求都會比對客戶區段，造成不必要的處理

客戶區段功能現在包含快取機制以改善效能。

_ACP2E-4299_

#### [雲端][experienceleague]目錄價格規則未套用

在修正目錄價格規則之前，當`special_price`僅在網站層級設定（而不是在「所有商店檢視」）時，不會套用。 現在，在網站層級設定`special_price`時，透過先檢查網站的預設商店，在固定目錄價格規則之後可正確套用。

_ACP2E-4372 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath()缺少entity_type篩選，導致CMS頁面被視為類別URL中的產品

修正DynamicStorage未依entity_type篩選的問題，此問題導致CMS頁面在類別URL中被錯誤視為產品；格式錯誤的URL現在會正確傳回404，而非提供CMS內容。

_AC-14991 - [GitHub問題](https://github.com/magento/magento2/issues/39996) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/64823f95)_

#### 在產品URL中啟用類別路徑會以多種方式中斷商店切換器

修正啟用產品URL中的類別路徑會造成商店切換器失敗的問題；商店切換現在可正確解析跨商店檢視的產品URL，不會重新導向首頁或傳回錯誤。

_AC-15110 - [GitHub問題](https://github.com/magento/magento2/issues/40037) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a7ef6300)_

#### ProductRepository getById中未定義的陣列索引鍵

以類似123abc的無效ID呼叫ProductRepository：：getById()時，會發生問題導致「未定義的陣列機碼」錯誤。
Magento 2.4.9-alpha3修正後，這類請求現在會正確傳回404頁面，而非擲回例外狀況。
QA已透過有效及格式錯誤的ID確認，且未發現其他問題。

_AC-15345 - [GitHub問題](https://github.com/magento/magento2/issues/40146) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### Storefront比較產品建立Google SEO錯誤 — 連結無法編目

解決搜尋引擎無法對店面「比較產品」連結進行編目，因為href屬性遺失或繫結不當的SEO問題。 此更新可確保連結現在包含有效的、可編目的URL，進而改善網站的可發現性，並幫助通過Google SEO稽核。

_AC-15547 - [GitHub問題](https://github.com/magento/magento2/issues/40185) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 透過REST API更新產品url_key不會產生301 URL重寫

透過REST API更新產品的URL金鑰時，如果將「如果URL金鑰變更，請為URL建立永久重新導向」設定設為「是」，產品URL重寫會建立從舊URL到新URL的重新導向。

_ACP2E-3900 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

#### [雲端] Sitemap產生永不結束

在此修正之前，如果目錄包含超過一百萬項產品，則網站地圖產生無法成功完成。 修正後，Sitemap的產生程式將會以較低的記憶體配置完成，而且每個商店最多可容納100萬個產品。

_ACP2E-3902 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### [雲端]存放區切換器無法從EN工作到FR以取得常見問題頁面

修正在商店檢視之間切換時，將使用者重新導向至首頁而非對應的翻譯CMS頁面的問題。 存放區切換器現在會檢查目標存放區中的URL重新寫入，以確保重新導向正確(例如英文的常見問題頁面→法文的常見問題頁面)。

_ACP2E-4112 - [GitHub問題](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [雲端]停用舊的Sitemap產生

新的組態選項現在可用於在標準Sitemap產生程式與新實作的批次模式之間切換。 此增強功能允許在Sitemap建立工作流程中提供更大的彈性和擴充性。

_ACP2E-4132 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 可疑請求會在exception.log中擲回例外狀況

修正了惡意或格式錯誤的URL要求造成資料庫定序錯誤及填入例外狀況記錄檔的問題。
以前，如果收到包含無效字元編碼或不支援字元的可疑請求，系統會嘗試解碼並處理這些請求，導致MySQL定序衝突。

_ACP2E-4328 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2687b487)_

### 銷售

#### 在訂購狀態下拉式清單中選取值時，訂購狀態會消失

訂單狀態指派現在可如預期運作。
先前，在指派自訂訂單狀態時，「正在處理」狀態會在取消指派狀態後從下拉式清單中消失，導致無法重新指派。
AC-15010

_AC-15010_

#### 當「訂單」層級啟用「禮品」訊息，但使用者未輸入任何資料及下單，則仍會顯示「管理員」中的「寄件者姓名」與「寄件者姓名」，並顯示客戶的名字與姓氏。

修正即使未輸入禮品訊息，禮品訊息寄件者和收件者欄位仍自動填入客戶名稱的問題；除非使用者提供詳細資訊，否則欄位現在保持空白。

_AC-15140 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a8cf637b)_

### 搜尋

#### 使用「記住類別分頁」在目錄搜尋上「確認表單重新提交」

修改工具列設定後，從產品頁面導覽回目錄搜尋結果頁面，在啟用「記住類別分頁」時，將不再觸發「確認表單重新提交」對話方塊。
以前，使用者在變更工具列引數（如排序順序）後返回搜尋結果頁面時，遇到瀏覽器錯誤或表單重新提交警告。

_ACP2E-4208 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e885088b)_

#### 彙總搜尋欄位「_search」不再用於搜尋查詢

現在，如果所有可搜尋欄位中的最低符合條件集體滿足，則全文檢索搜尋會傳回符合的產品，而不是要求條件由單一欄位滿足。

_ACP2E-4285 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cbca0396)_

### 安全性

#### 內部伺服器錯誤

Magento現在於使用非同步REST端點POST /rest/default/async/V1/carts/mine/items時，成功將產品新增至客戶的購物車。 之前，這個非同步「加入購物車」要求導致內部伺服器錯誤，且Magento記錄下列錯誤：錯誤：在app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162的null上呼叫成員函式setFinalPrice()。

_AC-16344 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

#### 套件式/合併式JS不屬於SRI雜湊

在修正之前，產生的套件組合或合併的檔案並未新增至SRI雜湊清單。 現在，檔案已適當地新增至SRI雜湊。

_ACP2E-3854 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD]在Newrelic中發生可寫入許可權問題

在修正之前，記錄檔中雜亂無章，常有例外狀況。 套用修正後，記錄現在乾淨且沒有例外狀況。

_ACP2E-4296 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/61c96348)_

### 送貨

#### 在幾個信用通知後要送出的數量不正確

修正在多個銷退折讓單之後，無法正確計算「送貨數量」值的問題，以允許退款專案的出貨。
現在，系統會根據已出貨與已退款的料號，準確地更新剩餘的可出貨數量，以防止無效的出貨。

_AC-1479 - [GitHub問題](https://github.com/magento/magento2/issues/34289) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/913bf1a6)_

#### 載入送貨方法時的潛在效能問題

已透過確保請求時僅載入有效承運商來最佳化出貨方法載入流程。 以前，所有送貨方法的工廠都已初始化，造成不必要的效能額外負荷。 此修正透過有條件地只載入有效出貨承運商，減少載入時間及資源使用量，進而提高效率。

_AC-15415 - [GitHub問題](https://github.com/magento/magento2/issues/40153) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/cc0ec250)_

#### [問題]商業目的地不應視為住宅

修正UPS REST船運整合中，商業目的地被錯誤視為住宅的問題。 ResidentialAddressIndicator現在僅包含在住宅地址的UPS費率要求中，以防止意外的住宅附加費，並確保準確的商業運費。

_AC-16285 - [GitHub問題](https://github.com/magento/magento2/issues/40314) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40307)_

#### 建立UPS出貨標籤時發生例外狀況

修正警告：在UPS出貨標籤建立期間陣列到字串的轉換

_ACP2E-3676 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Magento_Fedex核心模組在傳送要求以取得新權杖之前，是否會檢查有效的作用中權杖？

Adobe Commerce很快會向FedEx API服務提出許多要求來取得存取權杖。 先前，即使存取權杖仍然有效，Adobe Commerce一律會向FedEx API提出新請求，導致速率限制問題。

_ACP2E-3930 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4ca73607)_

### 測試和預覽

#### 當中繼更新調整規則時，受目錄價格規則影響的購物車中產品的價格不會變更

修正了透過測試更新修改目錄價格規則後，購物車中的產品價格未完全更新的問題。 以往，更新的價格只會出現在摘要區段，而中央購物車區塊會顯示舊值。 現在，修訂後的規則正確更新整個購物車的產品價格。

_AC-15304 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/913bf1a6)_

#### 刪除類別的排定更新時，不會減少父類別的子項數量

修正刪除類別的已排程更新並未減少父類別子項計數的問題，確保在移除已排程更新或子類別時計數會正確更新。

_AC-15670 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ef666cd9)_

#### 編輯類別的排程更新時，會將子金額新增至父類別

修正編輯子類別的現有排程更新時，資料庫中父類別的children_count會不正確地增加的問題。 儲存更新後，問題導致不正確的類別階層資料。 修正後，子系計數保持正確且不再意外增加。

_AC-16239 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/8670a2b4)_

#### 預覽排程更新會按字母順序開啟第一個商店檢視，而非感興趣的商店檢視

在修正之前，排程更新的預覽會依字母順序在第一個存放區檢視中開啟，而不是依指派的存放區檢視。
修正後，預覽現在會在指派給CMS區塊測試更新的存放區檢視中正確開啟。

_ACP2E-3671 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b12ffe36)_

#### Staging_apply_version Cron行為問題 — 已忽略special_price

修正後，在排程產品更新變更特殊價格後，將重新計算報價總計。

_ACP2E-3674_

#### 無法在啟用類別許可權的情況下預覽排程的產品更新

在修正之前，要啟用的未來產品不會以預覽模式顯示。 現在，即使目前狀態為停用，也會顯示它。

_ACP2E-3786 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7accebfa)_

#### 預覽期間範圍顯示不同的存放區檢視

在此修正之前，cms區塊和cms頁面內容的測試更新預覽可能已在不同存放區中開啟，而不是在從「內容測試控制面板」存取時，在cms區塊或頁面上指派的存放區。 修正後，如果cms區塊或頁面在測試更新中僅指派了特定存放區，則會從內容測試儀表板開啟預覽，並選取正確的存放區。

_ACP2E-3815_

#### 缺少目錄價格規則折扣金額欄位的驗證

之前，使用目前驗證規則時，暫存排程更新中的discount_amount欄位無法正確驗證。 不過，在套用修正之後，將會適當地驗證discount_amount欄位。

_ACP2E-3867 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/462ede94)_

#### 使用不同管理網域時，結帳時分段更新預覽會中斷

當商店基本URL與管理員URL不同時，客戶可以登入並在商店預覽模式下檢視其購物車。

_ACP2E-3906_

#### 內容中繼儀表板時間顯示不正確

現在，「內容測試控制面板」中的「開始時間」和「結束時間」日期篩選器會顯示正確的日期和時間。 先前，在日期選擇器中選取日期和時間後，顯示不正確的日期和時間

_ACP2E-3969_

#### 預覽排程更新產品和類別時，範圍顯示不同的商店檢視

在此修正之前，類別和產品的預覽連結未針對正確的商店產生。 進行此修正後，預覽連結會自動選取建立預覽的存放區。

_ACP2E-4053_

#### 具有已排程更新的套件組合產品會移除產品儲存動作中的套件組合專案選項

在排程更新中移除套件組合產品選項或相關產品時，不再影響原始套件組合選項和相關產品，反之亦然。 此外，在排程更新後移除原始產品中的搭售生產選項並取代為其他選項不再導致移除新新增的選項

_ACP2E-4212 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ab891304)_

#### 促銷活動預覽模式中套用的抵用券在套用後不久消失的問題。

修正前，驗證器程式碼無法在中繼預覽模式中正確使用。 現在，修正後，憑單代碼已正確套用至結帳頁面。

_ACP2E-4226_

#### 無法在排程更新預覽中的網站之間導覽

在此修正之前，嘗試預覽具有自訂網域的存放區內容時，排定的更新預覽會中斷。 此項修正後，自訂商店網域可依原樣預覽，並在預覽iframe中導覽。 此修正涵蓋產品、類別、CMS頁面和CMS區塊，並支援使用`{{store url}}`標籤標籤的導覽連結，如[Adobe Commerce變數和標籤標籤](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags)中所述。

_ACP2E-4308 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/0a3b7032)_

### 稅金

#### 錯誤訂單總計，舍入不會套用至價格計算。

系統現在可在計算price_after_discount、discount_amount及稅額時正確處理。
訂單的實際總計

_AC-11389 - [GitHub問題](https://github.com/magento/magento2/issues/38455) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39687)_

#### [問題]修正：「銷退折讓單專案」的base_weee_tax_applied_row_amnt值不正確

使用base_weee_tax_applied_row_ament的適當設定值，更正銷退折讓單計算，確保稅捐值只反映退款數量。 以前，列金額錯誤地使用了完整的訂單值，而不是部分銷退折讓單金額。

_AC-12049 - [GitHub問題](https://github.com/magento/magento2/issues/38765) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/3b5ac075)_

#### 從購物車移除贈品包裝時，不會更新稅額

透過setGiftOptionsOnCart GraphQL變異移除禮品包裝時，Magento現在會正確更新購物車稅捐總計。 先前，當選取贈品包裝選項，然後傳遞「giftWrappingId」來取消設定時：變異輸入中的null，報價中的稅額未更新，並且Magento繼續在購物車總計中加入贈品包裝稅，即使未套用贈品包裝。

_AC-14637_

#### 迷你購物車中的商品會顯示外幣價格，但不進行轉換

迷你購物車現在可以正確轉換貨幣，並根據設定的轉換率顯示正確的金額。

_ACP2E-4364 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1c547060)_

### 測試架構

#### [問題]從MFTF測試AdminSetUpWatermarkForSwatchImageTest移除重複的&lt;severity>標籤

系統現在在AdminSetUpWatermarkForSwatchImageTest中僅包含單一嚴重性標籤，以改善程式碼清晰度和一致性。 之前，此測試包含兩個相同的嚴重程度標籤，這並非必要操作，且可能會導致混淆。

_AC-11873 - [GitHub問題](https://github.com/magento/magento2/issues/38504) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/31862)_

#### [問題]忽略lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

系統現在會忽略執行單元測試時產生的&#39;env.php&#39;檔案，確保Git狀態在執行測試後保持乾淨。 以前，執行單元測試會產生新檔案&#39;env.php&#39;，導致Git狀態顯示找到的新檔案，並使其看起來很髒。

_AC-13293 - [GitHub問題](https://github.com/magento/magento2/issues/39304) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37631)_

#### [問題]修正攔截器的整合測試問題

系統現在可以在整合測試中正確識別及處理\Magento\TestFramework\App\Config\Interceptor ，確保測試可以存取必要的資料，即使類別上有外掛程式存在。 之前，系統無法考慮\Magento\TestFramework\App\Config成為\Magento\TestFramework\App\Config\Interceptor的可能性，導致在嘗試存取$data屬性時發生錯誤。

_AC-13305 - [GitHub問題](https://github.com/magento/magento2/issues/39324) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37187)_

#### [問題] MFTF：正在將電子郵件提交至已啟用驗證碼的Friend表單

測試案例會在啟用驗證碼時，說明「傳送電子郵件給朋友」表單的功能，確保表單提交程式可在驗證碼值不正確和正確的情況下正常運作。

_AC-13492 - [GitHub問題](https://github.com/magento/magento2/issues/39462) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32830)_

#### [雲端原生服務] CNS建置失敗 — 2.4.9-beta1 — 整合

_AC-16427_

#### 硬式編碼固定路徑在撰寫器組建中失敗

_AC-16488_

#### PR和Composer組建之間的PHPUnit設定檔案不相符

_AC-16501_

#### [問題] magento/magento2#： GraphQl突變。 客戶storeConfig設定的額外測試涵蓋範圍。

系統現在為下一個客戶storeConfig選項新增額外的測試涵蓋範圍：
required_character_classes_number
minimum_password_length

_AC-9370 - [GitHub問題](https://github.com/magento/magento2/issues/37915) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/28761)_

#### AC 2.4.7-p3中的環境特定單元測試失敗

此問題會修正未在所有版本和環境上重製的單元測試失敗。 以前，為了修正此問題，部分單元測試會因為不同程式庫版本或因較新版本新增的功能遺失而失敗。

_ACP2E-3712 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9ad7d277)_

#### [單元測試] Magento\GiftCardImportExport\Test\Unit\Model\Import\Product\Type\GiftCardTest：：testIsRowValid

已針對隨機失敗單元測試提供修正

_ACP2E-4263_

### UI框架

#### [問題]從較少的檔案中移除重複的變數

系統現在會從較少的檔案中移除重複的變數，確保程式碼更乾淨且更有效率。 以前，這些重複的變數出現在較少的檔案中，導致程式碼中不必要的冗餘。

_AC-11743 - [GitHub問題](https://github.com/magento/magento2/issues/31154) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/31150)_

#### 動態列中的WYSIWYG是空的

動態列中的WYSIWYG欄位現在已正確初始化並填入。
先前，動態列中的WYSIWYG欄位（例如設計設定表單中的）可能會顯示空白或在特定動作後遺失內容，需要手動介入以還原資料。
AC-12336

_AC-12336 - [GitHub問題](https://github.com/magento/magento2/issues/38893) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [問題]修正MIME型別錯字

系統可正確處理並修正gif影像的mime型別和拼寫錯誤

_AC-8001 - [GitHub問題](https://github.com/magento/magento2/issues/36899) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36669)_

#### [問題]從`@author`移除禁止的`Magento_Backend`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8814 - [GitHub問題](https://github.com/magento/magento2/issues/37522) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36976)_

#### [問題]避免直接存取檢閱清單Ajax

系統可正確處理並避免直接存取檢閱清單Ajax

_AC-9381 - [GitHub問題](https://github.com/magento/magento2/issues/37920) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33876)_

#### 標題登入/登出未使用共用Cookie在多重存放區設定中更新

登出時根據組態設定正確地更新登入標題。 如果客戶帳戶在全域共用，customer-data.js將使用Cookie來儲存「mage-customer-login」值。 否則，將使用本機儲存空間。

_ACP2E-4149 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobile] Fotorama可以在影像檢視器關閉動作時開啟迷你購物車

已修正Fotorama的問題。 以前，迷你購物車會在影像檢視器的關閉動作上開啟

_ACP2E-4231 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e885088b)_

#### 合併的js檔案無法在包含許多存放區的專案上正確產生。

現在當設定多個存放區時，合併JavaScript檔案可正確運作。
以前，檔案有時無法在多存放區設定中正確合併，導致結果不完整或不一致。

_ACP2E-4246 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ab891304)_

### 升級 — 升級相容性工具

#### 已棄用的功能：建立動態屬性Magento\Framework\Acl：：$_roleRegistry

已棄用的功能錯誤不會再阻止在升級後存取管理面板。
之前，升級至Magento 2.4.6後，嘗試存取管理面板可能會導致錯誤：
「已棄用的功能：建立動態屬性Magento\Framework\Acl：：$_roleRegistry已在vendor/magento/framework/Session/SessionManager.php online 186中棄用」
這會導致管理員無法登入。
AC-12343

_AC-12343 - [GitHub問題](https://github.com/magento/magento2/issues/37469)_

#### GUID未儲存為安全格式

_AC-15809_

#### 升級相容性工具，但發生錯誤嚴重問題

不適用

_ACP2E-3856_
