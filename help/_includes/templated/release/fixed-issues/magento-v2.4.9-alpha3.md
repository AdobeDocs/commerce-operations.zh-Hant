---
source-git-commit: ae571a9e7ca1234644a3bc9beade447009c58a3d
workflow-type: tm+mt
source-wordcount: '6079'
ht-degree: 0%

---
# Magento Open Source發行說明(v2.4.9-alpha3)

## 已修正v2.4.9-alpha3中的問題

我們已修正Magento Open Source 2.4.9-alpha3核心程式碼中的129個問題。 此版本中包含的已修正問題子集說明如下。

### API

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

#### REST API端點export-stock-salable-qty傳回不正確的專案total_count

修正存貨匯出庫存可銷售數量API中total_count不正確限製為頁面大小的分頁問題。 先前，當使用/rest/all/V1/inventory/export-stock-salable-qty/website/base端點搭配page_size=5之類的分頁引數時，回應中的total_count欄位會傳回5，而非符合搜尋條件的實際產品總數。 進行此修正後， total_count欄位現在會正確反映可用的產品總數（不論page_size引數為何），確保所有的Magento REST API端點具有一致的分頁行為。

_ACP2E-4086 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5632fb5e)_

#### 購物車專案REST API中的自訂選項ID驗證問題

REST API V1/guest-carts/&lt;cartId>/items/和V1/carts/mine/items/現在驗證「product_options.extension_attributes.custom_options」。*.option_id」以確保其參考購物車專案SKU的有效option_id。 之前，系統會在未經驗證的情況下處理此引數，並將其儲存在資料庫中。

_ACP2E-4138 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

### 帳戶

#### [問題]已移除後端格線上不必要的間距

系統現在會移除後端格點中不必要的間距。當有選取的專案時

_AC-11579 - [GitHub問題](https://github.com/magento/magento2/issues/38502) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32622)_

#### 無法透過`updateProductsInWishlist` GraphQL突變清除願望清單專案註解

修正未透過GraphQL變動更新願望清單註解的問題。
現在，註解會正確更新，並反映在API回應和店面中。

_AC-14682 - [GitHub問題](https://github.com/magento/magento2/issues/39911) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

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

#### 登入magento 2.4.8-p1後的問題

修正Magento 2.4.8-p1登入後首頁上仍顯示「建立帳戶」連結的問題。
現在，與其他頁面一樣，連結在登入後會正確隱藏。

_AC-15292 - [GitHub問題](https://github.com/magento/magento2/issues/40120)_

### 管理員UI

#### [問題]取代已棄用的逸出程式

此PR會移除已過時的getEscaper()，並透過建構函式插入來新增它

_AC-15132 - [GitHub問題](https://github.com/magento/magento2/issues/40062) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38135)_

#### 歡迎訊息在行動檢視中重疊產品類別。

修正使用者介面問題，此問題導致歡迎名稱與行動檢視中的產品類別重疊、阻礙點按。
現在，類別完全可見且可點按，沒有重疊問題。

_AC-15166 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Google reCAPTCHA管理面板的exception.log中的「無法解析reCAPTCHA引數」專案

已解決Google V3 reCAPTCHA管理員登入之`var/log/exception.log`檔案中的reCaptcha錯誤，且未記錄任何錯誤訊息。 以前，當管理員使用者設定其&#x200B;**設定** > **安全性** > **Google reCAPTCHA管理員面板**&#x200B;設定時，每隔幾秒就會擲回下列錯誤： `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`。  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub問題](https://github.com/magento/magento2/issues/34975) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub程式碼貢獻](https://github.com/magento/security-package/commit/804dbc2a)_

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

_ACP2E-4052 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

### 管理員UI、稅金

#### 稅率管理員UI錯誤

此票證修正了稅率管理員UI的問題，該問題導致切換國家/地區(例如從美國→英國)仍顯示先前選取的美國州別，誤導使用者。
在2.4.9-alpha3中，現在當選取的國家沒有狀態時，狀態列位會重設為*。

_AC-8440 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Rest API products-render-info傳回登入客戶的最終價格有誤

票證已修正Rest API產品 — render-info針對登入的客戶傳回錯誤的最終價格

_AC-5979 - [GitHub問題](https://github.com/magento/magento2/issues/35757) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/)_

#### 當我們嘗試從類別頁面新增請購單清單時，「新增至請購單清單」按鈕會消失

先前的「新增至請購單清單」按鈕在嘗試從分類頁面新增時消失，分類頁面現在已修正，我們可以看到分類頁面上的請購單按鈕

_AC-8575_

### B2B、購物車和結帳

#### 從管理員功能「以客戶身分登入」登入B2B公司使用者時，Storefront上不會顯示具有cartId = X錯誤的實體

現在，使用「以客戶身分登入」功能時，從管理員後端成功登入後，不會再出現「具有cartId = X的這類實體」錯誤。

_ACP2E-3994 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

### 購物車與結帳

#### [問題]新增EventPrefix和EventObject至簽出合約模型

系統現在包含簽出協定模型的EventPrefix和EventObject，允許使用事件首碼觸發事件。 此增強功能為開發人員提供處理簽出協定事件時的更多彈性。 先前，出庫協定模型不支援EventPrefix和EventObject，因此限制自訂事件處理的能力。

_AC-13252 - [GitHub問題](https://github.com/magento/magento2/issues/32510) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/32451)_

#### [Graphql]無法針對不可為null的欄位「SelectedCustomizableOption.label」傳回null

選取的選項不再存在時，系統現在不會擲回含有訊息的內部伺服器錯誤

_AC-14256 - [GitHub問題](https://github.com/magento/magento2/issues/39729) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8]無法在城市名稱中置入數字0-9、與號、句號或括弧的訂單

修正包含特殊字元（例如）的城市名稱簽出失敗的問題。、和，或括弧。
現在，已成功下具有此類城市名稱的訂單，且沒有驗證錯誤。

_AC-14495 - [GitHub問題](https://github.com/magento/magento2/issues/39854) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Salesrule Subselect with Quantity條件無法套用

修正具有產品細選條件的購物車價格規則未在結帳時套用的問題。
現在，已根據設定的規則成功套用折扣。

_AC-14884 - [GitHub問題](https://github.com/magento/magento2/issues/39965) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql — 啟用延交訂單時，合併購物車無法正常運作

修正在透過GraphQL合併購物車時，訪客購物車專案未與客戶購物車合併的問題。
現在，客戶購物車可正確反映訪客和客戶購物車的合併數量。

_AC-15148 - [GitHub問題](https://github.com/magento/magento2/issues/40064) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [整合] [簽出] Depend指示已在失敗的付款電子郵件範本中更新

已更新失敗的付款電子郵件範本，以正確處理depend指示。
修正確保送貨地址和送貨方式在適用時正確顯示。
以往，失敗的付款電子郵件會遺漏這些欄位。

_AC-15363 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 當購物車不再符合要求時，[雲端]免運費折扣未正確移除

小計(不包括 Tax)在購物車價格規則中，現在會合併先前規則的折扣。

_ACP2E-3973 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 在多重送貨中發現相同客戶的重複訂單

同時請求以多個出貨地址下單時，不會再產生相同客戶的重複訂單

_ACP2E-4117 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

### 購物車與結帳、訂購、產品

#### 即使訂單發票失敗，也會傳送禮品卡電子郵件

在此修正實施之前，禮品卡電子郵件會在發票建立後傳送。 不過，套用修正後，現在會在成功儲存及確認發票後，傳送禮品卡電子郵件。

_ACP2E-3905_

### 購物車與結帳、安全性

#### 實施sri修補程式後第一次嘗試時，在簽出頁面上取得[CLOUD]的JS檔案404

啟用縮制和套件組合時，修正Mixin之前的版本將不會載入購物車和結帳。 修正後，所有mixin都應如預期載入。

_ACP2E-4128 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

### 目錄

#### 價格範圍和config.php的問題

在Magento 2.4.2中，透過config.php變更價格範圍時，無法正確更新catalog_eav_attribute中price屬性的is_global值。
因此，產品價格會維持全球性，無法依網站儲存，即使價格範圍設定為網站亦然。
此因應措施需要手動更新資料庫中的is_global欄，這不適用於生產環境。
此行為與Magento的預設設計一致，其價格範圍為全域或網站，但並非根據商店檢視。

_AC-13857 - [GitHub問題](https://github.com/magento/magento2/issues/33559)_

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

#### 動態影像產生會產生大量影像

修正後，系統只會針對指派產品的網站產生影像。

_ACP2E-3927 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fab20b00)_

#### 前端發生500錯誤，因為配置中快取的配置結構不正確

修正由於版面中快取了不正確的版面結構，頁面傳回500錯誤碼的問題

_ACP2E-4040 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47721be6)_

#### 排定更新中「型錄價格規則」折扣金額欄位的驗證錯誤

先前，在修正此問題之前，針對型錄價格規則的排程更新，如果折扣金額為by_fixed，則因為驗證編號範圍規則而無法正確驗證。 套用此修正後，固定價格型錄價格規則的驗證即正常運作。

_ACP2E-4054 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 產品在停用後顯示為無庫存

修正後，停用的產品不存在於產品Widget中。

_ACP2E-4136 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [雲端]重複專案錯誤(temp_category_descendants_%)

針對巢狀類別數量高的環境，修正在建立期間，排程更新重複專案的問題

_ACP2E-4159 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a1c57b2e)_

### 目錄， GraphQL

#### GraphQl無效的折扣計算

當目錄價格設定為包含稅捐時，GraphQL現在可以正確顯示折扣百分比和基本價格。 先前曾發生舍入錯誤，例如顯示19.99%而非20%。

_ACP2E-3993 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

### 目錄、產品

#### 透過GraphQL的PDP中未出現透過相關產品規則顯示的相關產品

之前，在套用此修正之前，相對產品規則針對符合規則的產品傳回空白/空值。 套用此修正後，產品成功傳回相符產品的相對規則。

_ACP2E-3949_

### 內容

#### graphql (magento 2.4.6-p4 ) — 嘗試取得非作用中狀態的cms頁面時發生錯誤

修正停用CMS頁面的GraphQL查詢傳回內部伺服器錯誤的問題。
現在，查詢會擷取正確的回應，而不會發生錯誤。

_AC-12302 - [GitHub問題](https://github.com/magento/magento2/issues/38877) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl]路由查詢無限回圈

此票證修正具有相同請求路徑和目標路徑的GraphQL路由查詢造成無限回圈並最終逾時的問題。
在2.4.9-alpha3中，查詢現在會傳回正確的錯誤回應，而非回圈。

_AC-14269 - [GitHub問題](https://github.com/magento/magento2/issues/39707) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### 將常數IMAGE_FILE_NAME_PATTERN變更為公開可見，以獲得更大的彈性

GenerateRenditions.php中的常數IMAGE_FILE_NAME_PATTERN已公開，讓開發人員在處理影像轉譯時擁有更多彈性。此修正包含在Magento 2.4.9-alpha3中，具有完整單位和整合測試涵蓋範圍。

_AC-15338 - [GitHub問題](https://github.com/magento/magento2/issues/39733) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### 內容分段預覽不適用於搜尋結果

在測試預覽中搜尋現在會根據選取的範圍傳回產品。 以前，搜尋會傳回預設範圍內的結果，而不考慮所選存放區。

_ACP2E-4095_

#### 頁面產生器 — 產品條件邏輯問題（OR邏輯的行為未正確顯示較少產品）

現在，在「符合任何」條件中使用具有全域範圍的屬性時，頁面產生器產品Widget會傳回正確結果

_ACP2E-4096 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

### 客戶/

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

#### [問題]讓方法簽章與介面一致

getAttributes的方法簽章現在與其介面一致，防止覆寫方法時發生任何錯誤。 先前，當嘗試覆寫getAttributes方法時，方法簽章中的不一致會導致錯誤。

_AC-11578 - [GitHub問題](https://github.com/magento/magento2/issues/38501) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/31955)_

#### [問題]修正UI元件的驗證電子郵件規則

系統現在可正確驗證在UI元件中輸入的多個電子郵件地址，確保每個電子郵件都正確裁剪和驗證。 以前，系統使用不正確的方法修剪電子郵件地址，這可能會導致驗證錯誤。

_AC-11719 - [GitHub問題](https://github.com/magento/magento2/issues/38528) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33470)_

#### [問題]移除多餘的方法

程式碼品質：移除AsynchronousOperations和Sales元件中僅呼叫父方法而未新增功能的備援方法，進而改善程式碼可維護性。

_AC-11915 - [GitHub問題](https://github.com/magento/magento2/issues/29748) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/29147)_

#### 在欄位專案底下包含註解的etc/adminhtml/system.xml檔案上，xsd驗證失敗。

此PR修正phpstorm中評論節點的XML結構描述定義

_AC-12945 - [GitHub問題](https://github.com/magento/magento2/issues/39148) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8使用不遵循語意版本設定的開發套件

Magento 2.4.8需要pdein/pdepend和phpmd/phpmd (3.x-dev)的開發版本才能與PHP 8.4相容。
這些開發版本與協力廠商工具衝突，這些工具預期會符合SemVer的套件，因此無法進行某些升級。
暫時解決方法是為composer.json中的開發版本取名（例如「3.x-dev as 3.99.0」），以便在滿足語意版本化的同時提供相容性。
這可確保PHP 8.4的支援並避免衝突，直到穩定發行版本可用。

_AC-14519 - [GitHub問題](https://github.com/magento/magento2/issues/39796)_

#### Rest API：在null上呼叫成員函式getVideoProvider()

修正子產品只有YouTube視訊且沒有其他影像時，呼叫可設定產品子項API傳回500內部伺服器錯誤的問題。
錯誤是由ExternalVideoEntryConverter中的null參考所造成。
現在，API可正確傳回含有媒體集專案的子產品，包括外部視訊資料，而不會擲回錯誤。
這可確保透過REST API正確擷取子項產品的所有媒體型別。

_AC-15046 - [GitHub問題](https://github.com/magento/magento2/issues/40021)_

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

#### 更新模組Readmes和修正檔案連結

_AC-15340 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/ec9459d0)_

#### [問題]只有在未停用的情況下才記錄未宣告的外掛程式

此PR會修正並記錄實際未宣告且未使用的外掛程式（已啟用且遺漏執行個體）。

_AC-15386 - [GitHub問題](https://github.com/magento/magento2/issues/40086) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2、magento/framework 103.0.8-p2版：呼叫不已存在方法的EmailMessage類別

_AC-15446 - [GitHub問題](https://github.com/magento/magento2/issues/40170) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/059fd469) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x]資料/結構描述修補程式getAliases()在`setup:upgrade`期間造成錯誤

getAliases()在安裝:upgrade期間造成錯誤，此PR修正了相同的

_AC-15559 - [GitHub問題](https://github.com/magento/magento2/issues/31396) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38239)_

#### 必須是型別&#39;Magento\Customer\Api\Data\GroupInterface&#39;。 找到&#39;Magento\Customer\Model\Group&#39;。

修正使用GroupFactory透過GroupRepositoryInterface儲存客戶群組時，造成型別錯誤的問題。
之前，存放庫需要GroupInterface，但傳遞了群組模型執行個體，導致嚴重錯誤。
現在，可以透過存放庫確保適當的介面實作，成功儲存客戶群組。
這樣便能以程式設計方式建立或更新客戶群組時，解決IDE警告和執行階段錯誤。

_AC-6909 - [GitHub問題](https://github.com/magento/magento2/issues/36269)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8349 - [GitHub問題](https://github.com/magento/magento2/issues/37266) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37016)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8350 - [GitHub問題](https://github.com/magento/magento2/issues/37265) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37015)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8359 - [GitHub問題](https://github.com/magento/magento2/issues/37262) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37012)_

#### [問題]移除禁止的`@author`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8362 - [GitHub問題](https://github.com/magento/magento2/issues/37259) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37009)_

#### [問題]從`@author`和`Magento_Backup`移除禁止的`Magento_Bundle`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8367 - [GitHub問題](https://github.com/magento/magento2/issues/37244) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36979)_

#### [問題]修正catalogsearch中的變數名稱

系統現在可以在搜尋引擎模組中正確地命名變數，藉此加強程式碼清晰度和可維護性。 先前在搜尋引擎模組中使用了不相關的變數名稱$defaultCountry，而造成混淆。

_AC-9215 - [GitHub問題](https://github.com/magento/magento2/issues/37810) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]伺服器問題可能是由無效的S3存取金鑰所造成

不正確的AWS S3憑證不會再導致頁面無限期地載入店面。

_ACP2E-3890 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [雲端] Minify js無法運作

下列JS檔案現在會在啟用JS縮制時完全且正確地縮制： mage/backend/tabs.min.j、jquery/jquery.validate.min.js和Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js。 因此，頁面產生器CSS類別欄位驗證會如運期般運作。

_ACP2E-3925 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/47721be6)_

#### Cron工作未清除資料庫表格 — 造成Galera當機造成中斷

變更記錄檔表格清理目前正在批次執行，以避免大量的刪除作業。

_ACP2E-3995 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### 未縮制的JS有時會忽略「啟用js縮制」而載入

在修正前，即使您已啟用縮制，仍會請求部分JS檔案而沒有「min」首碼，導致404狀態代碼。 修正後，啟用縮制時，未要求非縮制的JS資源。

_ACP2E-4058 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 自訂屬性群組中的日期屬性無法在管理員中顯示日期選擇器

修正指派給自訂屬性群組時，日期屬性的行事曆快顯視窗會出現在畫面外的問題。

_ACP2E-4060 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### 客戶訂購GraphQL ：擷取關聯產品的產品類別「無法個別顯示」

在修正之前，如果訂單包含隱藏產品，則其類別會在客戶訂單GraphQl回應中顯示空白陣列。
現在，修正後，產品類別會包含在客戶訂單GraphQl請求的回應中，即使產品已隱藏。

_ACP2E-3945 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

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

### GraphQL、詳細目錄/MSI

#### GraphQL mergeCart變異差異

修正後，合併購物車GraphQL請求會考量庫存設定，正確檢查產品數量。

_ACP2E-4184 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL，安全性

#### 透過GraphQL重設客戶密碼未遵守限制

解決透過GraphQL變動提出的客戶密碼重設請求不符合存放區>設定>客戶>客戶設定>密碼選項下設定的密碼重設限制的問題。 系統現在會正確強制執行這些設定。

_ACP2E-3992 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

### 匯入/匯出

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

### 庫存/MSI

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

### 訂購

#### Magento 2.4.8 GraphQL — 訂購專案order_date格式錯誤

修正GraphQL回應中的order_date欄位傳回yyyy-mm-dd格式的問題。
現在，order_date以dd-mm-yyyy格式正確顯示。

_AC-14431 - [GitHub問題](https://github.com/magento/magento2/issues/39805) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 儘管已在商店設定中啟用，但從管理員訂單檢視提交時仍不會傳送出貨電子郵件

系統現在會傳送出貨確認電子郵件，因為它已在下訂單的商店設定中啟用。

_AC-14563 - [GitHub問題](https://github.com/magento/magento2/issues/39861) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39897)_

#### 由於欄位名稱模稜兩可，日期篩選無法運作

在Magento 2.4.7-p6中，依日期篩選訂單格線會回報由於與Braintree模組的結合而造成錯誤。
該問題涉及在套用日期篩選器時聯結braintree_transaction_details和sales_order表格的查詢。
Adobe Commerce工程部門已檢閱此案例，但無法在環境中重現錯誤。
預期行為是依日期篩選應該會傳回符合篩選器的訂單，而不會發生錯誤。

_AC-15037 - [GitHub問題](https://github.com/magento/magento2/issues/40024)_

#### Magento2：無法建立促銷活動規則

此PR修正，我們收到
\Magento\Catalog\Model\ResourceModel\Eav\Attribute模型，而不是\Magento\SalesRule\Model\Rule\Condition\Product：：loadAttributeOptions方法中的\Magento\Catalog\Model\ResourceModel\Eav\Attribute

_AC-15358 - [GitHub問題](https://github.com/magento/magento2/issues/12176) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/30479)_

#### 取消商業發票重新導向至404

取消以「非擷取」型態開立的商業發票時，不會再產生第404頁。

_ACP2E-4001 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 銷售封存Cron工作造成資料庫鎖定問題

在修正之前，位於封存cron順序中的未繫結DELETE查詢導致Galera發生問題。 現在，更新後，刪除查詢的執行會受到限制。

_ACP2E-4010_

#### 使用REST API時可設定選項的更新訂單問題

透過rest api端點更新訂單時，保留銷售訂單專案上的現有產品選項。

_ACP2E-4061 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

### 其他開發人員工具

#### [問題]正在清除未使用的程式碼。

系統現在會移除有關未使用匯入的未使用程式碼。

_AC-10980 - [GitHub問題](https://github.com/magento/magento2/issues/38424) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/33499)_

#### [問題]協助工具：功能表中的WAI-ARIA角色巢狀錯誤

系統現在產生Lighthouse協助功能，且WAI-ARIA角色在功能表錯誤中不會巢狀錯誤，報告應為綠色

_AC-15082 - [GitHub問題](https://github.com/magento/magento2/issues/40045) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/38617)_

#### 在Magento管理員中預覽電子郵件時出現控制檯錯誤

預覽電子郵件範本時，系統不會擲回任何主控台錯誤

_AC-9245 - [GitHub問題](https://github.com/magento/magento2/issues/37820) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/37933)_

### 付款

#### 來自PayPal的未知IPN濫用應用程式IPN處理器

IPN處理常式現在會忽略不支援或不明的IPN型別。 它會記錄問題並繼續處理，而不會傳回500錯誤，不會造成中斷。

_ACP2E-4049 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro儲存的卡片權杖付款時失敗

PayPal PayFlow Pro交易ID (PNREF)現在可在12個月的固定期間內用於參考交易。 一旦過期，已儲存的卡片將不再顯示，且必須重新新增。 以前，有效性取決於原始交易中使用的付款卡的到期日。

_ACP2E-4064 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

### 效能

#### [問題]靜態網站的更新使用快取控制不可變

此PR新增了效能改善，方法是在&amp;變更之前，不驗證每個頁面載入上的靜態內容。

_AC-15171 - [GitHub問題](https://github.com/magento/magento2/issues/39486) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/39484)_

#### [雲端]無法新增產品至類別

改善透過Visual Merchandiser將產品新增至類別時的效能。

_ACP2E-3946 - [GitHub程式碼貢獻](https://github.com/magento/inventory/commit/29653b1d)_

#### [雲端]快取無效超過10K個記錄

之前，在每次進行PLP或購物車造訪時都會清除快取，造成不必要的效能額外負荷。 Target規則快取不再在這些頁面上失效，進而改善瀏覽效率。

_ACP2E-4059_

### 定價

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

#### 測試案例AC-6158的可設定產品仍會顯示「最低」標籤

實作並驗證可設定的產品(P1-P7)具有各自的變數和類別指派。 已確保類別C下產品的店面價格顯示正確及「最低」標籤行為。

_AC-10847 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 透過存放庫請求產品失敗時產生的額外記錄

改善找不到SKU或ID時ProductRepository：：get和getById的錯誤訊息。
以前，例外不會提供關於哪個SKU或ID導致錯誤的上下文。
現在，例外狀況訊息會包含遺失的SKU或ID，有助於進行偵錯並改善開發人員體驗。
此變更不會影響API的任何功能行為。

_AC-15199 - [GitHub問題](https://github.com/magento/magento2/issues/40090) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 當可設定的產品由受限角色編輯時取消指派簡單產品

在此修正之前，如果受限制的管理員使用者將儲存包含管理員使用者無權存取的簡單產品的可設定產品，則會在儲存時從可設定產品中移除。 修復後，可設定的產品會保留為從完整許可權管理員儲存。

_ACP2E-4081_

#### [雲端] Sitemap產生效能大幅降低

針對含有影像的產品產生Sitemap不再發生指數式放緩。 以前，為已啟用影像包含功能的存放區產生Sitemap會導致處理時間過長。

_ACP2E-4153 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/e457c5e2)_

### 促銷活動

#### 透過GraphQl客戶請求取得客戶訂單的訂單料號折扣applied_to時發生錯誤

先前當透過GraphQl針對客戶訂單套用折扣_to時觀察到內部伺服器錯誤，此錯誤現在已修正，並且已擷取套用折扣的適當客戶訂單資料

_AC-14888 - [GitHub問題](https://github.com/magento/magento2/issues/39963) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fe72c407)_

#### 透過GraphQl客戶請求取得客戶訂單的訂單專案優惠券代碼時發生錯誤

修正透過GraphQL擷取含有優惠券詳細資料的訂單時，傳回內部伺服器錯誤的問題。
現在，查詢已成功執行，並在回應中傳回正確的優惠券資訊。

_AC-14889 - [GitHub問題](https://github.com/magento/magento2/issues/39962) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### ProductRepository getById中未定義的陣列索引鍵

以類似123abc的無效ID呼叫ProductRepository：：getById()時，會發生問題導致「未定義的陣列機碼」錯誤。
Magento 2.4.9-alpha3修正後，這類請求現在會正確傳回404頁面，而非擲回例外狀況。
QA已透過有效及格式錯誤的ID確認，且未發現其他問題。

_AC-15345 - [GitHub問題](https://github.com/magento/magento2/issues/40146) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/68a45d0a)_

#### [雲端] Sitemap產生永不結束

在此修正之前，如果目錄包含超過一百萬項產品，則網站地圖產生無法成功完成。 修正後，Sitemap的產生程式將會以較低的記憶體配置完成，而且每個商店最多可容納100萬個產品。

_ACP2E-3902 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/52f46328)_

#### [雲端]存放區切換器無法從EN工作到FR以取得常見問題頁面

修正在商店檢視之間切換時，將使用者重新導向至首頁而非對應的翻譯CMS頁面的問題。 存放區切換器現在會檢查目標存放區中的URL重新寫入，以確保重新導向正確(例如英文的常見問題頁面→法文的常見問題頁面)。

_ACP2E-4112_

### 測試和預覽

#### 使用不同管理網域時，結帳時分段更新預覽會中斷

當商店基本URL與管理員URL不同時，客戶可以登入並在商店預覽模式下檢視其購物車。

_ACP2E-3906_

#### 內容中繼儀表板時間顯示不正確

現在，「內容測試控制面板」中的「開始時間」和「結束時間」日期篩選器會顯示正確的日期和時間。 先前，在日期選擇器中選取日期和時間後，顯示不正確的日期和時間

_ACP2E-3969_

#### 預覽排程更新產品和類別時，範圍顯示不同的商店檢視

在此修正之前，類別和產品的預覽連結未針對正確的商店產生。 進行此修正後，預覽連結會自動選取建立預覽的存放區。

_ACP2E-4053_

### UI框架

#### [問題]從`@author`移除禁止的`Magento_Backend`標籤

此PR會從程式碼基底移除`@author`標籤

_AC-8814 - [GitHub問題](https://github.com/magento/magento2/issues/37522) - [GitHub程式碼貢獻](https://github.com/magento/magento2/pull/36976)_
