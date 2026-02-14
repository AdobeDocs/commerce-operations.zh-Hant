---
title: 發行說明
description: 了解 Adobe Commerce 可用的修補程式及其解決的問題。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
type: Troubleshooting
source-git-commit: 151dc8bbf046b1c269c34dcfc66718136b4b8b02
workflow-type: tm+mt
source-wordcount: '30792'
ht-degree: 0%

---

# 發行說明

它 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由 Adobe 與 Magento 開源社群開發的個別修補程式。 它允許您套用、還原及查看所有已安裝版本 Adobe Commerce 可用的修補程式的一般資訊。 你可以對 Adobe Commerce 和 Magento 開源專案套用修補程式，不論是誰開發修補程式。 例如，你可以將社群開發的修補程式套用到 Adobe Commerce 專案。

>[!INFO]
>
>請參閱 [「套用修補」](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant#apply-individual-patches) 了解如何將修補程式套用到 Adobe Commerce 專案。 請參閱「軟體更新指南」中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)，以檢視已發行修補程式的完整清單。

>[!INFO]
>
>如需Magento Open Source社群所建立[!DNL quality patches]的相關資訊，請參閱[發行說明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md)。

## v1.1.77 {#v1-1-77}

* **ACSD-63687** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正因無法清除Redis快取而顯示錯誤價格的問題。
* **ACSD-68341** (適用於Adobe Commerce >=2.4.4 &lt;2.4.9) — 修正在PDP載入期間，在市集建立多個客戶區段時多次設定X-Magento-Vary Cookie的問題。
* **ACSD-68537** (適用於Adobe Commerce >=2.4.8 &lt;2.4.9) — 修正客戶區段數量增加導致簽出效能降低的問題。
* **ACSD-68664** （用於 Adobe Commerce >=2.4.6 &lt;2.4.9) - Fixes the issue where the scheduled update preview breaks when attempting to preview content for stores with custom domains.
* **ACSD-68759** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4-p2 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p1 &lt;2.4.9) - Fixes the issue where creating a customer account fails when using the Arabic locale and the Date of Birth (DOB) attribute is set to display on the storefront.&lt;/2.4.5>
* **ACSD-68892** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正可快取頁面未正確儲存或從Fastly快取中提供的問題，進而導致不一致的快取行為並降低效能。
* **ACSD-69016** (適用於Adobe Commerce >=2.4.7 &lt;2.4.9) — 修正在不同時區建立的網站的特殊價格未生效的問題。
* **ACSD-69020** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正可設定產品在任何子產品符合篩選條件時，便會自動包含在PageBuilder產品輪播清單中的問題。
* **ACSD-69237** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.9) - Fixes the issue where the number of entries that can be processed and inserted through the sales_*_async_insert cron jobs is limited to 100 per run.
* **ACSD-69311** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.9) - Fixes the issue with the incorrect tax calculation in credit memos when creating a partial refund from an invoice, if a previous credit memo was created from the order view page.
* **ACSD-69351** （用於 Adobe Commerce >=2.4.4 &lt;2.4.9) - Fixes the issue where gift cards balances and expiration dates are displayed not in accordance to the website scope assigned.
* **ACSD-69494** （用於 Adobe Commerce 與 Magento 開源 >=2.4.8 &lt;2.4.9) - Fixes the issues with the async refund operations where refund requests with the &quot;is_online&quot; parameter are not processed correctly.
* 更新版本： **ACSD-67250**
* 替換的補丁： **ACSD-62629**、 **ACSD-66157**
* 已棄用的修補程式： **ACSD-66157**

## v1.1.76 {#v1-1-76}

* **ACSD-67091** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正最大寫入集大小錯誤，以透過根據資料量實作兩種刪除策略來確保目錄規則產品索引清理。
* **ACSD-67370** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.9) — 修正PDP/PLP上套件組合產品的價格不正確以及多貨幣商店購物車頁面的多個問題。
* **ACSD-68410** (針對Adobe Commerce，B2B >=1.3.3 &lt;1.5.3) — 修正針對可轉讓報價下訂單時，不正確地新增或合併額外購物車明細至報價的問題。 離開可協商報價結帳的最後一步後，產品現在可以正確新增到購物車中。
* **ACSD-69086** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.8) - Fixes the issue where the cron job fails to clear changelog tables, causing Galera Cluster crashes when handling large amounts of data.
* **ACSD-69115** （用於 Adobe 商務 >=2.4.4 &lt;2.4.9) - Fixes an issue where shopping cart errors were not displayed to the admin user when managing the shopping cart for a customer assigned to a non-default website.
* **ACSD-69129** （用於 Adobe Commerce 與 Magento 開源 >=2.4.5 &lt;2.4.7 ||=&quot;&quot;>=2.4.8 &lt;2.4.9) - Fixes an issue where deleting the default base website and using the secondary website as the default resulted in an error when attempting to update the tier price for the secondary website via REST API.&lt;/2.4.7>
* **ACSD-69203** （用於 Adobe Commerce 與 Magento 開源 >=2.4.8 &lt;2.4.9) - Fixes an issue where the Products List widget returned incorrect results when multiple categories were listed in the category condition.
* **ACSD-69261** （用於 Adobe Commerce 與 Magento Open Source >=2.4.4 &lt;2.4.9) - Fixes an issue where a cart price rule coupon configured for single use per customer was reused multiple times due to incorrect handling of the `times_used` 屬性，適用於部分發票及剩餘數量註銷情境。
* **ACSD-69308** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.9) - Fixes an issue where catalog price rules did not apply when `special_price` 僅設定在網站層級（非「所有商店檢視」）。 修正後，目錄價格規則會正確適用，請先檢查網站預設商店。
* **ACSD-69319** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.9) - Fixes an issue where bundle prices were not indexed properly when child products had stock under custom sources.
* **ACSD-69325** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.9) - Fixes an issue where modifying the SKU case caused the product to appear out-of-stock on the storefront.
* **ACSD-69331** （用於 Adobe Commerce 與 Magento 開源 >=2.4.5 &lt;2.4.9) - Fixes an issue where content creators in the media gallery could not create folders with only the `create_folder` 權限。 修復後，他們可以正常建立資料夾。
* **ACSD-69333（** 用於 Adobe Commerce >=2.4.7 &lt;2.4.9) - Fixes an issue where SKU changes were allowed for products with an active Scheduled Update. 修正後，在持續更新期間禁止更改 SKU;存檔會以明顯錯誤失敗，管理員 SKU 欄位會被停用。 這可避免因 SKU 變動而在暫存回滾時造成 MSI 庫存不一致的情況。
* **ACSD-69541** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.9) - Fixes an issue where reducing a product&#39;s quantity in the admin to less than what already exists in a cart made it impossible to edit the product quantity in that cart via GraphQL.
* 更新版本： **ACSD-46541**、 **ACSD-53750**、 **ACSD-66404**
* 替換的補丁： **ACSD-66404**、 **ACSD-68499**

## v1.1.75 {#v1-1-75}

* **ACSD-68289** （用於 Adobe Commerce 與 Magento 開源 >=2.4.8 &lt;2.4.9) - Fixes an issue where full-text search now returns matching products if the minimum match condition is met across all searchable fields collectively, rather than requiring the condition to be satisfied by a single field.
* **ACSD-68359** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正使用[!UICONTROL Pick in Store]結帳時選取商店不再因購物車中有許多產品時具有長URL而失敗的問題。 之前，這會在選取商店期間產生過長的URL，導致客戶無法完成結帳，進而觸發&#x200B;*414錯誤*。
* **ACSD-68451** (針對Adobe Commerce，B2B >=1.5.2-p1 &lt;1.5.3) — 修正多個網站的問題，其中公司管理員登入一個網站、在另一個網站上建立不相關的公司，但錯誤地連結到該不相關的公司。
* **ACSD-68490** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正受限管理員使用者在可設定產品建立期間看見[!UICONTROL Add New Attribute]按鈕的問題。
* **ACSD-68517** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正目錄和目錄搜尋頁面上的表單重新提交錯誤。
* **ACSD-68573** (適用於Adobe Commerce >=2.4.5 &lt;2.4.9) — 修正類別許可權未正確套用至客戶願望清單專案的問題。 修正後，願望清單專案可在網頁和GraphQL中正確顯示和分頁。
* **ACSD-68615** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正當處理的組合遺失訂單識別碼時，存貨預留補償CLI會顯示例外狀況的問題。
* **ACSD-68793** (針對Adobe Commerce，B2B >=1.5.1 &lt;1.5.3) — 修正將有效產品指派至共用目錄時，有效產品會不正確地遭到拒絕的問題。
* **ACSD-68925** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正GraphQL要求的回應現在透過HTTP規格與GraphQL對齊的問題。 當請求無法剖析、未獲授權或遇到一般問題時，會傳回4XX回應代碼。 如果請求經過剖析且可以處理，則會傳回200回應代碼。
* 已更新的版本： **MDVA-19640**、**ACSD-47910**、**ACSD-68040**、**ACSD-62965**
* 已取代的修補程式： **ACSD-62577**，**ACSD-68011**

## v1.1.74 {#v1-1-74}

* **ACSD-68636** (適用於Adobe Commerce >=2.4.4 &lt;2.4.9) — 修正從其他商店建立發票時，商店擁有者的名稱未正確顯示在禮品卡電子郵件標題的問題。
* **ACSD-68430** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.8) — 修正記錄中包含多個已從屬性設定刪除的屬性選項時，無法儲存客戶或客戶地址的問題。
* **ACSD-68499** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正GraphQL `updateCartItems`突變在更新數量超過可用庫存時傳回錯誤成功回應，導致數量和總數膨脹的問題。
* **ACSD-68810** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正將訂單指派給在其他網站上建立之客戶（不論&#x200B;**[!UICONTROL Customer Account Sharing]**&#x200B;設定為何）的問題。
* 已更新的版本： **ACSD-49737**、**ACSD-57003-V2**
* 已取代的修補程式： **ACSD-61969**

## v1.1.73 {#v1-1-73}

* **ACSD-67171** (適用於Adobe Commerce >=2.4.4 &lt;2.4.9) — 修正B2B使用者在工作階段過期或在結帳期間被移除時看到&#x200B;*[!UICONTROL Access Denied]*&#x200B;頁面的問題。
* **ACSD-67908** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正JS檔案無法在多存放區設定中正確合併的問題。
* **ACSD-68190** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 修正未套用折扣、套用折扣未正確顯示在GraphQL購物車檢視回應中，以及移除優惠券折扣時移除非優惠券折扣的問題。
* **ACSD-68206** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.9) — 修正使用GraphQL應用程式伺服器並安裝&#x200B;**[!UICONTROL Rate Limiting]**&#x200B;功能和[!DNL PHP Redis]擴充功能時的錯誤。
* **ACSD-68356** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正GraphQL購物車查詢傳回虛擬報價不正確折扣金額的問題。
* **ACSD-68391** (適用於Adobe Commerce >=2.4.6-p10 &lt;2.4.9) — 修正&#x200B;**[!UICONTROL Quick Order]**&#x200B;和&#x200B;**[!UICONTROL Requisition Lists]**&#x200B;中未正確套用類別相關許可權的問題。
* **ACSD-68400** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正虛擬禮卡數量未準確反映在庫存預訂表格中的問題。

## v1.1.72 {#v1-1-72}

* **ACSD-68040** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正有許多歷史搜尋請求的[!DNL MariaDB] 10.6和11.4上，前端搜尋頁面效能降低的問題。
* **ACSD-67941** (適用於Adobe Commerce和Magento Open Source >=2.4.7-p1 &lt;2.4.8) — 修正具有未知篩選器名稱的GraphQL請求會導致PHP例外狀況記錄的問題。
* **ACSD-68064** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正建立已排程的更新在巢狀類別數量高的環境中導致重複專案的問題。
* **ACSD-66807** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正`report_viewed_product_index`表格顯示不正確產品頁面檢視計數的問題。
* **ACSD-67383** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正在同一工作階段中使用具有兩個公司管理員帳戶的&#x200B;**[!UICONTROL Login as Customer]**&#x200B;會導致&#x200B;*沒有具有cartId*&#x200B;的這類實體錯誤的問題。
* **ACSD-67518** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正進階報告在列計數超過批次大小時產生重複標題列的問題。
* **ACSD-67639** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正將&#x200B;**[!UICONTROL Dynamic Price]**&#x200B;設為&#x200B;*No*&#x200B;的套件組合產品無法建立銷退折讓單的問題。
* **ACSD-67696** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正快取排清後，`media_gallery`專案未傳回購物車GraphQL產品節點的問題。
* **ACSD-67946** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.9) — 修正購物車更新顯示重複錯誤橫幅的問題。
* **ACSD-68011** (針對Adobe Commerce，B2B >=1.5.1 &lt;1.5.3) — 修正透過`/V1/sharedCatalog/:id/assignProducts` [!DNL REST] API將不存在的SKU指派給共用目錄的問題。
* **ACSD-68118** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.9) — 修正`customerCart` GraphQL查詢傳回的產品屬性值未反映市集標題，而造成本地化不一致的問題。
* **ACSD-68092** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正因排程更新與基本產品資料之間同步處理不當而在多次儲存後遺失套件產品選項的問題。
* **ACSD-67424** (針對Adobe Commerce，B2B >=1.5.0 &lt;1.5.3) — 修正使用可轉讓引號時，`updated_at` `GET /carts/search` API回應中的[!DNL REST]值不符合&#x200B;**[!UICONTROL Admin panel]**&#x200B;中顯示值的問題。
* **ACSD-67187** (針對Adobe Commerce，B2B >=1.5.1 &lt;1.5.3) — 修正管理員使用者受限於非預設網站時看到錯誤&#x200B;*的問題。請至少建立公開共用目錄以繼續*，並且無法存取公司格線上的&#x200B;**[!UICONTROL Add New Company]**&#x200B;按鈕。
* 已更新的版本： **ACSD-49737**、**ACSD-53750**、**ACSD-51819**、**ACSD-55566**、**ACSD-62965**、**ACSD-63323**、**ACSD-63406**、**ACSD-66139**、**ACSD-66404**、**ACSD-67659** **ACSD-66301**
* 已取代的修補程式： **ACSD-62577**、**ACSD-63325**、**ACSD-67102**

## v1.1.71 {#v1-1-71}

* **ACSD-60624** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正頁面產生器中&#x200B;**[!UICONTROL Upload Image]**、[!UICONTROL Image]和[!UICONTROL Banner]區段的[!UICONTROL Slider]無法用於空白內容的問題。
* **ACSD-67089** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正`inventory/export-stock-salable-qty` API中的分頁問題，此錯誤會將`total_count`限製為頁面大小。
* **ACSD-67093** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正使用日期範圍篩選器透過GraphQL擷取訂單時，傳回錯誤結果的問題。
* **ACSD-67459** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.9) — 修正說明長度超過65,536個字元的產品無法匯入的問題。
* **ACSD-67603** (適用於Adobe Commerce >=2.4.6 &lt;2.4.8) — 修正啟用影像包含之產品的Sitemap產生造成處理時間過長的問題。
* **ACSD-67643** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正排程更新期間，在有大量巢狀類別的環境中建立重複專案的問題。
* **ACSD-67652** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正GraphQL呼叫中，即使子產品和父產品有庫存，也會將套件組合產品狀態傳回為無庫存的問題。
* **ACSD-67904** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正城市名稱包含數字(0-9)、&amp;符號(&amp;)、句點(.)或括弧()時無法下單的問題。
* 已取代的修補程式： **ACSD-61322**，**ACSD-65848**

## v1.1.70 {#v1-1-70}

* **AC-15210** (適用於Adobe Commerce和Magento Open Source >=2.4.6-p3 &lt;2.4.9) — 將USPS整合從過時的網頁工具API移轉至新的RESTful USPS API。
* **ACSD-67102** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正Adobe Commerce後端載入&#x200B;**[!UICONTROL Categories]**&#x200B;緩慢的問題。
* **ACSD-66120** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正當目錄價格設定為包含稅捐時，[!DNL GraphQL]無法正確顯示折扣百分比和基本價格的問題。
* **ACSD-66157** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.9) — 修正在不同時區建立的網站的特殊價格未生效的問題。
* **ACSD-67659** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正轉譯的錯誤訊息傳回「未定義」錯誤碼的問題。
* **ACSD-67166** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正當在店面載入報價時多次執行`cataloginventory_stock_status`查詢，導致重複資料庫呼叫的問題。
* **ACSD-67289** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正套用特殊價格時未顯示一般價格的問題。
* **ACSD-67686** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p15 &lt;2.4.5) || >=2.4.5-p14 &lt;2.4.6 || >=2.4.6-p12 &lt;2.4.7) — 修正提交空的`Syntax Error: Unexpected <EOF>`請求時發生[!DNL GraphQL]錯誤的問題。
* **ACSD-67250** (適用於Adobe Commerce >=2.4.7-p4 &lt;2.4.8) — 修正&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;儲存作業會更新所有專案，而非僅更新受影響的專案，並透過消除不必要的作業來改善效能的問題。
* **ACSD-67030** (適用於Adobe Commerce >=2.4.4 &lt;2.4.9) — 修正受限角色管理員編輯時，從可設定產品中取消指派簡單產品的問題。
* 已更新的版本： **ACSD-54095**、**ACSD-51636**、**ACSD-51739**、**ACSD-66093**
* 已取代的修補程式： **ACSD-62415**

## v1.1.69 {#v1-1-69}

* **AC-15223** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正2.4.8店面中在切換存放區後，從快取中提供頁面且未反映所選存放區的問題。
* **ACP2E-3731** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正可見度為&#x200B;**[!UICONTROL Catalog, Search]**&#x200B;的產品匯出不正確地包含多商店環境中其他商店檢視的記錄的問題。
* **ACP2E-3767** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正無法移除套件組合產品中最後一個套件組合選項的問題。
* **ACP2E-3964** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.8) - Fixed the issue where child products of configurable products could not be listed via the REST API when a video was set in the gallery.
* **ACP2E-3977** （用於 Adobe Commerce >=2.4.4 &lt;2.4.9) - Fixes the issue where the **[!UICONTROL Cap Reward Points Balance At]** 欄位，設定時 [!UICONTROL Rewards Points Balance Redemption Threshold] 欄位不能空，會導致驗證錯誤。
* **ACP2E-4050** （用於 Adobe Commerce 與 Magento 開源 >=2.4.5 &lt;2.4.8) - Fixes the issue where cart price rules fail to apply correctly for multi-shipping products when bundle product is used and sub-select conditions are used with free shipping is enabled.
* **ACSD-56226** （用於 Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where READ queries at the slave node return outdated data when the `synchronous_replication` 標誌已啟用。
* **ACSD-57477** （用於 Adobe Commerce 與 Magento 開源 >=2.4.6 &lt;2.4.7) - Fixes the issue where sales rule processing causes slow performance on cart-related requests.
* **ACSD-58108** （用於 Adobe Commerce 與 Magento 開源 >=2.4.6 &lt;2.4.8) - Fixes the issue where the missing joining table name in the original fetching table caused errors with custom module extension SQL in the order grid.
* **ACSD-65983** （用於 Adobe Commerce >=2.4.6-p10 &lt;2.4.9) - Fixes the issue where reconfiguring a bundled product quote in the Admin backend throws an error.
* **ACSD-66149** （適用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.8) - Fixes the issue where the IPN handler returns a *，未支援或未知 IPN 類型出現 500* 錯誤。
* **ACSD-66153** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.9) - Fixes the issue where a page returns a *因快取錯誤排版結構導致 500* 錯誤。
* **ACSD-66302** （用於 Adobe Commerce 與 Magento 開源 >=2.4.8 &lt;2.4.9) - Fixes the issue where wishlist items are incorrectly filtered by store ID instead of being filtered by website.
* **ACSD-66311** （用於 Adobe Commerce >=2.4.6-p9 &lt;2.4.9) - Fixes the issue where the Companies grid loads slowly for admin users with restricted websites access.
* **ACSD-66404** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正cron工作無法清除changelog表格、在處理大量資料時導致[!DNL Galera Cluster]當機的問題。
* **ACSD-66952** (適用於Adobe Commerce >=2.4.4 &lt;2.4.9) — 修正每次PLP或購物車造訪時清除快取的問題，這會在設定目標規則時造成效能額外負荷。
* **ACSD-67264** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正跨裝置的套件組合和可下載產品頁面配置不一致的問題。
* **ACSD-67347** (適用於Adobe Commerce和Magento Open Source >=2.4.5-p11 &lt;2.4.6) — 修正當使用具有特殊字元的優惠券且啟用檔案鎖定時，順序失敗的&#x200B;*無法取得鎖定*&#x200B;錯誤的問題。
* 已取代的修補程式： **ACP2E-3841**

## v1.1.68 {#v1-1-68}

* **ACSD-58131** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.8) - Fixes the issue where the presence of a 0-byte image in the media gallery prevented all images in the directory from being displayed or selected.
* **ACSD-62415** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正Adobe Commerce後端載入類別非常緩慢的問題。
* **ACSD-66082** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.9) — 修正無法透過產品匯入更新產品的色票影像的問題。
* **ACSD-66179** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p11 &lt;2.4.5) || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.9) — 修正取消以「未擷取」付款型別建立的商業發票會導致404錯誤頁面的問題。
* **ACSD-66865** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正儲存目錄價格規則使索引子失效的問題，並提供僅重新索引受影響產品的替代方案。
* **ACSD-66963** （針對 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.8) - Fixes the issue where the `estimateTotals` 變異，當折扣碼套用於包含虛擬產品的購物車時，折扣會回傳為空。
* **ACSD-67039** （適用於 Adobe Commerce 與 Magento 開源>=2.4.4 &lt;2.4.8) - Fixes the issue where customer records were not saved due to validation of the `rp_token` ，系統屬性與變音符號驗證現僅套用於產生的客戶電子郵件。
* **ACSD-62146** （用於 Adobe Commerce >=2.4.7 &lt;2.4.8) - Fixes the issue where the selected billing address disappears on the checkout payment page when address search is enabled and &quot;Number of Customer Addresses Limit&quot; is set to 1.
* **ACSD-65938** （用於 Adobe Commerce >=2.4.4 &lt;2.4.9) - Fixes the issue where gift card emails were sent even when the invoice creation failed.
* **ACSD-66072** （用於 Adobe Commerce >=2.4.6 &lt;2.4.9) - Fixes the issue where related products were not returned via GraphQL on the Product Detail Page due to an internal server error when &quot;Related Product Rules&quot; were configured.
* **ACSD-66233** (適用於Adobe Commerce >=2.4.8 &lt;2.4.9) — 修正管理員使用者因無法載入「新增產品」快顯視窗而無法新增產品至類別的問題。
* **ACSD-66889** (適用於Adobe Commerce >=2.4.4 &lt;2.4.6) — 以正確結構修正已棄用的程式碼行，以確保成功完成清查索引子程式。
* **ACSD-66965** (適用於Adobe Commerce B2B >=1.5.0 &lt;1.5.3) — 修正「請購單清單頁面列印選項」造成錯誤的問題。
* **ACSD-66506** (適用於Adobe Commerce B2B >=1.5.0 &lt;1.5.3) — 修正先前指派的共用目錄產品遭到刪除及指派新產品時發生的後端錯誤。
* **ACSD-66417** (適用於Braintree 4.6.1) — 修正嘗試依日期篩選訂單時，銷售訂單格線擲回錯誤的問題。
* 已更新的版本： **ACSD-60590**，**ACP2E-3705**
* 已取代的修補程式： **ACSD-57003**，**ACSD-66434**

## v1.1.67 {#v1-1-67}

* **ACSD-65935** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正刪除產品時，`customerOrders` GraphQL查詢傳回內部伺服器錯誤的問題。
* **ACSD-66049** (適用於Adobe Commerce和Magento Open Source >=2.4.5-p3 &lt;2.4.6) || >=2.4.7 &lt;2.4.9) — 修正非英文店面因ICU程式庫版本而顯示不正確定價的問題。
* **ACSD-66084** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.9) — 修正訂單API回應中將`row_total_incl_tax`傳回為接近零的殘值的問題，而非完全折扣專案的0.00。
* **ACSD-66118** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正未重新整理設定快取時，更新存放區檢視程式碼會清除[!UICONTROL Design Configuration]設定的問題。
* **ACSD-66139** (適用於Adobe Commerce >=2.4.7 &lt;2.4.8) — 修正GraphQL呼叫對不存在或非使用中的購物車下訂單時傳回&#x200B;*未定義*&#x200B;錯誤碼的問題。
* **ACSD-66301** (適用於Adobe Commerce和Magento Open Source >=2.4.6-p9 &lt;2.4.7) || >=2.4.7-p4 &lt;2.4.8) — 修正在「管理員」中將產品從訂單移回購物車導致數量不符的問題。
* **ACSD-66434** (適用於Adobe Commerce >=2.4.6-p8 &lt;2.4.9) — 修正公司GraphQL查詢中缺少客戶ID的問題。
* **ACSD-66441** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.8) — 修正當索引多存放區設定的可設定產品時，存放區在階層式導覽中顯示不正確索引資料的問題。
* **AC-14984** (適用於Adobe Commerce和Magento Open Source >=2.4.6-p10 &lt;2.4.7) || >=2.4.8 &lt;2.4.9) — 修正RabbitMQ SSL連線上的錯誤&#x200B;*無效的框架型別21*。
* **AC-14985** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正使用啟用TLS的外部`smtp`伺服器時未傳送電子郵件的問題。
* 已更新的版本： **MDVA-12304**、**ACSD-47920**、**ACSD-56447**、**ACSD-61845**、**ACSD-64118**

## v1.1.66 {#v1-1-66}

* **ACP2E-3789** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.9) — 修正提供媒體ID時，透過[!DNL WebAPI]重複媒體檔案更新產品的問題。
* **ACP2E-3918** (適用於Adobe Commerce >=2.4.5 &lt;2.4.9) — 修正登入公司客戶在沒有預設帳單地址的情況下使用店內見面交收服務的結帳失敗問題。
* **ACSD-65750** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.9) — 修正GraphQL `route`查詢傳回產品在頁面產生器產品內容型別中順序不正確的問題。
* **ACSD-65775** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正訂購相同專案的多個數量時，[!DNL REST] API訂購詳細資料傳回不正確`base_row_total`和`row_total`值的問題。
* **ACSD-65777** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正`types` GraphQL請求中產品影像型別缺少`MediaGallery`欄位的問題。
* **ACSD-65848** (適用於Adobe Commerce和Magento Open Source >=2.4.8 &lt;2.4.9) — 修正使用子選取計算類別中產品總數的問題，方法是重構方法以使用連線。
* **ACSD-65913** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.9) — 修正具有相同價格之產品類別的[!DNL OpenSearch]擲回&#x200B;*illegal_argument_exception*&#x200B;錯誤的問題。
* **ACSD-66041** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正因缺少`CountryID`而無法搜尋取車地點愛爾蘭(IE)郵遞區號的問題。
* **ACSD-66212** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.9) — 修正匯入客戶CSV檔案兩次，導致第二次和後續嘗試失敗的問題。
* 已更新的版本： **MDVA-12304**、**MDVA-19640**、**ACP2E-3841**、**ACSD-65100**、**ACSD-65787**、**ACP2E-3753**、**ACSD-65202**、**ACSD-65331**、**ACSD-65822**

## v1.1.65 {#v1-1-65}

* **ACP2E-3753** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正多存放區設定中的產品警報電子郵件一律使用預設主題傳送的問題，無論存放區或主題設定為何。
* **ACSD-64118** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正同時要求儲存和更新相同產品導致資料不一致或產品重複的問題。
* **ACSD-64813** (適用於Adobe Commerce >=2.4.4 &lt;2.4.9) — 修正透過[!DNL B2B] API從[!DNL REST]共用目錄取消指派類別太久或大型目錄逾時的問題。
* **ACSD-65202** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正「我的帳戶」頁面未顯示同一商店內其他商店檢視的最近訂單的問題。
* **ACSD-65254** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正使用`updateCustomerEmail` [!DNL GraphQL]突變更新客戶帳戶上的電子郵件地址後，未傳送電子郵件通知給客戶的問題。
* **ACSD-65331** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正重複導覽回結帳頁面後，[!UICONTROL Pick in Store]中選取的存放區被清除的問題。
* **ACSD-65822** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正[!UICONTROL Customer's Activities]下購物車面板中無法正確顯示套件組合和可設定產品數量的問題。
* **ACSD-66093** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正電子郵件地址可能輸入到訪客客戶的[!UICONTROL First Name]和[!UICONTROL Last Name]欄位中，導致訂單確認電子郵件無效的問題。
* 更新的版本： **ACSD-51291**
* 已取代的修補程式： **ACSD-61522**

## v1.1.64 {#v1-1-64}

* **ACP2E-3838** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p9 &lt;2.4.4-p13) || >=2.4.5-p8 &lt;2.4.5-p12 || >=2.4.6-p6 &lt;2.4.6-p10 || >=2.4.7 &lt;2.4.7-p5) — 修正[!DNL Page Builder] CORS錯誤導致無法在生產模式中儲存管理面板中的變更的問題。
* **ACP2E-3841** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.8) — 修正使用子選取條件並啟用免運費時，多送貨產品的購物車價格規則無法正確套用的問題。
* **ACSD-63139** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正產品屬性包含數千個選項值時產品匯出失敗的問題。
* **ACSD-65100** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正在[!UICONTROL Maximum Width]設定中移除[!UICONTROL Maximum Height]和[!UICONTROL Media Gallery Image Optimization]的值會在影像最佳化程式期間導致錯誤的問題。
* **ACSD-65127** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正在生產模式中啟用JavaScript縮制會導致[!DNL TinyMCE] 6在瀏覽器主控台中產生錯誤，進而影響功能和使用者體驗的問題。
* **ACSD-65787** (適用於Adobe Commerce和Magento Open Source >=2.4.7-p5 &lt;2.4.8) — 修正SchemaBuilder類別在結構描述建立期間當機，或在處理資料表資料時因未定義的陣列索引鍵「欄」而更新的問題。
* **ACSD-65223** (適用於Adobe Commerce、B2B 1.5.1) — 修正手動為[!DNL B2B]份採購單選取條款與協定導致錯誤的問題。
* **ACSD-65540** (適用於Adobe Commerce，B2B 1.5.2) — 修正更新`REGEXP_LIKE`表格時，因缺少`company_structure`函式而發生SQL語法錯誤的問題。
* **ACSD-65684** (適用於Adobe Commerce、B2B 1.5.2) — 修正更新為`Magento_Company` 1.5.2後，處理[!DNL B2B]表格中的大量記錄(~100,000+)時，耗用超長時間的效能問題。`company_structure`
* 已更新的版本： **ACSD-48234**、**ACSD-51819**、**ACSD-57570**、**ACSD-56415**

## v1.1.63 {#v1-1-63}

* **ACSD-64627** (適用於Adobe Commerce >=2.4.6-p8 &lt;2.4.8) — 修正在「公司結構」中新增或編輯使用者時，無法儲存自訂客戶屬性的問題。
* **ACSD-64753** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正當送貨地址變更時，即使商店半徑之外，「店內提貨」中預先選取的商店不會更新的問題。
* **ACSD-65195** （用於 Adobe Commerce >=2.4.4 &lt;2.4.8) - Fixes the issue where the GraphQL mutation `createCompany` 會因未指定區域的國家而產生錯誤。
* **LYNX-839** （用於 Adobe Commerce 2.4.8）- 移除透過 GraphQL 揭露的客戶群組、細分區段及促銷規則資訊。
* 已更新的版本： **MDVA-12304**、**ACSD-48234**、**ACSD-58054**

## v1.1.62 {#v1-1-62}

* **ACSD-63406** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p9 &lt;2.4.5) || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) — 修正當`persistent_clear_expired` cron工作執行時，任何cron工作都無法清除過期的永久性引號的問題。
* **ACSD-63520** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正透過&#x200B;**[!UICONTROL Configurations]**&#x200B;在管理面板中新增的影像未遵守上傳大小上限的問題。
* **ACSD-64523** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正可能透過匯入程式（管理員或API）建立無名稱的新產品的問題，這會中斷管理員介面並導致產品無效。
* **ACSD-64532** （用於 Adobe Commerce 與 Magento 開源 >=2.4.6-p2 &lt;2.4.8) - Fixes the issue where an ENV variable set to &quot;false&quot; is treated as a string &quot;false&quot; instead of a boolean false.
* **ACSD-64592** （用於 Adobe Commerce >=2.4.4 &lt;2.4.8) - Fixes the issue where the claim link from the email for a gift card in non-default stores always redirected the gift card claim to the default website.
* **ACSD-65164** （適用於 Adobe Commerce 與 Magento 開源 >=2.4.6 &lt;2.4.8) - Fixes the issue where the error message *部分選中項目選項目前無法使用* ，發生在重新訂購可設定產品時，僅選出一個勾選的勾選框自訂選項。
* **ACSD-64732** （用於 Adobe Commerce >=2.4.4 &lt;2.4.8) - Fixes the issue where 3rd party controllers were not cached correctly with customer segments.

## v1.1.61 {#v1-1-61}

* **ACP2E-3689** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.8) - Fixes multiple issues with category tree display on deeper levels and reflecting anchor/non-anchor relationships.
* **ACP2E-3705** （用於 Adobe Commerce >=2.4.7 &lt;2.4.8) - Fixes an issue where the `indexer_update_all_views` ，設定 時 cron 執行失敗 `MAGE_INDEXER_THREADS_COUNT` 。
* **ACSD-63883** （用於 Adobe Commerce >=2.4.4 &lt;2.4.7-p4) - Fixes the issue where the Requisition List returns an incorrect `items_count` ，在 GraphQL 回應中。
* **ACSD-63974** （用於 Adobe 商務 >=2.4.4 &lt;2.4.8) - Fixes the issue where the Requisition list page takes too much time to load when there are too many items, by adding a pagination feature to the Requisition list grid on the Storefront, that displays only portions of records that are limited to the number of records per page, instead of all the records at once.
* **ACSD-64178** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.8) - Fixes the issue where the Attribute Set edit page loads slowly if there are thousands of product attributes.
* **ACSD-64209** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正cron排程器擷取所有可協商的引號，但不排除狀態為&#x200B;**[!UICONTROL ordered]**&#x200B;的引號，從而導致觸發電子郵件或電子郵件的問題。
* **ACSD-64431** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 請求中包含優惠券代碼資訊的`placeOrder`突變不再擲回內部錯誤，而是顯示已成功下訂單。
* **ACSD-64467** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正儲存商店檢視層級的類別說明後，WYSIWYG編輯器顯示為空白的問題。
* **ACSD-64546** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正UI中出現一般錯誤訊息，以及在UPS傳送標籤建立期間於記錄中儲存&#x200B;*陣列至字串轉換*&#x200B;例外狀況的問題，以確保在UI中顯示實際錯誤，並將正確的錯誤訊息儲存在記錄中。
* **ACSD-64684** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正因數字&#x200B;*一千(1,000)*&#x200B;中的逗號（千位分隔符號）而在編輯及儲存值大於&#x200B;*999*&#x200B;的禮品卡時發生驗證錯誤的問題。
* 已更新的版本： **ACSD-49392**、**ACSD-50368**、**ACSD-51819**、**ACSD-54966-V2**、**ACSD-57003**、**ACSD-62979**、**ACSD-64112**
* 已取代的修補程式： **ACSD-49392**、**ACSD-58739**、**ACSD-62689**、**ACSD-64112**
* 已棄用的修補程式： **ACSD-46192**，**ACSD-52133**

## v1.1.60 {#v1-1-60}

* **ACSD-63323** (適用於Adobe Commerce >=2.4.7 &lt;2.4.8) — 修正將產品新增至類別時，**[!UICONTROL Select All]**&#x200B;選項無法運作的問題。 此外，透過快顯視窗格線將產品新增至類別時，它可確保分頁和紀錄計數標籤正確運作。
* **ACSD-63992** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正無法透過Admin UI正確套用購物車價格規則（包含優惠券和基於送貨方法的條件）的問題。
* **ACSD-64111** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正在[!DNL Page Builder]中設定產品元件的巢狀條件時發生錯誤的問題。
* **ACSD-64137** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正依郵遞區號搜尋取車地點不適用於荷蘭當地語系化的問題。
* **ACSD-64149** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正僅編輯其中一個日期時，可以儲存具有日期範圍條件的客戶區段的問題。
* 已更新的版本： **MDVA-12304**、**ACSD-45049**、**MDVA-43824**、**ACSD-46192**、**ACSD-50368**、**ACSD-52133**、**ACSD-47657**、**ACSD-51819**、**ACSD-54966-V2**、**ACSD-55628** **ACSD-45049**，**ACSD-63242**

## v1.1.59 {#v1-1-59}

* **ACSD-63454** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正下拉式清單及多選屬性的預設值未正確儲存在資料庫中的問題。
* **ACSD-63574** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正透過Page Builder將套件組合產品清單新增至區塊導致錯誤的問題。
* **ACSD-63793** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.8) — 修正匯入程式在不同瀏覽器分頁中互相干擾的問題。
* **ACSD-64113** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.8) — 修正透過媒體集以相對較小的寬度上傳影像（反之亦然）時，導致管理員發生錯誤的問題。
* **ACSD-64212** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.8) — 修正下訂單後，透過GraphQL建立帳戶時，訂單與客戶帳戶沒有關聯的問題。
* **ACSD-63469** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7 &lt;2.4.8) - Fixes the issue where fixed-amount discounts for the whole cart were not being applied properly when more than one rule was applied.
* **ACSD-63870** （用於 Adobe Commerce >=2.4.4 &lt;2.4.4-p11) - Fixes the issue where a company customer wasn&#39;t logged out properly when the company status changes during the customer active session.
* **ACSD-64112** （用於 Adobe Commerce >=2.4.5 &lt;2.4.8) - Fixes an issue where the `indexer_update_all_views` ，設定 `MAGE_INDEXER_THREADS_COUNT` 時 cron 執行失敗。
* 更新版本： **ACSD-61622**
* 替換的補丁： **ACSD-61553**
* 已棄用補丁： **ACSD-61199**

## v1.1.58 {#v1-1-58}

* **ACSD-48570**（用於 Adobe Commerce 和 Magento 開源 >=2.4.4 &lt;2.4.7) - Fixes the issue where the reset password page couldn&#39;t be reached by clicking the [!UICONTROL Admin] 重設密碼連結，啟用 **URL 新增商店代碼**&#x200B;**，過去會顯示登入頁面或 404 頁面。
* **ACSD-62118** (適用於Adobe Commerce >=2.4.6 &lt;2.4.8) — 修正使用「採購單」方法下達`sales_order_tax_item`份訂單時，[!DNL B2B]表格未完全更新的問題。
* **ACSD-63067** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正所有產品數量皆未正確標示的問題，且僅有一個數量不正確時，會針對分組產品中的所有產品顯示訊息&#x200B;*[!DNL Please specify the quantity of product(s).]*。
* **ACSD-63090** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正將產品新增到購物車後，當產品被刪除時購物車專案被移除的問題。
* **ACSD-63182** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正儲存已啟用&#x200B;**[!DNL MSI]** *且重複的套件組合產品時發生錯誤的問題*。
* **ACSD-63283** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正從禮品登入訂購專案時發生例外狀況，以及禮品登入更新包含不屬於登入之專案的問題。
* **ACSD-63299** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正店面未顯示可設定產品的特殊價格的問題。
* **ACSD-63325** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正提交空的`Syntax Error: Unexpected <EOF>`請求時發生[!DNL GraphQL]錯誤的問題。
* **ACSD-63329** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正透過&#x200B;**[!UICONTROL Date]**&#x200B;建立產品時，具有&#x200B;**[!UICONTROL Date and Time]**&#x200B;或[!DNL REST API]輸入型別的屬性預設值未設定的問題。
* **ACSD-63572** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.8) — 修正索引器處理序終止時，`CatalogRule`索引器暫存資料表未清理的問題。
* **ACSD-63578** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正在&#x200B;**[!UICONTROL Delete]**&#x200B;中按一下&#x200B;**[!UICONTROL Add to Order by SKU]**&#x200B;中的[!UICONTROL Admin]按鈕未移除[!DNL SKU]的問題。
* 更新的版本： **MDVA-39305-V3**
* 已取代的修補程式： **ACSD-56280**
* 已棄用的修補程式： **ACSD-62872**

## v1.1.57 {#v1-1-57}

* **ACSD-57570** (適用於Adobe Commerce >=2.4.4 &lt;2.4.4-p10) — 修正具有特定商店存取權的受限制管理員使用者無法一律看見指派產品的所有共用目錄，也無法看見無法儲存的客戶，導致系統不一致的問題。
* **ACSD-58325** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正驗證錯誤後仍可使用&#x200B;**[!UICONTROL Import]**&#x200B;按鈕的問題。
* **ACSD-59083** (適用於Adobe Commerce >=2.4.4 &lt;2.5.0) — 修正某些資料庫更新作業導致&#x200B;*基底資料表或找不到檢視的問題*&#x200B;錯誤（如果[!DNL mview]更新同時執行）。
* **ACSD-61622** (適用於Adobe Commerce和Magento Open Source >=2.4.6-p1 &lt;2.4.7) — 修正回應中缺少[!DNL FedEx]帳戶特定費率的問題。
* **ACSD-61895** (適用於Adobe Commerce >=2.4.4 &lt;2.5.0) — 修正即使根類別沒有[!DNL GraphQL]允許&#x200B;**許可權，類別**&#x200B;查詢仍會傳回具有&#x200B;**允許**&#x200B;許可權的類別的問題。
* **ACSD-62212** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.5.0) — 修正&#x200B;**忘記密碼**&#x200B;電子郵件內容未翻譯成商店檢視語言的問題。
* **ACSD-62481** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.5.0) — 修正即使啟用&#x200B;**[!UICONTROL Persistence]**，客戶的購物車還是空白的問題。
* **ACSD-62629** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.5.0) — 修正&#x200B;**[!UICONTROL Widgets]**&#x200B;中使用的產品清單未反映類別條件的問題。
* **ACSD-62635** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.5.0) — 修正[!DNL GraphQL]產品查詢中無法正確顯示多商店相關產品的問題。
* **ACSD-62671** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.5.0) — 修正[!DNL GraphQL]請求在第一次嘗試時未傳回最新位址資訊的問題。
* **ACSD-62689** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.5.0) — 修正客戶在&#x200B;**[!UICONTROL Related Product Rules and Widgets]**&#x200B;深度4 *後無法在*&#x200B;中新增類別的問題。
* **ACSD-62708** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p11 &lt;2.4.5) || >=2.4.5-p10 &lt;2.4.6-p2 || >=2.4.6-p8 &lt;2.4.7-p1) — 修正管理員中[!DNL TinyMCE] 7編輯器字型大小顯示&#x200B;*PT*&#x200B;而非&#x200B;*PX*&#x200B;的問題。 現在，您也可以以&#x200B;*PX*&#x200B;設定字型大小，而非&#x200B;*PT*。
* **ACSD-62758** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.5.0) — 修正&#x200B;**[!UICONTROL Configurable Product]**&#x200B;包含選取的選項時，產品影片無法在[!DNL URL]的詳細資料頁面上正確轉譯的問題。
* **ACSD-62951** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.5.0) — 修正傳送銷退折讓單電子郵件（不含專案和總計）的問題。
* **ACSD-62965** (適用於Adobe Commerce >=2.4.7 &lt;2.5.0) — 修正訂單位置`LocalizedException`回應中未包含[!DNL GraphQL]訊息的問題。
* **ACSD-63286** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正透過[!DNL API]指派給共用目錄的產品在執行手動重新索引前未出現在店面的問題。
* **ACSD-63326** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.5.0) — 修正從後端下訂單後，[!UICONTROL Admin]會重新導向至中斷頁面的問題。
* 更新的版本： **ACSD-51739**
* 已取代的修補程式： **MDVA-43451**，**ACSD-62755**

## v1.1.56 {#v1-1-56}

* **ACSD-63244** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正[!DNL JavaScript]錯誤導致[!DNL Google Maps]無法正確呈現的問題。 修正許多&#x200B;*Uncaught TypeError的問題：這個。_each不是*&#x200B;面板中主控台中的函式[!UICONTROL Admin]錯誤。
* **ACSD-63242** (適用於Adobe Commerce和Magento Open Source >=2.4.6-p8 &lt;2.4.7) || >=2.4.7-p3 &lt;2.4.8) — 修正新增包含超過10,000個專案的目錄產品時，匯入緩慢的問題。
* **ACSD-63062** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正套用多個重疊規則時發生錯誤購物車折扣計算的問題。
* **ACSD-62979** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正在[!UICONTROL Store ID]標頭中使用錯誤[!DNL GraphQL]導致嚴重記憶體錯誤的問題。
* **ACSD-62971** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正匯入&#x200B;**quantity**&#x200B;欄中有非數值的庫存來源導致&#x200B;**quantity**&#x200B;設定為&#x200B;*0*&#x200B;的問題。
* **ACSD-62872** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正唯一屬性驗證的問題，其中排程更新驗證不正確。
* **ACSD-62755** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p11 &lt;2.4.5) || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) — 修正[!DNL TinyMCE] 7需要在編輯器初始化設定中特別新增字型大小和字型的問題。
* **ACSD-62670** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p11 &lt;2.4.5) || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) — 修正[!UICONTROL Products Ordered]報告匯出至[!DNL CSV]且[!DNL XML]傳回錯誤的問題。
* **ACSD-62577** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 透過最佳化查詢和表格索引，修正店面搜尋查詢效能緩慢的問題。
* **ACSD-62475** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正[!UICONTROL Gift Card]產品在購物車中錯誤合併的問題。
* **ACSD-62428** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正當`is_out_of_stock`未設為可搜尋屬性時，[!DNL SKU]在目錄搜尋索引中設為不正確值的問題。
* **ACSD-62355** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.8) — 當可設定產品是以具有許多值的許多屬性為基礎時，可改善可設定產品編輯頁面的載入時間。
* **ACSD-61805** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正透過[!DNL REST API]更新延期交貨狀態後，店面產品無存貨的問題。
* **ACSD-60811** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正目前狀態為&#x200B;*正在處理*&#x200B;或&#x200B;*詐騙*&#x200B;時，才能使用自訂值或註解更新訂單狀態的問題。
* **ACSD-62952** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正店面未正確顯示[!UICONTROL Gift Registry]日期的問題。
* **ACSD-55339** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正以&quot;0&quot; （零）開頭的產品[!DNL SKU]移除&quot;0&quot;，導致引號無法更新的問題。
**
* 更新的修補程式： **ACSD-59514**
* 更新的版本： **ACSD-60816**
* 已取代的修補程式： **ACSD-59967**

## v1.1.55 {#v1-1-55}

* **ACSD-58383** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正透過[!DNL REST API]發出退款，且同時執行兩個相同請求的問題，並建立重複的銷退折讓單。
* **ACSD-58471** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正排程相關目錄價格規則時，產品詳細資料頁面上無法載入動態內容的問題。
* **ACSD-58566** (適用於Adobe Commerce >=2.4.6 &lt;2.4.8) — 修正查詢[!DNL GraphQL]突變中的`created_at`欄位時，`addPurchaseOrderComment`傳回內部伺服器錯誤的問題。
* **ACSD-58685** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正當電子郵件通訊停用時，系統仍會在重新啟用電子郵件通訊後傳送銷售電子郵件的問題。
* **ACSD-58735** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正受限管理員無法檢視關聯網站[!UICONTROL Admin]中客戶帳戶頁面上的放棄購物車的問題。
* **ACSD-58828** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.8) — 修正伺服器端驗證訊息&#x200B;*位址為必要的問題* （若任何必要欄位留空）會連同使用者端驗證訊息一併顯示。 伺服器端驗證不會顯示空白必填欄位的訊息，而使用者端驗證將處理錯誤通知，指出&#x200B;*這是必填欄位。*
* **ACSD-60344** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正使用&#x200B;**[!UICONTROL Purchase Order]**&#x200B;進行自動核準時傳送重複訂單確認電子郵件的問題。
* **ACSD-61348** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正透過[!DNL GraphQL]顯示願望清單專案，但在多網站環境中不會顯示在店面的問題。
* **ACSD-61534** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正無法使用`bin/magento config:set`命令設定設計組態，以及透過表單操控變更鎖定值的問題。 現在無法更新從[!DNL CLI]設定的`--lock-env`或`--lock-conf`鎖定值。
* **ACSD-61785** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正無法透過`reward_warning_notification`突變和[!DNL GraphQL]呼叫更新[!DNL REST API]屬性的問題，使其行為符合`reward_update_notification`。
* **ACSD-62591** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正設定&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;時主題未正確切換的問題。
* **ACSD-62793** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正匯出資料中`datetime`屬性不包含時間元件的問題。 此外，如果&#x200B;**[!UICONTROL Fields Enclosure]**&#x200B;已啟用&#x200B;**，則`additional_attributes`資料行中的屬性值將會括在雙引號中。
* **ACSD-62332** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正產品清單[!DNL GraphQL]查詢限製為10,000項產品中的`total_count`的問題。 修正當透過[!DNL Live Search]查詢時，*在搜尋條件中將目前頁面設定為* 1 *而非頁面* 2[!DNL GraphQL]的問題。
* 已更新的版本： **ACSD-46581**、**ACSD-49513**、**ACSD-52801**、**ACSD-59514**
* 已取代的修補程式： **ACSD-52801**，**ACSD-55100**
* 已棄用的修補程式： **ACSD-52085**，**ACSD-57854**

## v1.1.54 {#v1-1-54}

* **AC-13283** （適用於 Adobe Commerce 與 Magento Open Source 2.4.6-p8）- 還原 2.4.6-p8 中包含的不相容後置順序變更。
* **ACSD-60267** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正當直接將具有FPT的簡單產品新增至購物車時，修正修正產品稅(FPT)正確套用的問題，但在透過可設定產品選項選取這些產品時失敗。
* **ACSD-61103** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正客戶透過API端點成功登入後，`customer_entity`表格中的失敗計數未重設為零的問題。
* **ACSD-61134** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正當購物者取消選取「[!DNL Braintree Vault]」核取方塊以更新其帳單地址時，結帳工作流程中會自動取消選取「*[!UICONTROL My billing and shipping address are the same]*」付款方式的問題。
* **ACSD-61199** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正CMS頁面階層索引標籤在編輯具有現有階層的CMS頁面時未顯示正確樹狀結構的問題。
* **ACSD-61200** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正銷售中&#x200B;*[!UICONTROL Total Amount]*&#x200B;和&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;的計算遺失&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*，而造成銷售訂單資料不一致的問題。
* **ACSD-61522** （用於 Adobe Commerce 和 Magento 開源 >=2.4.4 &lt;2.4.8) - Fixes the issue where it is possible to enter email addresses into the guest customer&#39;s *[!UICONTROL First Name]* ，以及 *[!UICONTROL Last Name]* 欄位，發送無效訂單確認郵件。
* **ACSD-61756** （用於 Adobe Commerce >=2.4.4 &lt;2.4.7) - Improves performance of `AdvancedSalesRule` 濾波器。
* **ACSD-61799** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.5) - Fixes the issue where the total discount is incorrectly calculated when multiple cart rules with fixed discounts are applied to the quote.
* **ACSD-61845** （用於 Adobe Commerce 與 Magento 開源 >=2.4.7-p1 &lt;2.4.8) - Fixes the error that occurs when a request is sent with only *文字/html* 接受標頭。
* **ACSD-62056** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.8) - Fixes the issue where image uploading for a configurable product fails if MSI is installed.
* **ACSD-62485** （用於 Adobe Commerce >=2.4.4 &lt;2.4.6-p8 ||=&quot;&quot;>=2.4.7 &lt;2.4.8) - Fixes the issue where `async.operations.all` ，消費者在公司成立時停止運作。&lt;/2.4.6-p8>
* 更新版本： **ACSD-48661**、 **ACSD-55100**、 **ACSD-61553**
* 已棄用補丁： **ACSD-51846**

## v1.1.53 {#v1-1-53}

* **ACSD-48318** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.7) - Fixes the issue where environment emulation nesting is not allowed. 現在，模擬會在通話中停止`send()`後開始`getInfoBlockHtml()`。
* **ACSD-59930** (適用於Adobe Commerce >=2.4.6 &lt;2.4.8) — 改善公司的&#x200B;**[!UICONTROL Create]**、**[!UICONTROL Save]**&#x200B;和&#x200B;**[!UICONTROL Delete]**&#x200B;流程的效能。
* **ACSD-60584** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正允許在一個網站上為使用者建立的存取權杖存取或變更其他網站上的客戶資訊的問題。
* **ACSD-60804** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正編輯連結至已刪除公司的客戶會在null *上造成錯誤`getSuperUserId()`呼叫成員函式*&#x200B;的問題。
* **ACSD-61133** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.8) — 修正`sales_clean_quotes` [!DNL cron]從未核准的採購單中刪除報價的問題。
* **ACSD-61528** (適用於Adobe Commerce >=2.4.6 &lt;2.4.8) — 修正使用[!UICONTROL Admin]從[!DNL GraphQL]擷取角色時未傳回任何結果的問題。
* **ACSD-61553** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正將不同優先順序的多重折扣和&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;套用至產品時，**[!UICONTROL Maximum Qty Discount is Applied To]**&#x200B;折扣計算錯誤的問題。
* **ACSD-61667** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 改善存貨效能，以建立多份店內取貨來源的送貨方式。
* **ACSD-61969** (適用於Adobe Commerce >=2.4.7 &lt;2.4.8) — 修正使用者必須輸入區分大小寫的優惠券代碼，才能與優惠券代碼設定完全相符的問題。
* 已更新的版本： **ACSD-54989**，**ACSD-60632**

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** (適用於Adobe Commerce和Magento Open Source) — 新增所有必要欄位，以使用[!DNL Braintree]作為付款閘道時滿足3DS VISA授權需求。
* **ACSD-59366** (適用於Adobe Commerce >=2.4.6 &lt;2.4.8) — 修正嘗試刪除團隊時發生錯誤，而該團隊包含未在團隊清單中顯示的已停用使用者的問題。
* **ACSD-59865** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正購物車中的產品數量不足以套用規則時，[!UICONTROL Cart Price Rule]無法取消先前套用規則的問題。
* **ACSD-59925** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正GraphQL中依位置排序[!UICONTROL Media Gallery]專案的問題。
* **ACSD-59952** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正使用指派給現有[!UICONTROL Shared Catalog]的群組識別碼建立[!UICONTROL Shared Catalog]時發生錯誤的問題。
* **ACSD-60590** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 改善為大量下單訂單產生[!UICONTROL Bestsellers Aggregated Daily Reports]的效能。
* **ACSD-60673** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正結帳時多種付款方式的[!UICONTROL Cart Price Rule]未正確套用至特定付款方式的問題。
* **ACSD-60684** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正按多個欄位排序的GraphQL產品無法如預期運作的問題。
* **ACSD-60788** (適用於Adobe Commerce >=2.4.7 &lt;2.4.8) — 修正由於內容安全性原則(CSP)錯誤而無法執行[!DNL Google Tag Manager]的自訂指令碼的問題。
* **ACSD-61322** (適用於Adobe Commerce >=2.4.6 &lt;2.4.8) — 修正XML Sitemap中仍包含[!UICONTROL Products/Categories]未指派給預設值（一般群組）的[!UICONTROL Shared Catalog]的問題。
* **ACSD-61366** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正為DB連線指定連線埠時，必須在主機引數`setup:static-content:deploy --jobs 4`錯誤中設定&#x200B;*連線埠時，在多個工作失敗的情況下執行*&#x200B;命令的問題。
* 更新修補程式：ACSD-51857、ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.8) — 修正GraphQL在嘗試取得過期報價的報價識別碼時，傳回內部伺服器錯誤的問題。
* **ACSD-60234** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正當付款方式套用折扣時，[!DNL PayPal]上顯示不正確金額的問題。
* **ACSD-59967** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7-p2) — 修正JavaScript錯誤導致[!DNL Google Maps]無法正確呈現的問題。
* **ACSD-60326** (適用於Adobe Commerce >=2.4.4 &lt;2.4.8) — 修正GraphQL查詢客戶回訪狀態發生錯誤的問題。
* **ACSD-60538** (適用於Adobe Commerce >=2.4.7 &lt;2.4.8) — 修正產品在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中停用，且只在特定商店檢視範圍中啟用的情況下，產品屬性在GraphQL回應中無法正確顯示，導致產品無法正確顯示的問題。
* **ACSD-60631** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正將相同的簡單產品指派給多個可設定產品時，GraphQL傳回錯誤的問題。
* **ACSD-60632** (適用於Adobe Commerce和Magento Open Source >=2.4.5-p8 &lt;2.4.8) — 修正每次嘗試下訂單時儲存新位址的問題，無論是否成功建立訂單。
* **ACSD-60816** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正APM代理程式插入的[!DNL New Relic Browser Monitoring]指令碼不符合CSP （內容安全性原則）的問題，使其無法執行。
* **ACSD-61195** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正購物車GraphQL請求的最後一頁未傳回購物車專案的問題。
* 更新修補程式：ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正安裝2.4.4-pX版本時發生的錯誤&#x200B;*呼叫ReflectionUnionType：：getName()*。
* **ACSD-45049** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.4-p8) || >=2.4.5 &lt;2.4.6) — 修正客戶&#x200B;*[!UICONTROL Is required]*&#x200B;屬性設定無法按照「管理員」中的網站範圍正確運作的問題。
* **ACSD-46938** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正`setup:upgrade`期間重新建立DB觸發器的效能問題。
* **ACSD-48210** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正更新特定存放區檢視中的&#x200B;*[!UICONTROL Website Scope]*&#x200B;屬性會覆寫全域範圍中屬性值的問題。
* **ACSD-54887** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9) || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) — 修正客戶工作階段過期（啟用[!UICONTROL Persistent Shopping Cart]）後客戶購物車被清除的問題。
* **ACSD-58141** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正PHPSESSID在登入客戶的店面區域重新產生POST要求的問題（如果[!DNL L2 Redis cache]已啟用，且客戶已從管理員更新）。
* **ACSD-58352** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 修正要求標頭中指定非預設存放區檢視時，透過GraphQL API傳回預設存放區檢視之傳回屬性標籤的問題。
* **ACSD-58442** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7-p1) — 修正將寬度為768px的裝置視為行動裝置的問題，其導致功能表和標題載入行動檢視而非桌上型電腦。
* **ACSD-58790** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.8) — 修正[!DNL Chrome]上行動檢視中產品詳細資料頁面影像的夾點至縮放功能。
* **ACSD-59036** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正載入上下限均等於$0的產品價格時發生例外狀況。
* **ACSD-59229** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正客戶群組相關資訊因X-Magento-Vary在請求中的舊值而儲存在錯誤區段的問題。
* **ACSD-59378** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正匯入期間未正確更新存放區層級URL重寫的問題。
* **ACSD-59514** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7-p2) — 修正具有[!DNL Page Builder]之管理區域中的表單擲回錯誤&#x200B;*[!DNL Page Builder]持續呈現5秒而未解除鎖定的問題。在瀏覽器主控台中提交表單後*，變更無法儲存。
* **ACSD-60303** (適用於Adobe Commerce >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) — 修正啟用HTML縮制時，無法發出管理員訂單的問題。
* **ACSD-60441** (適用於Adobe Commerce和Magento Open Source 2.4.4-p9) || 2.4.5 - p8 || 2.4.6 - p6 || 2.4.7-p1) — 修正使用後端產生的整合存取權杖時，透過`V1/customers` [!DNL REST API]端點更新客戶的問題。
* 更新修補程式：ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正刪除中繼更新後移除產品影像的問題。
* **ACSD-57086** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正來自啟用條款與條件之非預設網站的訂單未正確處理的問題。
* **ACSD-57588** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正將訂單運送至多個地址會在地區ID處理期間觸發錯誤的問題。
* **ACSD-57643** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正透過GraphQL將具有自訂選項的產品錯誤新增到購物車的問題。
* **ACSD-57846** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正GraphQL產品以零價格篩選條件搜尋時，由於發生例外狀況，無法傳回任何結果的問題。
* **ACSD-57941** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正產品選項未正確指派給管理員存放區（而非其個別存放區）的問題。
* **ACSD-58375** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正當在商店檢視層級新增&#x200B;*[!DNL YouTube API Key]*&#x200B;視訊時，錯誤的[!DNL YouTube]設定會導致錯誤的問題。
* **ACSD-58739** (適用於Adobe Commerce和Magento Open Source >=2.4.7 &lt;2.4.8) — 修正部分重新索引擲回錯誤的問題。
* **ACSD-58446** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正刪除具有子使用者或團隊的團隊時，不論其狀態為何（非作用中），系統都會提供與UI不一致的錯誤訊息，且無法提供相關資訊的問題。
* **ACSD-58054** (適用於Adobe Commerce >=2.4.4 &lt;2.4.6) — 修正可能透過API為非作用中客戶產生客戶權杖的問題。
* **ACSD-58163** (適用於Adobe Commerce >=2.4.3 &lt;2.4.7) — 修正&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;不從相符的&#x200B;*[!UICONTROL Customer Segment]*&#x200B;購物車（不含優惠券代碼）為訪客客戶套用折扣的問題。
* **ACSD-57045** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正URL重新寫入導致從&#x200B;*[!UICONTROL Website Root]*&#x200B;取消勾選&#x200B;*[!UICONTROL Hierarchy]*&#x200B;後出現無限頁面回圈的問題。
* 更新修補程式：ACSD-46815、ACSD-47027、ACSD-51683、ACSD-55031、ACSD-51819、ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正當合併具有相同組合專案的來源和目的地購物車時，`mergeCart`回應中的&#x200B;*變異失敗並出現「*&#x200B;內部伺服器錯誤[!DNL GraphQL]」的問題。
* **ACSD-56546** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正當&#x200B;**顯示無產品組態**&#x200B;為&#x200B;**已停用**&#x200B;時，可設定和套件產品在店面顯示為&#x200B;*無庫存*&#x200B;的問題。
* **ACSD-56635** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正當匯入用於&#x200B;**帳戶共用**&#x200B;設定為&#x200B;*全域*&#x200B;時，匯入的客戶會以相同的電子郵件地址重複的問題。
* **ACSD-56741** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正當資料庫包含與索引機制和&#x200B;*無關的自訂*&#x200B;觸發程式時，在`setup:upgrade`期間顯示的錯誤訊息「[!DNL MySQL]嘗試存取型別null[!DNL MView]的值上的陣列位移」。
* **ACSD-57315** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正每次在Admin的[!DNL PayPal Payflow Pro]畫面上按一下[!UICONTROL Fetch]按鈕時，**[!UICONTROL View transaction]**&#x200B;中建立新交易的問題。
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
* **ACSD-57074** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正以&#x200B;*開頭的*&#x200B;的`attrbute_code`是/否`price_`自訂屬性無法正確搭配索引運作，以及前端無法使用具有這類屬性的產品的問題。
* 更新修補程式：ACSD-53378、ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正庫存數量變更時，即使產品仍有庫存，類別頁面快取無效的問題。
* **ACSD-54656** (適用於Adobe Commerce >=2.4.5 &lt;2.4.6) — 修正隱藏的Recaptcha在結帳期間失敗，導致無法下訂單的問題。
* **ACSD-55100** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正GraphQL在搜尋結果中未傳回超過10,000項產品的問題。
* **ACSD-56621** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正公司管理員使用者的問候語標題區段中未反映更新後名字和姓氏的問題。
* **ACSD-56842** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正執行`setup:di:compile`後遺失延遲代理程式和延遲代理程式工廠的問題。
* **ACSD-57003** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正部分退款及部分運送訂單時，訂單狀態變更為&#x200B;*[!UICONTROL Complete]*&#x200B;而非變更為&#x200B;*[!UICONTROL Processing]*&#x200B;的問題。
* 更新修補程式：ACSD-50260-v2、ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正排程更新停用其中一項子產品時，可設定產品無存貨的問題。
* **ACSD-56616** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正當簡易產品無庫存時，店面捆綁產品顯示為庫存的問題。
* **ACSD-56515** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正具有網站層級許可權的管理員無法新增或編輯動態區塊的問題。
* **ACSD-56447** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正透過平行REST Web API請求將相同產品新增到購物車導致購物車中有兩個單獨專案的問題。
* **ACSD-56415** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正當資料庫有許多要編制索引的區域性價格資料時，由於`DELETE`查詢，部分價格索引的效能變慢的問題。
* **ACSD-54965** (適用於Adobe Commerce >=2.4.5 &lt;2.4.6) — 修正當產品僅指派給自訂庫存時，視覺銷售格線無法顯示正確庫存的問題。
* **ACSD-52824** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正當公司設定中停用PayPal Express、Google Pay及Apple Pay按鈕時，公司客戶會顯示此類付款方式的問題。
* 更新修補程式：ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正使用「**從庫存移至底部**」選項排序類別產品時，系統會將使用者重新導向至管理員控制面板的問題，且`Invalid security or form key. Please refresh the page`錯誤會顯示在畫面頂端。
* **ACSD-56280** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 修正從禮品登入訂購專案會導致例外狀況的問題。
* **ACSD-56246** （用於 Adobe Commerce 與 Magento 開源 >=2.4.6 &lt;2.4.7) - Fixes the issue where data is removed from the custom multi-select attribute when a scheduled update for a product becomes active.
* **ACSD-56193** （用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.4) - Fixes the issue where the Varnish/Fastly cache is not updated when a scheduled block is used in the category description using Page Builder.
* **ACSD-56158** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正「購物車」查詢傳回每個稅捐規則的總稅捐值的問題。
* **ACSD-56023** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正當啟用快取時，CMS頁面上的Widget內容未更新的問題。
* **ACSD-55427** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正管理員使用者無法從管理員的產品頁面取消指派共用目錄中的產品的問題。
* **ACSD-55352** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正使用客戶獎勵點數建立部分銷退折讓單後，訂單狀態變更為「已結」且銷退折讓單選項從「管理員訂單」頁面消失的問題。
* **ACSD-55231** （用於 Adobe Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where you cannot add products to a cart using the quick order functionality.
* **ACSD-54283** （用於 Adobe Commerce >=2.4.3 &lt;2.4.4) - Fixes the issue where Products/Categories not assigned to the Shared Catalog for the Default (General Group) are still included in the XML Sitemap.
* 更新補丁：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** （用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.7) - Fixes the issue where the canonical category URL doesn&#39;t update after changing the category URL.
* **ACSD-53636** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt;2.4.5) - Fixes the issue where the regular price is not displayed on product listing pages for configurable products that have child products with special prices.
* **ACSD-54885** （用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.7) - Fixes the issue with the multiple address checkout when the admin user is using the *以客戶* 身份登入功能。
* **ACSD-55610** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.7) - Fixes the issue where a partially canceled order has an incorrect discount amount.
* **ACSD-55334** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt;2.4.7) - Fixes translations for labels through Translation dictionaries in GraphQL response.
* **ACSD-54739** （用於 Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the product stock status condition is not applied for related product rules.
* **ACSD-53925** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正當`catalog_product_price` dimensions-mode設為&#x200B;*網站*&#x200B;時，管理員無法將CMS區塊與產品輪播儲存的問題。
* **ACSD-52714** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正日期格式設為&#x200B;*Y-m-d*&#x200B;時，日期篩選器在管理格線中無法運作的問題。
* **ACSD-55055** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 改善在購物車的購物車價格規則中載入產品屬性的效能。
* **ACSD-53790** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正可透過REST API為單一產品建立多個RMA的問題。
* **ACSD-56090** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5) — 修正GraphQL要求回應所有存放區資料（而非特別要求的存放區資料）的問題。
* **ACSD-54983** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正當使用者狀態設為&#x200B;*[!UICONTROL Inactive]*&#x200B;時，無法使用GraphQL要求取得公司使用者UID的問題。
* **ACSD-53309** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正當選取可自訂選項時，*[!UICONTROL Regular Price]*&#x200B;標籤中未完全套用稅金的問題。
* **ACSD-55305** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 修正&#x200B;*[!UICONTROL Edit Company User]* > **[!UICONTROL myAccount]**&#x200B;頁面上的&#x200B;**[!UICONTROL Company Structure]**&#x200B;快顯視窗因熒幕上的載入器而凍結的問題。
* 更新修補程式：ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正商店檢視中&#x200B;*[!UICONTROL Recently Viewed]*&#x200B;產品資料未正確更新的問題。
* **ACSD-54626** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正您無法透過`createPurchaseOrderApprovalRule`建立具有`NUMBER_OF_SKUS`屬性的新採購單規則([!DNL GraphQL])的問題。
* **ACSD-53845** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正[!DNL MySQL] = 0時的`consumer max_messages`連線逾時問題。
* **ACSD-54890** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正`aggregate_sales_report_bestsellers_data`由於[!DNL MySQL]磁碟空間不足而導致`/tmp`錯誤的問題。
* **ACSD-55112** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正可多次點選「*[!UICONTROL Submit review]*」按鈕而無需[!DNL Google reCAPTCHA v3]驗證的問題。
* **ACSD-54264** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) — 修正錯誤訊息&#x200B;*「您無法更新要求的屬性」的問題。 資料列識別碼： store_id&quot;*&#x200B;會在客戶嘗試從其他商店檢視中取出可轉讓的報價時出現。
* **ACSD-54418** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正動態定價套件組合的每個子產品不正確套用固定金額折扣的問題。
* **ACSD-55238** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正儲存空白產品&#x200B;*[!UICONTROL Meta Description]*。
* **ACSD-54966** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正先前訂單失敗時，無法重複使用每位客戶限量使用之優惠券代碼的問題。
* **ACSD-54060** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正受限管理員無法儲存產品（如果產品是指派給其他範圍之其他產品的子產品）的問題。
* **ACSD-48910** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正訂單開立商業發票及出貨後，即使訂單數量仍非零，指派給多個來源的套件產品也會無存貨的問題。
* **ACSD-55381** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正透過`configurable_product_option_uid`從`configurable_product_option_value_uid` [!DNL B2B]查詢&#x200B;*[!UICONTROL Requisition list]*&#x200B;及[!DNL GraphQL]欄位時的內部伺服器錯誤。
* **ACSD-55628** (適用於Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) — 修正了在公司登錄檔單上傳檔案和取代店面中客戶屬性的檔案。
* 更新修補程式：ACSD-51240、ACSD-51890、ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正將產品加入購物車後，從共用目錄移除產品時購物車中發生的問題。
* **ACSD-53722** (適用於Adobe Commerce >=2.4.4 &lt;2.4.7) — 修正當不同範圍的排程更新生效時，隨附的產品選項價格變更為$0的問題。
* **ACSD-53643** (適用於Adobe Commerce >=2.4.3 &lt;2.4.7) — 修正訂購停用或無存貨的產品時，訂單總計有誤的問題。 已透過隱藏此類採購單的&#x200B;*[!UICONTROL Place Order]*&#x200B;按鈕來修正。
* **ACSD-54067** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正產品影片無法在行動裝置上播放的問題。
* **ACSD-55414** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 改善MariaDB嘗試將EAV entity_id從字串轉換為整數時的效能。
* **ACSD-51819** (適用於Adobe Commerce >=2.4.4 &lt;2.4.4-p4) — 修正可使用相同報價識別碼下多份訂單的問題。
* **ACSD-53118** (適用於Adobe Commerce >=2.4.0 &lt;2.4.7) — 修正當產品具有空白屬性時，使用優惠券代碼套用&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;的問題，此問題應已導致規則失效。
* **ACSD-54324** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正GraphQL requisition_lists要求未考慮分頁設定並傳回所有結果的問題。
* 更新修補程式：MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (適用於Adobe Commerce >=2.4.0 &lt;2.4.6) — 修正無法處理針對具有多個指派來源的產品所提交的B2B報價的問題。
* **ACSD-54040** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6) — 修正啟用B2B模組時，*[!UICONTROL Created]*&#x200B;欄位空白的問題，以取得詳細資訊。
* **ACSD-54319** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正&#x200B;*[!UICONTROL Product in Cart]*&#x200B;報表中產品價格為零的問題。
* **ACSD-53378** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 為擁有大型通訊錄的客戶改善結帳頁面載入時間。
* **ACSD-52657** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正使用子網域的次要商店未更新minicart的問題。
* **ACSD-53414** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正受限管理員使用者可在其許可權範圍以外看到CMS頁面的問題。
* **ACSD-54472** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正被拒絕公司的客戶仍可驗證，以及被封鎖和被拒絕公司的客戶仍可下訂單的問題。 此修補程式新增了GraphQL端點的額外驗證。
* **ACSD-52801** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 新增在GraphQL中搜尋產品時進行部分比對的選項。
* **ACSD-55004** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正上傳大於`php.ini`中設定值的匯入檔案時，驗證器當機的問題。
* **ACSD-54989** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) — 修正當&#x200B;*[!UICONTROL Enable Purchase Orders]*&#x200B;設為&#x200B;*[!UICONTROL Yes]*&#x200B;且&#x200B;*[!UICONTROL Purchase Order]*&#x200B;設為&#x200B;*[!UICONTROL No]*&#x200B;時，公司管理員無法下訂單的問題。
* **ACSD-54007** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正匯入客戶資料時的錯誤&#x200B;*「未定義的陣列機碼&quot;_scope&quot;*。
* **ACSD-55031** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正&#x200B;*型別「混合」在編譯期間不可為nullable*&#x200B;錯誤。
* **ACSD-54961** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正受限管理員使用者無法大量更新&#x200B;*產品評論*&#x200B;狀態的問題。
* **ACSD-55256** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正影像滑桿中僅成功顯示第一個影像的問題。
* 更新修補程式：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (適用於Adobe Commerce >=2.4.0 &lt;2.4.7) — 修正獎勵點到期後獎勵點餘額歷史記錄計算錯誤的問題。
* **ACSD-53583** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 改善&#x200B;*類別產品*&#x200B;和&#x200B;*產品類別*&#x200B;索引器的部分重新索引效能。
* **ACSD-54026** (適用於Adobe Commerce >=2.4.6 &lt;2.4.7) — 修正非授權使用者`updateCompanyRole` GraphQL請求的不正確錯誤訊息。
* **ACSD-54106** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5) — 修正土耳其文重音字元依名稱排序的類別產品錯誤問題。
* **ACSD-52219** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正經常在書籤檢視之間切換時，管理員格線儲存的篩選器無法如預期運作的問題。
* **ACSD-54342** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正不正確的錯誤訊息&#x200B;*資料結構中的錯誤：匯入沒有有效資料的CSV檔案時，會混合值*。
* **ACSD-54660** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 已新增輸入屬性&#x200B;*sort*，以便在GraphQL中依`sort_field`和`sort_direction`排序客戶訂單。
* **ACSD-54776** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正未核取的&#x200B;*[!UICONTROL Use Default Value]*&#x200B;及非預設產品欄位值未儲存至第二個網站、商店及商店檢視的問題。
* **ACSD-53998** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p2 &lt;2.4.5) || >=2.4.5-p1 &lt;2.4.7) — 修正從客戶帳戶登出後，以&#x200B;**[!UICONTROL Dynamic Block]**&#x200B;為基礎的&#x200B;**[!UICONTROL Customer Segment]**&#x200B;無法正常運作的問題。
* **ACSD-53204** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正&#x200B;*無法儲存產品。使用*&#x200B;端點同時要求將影像新增至產品相簿時發生`rest/V1/products/<sku>/media`錯誤。
* **ACSD-47657** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 已新增AWS憑證的快取機制。 認證提供者現在會使用Magento快取來快取從AWS擷取的認證，以進行EC2設定。
* 更新修補程式：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4) — 修正執行部分索引時，指派給共用目錄的產品未出現在店面的問題。
* **ACSD-54018** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正Widget條件中使用非全域屬性的[!UICONTROL Product List]介面工具集的效能問題。
* **ACSD-54111** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正當浮水印影像的外觀比例不符合產品影像時，店面未顯示產品縮圖影像的問題。
* **ACSD-47669** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正&#x200B;*完整性條件約束違規： 1452無法新增或更新子列：匯入產品CSV時，外部索引鍵條件約束失敗*&#x200B;錯誤。
* **ACSD-53347** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正價格索引器耗費太多時間執行的問題。
* **ACSD-52287** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正啟用非同步格線索引時，封存的訂單格線中順序狀態不正確的問題。
* **ACSD-52929** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正當庫存索引器設定為非同步模式時，重新索引預設來源專案的多餘請求問題。
* **ACSD-53824** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正`UpdateMultiselectAttributesBackendTypes`期間`setup:upgrade`移轉資料修補程式超過資料庫交易大小限制的問題。

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正即使未透過REST API更新`Inventory_source`專案，快取和索引也會重新整理的問題。
* **ACSD-51884** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正執行調整大小命令後，產品影像快取路徑不正確的問題。
* **ACSD-53628** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正CSV銷售訂單報告顯示不正確的特殊字元的問題。
* **ACSD-53148** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正GraphQL中新增相同可設定產品至購物車的兩個平行請求，在購物車上會產生兩個具有相同產品SKU的個別專案的問題。
* **ACSD-52606** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正使用者按一下&#x200B;*時，顯示錯誤訊息*&#x200B;您的訂單未準備好取貨&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;的問題。
* **ACSD-51574** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正將影像取代為具有相同名稱的另一個影像後，影像沒有在前端更新的問題。
* **ACSD-53728** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正產品EAV索引器需要更長時間才能完成的問題。
* **ACSD-53979** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正如果歡迎訊息包含單引號，首頁上發生的JS問題。
* **ACSD-52085** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正產品輪播中看不到具有特殊價格的可設定產品的問題。
* **ACSD-53795** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正`indexer_update_all_views` cron工作中資料型別無效的問題。
* **ACSD-52143** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正產品匯入後移除自訂選項的問題。
* **ACSD-53750** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正多重執行緒&#x200B;*重新索引期間的*&#x200B;中斷管道或關閉的連線`catalog_product_price`錯誤。
* **ACSD-49843** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.7) — 修正啟用&#x200B;**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**&#x200B;設定之線上付款方式自動開立訂購專案的發票後，無法使用產品下載連結的問題。
* **ACSD-47054** (適用於Adobe Commerce >=2.4.2 &lt;2.4.6) — 修正預覽重新索引為所有存放區執行重新索引，導致速度緩慢的問題。
* 已新增ACSD-46541、ACSD-47079的新版本。
* ACSD-49970-v3 被 ACSD-54095 取代。

## v1.1.36 {#v1-1-36}

* **ACSD-53239** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt; 2.4.6) - Fixes the issue where the inventory indexer cleans all caches in the Update on Schedule mode.
* **ACSD-50887**（適用於 Adobe Commerce 和 Magento Open Source >=2.4.0 *[!UICONTROL Use in Search Results Layered Navigation]*&lt;2.4.7) - Fixes the issue where the product attribute property ）可以設定為&#x200B;*「是*」，但不必設定&#x200B;*[!UICONTROL Use in search]*&#x200B;為&#x200B;*「是*」。
* **ACSD-51846** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3-p2 &lt;2.4.6) - Fixes the *內部錯誤* 問題，因為並非所有層級的 REST API 有效載荷都被驗證。
* **ACSD-52906** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正屬於相同客戶區段的登入客戶若未正確設定X-Magento-Vary Cookie，會導致某些頁面快取不當的問題。
* **ACSD-52736** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正包含可設定產品數量需求的&#x200B;*購物車價格規則*&#x200B;無法如預期運作的問題。
* **ACSD-47875** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正管理員使用者無法針對具有詳細目錄管理的特定商店檢視範圍，從管理員將產品新增到客戶購物車的問題。
* **ACSD-53176** (適用於Adobe Commerce >=2.3.7 &lt;2.4.5) — 修正&#x200B;*具有*&#x200B;的「相關產品規則」*為*&#x200B;條件之一的某一項不符合產品的問題。
* **ACSD-51666** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正錯誤&#x200B;*工作階段已過期，請重新登入。在客戶嘗試登入後發生的*。
* 新增 MDVA-39305-v2 版本。
* ACSD-19640 的最新需求。

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正結帳送貨步驟上的預設送貨地址自動填入先前選取的店內取貨地址的問題。
* **ACSD-52041** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正錯誤訊息： *[錯誤] [!DNL Page Builder]呈現5秒而未解除鎖定的問題。儲存使用*&#x200B;編輯的內容時，[!DNL Page Builder]會出現在Chrome瀏覽器中。
* **ACSD-52095** （針對 Adobe Commerce 和 Magento 開源>=2.3.7 &lt;2.4.6) - Fixes the issue where the `manage_stock` 在產品匯出後的 CSV 檔案中錯誤設為 0。
* **ACSD-51358** （用於 Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where removing a scheduled update without an end date leads to removing other scheduled updates for the same entity.
* **ACSD-48070** （用於 Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where editing a scheduled update triggers an exception.
* **ACSD-51890** （適用於 Adobe Commerce 和 Magento 開源 >=2.4.0 &lt;2.4.7) - Fixes the issue where the [!UICONTROL Submit review] 按鈕可在不 [!DNL Google reCAPTCHA] 驗證 v3 的情況下多次點擊。
* **ACSD-51984** （用於 Adobe 商務 >=2.4.5 &lt;2.4.7) - Fixes the issue where unchecked *[!UICONTROL Use Default Value]* ，且 *[!UICONTROL non-default product field]* 不儲存第二個網站、商店及商店檢視的值。
* **ACSD-52398** （適用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.7) - Fixes the error *在嘗試更新商店購物車中捆綁商品數量時，請求的數量無法取得* 。
* **ACSD-52786** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正目錄規則條件&#x200B;*SKU為*&#x200B;的問題，適用於從指定SKU開始的所有產品。
* **ACSD-52921** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正當購物車有無存貨的可設定產品時，若向GraphQL要求購物車詳細資料會發生內部錯誤的問題。
* **ACSD-51683** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正無法使用GraphQL將可自訂選項新增到購物車的問題。
* **ACSD-52133** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正升級後無法儲存客戶帳戶的問題。
* **ACSD-52202** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正訂單履行時，非預設存貨變更為0數量時，預設存貨的可銷售數量錯誤地變更為0的問題。
* **ACSD-51265** （用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.7) - Fixes the issue with `catalog_product_price` 當系統中捆綁產品過多時的重新索引效能。
* **ACSD-52831** （用於 Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where customers cannot place negotiable quote orders when [!DNL Google reCAPTCHA v3 Invisible] ）已啟用。
* **ACSD-51845** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.7) - Fixes the issue where subsequent products with tier prices and different attribute sets cannot be updated via asynchronous bulk REST API.
* **ACSD-52815** （用於 Adobe Commerce 與 Magento 開源 >=2.3.7 &lt;2.4.7) - Fixes the issue where the input for the quantity field of a non-default source supports only up to 6 digits, unlike 8 for a default stock.
* **ACSD-51149** （用於 Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where Scheduled ImportExport with enabled Catalog Permissions invalidates indexers and then cache flushes by cron.
* **ACSD-50815** （用於 Adobe Commerce 與 Magento 開源 >=2.4.5 &lt;2.4.6) - Fixes the issue where decimal quantity for a simple product cannot be used for a new Bundled product option.
* ACSD-47803 的更新版本。
* ACSD-51892 更新標題。
* 更新為 ACSD-51379。
* 更新為 ACSD-49970-v2。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** （用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.7) - Fixes the issue where an admin user is not redirected properly after selecting a store view when creating a new order in Admin.
* **ACSD-50813** （用於 Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where Admin was not able to add bundled products containing a slash in the SKU with the [!UICONTROL Add Products by SKU] 功能於管理員訂單中。
* **ACSD-51630** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt;2.4.7) - Fixes the issue where a large amount of system messages slows the downloading of admin pages.
* **ACSD-51853** （用於 Adobe Commerce 與 Magento 開源 >=2.4.1 &lt;2.4.7) - Fixes the issue where copied text styles are not applied when using the [!UICONTROL Page Builder]。
* **ACSD-52160** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.7) - Fixes the issue where the product validation result against the cart price rule was not properly evaluated based on the rule condition &#39;If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true&#39;.
* **ACSD-51636** （用於 Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the company admin cannot add new users from the customer account section despite having all necessary roles and permissions.
* **ACSD-51739** （用於 Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where an error is returned when the `structure_id` ）會在 CompanyTeam GraphQL 請求中被請求。
* **ACSD-51857** （用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.7) - Fixes the issue where the slow performance of the `aggregate_sales_report_bestsellers_data` cron報告，涉及大型sales_order與 `sales_order_item` 資料庫資料表，是因為主要資料查詢的撰寫方式所致。
* **ACSD-48448** （用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.7) - Fixes the issue where there is a race condition issue happening during the order cancellations, which causes a duplicated entry in the `inventory_reservation` 表格。
* **ACSD-52689** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt;2.4.6) - Fixes the issue where images cannot be uploaded to Amazon S3 storage using REST API.
* **B2B-2674** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.7) - Add caching capability to the 1customAttributeMetadata1 GraphQL query.
* 新增 ACSD-44938 版本。
* 新增ACSD-46988的需求。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5) — 修正資料庫傾印包含觸發程式和&#x200B;*分隔符號* SQL命令時的資料庫復原命令。
* **ACSD-50512** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正&#x200B;*錯誤：可下載的連結與產品無關。 請驗證連結，然後再試一次。更新可下載產品臨時更新的開始日期時發生*&#x200B;個錯誤。
* **ACSD-50949** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正進階搜尋中的價格篩選器在搭配SKU篩選器使用時未傳回正確結果的問題。
* **ACSD-51645** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正擴充功能`Magento_OfflineShipping`停用時，儲存新購物車價格規則時擲回的錯誤。
* **ACSD-50895** (適用於Adobe Commerce >=2.4.5 &lt;2.4.7) — 修正未設定[!DNL Google Analytics] 4 GTM時無法引發[!DNL Google Analytics] 3 GTM標籤的問題。
* **ACSD-51102** (適用於Adobe Commerce >=2.4.2 &lt;2.4.7) — 修正排程更新啟用規則時，套用至大量產品的目錄規則未正確編制索引的問題。
* **ACSD-50368** (適用於Adobe Commerce和Magento Open Source >= 2.4.3 &lt;2.4.5) — 修正透過Async REST API或Async Bulk REST API建立客戶時，客戶的`group_id`遭忽略的問題。
* **ACSD-51497** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) — 修正客戶無法依下拉式清單型別的自訂屬性排序目錄頁面的問題。
* **ACSD-51408** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt; 2.4.7) — 修正訂單專案狀態錯誤設定為&#x200B;*[!UICONTROL Backordered]*&#x200B;的問題。
* **ACSD-51735** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正產品庫存為&#x200B;*[!UICONTROL Ordered]* 0 *時，訂單專案狀態未正確設定為*&#x200B;的問題。
* **ACSD-51792** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正啟用[!DNL Google Tag Manager] 4時頁面沒有曝光事件的問題。
* **ACSD-51471** (適用於Adobe Commerce >=2.4.3 &lt;2.4.7) — 修正管理員使用者無法針對使用簡單產品（本身已有排程更新）的套件產品儲存排程更新的問題。
* **ACSD-51700** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正在Admin的可下載產品編輯頁面上切換商店檢視時發生的錯誤。
* **ACSD-51120** (適用於Adobe Commerce >=2.3.7 &lt;2.4.3) — 修正包含透過中繼更新更新的GraphQL區塊的GET頁面未清除CMSCMS請求快取的問題。
* **ACSD-51240** (適用於Adobe Commerce >=2.4.4 &lt;2.4.6) — 修正透過公司登錄檔格進行註冊時，所上傳檔案遺失的問題。
* **ACSD-51907** (適用於Adobe Commerce >=2.4.2 &lt;2.4.3) — 修正受限管理員使用者無法以離線退款建立銷退折讓單的問題。
* **ACSD-52148** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正[!DNL Google V3 reCAPTCHA]管理員登入偶爾失敗的問題。
* **ACSD-51431** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正即使變更記錄檔中沒有新專案，索引子狀態為&#x200B;*正在運作*&#x200B;的問題。
* **ACSD-51892** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正設定檔案載入多次的效能問題。
* 已棄用ACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正[!UICONTROL Page Builder's]多個錯誤導致管理員無法儲存沒有內容許可權的產品的問題。
* **ACSD-51305** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正GraphQL回應中無法使用無庫存可設定子產品的問題。
* **ACSD-50621** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正嘗試在多網站環境中編輯共用目錄中不同網站的[!UICONTROL Tier Prices]時，無法顯示的問題。
* **ACSD-51041** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.6) — 改善價格索引器的效能。
* **ACSD-51379** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正無法透過[!UICONTROL Page Builder]儲存頁面文字內容變更的問題。
* **ACSD-49480** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正僅將一個購物車價格規則套用至購物車的問題。
* **ACSD-51230** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正處理訂單中簡單產品的部分退款時，禮品卡帳戶遭到刪除的問題。
* **ACSD-51238** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修正更新可設定產品及編輯價格時移除庫存來源的問題。
* **ACSD-50794** (適用於Adobe Commerce >=2.4.1 &lt;2.4.7) — 修正透過GraphQL移除禮品訊息或禮品包裝時，資料庫中未更新禮品訊息或禮品包裝詳細資料的問題。
* **ACSD-51528** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正&#x200B;*sales_order*&#x200B;表格中&#x200B;*x_forwarded_for*&#x200B;欄含有null值的問題。
* **ACSD-50849** (適用於Adobe Commerce >=2.4.4 &lt;2.4.6) — 修正清除快取後將新產品新增至類別，導致現有產品的位置和選擇不符的問題。
* **ACSD-51294** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正GTM/GA價格、數量、稅金、配送和收入以字串形式傳送至[!DNL Google Analytics]和GTM的問題。
* **ACSD-51204** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正建立銷退折讓單後，已完整銷售的產品未退還存貨的問題。
* **ACSD-51291** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.4-p4) || >=2.4.5 &lt;2.4.5-p3) — 修正限制管理員存取一個網站後，可以將影像/影片新增至指派給多個網站之產品的問題。
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

* **ACSD-50336** (適用於Adobe Commerce和Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) — 修正產品重新上架或價格變更時，未傳送產品警示電子郵件的問題。
* **ACSD-50367** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正建立不含值的多重選取客戶地址屬性時，無法匯出客戶地址的問題。
* **ACSD-49877** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正視訊直接連結至遠端視訊檔案而非串流服務時，在行動[!DNL Safari]上無法自動播放視訊的問題。
* **ACSD-50165** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修正錯誤&#x200B;*無法刪除檔案。 警告！unlink：從Admin排清JS/CSS快取時，沒有這樣的檔案或目錄*。
* **ACSD-49737** (適用於Adobe Commerce和Magento Open Source >=2.4.1-p1 &lt;2.4.7) — 修正信用卡付款失敗後，優惠券被錯誤地標示為使用的問題。
* **ACSD-50814** (適用於Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修正管理員使用者無法建立銷退折讓單的問題。
* **ACSD-50116** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正管理員使用者無法為子類別層級3或更低層級建立URL重寫的問題。
* **ACSD-49513** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5) — 修正遠端儲存體同步作業因0位元組檔案而失敗的問題。
* **ACSD-46683** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正送貨價格顯示&#x200B;*尚未計算*&#x200B;的問題。
* **ACSD-49129** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正&#x200B;*[!UICONTROL content]*&#x200B;產品媒體API回應中未傳回`rest/V1/products/sku/media`屬性（base64影像代碼）的問題。
* **ACSD-50276** (適用於Adobe Commerce >=2.4.0 &lt;2.4.7) — 修正建立多選客戶屬性時，店面無法使用客戶登錄檔單的問題。
* **ACSD-50527** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正儲存具有空白動態區塊的頁面時發生的錯誤。
* **ACSD-49973** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 改善透過GraphQL擷取套件產品的效能。
* **ACSD-51114** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正啟用非同步索引時，大型目錄中的隨機產品消失的問題。 改善大型目錄非同步重新索引的效能。
* **B2B-2598** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 將快取功能新增至[!UICONTROL availableStores]、[!UICONTROL countries]、[!UICONTROL country]、[!UICONTROL currency]和[!UICONTROL storeConfig]個GraphQL查詢。
* 新增 MDVA-42806、ACSD-48627、ACSD-46815 版本。
* 更新了 ACSD-49773、ACSD-47179、ACSD-48300 的補丁元資料。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** （用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.7) - Fixes the issue where a ready-to-pick-up email is sent by API when the order is not ready for pickup.
* **ACSD-49822** （用於 Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where updates in the [!UICONTROL Requisition List] 頁面）不會反映在 [!UICONTROL Print Requisition List].
* **ACSD-48771** （適用於 Adobe Commerce 與 Magento 開源>=2.4.5 &lt;2.4.7) - Fixes the issue with upgrading the column-block content type from older [!DNL Page Builder] 版本。
* **ACSD-49464** （用於 Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where invoices, shipments, and credit memos are not moved back from the archive when the orderId is different.
* **ACSD-49773** （用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.6) - Fixes the issue where product export fails when AWS S3 is used as remote storage.
* **ACSD-49748** （用於 Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where invitations cannot be sent.
* **ACSD-49502** （用於 Adobe Commerce >=2.4.3 &lt;2.4.7) - Fixes the issue where the downloadable link is not updated properly after a staging update is applied to the downloadable product.
* **ACSD-49527** （用於 Adobe Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where GraphQL company roles don&#39;t display pagination correctly.
* **ACSD-49706** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正未選取值時為視覺色票屬性儲存預設值的問題。
* **ACSD-49835** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正多選屬性的存放區層級未正確儲存「使用預設核取方塊值」的問題。
* **ACSD-49898** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正當捆綁產品的特殊價格超過1000時，產品格線擲回例外狀況的問題。
* **ACSD-50234** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.5) — 修正向[!DNL PayPal]下訂單時，確認電子郵件中客戶名稱錯誤的問題。
* **ACSD-49960** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正客戶訂單格線無法依日期篩選的問題。
* **ACSD-49849** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正透過GraphQL以[!DNL PayPal]下訂單時，客戶電子郵件被[!DNL PayPal Express]電子郵件取代的問題。
* **ACSD-49839** （用於 Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where Shared Catalog Pricing and structure throws an error in Admin when products have single or double quotes in SKU.
* **ACSD-49970** （用於 Adobe Commerce 和 Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes incorrect handling of GraphQL errors when [!DNL New Relic] 報告已開啟。
* **ACSD-50260** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正GraphQL產品搜尋結果限製為僅限10,000個結果的問題。
* **ACSD-48813** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正搜尋未根據屬性的搜尋權重顯示相關結果的問題。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** （用於 Adobe Commerce 與 Magento 開源 >=2.3.7 &lt;2.4.3) - Fixes the issue where a catalog price rule created based on the Yes/No attribute does not consider the selected scope.
* **ACSD-47704** （用於 Adobe Commerce 與 Magento 開源 >=2.3.7 &lt;2.4.7) - Fixes the issue where the bundled product shows the price of in stock products only.
* **ACSD-49370**（用於 Adobe Commerce 與 Magento 開源 >=2.3.7 *&lt;2.4.7) - Fixes the issue where the  Date Time* 產品屬性在 GraphQL 架構中有一個 *FilterMatchTypeInput* 類型。
* **ACSD-48807** （用於 Adobe Commerce 與 Magento 開源 >=2.4.1 &lt;2.4.7) - Fixes the issue where customer Product Reviews are not filtered by storeview via GraphQL.
* **ACSD-49433** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt;2.4.7) - Fixes the issue where the default amount is shown as subtotal in the cart for gift card with an open amount.
* **ACSD-48866** （用於 Adobe Commerce 與 Magento 開源 >=2.3.7 &lt;2.4.7) - Fixes the issue where an error occurs when requesting RSS feed for categories.
* **ACSD-48784** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正客戶群組之間不正確快取客戶區段價格的問題。
* **ACSD-48857** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正使用者在使用頁面產生器編輯後無法儲存變更的問題。
* **ACSD-49065** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正僅指派給自訂庫存時，管理員中看不到報價專案的問題。
* **ACSD-49179** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正不同商店使用不同貨幣時，訂單報表顯示錯誤金額的問題。
* **ACSD-49286** （用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt;2.4.7) - Fixes the issue where a product is added twice to a cart when multiple product widgets are present on the page.
* **ACSD-49574** （用於 Adobe Commerce >=2.4.4 &lt;2.4.7) - Adds functionality to support Gift Card product updates in a cart via GraphQL.
* 更新更新：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (適用於Adobe Commerce >=2.4.1 &lt;2.4.7) — 修正使用可協商報價下訂單時，使用預設送貨地址而非新送貨地址的問題。
* **ACSD-48059** (適用於Adobe Commerce >=2.3.7 &lt;2.4.7) — 修正商家無法儲存類別中「[!UICONTROL Match product by rule]」的問題。
* **ACSD-48216** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修正[!UICONTROL AUTO_INCREMENT]作業中[!UICONTROL inventory_source_item]資料表的[!UICONTROL UPDATE]增加的問題。
* **ACSD-47908** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修正結帳期間，在出貨步驟上選取來源和數量時，出現「預期值小於或等於0」的錯誤。
* **ACSD-49497** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正訂單在出貨後仍為處理狀態且套用部分退款的問題。
* **ACSD-48694** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) — 修正錯誤「要求的狀態變更無效」導致客戶無法下訂單的問題。
* **ACSD-49013** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修正使用大量API建立客戶時，電子郵件確認未轉譯為網站地區設定的問題。
* **ACSD-48164** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正受限管理員無法儲存網站層級值的問題。
* **ACSD-48404** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正按瀏覽器的上一頁按鈕時，「記住類別分頁=是」會導致錯誤的問題。
* **ACSD-48634** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 啟用「[!UICONTROL Google Analytics Content Experiments]」時，修正測試更新頁面上的JS錯誤。
* **ACSD-49042** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正無法從店面訂購無限延期交貨的產品的問題。
* 更新修補程式：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (適用於Adobe Commerce和Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) — 修正由於應用程式層級的快取而不一定傳送價格下降通知的問題。
* **ACSD-48661** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正當公司的信用額度大於999時，逗號分隔符號會因驗證錯誤而無法儲存公司的問題。
* **ACSD-48773** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修正從錯誤商店取得獎勵點數電子郵件範本的問題。
* **ACSD-48587** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修正產品Widget比對規則中HTML特殊字元無法顯示相符產品的問題。
* **ACSD-48212** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正產品匯入將產品指派給錯誤來源的問題。
* **ACSD-47988** (適用於Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修正產品匯出從頁面產生器產品說明中裁剪HTML標籤的問題。
* **ACSD-48366** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正「補貨」電子郵件範本未顯示產品影像的問題。
* **ACSD-48417** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修正建立產品的排程變更並儲存另一個產品後出現SQL錯誤的問題。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正未將套件組合產品指派給任何網站時，產品價格重新索引無法運作的問題。
* **ACSD-48262** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正當「允許每頁所有產品」設定設為「是」時，前端不會顯示產品的問題。
* **ACSD-48293** (適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4) — 修正當已售出的子產品恢復庫存時，複合產品缺貨的問題。
* **ACSD-47520** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正建立銷退折讓單時客戶遺失獎勵點數的問題。
* **ACSD-48044** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正將多張禮品卡套用至有多張送貨的單張訂單時，無法下單的問題。
* **ACSD-48300** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正移除可設定產品時無法建立傳回的問題。
* **ACSD-47910** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正個別實體網格中遺失訂單、發票、出貨及銷退折讓單的問題。
* **ACSD-47292** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正當「顯示無庫存產品」設為「是」時，GraphQL回應中無法使用無庫存套件產品的問題。
* **ACSD-48234** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正啟用「無庫存」選項時，目錄搜尋結果顯示不正確類別專案計數的問題。
* **ACSD-48313** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5) — 修正屬性值包含逗號時無法剖析「configurable_variations」欄的問題。 「additional_attributes」會使用相同的剖析演演算法。
* **ACSD-48627** (適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6) — 修正當傳送GraphQL請求以取得購物車詳細資料時，無存貨的可設定產品會導致錯誤的問題。
* 更新修補程式：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正在store-view層級上覆寫&#x200B;*url_key*&#x200B;屬性的產品未產生SEO易記URL的問題。
* **ACSD-46865** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正啟用非同步索引時未填入出貨和銷退折讓單格線的問題。
* **ACSD-47004** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正無VAT ID的帳單地址未套用VAT的問題。
* **ACSD-47803** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正無庫存可設定產品色票顯示為可用色票的問題。
* **ACSD-47137** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 當pub/media資料夾非常大時，提升影像庫的載入速度。
* **ACSD-46770** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正即使未勾選&#x200B;*電子郵件訂單確認*，仍會傳送管理員訂單電子郵件的問題。
* **ACSD-47955** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正GraphQL未正確顯示購物車折扣的問題。
* **ACSD-46617** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正即使小計大於設定的&#x200B;*最小訂購量*，*繼續結帳*&#x200B;按鈕仍會呈現灰色的問題。
* **ACSD-47079** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修正當子產品庫存狀態透過REST API POST /rest/V1/inventory/source-items變更時，複合產品（套件、分組和可設定）庫存狀態未更新的問題。
* **ACSD-47336** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正&#x200B;*發生錯誤。在Commerce管理員中關閉通知時發生*&#x200B;錯誤。
* **ACSD-47559** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正預覽電子郵件範本區域未完全可見的問題。
* **ACSD-47920** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正在&#x200B;*允許訪客結帳*&#x200B;關閉時，透過Rest API以訪客使用者身分下訂單的問題。
* 已取代的修補程式：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正具有特定範圍受限存取權的管理員無法刪除產品評論的問題。
* **ACSD-47107** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5) — 修正將目錄價格規則折扣套用至自訂產品選項的問題。
* **ACSD-47232** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正無法在Admin中套用具有總權重條件的優惠券的問題。
* **ACSD-46519** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.6) — 修正GraphQL categoryList要求傳回錨點類別不正確product_count的問題。
* **ACSD-47027** （用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.6) - Fixes a slow updateCompanyRole GraphQL request.
* **ACSD-47666** （用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.6) -=&quot;&quot; fixes=&quot;&quot; the=&quot;&quot; issue=&quot;&quot; where=&quot;&quot; the=&quot;&quot; filter=&quot;&quot; function=&quot;&quot; does=&quot;&quot; not=&quot;&quot; work=&quot;&quot; in=&quot;&quot; the=&quot;&quot; admin=&quot;&quot;> 系統>權限>使用者角色>角色>角色使用者格子。&lt;/2.4.6)>
* **ACSD-47497** （用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.6) - Fixes the issue where the Services tab is not visible in the Configuration under the Admin.
* 更新修補程式：ACSD-47743。
* 已取代的修補程式：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444（** 用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.3) - Fixes the _嘗試在存取某些不存在的類別路徑時，針對 type 為 bool_ 的值存取陣列偏移量，該路徑為 PHP 7.4 的已知產品。
* **ACSD-47332** （用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.6) - Fixes the issue where cron fails with an error that is only reported when running between 00:00 及 00:59 UTC。
* **ACSD-47280** （用於 Adobe Commerce 與 Magento 開源 >=2.4.0 &lt;2.4.6) - Fixes the issue where disabling the shared catalog feature on a specific scope does not work correctly.
* **ACSD-47106** （用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.6) - Fixes the issue where a value cannot be saved in a new custom attribute on a company creation page.
* 更新修補程式：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修正使用者在指派大量產品來源時出現錯誤的問題。
* **ACSD-46856** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 透過「系統>設定>匯入>進階價格」，改善效能並更新層級價格。
* **ACSD-46541** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修正刪除訂單專案時，管理員使用者無法建立銷退折讓單的問題。
* **ACSD-46581** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正選取購物車中的國家/地區後，預估稅捐總計未更新的問題。
* **ACSD-46618** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正產品清單Widget針對登入客戶顯示不正確快取價格的問題。
* **ACSD-46674** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修正客戶電子郵件中將影像型別的自訂選項顯示為HTML的問題。
* **ACSD-46988** (適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修正GraphQL &#39;currency&#39; API要求傳回自訂貨幣NULL值的問題。
* **ACSD-47076** (適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5) — 修正無法在店面播放Vimeo影片的問題。
* **ACSD-45071** (適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4) — 修正匯入期間將預設來源新增至產品的問題。
* **AC-3023** (適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 將DHL配置更新至最新版本10.0。
* 更新修補程式：MDVA-42584。
* 已取代修補程式：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5*) — 修正使用者使用商店點數退款時訂單狀態不正確的問題。
* **ACSD-46703** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6*) — 修正無法在產品編輯頁面上拖放自訂選項的問題。
* **ACSD-44851** (*用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6*) — 修正具有子類別的類別無法開啟或展開的問題。
* **ACSD-46815** (*適用於Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.6*) — 修正類別樹狀結構請求限製為20個類別的問題。
* **ACSD-45675** (*用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6*) — 修正產品匯出使用&#x200B;*預設商店檢視*&#x200B;範圍內的類別名稱的問題。
* **ACSD-46869** (*適用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6*) — 修正購物車中的可設定產品未透過&#x200B;*PUT REST API*&#x200B;請求更新而不變更產品數量的問題。
* **MDVA-42768-V2**（*適用於 Adobe Commerce 與 Magento 開源 >=2.4.2*&lt;2.4.3）-修正了可配置產品在顯示缺貨&#x200B;*為*「是」*時，正常價格*&#x200B;顯示為 0 **&#x200B;的問題。
* 更新的補丁：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 已棄用補丁：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** （*用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.3*）-修正類別樹請求限制為 20 個類別的問題。
* **ACSD-45781** （*用於 Adobe Commerce 與 Magento 開源 >=2.4.1 &lt;2.4.2*）-修正了行動端商店搜尋欄位未顯示的問題。
* **ACSD-46192**（*用於 Adobe Commerce 與 Magento 開源 >=2.3.6*&lt;2.4.5）- 解決使用`async/bulk/V1/configurable-products/bySku/options`端點的問題。
* **ACSD-46404** （*適用於 Adobe Commerce 與 Magento 開源 >=2.4.4 &lt;2.4.5*）— 修正管理員升級至 2.4.4 後無法登入的問題。
* 更新版補丁：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** （*適用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.4*）-修正特定商店的 GraphQL 產品變異會回傳所有可配置版本的問題，包括未分配到指定商店的版本。
* **ACSD-46146** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.6*) — 修正管理員下單後傳送兩封訂單確認電子郵件的問題。
* **ACSD-45255** (*適用於Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修正受限管理員使用者的「低庫存報告」頁面上的例外狀況。
* **ACSD-45488** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6*) — 修正具有多個來源的可設定產品未自動傳回庫存的問題。
* **ACSD-45754** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.6*) — 修正將優惠券套用至購物車後未新增獎勵點數的問題。
* **ACSD-45849** (*適用於Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修正套用中繼更新後視訊中繼資料遺失的問題。
* **ACSD-45257** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.4*) — 修正GraphQL未正確顯示購物車折扣的問題。
* **ACSD-44938** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4*) — 修正`VAT_ID`無法套用至訪客使用者之GraphQL要求的問題。
* 更新修補程式：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.4*) — 修正建立銷退折讓單後虛擬產品存貨數量計算錯誤的問題。
* **ACSD-43887** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正啟用公司採購訂單時，結帳付款頁面上顯示不正確詳細資訊的問題。
* **ACSD-45143** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5*) — 修正`setShippingAddressesOnCart`突變不允許將數值區碼設為&#x200B;*region*&#x200B;的問題。
* **ACSD-44591** (*用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.6*) — 修正未通過驗證碼確認而下達訂單時發生的錯誤。
* **ACSD-45520** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.6*) — 修正使用者從購物車編輯可設定產品時，未在產品詳細資料頁面上預先選取色票選項的問題。
* **ACSD-45169** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.6*) — 修正套用中繼更新後，[!DNL Visual Merchandiser]無法顯示可設定產品正確庫存和價格的問題。
* **ACSD-45424** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.6*) — 修正部分退款（銷退折讓單）後建立錯誤預訂補償的問題。
* **MDVA-42807** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.6*) — 修正商店前方未顯示自訂貨幣符號的問題。
* 更新修補程式：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正限制管理員使用者的「訂單」報表中訂單總計計算錯誤的問題。
* **MDVA-44940** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正從管理員儲存類別時發生的SQL錯誤。
* **MDVA-44562** (*用於Adobe Commerce和Magento Open Source GraphQL >=2.4.0 &lt;2.4.2-p2*) — 修正預設商店ID覆寫報價專案的非預設商店ID的問題，儘管該請求源自非預設商店檢視。
* **MDVA-43167** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正當管理員使用者選取所有訂單時，管理員訂單格線大量動作不適用於多頁的問題。
* **MDVA-44044** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.2-p2*) — 修正將產品指派至新網站後，產品未顯示在類別頁面上的問題。
* **MDVA-42509** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.4*) — 修正無法快速上傳CSV而導致&#x200B;*無法傳送Cookie*&#x200B;錯誤的問題。
* 更新修補程式：MDVA-41061、MDVA-42584。
* 由於內部處理程式變更，新[!DNL Quality Patches Tool]修補程式的字首將從&#x200B;*MDVA*&#x200B;變更為&#x200B;*ACSD*。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正當購物車中已有最小專案數量時，無法將其他專案新增到購物車的問題。
* **MDVA-44887** (*用於Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5*) — 修正「管理」面板中的&#x200B;*Uncaught SyntaxError： Unexpected token &#39;const&#39;*&#x200B;錯誤。
* **MDVA-43718** (*用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正&#x200B;*消費者無權存取%resources。從自訂整合存取共用目錄時出現*&#x200B;錯誤。
* **MDVA-44660** (*適用於Adobe Commerce和Magento Open Source >=2.4.2-p1 &lt;2.4.5*) — 修正重音符號字元``` ` ```無法用於客戶名字和姓氏的問題。
* **MDVA-40896** (*用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正非同步產品批次API中的&#x200B;*錯誤： TypeError：傳遞給Magento*&#x200B;引數3錯誤。
* **MDVA-38559** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.3*) — 修正具有多個訂閱之客戶的&#x200B;*/V1/customers/search API*&#x200B;錯誤。
* **MDVA-44533** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.4*) — 修正錯誤將折扣套用至套件組合子產品的問題。
* 更新修補程式：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正產品&#x200B;*無法個別顯示*&#x200B;仍出現在目錄進階搜尋結果中的問題。
* **MDVA-44100** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正將所有FPT指派給購物車中最後一個產品並為其他產品重設的問題。
* **MDVA-43605** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.5*) — 修正使用Rest API時，訂單資料傳回列總計負值的問題。
* **MDVA-43102** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;2.4.5*) — 修正透過REST API進行退款時，未正確更新可售數量的問題。
* **MDVA-43178** (*適用於Adobe Commerce和Magento Open Source >=2.4.3-p2 &lt;2.4.5*) — 修正無法在GraphQL中擷取自訂存放區之客戶權杖的問題。
* **MDVA-43859** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正錯誤&#x200B;*當已刪除的客戶嘗試登入時，不會記錄任何具有customerId =*&#x200B;的這類實體的問題。
* **MDVA-44147** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正GraphQL要求未傳回請購單清單的問題。
* **MDVA-44505** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.3*) — 修正GraphQL套用獎勵點數未更新總量，以及在下單期間多次套用商店點數的問題。
* 更新修補程式：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.3*) — 修正當「客戶區段」設定為&#x200B;*全部*&#x200B;時，「相關產品規則」才能運作的問題。
* **MDVA-39605** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.5*) — 修正Redis快取TTL （到期日）有錯誤值的問題。
* **MDVA-43862** (*用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.5*) — 修正客戶由於GraphQL *UpdateCartItems突變*&#x200B;錯誤而無法更新購物車專案的問題。
* **MDVA-43824** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 修正取消具有折扣的訂單時出現錯誤的問題。
* **MDVA-43451** (*用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正錯誤&#x200B;*找不到所要求的存放區的問題。 請驗證存放區，然後再試一次。為特定網站設定共用目錄時出現*。
* **MDVA-43491** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.5*) — 修正為多商店網站匯入產品時，基礎影像標籤未更新的問題。
* **MDVA-43601** (*用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正完整重新索引後缺少觸發器的問題。
* **MDVA-42046** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修正更新產品時，透過日期輸入欄位將錯誤值指派給產品屬性的問題。
* **MDVA-43935** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正向上銷售產品顯示兩次的問題。
* **MDVA-44188** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正系統所核發的電子郵件地址中`.-`未傳送的問題。
* **MDVA-42283** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正法文地區設定的管理順序格線中的日期 — 時間格式無效的問題。
* 更新修補程式：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 已新增[!DNL Site-Wide Analysis Tool]的修補程式中繼資料。

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.3.6*) — 修正使用者可編輯作用中排程更新開始時間的問題。
* **MDVA-42410** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正優惠券報表僅顯示預設基本貨幣的問題。
* **MDVA-41136** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正`mage-cache-sessid`到期日未延長，導致客戶資料清理的問題。
* **MDVA-39993** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修正透過API完成的詳細目錄變更未反映在前端產品頁面上的問題。
* **MDVA-42855** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正結帳期間新客戶地址未儲存至通訊錄的問題。
* **MDVA-42645** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正當商店信用功能停用時，管理員無法退款獎勵點數的問題。
* **MDVA-43414** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) — 修正數值SKU上執行`inventory.reservations.updateSalabilityStatus`佇列消費者時發生的PHP嚴重錯誤。
* **MDVA-41628** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5*) — 修正當新增模組時，現有受限制的管理員使用者取得新資源存取權的問題。
* **MDVA-43348** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正`gift_card_options`包含&#x200B;*uid*&#x200B;時，禮品卡GraphQL要求顯示錯誤的問題。
* **MDVA-39546** （*適用於 Adobe Commerce 與 Magento 開源 >=2.3.0 &lt;2.4.5*）— 修正編輯時階段更新開始日期可能比當前日期更早的問題。
* **MDVA-42950** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正產品頁面上無法播放視訊的問題。
* **MDVA-42689** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正匯入期間更新產品類別時，Adobe Commerce擲回&#x200B;*完整性條件約束違規*&#x200B;錯誤的問題。
* **MDVA-41229** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正可設定產品匯入後，前端上可用的影像未顯示的問題。
* **MDVA-43731** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正在&#x200B;*符合*&#x200B;的最少字詞中新增值時，*搜尋同義字*&#x200B;不再運作的問題。
* **MDVA-43232** (*用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.5*) — 修正在[!DNL Visual Merchandiser]中依「特殊價格從下到上」排序產品時，導致儲存類別時發生錯誤的問題。
* **MDVA-43726** （*適用於 Adobe Commerce 與 Magento 開源 >=2.3.3 &lt;2.4.3*）— 修正基於商店層級屬性匹配的目錄價格規則在部分重新索引後無法適用的問題。
* 更新補丁：MDVA-36464、MDVA-37478、MDVA-38608。
* 新增了 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** （*適用於 Adobe Commerce 與 Magento 開源 >=2.4.3 &lt;2.4.5*）-修正無法透過 REST API 更新特定網站產品價格屬性的問題。
* **MDVA-41350** （*適用於 Adobe Commerce 與 Magento 開源 >=2.3.0 &lt;2.4.5*）— 修正了當管理員以受限制存取權限依 SKU 新增超出其角色範圍的產品時，拋出例外問題。
* **MDVA-42269**（*適用於 Adobe Commerce 與 Magento 開源 >=2.4.3-p1&lt;2.4.5*）— 修正管理員因 TypeError： strtotime（） 預期參數 1 為字串，錯誤時&#x200B;*為空，無法登入管理員*&#x200B;的問題。
* **MDVA-40830** （*適用於 Adobe Commerce 和 Magento 開源 >=2.3.0 &lt;2.4.5*）-修正了下單時商店點數重複套用的問題。
* **MDVA-42237** （*適用於 Adobe Commerce 與 Magento 開源 >=2.4.2 &lt;2.4.5*）- 修正可設定產品特別價格在其子產品價格變動後未更新的問題。
* **MDVA-42520**（*適用於 Adobe Commerce 與 Magento 開源 >=2.4.3&lt;2.4.4*）-修正若啟用跨境貿易&#x200B;*時*&#x200B;稅率會重複適用的問題。
* 更新補丁：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已棄用的修補程式：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*適用於Adobe Commerce和Magento Open Source >=2.3.2 &lt;2.4.5*) — 修正大量屬性更新在變更&#x200B;*產品可見度*&#x200B;後才會為預設商店建立URL重寫的問題。
* **MDVA-43091** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正從後端的Admin訂購套件組合產品時，發生錯誤&#x200B;*的問題。您無法對此產品使用小數數量*。
* **MDVA-40816** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正相關產品規則顯示規則條件中未定義類別之產品的問題。
* **MDVA-41305** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5*) — 修正GraphQL突變在將其新增至願望清單後未傳回可設定產品選項的問題。
* **MDVA-39181** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正相關產品規則顯示規則條件中未定義類別之產品的問題。
* **MDVA-42584** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正透過「匯入」或API變更數量與庫存狀態後，後端中可設定的庫存狀態未更新的問題。
* **MDVA-40175** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.3*) — 修正&#x200B;*按一下以變更送貨方法*&#x200B;在重新排序期間未顯示選項按鈕以在Admin中選取送貨方法的問題。
* **MDVA-42768** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.5*) — 修正當&#x200B;*顯示無庫存*&#x200B;為「是」時，可設定產品的正常價格顯示為0的問題。
* **MDVA-43201** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正搭配特定地區設定使用DOB屬性時，客戶登入發生錯誤的問題。
* 更新修補程式：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.5*) — 修正當Adobe Commerce時區與本機環境時區不同時，日期篩選器無法正常運作的問題。
* **MDVA-42657** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正管理員使用者無法在客戶區段條件中選取類別的問題。
* **MDVA-42806** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正每次透過REST API更新現有公司時，都會傳送&#x200B;*新公司註冊*&#x200B;電子郵件的問題。
* **MDVA-37984** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5*) — 修正[!DNL Visual Merchandiser] *依規則比對產品*&#x200B;功能無法正確篩選具有暫存更新的產品的問題。
* **MDVA-40488** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正可設定產品與無庫存子產品無法在其正確價格範圍中顯示的問題。
* **MDVA-42507** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5*) — 修正套用購物車規則的測試更新後，清除整頁快取的問題。
* **MDVA-39163** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.5*) — 修正新使用者註冊後無法使用送貨方法，且購物車中的產品來自訪客工作階段的問題。
* **MDVA-38626** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.5*) — 修正管理員使用者無法使用[!DNL PayPal Payflow Pro]付款在後端下單的問題。
* **MDVA-38666** (*適用於Adobe Commerce和Magento Open Source >=2.3.2 &lt;2.3.6*) — 修正管理員使用者無法變更客戶購物車中可設定產品選項的問題。
* **MDVA-38526** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正系統管理員使用者無法存取[!DNL Site-Wide Analysis tool]的問題。
* 更新修補程式：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正使用者在設定&#x200B;*mage-messages* Cookie （如果已經存在）後收到500錯誤的問題，但沒有任何新訊息。
* **MDVA-41139** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4*) — 修正產品匯入後，當簡單產品其中一個來源的數量為0時，可設定產品會變成無存貨的問題。
* **MDVA-42326** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正即使永續性購物車已啟用，客戶在工作階段逾時後結帳時仍發生錯誤的問題。
* **MDVA-42341** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正當要求具有存放區標頭時，`categoryList` GraphQL查詢無法篩選結果的問題。
* **MDVA-38393** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正簡單產品重新命名時，可設定產品目錄規則停止運作的問題。
* **MDVA-39153** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正在Admin中重新排序時折扣金額計算不正確的問題。
* 更新修補程式：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.3*) — 修正管理員使用者在刪除網站後無法存取客戶網格的問題。
* **MDVA-40311** (*適用於Adobe Commerce和Magento Open Source >=2.4.2-p2 &lt;2.4.4*) — 修正管理員使用者收到錯誤訊息&#x200B;*安全性或表單金鑰無效的問題。 如果已設定自訂管理路徑且啟用秘密金鑰，請在登入管理員後重新整理頁面*。
* **MDVA-41631** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正使用者嘗試透過GraphQL擷取訂單資訊時，在沒有選擇性&#x200B;*電話*&#x200B;值的情況下發生錯誤的問題。
* **MDVA-27239** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.3.6*) — 修正未顯示交叉銷售產品的問題。
* 更新修補程式：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.4*) — 修正重新索引期間前端遺失產品的問題。
* **MDVA-40120** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正按DESC/ASC排序的GraphQL無法搭配具有相同關聯性或價格的產品運作的問題。
* **MDVA-41399** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;2.4.2*) — 修正客戶將產品加入願望清單時，管理員使用者無法存取&#x200B;*管理購物車*&#x200B;頁面的問題。
* **MDVA-40609** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正`cataloginventory_stock_status`索引表格中沒有停用產品資料，顯示不正確停用產品數量的問題。
* **MDVA-39031** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正即使未指派至目標網站，透過GraphQL將產品新增至購物車仍可行的問題。
* **MDVA-41597** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正使用GraphQL將多個可設定產品新增到購物車時，使用者收到錯誤的問題。
* **MDVA-27456** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.3.7*) — 修正使用者嘗試載入[!DNL Swagger]時發生錯誤的問題。
* **MDVA-32776** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.2*) — 修正已下訂單但未送貨時存貨狀態未更新的問題。
* **MDVA-30862** (*用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.0*) — 修正列印的PDF發票上訂購日期不正確的問題。
* 已改善[!DNL Quality Patch Tool]的索引頁面。 新增工具最新版本的[!DNL quality patches]便利搜尋和篩選功能。
* 更新修補程式：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正先前已移除「結束日期」時，無法建立新的產品更新或編輯現有排程更新的問題。
* **MDVA-41046** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正簡單產品可指派給可設定/分組產品的問題。
* **MDVA-40545** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正即使同一頁面有多個節點，僅擷取頁面的第一個節點的問題。
* **MDVA-41164** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3-p1*) — 修正管理員使用者無法儲存或編輯具有檔案或影像型別自訂客戶屬性的公司的問題。
* **MDVA-39229** (*用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正更新目錄規則中繼更新開始時間後出現下列錯誤的問題： *Cron工作staging_synchronize_entities_period有錯誤：無法刪除作用中的更新。*
* **MDVA-40619** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正嘗試在CMS頁面上執行內聯編輯時，CMS頁面階層變更會導致500錯誤的問題。
* **MDVA-41061** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正從管理員儲存產品時，庫存狀態重設為可銷售的問題。
* **MDVA-31763** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正目錄價格規則在手動重新索引前還原（或未套用）的問題。
* **MDVA-37748** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正GraphQL查詢傳回未指派給共用目錄之產品的問題。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正無法透過REST API同時建立相同訂單部分發票的問題。
* **MDVA-40101** (*適用於Adobe Commerce和Magento Open Source >=2.3.2 &lt;2.4.0*) — 修正使用[!DNL PayPal Express]結帳成功下單後，無法從迷你購物車移除專案的問題。
* **MDVA-40401** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正即使下訂單失敗，優惠券使用量值仍會變更的問題。
* **MDVA-40537** (*用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) — 修正使用者在建立存放區檢視時遇到錯誤(若存在具有相同URL金鑰的多個CMS頁面)的問題。
* **MDVA-37725** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) — 修正從非預設網站傳送的非同步訂購電子郵件包含預設網站的標誌URL的問題。
* **MDVA-39482** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修正啟用延期交貨時，以「0」數量匯入的產品無存貨的問題。
* **MDVA-40435** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;2.4.4*) — 修正透過GraphQL套用時，具有動態價格的套件組合產品折扣不正確的問題。
* **MC-42528** (*適用於Adobe Commerce和Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) — 修正`categoryList` GraphQL查詢傳回已指派和未指派類別的問題。
* **MDVA-29400** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修正[!DNL PayPal Express Checkout]下重複訂單的問題。
* **MDVA-26005** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) — 修正無法在購物車價格規則條件的類別樹狀結構中選取類別的問題。
* **MDVA-25631** (*適用於Adobe Commerce和Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) — 改善編輯和儲存包含大量客戶的客戶區段的效能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正GraphQL搜尋查詢未顯示在Admin常用搜尋詞中的問題。
* **MDVA-40601** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) — 修正使用者嘗試透過GraphQL取得排程更新所變更類別的相關資訊時發生錯誤的問題。
* **MDVA-37234** (*適用於Adobe Commerce和Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修正針對相同SKU將專案多次新增至購物車（平行請求）時，會為相同購物車ID建立重複條列專案的問題。
* **MDVA-33606** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) — 修正使用者在儲存指派給階層的CMS頁面時，收到&#x200B;*唯一條件約束違規*&#x200B;錯誤的問題。
* **MDVA-31590** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) — 修正使用者無法使用MySQL非同步佇列大量更新屬性的問題。
* **MDVA-36309** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修正管理格線中依屬性搜尋產品速度緩慢的問題。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正從商店信用支付訂單時，含FPT的商業發票顯示錯誤總金額的問題。
* **MDVA-37364** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;=2.4.3*) — 修正日期型別的自訂客戶屬性破壞客戶網格UI的問題。
* **MDVA-39195** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修正當重新導向至購物車已啟用時，*加入購物車*&#x200B;按鈕在類別頁面上未作用中的問題。
* **MDVA-37115** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修正可設定產品頁面上顯示不必要的&#x200B;*僅剩下0*&#x200B;注意事項的問題。
* **MDVA-39521** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4*) — 修正使用者無法透過GraphQL以空白電話號碼設定購物車送貨地址的問題。
* **MDVA-39384** (*適用於Adobe Commerce和Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修正未儲存公司使用者的自訂客戶屬性的問題。
* **MDVA-39043** (*適用於Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.4.3*) — 修正具有有限存取權的管理員使用者嘗試將&#x200B;*產品*&#x200B;小工具新增至CMS頁面時發生錯誤的問題。
* **MDVA-39966** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 修正部署錯誤地區設定的問題。
* **MDVA-38852** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) — 修正目錄庫存依設計鎖定資料表的問題，此問題會在有多個平行訂單的情況下大幅降低效能。
* **MDVA-39986** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.3*) — 修正使用者無法使用Safari瀏覽器在MacOS的Admin中下訂單的問題。
* **MDVA-38447** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4*) — 修正兩個問題：其中&#x200B;*無法個別顯示*&#x200B;可設定的子產品會在GraphQL回應中傳回，並使用類別篩選器最佳化GraphQL產品查詢的MySQL查詢。
* **MDVA-40134** (*適用於Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.3*) — 修正啟用共用目錄時，GraphQL未傳回相關產品的問題。
* **MDVA-39935** (*適用於Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.4*) — 修正GraphQL傳回可在網站層級停用的可設定子產品的問題。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4*) — 修正Admin中訂單詳細資料頁面上顯示&#x200B;*呼叫成員函式getId()*&#x200B;錯誤的問題。
* **MDVA-34948** (*適用於Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修正長時間執行之查詢（例如`GET_LOCK`）的問題。
* **MDVA-39305** (*適用於Adobe Commerce和Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) — 修正註冊客戶無法以已啟用的Google ReCaptcha登入的問題。
* **MDVA-37897** (*適用於Adobe Commerce和Magento Open Source >=2.3.0 &lt;2.4.4*) — 修正客戶嘗試使用「最近檢視」Widget的選項新增產品時，重新導向不正確的問題。

## v1.1.0 {#v1-1-0}

* 我們引進了修補程式類別，以改善使用者體驗，並讓客戶更輕鬆地搜尋所需的修補程式。
* `patches.json`檔案已重新命名為`support-patches.json`。
* **MDVA-38799** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正建立中繼更新後未儲存可下載產品的問題。
* **MDVA-37592** (*適用於Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修正指定至共用目錄之零價格產品無法正確依價格排序的問題。
* **MDVA-38827** (*適用於Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) — 修正客戶收到包含錯誤訊息的訂單運送電子郵件的問題。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*用於Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修正儲存CMS頁面時的錯誤： *已有相同識別碼PAGE_ID的專案*。
* **MDVA-34680** (*適用於Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修正客戶格線中未正確篩選客戶帳戶建立時間的問題。
* **MDVA-37068** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.4*) — 修正當購物車只有虛擬產品時顯示錯誤稅率的問題。
* **MDVA-38608** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正重新索引未成功完成時暫時資料表未刪除的問題。
* **MDVA-38308（用於 Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 ||=&quot;&quot;>=2.4.0 &lt;=2.4.1-p1 ||=&quot;&quot;>=2.4.2&lt;2.4.4**）- 修正與在產品中新增&#x200B;*影片相關的問題。&lt;/=2.4.1-p1>&lt;/=2.3.6-p1>*[!DNL Vimeo]

## v1.0.25 {#v1-0-25}

* **MDVA-37916**（*用於 Adobe Commerce >=2.3.6*&lt;2.4.3）- 修正使用[!DNL Paypal Payment Advanced]該方法時客戶未進入付款確認頁面的問題。
* **MDVA-37082** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.3*）— 修正了儲存群組產品的自訂庫存導致前端顯示缺貨的問題。
* **MDVA-36572** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修正銷退折讓單更新不再導致資料庫中出現重複產品預訂更新的問題。
* **MDVA-38132**（*用於 Adobe Commerce >=2.3.3*&lt;2.4.3）— 當管理員面板因太多重定向&#x200B;*錯誤無法存取*&#x200B;時，能修正問題。
* **MDVA-38270** （*用於 Adobe Commerce >=2.4.1 &lt;2.4.3*）— 修正了 GraphQL 訂單總額中缺少禮品卡資訊的問題。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** （*用於 Adobe Commerce >=2.4.2 &lt;=2.4.4*）- 修正了當網站 ID 與商店 ID 不符時，透過 GraphQL 將可設定產品加入購物車的問題。
* **MDVA-36832** （*用於 Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*）-修正了當視距為 768px 時頁面上圖片重複的問題。
* **MDVA-37874** （*用於 Adobe Commerce >=2.3.6 &lt;=2.3.7 ||=&quot;&quot;>=2.4.1 &lt;=2.4.2-p1*）- 修正 *了整車* 固定折扣金額錯誤套用於包含多個選項的組合產品的問題。&lt;/=2.3.7>
* **MDVA-37913** （*用於 Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*）- 修正了當可下載產品透過 API 更新時，連結會消失的問題。
* **MDVA-34330** （*用於 Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*）- 修正訂單網格中訂單未依管理時區篩選的問題。

## v1.0.23 {#v1-0-23}

* **MDVA-37478**（*用於 Adobe Commerce >=2.3.0*&lt;=2.3.7）— 修正了 Adobe Commerce 在透過 REST API 以帳戶&#x200B;*支付方式下單時，為部分*&#x200B;發票產生錯誤的問題。
* **MDVA-37362** （*用於 Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*）-修正了 GraphQL 回應中可設定產品選項值與變體屬性值為空的問題。
* **MDVA-37288** （*用於 Adobe Commerce 2.4.2*）-修正了 GraphQL 請求後退錯階級價格的問題。
* **MDVA-37225** （*用於 Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*）— 修正了在快速訂單建立時，當匯入 SKU 有整數值時，上傳流程卡住的問題。
* **MDVA-37224**（*用於 Adobe Commerce >=2.3.3*&lt;=2.4.2-p1）— 修正客戶無法用其他商品購買可轉價報價[!DNL PayFlow Pro]的問題。
* **MDVA-36286** （*用於 Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*）- 修正了頁面建置器產品小工具預覽在相同 SKU 子類別位置不同時會出問題。
* **MDVA-30186** （*用於 Adobe Commerce >=2.3.4 &lt;=2.3.5-p2,>=2.4.0 &lt;=2.4.0-p1,>=2.4.2 &lt;=2.4.2-p1*）- 修正 GraphQL 回應中屬性選項依選項值排序，而非屬性項目數量的問題。&lt;/=2.4.0-p1,>&lt;/=2.3.5-p2,>

## v1.0.22 {#v1-0-22}

* **MDVA-36718** （*用於 Adobe Commerce >=2.3.0 &lt;=2.4.2*）— 修正了舊自訂選項在透過 API 更改後仍保留的問題。
* **MDVA-35773** （*用於 Adobe Commerce >= &lt;=2.3.6-p1 ||=&quot;&quot;>2.3.6 =2.4.1 &lt;=2.4.2*）— 修正了訂單 100% 折扣時，總計未顯示為零的問題。&lt;/=2.3.6-p1>
* **MDVA-36833** （*用於 Adobe Commerce 2.4.2*）— 修正在排除共享目錄中某些產品後，搜尋結果顯示每頁產品數量隨機的問題。
* **MDVA-37182**（*用於 Adobe Commerce >=2.4.1*&lt;=2.4.2）— 修正了版本 6 和 7 中搜尋結果[!DNL Elasticsearch]錯誤的問題。
* **MDVA-36253** （*適用於 Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*）- 修正了刪除項目後迷你購物車中出現錯誤小計的問題。
* **MDVA-36853** （*用於 Adobe Commerce 2.4.2*）— 修正載入大型媒體圖庫時圖片不會出現的問題。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*適用於Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修正類別頁面上遺失套件產品的問題。
* **MDVA-36615** (*適用於Adobe Commerce 2.4.2*) — 修正Admin產品格線中產品計數不正確的問題。
* **MDVA-36464** (*適用於Adobe Commerce >=2.4.0 &lt;=2.4.2*) — 修正電子郵件通知設定在存放區檢視層級無法運作的問題。
* **MDVA-36138** (*適用於Adobe Commerce ^2.3.2*) — 修正未調整送貨價格，且購物車中並非所有專案都符合免運費購物車規則時，向客戶顯示完整送貨價格的問題。
* **MDVA-36424** （*用於 Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 ||=&quot;&quot;>=2.0.0 &lt;2.2.0*）- 修正當內容反覆編輯時，若後端基礎 URL 與商店底線 URL 不同，附帶於頁面建構元素的媒體影像會消失的問題。&lt;/=2.3.3-p1>
* **MDVA-35984** （*用於 Adobe Commerce ^2.4.0*）- 修正在同一產品建立多次同時出貨後，商品數量與可銷售數量錯誤的問題。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** （*用於 Adobe Commerce >=2.3.4 &lt;2.4.2*）- 此工具解決了 GraphQL 查詢未透過類別快取標籤快取的問題。
* **MDVA-33168** （*用於 Adobe Commerce >=2.3.3 &lt;2.4.2*）- 修正透過 API 更新產品屬性時，其他屬性會改為空值的問題。
* **MDVA-19640** （*用於 Adobe Commerce >=2.3.0*）- 修正 [!DNL Advanced Reporting] 了無法顯示任何資料的問題。
* **MDVA-11189**（*用於 Adobe Commerce >=2.3.0*&lt;2.3.5）-修正匯入 CSV 檔案更新產品庫存後，表格中的資料`cataloginventory_stock`列會被刪除的問題。
* **MDVA-26639** （*用於 Adobe Commerce >=2.3.3-p1 &lt;2.3.6*）— 修正了如果建立新的訂單確認郵件範本，訂單郵件中缺少訂單項目的問題。
* **MDVA-15546** （*用於 Adobe Commerce >=2.3.0*）- 修正了建立訂單 *後，例外日誌中子句為歧義* 欄位entity_id錯誤的問題。
* **MDVA-21095**（*用於 Adobe Commerce >=2.3.0*&lt;2.3.5）- 修正`INSERT INTO search_tmp`查詢在大規模屬性值更新後無法結束的問題。
* **MDVA-23845** （*用於 Adobe Commerce >=2.3.2-p2 &lt;2.3.5*）— 修正啟用 JavaScript 壓縮後，電子郵件範本無法預覽的問題。
* **MDVA-22026** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正從CSV檔案匯入產品（包括來自外部URL的影像）失敗的問題。
* **MDVA-22383** （*用於 Adobe Commerce >=2.3.0 &lt;2.3.4*）— 修正儲存產品耗時久且頁面斷裂的問題。
* **MC-41359** （*用於 Adobe Commerce >=2.3.6-p1 &lt;2.3.7,>=2.4.2 &lt;2.4.3*）-修正 SameSite cookie 參數設定錯誤的問題。&lt;/2.3.7,>

## v1.0.19 {#v1-0-19}

* **MDVA-33614** （*用於 Adobe Commerce 2.4.1*）- 修正頁面建構器會跳出以下錯誤的問題： *啟動頁面建置器時發生錯誤。 請諮詢您的技術支援聯絡人。*
* **MDVA-35356** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.3*）- 修正部分發票訂單取消後商店信用退還錯誤的問題。
* **MDVA-33289（用於 Adobe Commerce >=2.4.0&lt;2.4.3**）- 修正結帳時帳單地址介面中顯示原始 JavaScript 程式碼的問題，若啟用此功能&#x200B;*。*[!DNL Google Tag Manager]
* **MDVA-35982** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.3*）— 修正了管理員用戶無法為同一網站上的訂單建立出貨問題。
* **MDVA-35155** （*用於 Adobe Commerce >=2.3.0 &lt;2.3.6*）— 修正了若選項標題更改，無法購買組合產品的問題。
* **MDVA-35910** （*用於 Adobe Commerce >=2.4.1 &lt;2.4.3*）- 修正在停用「以客戶身份登入」功能後，無法建立新客戶帳戶的問題。
* **MDVA-34474** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正使用API將產品新增至請購單清單的問題。
* **MDVA-34591** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正&#x200B;*套用到*&#x200B;的最大數量折扣與&#x200B;*折扣數量步驟（購買X）*&#x200B;的購物車規則折扣計算不正確的問題。
* **MDVA-33704** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修正&#x200B;*在商店取貨*&#x200B;配送選項未顯示的問題，儘管已設定為可用。
* **MDVA-34928** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修正將商店評分從付款中移除後，頁面載入器會無限期顯示的問題。
* **MDVA-35254** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正簽出期間驗證碼的問題。
* **MDVA-35569** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正指定狀態時，GraphQL回應中未填入&#x200B;*已修正產品稅捐*&#x200B;欄位的問題。
* **MDVA-35847** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修正使用自訂客戶屬性時公司使用者表單中斷的B2B問題。
* **MDVA-31307** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正某些類別上因快取區塊的動態CSP白名單發生問題而出現&#x200B;*記憶體不足*&#x200B;錯誤的問題。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 刪除數個產品後，將消費者&#x200B;*的不正確*&#x200B;進行中&#x200B;*訊息狀態修正為正確的*&#x200B;完成`quoteItemCleaner`訊息。
* **MDVA-34102** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正「產品網格」和「管理」區域之「編輯產品」頁面上已停用產品的預設庫存量為零。
* **MDVA-35286** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正客戶在購物車中捆綁產品，並從多個地址簽出切換為單一頁面簽出時發生錯誤的問題。
* **MDVA-35312** (*適用於Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) — 修正空白GraphQL請求時的回應代碼500。
* **MDVA-34189** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修正載入「管理類別」頁面時，[!DNL Visual Merchandiser]個查詢的503個第一位元組逾時問題。
* **MDVA-34695** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1*) — 刪除類別後修正負值`children_count`。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修正套用排程變更後，*使用預設值*&#x200B;核取方塊被清除的問題。 一旦排程的變更不再有效，問題就會出現。
* **MDVA-35064** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修正無法透過API建立的可設定產品產生URL重寫的問題。
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
* **MDVA-34023** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修正錯誤&#x200B;*沒有這類具有addressId*&#x200B;的實體在訪客的瀏覽器上隨機顯示的問題。
* **MDVA-32759** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.3 （含B2B擴充功能*）) — 修正共用目錄刪除現有層級定價的問題。
* **MDVA-33482** (*用於Adobe Commerce ^2.3.5*) — 修正針對部份商業發票產生「銷退折讓單」，導致對訂單總額計稅，而非該部份商業發票計稅的問題。
* **MDVA-33393** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正錯誤&#x200B;*所提供的國家/地區ID不存在*。
* **MDVA-33632** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.7*) — 提供例外狀況訊息&#x200B;*此產品無庫存*&#x200B;的修正，現在會在嘗試重新訂購無庫存產品時向管理員使用者顯示。
* **MDVA-34469** (*適用於Adobe Commerce >=2.4.1 &lt;2.4.2*) — 修正使用多個商店檢視時，客戶購物車上GraphQL突變失敗的問題。
* **MDVA-33976** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修正從套件產品移除第二個選項後，套件組合產品在店面無存貨顯示的問題。
* **MDVA-33894** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1 （含B2B擴充功能*）) — 修正快速訂購功能的多個問題，包括新增和移除多個產品以及SKU區分大小寫。
* **MDVA-27664** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正客戶登錄檔單中造成錯誤顯示的問題： *錯誤 — 出生日期不應晚於今天。*
* **MDVA-33970** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正當價格屬性的範圍設定為網站時，銷退折讓單中有錯誤貨幣符號的問題。
* **MDVA-33992** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正結帳時B2B特殊價格顯示不正確的問題。
* **MDVA-34100** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2 （具有B2B擴充功能）*) — 修正無法從公司結構頁面建立公司帳戶的問題。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5， >=2.4.0 &lt;2.4.2*) — 修正從CSV檔案匯入產品後重複影像的問題。
* **MDVA-33382** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正從類別移除產品後，索引子失效的問題。
* **MDVA-28511** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修正「名稱」欄位包含特定字元（如重音大寫字母）時，無法完成[!DNL PayPal]結帳的問題。
* **MDVA-31519** (*適用於Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修正使用全網站銷售規則時，訪客結帳中的等待逾時問題。
* **MDVA-33281** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修正`inventory:reservation:list-inconsistencies`中由於SKU引數型別錯誤而發生嚴重錯誤的問題。
* **MDVA-24201** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正價格在手動重新編列索引前無法反映排程購物車價格規則的問題。
* **MDVA-32694** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修正管理員使用者無法將產品新增至可轉讓報價單（如果產品與非預設商店有關）的問題。
* **MDVA-33516** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修正編輯請購單清單中的套件組合產品導致錯誤的問題。
* **MDVA-33975** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正GraphQL要求中有關價格計算的多個問題。

## v1.0.13 {#v1-0-13}

* **MDVA-30858**（*用於 Adobe Commerce >=2.3.0&lt;2.4.2*）— 修正[!DNL PayPal]了結算報告無法如預期在&#x200B;**銷售報告**> **&#x200B;**&#x200B;結算>**[!DNL PayPal]**&#x200B;中提供的問題。
* **MCP-87** （*用於 Adobe Commerce >=2.3.1 &lt;2.4.2*）- 改善大型投資組合類別產品及股票索引器的索引時間。
* **MDVA-33106** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正執行cron `run`命令後清除重新排程產品變更的問題。
* **MDVA-19391** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修正`analytics_collect_data`因`catalog_category_entity_text`表格中有NULL描述記錄而發生錯誤的問題。
* **MDVA-20376** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正訂單放置後登入客戶在&#x200B;*中*&#x200B;沒有具有customerId = 1`exception.log`的這類實體錯誤的問題。
* **MDVA-23764（用於 Adobe Commerce >=2.3.2&lt;2.3.5**）-修正影響動態區塊顯示的錯誤&#x200B;*。*`JsFooterPlugin.php`
* **MDVA-13203**（*用於 Adobe Commerce >=2.3.0*&lt;2.4.2）- 修正&#x200B;*完整重新索引後出現完整性約束違規search_tmp_*&#x200B;表格錯誤的問題。
* **MDVA-23426** （*用於 Adobe Commerce >=2.3.3 &lt;2.3.5*）-修正 Adobe Commerce 發送的通知郵件中包含空白正文且內容被附加為附件的問題。
* **MDVA-22150** （*用於 Adobe Commerce >=2.3.1 &lt;2.3.4*）- 修正了客戶在購物車中有可設定產品且套用優惠券，若該產品在管理員中被停用，無法登入的問題。
* **MDVA-32545** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.2*）- 修正管理員建立訂單時發票不會自動寄出的問題。
* **MDVA-32714** （*用於 Adobe Commerce >=2.3.4 &lt;2.4.1*）— 修正了 GraphQL 產品查詢中客戶群組價格無法運作的問題。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*適用於Adobe Commerce >=2.3.2 &lt;2.4.2*) — 新增&#x200B;*小計(包括 稅捐)*&#x200B;價格規則條件的選項。
* **MDVA-31236** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修正具有自訂資源存取權的管理員無法設定2FA或登入的問題。
* **MDVA-30845（用於 Adobe Commerce >=2.3.5&lt;2.3.7**）-修正了當無法連接 UPS XML/USPS/DHL 且無法使用其他運送方式時，會出現「抱歉，目前訂單無法提供&#x200B;*報價」的錯誤*。**
* **MDVA-32133** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正某些情況下無法從頁面產生器載入媒體集的問題。
* **MDVA-12304** （*用於 Adobe Commerce >=2.3.0*）- 將最大 Cookie 數量從 50 個增加到 200 個。
* **MDVA-32632** （*用於 Adobe Commerce >=2.3.2 &lt;2.3.5*）- 修正訂單出現在支付系統，但 Adobe Commerce 中沒有的問題。
* **MDVA-32449** （*用於 Adobe Commerce >=2.3.0 &lt;2.3.6 ||=&quot;&quot; 2.4.0=&quot;&quot; ||=&quot;&quot;>=2.4.1 &lt;2.4.2 with B2B extension*）— 修正訂單歷史載入非常緩慢或完全無法載入的問題。&lt;/2.3.6>
* **MDVA-32739** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.2*）- 修正啟用非同步電子郵件通知時寄出舊銷售郵件的問題。

## v1.0.11 版本 {#v1-0-11}

* **MC-38509**（*適用於 Adobe Commerce 2.3.6、2.4.1*）— 修正&#x200B;*了在「建立新客戶帳戶*」表單中修正無效資料&#x200B;*後，建立帳戶*&#x200B;按鈕仍保持停用的問題。
* **MDVA-31006** （*適用於 Adobe Commerce 2.3.0、2.3.1*）— 修正了下 [!DNL Paypal Express] 單後出現重複訂單的問題。
* **MDVA-25602**（*用於 Adobe Commerce 2.3.0*）- 修正 Chrome 80 瀏覽器中支付方式及預設 cookie [!DNL PayPal Payflow Pro] 處理的問題`SameSite=Lax`，以及 API 回應會導向至客戶登入頁面。

## v1.0.10 {#v1-0-10}

補丁版本的小修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363**（*用於 Adobe Commerce >=2.3.2&lt;2.4.2*）— 修正了在使用 Fixed 金額折扣整車&#x200B;*行動時，GraphQL*&#x200B;中不適用購物車價格規則與優惠券的問題。
* **MDVA-30889** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.2*）— 修正在以虛擬及簡單產品為選項的套裝後，開票時發生錯誤的問題。
* **MDVA-31791** （*用於 Adobe Commerce >=2.3.4 &lt;2.3.5*）-在使用目標規則或連結產品時，提升產品頁面的效能。
* **MDVA-31168** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.2*）- 修正產品匯出 CSV 檔未出現且記憶體配置錯誤的問題。
* **MDVA-32313** （*用於 Adobe Commerce >=2.3.0 &lt;2.3.4*）- 修正了可設定產品可能因設定選項錯誤而被加入願望清單的問題。
* **MDVA-31759** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.2*）— 修正了 CSV 匯入時產品未更新下 *拉選單* 和 *textarea* 屬性值的問題。
* **MDVA-32012** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.2*）- 修正韓國與阿根廷郵遞區號無法驗證的問題。
* **MDVA-31640** （*用於 Adobe Commerce >=2.3.1 &lt;2.3.6 ||=&quot;&quot;>=2.4.0 &lt;2.4.1*）— 修正無法透過 REST API 更新特殊價格的問題。&lt;/2.3.6>
* **MDVA-28651** （*用於 Adobe Commerce >=2.3.0 &lt;2.3.6 ||=&quot;&quot;>2.4.0 及 B2B 擴充）*— 修正透過 REST API 載入可協商報價時的效能問題。&lt;/2.3.6>

## v1.0.8 {#v1-0-8}

* **MDVA-31242** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.1 with B2B extension*）- 修正信用備忘錄格中顯示錯誤貨幣符號的問題。
* **MDVA-31295** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正部分訂單完成且專案徵稅時未計算獎勵點數的問題。
* **MDVA-30112** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正若訂購數量超過&#x200B;*bunch-size*&#x200B;值，Adobe Commerce會將狀態為&#x200B;*擱置*&#x200B;的訂購視為不一致的問題。
* **MDVA-31150** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正GET Invoice Rest API呼叫未傳回商店信用卡與禮品卡餘額的問題，當商業發票以Rest API呼叫過帳且訂單部份由商店信用卡與禮品卡帳戶支付時。
* **MDVA-30963** (*適用於Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修正產品篩選結果集僅包含為Admin中的&#x200B;*所有商店檢視*&#x200B;範圍指定的值，且包含已在商店檢視層級上覆寫值的產品的問題。
* **MDVA-29954** (*適用於Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2含B2B副檔名*) — 修正&#x200B;*新公司註冊要求*&#x200B;與&#x200B;*您已連結至公司*&#x200B;電子郵件傳送錯誤地址的問題。
* **MDVA-28357（用於 Adobe Commerce >=2.3.2 &lt;2.3.6 ||=&quot;&quot;>=2.4.0&lt;2.4.1**）-以自訂分析器取代標準分析器，並針對索引中 SKU 欄位&#x200B;*的關鍵字分詞器，使通配字搜尋查詢能與包含連字號（“-”）的 SKU 相容。&lt;/2.3.6>*[!DNL ElasticSearch]

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正使用WebApi建立部分出貨後，自訂訂單狀態變更為&#x200B;*處理*&#x200B;的問題。
* **MDVA-30428** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修正當此產品已指派給自訂詳細目錄來源時，客戶無法新增產品至願望清單的問題。
* **MDVA-30594** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正設定FPT時，無法在結帳期間儲存含有多個位址之訂單的問題。
* **MDVA-29148** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正透過API呼叫建立產品時的問題，如果承載中未提供任何值，則`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如Multiselect）型別的產品自訂屬性不會使用其預設值。
* **MDVA-30837** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.5*) — 已在免運費方法組態中新增組態設定&#x200B;*包含稅金至金額：是/否*。 當&#x200B;*含稅金額*&#x200B;設定為&#x200B;*是*&#x200B;時，最小訂購金額會以小計+稅捐計算。 當&#x200B;*含稅金額*&#x200B;設定為&#x200B;*否*&#x200B;時，最小訂購金額會以小計計算
* **MDVA-25028** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) — 修正觸發欺詐篩選時，使用[!DNL PayPal Payflow Pro]下訂單未設定為疑似欺詐狀態的問題。
* **MDVA-31224** (*適用於Adobe Commerce >=2.3.3 &lt;2.3.5*) — 改善套件組合產品之`catalog_product_price`重新索引作業的效能。
* **MDVA-31321** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修正選取&#x200B;*全部顯示*&#x200B;時的空白頁面（錯誤）。 [!DNL Elasticsearch]會傳回大量的產品ID清單。 在此案例中，order by子句會轉換為不正確的SQL格式。
* **MDVA-30815** (*適用於Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修正當您變更搜尋結果頁面上應顯示的搜尋結果數目時，Adobe Commerce會顯示空白頁面的問題。 當您變更每頁檢視的搜尋結果數目時，[!DNL Elasticsearch]現在可以正確顯示類別頁面的結果。
* **MDVA-30782** (*適用於Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修正不論購物車規則為何，都會顯示動態區塊的問題。
* **MDVA-31021** (*用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正`module-catalog-import-export/Model/Import/Product/Option.php`中存在效能問題的問題。 如果`catalog_product_option`表格中有超過~100k筆記錄，則含有單一產品的新CSV需要少於10秒的驗證時間。
* **MDVA-31007** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正自訂地址屬性未正確顯示在我的帳戶區域和後端的訂單詳細資訊頁面中的問題。
* **MDVA-29389** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正進階報告的問題，其中`analytics_collect_data` cronjob指出： *連線埠必須在主機引數（例如localhost:3306）中設定*。
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

* **MDVA-30841** (*適用於Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修正分層導覽的問題，其中若將&#x200B;*當做搜尋引擎使用，則布林值型別產品屬性的* No[!DNL Elasticsearch]值不會包含在分層導覽中。
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
* **MDVA-28661** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2 （含B2B擴充功能）*) — 修正公司管理員變更後，「公司使用者」公司帳戶區段中擲回錯誤的問題。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*適用於Adobe Commerce 2.3.1 - 2.3.4-p2*) — 修正資料庫名稱太長時cron工作失敗，導致前端未更新類別的問題。
* **MDVA-30106** (*用於Adobe Commerce ^2.3.0*) — 修正結帳付款期間未載入&#x200B;*無法讀取JS主控台中null為*&#x200B;之屬性「長度」錯誤的問題。
* **MDVA-28656** (*適用於Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) — 修正下列問題：如果下訂單時不需要付款資訊（例如，有100%折扣），且已建立訂單發票，則訂單狀態會變更為&#x200B;*已關閉*，而非「完成」。
* **MDVA-30209** (*適用於Adobe Commerce 2.3.0 - 2.3.3-p1*) — 修正客戶更新其帳戶資訊時，客戶群組變更為預設的問題。
* **MDVA-30123** (*適用於Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修正GraphQL查詢的屬性選項標籤未正確轉譯的問題。
* **MDVA-29996** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修正啟用類別許可權後，類別頁面無法由完整頁面快取快取的問題。
* **MDVA-30164** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修正存在自訂客戶屬性時無法從客戶格線匯出客戶記錄的問題。
* **MDVA-30444** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修正使用GraphQL下訂單時未傳送確認電子郵件的問題。
* **MDVA-30490** (*適用於Adobe Commerce 2.3.4 - 2.3.5-p2*) — 修正當其中一個產品的簡短描述空白時，產品比較會擲回500錯誤頁面的問題。
* **MDVA-30232** (*適用於Adobe Commerce >=2.3.1 &lt;2.4.1*) — 修正原始訂單包含禮品卡時無法重新訂購的問題。
* **MDVA-29965** (*適用於Adobe Commerce >=2.3.3 &lt;2.4.0*) — 修正客戶將產品新增至購物車時，收到「無效表單金鑰」錯誤的問題。
* **MDVA-30008** (*適用於Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修正無法透過管理應用程式開發介面為公開目錄中的產品下單的B2B問題。
* **MDVA-22469** (*適用於Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) — 修正升級至Adobe Commerce 2.3.3後，頁面產生器在「管理」面板中無法運作以及部分JS和CSS檔案無法載入的問題。
* **MC-35984** (*適用於Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修正商家為退貨授權(RMA)建立運送標籤後，無法與退貨頁面上的任何頁面元素互動的問題。

## v1.0.3 版本 {#v1-0-3}

* **MDVA-25602**（*適用於 Adobe Commerce 2.3.0 - 2.3.4*）- 修正支付方式及 Chrome 80 瀏覽器預設對 Cookie [!DNL PayPal Payflow Pro] 處理的問題`SameSite=Lax`，API 回應會導向客戶登入頁面。
* **MDVA-26694** （*用於 Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*）— 修正產品與目錄快取每日過期的問題，但其過期排程不同。
* **MDVA-27825** （*用於 Adobe Commerce >=2.3.0 &lt;2.4.1*）— 修正了因記憶體洩漏導致大量資料匯出失敗的問題。
* **MDVA-29085** （*用於 Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*）- 修正 B2B 問題，即若公司由 API 建立，則不會發送新郵件。
* **MDVA-29344** （*用於 Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*）-修正頁面建構器在將標題元素的文字複製到文字元素後卡住的問題。
* **MDVA-29835** （*用於 Adobe Commerce >2.3.1 &lt;2.4.2*）-修正禮品卡訂單中包含兩個代碼而非一個的問題。
* **MDVA-30052** （*用於 Adobe Commerce >=2.3.2-p2 &lt;2.3.5*）— 修正了私有內容（本地儲存）未正確填入、導致效能問題的問題。
* **MDVA-30131**（*用於 Adobe Commerce >=2.3.4*&lt;2.3.6 || 2.4.0）- 修正分層導覽的問題，若&#x200B;*用作搜尋引擎，*&#x200B;則布林型產品屬性的 No[!DNL Elasticsearch] 值未包含在分層導覽中。
* **MDVA-35514** （*用於 Adobe Commerce >=2.4.0 &lt;2.4.1*）- 修正在「建立包裹」模態視窗中建立運送標籤及將訂購商品加入包裹的問題。
