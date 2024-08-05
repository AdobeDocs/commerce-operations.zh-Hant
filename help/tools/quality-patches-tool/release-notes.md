---
title: 發行說明
description: 瞭解Adobe Commerce可用的修補程式及其解決的問題。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 7c294a9450be46049090c78074d4fbe722a75119
workflow-type: tm+mt
source-wordcount: '20855'
ht-degree: 0%

---

# 發行說明

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)提供由Adobe和Magento Open Source社群開發的個別修補程式。 它可讓您套用、還原和檢視已安裝的Adobe Commerce版本可用的所有個別修補程式的一般資訊。 無論誰開發修補程式，您都可以將修補程式套用至Adobe Commerce和Magento Open Source專案。 例如，您可以將社群開發的修補程式套用至Adobe Commerce專案。

>[!INFO]
>
>如需將修補程式套用至您的Adobe Commerce專案的指示，請參閱[套用修補程式](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches)。 請參閱「軟體更新指南」中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)，以檢視已發行修補程式的完整清單。

>[!INFO]
>
>如需Community為Magento Open Source而建立[!DNL quality patches]的相關資訊，請參閱[發行說明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md)。

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正刪除中繼更新後移除產品影像的問題。
* **ACSD-57086** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正來自啟用條款與條件之非預設網站的訂單未正確處理的問題。
* **ACSD-57588** (適用於Adobe Commerce及Magento Open Source >=2.4.6 &lt;2.4.7) — 修正將訂單運送至多個地址會在地區ID處理期間觸發錯誤的問題。
* **ACSD-57643** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正透過GraphQL將具有自訂選項的產品錯誤新增到購物車的問題。
* **ACSD-57846** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正GraphQL產品以零價格篩選條件搜尋時，由於發生例外狀況，無法傳回任何結果的問題。
* **ACSD-57941** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正產品選項未正確指派給管理員存放區（而非其個別存放區）的問題。
* **ACSD-58375** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正當在商店檢視層級新增[!DNL YouTube]視訊時，錯誤的&#x200B;*[!DNL YouTube API Key]*&#x200B;設定導致錯誤的問題。
* **ACSD-58739** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正部分重新索引擲回錯誤的問題。
* **ACSD-58446** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正刪除具有子使用者或團隊的團隊時，不論其狀態為何（非作用中），系統都會提供與UI不一致的錯誤訊息，且無法提供相關資訊的問題。
* **ACSD-58054** （用於Adobe Systems商務>=2.4.4 &lt;2.4.6) - Fixes the issue where it is possible to generate customer tokens for inactive customers via API.
* **ACSD-58163** （適用於Adobe Systems商務>=2.4.3 &lt;2.4.7) - Fixes the issue where a *[!UICONTROL Cart Price Rule]* ）不會對沒有抵用券代碼的匹配 *[!UICONTROL Customer Segment]* 購物車中的訪客客戶應用折扣。
* **ACSD-57045** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正URL重新寫入導致從&#x200B;*[!UICONTROL Hierarchy]*&#x200B;取消勾選&#x200B;*[!UICONTROL Website Root]*&#x200B;後出現無限頁面回圈的問題。
* 更新修補程式：ACSD-46815、ACSD-47027、ACSD-51683、ACSD-55031、ACSD-51819、ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修正當合併具有相同組合專案的來源和目的地購物車時，[!DNL GraphQL]回應中的`mergeCart`變異失敗並出現「*內部伺服器錯誤*」的問題。
* **ACSD-56546** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修正當&#x200B;**顯示無產品組態**&#x200B;為&#x200B;*已停用*&#x200B;時，可設定和套件產品在店面顯示為&#x200B;**無庫存**&#x200B;的問題。
* **ACSD-56635** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正當匯入用於&#x200B;**帳戶共用**&#x200B;設定為&#x200B;*全域*&#x200B;時，匯入的客戶會以相同的電子郵件地址重複的問題。
* **ACSD-56741** (適用於Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修正當資料庫包含與索引機制和[!DNL MView]無關的自訂[!DNL MySQL]觸發程式時，在`setup:upgrade`期間顯示的錯誤訊息「*嘗試存取型別null*&#x200B;的值上的陣列位移」。
* **ACSD-57315** (適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修正每次在Admin的&#x200B;**[!UICONTROL View transaction]**&#x200B;畫面上按一下[!UICONTROL Fetch]按鈕時，[!DNL PayPal Payflow Pro]中建立新交易的問題。
* **ACSD-57337** (適用於Adobe Commerce >=2.4.4 &lt;2.4.6) — 修正具有特定網站存取限制的管理員使用者可以在&#x200B;**[!UICONTROL Companies]**&#x200B;格線中看見所有網站的公司的問題。
* **ACSD-57394** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正[!DNL GraphQL]中多個排序欄位的產品排序不正確的問題。
* **ACSD-57565** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正&#x200B;**[!UICONTROL Order]**&#x200B;儀表板在更新時段前顯示錯誤訂單資訊的問題。 儀表板現在會在第一次載入時顯示正確的訂單統計資料。
* **ACSD-57854** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正產品[!DNL GraphQL]請求在類別彙總中傳回停用類別的問題。
* **ACSD-58008** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正更新排程更新時，若未指定結束日期，會移除分段專案的先前版本的問題。
* 更新修補程式：MDVA-39305-V2、ACSD-48627、ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正下列問題：在多個位址結帳期間使用產生的優惠券時，*[!UICONTROL Used]*&#x200B;和&#x200B;*[!UICONTROL Times Used]*&#x200B;屬性會顯示不正確的值。
* **ACSD-56760** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正管理員使用者受限於特定網站時，若網站商店擁有自己的根類別，則無法在類別內排序或新增產品的問題。
* **ACSD-56858** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正受限制公司管理員無法正確顯示B2B公司角色許可權的問題。
* **ACSD-57074** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正以`price_`開頭的`attrbute_code`的&#x200B;*是/否*&#x200B;自訂屬性無法正確搭配索引運作，且含有此類屬性的產品無法前端使用的問題。
* 更新的修補程式：ACSD-53378、ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正庫存數量變更時，即使產品仍有庫存，類別頁面快取無效的問題。
* **ACSD-54656** (適用於Adobe Commerce >=2.4.5 &lt;2.4.6) — 修正隱藏的Recaptcha在結帳期間失敗，導致無法下訂單的問題。
* **ACSD-55100** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正GraphQL在搜尋結果中未傳回超過10,000項產品的問題。
* **ACSD-56621** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正公司管理員使用者的問候語標題區段中未反映更新後名字和姓氏的問題。
* **ACSD-56842** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正執行`setup:di:compile`後遺失延遲代理程式和延遲代理程式工廠的問題。
* **ACSD-57003** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正部分退款和部分運送訂單時，訂單狀態變更為&#x200B;*[!UICONTROL Complete]*&#x200B;而非變更為&#x200B;*[!UICONTROL Processing]*&#x200B;的問題。
* 更新修補程式：ACSD-50260-v2、ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正排程更新停用兩個子產品之一時，可設定產品無存貨的問題。
* **ACSD-56616** （用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where bundled products display as in stock on the storefront when their simple products are out of stock.
* **ACSD-56515** （用於Adobe Systems商務>=2.4.2 &lt;2.4.7) - Fixes the issue where admin with website level permissions cannot add or edit a dynamic block.
* **ACSD-56447** （用於Adobe Systems商務和Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where adding the same product to the cart via parallel REST web API requests results in two separate items in the cart.
* **ACSD-56415** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正當資料庫有許多要編制索引的區域性價格資料時，由於`DELETE`查詢，部分價格索引的效能變慢的問題。
* **ACSD-54965** (適用於Adobe Commerce >=2.4.5 &lt;2.4.6) — 修正當產品僅指派給自訂庫存時，視覺銷售格線無法顯示正確庫存的問題。
* **ACSD-52824** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正當公司設定中停用PayPal Express、Google Pay及Apple Pay按鈕時，公司客戶會顯示此類付款方式的問題。
* 更新修補程式：ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (適用於Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修正使用「**從庫存移至底部**」選項排序類別產品時，將使用者重新導向至管理員控制面板的問題，且`Invalid security or form key. Please refresh the page`錯誤會顯示在畫面頂端。
* **ACSD-56280** (for Adobe Commerce >=2.4.4 &lt;2.4.7) - Fixes the issue where ordering items from a gift registry leads to an exception.
* **ACSD-56246** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where data is removed from the custom multi-select attribute when a scheduled update for a product becomes active.
* **ACSD-56193** （用於Adobe Systems商務和Magento Open Source >=2.4.2 &lt;2.4.4) - Fixes the issue where the Varnish/Fastly cache is not updated when a scheduled block is used in the category description using Page Builder.
* **ACSD-56158** （用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the &quot;cart&quot; query returns the total tax value for each tax rule.
* **ACSD-56023** （用於Adobe Systems商業和Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where widget content is not updating on the CMS page when cache is enabled.
* **ACSD-55427** （用於Adobe Systems商務>=2.4.5 &lt;2.4.7) - Fixes the issue where the admin user cannot unassign a product from a shared catalog from the product page in the Admin.
* **ACSD-55352** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正使用客戶獎勵點數建立部分銷退折讓單之後，訂單狀態變更為「已結」且銷退折讓單選項從「管理員」訂單頁面消失的問題。
* **ACSD-55231** （Adobe Systems商務>=2.4.2 &lt;2.4.7) - Fixes the issue where you cannot add products to a cart using the quick order functionality.
* **ACSD-54283** （用於Adobe Systems商務>=2.4.3 &lt;2.4.4) - Fixes the issue where Products/Categories not assigned to the Shared Catalog for the Default (General Group) are still included in the XML Sitemap.
* 更新的修補程式：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** （用於Adobe Systems商務和Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the canonical category URL doesn&#39;t update after changing the category URL.
* **ACSD-53636** （用於Adobe Systems商務和Magento Open Source >=2.4.3 &lt;2.4.5) - Fixes the issue where the regular price is not displayed on product listing pages for configurable products that have child products with special prices.
* **ACSD-54885** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue with the multiple address checkout when the admin user is using the *Login as Customer* functionality.
* **ACSD-55610** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where a partially canceled order has an incorrect discount amount.
* **ACSD-55334** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes translations for labels through Translation dictionaries in GraphQL response.
* **ACSD-54739** （用於Adobe Systems商務>=2.4.5 &lt;2.4.7) - Fixes the issue where the product stock status condition is not applied for related product rules.
* **ACSD-53925** （用於Adobe Systems商務和Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the admin is unable to save CMS block with product carousel when `catalog_product_price` 維度模式 *設置為網站*。
* **ACSD-52714** (適用於Adobe Commerce及Magento Open Source >=2.4.2 &lt;2.4.7) — 修正日期格式設為&#x200B;*Y-m-d*&#x200B;時，日期篩選器在管理格線中無法運作的問題。
* **ACSD-55055** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 改善在購物車的購物車價格規則中載入產品屬性的效能。
* **ACSD-53790** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正可透過REST API為單一產品建立多個RMA的問題。
* **ACSD-56090** (適用於Adobe Commerce及Magento Open Source >=2.4.2 &lt;2.4.5) — 修正GraphQL要求回應所有存放區資料（而非特別要求的存放區資料）的問題。
* **ACSD-54983** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正當使用者狀態設為&#x200B;*[!UICONTROL Inactive]*&#x200B;時，無法使用GraphQL要求取得公司使用者UID的問題。
* **ACSD-53309** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正當選取可自訂選項時，*[!UICONTROL Regular Price]*&#x200B;標籤中未完全套用稅金的問題。
* **ACSD-55305**（用於Adobe Systems商務>=2.4.4 &lt;2.4.7) - Fixes the issue where the *[!UICONTROL Edit Company User]* >**[!UICONTROL myAccount]****[!UICONTROL Company Structure]**&#x200B;彈出視窗頁面在螢幕上使用載入器凍結。
* 更新修補程式：ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (適用於Adobe Commerce及Magento Open Source >=2.4.4 &lt;2.4.7) — 修正商店檢視中&#x200B;*[!UICONTROL Recently Viewed]*&#x200B;產品資料未正確更新的問題。
* **ACSD-54626** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正您無法透過[!DNL GraphQL]建立具有`NUMBER_OF_SKUS`屬性的新採購單規則(`createPurchaseOrderApprovalRule`)的問題。
* **ACSD-53845** (適用於Adobe Commerce及Magento Open Source >=2.4.0 &lt;2.4.7) — 修正`consumer max_messages` = 0時的[!DNL MySQL]連線逾時問題。
* **ACSD-54890**（用於Adobe Systems商務和 Magento Open Source >=2.4.0`aggregate_sales_report_bestsellers_data` [!DNL MySQL] &lt;2.4.7) - Fixes the issue where 會導致磁碟空間不足而導致`/tmp`錯誤。
* **ACSD-55112** （用于Adobe Systems商務和 Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the *[!UICONTROL Submit review]* 按鈕可以多次點擊而不會 [!DNL Google reCAPTCHA v3] 驗證。
* **ACSD-54264** （用於Adobe Systems商務>=2.4.4-p5 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p4 &lt;2.4.6 ||=&quot;&quot;>=2.4.6-p2 &lt;2.4.7) - Fixes the issue where the error message *“您無法更新請求的屬性。 &lt;/2.4.6>&lt;/2.4.5>行 ID： 商店_id“* 當客戶嘗試使用其他商店 視圖的可協商報價簽出時出現。
* **ACSD-54418** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a fixed amount of discount is incorrectly applied to each child product of the dynamically priced bundle.
* **ACSD-55238** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正儲存空產品&#x200B;*[!UICONTROL Meta Description]*&#x200B;的問題。
* **ACSD-54966** (適用於Adobe Commerce及Magento Open Source >=2.4.5 &lt;2.4.7) — 修正先前訂單失敗時，無法重複使用每位客戶限量使用之優惠券代碼的問題。
* **ACSD-54060** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正受限管理員無法儲存產品（如果產品是指派給其他範圍之其他產品的子產品）的問題。
* **ACSD-48910** (適用於Adobe Commerce且Magento Open Source>=2.4.5 &lt;2.4.6) — 修正訂單開立商業發票及出貨後，即使訂單數量仍非零，指派給多個來源的套件產品也會無存貨的問題。
* **ACSD-55381** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正透過[!DNL GraphQL]從[!DNL B2B] *[!UICONTROL Requisition list]*&#x200B;查詢`configurable_product_option_uid`及`configurable_product_option_value_uid`欄位時的內部伺服器錯誤。
* **ACSD-55628** (適用於Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) — 修正了在公司登錄檔單上傳檔案和取代店面中客戶屬性的檔案。
* 更新修補程式：ACSD-51240、ACSD-51890、ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正將產品加入購物車後，從共用目錄移除產品時購物車中發生的問題。
* **ACSD-53722** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 修正當不同範圍的排程更新生效時，隨附的產品選項價格變更為$0的問題。
* **ACSD-53643** (適用於Adobe Commerce >=2.4.3 &lt;2.4.7) — 修正訂購停用或無存貨的產品時，訂單總計有誤的問題。 已透過隱藏此類採購單的&#x200B;*[!UICONTROL Place Order]*&#x200B;按鈕來修正。
* **ACSD-54067** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a product video doesn&#39;t play on a mobile device.
* **ACSD-55414** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.6) - Improves performance when the MariaDB tries to cast the EAV entity_id from string to integer.
* **ACSD-51819** （適用於Adobe Systems商務>=2.4.4 &lt;2.4.4-p4) - Fixes the issue where multiple orders can be placed with the same quote ID.
* **ACSD-53118** （用於Adobe Systems商務>=2.4.0 &lt;2.4.7) - Fixes the issue where the *[!UICONTROL Cart Price Rule]* ）在產品具有空屬性時使用抵用券代碼應用。
* **ACSD-54324** （用於Adobe Systems商務>=2.4.5 &lt;2.4.7) - Fixes the issue where the GraphQL requisition_lists request does not consider pagination settings and returns all results.
* 更新修補程式：MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (適用於Adobe Commerce >=2.4.0 &lt;2.4.6) — 修正無法處理針對具有多個指派來源的產品所提交的B2B報價的問題。
* **ACSD-54040** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6) — 修正啟用B2B模組時，*[!UICONTROL Created]*&#x200B;欄位空白的問題，以取得詳細資訊。
* **ACSD-54319** （用於Adobe Systems商務和Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where the product price shows zero in the *[!UICONTROL Product in Cart]* 報告。
* **ACSD-53378** （用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.7) - Improves checkout page load time for customers who have large address books.
* **ACSD-52657** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正使用子網域的次要商店未更新minicart的問題。
* **ACSD-53414** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正受限管理員使用者可在其許可權範圍以外看到CMS頁面的問題。
* **ACSD-54472** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正被拒絕公司的客戶仍可驗證，以及被封鎖和被拒絕公司的客戶仍可下訂單的問題。 此修補程式新增了GraphQL端點的額外驗證。
* **ACSD-52801** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 新增在GraphQL中搜尋產品時進行部分比對的選項。
* **ACSD-55004** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正上傳大於`php.ini`中設定值的匯入檔案時，驗證器當機的問題。
* **ACSD-54989** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) — 修正當&#x200B;*[!UICONTROL Enable Purchase Orders]*&#x200B;設為&#x200B;*[!UICONTROL Yes]*&#x200B;且&#x200B;*[!UICONTROL Purchase Order]*&#x200B;設為&#x200B;*[!UICONTROL No]*&#x200B;時，公司管理員無法下訂單的問題。
* **ACSD-54007** (適用於Adobe Commerce及Magento Open Source>=2.4.0 &lt;2.4.7) — 修正匯入客戶資料時的錯誤&#x200B;*「未定義的陣列機碼&quot;_scope&quot;*。
* **ACSD-55031** (適用於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修正&#x200B;*型別「混合」在編譯期間不可為nullable*&#x200B;錯誤。
* **ACSD-54961** (適用於Adobe Commerce及Magento Open Source>=2.4.0 &lt;2.4.7) — 修正受限管理員使用者無法大量更新&#x200B;*產品評論*&#x200B;狀態的問題。
* **ACSD-55256** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正影像滑桿中僅成功顯示第一個影像的問題。
* 更新修補程式：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (適用於Adobe Commerce >=2.4.0 &lt;2.4.7) — 修正獎勵點到期後獎勵點餘額歷史記錄計算錯誤的問題。
* **ACSD-53583** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 改善&#x200B;*類別產品*&#x200B;和&#x200B;*產品類別*&#x200B;索引器的部分重新索引效能。
* **ACSD-54026** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正非授權使用者`updateCompanyRole` GraphQL請求的不正確錯誤訊息。
* **ACSD-54106** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5) — 修正土耳其文重音字元依名稱排序的類別產品錯誤問題。
* **ACSD-52219** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正經常在書籤檢視之間切換時，管理員格線儲存的篩選器無法如預期運作的問題。
* **ACSD-54342** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修正不正確的錯誤訊息&#x200B;*資料結構中的錯誤：匯入沒有有效資料的CSV檔案時，會混合值*。
* **ACSD-54660** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 已新增輸入屬性&#x200B;*sort*，以便在GraphQL中依`sort_field`和`sort_direction`排序客戶訂單。
* **ACSD-54776** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正未核取的&#x200B;*[!UICONTROL Use Default Value]*&#x200B;及非預設產品欄位值未儲存至第二個網站、商店及商店檢視的問題。
* **ACSD-53998** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p2 &lt;2.4.5) || >=2.4.5-p1 &lt;2.4.7) — 修正從客戶帳戶登出後，以&#x200B;**[!UICONTROL Customer Segment]**&#x200B;為基礎的&#x200B;**[!UICONTROL Dynamic Block]**&#x200B;無法正常運作的問題。
* **ACSD-53204** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正&#x200B;*無法儲存產品。使用`rest/V1/products/<sku>/media`端點同時要求將影像新增至產品相簿時發生*&#x200B;錯誤。
* **ACSD-47657** （用於Adobe Systems商務和Magento Open Source >=2.4.4 &lt;2.4.7) - Added a caching mechanism for AWS credentials. 認證提供者現在會使用Magento快取來快取從AWS擷取的認證，以進行EC2設定。
* 更新修補程式：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4) — 修正執行部分索引時，指派給共用目錄的產品未出現在店面的問題。
* **ACSD-54018** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.6) — 修正Widget條件中使用非全域屬性的[!UICONTROL Product List]介面工具集的效能問題。
* **ACSD-54111** （用於Adobe Systems商務和Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where the product thumbnail images are not displayed on the storefront when the aspect ratio of the watermark image does not match the product image.
* **ACSD-47669** （用於Adobe Systems商務和Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes *完整性約束衝突：1452 無法添加或更新子行：導入產品時外鍵約束失敗* 錯誤CSV。
* **ACSD-53347** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the price indexer takes too much time to execute.
* **ACSD-52287** （用於Adobe Systems商務>=2.3.7 &lt;2.4.7) - Fixes the issue with incorrect order status in the archived order grid when asynchronous grid indexing is enabled.
* **ACSD-52929** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue with redundant requests to reindex default source items when the inventory indexer is configured in async mode.
* **ACSD-53824** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正`setup:upgrade`期間`UpdateMultiselectAttributesBackendTypes`移轉資料修補程式超過資料庫交易大小限制的問題。

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正即使未透過REST API更新`Inventory_source`專案，快取和索引也會重新整理的問題。
* **ACSD-51884** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.7) — 修正執行調整大小命令後，產品影像快取路徑不正確的問題。
* **ACSD-53628** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正CSV銷售訂單報告顯示不正確的特殊字元的問題。
* **ACSD-53148** （用於Adobe Systems商務和Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where two parallel requests in GraphQL for adding the same configurable product to the cart resulted in two separate items on the cart with the same product SKU.
* **ACSD-52606**（用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the error message *當用戶按兩下&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**時，將顯示您的訂單尚未準備好取件*。
* **ACSD-51574** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正將影像取代為具有相同名稱的另一個影像後，影像沒有在前端更新的問題。
* **ACSD-53728** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正產品EAV索引器需要更長時間才能完成的問題。
* **ACSD-53979** （用於Adobe Systems商務和Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the JS issue that occurs on the homepage if the welcome message contains a single quote.
* **ACSD-52085** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正產品輪播中看不到可設定產品的特殊價格的問題。
* **ACSD-53795** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正`indexer_update_all_views` cron工作中資料型別無效的問題。
* **ACSD-52143** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正產品匯入後移除自訂選項的問題。
* **ACSD-53750** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修正多重執行緒`catalog_product_price`重新索引期間的&#x200B;*中斷管道或關閉的連線*&#x200B;錯誤。
* **ACSD-49843** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.7) — 修正啟用&#x200B;**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**&#x200B;設定之線上付款方式自動開立訂購專案的發票後，無法使用產品下載連結的問題。
* **ACSD-47054** (適用於Adobe Commerce >=2.4.2 &lt;2.4.6) — 修正預覽重新索引為所有存放區執行重新索引，導致速度緩慢的問題。
* 新增了 ACSD-46541、ACSD-47079 的新版本。
* ACSD-49970-v3已取代為ACSD-54095。

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (適用於Adobe Commerce且Magento Open Source >=2.4.3 &lt; 2.4.6) — 修正清查索引子在「依排程更新」模式中清除所有快取的問題。
* **ACSD-50887** (適用於Adobe Commerce及Magento Open Source>=2.4.0 &lt;2.4.7) — 修正產品屬性屬性&#x200B;*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;可設為&#x200B;*是*，而非&#x200B;*[!UICONTROL Use in search]*&#x200B;選項設為&#x200B;*是*&#x200B;的問題。
* **ACSD-51846** （用於Adobe Systems商務和 Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Fixes the *由於未驗證所有級別的 REST API 有效負載而發生的內部錯誤* 問題。
* **ACSD-52906** （用於Adobe Systems商務>=2.3.7 &lt;2.4.7) - Fixes the issue where the X-Magento-Vary cookie is set incorrectly for logged-in customers that belong to the same customer segment causing improper caching for some pages.
* **ACSD-52736** （適用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where a *包含可配置產品數量要求的購物車價格規則* 無法按預期工作。
* **ACSD-47875** (適用於Adobe Commerce及Magento Open Source>=2.3.7 &lt;2.4.7) — 修正管理員使用者無法針對具有詳細目錄管理的特定商店檢視範圍，從管理員將產品新增到客戶購物車的問題。
* **ACSD-53176** （用於Adobe Systems商務 >=2.3.7 &lt;2.4.5) - Fixes the issue where *相關產品規則* 是 *條件之一* 不匹配產品。
* **ACSD-51666** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the error *會話已過期，請再次登入。在客戶嘗試登入後發生的*。
* 已新增MDVA-39305-v2的新版本。
* 更新ACSD-19640的需求。

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the default shipping address on the checkout shipping step is auto-populated with a previously selected in-store pickup address.
* **ACSD-52041** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where the error message: *[ERROR] [!DNL Page Builder] was rendering for 5 seconds without releasing locks.* 儲存內容编辑時 [!DNL Page Builder]出現在鉻黃 瀏覽器中。
* **ACSD-52095** （用於Adobe Systems商務和 Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where the `manage_stock` 值在產品匯出后的CSV檔中錯誤地設置為 0。
* **ACSD-51358** （用於Adobe Systems商務>=2.4.5 &lt;2.4.7) - Fixes the issue where removing a scheduled update without an end date leads to removing other scheduled updates for the same entity.
* **ACSD-48070** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正編輯已排程更新時觸發例外狀況的問題。
* **ACSD-51890** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正可多次點選「[!UICONTROL Submit review]」按鈕而無需[!DNL Google reCAPTCHA] v3驗證的問題。
* **ACSD-51984** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正未核取第二個網站、商店和商店檢視的&#x200B;*[!UICONTROL Use Default Value]*&#x200B;和&#x200B;*[!UICONTROL non-default product field]*&#x200B;值未儲存的問題。
* **ACSD-52398** （用于Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the error *嘗試更新店面購物車中捆綁產品的數量時，請求的數量不可用* 。
* **ACSD-52786** （用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where a catalog rule condition *SKU* 適用於以給定SKU開頭的所有產品。
* **ACSD-52921** （用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where an internal error occurs if requesting cart details from GraphQL when there is an out-of-stock configurable product in the cart.
* **ACSD-51683** （用於Adobe Systems商務和Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a customizable option can&#39;t be added to the cart using GraphQL.
* **ACSD-52133** （用於Adobe Systems商業和Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a customer account cannot be saved after an upgrade.
* **ACSD-52202** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the salable qty of default stock wrongly changes to 0 when a non-default stock is changed to 0 qty on order fulfillment.
* **ACSD-51265** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue with `catalog_product_price` reindexing performance when there are too many bundled products in the system.
* **ACSD-52831** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正啟用[!DNL Google reCAPTCHA v3 Invisible]時，客戶無法下可轉讓報價單的問題。
* **ACSD-51845** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正無法透過非同步大量REST API更新具有層級價格及不同屬性集的後續產品的問題。
* **ACSD-52815** (適用於Adobe Commerce且Magento Open Source >=2.3.7 &lt;2.4.7) — 修正非預設來源之數量欄位輸入最多只支援6位數的問題，預設庫存則支援8位。
* **ACSD-51149** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正具有已啟用目錄許可權的已排程ImportExport使索引器失效，然後由cron快取排清的問題。
* **ACSD-50815** (適用於Adobe Commerce且Magento Open Source>=2.4.5 &lt;2.4.6) — 修正簡單產品的小數數量無法用於新套件產品選項的問題。
* ACSD-47803的更新版本。
* 更新ACSD-51892的標題。
* 更新ACSD-51379。
* 更新ACSD-49970-v2。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正在Admin中建立新訂單時，管理員使用者在選取商店檢視後未正確重新導向的問題。
* **ACSD-50813** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正管理員無法在具有[!UICONTROL Add Products by SKU]功能的SKU中新增包含斜線的套件產品至管理員訂單的問題。
* **ACSD-51630** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正大量系統訊息會減緩管理員頁面下載速度的問題。
* **ACSD-51853** (適用於Adobe Commerce及Magento Open Source >=2.4.1 &lt;2.4.7) — 修正使用[!UICONTROL Page Builder]時未套用複製文字樣式的問題。
* **ACSD-52160** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修正未根據規則條件「如果在購物車中找到/找不到專案，且全部滿足上述任何條件」正確評估購物車價格規則之產品驗證結果的問題。
* **ACSD-51636** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正公司管理員無法從客戶帳戶區段新增使用者（儘管擁有所有必要的角色和許可權）的問題。
* **ACSD-51739** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正在CompanyTeam GraphQL要求中要求`structure_id`時傳回錯誤的問題。
* **ACSD-51857** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正大型sales_order和`sales_order_item`資料庫表格上`aggregate_sales_report_bestsellers_data` cron報告效能緩慢的問題，此問題是因為寫入主要資料查詢的方式所導致。
* **ACSD-48448** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正取消訂單期間發生競爭條件問題，導致`inventory_reservation`表格中出現重複專案的問題。
* **ACSD-52689** (適用於Adobe Commerce及Magento Open Source >=2.4.3 &lt;2.4.6) — 修正無法使用REST API將影像上傳至Amazon S3儲存空間的問題。
* **B2B-2674** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 新增快取功能至1customAttributeMetadata1 GraphQL查詢。
* 已新增ACSD-44938的新版本。
* 新增ACSD-46988的需求。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 修正資料庫傾印包含觸發程式和&#x200B;*分隔符號* SQL命令時的資料庫復原命令。
* **ACSD-50512** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正&#x200B;*錯誤：可下載的連結與產品無關。 請驗證連結，然後再試一次。更新可下載產品臨時更新的開始日期時發生*&#x200B;個錯誤。
* **ACSD-50949** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正進階搜尋中的價格篩選器在搭配SKU篩選器使用時未傳回正確結果的問題。
* **ACSD-51645** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正擴充功能`Magento_OfflineShipping`停用時，儲存新購物車價格規則時擲回的錯誤。
* **ACSD-50895** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正未設定[!DNL Google Analytics] 4 GTM時無法引發[!DNL Google Analytics] 3 GTM標籤的問題。
* **ACSD-51102** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正排程更新啟用規則時，套用至大量產品的目錄規則未正確編制索引的問題。
* **通過異步 REST API 或異步批量 REST API 創建客戶時，將忽略 ACSD-50368** （用於 Adobe Systems Commerce 和 Magento Open Source >= 2.4.3 &lt;2.4.5) - Fixes the issue where the customer&#39;s `group_id` ）。
* **ACSD-51497** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.0 ||=&quot;&quot;>= 2.4.1 &lt;2.4.7) - Fixes the issue where a customer can&#39;t sort a catalog page by Custom Attribute of the dropdown type.&lt;/2.4.0>
* **ACSD-51408** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt; 2.4.7) - Fixes the issue where the order item status is incorrectly set to *[!UICONTROL Backordered]*。
* **ACSD-51735**（用於Adobe Systems商務，當產品庫存為 *0* 時，Magento Open Source >=2.4.4&lt;2.4.5) - Fixes the issue where the order item status is incorrectly set to *[!UICONTROL Ordered]*。
* **ACSD-51792** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正啟用[!DNL Google Tag Manager] 4時頁面沒有曝光事件的問題。
* **ACSD-51471** (適用於Adobe Commerce >=2.4.3 &lt;2.4.7) — 修正管理員使用者無法針對使用簡單產品（本身已有排程更新）的套件產品儲存排程更新的問題。
* **ACSD-51700** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正在Admin的可下載產品編輯頁面上切換商店檢視時發生的錯誤。
* **ACSD-51120** (適用於Adobe Commerce >=2.3.7 &lt;2.4.3) — 修正包含透過中繼更新更新的GraphQL區塊的CMS頁面未清除CMSGET要求快取的問題。
* **ACSD-51240** (適用於Adobe Commerce >=2.4.4 &lt;2.4.6) — 修正透過公司登錄檔格進行註冊時，所上傳檔案遺失的問題。
* **ACSD-51907** （用於Adobe Systems商務>=2.4.2 &lt;2.4.3) - Fixes the issue where a restricted admin user cannot create a credit memo with an offline refund.
* **ACSD-52148** （用於Adobe Systems商務和 Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where the [!DNL Google V3 reCAPTCHA] 管理登入偶爾會失敗。
* **ACSD-51431** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正即使變更記錄檔中沒有新專案，索引子狀態為&#x200B;*正在運作*&#x200B;的問題。
* **ACSD-51892** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正設定檔案載入多次的效能問題。
* 已棄用ACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正[!UICONTROL Page Builder's]多個錯誤導致管理員無法儲存沒有內容許可權的產品的問題。
* **ACSD-51305** (適用於Adobe Commerce及Magento Open Source >=2.4.6 &lt;2.4.7) — 修正GraphQL回應中無法使用無庫存可設定子產品的問題。
* **ACSD-50621** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正嘗試在多網站環境中編輯共用目錄中不同網站的[!UICONTROL Tier Prices]時，無法顯示的問題。
* **ACSD-51041** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.6) — 改善價格索引器的效能。
* **ACSD-51379** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.7) — 修正無法透過[!UICONTROL Page Builder]儲存對頁面文字內容所做變更的問題。
* **ACSD-49480** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正僅將一個購物車價格規則套用至購物車的問題。
* **ACSD-51230** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正處理訂單中簡單產品的部分退款時，禮品卡帳戶遭到刪除的問題。
* **ACSD-51238** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正更新可設定產品及編輯價格時移除庫存來源的問題。
* **ACSD-50794** (適用於Adobe Commerce >=2.4.1 &lt;2.4.7) — 修正透過GraphQL移除禮品訊息或禮品包裝時，資料庫中未更新禮品訊息或禮品包裝詳細資料的問題。
* **ACSD-51528** (適用於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修正&#x200B;*sales_order*&#x200B;表格中&#x200B;*x_forwarded_for*&#x200B;欄含有null值的問題。
* **ACSD-50849** (適用於Adobe Commerce >=2.4.4 &lt;2.4.6) — 修正清除快取後將新產品新增至類別，導致現有產品的位置和選擇不符的問題。
* **ACSD-51294** (適用於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修正GTM/GA價格、數量、稅金、送貨和收入以字串形式傳送至[!DNL Google Analytics]和GTM的問題。
* **ACSD-51204** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正建立銷退折讓單後已完全銷售的產品未退還存貨的問題。
* **ACSD-51291** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.4-p4) || >=2.4.5 &lt;2.4.5-p3) — 修正限制管理員存取一個網站後，可以將影像/影片新增至指派給多個網站之產品的問題。
* 已新增ACSD-50336的新版本。
* 已取代ACSD-49970修補程式。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4) || >=2.4.4-p1 &lt;2.4.6) — 修正Recaptcha v2在提交失敗的付款後未重新載入的問題。
* **ACSD-50817** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 最佳化Cron工作`sales_clean_quotes`以更快執行。
* **ACSD-49392** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) — 修正當套件產品的部分退款後，訂單狀態變更為已關閉的問題。
* **ACSD-51036** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正同時執行REST API呼叫期間的競爭條件導致[!UICONTROL Items Ordered]表格中出貨狀態資訊覆寫的問題。
* **ACSD-50858** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 改善載入橫幅內容的效能。
* 已新增MDVA-39305-v2、ACSD-45169的新版本。
* 更新修補程式ACSD-50260-v2。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** （用於Adobe Systems商務和Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Fixes the issue where product alert emails are not sent when a product is back in stock or the price is changed.
* **ACSD-50367** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where customer address export does not work when a multi-select customer address attribute without values is created.
* **ACSD-49877** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where video autoplay does not work on mobile [!DNL Safari] ，當視頻直接連結到遠端視頻檔而不是流服務時。
* **ACSD-50165** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the error *無法刪除該檔。 警告！取消連結：從管理員刷新 JS/CSS 快取時沒有此類文件或目錄* 。
* **ACSD-49737** (適用於Adobe Commerce和Magento Open Source >=2.4.1-p1 &lt;2.4.7) — 修正卡付款失敗後，優惠券被錯誤地標示為使用的問題。
* **ACSD-50814** (適用於Adobe Commerce及Magento Open Source >=2.4.6 &lt;2.4.7) — 修正管理員使用者無法建立銷退折讓單的問題。
* **ACSD-50116** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.7) — 修正管理員使用者無法建立3級或更低子類別層級URL重寫的問題。
* **ACSD-49513** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5) — 修正遠端儲存體同步作業因0位元組檔案而失敗的問題。
* **ACSD-46683** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正送貨價格顯示&#x200B;*尚未計算*&#x200B;的問題。
* **ACSD-49129** （用於Adobe Systems商務和 Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where the *[!UICONTROL content]* 屬性（base64 圖像代碼）不會在產品媒體 API 回應中 `rest/V1/products/sku/media` 返回。
* **ACSD-50276** （適用於Adobe Systems商務>=2.4.0 &lt;2.4.7) - Fixes the issue where the customer registration form doesn&#39;t work on the storefront if a multi-select customer attribute is created.
* **ACSD-50527** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正儲存具有空白動態區塊的頁面時發生的錯誤。
* **ACSD-49973** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 改善透過GraphQL擷取套件產品的效能。
* **ACSD-51114** （用於Adobe Systems商務和Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a random product disappears from large catalogs when asynchronous indexing is enabled. 改進了大型目錄的異步重新索引的性能。
* **B2B-2598** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 將快取功能新增到[!UICONTROL availableStores]、[!UICONTROL countries]、[!UICONTROL country]、[!UICONTROL currency]和[!UICONTROL storeConfig]個GraphQL查詢。
* 已新增MDVA-42806、ACSD-48627、ACSD-46815的新版本。
* 更新ACSD-49773、ACSD-47179、ACSD-48300的修補程式中繼資料。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (適用於Adobe Commerce及Magento Open Source >=2.4.0 &lt;2.4.7) — 修正當訂單無法收取時，API會傳送準備收取電子郵件的問題。
* **ACSD-49822** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正[!UICONTROL Requisition List]頁面中的更新未反映在[!UICONTROL Print Requisition List]上的問題。
* **ACSD-48771** （適用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue with upgrading the column-block content type from older [!DNL Page Builder] 版本。
* **ACSD-49464** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正當orderId不同時，發票、出貨及銷退折讓單不會從封存移回的問題。
* **ACSD-49773** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正使用AWS S3作為遠端儲存體時，產品匯出失敗的問題。
* **ACSD-49748** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正無法傳送邀請的問題。
* **ACSD-49502** (適用於Adobe Commerce >=2.4.3 &lt;2.4.7) — 修正將中繼更新套用至可下載產品後，可下載連結未正確更新的問題。
* **ACSD-49527** （用於Adobe Systems商務>=2.4.2 &lt;2.4.7) - Fixes the issue where GraphQL company roles don&#39;t display pagination correctly.
* **ACSD-49706** （用於Adobe Systems商務和Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the default value is saved for a visual swatch attribute when no value is selected.
* **ACSD-49835** (適用於Adobe Commerce及Magento Open Source >=2.4.5 &lt;2.4.7) — 修正多選屬性的存放區層級未正確儲存「使用預設核取方塊值」的問題。
* **ACSD-49898** (適用於Adobe Commerce且Magento Open Source >=2.4.4 &lt;2.4.6) — 修正當套件產品的特殊價格超過1000時，產品格線擲回例外狀況的問題。
* **ACSD-50234** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.5) — 修正向[!DNL PayPal]下訂單時，確認電子郵件中客戶名稱錯誤的問題。
* **ACSD-49960** (適用於Adobe Commerce及Magento Open Source >=2.4.5 &lt;2.4.7) — 修正客戶訂單格線無法依日期篩選的問題。
* **ACSD-49849** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正透過GraphQL以[!DNL PayPal Express]下訂單時，客戶電子郵件被[!DNL PayPal]電子郵件取代的問題。
* **ACSD-49839** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正當產品在SKU中有單引號或雙引號時，共用目錄定價和結構會在Admin中擲回錯誤的問題。
* **ACSD-49970** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正開啟[!DNL New Relic]報告功能時，GraphQL錯誤的不正確處理。
* **ACSD-50260** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正GraphQL產品搜尋結果限製為僅限10,000個結果的問題。
* **ACSD-48813** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正搜尋未根據屬性的搜尋權重顯示相關結果的問題。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.3) — 修正根據「是/否」屬性建立的目錄價格規則未考量所選取範圍的問題。
* **ACSD-47704** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.7) — 修正套件產品僅顯示庫存產品價格的問題。
* **ACSD-49370** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正GraphQL結構描述中&#x200B;*日期時間*&#x200B;產品屬性具有&#x200B;*FilterMatchTypeInput*&#x200B;型別的問題。
* **ACSD-48807** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.7) — 修正透過GraphQL商店評論未篩選客戶產品評論的問題。
* **ACSD-49433** (適用於Adobe Commerce及Magento Open Source >=2.4.3 &lt;2.4.7) — 修正購物車中，針對未結金額的禮品卡，以小計顯示預設金額的問題。
* **ACSD-48866** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正要求類別的RSS摘要時發生錯誤的問題。
* **ACSD-48784** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正客戶群組之間不正確快取客戶區段價格的問題。
* **ACSD-48857** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正使用者在使用頁面產生器編輯後無法儲存變更的問題。
* **ACSD-49065** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.7) — 修正僅指派給自訂庫存時，管理員中看不到報價專案的問題。
* **ACSD-49179** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正不同商店使用不同貨幣時，訂單報表顯示不正確金額的問題。
* **ACSD-49286** (適用於Adobe Commerce及Magento Open Source >=2.4.3 &lt;2.4.7) — 修正當頁面上出現多個產品Widget時，產品會新增至購物車兩次的問題。
* **ACSD-49574** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 新增功能以透過GraphQL支援購物車中的禮品卡產品更新。
* 更新修補程式：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (適用於Adobe Commerce >=2.4.1 &lt;2.4.7) — 修正使用可協商報價下訂單時，使用預設送貨地址而非新送貨地址的問題。
* **ACSD-48059** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正商家無法儲存類別中「[!UICONTROL Match product by rule]」的問題。
* **ACSD-48216** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修正[!UICONTROL UPDATE]作業中[!UICONTROL inventory_source_item]資料表的[!UICONTROL AUTO_INCREMENT]增加的問題。
* **ACSD-47908** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修正結帳期間，在出貨步驟上選取來源和數量時，出現「預期值小於或等於0」的錯誤。
* **ACSD-49497** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.6) — 修正訂單在出貨後仍維持處理狀態且套用部分退款的問題。
* **ACSD-48694** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) — 修正錯誤「要求的狀態變更無效」導致客戶無法下訂單的問題。
* **ACSD-49013** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正使用大量API建立客戶時，電子郵件確認未轉譯為網站地區設定的問題。
* **ACSD-48164** (適用於Adobe Commerce及Magento Open Source >=2.3.7 &lt;2.4.7) — 修正受限管理員無法儲存網站層級值的問題。
* **ACSD-48404** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修正按瀏覽器的上一頁按鈕時，「記住類別分頁=是」會導致錯誤的問題。
* **ACSD-48634** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 啟用「[!UICONTROL Google Analytics Content Experiments]」時，修正測試更新頁面上的JS錯誤。
* **ACSD-49042** (適用於Adobe Commerce及Magento Open Source >=2.4.4 &lt;2.4.5) — 修正無法從店面訂購無限延期交貨的產品的問題。
* 更新修補程式：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (適用於Adobe Commerce和Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) — 修正由於應用程式層級的快取而不一定傳送價格下降通知的問題。
* **ACSD-48661** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正當公司的信用額度大於999時，逗號分隔符號會因驗證錯誤而無法儲存公司的問題。
* **ACSD-48773** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正從錯誤商店取得獎勵點數電子郵件範本的問題。
* **ACSD-48587** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正產品Widget比對規則中HTML特殊字元導致其無法顯示相符產品的問題。
* **ACSD-48212** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正產品匯入將產品指派給錯誤來源的問題。
* **ACSD-47988** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正產品匯出會從頁面產生器產品說明中裁剪HTML標籤的問題。
* **ACSD-48366** (適用於Adobe Commerce及Magento Open Source >=2.4.4 &lt;2.4.6) — 修正產品影像未顯示在「補貨」電子郵件範本上的問題。
* **ACSD-48417** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正建立產品的排程變更並儲存另一個產品後出現SQL錯誤的問題。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正未將套件組合產品指派給任何網站時，產品價格重新索引無法運作的問題。
* **ACSD-48262** (適用於Adobe Commerce及Magento Open Source >=2.4.5 &lt;2.4.6) — 修正「允許每頁所有產品」設定設為「是」時，前端不會顯示產品的問題。
* **ACSD-48293** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4) — 修正當已售出的子產品恢復庫存時，複合產品缺貨的問題。
* **ACSD-47520** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正建立銷退折讓單時客戶遺失獎勵點數的問題。
* **ACSD-48044** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正將多張禮品卡套用至有多張送貨的單張訂單時，無法下單的問題。
* **ACSD-48300** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where a return cannot be created if the configurable product is removed.
* **ACSD-47910** （用於Adobe Systems商務和Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue of missing orders, invoices, shipments, and credit memos in respective entity grids.
* **ACSD-47292** （用於Adobe Systems商務和Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where out-of-stock bundled products are not available in the GraphQL response if the &quot;show out-of-stock products&quot; is set to Yes.
* **ACSD-48234** （用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the catalog search result shows an incorrect category item count when the &quot;show out of stock&quot; option is enabled.
* **ACSD-48313** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5) — 修正屬性值包含逗號時無法剖析「configurable_variations」欄的問題。 「additional_attributes」會使用相同的剖析演演算法。
* **ACSD-48627** （用於Adobe Systems商務和Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the out-of-stock configurable product causes an error when sending a GraphQL request to get cart details.
* 更新補丁：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** （用于Adobe Systems商務和 Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where SEO-friendly URLs are not generated for products that have *url_key* 属性在 商店-視圖 級別被覆蓋。
* **ACSD-46865** （用於Adobe Systems商務和Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the Shipment and Credit Memo grid is not populated when asynchronous indexing is enabled.
* **ACSD-47004** (適用於Adobe Commerce及Magento Open Source >=2.4.2 &lt;2.4.6) — 修正無VAT ID的帳單地址未套用VAT的問題。
* **ACSD-47803** (適用於Adobe Commerce及Magento Open Source >=2.4.0 &lt;2.4.6) — 修正無庫存可設定產品色票顯示為可用色票的問題。
* **ACSD-47137** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 當pub/media資料夾非常大時，提升影像庫的載入速度。
* **ACSD-46770** (適用於Adobe Commerce及Magento Open Source>=2.4.0 &lt;2.4.6) — 修正即使未勾選&#x200B;*電子郵件訂單確認*，仍會傳送管理員訂單電子郵件的問題。
* **ACSD-47955** (適用於Adobe Commerce及Magento Open Source >=2.4.4 &lt;2.4.6) — 修正GraphQL未正確顯示購物車折扣的問題。
* **ACSD-46617** (適用於Adobe Commerce及Magento Open Source>=2.4.0 &lt;2.4.6) — 修正即使小計大於設定的&#x200B;*最小訂購量*，*繼續結帳*&#x200B;按鈕仍會呈現灰色的問題。
* **ACSD-47079** (適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修正當子產品庫存狀態透過REST APIPOST/rest/V1/inventory/source-items變更時，複合產品（套件、分組和可設定）庫存狀態未更新的問題。
* **ACSD-47336** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正&#x200B;*發生錯誤。在Commerce管理員中關閉通知時發生*&#x200B;錯誤。
* **ACSD-47559** (適用於Adobe Commerce及Magento Open Source >=2.4.0 &lt;2.4.6) — 修正預覽電子郵件範本區域未完全可見的問題。
* **ACSD-47920** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正在&#x200B;*允許訪客結帳*&#x200B;關閉時，透過Rest API以訪客使用者身分下訂單的問題。
* 已取代的修補程式：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (適用於Adobe Commerce及Magento Open Source >=2.4.0 &lt;2.4.6) — 修正具有特定範圍受限存取權的管理員無法刪除產品評論的問題。
* **ACSD-47107** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5) — 修正將目錄價格規則折扣套用至自訂產品選項的問題。
* **ACSD-47232** (適用於Adobe Commerce及Magento Open Source >=2.4.0 &lt;2.4.6) — 修正無法在Admin中套用具有總權重條件的優惠券的問題。
* **ACSD-46519** (適用於Adobe Commerce且Magento Open Source >=2.4.1 &lt;2.4.6) — 修正GraphQL categoryList要求傳回錨點類別不正確product_count的問題。
* **ACSD-47027** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正更新緩慢的CompanyRole GraphQL請求。
* **ACSD-47666** (適用於Adobe Commerce及Magento Open Source>=2.4.0 &lt;2.4.6) — 修正「管理員>系統>許可權>使用者角色>角色>角色使用者」格線中無法運作篩選功能的問題。
* **ACSD-47497** (適用於Adobe Commerce及Magento Open Source >=2.4.0 &lt;2.4.6) — 修正「管理」下的「設定」中未顯示「服務」索引標籤的問題。
* 更新修補程式：ACSD-47743。
* 已取代的修補程式：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3) — 修正當存取PHP 7.4上已知產品的特定非現有類別路徑時，_嘗試存取型別bool值的陣列位移_&#x200B;錯誤。
* **ACSD-47332** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正cron失敗的問題，並只在00:00到00:59 UTC之間執行時回報錯誤。
* **ACSD-47280** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正在特定範圍上停用共用目錄功能無法正常運作的問題。
* **ACSD-47106** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正無法在公司建立頁面上的新自訂屬性中儲存值的問題。
* 更新修補程式：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (適用於Adobe Commerce及Magento Open Source >=2.4.2 &lt;2.4.6) — 修正使用者在指派大量產品來源時會發生錯誤的問題。
* **ACSD-46856** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 透過「系統>設定>匯入>進階價格」，改善效能並更新層級價格。
* **ACSD-46541** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where an admin user cannot create a credit memo if an order item is deleted.
* **ACSD-46581** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the estimated tax total is not updated after selecting a country in the shopping cart.
* **ACSD-46618** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the product list widget shows incorrect cached prices for a logged-in customer.
* **ACSD-46674** （用於Adobe Systems商務和Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where custom options of an image type are displayed as HTML in customer emails.
* **ACSD-46988** （用於Adobe Systems商務和Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the GraphQL &#39;currency&#39; API Request returns NULL values for a custom currency.
* **ACSD-47076** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5) — 修正無法在店面播放Vimeo影片的問題。
* **ACSD-45071** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4) — 修正匯入期間將預設來源新增至產品的問題。
* **AC-3023** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 將DHL配置更新至最新版本10.0。
* 更新修補程式：MDVA-42584。
* 已取代修補程式：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5*) — 修正使用者使用商店信用退款時取得錯誤訂單狀態的問題。
* **ACSD-46703** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6*) — 修正無法在產品編輯頁面上拖放自訂選項的問題。
* **ACSD-44851** (*用於Adobe Commerce，且Magento Open Source>=2.4.0 &lt;2.4.6*) — 修正具有子類別的類別無法開啟或展開的問題。
* **ACSD-46815** (*適用於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6*) — 修正類別樹狀結構請求限製為20個類別的問題。
* **ACSD-45675** (*用於Adobe Commerce且Magento Open Source>=2.4.0 &lt;2.4.6*) — 修正產品匯出使用&#x200B;*預設商店檢視*&#x200B;範圍內的類別名稱的問題。
* **ACSD-46869** (*適用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修正購物車中的可設定產品未透過&#x200B;*PUTREST API*&#x200B;請求更新而不變更產品數量的問題。
* **MDVA-42768-V2** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正當&#x200B;*顯示無庫存*&#x200B;為&#x200B;*是*&#x200B;時，可設定產品將一般價格顯示為&#x200B;*0*&#x200B;的問題。
* 更新修補程式：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 已棄用的修補程式：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*用於Adobe Commerce且Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正類別樹狀結構請求限製為20個類別的問題。
* **ACSD-45781** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.2*) — 修正行動裝置上未顯示商店前方搜尋欄位的問題。
* **ACSD-46192** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;2.4.5*) — 修正使用`async/bulk/V1/configurable-products/bySku/options`端點的問題。
* **ACSD-46404** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5*) — 修正管理員使用者在升級至2.4.4後無法登入的問題。
* 更新修補程式：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*適用於Adobe Commerce且Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正特定商店的GraphQL產品突變傳回所有可設定變體的問題，包括未指派給請求商店的變體。
* **ACSD-46146** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修正管理員下單後傳送兩封訂單確認電子郵件的問題。
* **ACSD-45255** (*適用於Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修正受限管理員使用者的「低庫存報告」頁面上的例外狀況。
* **ACSD-45488** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6*) — 修正具有多個來源的可設定產品未自動傳回庫存的問題。
* **ACSD-45754** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修正將優惠券套用至購物車後未新增獎勵點數的問題。
* **ACSD-45849** (*適用於Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修正套用中繼更新後視訊中繼資料遺失的問題。
* **ACSD-45257** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.4*) — 修正GraphQL未正確顯示購物車折扣的問題。
* **ACSD-44938** (*適用於Adobe Commerce且Magento Open Source>=2.4.0 &lt;2.4.4*) — 修正無法在GraphQL要求中套用`VAT_ID`適用於訪客使用者的問題。
* 更新修補程式：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*用於Adobe Commerce，且Magento Open Source>=2.3.5 &lt;2.4.4*) — 修正建立銷退折讓單後虛擬產品存貨數量計算錯誤的問題。
* **ACSD-43887** (*適用於Adobe Commerce且Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正啟用「公司採購訂單」時，結帳付款頁面上顯示不正確詳細資訊的問題。
* **ACSD-45143** (*適用於Adobe Commerce且Magento Open Source>=2.4.0 &lt;2.4.5*) — 修正`setShippingAddressesOnCart`突變不允許將數值區碼設為&#x200B;*region*&#x200B;的問題。
* **ACSD-44591** (*用於Adobe Commerce且Magento Open Source>=2.4.3 &lt;2.4.6*) — 修正未通過驗證碼確認下訂單時發生的錯誤。
* **ACSD-45520** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修正使用者從購物車編輯可設定產品時，未在產品詳細資料頁面上預先選取色票選項的問題。
* **ACSD-45169** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6*) — 修正套用中繼更新後，[!DNL Visual Merchandiser]無法顯示可設定產品正確庫存和價格的問題。
* **ACSD-45424** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.6*) — 修正部分退款（銷退折讓單）後建立錯誤預訂補償的問題。
* **MDVA-42807** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修正商店前方未顯示自訂貨幣符號的問題。
* 更新修補程式：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*適用於Adobe Commerce，且Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正限制管理員使用者的「訂單」報表中訂單總計計算錯誤的問題。
* **MDVA-44940** (*用於Adobe Commerce，且Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正從管理員儲存類別時發生的SQL錯誤。
* **MDVA-44562** (*用於Adobe Commerce和Magento Open Source GraphQL>=2.4.0 &lt;2.4.2-p2*) — 修正預設商店ID覆寫報價專案的非預設商店ID的問題，儘管該請求源自非預設商店檢視。
* **MDVA-43167** (*適用於Adobe Commerce，且Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正當管理員使用者選取所有訂單時，管理員訂單格線整批動作不適用於多頁的問題。
* **MDVA-44044** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.2-p2*) — 修正將產品指派至新網站後，產品未顯示在類別頁面上的問題。
* **MDVA-42509** (*適用於Adobe Commerce且Magento Open Source>=2.3.3 &lt;2.4.4*) — 修正無法快速上傳CSV而導致&#x200B;*無法傳送Cookie*&#x200B;錯誤的問題。
* 更新修補程式：MDVA-41061、MDVA-42584。
* 由於內部處理程式變更，新[!DNL Quality Patches Tool]修補程式的字首將從&#x200B;*MDVA*&#x200B;變更為&#x200B;*ACSD*。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正當購物車中已有最小專案數量時，無法將其他專案新增到購物車的問題。
* **MDVA-44887** (*用於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修正「管理」面板中的&#x200B;*Uncaught SyntaxError： Unexpected token &#39;const&#39;*&#x200B;錯誤。
* **MDVA-43718** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正&#x200B;*消費者無權存取%resources。從自訂整合存取共用目錄時出現*&#x200B;錯誤。
* **MDVA-44660** (*適用於Adobe Commerce和Magento Open Source>=2.4.2-p1 &lt;2.4.5*) — 修正重音符號字元``` ` ```無法用於客戶名字和姓氏的問題。
* **MDVA-40896** (*用於Adobe Commerce，且Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正非同步產品批次API中的&#x200B;*錯誤： TypeError：傳遞給Magento*&#x200B;的引數3錯誤。
* **MDVA-38559** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修正具有多個訂閱之客戶的&#x200B;*/V1/customers/search API*&#x200B;錯誤。
* **MDVA-44533** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.4*) — 修正錯誤將折扣套用至套件組合子產品的問題。
* 更新修補程式：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正產品&#x200B;*無法個別顯示*&#x200B;仍出現在目錄進階搜尋結果中的問題。
* **MDVA-44100** (*適用於Adobe Commerce且Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正所有FPT指派給購物車中最後一個產品並重設其他產品的問題。
* **MDVA-43605** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修正使用Rest API時，訂單資料傳回列總計負值的問題。
* **MDVA-43102** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修正透過REST API完成退款時，可銷售數量未正確更新的問題。
* **MDVA-43178** （*適用於 Adobe Systems Commerce 和 Magento Open Source >=2.4.3-p2 &lt;2.4.5*） - 修正無法在 GraphQL 中擷取自定義商店的客戶代號的問題。
* **MDVA-43859** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.1*&lt;2.4.5 ） - 修復了以下問題&#x200B;*：當已刪除的客戶嘗試登錄時，錯誤沒有記錄具有 customerId =* 的此類實體。
* **MDVA-44147** （*用於Adobe Systems商務和 Magento Open Source >=2.4.2 &lt;2.4.5*） - 修復了 GraphQL 請求不返回申請列表的問題。
* **MDVA-44505** （*適用於Adobe Systems商務和Magento Open Source >=2.4.1 &lt;2.4.3*） - 修復了 GraphQL 應用獎勵點不更新總量以及在訂單刊登期間多次應用積分商店的問題。
* 更新的修補程式：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*適用於Adobe Commerce，且Magento Open Source>=2.4.1 &lt;2.4.3*) — 修正當「客戶區段」設定為&#x200B;*全部*&#x200B;時，「相關產品規則」才能運作的問題。
* **MDVA-39605** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.5*) — 修正Redis快取TTL （到期日）有錯誤值的問題。
* **MDVA-43862** (*用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修正客戶由於GraphQL *UpdateCartItems突變*&#x200B;錯誤而無法更新購物車專案的問題。
* **MDVA-43824** （*適用於Adobe Systems商務和Magento Open Source >= &lt;=2.3.7-p3 ||=&quot;&quot;>2.3.6 =2.4.1 &lt;2.4.5*） - 修復了取消折扣訂單時出現錯誤的問題。&lt;/=2.3.7-p3>
* **MDVA-43451** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.3 &lt;2.4.5* ） - 修復了錯誤 *找不到請求商店的問題。 請驗證商店，然後再試一次。* 在為特定網站配置共享目錄時顯示。
* **MDVA-43491** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.3.5 &lt;2.4.5*） - 修正為多商店網站匯入產品時基本影像捲標不更新的問題。
* **MDVA-43601** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.3.0 &lt;2.4.5*） - 修正完全重新索引後遺失觸發器的問題。
* **MDVA-42046** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修正更新產品時，透過日期輸入欄位將錯誤值指派給產品屬性的問題。
* **MDVA-43935** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.1 &lt;2.4.5*） - 修正追加銷售產品顯示兩次的問題。
* **MDVA-44188** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.3 &lt;2.4.5* ） - 修正系統發出的 `.-` 包含地址的電子郵件未傳送的問題。
* **MDVA-42283** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.3.0 &lt;2.4.5*） - 修正法文地區管理順序網格線中的日期時間格式為 無效 的問題。
* 更新的修補程式：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 添加了 的 [!DNL Site-Wide Analysis Tool]修補程序中繼資料。

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*適用於Adobe Commerce且Magento Open Source>=2.3.0 &lt;2.3.6*) — 修正使用者可編輯作用中排程更新開始時間的問題。
* **MDVA-42410** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正優惠券報表僅顯示預設基本貨幣的問題。
* **MDVA-41136** (*適用於Adobe Commerce及Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正`mage-cache-sessid`到期日未延長，導致客戶資料清理的問題。
* **MDVA-39993** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修正透過API完成的詳細目錄變更未反映在前端產品頁面上的問題。
* **MDVA-42855** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正結帳期間新客戶地址未儲存至通訊錄的問題。
* **MDVA-42645** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正當商店信用功能停用時，管理員無法退款獎勵點數的問題。
* **MDVA-43414** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2*) — 修正數值SKU上執行`inventory.reservations.updateSalabilityStatus`佇列消費者時發生的PHP嚴重錯誤。
* **MDVA-41628** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修正新增模組時，現有受限制的管理員使用者取得新資源存取權的問題。
* **MDVA-43348** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正`gift_card_options`包含&#x200B;*uid*&#x200B;時，禮品卡GraphQL要求顯示錯誤的問題。
* **MDVA-39546** (*適用於Adobe Commerce，且Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正編輯期間，將測試更新開始日期設為目前日期之前日期的問題。
* **MDVA-42950** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正產品頁面上未播放視訊的問題。
* **MDVA-42689** (*適用於Adobe Commerce且Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正匯入期間更新產品類別時，Adobe Commerce擲回&#x200B;*完整性條件約束違規*&#x200B;錯誤的問題。
* **MDVA-41229** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修正可設定產品匯入後，前端上可用的影像無法顯示的問題。
* **MDVA-43731** (*用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正在&#x200B;*符合*&#x200B;的最少字詞中新增值時，*搜尋同義字*&#x200B;不再運作的問題。
* **MDVA-43232** (*用於Adobe Commerce且Magento Open Source>=2.3.4 &lt;2.4.5*) — 修正在[!DNL Visual Merchandiser]中依「特殊價格從下到上」排序產品時，導致儲存類別時發生錯誤的問題。
* **MDVA-43726** (*適用於Adobe Commerce且Magento Open Source>=2.3.3 &lt;2.4.3*) — 修正部分重新索引後無法套用以存放區層級屬性相符為基礎的目錄價格規則的問題。
* 更新修補程式：MDVA-36464、MDVA-37478、MDVA-38608。
* 已新增[!DNL Site-Wide Analysis Tool]的修補程式中繼資料。

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.5*) - Fixes the issue where product price attributes cannot be updated for a specific website via REST API.
* **MDVA-41350** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*) - Fixes the issue where an exception is thrown when an admin user with restricted access adds a product outside their role scope by SKU in an order.
* **MDVA-42269** (*for Adobe Commerce and Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Fixes the issue where an admin user cannot log in to the Admin due to the *TypeError: strtotime() expects parameter 1 to be string, null given* error.
* **MDVA-40830** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*) - Fixes the issue where the store credit is applied multiple times during order placement.
* **MDVA-42237** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.5*) - Fixes the issue where a configurable product special price is not updated after changes in its subproduct price.
* **MDVA-42520**（*用於Adobe Systems商務和Magento Open Source >=2.4.3&lt;2.4.4*） - 修復了如果使用“啟用交叉邊框貿易&#x200B;*”，稅率*&#x200B;將應用兩次的問題。
* 更新修補程式：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已棄用的修補程式：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*適用於Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.5*) — 修正大量屬性更新在變更&#x200B;*產品可見性*&#x200B;後才會為預設商店建立URL重寫的問題。
* **MDVA-43091** (*適用於Adobe Commerce且Magento Open Source>=2.4.3 &lt;2.4.4*) — 修正從後端的Admin訂購套件組合產品會造成錯誤&#x200B;*的問題。您無法對此產品使用小數數量*。
* **MDVA-40816** （*適用於Adobe Systems商務且 Magento Open Source >=2.3.0 &lt;2.4.5*） - 修正相關產品規則顯示未在規則條件中定義的類別之產品的問題。
* **MDVA-41305** (*用於Adobe Commerce且Magento Open Source>=2.4.2 &lt;2.4.5*) — 修正GraphQL突變在將其新增至願望清單後未傳回可設定產品選項的問題。
* **MDVA-39181** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修正相關產品規則顯示規則條件中未定義類別之產品的問題。
* **MDVA-42584** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正透過「匯入」或API變更數量及庫存狀態後，後端中可設定的庫存狀態未更新的問題。
* **MDVA-40175** (*適用於Adobe Commerce且Magento Open Source>=2.4.0 &lt;2.4.3*) — 修正&#x200B;*按一下以變更送貨方法*&#x200B;在重新排序期間未顯示選項按鈕以在Admin中選取送貨方法的問題。
* **MDVA-42768** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修正當&#x200B;*顯示無庫存*&#x200B;為「是」時，可設定產品的正常價格顯示為0的問題。
* **MDVA-43201** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正搭配特定地區設定使用DOB屬性時，客戶登入發生錯誤的問題。
* 更新修補程式：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.3.0 &lt;2.4.5*） - 修復了當Adobe Systems商務時區與本地環境時區不同時，日期篩選器無法正常工作的問題。
* **MDVA-42657** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.1 &lt;2.4.5*） - 修復了管理員用戶無法在客戶 區段條件中選擇類別的問題。
* **MDVA-42806** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正每次透過REST API更新現有公司時傳送&#x200B;*新公司註冊*&#x200B;電子郵件的問題。
* **MDVA-37984** (*適用於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修正[!DNL Visual Merchandiser] *依規則比對產品*&#x200B;功能無法正確篩選具有暫存更新的產品的問題。
* **MDVA-40488** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正可設定產品與無庫存子產品無法在其正確價格範圍中顯示的問題。
* **MDVA-42507** (*適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修正套用購物車規則的測試更新後，清除整頁快取的問題。
* **MDVA-39163** (*適用於Adobe Commerce，且Magento Open Source>=2.3.5 &lt;2.4.5*) — 修正新使用者註冊後無法使用送貨方法，且購物車中的產品來自訪客工作階段的問題。
* **MDVA-38626** (*適用於Adobe Commerce且Magento Open Source>=2.3.3 &lt;2.4.5*) — 修正管理員使用者無法使用[!DNL PayPal Payflow Pro]付款在後端下單的問題。
* **MDVA-38666** （*適用於Adobe Systems商務和 Magento Open Source >=2.3.2 &lt;2.3.6*） - 修復了管理員用戶無法更改客戶購物車中的可配置產品選項的問題。
* **MDVA-38526 （適用於 Adobe Systems Commerce 和 Magento Open Source >=2.4.1 &lt;2.4.4 *） - 修正了管理員用戶無法存取 的問題。***[!DNL Site-Wide Analysis tool]
* 更新的補丁：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** （*適用於 Adobe Systems Commerce 和 Magento Open Source >=2.3.0 &lt;2.4.4*） - 修復了使用者在設置 *法師消息* Cookie（如果它已經存在）但沒有新消息後收到 500 錯誤的問題。
* **MDVA-41139** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.3 &lt;2.4.4*） - 修復了以下問題：當其中一個來源的簡單產品 qty=0 時，可配置產品在產品導入後變得不Stock的問題。
* **MDVA-42326** （*適用於Adobe Systems商務和 Magento Open Source >= &lt;=2.3.7-p2 ||=&quot;&quot;>2.3.6 =2.4.1 &lt;2.4.4*） - 修復了客戶在會話逾時平均啟用持久購物車後結帳時收到錯誤的問題。&lt;/=2.3.7-p2>
* **MDVA-42341 （適用於 Adobe Systems Commerce 和 Magento Open Source >=2.4.2 &lt;2.4.4 *） - 修復了如果請求具有商店標頭，GraphQL 查詢 不會篩選結果的問題。***`categoryList`
* **MDVA-38393** （*適用於 Adobe Systems Commerce 和 Magento Open Source >=2.3.0 &lt;2.4.4*） - 修正以下問題：如果將簡單產品重新命名，目錄規則將停止對可設定產品起作用。
* **MDVA-39153** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.2 &lt;2.4.4*） - 修復了在管理中重新訂購期間錯誤計算折扣量的問題。
* 更新的修補程式： MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** （*適用於Adobe Systems商務和 Magento Open Source >=2.3.0 &lt;2.4.3*） - 修正管理員使用者在刪除網站后，無法訪問客戶網格的問題。
* **MDVA-40311** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.4.2-p2 &lt;2.4.4* ） - 修正管理員使用者收到錯誤訊息 *「安全性或窗體密鑰無效」的問題。 如果配置了自定義管理路徑並啟用了密鑰，請在登入管理員后刷新頁面* 。
* **MDVA-41631** （*用於Adobe Systems商務和 Magento Open Source >=2.4.1*&lt;2.4.4 ） - 修復了使用者在嘗試通過 GraphQL 檢索沒有可選&#x200B;*電話*&#x200B;值的訂單資訊時出現錯誤的問題。
* **MDVA-27239** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修正未顯示交叉銷售產品的問題。
* 更新的修補程式： MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.3.5 &lt;2.4.4*） - 修正重新編列索引期間前端遺失產品的問題。
* **MDVA-40120** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.4.1 &lt;2.4.4*） - 修復了 GraphQL 按 DESC/ASC 排序不適用於具有相同相關性或價格的產品的問題。
* **MDVA-41399** （*適用於Adobe Systems商務且Magento Open Source >=2.3.3 &lt;2.4.2* ） - 修正若客戶將產品新增至願望單，管理員 *使用者將無法訪問「管理購物車* 」頁面的問題。
* **MDVA-40609** (*用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正`cataloginventory_stock_status`索引表格中沒有停用產品資料，顯示不正確停用產品數量的問題。
* **MDVA-39031** (*適用於Adobe Commerce且Magento Open Source>=2.4.1 &lt;2.4.4*) — 修正即使未指派至目標網站，透過GraphQL將產品新增至購物車仍可行的問題。
* **MDVA-41597** (*用於Adobe Commerce且Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正使用者使用GraphQL新增一個以上可設定產品至購物車時出現錯誤的問題。
* **MDVA-27456** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.3.7*) — 修正使用者嘗試載入[!DNL Swagger]時發生錯誤的問題。
* **MDVA-32776** (*適用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2*) — 修正已下訂單但未送出時存貨狀態未更新的問題。
* **MDVA-30862** (*用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.0*) — 修正列印的PDF發票上訂購日期不正確的問題。
* 已改善[!DNL Quality Patch Tool]的索引頁面。 新增工具最新版本的[!DNL quality patches]便利搜尋和篩選功能。
* 更新修補程式：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*適用於Adobe Commerce且Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正之前已移除「結束日期」時，無法建立新的或編輯產品現有排程更新的問題。
* **MDVA-41046** (*適用於Adobe Commerce，且Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正簡單產品可指派給可設定/分組產品的問題。
* **MDVA-40545** (*適用於Adobe Commerce，且Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正即使同一頁面有多個節點，僅擷取頁面的第一個節點的問題。
* **MDVA-41164** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3-p1*) — 修正管理員使用者無法儲存或編輯具有檔案或影像型別自訂客戶屬性的公司的問題。
* **MDVA-39229** (*用於Adobe Commerce且Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正更新目錄規則中繼更新開始時間後，導致出現下列錯誤的問題： *Cron工作staging_synchronize_entities_period有錯誤：無法刪除作用中的更新。*
* **MDVA-40619** (*適用於Adobe Commerce且Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正嘗試在CMS頁面上執行內聯編輯時，CMS頁面階層變更會導致500錯誤的問題。
* **MDVA-41061** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正從管理員儲存產品時，庫存狀態重設為可銷售的問題。
* **MDVA-31763** （*適用於Adobe Systems商務和 Magento Open Source >=2.3.0 &lt;2.4.4*） - 修正目錄價格規則在手動重新索引之前會還原 （或不套用） 的問題。
* **MDVA-37748** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.4.2 &lt;2.4.3*） - 修正 GraphQL 查詢返回未指派給共用目錄的產品的問題。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.2 &lt;2.4.4*） - 修正無法透過 REST API 同時建立相同訂單的部分發票的問題。
* **MDVA-40101** (*適用於Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.0*) — 修正使用[!DNL PayPal Express]結帳成功下單後，無法從迷你購物車移除專案的問題。
* **MDVA-40401** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正即使下訂單失敗，優惠券使用量值仍會變更的問題。
* **MDVA-40537** (*用於Adobe Commerce且Magento Open Source>=2.3.4 &lt;=2.4.0-p1*) — 修正使用者建立商店檢視時，若存在數個具有相同URL索引鍵的CMS頁面時，會發生錯誤的問題。
* **MDVA-37725** (*適用於Adobe Commerce且Magento Open Source>=2.3.0 &lt;=2.4.3-p1*) — 修正從非預設網站傳送的非同步訂購電子郵件包含預設網站的標誌URL的問題。
* **MDVA-39482** (*適用於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正啟用延期交貨時，以「0」數量匯入的產品無存貨的問題。
* **MDVA-40435** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.4*) — 修正透過GraphQL套用時，具有動態價格的套件組合產品折扣不正確的問題。
* **MC-42528** (*用於Adobe Commerce且Magento Open Source>=2.4.3 &lt;=2.4.3-p1*) — 修正`categoryList` GraphQL查詢傳回指派和未指派類別的問題。
* **MDVA-29400** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修正[!DNL PayPal Express Checkout]下重複訂單的問題。
* **MDVA-26005** (*適用於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2*) — 修正無法在購物車價格規則條件的類別樹狀結構中選取類別的問題。
* **MDVA-25631** (*適用於Adobe Commerce和Magento Open Source>=2.3.3 &lt;=2.3.5-p2*) — 改善編輯和儲存包含大量客戶的客戶區段的效能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修正GraphQL搜尋查詢未顯示在Admin中常用搜尋詞的問題。
* **MDVA-40601** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.4.2-p2*) — 修正使用者嘗試透過GraphQL取得排程更新所變更類別的相關資訊時發生錯誤的問題。
* **MDVA-37234** (*適用於Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修正針對相同SKU將專案多次新增至購物車（平行請求）時，會為相同購物車ID建立重複條列專案的問題。
* **MDVA-33606** (*用於Adobe Commerce且Magento Open Source>=2.4.1 &lt;=2.4.2-p2*) — 修正使用者在儲存指派給階層的CMS頁面時收到&#x200B;*唯一條件約束違規*&#x200B;錯誤的問題。
* **MDVA-31590** (*用於Adobe Commerce且Magento Open Source>=2.4.0 &lt;=2.4.1-p1*) — 修正使用者無法使用MySQL非同步佇列大量更新屬性的問題。
* **MDVA-36309** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修正管理格線中依屬性搜尋產品速度緩慢的問題。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** （*適用於Adobe Systems商務和 Magento Open Source >=2.3.0 &lt;2.4.4*） - 修復了從商店信用額度支付訂單時，帶有 FPT 的發票顯示錯誤的總量的問題。
* **MDVA-37364** （*適用於Adobe Systems商務和 Magento Open Source >=2.4.0 &lt;=2.4.3*） - 修復日期類型的自定義 客戶 屬性中斷客戶網格UI的問題。
* **MDVA-39195 （適用於 Adobe Systems Commerce 且 Magento Open Source >=2.4.2 &lt;=2.4.2-p2 *） - 修正啟用「新增到購物車*」按鈕在類別 頁面上重新導向購物車時處於非作用中狀態的問題。****
* **MDVA-37115** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修正可設定產品頁面上顯示不必要的&#x200B;*僅剩下0*&#x200B;注意事項的問題。
* **MDVA-39521** (*適用於Adobe Commerce且Magento Open Source>=2.4.0 &lt;2.4.4*) — 修正使用者無法透過GraphQL以空白電話號碼設定購物車送貨地址的問題。
* **MDVA-39384** (*適用於Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修正未儲存公司使用者的自訂客戶屬性的問題。
* **MDVA-39043** (*適用於Adobe Commerce且Magento Open Source>=2.3.4 &lt;=2.4.3*) — 修正具有有限存取權的管理員使用者嘗試將&#x200B;*產品*&#x200B;小工具新增至CMS頁面時發生錯誤的問題。
* **MDVA-39966** （*適用於 Adobe Systems Commerce 和 Magento Open Source >= &lt;=2.3.5-p2 ||=&quot;&quot;>2.3.0 =2.4.0 &lt;=2.4.0-p1*） - 修正部署錯誤地區的問題。&lt;/=2.3.5-p2>
* **MDVA-38852** （*適用於Adobe Systems商務和 Magento Open Source >=2.3.0 &lt;=2.3.5-p2*） - 修復了目錄清單按設計鎖定表以查找更新的問題，這在具有多個並行訂單的情況下會顯著降低性能。
* **MDVA-39986** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.4.1 &lt;2.4.3*） - 修正用戶無法使用 Safari 瀏覽器在 MacOS 的「管理」中下訂單的問題。
* **MDVA-38447** （*用於Adobe Systems商務和 Magento Open Source >=2.4.2*&lt;2.4.4 ） - 修復了兩個問題：*在 GraphQL 回應中返回不可見的可單獨*&#x200B;配置的子產品，並使用類別篩檢程式優化 GraphQL 查詢產品的 MySQL 查詢。
* **MDVA-40134** (*適用於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修正啟用共用目錄時，GraphQL未傳回相關產品的問題。
* **MDVA-39935** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.4.1 &lt;2.4.4*） - 修復 GraphQL 傳回在網站級別禁用的可配置子產品的問題。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*用於Adobe Commerce且Magento Open Source>=2.4.0 &lt;2.4.4*) — 修正Admin中訂單詳細資料頁面上顯示&#x200B;*呼叫成員函式getId()*&#x200B;錯誤的問題。
* **MDVA-34948 （用於 Adobe Systems Commerce 和 Magento Open Source >=&lt;=2.3.6-p1 ||=&quot;&quot;>2.3.6 =2.4.0 &lt;=2.4.0-p1 *） - 修復了長時間運行的查詢的問題，按讚 `GET_LOCK`.&lt;/=2.3.6-p1>***
* **MDVA-39305** （*適用於 Adobe Systems Commerce 且 Magento Open Source >=2.4.0 &lt;=2.4.2-p1*） - 修正註冊客戶無法使用已啟用的 Google ReCaptcha 登入的問題。
* **MDVA-37897** (*適用於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修正客戶嘗試使用「最近檢視」Widget的選項新增產品時，重新導向不正確的問題。

## v1.1.0 {#v1-1-0}

* 我們引進了修補程式類別，以改善使用者體驗，並讓客戶更輕鬆地搜尋所需的修補程式。
* `patches.json`檔案已重新命名為`support-patches.json`。
* **MDVA-38799** (*for Adobe Commerce >=2.3.0 &lt;2.4.3*) - Fixes the issue where downloadable products weren&#39;t saved after creating a staging update.
* **MDVA-37592** （*適用於Adobe Systems商務>=2.3.6 &lt;=2.4.2-p1*） - 修復了按價格排序無法正常工作的問題，對於分配給共用目錄的零價格的產品。
* **MDVA-38827** （*適用於Adobe Systems商務 >=2.3.3-p1 &lt;2.4.4*） - 修復了客戶收到包含錯誤消息的訂單發貨電子郵件的問題。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*用於Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修正儲存CMS頁面時的錯誤： *已有相同識別碼PAGE_ID的專案*。
* **MDVA-34680** (*適用於Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修正客戶格線中未正確篩選客戶帳戶建立時間的問題。
* **MDVA-37068** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.4*) — 修正當購物車只有虛擬產品時顯示錯誤稅率的問題。
* **MDVA-38608** （*適用於 Adobe Systems Commerce >=2.3.0 &lt;2.4.3*） - 修復了在重新索引未成功完成時不會刪除臨時表的問題。
* **MDVA-38308 （適用於Adobe Systems商務>=2.3.5 &lt;=2.3.6-p1 ||=&quot;&quot;>=2.4.0 &lt;=2.4.1-p1 ||=&quot;&quot;>=2.4.2 &lt;2.4.4 *） - 修正與新增[!DNL Vimeo]視訊至產品相關的問題。&lt;/=2.4.1-p1>&lt;/=2.3.6-p1>***

## v1.0.25 {#v1-0-25}

* **MDVA-37916** （*適用於Adobe Systems商務 >=2.3.6 &lt;2.4.3* ） - 修正使用 [!DNL Paypal Payment Advanced] 該方法時，客戶不會被帶到付款確認頁面的問題。
* **MDVA-37082** （*適用於Adobe Systems商務 >=2.3.0 &lt;2.4.3*） - 修復了保存分組產品的自定義庫存導致產品在前端顯示缺貨的問題。
* **MDVA-36572** (*for Adobe Commerce >=2.3.5 &lt;2.4.3*) - Fixes the issue when Credit Memo updates no longer cause duplicate product reservation updates in the database.
* **MDVA-38132** (*for Adobe Commerce >=2.3.3 &lt;2.4.3*) - Fixes the issue when the Admin panel is unreachable due to a *too many redirects* error.
* **MDVA-38270** (*for Adobe Commerce >=2.4.1 &lt;2.4.3*) - Fixes the issue with missing Gift card information in the order total in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*for Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Fixes the issue with adding a configurable product to the cart via GraphQL when the website ID does not coincide with the store ID.
* **MDVA-36832** （*適用於 Adobe Systems Commerce >=2.3.4 &lt;=2.4.2-p1*） - 修正寬度為 768px 時，頁面上重複影像視圖的問題。
* **MDVA-37874** (*適用於Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 修正&#x200B;*整個購物車*&#x200B;的固定折扣金額不正確套用至包含多個選項的套件組合產品的問題。
* **MDVA-37913** (*適用於Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) — 修正透過API更新可下載產品時，可下載連結消失的問題。
* **MDVA-34330** (*適用於Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) — 修正「訂單」格線中的訂單未根據管理員時區進行篩選的問題。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.7*) — 修正透過REST API以&#x200B;*帳戶付款*&#x200B;付款方式開立訂單的部分發票時，Adobe Commerce擲回錯誤的問題。
* **MDVA-37362** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修正GraphQL回應中可設定的產品選項值和變數屬性值為空白的問題。
* **MDVA-37288** (*適用於Adobe Commerce 2.4.2*) — 修正GraphQL要求後傳回錯誤層級價格的問題。
* **MDVA-37225** (*適用於Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) — 修正當匯入SKU中有整數值時快速建立訂單期間上傳程式卡住的問題。
* **MDVA-37224** (*適用於Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) — 修正客戶無法針對購物車中其他產品的[!DNL PayFlow Pro]可轉讓報價付款的問題。
* **MDVA-36286** (*適用於Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修正若同一SKU在子類別中有不同位置，頁面產生器產品Widget預覽會中斷的問題。
* **MDVA-30186** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.5-p2， >=2.4.0 &lt;=2.4.0-p1， >=2.4.2 &lt;=2.4.2-p1*) — 修正GraphQL回應中，屬性選項是依選項值而非屬性專案計數排序的問題。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** （*適用於 Adobe Systems Commerce >=2.3.0 &lt;=2.4.2*） - 修正透過 API 變更後保留舊自定義選項的問題。
* **MDVA-35773** （*適用於Adobe Systems商務>=2.3.6 &lt;=2.3.6-p1 ||=&quot;&quot;>=2.4.1 &lt;=2.4.2*） - 修復了 100% 折扣訂單的發票上總計未顯示為零的問題。&lt;/=2.3.6-p1>
* **MDVA-36833** （*適用於 Adobe Systems Commerce 2.4.2*） - 修正從共享目錄中排除某些產品后，搜尋結果顯示每個頁面隨機產品數的問題。
* **MDVA-37182** （*適用於 Adobe Systems Commerce >=2.4.1 &lt;=2.4.2* ） - 修正在版本 6 和版本 7 中取得 [!DNL Elasticsearch] 錯誤搜尋結果的問題。
* **MDVA-36253** (*適用於Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) — 修正專案刪除後，迷你購物車中顯示錯誤小計的問題。
* **MDVA-36853** (*適用於Adobe Commerce 2.4.2*) — 修正載入大型媒體集時未顯示影像的問題。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修正類別頁面上遺失套件產品的問題。
* **MDVA-36615** (*適用於Adobe Commerce 2.4.2*) — 修正Admin產品格線中產品計數不正確的問題。
* **MDVA-36464** (*適用於Adobe Commerce >=2.4.0 &lt;=2.4.2*) — 修正電子郵件通知設定在存放區檢視層級無法運作的問題。
* **MDVA-36138** （*適用於Adobe Systems商務^2.3.2*） - 修復了以下問題：如果購物車中的所有商品都不符合免費運費購物車 規則，則未調整運費並向買家顯示完整運費的問題。
* **MDVA-36424** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — 修正當後端基底URL與店面基底URL不同時，附加至頁面產生器元素的媒體影像在內容重複編輯時消失的問題。
* **MDVA-35984** (*用於Adobe Commerce ^2.4.0*) — 修正建立相同產品的多次並行出貨後，產品數量和可銷售數量不正確的問題。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 這修正了使用類別快取標籤時GraphQL查詢未快取的問題。
* **MDVA-33168** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正透過API更新產品屬性時，所有其他屬性會變更為空值的問題。
* **MDVA-19640** （*適用於 Adobe Systems Commerce >=2.3.0*） - 修正未顯示任何數據的問題 [!DNL Advanced Reporting] 。
* **MDVA-11189** （*適用於Adobe Systems商務 >=2.3.0 &lt;2.3.5* ） - 修復導入CSV檔以更新產品庫存后，刪除表中行 `cataloginventory_stock` 的問題。
* **MDVA-26639** （*適用於Adobe Systems商務 >=2.3.3-p1 &lt;2.3.6*） - 修復了以下問題：如果創建新的訂單確認電子郵件範本，訂單郵件中缺少訂單專案。
* **MDVA-15546** （*適用於Adobe Systems商務>=2.3.0*） - 修復了以下問題：創建訂單后， *異常日誌中顯示列entity_id子句不明確* 錯誤的問題。
* **MDVA-21095** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正大量屬性值更新後查詢`INSERT INTO search_tmp`無法結束的問題。
* **MDVA-23845** (*適用於Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修正啟用JavaScript縮制後無法預覽電子郵件範本的問題。
* **MDVA-22026** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正從CSV檔案匯入產品（包括來自外部URL的影像）失敗的問題。
* **MDVA-22383** (*用於Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正儲存產品需要很長時間且分頁的問題。
* **MC-41359** (*適用於Adobe Commerce >=2.3.6-p1 &lt;2.3.7， >=2.4.2 &lt;2.4.3*) — 修正SameSite Cookie引數設定不正確的問題。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*適用於Adobe Commerce 2.4.1*) — 修正頁面產生器擲回下列錯誤的問題： *起始頁面產生器時發生錯誤。 請洽詢您的技術支援連絡人。*
* **MDVA-35356** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正取消部份開立商業發票後的商店信用退款不正確的問題。
* **MDVA-33289** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修正結帳期間帳單地址UI中顯示原始JavaScript程式碼（如果已啟用[!DNL Google Tag Manager]）的問題。
* **MDVA-35982** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正僅限特定網站的管理員使用者無法為相同網站上的訂單建立出貨的問題。
* **MDVA-35155** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正選項標題變更時無法購買套件組合產品的問題。
* **MDVA-35910** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正停用「登入為客戶」功能後無法建立新客戶帳戶的問題。
* **MDVA-34474** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正使用API將產品新增至請購單清單的問題。
* **MDVA-34591** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正&#x200B;*套用到*&#x200B;的最大數量折扣與&#x200B;*折扣數量步驟（購買X）*&#x200B;的購物車規則折扣計算不正確的問題。
* **MDVA-33704** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修正&#x200B;*在商店取貨*&#x200B;配送選項未顯示的問題，儘管已設定為可用。
* **MDVA-34928** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修正將商店評分從付款中移除後，頁面載入器會無限期顯示的問題。
* **MDVA-35254** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正簽出期間驗證碼的問題。
* **MDVA-35569** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正指定狀態時，GraphQL回應中未填入&#x200B;*已修正產品稅捐*&#x200B;欄位的問題。
* **MDVA-35847** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正使用自訂客戶屬性時公司使用者表單中斷的B2B問題。
* **MDVA-31307** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正某些類別上因快取區塊的動態CSP白名單發生問題而出現&#x200B;*記憶體不足*&#x200B;錯誤的問題。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 刪除數個產品後，將消費者`quoteItemCleaner`的不正確&#x200B;*進行中*&#x200B;訊息狀態修正為正確的&#x200B;*完成*&#x200B;訊息。
* **MDVA-34102** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正「產品網格」和「管理」區域之「編輯產品」頁面上已停用產品的預設庫存量為零。
* **MDVA-35286** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正客戶在購物車中捆綁產品，並從多個地址簽出切換為單一頁面簽出時發生錯誤的問題。
* **MDVA-35312** (*適用於Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) — 修正空白GraphQL請求時的回應代碼500。
* **MDVA-34189** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修正載入「管理類別」頁面時，[!DNL Visual Merchandiser]個查詢的503個第一位元組逾時問題。
* **MDVA-34695** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1*) — 刪除類別後修正負值`children_count`。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正套用排程變更後，*使用預設值*&#x200B;核取方塊被清除的問題。 一旦計劃的更改不再有效，問題就會出現。
* **MDVA-35064** （*適用於Adobe Systems商務 >=2.3.3 &lt;2.4.3*） - 修正針對透過 API 建立的可設定產品，不會產生URL重寫的問題。
* **MDVA-34943** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正快速訂購快取先前輸入SKU的問題。
* **MDVA-35197** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.0*) — 修正先前新增的產品無存貨時，使用GraphQL新增購物車時出現錯誤的問題。
* **MDVA-34850** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.0*) — 修正可設定產品無庫存選項未顯示而非顯示為刪除的問題。
* **MDVA-34867** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正排程更新的條件欄位集值未儲存的問題。
* **MDVA-35092** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修正使用者因已棄用[!DNL Vimeo] API而無法新增[!DNL Vimeo]視訊的問題。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*適用於Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修正如果相符產品對每個網站的價格不同，頁面產生器產品內容型別預覽會中斷的問題。
* **MDVA-32634** (*用於Adobe Commerce ^2.3.1*) — 修正指派給所有存放區的類別`url_path`在階層中移動類別後未變更的問題。
* **MDVA-33344** (*用於Adobe Commerce ^2.3.0*) — 修正使用硬式編碼`rma_item`實體預設屬性集ID而非資料庫值的問題。
* **MDVA-34192** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修正無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。
* **MDVA-34847** (*適用於Adobe Commerce ^2.3.0*) — 修正具有自訂許可權之管理員使用者在管理集合中，SQL條件的SQL存放區ID型別轉換為整數。
* **MDVA-34886** (*用於Adobe Commerce ^2.3.2*) — 修正當&#x200B;*權重*&#x200B;產品屬性設定為可搜尋時，搜尋無法傳回結果的問題。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正[!DNL PayPal Payflow Pro]付款失敗且發生重新導向引數清單格式錯誤的問題。
* **MDVA-34023** （*適用於 Adobe Systems Commerce >=2.3.0 &lt;2.4.3*） - 修復了以下 *錯誤：訪問者的瀏覽器上沒有隨機顯示具有 addressId* 的實體。
* **MDVA-32759** （*適用於Adobe Systems商務>=2.3.1 &lt;2.4.3 with B2B extension*） - 修復了共用目錄刪除現有層定價的問題。
* **MDVA-33482** (*用於Adobe Commerce ^2.3.5*) — 修正針對部份商業發票產生「銷退折讓單」，導致對訂單總額計稅，而非該部份商業發票計稅的問題。
* **MDVA-33393** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正錯誤&#x200B;*所提供的國家/地區ID不存在*。
* **MDVA-33632** （*適用於Adobe Systems商務 >=2.3.0 &lt;2.3.7* ） - 修復了在嘗試重新訂購缺貨產品時，異常消息 *此產品缺貨* 現在會顯示給管理員使用者。
* **MDVA-34469** （*用于Adobe Systems商務 >=2.4.1 &lt;2.4.2*） - 修復了使用多個商店視圖時，客戶購物車上的 GraphQL 突變失敗的問題。
* **MDVA-33976** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修正從套件產品移除第二個選項後，套件組合產品在店面無存貨顯示的問題。
* **MDVA-33894** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1 （含B2B擴充功能*）) — 修正快速訂購功能的多個問題，包括新增和移除多個產品以及SKU區分大小寫。
* **MDVA-27664** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正客戶登錄檔單中造成錯誤顯示的問題： *錯誤 — 出生日期不應晚於今天。*
* **MDVA-33970** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正當價格屬性的範圍設定為網站時，銷退折讓單中有錯誤貨幣符號的問題。
* **MDVA-33992** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正結帳時B2B特殊價格顯示不正確的問題。
* **MDVA-34100** （*適用於Adobe Systems商務 >=2.3.4 &lt;2.4.2 with B2B extension*） - 修正無法從公司結構頁面建立公司 帳戶的問題。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5， >=2.4.0 &lt;2.4.2*) — 修正從CSV檔案匯入產品後重複影像的問題。
* **MDVA-33382** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正從類別移除產品後，索引子失效的問題。
* **MDVA-28511** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修正「名稱」欄位包含特定字元（如重音大寫字母）時，無法完成[!DNL PayPal]結帳的問題。
* **MDVA-31519** （*適用於Adobe Systems商務>=2.3.5 &lt;2.3.6*） - 修復了使用網站範圍的銷售規則時訪客結帳等待超時的問題。
* **MDVA-33281** （*適用於Adobe Systems商務 >=2.3.4 &lt;2.3.6* ） - 修復了由於 `inventory:reservation:list-inconsistencies` 錯誤的SKU參數類型而導致致命錯誤的問題。
* **MDVA-24201** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正價格在手動重新編列索引前無法反映排程購物車價格規則的問題。
* **MDVA-32694** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修正管理員使用者無法將產品新增至可轉讓報價單（如果產品與非預設商店有關）的問題。
* **MDVA-33516** （*適用於Adobe Systems商務 >=2.3.0 &lt;2.3.6*） - 修復了在申請清單中編輯捆綁產品會導致錯誤的問題。
* **MDVA-33975** （*用於Adobe Systems商務 >=2.3.4 &lt;2.4.2*） - 修復了與 GraphQL 請求中的價格計算相關的多個問題。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正在&#x200B;**報告** > **銷售** > **[!DNL PayPal]**&#x200B;結算下無法取得[!DNL PayPal]結算報告的問題。
* **MCP-87** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.2*) — 改善大型設定檔的類別產品和庫存索引器的索引時間。
* **MDVA-33106** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正執行cron `run`命令後清除重新排程產品變更的問題。
* **MDVA-19391** (*for Adobe Commerce >=2.3.0 &lt;2.3.5*) - Fixes the issue where `analytics_collect_data` is throwing an error due to NULL description records in the `catalog_category_entity_text` table.
* **MDVA-20376** （*適用於Adobe Systems商務 >=2.3.2&lt;2.3.4* ） - 修復了&#x200B;*“`exception.log`訂購後登錄客戶沒有此類實體的 customerId = 1*”錯誤的問題刊登。
* **MDVA-23764 （用於Adobe Systems商務 >=2.3.2 &lt;2.3.5 *） - 修復了影響動態塊顯示的錯誤。***`JsFooterPlugin.php`
* **MDVA-13203 （適用於Adobe Systems商務 >=2.3.0 &lt;2.4.2 *） - 修復完全重新索引后出現完整性限制衝突 搜尋_tmp_ 表*錯誤的問題。****
* **MDVA-23426** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5*) — 修正Adobe Commerce傳送的通知電子郵件包含空白內文，且內容已新增為附件的問題。
* **MDVA-22150** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.4*) — 修正購物車中擁有可設定產品且已套用優惠券的客戶無法在Admin中登入該可設定產品的問題。
* **MDVA-32545** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正從管理員建立訂單時，未自動傳送發票的問題。
* **MDVA-32714** （*適用於 Adobe Systems Commerce >=2.3.4 &lt;2.4.1*） - 修正 GraphQL 產品查詢客戶 群組價格不起作用的問題。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** （*用於Adobe Systems商務>=2.3.2 &lt;2.4.2* ） - 添加 *小計（包括 稅）* 選擇定價規則條件。
* **MDVA-31236** （*適用於 Adobe Systems Commerce >=2.4.0 &lt;2.4.2*） - 修復了具有自定義資源訪問許可權的管理員無法設置 2FA 或登錄的問題。
* **MDVA-30845** （*適用於Adobe Systems商務>=2.3.5 &lt;2.3.7*） - 修復了以下問題： *抱歉，目前* 此訂單沒有報價可用，當無法連接到 UPS XML/USPS/DHL 時顯示錯誤，並且沒有其他可用的運輸方式。
* **MDVA-32133** (*for Adobe Commerce >=2.4.0 &lt;2.4.1*) - Fixes the issue where media gallery is not loading from Page Builder in certain cases.
* **MDVA-12304** (*for Adobe Commerce >=2.3.0*) - Increases the maximum number of cookies from 50 to 200.
* **MDVA-32632** (*for Adobe Commerce >=2.3.2 &lt;2.3.5*) - Fixes the issue where orders appear in the payment system, but not in Adobe Commerce.
* **MDVA-32449** （*適用於Adobe Systems商務>=2.3.0 &lt;2.3.6 ||=&quot;&quot; 2.4.0=&quot;&quot; ||=&quot;&quot;>=2.4.1 &lt;2.4.2 with B2B extension*） - 修復了訂單歷史記錄載入非常緩慢或根本不載入的問題。&lt;/2.3.6>
* **MDVA-32739** （*適用於Adobe Systems商務 >=2.3.0 &lt;2.4.2*） - 修正啟用異步電子郵件通知會傳送舊銷售電子郵件的問題。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*適用於Adobe Commerce 2.3.6、2.4.1*) — 修正&#x200B;*建立帳戶*&#x200B;按鈕在修正&#x200B;*建立新客戶帳戶*&#x200B;表單中的無效資料後仍保持停用狀態的問題。
* **MDVA-31006** (*適用於Adobe Commerce 2.3.0、2.3.1*) — 修正使用[!DNL Paypal Express]付款下訂單後出現重複訂單的問題。
* **MDVA-25602** (*適用於Adobe Commerce 2.3.0*) — 修正[!DNL PayPal Payflow Pro]付款方法的問題，並在Chrome 80瀏覽器中將Cookie依預設視為`SameSite=Lax`，且API回應重新導向至客戶登入頁面。

## v1.0.10 {#v1-0-10}

修補程式版本的微幅修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*適用於Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修正使用&#x200B;*整個購物車*&#x200B;動作的固定金額折扣時，未透過GraphQL套用含優惠券的購物車價格規則的問題。
* **MDVA-30889** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正以虛擬及簡單產品作為選項開立套件組合發票後發生錯誤的問題。
* **MDVA-31791** (*用於Adobe Commerce >=2.3.4 &lt;2.3.5*) — 在使用目標規則或連結的產品時，改善產品頁面的效能。
* **MDVA-31168** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正產品匯出CSV檔案未出現，以及記憶體配置錯誤的問題。
* **MDVA-32313** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正可設定產品可能以錯誤的設定選項新增至願望清單的問題。
* **MDVA-31759** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正產品在CSV匯入期間未使用&#x200B;*下拉式清單*&#x200B;和&#x200B;*textarea*&#x200B;屬性值更新的問題。
* **MDVA-32012** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正無法驗證韓國和阿根廷郵遞區號的問題。
* **MDVA-31640** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 修正無法透過REST API更新特殊價格的問題。
* **MDVA-28651** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 （含B2B擴充功能*） — 修正透過REST API載入可轉讓引號時出現效能問題的問題。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1 （含B2B副檔名*）) — 修正「銷退折讓單」格線中顯示錯誤貨幣符號的問題。
* **MDVA-31295** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正部分訂單完成且專案徵稅時未計算獎勵點數的問題。
* **MDVA-30112** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正若訂購數量超過&#x200B;*bunch-size*&#x200B;值，Adobe Commerce會將狀態為&#x200B;*擱置*&#x200B;的訂購視為不一致的問題。
* **MDVA-31150** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正GETInvoice Rest API呼叫未傳回商店信用卡與禮品卡餘額的問題，當商業發票以Rest API呼叫過帳且訂單部份由商店信用卡與禮品卡帳戶支付時。
* **MDVA-30963** (*適用於Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修正產品篩選結果集僅包含為Admin中的&#x200B;*所有商店檢視*&#x200B;範圍指定的值，且包含已在商店檢視層級上覆寫值的產品的問題。
* **MDVA-29954** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2含B2B副檔名*) — 修正&#x200B;*新公司註冊要求*&#x200B;與&#x200B;*您已連結至公司*&#x200B;電子郵件傳送錯誤地址的問題。
* **MDVA-28357** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 在[!DNL ElasticSearch]索引的SKU欄位中，以具有關鍵字tokenizer的自訂分析器取代標準分析器，讓萬用字元搜尋查詢可搭配包含連字型大小(「 — 」)的SKU運作。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正使用WebApi建立部分出貨後，自訂訂單狀態變更為&#x200B;*處理*&#x200B;的問題。
* **MDVA-30428** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修正當此產品已指派給自訂詳細目錄來源時，客戶無法新增產品至願望清單的問題。
* **MDVA-30594** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正設定FPT時，無法在結帳期間儲存含有多個位址之訂單的問題。
* **MDVA-29148** （*適用於Adobe Systems商務 >=2.3.0 &lt;2.4.2* ） - 修復了通過 API 調用創建產品時，如果有效負載中未提供任何值，則 （按讚 多選） 類型的 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 產品自定義屬性不使用其預設值的問題。
* **MDVA-30837 （適用於Adobe Systems商務 >=2.3.1 &lt;2.3.5 *） - 在「免費送貨」方式配置中新增「將稅包含在金額： 是/否*」的配置設定。****&#x200B;當“將稅款到金額&#x200B;*”設置為*“是&#x200B;*”時*，最小訂單金額將計算為“小計 + 稅金”。當“將稅款計入金額&#x200B;*”設置為*“否&#x200B;*”時*，最小訂單金額將計算為小計
* **MDVA-25028（適用於Adobe Systems商務>=2.3.2 &lt;2.3.3 ||=&quot;&quot;>=2.3.5 &lt;2.3.6 *） - 修復了以下問題：在觸發欺詐篩選器時，使用[!DNL PayPal Payflow Pro]下達的訂單未設置為“可疑欺詐”狀態。&lt;/2.3.3>***
* **MDVA-31224** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5*) — 改善套件組合產品之`catalog_product_price`重新索引作業的效能。
* **MDVA-31321** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正選取&#x200B;*全部顯示*&#x200B;時的空白頁面（錯誤）。 [!DNL Elasticsearch]會傳回大量的產品ID清單。 在此案例中，order by子句會轉換為不正確的SQL格式。
* **MDVA-30815** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正當您變更搜尋結果頁面上應顯示的搜尋結果數目時，Adobe Commerce會顯示空白頁面的問題。 當您變更每頁檢視的搜尋結果數目時，[!DNL Elasticsearch]現在可以正確顯示類別頁面的結果。
* **MDVA-30782** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修正不論購物車規則為何，都會顯示動態區塊的問題。
* **MDVA-31021** （*適用於 Adobe Systems Commerce >=2.3.0 &lt;2.4.2* ） - 修正 中 `module-catalog-import-export/Model/Import/Product/Option.php`存在效能問題的問題。 如果表中的記錄 `catalog_product_option` 超過 ~100k，則具有單個產品的新CSV需要不到 10 秒的時間來驗證。
* **MDVA-31007** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正自訂地址屬性未正確顯示在我的帳戶區域和後端的訂單詳細資訊頁面中的問題。
* **MDVA-29389** (*用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正進階報告的問題，其中`analytics_collect_data` cronjob指出： *連線埠必須在主機引數中設定（如localhost：3306）*。
* **MDVA-31343** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6*) — 已排程類別時，修正已移除內文類別`page-layout-category-full-width`的問題。
* **MDVA-30945** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正您在更新購物車`Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`時收到嚴重錯誤訊息的問題。

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.0*) — 實作&#x200B;*最小值應符合*&#x200B;功能和[!DNL Elasticsearch]引擎的部分搜尋。 解決搜尋查詢中連字型大小的問題。
* **MDVA-30102** (*適用於Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修正Redis快取因配置快取沒有TTL而快速成長的問題。
* **MDVA-30599** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.0*) — 修正使用API建立的訪客報價錯誤地標籤為已登入客戶的報價的問題。
* **MDVA-29446** (*適用於Adobe Commerce >=2.3.3 &lt;=2.4.0*) — 修正結帳期間不適用送貨方法價格顯示為零的問題。
* **MDVA-30357** (*適用於Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修正當cron產生Sitemap時建立錯誤影像URL的問題。
* **MDVA-30565** (*適用於Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) — 修正下列問題：如果已啟用永久性購物車，店面結帳時不會針對訪客客戶顯示&#x200B;*具有cartid = 0*&#x200B;的這類實體錯誤。
* **MDVA-29787** (*適用於Adobe Commerce >=2.3.0 &lt;=2.4.0*) — 修正當&#x200B;*是*&#x200B;條件之一，用來定義要顯示的產品時，相關產品的目標規則無法運作的問題。
* **MDVA-30977** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) — 修正重新索引後類別中遺失隨機產品的問題。
* **MDVA-28202** (*適用於Adobe Commerce >=2.3.4 &lt;=2.4.2*) — 修正使用MSI時，階層導覽無法正確篩選可設定產品的問題。
* **MDVA-28300** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正GQL要求未反映目錄價格規則之價格變更的問題。
* **MDVA-31006** (*適用於Adobe Commerce >=2.3.2 &lt;=2.4.2*) — 修正使用[!DNL Paypal Express]付款下訂單後出現重複訂單的問題。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正分層導覽的問題，其中若將[!DNL Elasticsearch]當做搜尋引擎使用，則布林值型別產品屬性的&#x200B;*No*&#x200B;值不會包含在分層導覽中。
* **MDVA-28191** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正透過管理員建立訂單期間未載入付款方式的問題。
* **MDVA-29959** (*適用於Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 （具有B2B擴充功能）*) — 修正具有&#x200B;*公司*&#x200B;許可權的受限制系統管理員使用者無法刪除公司帳戶的問題。
* **MDVA-30265** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正建立發票後出貨追蹤連結停止運作的問題。
* **MDVA-28409** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正資料庫中過期引號數目非常多時，`sales_clean_quotes` cron作業失敗並出現&#x200B;*記憶體不足*&#x200B;錯誤的問題。
* **MDVA-30593** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修正未清除根據「報價期限」設定過期的報價的問題。
* **MDVA-30107** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正將不同基底URL用於存放區檢視時，存放區切換器無法如預期運作的問題。
* **MDVA-28763** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正使用REST API多次更新產品資訊後產品影像重複的問題。
* **MDVA-30284** (*用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正目錄搜尋索引器因下列&#x200B;*[!DNL Elasticsearch]錯誤而失敗的問題：已超過索引中欄位總數的限制。*
* **MDVA-29042** (*適用於Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 （含B2B擴充功能）*) — 修正將新產品新增至共用目錄後，目錄許可權自動變更為&#x200B;*允許*&#x200B;的問題。
* **MDVA-30428** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正當此產品指派給自訂詳細目錄來源時，客戶無法新增產品至願望清單的問題。
* **MDVA-28661** （*適用於 Adobe Systems Commerce >=2.3.0 &lt;2.4.2 with B2B extension*） - 修正在變更管理員后，「公司使用者公司 帳戶公司區段發生錯誤的問題。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** （*適用於Adobe Systems商務 2.3.1 - 2.3.4-p2*） - 修復了在資料庫名稱過長時 cron 作業失敗的問題，導致前端的類別無法更新。
* **MDVA-30106** （*適用於 Adobe Systems Commerce ^2.3.0*） - 修復了結帳時付款未載入 無法 *讀取 JS 控制台中空屬性“長度”* 錯誤的問題。
* **MDVA-28656** （*適用於Adobe Systems商務>=2.3.1 &lt;2.3.6 ||=&quot;&quot;>=2.4.0 &lt;2.4.2*） - 修復了以下問題：如果下訂單時不需要付款資訊（例如，有 100% 折扣），並且為該訂單創建了發票，則訂單狀態將更改為 *“已關閉* ”而不是完整應用程式。&lt;/2.3.6>
* **MDVA-30209** (*適用於Adobe Commerce 2.3.0 - 2.3.3-p1*) — 修正客戶更新其帳戶資訊時，客戶群組變更為預設的問題。
* **MDVA-30123** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正GraphQL查詢的屬性選項標籤未正確轉譯的問題。
* **MDVA-29996** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正啟用類別許可權後，類別頁面無法由完整頁面快取快取的問題。
* **MDVA-30164** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修正存在自訂客戶屬性時無法從客戶格線匯出客戶記錄的問題。
* **MDVA-30444** （*適用於 Adobe Systems Commerce >=2.3.0 &lt;2.4.1*） - 修復了使用 GraphQL 下達的訂單不會發送確認電子郵件的問題。
* **MDVA-30490** （*適用於 Adobe Systems Commerce 2.3.4 - 2.3.5-p2*） - 修復了如果某個產品具有空的簡短描述，產品比較會引發 500 錯誤頁面的問題。
* **MDVA-30232** （*適用於Adobe Systems商務 >=2.3.1 &lt;2.4.1*） - 修復了如果原始訂單包含禮品卡片則無法重新訂購的問題。
* **MDVA-29965** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.0*) — 修正客戶將產品新增至購物車時，收到「無效表單金鑰」錯誤的問題。
* **MDVA-30008** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正無法透過管理應用程式開發介面為公開目錄中的產品下單的B2B問題。
* **MDVA-22469** （*適用於 Adobe Systems Commerce 2.3.2-p2 - 2.3.3-p1*） - 修復了以下問題：升級到 Adobe Systems Commerce 2.3.3 后，頁面 Builder 無法在管理面板中運行，並且某些 JS 和 CSS 檔無法載入。
* **MC-35984** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正商家為退貨授權(RMA)建立運送標籤後，無法與退貨頁面上的任何頁面元素互動的問題。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*適用於Adobe Commerce 2.3.0 - 2.3.4*) — 修正[!DNL PayPal Payflow Pro]付款方法的問題，並在Chrome 80瀏覽器和API回應重新導向至客戶登入頁面中，將Cookie預設視為`SameSite=Lax`。
* **MDVA-26694** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) — 修正產品和目錄快取每天過期的問題，但過期時間排程不同。
* **MDVA-27825** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正因記憶體洩漏而匯出大量資料失敗的問題。
* **MDVA-29085** （*適用於 Adobe Systems Commerce >=2.3.0 &lt;=2.3.5-p1*） - 修正B2B的問題：如果 API 建立公司，則不會傳送任何必需的新公司電子郵件。
* **MDVA-29344** (*適用於Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) — 修正頁面產生器從標題元素複製文字至文字元素後卡住的問題。
* **MDVA-29835** (*適用於Adobe Commerce >2.3.1 &lt;2.4.2*) — 修正禮品卡訂單包含兩個代碼（而非一個）的問題。
* **MDVA-30052** (*適用於Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修正未正確填入私人內容（本機儲存）而導致效能問題的問題。
* **MDVA-30131** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正分層導覽的問題，其中若將[!DNL Elasticsearch]當做搜尋引擎使用，則布林值型別產品屬性的&#x200B;*No*&#x200B;值不會包含在分層導覽中。
* **MDVA-35514** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正在「建立封裝」強制回應視窗中建立送貨標籤及新增訂購產品至封裝的問題。
