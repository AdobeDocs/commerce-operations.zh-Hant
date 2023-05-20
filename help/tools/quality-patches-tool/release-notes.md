---
title: 發行說明
description: 瞭解Adobe Commerce可用的修補程式及其解決的問題。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 205a0b67fab14a313d28355eed668d60ce477e64
workflow-type: tm+mt
source-wordcount: '12066'
ht-degree: 0%

---

# 發行說明

的 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source社區開發的各個修補程式。 它允許您應用、還原和查看有關可用於已安裝版本的Adobe Commerce或Magento Open Source的所有單個修補程式的一般資訊。 您可以將修補程式應用於Adobe Commerce和Magento Open Source項目，而不管是誰開發了該修補程式。 例如，您可以將社區開發的修補程式應用到Adobe Commerce項目。

>[!INFO]
>
>請參閱 [應用修補程式](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) 有關將修補程式應用到您的Adobe Commerce或Magento Open Source項目的說明。 請參閱 [[!DNL Quality Patches Tool]:搜索修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 查看已發佈修補程式的完整清單。

>[!INFO]
>
>有關 [!DNL quality patches] 由社區建立以供Magento Open Source，請參閱 [發行說明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md)。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (適用於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) — 解決在提交失敗付款後Recaptcha v2未重新載入的問題。
* **ACSD-50817** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 優化Cron作業 `sales_clean_quotes` 跑得更快。
* **ACSD-49392** (適用於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) — 解決訂單狀態在捆綁產品部分退款後變為關閉的問題。
* **ACSD-51036** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 解決併發REST API調用期間的競爭條件導致覆蓋中發運狀態資訊的問題 [!UICONTROL Items Ordered] 的子菜單。
* **ACSD-50858** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 提高載入橫幅內容的效能。
* 已添加MDVA-39305-v2、ACSD-45169的新版本。
* 更新的修補程式ACSD-50260-v2。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (對於Adobe Commerce和Magento Open Source>=2.4.4-p1 &lt;2.4.4-p3) — 解決當產品退回庫存或價格更改時不會發送產品警報電子郵件的問題。
* **ACSD-50367** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決在建立無值的多選客戶地址屬性時客戶地址導出不起作用的問題。
* **ACSD-49877** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決視頻自動播放在移動設備上不起作用的問題 [!DNL Safari] 將視頻直接連結到遠程視頻檔案而不是流式服務時。
* **ACSD-50165** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修復錯誤 *無法刪除檔案。 警告！取消連結：沒有此類檔案或目錄* 從管理員中刷新JS/CSS快取時。
* **ACSD-49737** (對於Adobe Commerce和Magento Open Source>=2.4.1-p1 &lt;2.4.7) — 解決在支付卡失敗後將優惠券錯誤標籤為使用的問題。
* **ACSD-50814** (對於Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 解決管理員用戶無法建立貸項通知單的問題。
* **ACSD-50116** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決管理員用戶無法為子類別3級或更低級別建立URL重寫的問題。
* **ACSD-49513** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5) — 解決由於0位元組檔案導致遠程儲存同步失敗的問題。
* **ACSD-46683** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 解決發運價格顯示的問題 *尚未計算*。
* **ACSD-49129** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 解決 *[!UICONTROL content]* 屬性（base64映像代碼）未在中返回 `rest/V1/products/sku/media` 產品媒體API響應。
* **ACSD-50276** (對於Adobe Commerce>=2.4.0 &lt;2.4.7) — 如果建立了多選客戶屬性，則解決客戶註冊表在店面上不起作用的問題。
* **ACSD-50527** (對於Adobe Commerce>=2.3.7 &lt;2.4.7) — 修復保存具有空動態塊的頁面時發生的錯誤。
* **ACSD-49973** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 提高通過GraphQL讀取捆綁產品的效能。
* **ACSD-51114** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 解決啟用非同步索引時隨機產品從大型目錄中消失的問題。 提高大型目錄非同步重新索引的效能。
* **B2B-2598** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 向 [!UICONTROL availableStores]。 [!UICONTROL countries]。 [!UICONTROL country]。 [!UICONTROL currency], [!UICONTROL storeConfig] GraphQL。
* 已添加MDVA-42806、ACSD-48627、ACSD-46815的新版本。
* ACSD-49773、ACSD-47179、ACSD-48300的更新補丁程式元資料。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 解決訂單未準備好接收時，API發送準備接收電子郵件的問題。
* **ACSD-49822** (對於Adobe Commerce>=2.3.7 &lt;2.4.7) — 修復中更新的問題 [!UICONTROL Requisition List] 頁面沒有反映在 [!UICONTROL Print Requisition List]。
* **ACSD-48771** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 通過從舊版本升級列塊內容類型來解決問題 [!DNL Page Builder] 版本。
* **ACSD-49464** (對於Adobe Commerce>=2.3.7 &lt;2.4.7) — 在orderId不同時，解決發票、發運和貸項通知單未從存檔中移回的問題。
* **ACSD-49773** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 解決將AWSS3用作遠程儲存時產品出口失敗的問題。
* **ACSD-49748** (對於Adobe Commerce>=2.3.7 &lt;2.4.7) — 解決無法發送邀請的問題。
* **ACSD-49502** (對於Adobe Commerce>=2.4.3 &lt;2.4.7) — 修復在將暫存更新應用到可下載產品後無法正確更新可下載連結的問題。
* **ACSD-49527** (對於Adobe Commerce>=2.4.2 &lt;2.4.7) — 解決GraphQL公司角色無法正確顯示分頁的問題。
* **ACSD-49706** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決未選擇值時為可視色板屬性保存預設值的問題。
* **ACSD-49835** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 解決「使用預設值」複選框值未正確保存在多選屬性的儲存級別上的問題。
* **ACSD-49898** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 解決當捆綁產品的特殊價格超過1000時產品網格引發異常的問題。
* **ACSD-50234** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.5) — 如果訂單與 [!DNL PayPal]。
* **ACSD-49960** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 解決按日期篩選不適用於客戶訂單網格的問題。
* **ACSD-49849** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 解決將客戶電子郵件替換為 [!DNL PayPal] 下訂單時發送電子郵件 [!DNL PayPal Express] 通過GraphQL。
* **ACSD-49839** (對於Adobe Commerce>=2.3.7 &lt;2.4.7) — 解決當產品在SKU中有單引號或雙引號時，共用目錄定價和結構在Admin中引發錯誤的問題。
* **ACSD-49970** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修復GraphQL錯誤的錯誤處理 [!DNL New Relic] 報告已開啟。
* **ACSD-50260** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 解決GraphQL產品搜索結果僅限於10,000個結果的問題。
* **ACSD-48813** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 根據屬性的搜索權重，解決搜索未顯示相關結果的問題。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.3) — 解決基於「是/否」屬性建立的目錄價格規則未考慮選定範圍的問題。
* **ACSD-47704** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決捆綁產品僅顯示庫存產品價格的問題。
* **ACSD-49370** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決 *日期時間* product屬性具有 *篩選器匹配類型輸入* 在GraphQL架構中鍵入。
* **ACSD-48807** (對於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.7) — 通過GraphQL通過storeview解決客戶產品評論未篩選的問題。
* **ACSD-49433** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 解決在購物車中預設金額顯示為小計的具有開啟金額的禮品卡的問題。
* **ACSD-48866** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決在請求類別的RSS源時出錯的問題。
* **ACSD-48784** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決客戶組之間錯誤地快取客戶段價格的問題。
* **ACSD-48857** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修復用戶在使用頁面生成器編輯後無法保存更改的問題。
* **ACSD-49065** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 如果僅分配給自定義庫存，則解決在管理員中無法看到報價項的問題。
* **ACSD-49179** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 解決「訂單報表」在不同商店的不同幣種下顯示不正確金額的問題。
* **ACSD-49286** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 解決在頁面上存在多個產品小部件時將產品兩次添加到購物車的問題。
* **ACSD-49574** (對於Adobe Commerce>=2.4.4 &lt;2.4.7) — 添加功能以支援通過GraphQL的購物車中的禮品卡產品更新。
* 更新的修補程式：ACSD-48694

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (對於Adobe Commerce>=2.4.1 &lt;2.4.7) — 使用可轉讓報價下單時，解決使用預設發運地址而不是新地址的問題。
* **ACSD-48059** (對於Adobe Commerce>=2.3.7 &lt;2.4.7) — 解決商家無法保存「[!UICONTROL Match product by rule]的下界。
* **ACSD-48216** (適用於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) — 修復問題 [!UICONTROL AUTO_INCREMENT] 的 [!UICONTROL inventory_source_item] 表增加 [!UICONTROL UPDATE] 的下界。
* **ACSD-47908** (適用於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) — 在結帳期間在發運步驟上選擇來源和數量時，修復錯誤「A value is expected to 0」。
* **ACSD-49497** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 解決訂單在發運後仍處於處理狀態且應用部分退款的問題。
* **ACSD-48694** (適用於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) — 解決「請求無效狀態更改」錯誤導致客戶無法下訂單的問題。
* **ACSD-49013** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 使用批量API建立客戶時，解決電子郵件確認未翻譯到網站區域設定的問題。
* **ACSD-48164** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決受限管理員無法保存網站級值的問題。
* **ACSD-48404** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 解決按瀏覽器的後退按鈕時「記住類別分頁=是」導致錯誤的問題。
* **ACSD-48634** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 在「」時在臨時更新頁上修復JS錯誤[!UICONTROL Google Analytics Content Experiments]」。
* **ACSD-49042** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 解決無法從Storefront訂購具有無限背訂單的產品的問題。
* 更新的修補程式：ACSD-48366, ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (Adobe Commerce和Magento Open Source2.4.4 || >=2.4.5 &lt;2.4.6) — 解決因應用程式級快取而並不總是發送降價通知的問題。
* **ACSD-48661** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決以下問題：如果公司的信用限額大於999，則逗號分隔符會因驗證錯誤而阻止公司保存。
* **ACSD-48773** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 解決獎勵積分電子郵件模板從錯誤儲存中取出的問題。
* **ACSD-48587** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 解決在產品小部件匹配規則中HTML特殊字元阻止它們顯示匹配產品的問題。
* **ACSD-48212** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 解決產品導入將產品分配給錯誤來源的問題。
* **ACSD-47988** (對於Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修復產品導出從頁面生成器產品說明中刪除HTML標籤的問題。
* **ACSD-48366** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 解決產品影像未顯示在「退貨至股票」電子郵件模板上的問題。
* **ACSD-48417** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修復在為產品建立計畫更改並保存其他產品後出現SQL錯誤的問題。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 解決如果捆綁產品未分配給任何網站，則產品價格重新索引無效的問題。
* **ACSD-48262** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 當「允許每頁所有產品」設定設定為「是」時，解決在前端看不到產品的問題。
* **ACSD-48293** (對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4) — 解決當已售出的子產品退回庫存時複合產品庫存不足的問題。
* **ACSD-47520** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決建立貸項通知單時客戶損失獎勵積分的問題。
* **ACSD-48044** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 解決將多個禮品卡應用到具有多發運的單個訂單時，無法下訂單的問題。
* **ACSD-48300** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決在刪除可配置產品時無法建立返回的問題。
* **ACSD-47910** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 在各實體網格中修復丟失訂單、發票、發運和貸項通知單的發放。
* **ACSD-47292** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 如果「顯示缺貨產品」設定為「是」，則解決在GraphQL響應中無法提供缺貨產品的問題。
* **ACSD-48234** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 解決啟用「顯示缺貨」選項時目錄搜索結果顯示不正確類別物料計數的問題。
* **ACSD-48313** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 如果屬性值包含逗號，則解決不分析&quot;configurable_variations&quot;列的問題。 「additional_attributes」使用相同的分析算法。
* **ACSD-48627** (對於Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 解決在發送GraphQL請求以獲取購物車詳細資訊時庫存不足的可配置產品導致錯誤的問題。
* 更新的修補程式：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 解決沒有為具有SEO友好URL的產品生成SEO友好URL的問題 *url_key* 在儲存視圖級別上覆蓋的屬性。
* **ACSD-46865** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 解決啟用非同步索引時未填充發運和貸項通知單網格的問題。
* **ACSD-47004** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 解決未將增值稅應用於沒有增值稅ID的帳單地址的問題。
* **ACSD-47803** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決可配置產品庫存不足的色板顯示為可用的問題。
* **ACSD-47137** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 當pub/media資料夾非常大時，可提高影像庫的載入速度。
* **ACSD-46770** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決即使在 *電子郵件訂單確認* 複選框。
* **ACSD-47955** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 解決GraphQL未正確顯示購物車折扣的問題。
* **ACSD-46617** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決 *繼續簽出* 即使小計大於配置的值，該按鈕也會呈灰色 *最小訂單金額*。
* **ACSD-47079** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 解決當子產品庫存狀態通過REST APIPOST/rest/V1/inventory/source-items更改時未更新複合產品（捆綁、分組和可配置）庫存狀態的問題。
* **ACSD-47336** (用於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修復 *出了問題。* 在Commerce Admin中撤消通知時出錯。
* **ACSD-47559** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決「預覽電子郵件模板」區域不完全可見的問題。
* **ACSD-47920** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決可以通過Rest API作為來賓用戶下訂單的問題，即使在 *允許來賓簽出* 關閉。
* 已更換的修補程式：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決對特定範圍具有限制訪問權限的管理員無法刪除產品審查的問題。
* **ACSD-47107** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5) — 解決將目錄價格規則折扣應用於定制產品選項的問題。
* **ACSD-47232** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決無法在管理員中應用具有總重量條件的優惠券的問題。
* **ACSD-46519** (對於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6) — 解決GraphQLcategoryList請求返回錨點類別的不正確product_count的問題。
* **ACSD-47027** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修復緩慢的updateCompanyRoleGraphQL請求。
* **ACSD-47666** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決篩選器功能在「管理」>「系統」>「權限」>「用戶角色」>「角色」>「角色用戶」網格中不能正常工作的問題。
* **ACSD-47497** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決「Admin（管理）」下「Configuration（配置）」中「Services（服務）」頁籤不可見的問題。
* 更新的修補程式：ACSD-47743
* 已更換的修補程式：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3) — 修復 _嘗試訪問類型bool的值上的陣列偏移_ 訪問PHP 7.4上已知產品的某些非現有類別路徑時出錯。
* **ACSD-47332** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修復cron失敗的問題，該錯誤僅在運行00:00到00:59 UTC之間時報告。
* **ACSD-47280** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決在特定作用域上禁用共用目錄功能無法正常工作的問題。
* **ACSD-47106** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 解決無法將值保存在公司建立頁面上的新自定義屬性中的問題。
* 更新的修補程式：ACSD-45143

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 解決分配大量產品源時用戶出錯的問題。
* **ACSD-46856** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 通過「系統」>「配置」>「導入」>「高級定價」改進效能更新層價格。
* **ACSD-46541** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修復管理員用戶在刪除訂單項時無法建立貸項通知單的問題。
* **ACSD-46581** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決在選擇購物車中的國家/地區後未更新估計稅總額的問題。
* **ACSD-46618** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決產品清單構件顯示登錄客戶的錯誤快取價格的問題。
* **ACSD-46674** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 解決在客戶電子郵件中將映像類型的自定義選項顯示為HTML的問題。
* **ACSD-46988** (對於Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 解決GraphQL「currency」 API請求返回自定義貨幣的NULL值的問題。
* **ACSD-47076** (對於Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5) — 解決無法在店面播放Vimeo視頻的問題。
* **ACSD-45071** (對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4) — 解決在導入期間將預設源添加到產品中的問題。
* **AC-3023** (對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 將DHL方案更新為最新版本10.0。
* 更新的修補程式：MDVA-42584。
* 已更換的修補程式：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 解決用戶在使用商店信用退款時獲得錯誤訂單狀態的問題。
* **ACSD-46703** (*Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 解決無法在產品編輯頁面上拖放自定義選項的問題。
* **ACSD-44851** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 修復具有子類別的類別無法開啟或展開的問題。
* **ACSD-46815** (*Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6*) — 解決類別樹請求限制為20個類別的問題。
* **ACSD-45675** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 解決產品導出使用類別名稱的問題 *預設儲存視圖* 範圍。
* **ACSD-46869** (*Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 解決無法通過 *PUTREST API* 請求，而不更改產品數量。
* **MDVA-42768-V2** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 解決可配置產品將常規價格顯示為 *0* 何時 *顯示庫存不足* 是 *是*。
* 更新的修補程式：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 不建議使用的修補程式：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 解決類別樹請求限制為20個類別的問題。
* **ACSD-45781** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.2*) — 解決移動上未顯示儲存前搜索欄位的問題。
* **ACSD-46192** (*Adobe Commerce和Magento Open Source>=2.3.6 &lt;2.4.5*) — 使用 `async/bulk/V1/configurable-products/bySku/options` 端點。
* **ACSD-46404** (*Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修復管理員用戶在升級到2.4.4後無法登錄的問題。
* 更新的修補程式：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 解決特定商店的GraphQL產品變異返回所有可配置變型的問題，包括未分配給請求商店的變型。
* **ACSD-46146** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修復在向管理員下訂單後發送兩封訂單確認電子郵件的問題。
* **ACSD-45255** (*Adobe Commerce>=2.4.3 &lt;2.4.6*) — 修復受限管理員用戶的「Low Stock Report（低庫存報告）」頁上的異常。
* **ACSD-45488** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6*) — 解決不能自動將具有多個來源的可配置產品返回到庫存的問題。
* **ACSD-45754** (*Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 解決在將優惠券應用到購物車後未添加獎勵積分的問題。
* **ACSD-45849** (*Adobe Commerce>=2.4.3 &lt;2.4.4*) — 修復在應用轉移更新後丟失視頻元資料的問題。
* **ACSD-45257** (*Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 解決GraphQL無法正確顯示購物車折扣的問題。
* **ACSD-44938** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 解決問題的位置 `VAT_ID` 無法應用於來賓用戶的GraphQL請求。
* 更新的修補程式：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修復建立貸項通知單後虛擬產品庫存數量計算錯誤的問題。
* **ACSD-43887** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 解決啟用公司採購訂單時，結帳付款頁上顯示不正確詳細資訊的問題。
* **ACSD-45143** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修復問題 `setShippingAddressesOnCart` 突變不允許將數字區域代碼設定為 *區域*。
* **ACSD-44591** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6*) — 修復在未確認驗證碼的情況下下訂單時發生的錯誤。
* **ACSD-45520** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修復當用戶從購物車編輯可配置產品時，未在產品詳細資訊頁面上預選樣本選項的問題。
* **ACSD-45169** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6*) — 解決問題的位置 [!DNL Visual Merchandiser] 應用登台更新後，不顯示可配置產品的正確庫存和價格。
* **ACSD-45424** (*Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.6*) — 解決在部分退款（貸項通知單）後建立不正確的保留補償的問題。
* **MDVA-42807** (*Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修復商店前面未顯示自定義貨幣符號的問題。
* 更新的修補程式：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 解決訂單報告中對受限管理員用戶的訂單合計計算錯誤的問題。
* **MDVA-44940** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修復從Admin中保存類別時發生的SQL錯誤。
* **MDVA-44562** (*對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2-p2*) — 解決以下問題：儘管GraphQL請求源於非預設儲存視圖，但報價項的非預設儲存ID仍被預設儲存ID覆蓋。
* **MDVA-43167** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 解決管理員用戶選擇所有訂單時管理員訂單網格成批操作不適用於多頁的問題。
* **MDVA-44044** (*對於Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.2-p2*) — 修復產品在分配給新網站後未顯示在類別頁面上的問題。
* **MDVA-42509** (*Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.4*) — 修復無法上載CSV以快速訂購導致 *無法發送Cookie* 錯誤。
* 更新的修補程式：MDVA-41061、MDVA-42584。
* 新的前置詞 [!DNL Quality Patches Tool] 修補程式將從 *MDVA* 至 *ACSD* 由於內部流程更改。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 解決在購物車中已存在最小數量的購物車中無法添加附加物料的問題。
* **MDVA-44887** (*Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修復 *未捕獲的語法錯誤：意外標籤「const」* 「管理」面板中出錯。
* **MDVA-43718** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修復 *使用者無權訪問%resources。* 從自定義整合訪問共用目錄時出現的錯誤。
* **MDVA-44660** (*對於Adobe Commerce和Magento Open Source>=2.4.2-p1 &lt;2.4.5*) — 修復嚴重強調字元的問題 ``` ` ``` 不能用於客戶的姓和姓。
* **MDVA-40896** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修復 *錯誤：類型錯誤：參數3傳遞給Magento* 非同步產品批量API中出錯。
* **MDVA-38559** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修復 */V1/customers/search API* 具有多個訂閱的客戶出錯。
* **MDVA-44533** (*Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.4*) — 解決將折扣錯誤應用到捆綁包子產品的問題。
* 更新的修補程式：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 解決產品 *不單獨顯示* 仍顯示在目錄高級搜索結果中。
* **MDVA-44100** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修復將所有FPT分配給購物車中最後一個產品並重置其他產品的問題。
* **MDVA-43605** (*Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 解決使用Rest API時順序資料返回行合計負值的問題。
* **MDVA-43102** (*Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 解決在通過REST API執行退款時無法正確更新可出售數量的問題。
* **MDVA-43178** (*對於Adobe Commerce和Magento Open Source>=2.4.3-p2 &lt;2.4.5*) — 解決無法在GraphQL檢索自定義儲存的客戶令牌的問題。
* **MDVA-43859** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修復錯誤的問題 *沒有具有customerId =的此類實體* 在刪除的客戶嘗試登錄時記錄。
* **MDVA-44147** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 解決GraphQL請求未返回申請清單的問題。
* **MDVA-44505** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修復GraphQL應用獎勵積分不更新總計和在下單期間多次應用商店信用的問題。
* 更新的修補程式：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 僅當「客戶段」設定為時，才解決「相關產品規則」工作的問題 *全部*。
* **MDVA-39605** (*Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 解決Redis快取TTL（過期日期）值錯誤的問題。
* **MDVA-43862** (*Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 解決客戶因GraphQL而無法更新購物車物料的問題 *UpdateCartItems變異* 錯誤。
* **MDVA-43824** (*對於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p3 ||>=2.4.1 &lt;2.4.5*) — 解決取消帶折扣訂單時出現錯誤的問題。
* **MDVA-43451** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修復錯誤的問題 *找不到請求的儲存。 驗證儲存並重試。* 配置特定網站的共用目錄時顯示。
* **MDVA-43491** (*Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 解決在導入多商店網站的產品時基本映像標籤不更新的問題。
* **MDVA-43601** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 在完全重新索引後修復缺少觸發器的問題。
* **MDVA-42046** (*對於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2 ||>=2.4.0 &lt;2.4.5*) — 解決在更新產品時為帶有日期輸入欄位的產品屬性分配不正確值的問題。
* **MDVA-43935** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修復追加銷售產品顯示兩次的問題。
* **MDVA-44188** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 解決系統發出的電子郵件 `.-` 不發送地址。
* **MDVA-42283** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修復管理順序網格中法語區域設定的日期 — 時間格式無效的問題。
* 更新的修補程式：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 已添加的修補程式元資料 [!DNL Site-Wide Analysis Tool]。

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修復用戶能夠編輯活動計畫更新的開始時間的問題。
* **MDVA-42410** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修復優惠券報告僅顯示預設基本貨幣的問題。
* **MDVA-41136** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修復到 `mage-cache-sessid` 未擴展，導致客戶資料清理。
* **MDVA-39993** (*對於Adobe Commerce和Magento Open Source>=2.3.5 &lt;=2.3.7-p2 ||>=2.4.0 &lt;2.4.4*) — 修復通過API完成的清單更改未反映在前端產品頁面上的問題。
* **MDVA-42855** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 解決在結帳期間未將新客戶地址保存到通訊簿的問題。
* **MDVA-42645** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 解決管理員在禁用儲存信用功能時無法退款獎勵積分的問題。
* **MDVA-43414** (*對於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2*) — 修復運行PHP時出現的錯誤 `inventory.reservations.updateSalabilityStatus` 數字SKU上的隊列使用者。
* **MDVA-41628** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 解決現有受限管理員用戶在添加新模組時可以訪問新資源的問題。
* **MDVA-43348** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修復禮品卡GraphQL請求在 `gift_card_options` 含 *UID*。
* **MDVA-39546** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修復在編輯期間可以將暫存更新的開始日期設定為早於當前日期的問題。
* **MDVA-42950** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 解決產品頁面上不播放視頻的問題。
* **MDVA-42689** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 解決Adobe Commerce拋出 *完整性約束衝突* 導入期間更新產品類別時出錯。
* **MDVA-41229** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 解決在可配置產品導入後後端上的可用映像未顯示在前端的問題。
* **MDVA-43731** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 解決問題的位置 *搜索同義詞* 在中增加值時不再工作 *要匹配的最低條款*。
* **MDVA-43232** (*Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 解決在中對產品排序的問題 [!DNL Visual Merchandiser] 按特殊價格到底/頂在保存類別時導致錯誤。
* **MDVA-43726** (*Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.3*) — 修復基於儲存級屬性匹配的目錄價格規則在部分重新索引後無法應用的問題。
* 更新的修補程式：MDVA-36464、MDVA-37478、MDVA-38608。
* 已添加的修補程式元資料 [!DNL Site-Wide Analysis Tool]。

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 解決無法通過REST API為特定網站更新產品價格屬性的問題。
* **MDVA-41350** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 解決當具有限制訪問權限的管理員用戶按訂單按SKU在其角色範圍外添加產品時引發異常的問題。
* **MDVA-42269** (*對於Adobe Commerce和Magento Open Source>=2.4.3-p1 &lt;2.4.5*) — 解決管理員用戶由於 *類型錯誤：strtotime(需要參數1為字串，給定空值* 錯誤。
* **MDVA-40830** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 解決在下單期間多次應用商店信用的問題。
* **MDVA-42237** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 解決在子產品價格更改後不更新可配置產品特價的問題。
* **MDVA-42520** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修復在以下情況下兩次應用稅率的問題： *啟用跨境貿易* 的子菜單。
* 更新的修補程式：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 不建議使用的修補程式：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.5*) — 僅在更改後，批量屬性更新才會為預設儲存建立URL重寫的問題 *產品可見性*。
* **MDVA-43091** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 解決從後端管理員訂購捆綁產品時出錯的問題 *不能為此產品使用小數量*。
* **MDVA-40816** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 解決相關產品規則顯示未在規則條件中定義的類別的產品的問題。
* **MDVA-41305** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 解決將GraphQL突變添加到願望清單後不返回可配置產品選項的問題。
* **MDVA-39181** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 解決相關產品規則顯示未在規則條件中定義的類別的產品的問題。
* **MDVA-42584** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 通過「導入」或「API」更改數量和庫存狀態後，如果後端中的可配置庫存狀態未更新，則修復此問題。
* **MDVA-40175** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 解決問題的位置 *按一下以更改發運方法* 不顯示單選按鈕以在重新排序期間在管理員中選擇發運方法。
* **MDVA-42768** (*Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修復可配置產品在以下情況下將常規價格顯示為0的問題： *顯示庫存不足* 是的。
* **MDVA-43201** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 解決在將DOB屬性用於某些區域設定時客戶登錄時出錯的問題。
* 更新的修補程式：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 解決當Adobe Commerce時區與本地環境時區不同時，日期篩選器無法正常工作的問題。
* **MDVA-42657** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 解決管理員用戶無法在客戶段條件中選擇類別的問題。
* **MDVA-42806** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修復問題 *新公司註冊* 每次通過REST API更新現有公司時都會發送電子郵件。
* **MDVA-37984** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修復問題 [!DNL Visual Merchandiser] *按規則匹配產品* 功能無法正確篩選具有轉移更新的產品。
* **MDVA-40488** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 解決不能將具有庫存不足子產品的可配置產品顯示在其正確價格範圍內的問題。
* **MDVA-42507** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修復在應用購物車規則的暫存更新後清理全頁快取的問題。
* **MDVA-39163** (*Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 解決在註冊新用戶且購物車中的產品來自來賓會話時無法使用發運方法的問題。
* **MDVA-38626** (*Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修復管理員用戶無法使用 [!DNL PayPal Payflow Pro] 付款。
* **MDVA-38666** (*Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.3.6*) — 解決管理員用戶無法更改客戶購物車中可配置產品選項的問題。
* **MDVA-38526** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修復管理員用戶無法訪問 [!DNL Site-Wide Analysis tool]。
* 更新的修補程式：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修復用戶在設定500錯誤後 *影像消息* cookie（如果它已存在），但沒有新消息。
* **MDVA-41139** (*Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 解決當簡單產品的數量為其來源之一時，在產品導入後可配置產品出現庫存不足的問題。
* **MDVA-42326** (*對於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 ||>=2.4.1 &lt;2.4.4*) — 解決在會話超時後客戶在結帳時出錯的問題，即使啟用了永久購物車。
* **MDVA-42341** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修復問題 `categoryList` GraphQL查詢不篩選具有「儲存」標頭的請求的結果。
* **MDVA-38393** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修復目錄規則在可配置產品的簡單產品重新命名時停止工作的問題。
* **MDVA-39153** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修復在管理員重新訂購期間錯誤計算折扣金額的問題。
* 更新的修補程式：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.3*) — 修復管理員用戶在刪除網站後無法訪問客戶網格的問題。
* **MDVA-40311** (*對於Adobe Commerce和Magento Open Source>=2.4.2-p2 &lt;2.4.4*) — 修復管理員用戶獲取錯誤消息的問題 *無效的安全性或表單密鑰。 請刷新頁面* 如果配置了自定義管理路徑並啟用了密鑰，則登錄到管理員後。
* **MDVA-41631** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 解決用戶在嘗試檢索訂單資訊時遇到錯誤而沒有可選 *電話* 通過GraphQL。
* **MDVA-27239** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 解決不顯示交叉銷售產品的問題。
* 更新的修補程式：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 在重新編製索引期間解決前端上缺少產品的問題。
* **MDVA-40120** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 解決按DESC/ASC排序的GraphQL排序與具有相同相關性或價格的產品不協作的問題。
* **MDVA-41399** (*Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.2*) — 修復管理員用戶無法訪問 *管理購物車* 頁。
* **MDVA-40609** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修復禁用的產品資料在 `cataloginventory_stock_status` 索引表，顯示不正確的禁用產品數量。
* **MDVA-39031** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 解決即使未將產品分配給目標網站，也可通過GraphQL將產品添加到購物車的問題。
* **MDVA-41597** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 解決用戶在使用GraphQL向購物車中添加多個可配置產品時出錯的問題。
* **MDVA-27456** (*Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.3.7*) — 修復用戶嘗試載入時出錯的問題 [!DNL Swagger]。
* **MDVA-32776** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2*) — 解決在下訂單時未更新庫存狀態而未發運的問題。
* **MDVA-30862** (*Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.0*) — 在打印的PDF發票上使用錯誤的訂單日期解決問題。
* 改進的 [!DNL Quality Patch Tool]。 添加了方便的搜索和篩選 [!DNL quality patches] 工具的最新版本。
* 更新的修補程式：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 解決以前刪除「結束日期」後無法為產品建立新計畫更新或編輯現有計畫更新的問題。
* **MDVA-41046** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 解決具有定制選項的簡單產品可用於分配給可配置/分組產品的問題。
* **MDVA-40545** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修復僅檢索頁面的第一個節點的問題，即使同一頁面有多個節點。
* **MDVA-41164** (*對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3-p1*) — 解決管理員用戶無法保存或編輯具有檔案或映像類型自定義客戶屬性的公司的問題。
* **MDVA-39229** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修復導致更新目錄規則暫存更新開始時間後出現以下錯誤的問題： *Cron Job staging_synchronize_entities_period出現錯誤：無法刪除活動更新。*
* **MDVA-40619** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修復在CMS頁面上嘗試進行內聯編輯時，對CMS頁面層次結構所做的更改導致500錯誤的問題。
* **MDVA-41061** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 解決將產品從管理員中保存時庫存狀態重置為可出售的問題。
* **MDVA-31763** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修復在手動重新索引之前還原（或未應用）目錄價格規則的問題。
* **MDVA-37748** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修復GraphQL查詢返回未分配給共用目錄的產品的問題。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 解決無法通過REST API同時建立同一訂單的部分發票的問題。
* **MDVA-40101** (*Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.0*) — 使用以下方法修復在成功下單後未從Mini Cart中刪除項目的問題： [!DNL PayPal Express] 簽出。
* **MDVA-40401** (*對於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 ||>=2.4.1 &lt;2.4.4*) — 解決即使訂單失敗，優惠券使用值也會更改的問題。
* **MDVA-40537** (*對於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.0-p1*) — 如果存在多個具有相同URL鍵的CMS頁，則修復在建立儲存視圖時用戶遇到錯誤的問題。
* **MDVA-37725** (*對於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.4.3-p1*) — 修復從非預設網站發送的非同步訂單電子郵件包含預設網站的徽標URL的問題。
* **MDVA-39482** (*對於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 ||>=2.4.1 &lt;2.4.4*) — 在啟用延交訂單時，以「0」數量導入產品時，解決產品缺貨問題。
* **MDVA-40435** (*Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 在通過GraphQL應用時，使用動態價格的捆綁產品上不正確的折扣來解決問題。
* **MC-42528** (*對於Adobe Commerce和Magento Open Source>=2.4.3 &lt;=2.4.3-p1*) — 修復問題 `categoryList` GraphQL查詢返回已分配和未分配的類別。
* **MDVA-29400** (*對於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 使用與一起下的重複訂單解決問題 [!DNL PayPal Express Checkout]。
* **MDVA-26005** (*對於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2*) — 解決無法在類別樹中為購物車價格規則條件選擇類別的問題。
* **MDVA-25631** (*對於Adobe Commerce和Magento Open Source>=2.3.3 &lt;=2.3.5-p2*) — 提高編輯和保存包含大量客戶的客戶段的效能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修復在管理中常用搜索詞中未顯示GraphQL搜索查詢的問題。
* **MDVA-40601** (*對於Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.4.2-p2*) — 解決用戶在嘗試通過GraphQL計畫更新獲取有關類別更改的資訊時遇到錯誤的問題。
* **MDVA-37234** (*Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 解決多次向購物車添加物料（並行請求）以建立同一購物車ID的重複行物料的問題。
* **MDVA-33606** (*對於Adobe Commerce和Magento Open Source>=2.4.1 &lt;=2.4.2-p2*) — 解決用戶獲取 *唯一約束衝突* 保存分配給層次結構的CMS頁時出錯。
* **MDVA-31590** (*對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.1-p1*) — 解決用戶無法使用MySQL非同步隊列批量更新屬性的問題。
* **MDVA-36309** (*對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修復管理網格中按屬性進行產品搜索速度較慢的問題。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 解決當從商店貸方支付訂單時，使用FPT的發票顯示錯誤的總計時的問題。
* **MDVA-37364** (*對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.3*) — 修復日期類型的自定義客戶屬性斷開客戶網格UI的問題。
* **MDVA-39195** (*對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 解決問題的位置 *添加到購物車* 當重定向到啟用購物車時，按鈕在類別頁上處於非活動狀態。
* **MDVA-37115** (*對於Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 在不必要時解決問題 *只剩0個* 「通知」顯示在可配置產品頁面上。
* **MDVA-39521** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 解決用戶無法通過GraphQL在購物車上設定空電話號碼的送貨地址的問題。
* **MDVA-39384** (*對於Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 解決未保存公司用戶的自定義客戶屬性的問題。
* **MDVA-39043** (*對於Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.3*) — 解決管理員用戶在嘗試添加 *產品* 構件到CMS頁面。
* **MDVA-39966** (*對於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 通過部署不正確的語言環境解決問題。
* **MDVA-38852** (*對於Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.5-p2*) — 通過設計來修復目錄清單鎖定表以獲取在多個並行訂單的情況下顯著降低效能的更新的問題。
* **MDVA-39986** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修復用戶無法使用Safari瀏覽器在MacOS管理中下訂單的問題。
* **MDVA-38447** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修復兩個問題：在 *不單獨顯示* 在GraphQL響應中返回可配置的子產品，並使用類別篩選器優化GraphQL產品查詢的MySQL查詢。
* **MDVA-40134** (*Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 解決啟用共用目錄時GraphQL不返回相關產品的問題。
* **MDVA-39935** (*Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 解決GraphQL返回在網站級別禁用的可配置子產品的問題。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修復問題 *對成員函式getId()的調用* 「管理」中的「訂單詳細資訊」頁上顯示錯誤。
* **MDVA-34948** (*對於Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 通過長時間運行的查詢解決問題，如 `GET_LOCK`。
* **MDVA-39305** (*對於Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.2-p1*) — 解決註冊客戶無法使用已啟用的GoogleReCaptcha登錄的問題。
* **MDVA-37897** (*Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 當客戶嘗試使用最近查看的構件中的選項添加產品時，使用錯誤的重定向來解決問題。

## v1.1.0 {#v1-1-0}

* 為了改善用戶體驗，使客戶更容易搜索所需的修補程式，引入了修補程式類別。
* 的 `patches.json` 檔案已更名為 `support-patches.json`。
* **MDVA-38799** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 修復建立轉移更新後未保存可下載產品的問題。
* **MDVA-37592** (*Adobe Commerce>=2.3.6 &lt;=2.4.2-p1*) — 當按價格排序無法正確處理分配給共用目錄的零價格產品時，可解決此問題。
* **MDVA-38827** (*Adobe Commerce>=2.3.3-p1 &lt;2.4.4*) — 解決客戶收到包含錯誤消息的訂單發運電子郵件的問題。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*Adobe Commerce>=2.3.2 &lt;=2.3.5-p2*) — 修復保存CMS頁時的錯誤： *具有相同ID的項PAGE_ID已存在*。
* **MDVA-34680** (*Adobe Commerce>=2.3.6 &lt;=2.3.7 ||>=2.4.1 &lt;2.4.3*) — 解決客戶網格中客戶帳戶建立時間未正確篩選的問題。
* **MDVA-37068** (*Adobe Commerce>=2.3.1 &lt;2.4.4*) — 解決購物車只有虛擬產品時顯示錯誤稅率的問題。
* **MDVA-38608** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 修復未成功完成重新索引時未刪除臨時表的問題。
* **MDVA-38308** (*Adobe Commerce>=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 ||>=2.4.2 &lt;2.4.4*) — 修復與添加相關的問題 [!DNL Vimeo] 視頻到產品。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*Adobe Commerce>=2.3.6 &lt;2.4.3*) — 解決在使用 [!DNL Paypal Payment Advanced] 的雙曲餘切值。
* **MDVA-37082** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 在保存已分組產品的定製庫存導致產品在前端顯示庫存不足時，解決此問題。
* **MDVA-36572** (*Adobe Commerce>=2.3.5 &lt;2.4.3*) — 當貸項通知單更新不再導致資料庫中重複的產品保留更新時，修復此問題。
* **MDVA-38132** (*Adobe Commerce>=2.3.3 &lt;2.4.3*) — 修復由於以下原因導致無法訪問管理面板時的問題 *重定向過多* 錯誤。
* **MDVA-38270** (*Adobe Commerce>=2.4.1 &lt;2.4.3*) — 解決GraphQL訂單總數中缺少禮品卡資訊的問題。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*Adobe Commerce>=2.4.2 &lt;=2.4.4*) — 當網站ID與商店ID不一致時，通過GraphQL將可配置產品添加到購物車中可解決此問題。
* **MDVA-36832** (*Adobe Commerce>=2.3.4 &lt;=2.4.2-p1*) — 當視圖寬度為768像素時，修復頁面上影像重複的問題。
* **MDVA-37874** (*Adobe Commerce>=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 解決問題的位置 *整個購物車的固定折扣金額* 未正確應用於包含多個選項的捆綁產品。
* **MDVA-37913** (*Adobe Commerce>=2.3.0 &lt;=2.4.0-p1*) — 修復可下載產品通過API更新時可下載連結消失的問題。
* **MDVA-34330** (*Adobe Commerce>=2.3.1 &lt;=2.4.2-p1*) — 解決訂單網格中未按管理時區篩選訂單的問題。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*Adobe Commerce>=2.3.0 &lt;=2.3.7*) — 解決Adobe Commerce在為與Windows Server一起下單的訂單建立部分發票時出錯的問題 *按帳戶付款* 通過REST API進行支付。
* **MDVA-37362** (*Adobe Commerce>=2.3.4 &lt;=2.4.2-p1*) — 解決可配置產品選項值和變型屬性值在GraphQL響應中為空的問題。
* **MDVA-37288** (*Adobe Commerce2.4.2*) — 解決在GraphQL請求後返回錯誤層價的問題。
* **MDVA-37225** (*Adobe Commerce>=2.4.1 &lt;=2.4.2-p1*) — 解決當導入的SKU中存在整數值時，在快速建立訂單期間上載過程停滯的問題。
* **MDVA-37224** (*Adobe Commerce>=2.3.3 &lt;=2.4.2-p1*) — 解決客戶無法用可轉讓報價付款的問題 [!DNL PayFlow Pro] 和另一個產品。
* **MDVA-36286** (*Adobe Commerce>=2.3.6 &lt;=2.4.2-p1*) — 修復頁面生成器產品小部件在子類別中位置不同的情況下預覽中斷的問題。
* **MDVA-30186** (*Adobe Commerce>=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) — 解決在GraphQL響應中按選項值而不是屬性項計數排序屬性選項的問題。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*Adobe Commerce>=2.3.0 &lt;=2.4.2*) — 修復通過API更改舊自定義選項後仍保留的問題。
* **MDVA-35773** (*Adobe Commerce>=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) — 修復問題，在發票上未顯示100%折扣訂單的總計為零。
* **MDVA-36833** (*Adobe Commerce2.4.2*) — 在將某些產品從共用目錄中排除後，通過顯示每頁產品隨機數的搜索結果來解決此問題。
* **MDVA-37182** (*Adobe Commerce>=2.4.1 &lt;=2.4.2*) — 解決在這兩種情況下獲取錯誤搜索結果的問題 [!DNL Elasticsearch] 版本6和版本7。
* **MDVA-36253** (*Adobe Commerce>=2.4.0 &lt;=2.4.1-p1*) — 修復刪除項目後，迷你購物車中出現錯誤小計的問題。
* **MDVA-36853** (*Adobe Commerce2.4.2*) — 在載入大型媒體集時，解決不顯示影像的問題。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*Adobe Commerce>=2.3.4 &lt;=2.3.4-p2*) — 解決類別頁面上缺少捆綁產品的問題。
* **MDVA-36615** (*Adobe Commerce2.4.2*) — 在管理產品網格中用不正確的產品計數解決問題。
* **MDVA-36464** (*Adobe Commerce>=2.4.0 &lt;=2.4.2*) — 解決電子郵件通知配置在儲存視圖級別無法正常工作的問題。
* **MDVA-36138** (*Adobe Commerce^2.3.2*) — 解決未調整發運價格並顯示完整發運價格的問題（如果購物車中的所有物料不符合免費發運購物車規則）。
* **MDVA-36424** (*Adobe Commerce>=2.3.0 &lt;=2.3.3-p1 ||>=2.0.0 &lt;2.2.0*) — 如果後端基URL與店面基URL不同，則修復在內容重複編輯時附加到頁面生成器元素的媒體影像消失的問題。
* **MDVA-35984** (*Adobe Commerce^2.4.0*) — 在為同一產品建立多個併發發運後，使用不正確的產品數量和可銷售數量解決問題。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*Adobe Commerce>=2.3.4 &lt;2.4.2*) — 這通過使用類別快取標籤解決了GraphQL查詢未快取的問題。
* **MDVA-33168** (*Adobe Commerce>=2.3.3 &lt;2.4.2*) — 通過API更新產品屬性時，所有其他屬性更改為空值時，會解決此問題。
* **MDVA-19640** (*Adobe Commerce>=2.3.0*) — 解決問題的位置 [!DNL Advanced Reporting] 不顯示任何資料。
* **MDVA-11189** (*Adobe Commerce>=2.3.0 &lt;2.3.5*) — 在導入CSV檔案以更新產品庫、 `cataloginventory_stock` 表格。
* **MDVA-26639** (*Adobe Commerce>=2.3.3-p1 &lt;2.3.6*) — 解決在建立新訂單確認電子郵件模板時訂單郵件中缺少訂單項的問題。
* **MDVA-15546** (*Adobe Commerce>=2.3.0*) — 在建立訂單後修復問題 *列entity_id其中子句不明確* 異常日誌中顯示錯誤。
* **MDVA-21095** (*Adobe Commerce>=2.3.0 &lt;2.3.5*) — 在查詢時修復問題 `INSERT INTO search_tmp` 不會在成批屬性值更新後結束。
* **MDVA-23845** (*Adobe Commerce>=2.3.2-p2 &lt;2.3.5*) — 解決啟用JavaScript精簡後無法預覽電子郵件模板的問題。
* **MDVA-22026** (*Adobe Commerce>=2.3.2 &lt;2.3.4*) — 解決從CSV檔案（包括來自外部URL的映像）導入產品失敗的問題。
* **MDVA-22383** (*Adobe Commerce>=2.3.0 &lt;2.3.4*) — 修復保存產品需要很長時間且分頁的問題。
* **MC-41359** (*Adobe Commerce>=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) — 修復錯誤的SameSite Cookie參數設定問題。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*Adobe Commerce2.4.1*) — 修復頁面生成器引發以下錯誤的問題： *啟動頁面生成器時出錯。 請咨詢您的技術支援聯繫人。*
* **MDVA-35356** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 在取消部分開票訂單後，使用錯誤的儲存信用退貨來解決問題。
* **MDVA-33289** (*Adobe Commerce>=2.4.0 &lt;2.4.3*) — 修復在簽出期間將原始JavaScript代碼顯示在計費地址UI(如果 [!DNL Google Tag Manager] 的子菜單。
* **MDVA-35982** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 解決限制在特定網站的管理員用戶無法為同一網站上的訂單建立裝運的問題。
* **MDVA-35155** (*Adobe Commerce>=2.3.0 &lt;2.3.6*) — 解決在選項標題更改時無法購買捆綁產品的問題。
* **MDVA-35910** (*Adobe Commerce>=2.4.1 &lt;2.4.3*) — 解決在禁用「作為客戶登錄」功能後無法建立新客戶帳戶的問題。
* **MDVA-34474** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 通過使用API將產品添加到申請清單來解決問題。
* **MDVA-34591** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 使用錯誤的購物車規則折扣計算來解決問題 *最大數量折扣應用於* 和 *折扣數量步驟（購買X）*。
* **MDVA-33704** (*Adobe Commerce>=2.4.0 &lt;2.4.3*) — 修復問題 *在商店取貨* 發運選項未顯示，儘管已配置為可用。
* **MDVA-34928** (*Adobe Commerce>=2.3.5 &lt;2.3.5-p2*) — 修復在從付款中刪除儲存信用後無限期顯示頁面載入器的問題。
* **MDVA-35254** (*Adobe Commerce>=2.3.1 &lt;2.4.3*) — 在簽出期間修複驗證碼問題。
* **MDVA-35569** (*Adobe Commerce>=2.3.4 &lt;2.4.2*) — 修復問題 *固定產品稅* 指定狀態時，在GraphQL響應中未填充欄位。
* **MDVA-35847** (*Adobe Commerce>=2.4.1 &lt;2.4.3*) — 修復B2B問題，如果使用自定義客戶屬性，則Company Users表單將斷開。
* **MDVA-31307** (*Adobe Commerce>=2.4.0 &lt;2.4.2*) — 解決存在 *記憶體不足* 由於快取塊的動態CSP白名單出現問題，某些類別出現錯誤。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 修復錯誤 *正在進行* 消息狀態為正確 *完整* 消息 `quoteItemCleaner` 刪除多個產品後。
* **MDVA-34102** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 在「產品網格」和「編輯產品」頁面的「管理」區域中，為禁用的產品修復預設庫存數為零。
* **MDVA-35286** (*Adobe Commerce>=2.4.0 &lt;2.4.2*) — 如果客戶在購物車中捆綁了產品，並將「多地址簽出」切換到「一頁簽出」，則解決出現錯誤的問題。
* **MDVA-35312** (*Adobe Commerce>=2.4.1-p1 &lt;2.4.2*) — 當空的GraphQL請求時修復響應代碼500。
* **MDVA-34189** (*Adobe Commerce>=2.3.4 &lt;2.4.3*) — 修復503第一個位元組超時 [!DNL Visual Merchandiser] 載入「管理類別」頁時查詢。
* **MDVA-34695** (*Adobe Commerce>=2.3.0 &lt;2.4.1*) — 修復負 `children_count` 刪除類別後。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*Adobe Commerce>=2.3.1 &lt;2.4.3*) — 修復問題 *使用預設值* 在應用計畫更改後，複選框將被清除。 一旦計畫的更改不再有效，問題就會出現。
* **MDVA-35064** (*Adobe Commerce>=2.3.3 &lt;2.4.3*) — 解決不為通過API建立的可配置產品生成URL重寫的問題。
* **MDVA-34943** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決快速訂單快取先前輸入的SKU的問題。
* **MDVA-35197** (*Adobe Commerce>=2.3.5 &lt;2.4.0*) — 如果以前添加的產品出庫，則使用GraphQL添加到購物車時出錯，請解決此問題。
* **MDVA-34850** (*Adobe Commerce>=2.3.1 &lt;2.4.0*) — 解決不顯示可配置產品的庫存外選項而不顯示為直接顯示的問題。
* **MDVA-34867** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 修復未保存計畫更新條件欄位集的值的問題。
* **MDVA-35092** (*Adobe Commerce>=2.3.5 &lt;2.4.3*) — 修復用戶無法添加的問題 [!DNL Vimeo] 視頻由於不建議使用 [!DNL Vimeo] API。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*Adobe Commerce>=2.3.6 &lt;2.4.3*) — 修復頁面生成器產品內容類型預覽分隔符的問題（如果匹配的產品對每個網站的價格不同）。
* **MDVA-32634** (*Adobe Commerce^2.3.1*) — 修復問題 `url_path` 在層次結構中移動類別後，分配給所有儲存的類別仍保持不變。
* **MDVA-33344** (*Adobe Commerce^2.3.0*) — 修復硬編碼的問題 `rma_item` 使用實體預設屬性集ID，而不是資料庫中的值。
* **MDVA-34192** (*Adobe Commerce>=2.3.4 &lt;2.4.3*) — 解決無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。
* **MDVA-34847** (*Adobe Commerce^2.3.0*) — 將具有自定義權限的管理員用戶的管理集合中的SQL條件的儲存ID類型轉換為整數。
* **MDVA-34886** (*Adobe Commerce^2.3.2*) — 修復搜索不返回結果的問題 *重量* 產品屬性配置為可搜索。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 修復 [!DNL PayPal Payflow Pro] 付款失敗，出現重定向參數清單格式錯誤。
* **MDVA-34023** (*Adobe Commerce>=2.3.0 &lt;2.4.3*) — 修復錯誤的問題 *沒有具有addressId的此類實體* 隨機顯示在訪問者的瀏覽器上。
* **MDVA-32759** (*對於Adobe Commerce>=2.3.1 &lt;2.4.3，帶B2B擴展*) — 修復共用目錄正在刪除現有層定價的問題。
* **MDVA-33482** (*Adobe Commerce^2.3.5*) — 解決以下問題：根據部分發票生成貸項通知單將導致對該部分發票的總訂單徵稅，而不是對該部分發票徵稅。
* **MDVA-33393** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復錯誤 *提供的countryId不存在*。
* **MDVA-33632** (*Adobe Commerce>=2.3.0 &lt;2.3.7*) — 提供異常消息所在的修復 *此產品現貨不足* 現在，在嘗試重新訂購出庫產品時，將顯示給管理員用戶。
* **MDVA-34469** (*Adobe Commerce>=2.4.1 &lt;2.4.2*) — 解決使用多個儲存視圖時客戶購物車上的GraphQL突變失敗的問題。
* **MDVA-33976** (*Adobe Commerce>=2.3.0 &lt;2.3.7*) — 在從捆綁產品中刪除第二個選項後，修復在店面上顯示捆綁產品庫存不足的問題。
* **MDVA-33894** (*對於Adobe Commerce>=2.4.0 &lt;2.4.1，帶B2B擴展*) — 解決快速訂購功能的多個問題，包括添加和刪除多個產品和SKU區分大小寫。
* **MDVA-27664** (*Adobe Commerce>=2.3.4 &lt;2.3.6*) — 修復客戶註冊表中導致錯誤顯示的問題： *錯誤 — 出生日期不應大於今天。*
* **MDVA-33970** (*Adobe Commerce>=2.3.4 &lt;2.4.2*) — 在將價格屬性的範圍設定為網站時，解決貸項通知單中存在錯誤貨幣符號的問題。
* **MDVA-33992** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復B2B特殊定價在結帳期間顯示不正確的問題。
* **MDVA-34100** (*對於Adobe Commerce>=2.3.4 &lt;2.4.2，帶B2B擴展*) — 修復無法從公司結構頁面建立公司帳戶的問題。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*Adobe Commerce>=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) — 從CSV檔案導入產品後，使用重複映像修復此問題。
* **MDVA-33382** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復從類別中刪除產品後索引器失效的問題。
* **MDVA-28511** (*Adobe Commerce>=2.3.5 &lt;2.3.6*) — 解決無法完成的問題 [!DNL PayPal] 如果「名稱」欄位包含某些字元（如帶重音的大寫字母），則簽出。
* **MDVA-31519** (*Adobe Commerce>=2.3.5 &lt;2.3.6*) — 使用站點範圍的銷售規則時，通過來賓簽出中的等待超時來解決此問題。
* **MDVA-33281** (*Adobe Commerce>=2.3.4 &lt;2.3.6*) — 修復中出現致命錯誤的問題 `inventory:reservation:list-inconsistencies` 因為SKU參數類型錯誤。
* **MDVA-24201** (*Adobe Commerce>=2.3.0 &lt;2.3.5*) — 修復價格在手動重新編製索引之前未反映計畫購物車價格規則的問題。
* **MDVA-32694** (*Adobe Commerce>=2.3.0 &lt;2.3.6 ||>= 2.4.0 &lt;2.4.2*) — 解決管理員用戶無法將產品添加到可轉讓報價（如果產品與非預設儲存相關）的問題。
* **MDVA-33516** (*Adobe Commerce>=2.3.0 &lt;2.3.6*) — 修復在申請清單中編輯捆綁產品導致錯誤的問題。
* **MDVA-33975** (*Adobe Commerce>=2.3.4 &lt;2.4.2*) — 修復與GraphQL請求中的價格計算相關的多個問題。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 通過 [!DNL PayPal] 未在下面提供結算報告 **報告** > **銷售** > **[!DNL PayPal]** 按預期結算。
* **MCP-87** (*Adobe Commerce>=2.3.1 &lt;2.4.2*) — 大型配置檔案的類別產品和庫存索引器的索引時間縮短。
* **MDVA-33106** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復重新計畫的產品更改在cron之後被擦除的問題 `run` 命令。
* **MDVA-19391** (*Adobe Commerce>=2.3.0 &lt;2.3.5*) — 解決問題的位置 `analytics_collect_data` 由於中的NULL描述記錄而引發錯誤 `catalog_category_entity_text` 的子菜單。
* **MDVA-20376** (*Adobe Commerce>=2.3.2 &lt;2.3.4*) — 使用 *沒有客戶ID為1的此類實體* 錯誤 `exception.log` 訂單下單後登錄的客戶。
* **MDVA-23764** (*Adobe Commerce>=2.3.2 &lt;2.3.5*) — 修復中的錯誤 `JsFooterPlugin.php` 影響動態塊的顯示。
* **MDVA-13203** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復問題 *完整性約束違規search_tmp_表* 完全重新索引後出現錯誤。
* **MDVA-23426** (*Adobe Commerce>=2.3.3 &lt;2.3.5*) — 解決Adobe Commerce發送的通知電子郵件包含空白正文且內容作為附件添加的問題。
* **MDVA-22150** (*Adobe Commerce>=2.3.1 &lt;2.3.4*) — 解決在Admin中禁用了可配置產品且應用了優惠券的客戶無法登錄的問題。
* **MDVA-32545** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決在從管理員建立訂單時不自動發送發票的問題。
* **MDVA-32714** (*Adobe Commerce>=2.3.4 &lt;2.4.1*) — 解決客戶組價格在GraphQL產品查詢中不起作用的問題。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*Adobe Commerce>=2.3.2 &lt;2.4.2*) — 添加 *小計(包括 稅)* 選項來定價規則條件。
* **MDVA-31236** (*Adobe Commerce>=2.4.0 &lt;2.4.2*) — 修復具有自定義資源訪問權限的管理員無法設定2FA或登錄的問題。
* **MDVA-30845** (*Adobe Commerce>=2.3.5 &lt;2.3.7*) — 修復問題 *抱歉，此時此訂單沒有報價* 無法連接到UPS XML/USPS/DHL時顯示錯誤，並且沒有其他發送方法可用。
* **MDVA-32133** (*Adobe Commerce>=2.4.0 &lt;2.4.1*) — 在某些情況下修復媒體集未從頁面生成器載入的問題。
* **MDVA-12304** (*Adobe Commerce>=2.3.0*) — 將Cookie的最大數量從50增加到200。
* **MDVA-32632** (*Adobe Commerce>=2.3.2 &lt;2.3.5*) — 解決付款系統中出現訂單，但Adobe Commerce不出現訂單的問題。
* **MDVA-32449** (*Adobe Commerce>=2.3.0 &lt;2.3.6 | 2.4.0 || >=2.4.1 &lt;2.4.2，帶B2B擴展*) — 修復訂單歷史記錄載入非常緩慢或根本不載入的問題。
* **MDVA-32739** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決啟用非同步電子郵件通知發送舊銷售電子郵件的問題。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*Adobe Commerce2.3.6,2.4.1*) — 修復問題 *建立帳戶* 按鈕在更正無效資料後處於禁用狀態 *建立新客戶帳戶* 的雙曲餘切值。
* **MDVA-31006** (*Adobe Commerce2.3.0,2.3.1*) — 使用 [!DNL Paypal Express] 付款。
* **MDVA-25602** (*Adobe Commerce2.3.0*) — 修復問題 [!DNL PayPal Payflow Pro] 支付方法和將cookie視為 `SameSite=Lax` 預設情況下，在Chrome 80瀏覽器和API響應中重定向到客戶登錄頁。

## v1.0.10 {#v1-0-10}

修補程式版本的次要修復

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*Adobe Commerce>=2.3.2 &lt;2.4.2*) — 解決在以下情況下不適用的問題：帶優惠券的購物車價格規則在GraphQL *整個購物車的固定金額折扣* 操作。
* **MDVA-30889** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決在將虛擬和簡單產品作為選項為捆綁包開票後出現錯誤的問題。
* **MDVA-31791** (*Adobe Commerce>=2.3.4 &lt;2.3.5*) — 在使用目標規則或連結產品時，提高產品頁的效能。
* **MDVA-31168** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復產品導出CSV檔案未出現且記憶體分配錯誤的問題。
* **MDVA-32313** (*Adobe Commerce>=2.3.0 &lt;2.3.4*) — 解決可配置產品可以添加到願望清單中，但配置選項錯誤的問題。
* **MDVA-31759** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決產品未更新的問題 *下拉清單* 和 *毛蕊* 屬性值。
* **MDVA-32012** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決無法驗證韓國和阿根廷郵遞區號的問題。
* **MDVA-31640** (*Adobe Commerce>=2.3.1 &lt;2.3.6 ||>=2.4.0 &lt;2.4.1*) — 解決無法通過REST API更新特價的問題。
* **MDVA-28651** (*Adobe Commerce>=2.3.0 &lt;2.3.6 || >2.4.0，帶B2B擴展*) — 解決通過REST API載入可協商報價時出現效能問題的問題。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*對於Adobe Commerce>=2.3.0 &lt;2.4.1，帶B2B擴展*) — 解決在貸項通知單網格中顯示錯誤貨幣符號的問題。
* **MDVA-31295** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決在完成部分訂單和對項目課稅時未計算獎勵積分的問題。
* **MDVA-30112** (*Adobe Commerce>=2.3.4 &lt;2.4.2*) — 如果訂單數超過 *束團大小* 值，Adobe Commerce考慮 *掛起* 狀態為不一致。
* **MDVA-31150** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決在GET發票餘額API調用未返回商店信用卡和禮品卡餘額時，在發票由餘額API調用過帳且訂單部分由商店信用卡和禮品卡帳戶支付時的問題。
* **MDVA-30963** (*Adobe Commerce>=2.3.2 &lt;2.4.2*) — 修復產品篩選結果集僅包含為指定的值的問題 *所有儲存視圖* 在「管理」中，包括在儲存視圖級別上值被覆蓋的產品。
* **MDVA-29954** (*Adobe Commerce>=2.3.0 &lt;2.3.6 | 2.4.0 || 2.4.2，帶B2B擴展*) — 修復問題 *新公司註冊請求* 和 *你和一家公司有聯繫* 電子郵件從錯誤的地址發送。
* **MDVA-28357** (*Adobe Commerce>=2.3.2 &lt;2.3.6 ||>=2.4.0 &lt;2.4.1*) — 將標準分析器替換為SKU欄位的關鍵字標籤器 [!DNL ElasticSearch] 使通配符搜索查詢與包含連字元(&quot;-&quot;)的SKU配合使用的索引。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復將自定義訂單狀態更改為的問題 *處理* 在使用WebApi建立部分裝運後。
* **MDVA-30428** (*Adobe Commerce>=2.3.4 &lt;2.3.5*) — 解決如果將此產品分配給自定義庫存來源，客戶無法將產品添加到願望清單的問題。
* **MDVA-30594** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決配置FPT時，在簽出期間無法保存具有多個地址的訂單的問題。
* **MDVA-29148** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 通過API調用建立產品時解決問題，產品自定義屬性 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 如果負載中未提供值，則類型（如多選）不使用其預設值。
* **MDVA-30837** (*Adobe Commerce>=2.3.1 &lt;2.3.5*) — 已添加配置設定 *包括稅額：是/否* 在免費發運方法配置中。 當 *包括稅額* 設定為 *是*，最小訂單金額按小計+稅計算。 當 *包括稅額* 設定為 *否*，最小訂單金額計算為小計
* **MDVA-25028** (*Adobe Commerce>=2.3.2 &lt;2.3.3 ||>=2.3.5 &lt;2.3.6*) — 在下訂單時使用 [!DNL PayPal Payflow Pro] 在觸發欺詐篩選器時未設定為「懷疑欺詐」狀態。
* **MDVA-31224** (*Adobe Commerce>=2.3.3 &lt;2.3.5*) — 提高 `catalog_product_price` 為捆綁產品重新編製索引操作。
* **MDVA-31321** (*Adobe Commerce>=2.3.2 &lt;2.3.5*) — 修復空白頁（錯誤） *全部顯示* 的子菜單。 [!DNL Elasticsearch] 返回大量產品ID清單。 在此方案中， order by子句將轉換為不正確的SQL格式。
* **MDVA-30815** (*Adobe Commerce>=2.3.2 &lt;2.3.4*) — 修復當您更改搜索結果頁面上應顯示多少個搜索結果時，Adobe Commerce將顯示空白頁面的問題。 [!DNL Elasticsearch] 現在，在更改每頁查看的搜索結果數時，可以正確顯示類別頁中的結果。
* **MDVA-30782** (*Adobe Commerce>=2.3.5 &lt;2.4.2*) — 解決不管購物車規則如何顯示動態塊的問題。
* **MDVA-31021** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復中存在效能問題的問題 `module-catalog-import-export/Model/Import/Product/Option.php`。 如果在 `catalog_product_option` 表中，使用單個產品的新CSV驗證不到10秒。
* **MDVA-31007** (*Adobe Commerce>=2.4.0 &lt;2.4.1*) — 修復自定義地址屬性未正確顯示在「我的帳戶」區域和後端的「訂單詳細資訊」頁中的問題。
* **MDVA-29389** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 使用Advanced Reporting解決問題， `analytics_collect_data` 克羅尼布說： *必須在主機參數內配置埠（如localhost:3306）*。
* **MDVA-31343** (*Adobe Commerce>=2.3.4 &lt;2.3.6*) — 通過刪除的body類解決問題 `page-layout-category-full-width` 類別時。
* **MDVA-30945** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復更新購物車時收到致命錯誤消息的問題 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`。

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*Adobe Commerce>=2.3.4 &lt;2.4.0*) — 實施 *最小值應匹配* 功能和部分搜索 [!DNL Elasticsearch] 引擎。 解決搜索查詢中連字元的問題。
* **MDVA-30102** (*Adobe Commerce>=2.3.2 &lt;=2.4.0*) — 解決Redis快取快速增長的問題，因為佈局快取沒有TTL。
* **MDVA-30599** (*Adobe Commerce>=2.3.4 &lt;=2.4.0*) — 解決使用API建立的來賓報價被錯誤地標籤為登錄客戶的報價的問題。
* **MDVA-29446** (*Adobe Commerce>=2.3.3 &lt;=2.4.0*) — 解決在結帳期間不適用發運方法的價格顯示為零的問題。
* **MDVA-30357** (*Adobe Commerce>=2.3.2 &lt;=2.4.0*) — 通過cron生成站點地圖時，會建立錯誤的映像URL，從而解決此問題。
* **MDVA-30565** (*Adobe Commerce>=2.3.2 &lt;=2.3.3-p1*) — 解決問題的位置 *沒有具有cartid = 0的此類實體* 如果啟用了永久購物車，則在店面結帳時將顯示來賓客戶的錯誤。
* **MDVA-29787** (*Adobe Commerce>=2.3.0 &lt;=2.4.0*) — 解決相關產品的目標規則在以下情況下不起作用的問題： *是* 條件用於定義要顯示的產品。
* **MDVA-30977** (*Adobe Commerce>=2.3.4 &lt;=2.3.5-p2*) — 修復重新索引後類別中缺少隨機產品的問題。
* **MDVA-28202** (*Adobe Commerce>=2.3.4 &lt;=2.4.2*) — 解決使用MSI時分層導航無法正確篩選可配置產品的問題。
* **MDVA-28300** (*Adobe Commerce>=2.3.0 &lt;2.3.6*) — 解決GQL請求未反映目錄價格規則中的價格更改的問題。
* **MDVA-31006** (*Adobe Commerce>=2.3.2 &lt;=2.4.2*) — 使用 [!DNL Paypal Express] 付款。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*Adobe Commerce>=2.3.4 &lt;2.3.6 | 2.4.0*) — 通過分層導航解決問題， *否* 布爾類型產品屬性的值未包括在分層導航中(如果 [!DNL Elasticsearch] 被用作搜索引擎。
* **MDVA-28191** (*Adobe Commerce>=2.3.3 &lt;2.4.2*) — 解決在通過管理員建立訂單期間未載入付款方法的問題。
* **MDVA-29959** (*對於Adobe Commerce>=2.3.0 &lt;=2.3.3-p1，帶B2B擴展*) — 解決管理員用戶受限的問題 *公司* 不允許刪除公司帳戶的權限。
* **MDVA-30265** (*Adobe Commerce>=2.3.3 &lt;2.4.2*) — 修復在建立發票後發運跟蹤連結停止工作的問題。
* **MDVA-28409** (*Adobe Commerce>=2.3.4 &lt;2.3.6 | 2.4.0*) — 修復問題 `sales_clean_quotes` cron作業失敗 *記憶體不足* 資料庫中過期引號數量巨大時出錯。
* **MDVA-30593** (*Adobe Commerce>=2.3.0 &lt;2.3.4*) — 解決未清除根據「報價生存期」設定過期的報價的問題。
* **MDVA-30107** (*Adobe Commerce>=2.3.0 &lt;2.3.6*) — 解決如果儲存視圖使用不同的基URL，則儲存交換機無法按預期工作的問題。
* **MDVA-28763** (*Adobe Commerce>=2.3.2 &lt;2.3.4*) — 使用REST API多次更新產品資訊後，解決產品映像被複製的問題。
* **MDVA-30284** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 修復目錄搜索索引器因以下原因而失敗的問題 *[!DNL Elasticsearch]錯誤：已超出索引中的總欄位的限制。*
* **MDVA-29042** (*對於Adobe Commerce>=2.3.3 &lt;=2.3.4-p2，帶B2B擴展*) — 修復目錄權限更改為的問題 *允許* 將新產品添加到共用目錄後自動執行。
* **MDVA-30428** (*Adobe Commerce>=2.3.3 &lt;2.4.2*) — 解決如果將此產品分配給自定義庫存來源，客戶無法將產品添加到願望清單的問題。
* **MDVA-28661** (*對於Adobe Commerce>=2.3.0 &lt;2.4.2，帶B2B擴展*) — 在更改公司管理員後，在「公司用戶」公司帳戶部分中修復引發錯誤的問題。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*Adobe Commerce2.3.1 - 2.3.4-p2*) — 修復當資料庫名稱過長時cron作業失敗的問題，導致未在前端更新類別。
* **MDVA-30106** (*Adobe Commerce^2.3.0*) — 修復未在結帳付款期間載入的問題 *無法讀取空屬性「length」* JS控制台中出錯。
* **MDVA-28656** (*Adobe Commerce>=2.3.1 &lt;2.3.6 ||>=2.4.0 &lt;2.4.2*) — 解決在下單時不需要付款資訊（例如，折扣為100%）並為訂單建立發票時，訂單狀態將更改為 *已關閉* 而不是「完成」。
* **MDVA-30209** (*Adobe Commerce2.3.0 - 2.3.3-p1*) — 解決在客戶更新其帳戶資訊時將客戶組更改為預設值的問題。
* **MDVA-30123** (*Adobe Commerce>=2.3.4 &lt;2.4.2*) — 解決屬性選項標籤無法正確翻譯的GraphQL查詢問題。
* **MDVA-29996** (*Adobe Commerce>=2.3.3 &lt;2.4.2*) — 解決啟用類別權限後類別頁面未被全頁快取快取的問題。
* **MDVA-30164** (*Adobe Commerce>=2.3.1 &lt;2.4.2*) — 解決客戶記錄無法從客戶網格中導出（如果存在自定義客戶屬性）的問題。
* **MDVA-30444** (*Adobe Commerce>=2.3.0 &lt;2.4.1*) — 解決使用GraphQL下單時未發送確認電子郵件的問題。
* **MDVA-30490** (*Adobe Commerce2.3.4 - 2.3.5-p2*) — 修復產品比較在其中一個產品有空簡短說明時引發500錯誤頁的問題。
* **MDVA-30232** (*Adobe Commerce>=2.3.1 &lt;2.4.1*) — 如果原始訂單包含禮品卡，則無法重新訂購，則解決此問題。
* **MDVA-29965** (*Adobe Commerce>=2.3.3 &lt;2.4.0*) — 解決客戶在將產品添加到購物車時出現「Invalid Form Key（無效表單密鑰）」錯誤的問題。
* **MDVA-30008** (*Adobe Commerce>=2.3.0 &lt;2.4.2*) — 解決B2B問題，因為無法通過Admin API為公共目錄中的產品下訂單。
* **MDVA-22469** (*Adobe Commerce2.3.2-p2 - 2.3.3-p1*) — 解決升級到Adobe Commerce2.3.3後，頁面生成器在「管理」面板中不工作，並且某些JS和CSS檔案未載入的問題。
* **MC-35984** (*Adobe Commerce>=2.4.0 &lt;2.4.1*) — 修復在為退貨授權(RMA)建立發運標籤後，商家無法與退貨頁面上的任何頁面元素交互的問題。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*Adobe Commerce2.3.0 - 2.3.4*) — 通過 [!DNL PayPal Payflow Pro] 支付方法和將cookie視為 `SameSite=Lax` 預設情況下，在Chrome 80瀏覽器和API響應中重定向到客戶登錄頁。
* **MDVA-26694** (*Adobe Commerce>=2.3.0 &lt;2.3.6 | 2.4.0*) — 解決產品快取和目錄快取每天過期的問題，儘管計畫的過期時間不同。
* **MDVA-27825** (*Adobe Commerce>=2.3.0 &lt;2.4.1*) — 解決因記憶體洩漏導致大量資料導出失敗的問題。
* **MDVA-29085** (*Adobe Commerce>=2.3.0 &lt;=2.3.5-p1*) — 解決B2B問題，如果公司是由API建立的，則不會發出所需的新公司電子郵件。
* **MDVA-29344** (*Adobe Commerce>=2.3.5 &lt;=2.4.0-p1*) — 修復將文本從標題元素複製到文本元素後頁面生成器卡住的問題。
* **MDVA-29835** (*Adobe Commerce>2.3.1 &lt;2.4.2*) — 解決禮品卡訂單包含兩個代碼而非一個代碼的問題。
* **MDVA-30052** (*Adobe Commerce>=2.3.2-p2 &lt;2.3.5*) — 解決私有內容（本地儲存）未正確填充的問題，導致效能問題。
* **MDVA-30131** (*Adobe Commerce>=2.3.4 &lt;2.3.6 | 2.4.0*) — 通過分層導航解決問題， *否* 布爾類型產品屬性的值未包括在分層導航中(如果 [!DNL Elasticsearch] 被用作搜索引擎。
* **MDVA-35514** (*Adobe Commerce>=2.4.0 &lt;2.4.1*) — 通過在「建立包」模式窗口中建立發運標籤和將訂購的產品添加到包來解決此問題。
