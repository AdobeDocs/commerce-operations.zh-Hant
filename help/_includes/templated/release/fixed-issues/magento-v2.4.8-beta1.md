---
source-git-commit: aedbb5c550a088b67328891fbb788458d14f31a8
workflow-type: tm+mt
source-wordcount: '12351'
ht-degree: 0%

---
# Magento Open Source已修正問題(v2.4.8-beta1)

## 已修正的問題

我們已修正Magento Open Source2.4.8核心程式碼中的231個問題。 此版本中包含的已修正問題子集說明如下。

### API

* _AC-10042_： /V1/transactions REST API在parent_txn_id = txn_id時傳回錯誤
   * _修正附註_：系統現在會正確處理父項交易ID與交易ID相同的父項和子項概念交易，避免在查詢/V1/transactions REST API端點時發生無限回圈。 以前，此情況會導致嚴重錯誤，因為超過最大執行時間。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_： 2.4.7中的[Graphql]型別問題
   * _修正附註_：系統現在會在執行GraphQL查詢時，正確處理GetCustomSelectedOptionAttributes函式中的整數值，避免任何與型別相關的錯誤。 之前，啟動使用具有整數引數的GetCustomSelectedOptionAttributes的GraphQL查詢會導致型別錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38662>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38663>
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

### 帳戶

* _AC-10782_：客戶地址表單允許在名稱欄位中使用隨機碼
   * _修正附註_：系統現在會驗證客戶地址表單中「名字」和「姓氏」欄位的輸入，避免使用隨機代碼。 之前，系統允許在這些欄位中使用隨機程式碼，而不會擲回錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38331>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38345>
* _AC-10990_：儲存時我的帳戶新增位址當機
   * _修正附註_：系統現在即使未顯示地區欄位，仍可正確儲存客戶地址，避免在儲存過程中當機。 先前，嘗試新增或編輯沒有顯示區域欄位的地址會導致例外錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38406>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38407>
* _AC-11919_：管理員：頁面動作按鈕會向左浮動，而非向右
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38701>
   * _GitHub程式碼貢獻_： &lt;https://github.com/magento/magento2/ （內部，未合併）>
* _AC-11999_： magento 2.4.7中的dev:di:info錯誤
   * _修正附註_：系統現在會在執行dev:di:info命令時正確顯示建構函式引數，避免發生任何錯誤。 以前，執行此命令會導致錯誤，因為引數中的型別不相符。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38740>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_：客戶已登入，但在前端顯示404錯誤。
   * _修正附註_： storefront客戶儀表板頁面現在會在客戶登入時依預期載入。 客戶以前可以登入，但此頁面顯示404錯誤。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35838>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_：無法在管理員編輯客戶區段中儲存客戶屬性資訊；
   * _修正附註_：現在已針對管理員客戶編輯表單的網站範圍，正確實作客戶的商店ID。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/488c1034>

### 管理員UI

* _AC-11588_：資料驗證成功，且在具有取代行為的匯入產品期間出現匯入按鈕
   * _修正附註_：系統現在會正確驗證資料，並在產品匯入程式期間以「取代」行為隱藏「匯入」按鈕，以防止任何非預期的資料取代。 以前，系統錯誤地驗證資料並顯示「匯入」按鈕，導致潛在的資料不一致。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_： [錯誤] 2.4.7Magento不允許產品像片的副檔名為大寫字母。
   * _修正附註_：系統現在接受具有大寫字母副檔名的產品影像上傳，以確保順利的產品建立程式。 之前，以大寫字母副檔名的影像上傳遭到拒絕，迫使使用者將副檔名變更為小寫。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38831>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-7700_： [問題]在mview取消訂閱上卸除索引子變更記錄檔表格
   * _修正備註_：系統現在會在索引從「依排程更新」切換為「儲存時更新」時，自動移除未使用的變更記錄檔表格，將索引標籤為無效，以確保不會遺漏任何專案。 以前，將索引切換為「儲存時更新」會在系統中保留未使用的變更記錄檔表格，並將所有變更的索引標籤為「有效」。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/29789>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/25859>
* _AC-9843_： i18n：collect-phrases中斷翻譯完整性
   * _修正附註_： `bin/magento i18n:collect-phrases -o`命令現在可以正確從JavaScript和.phtml檔案收集並新增新片語，確保翻譯檔案能正確反映翻譯。 以前，系統無法在翻譯檔案中包含來自JavaScript檔案的多行翻譯短語以及來自.phtml檔案的短語，導致翻譯不完整或不正確。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_：存放區檢視名稱中的縮寫符號已取代為&#39;
   * _修正附註_：格線的存放區檢視篩選器現在會正確顯示單引號
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38395>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_： Favicon上傳無法驗證.ico檔案
   * _修正附註_：檔案驗證錯誤已更新為「檔案驗證失敗」。 請驗證存放區設定中的影像處理設定。」 以前只是「檔案驗證失敗」。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_： PageBuilder中的相簿顯示舊的影像縮圖，而非新上傳的影像
   * _修正附註_：透過頁面產生器內容中的媒體集，重新產生已刪除及重新上傳之相同名稱影像的影像預覽。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/001e5188>，<https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_：由具有不同角色範圍的管理員使用者儲存產品會覆寫/刪除產品中現有的相關產品資訊
   * _修正備註_：之前，修正前，當次要管理員使用者按一下「儲存」按鈕，而相關產品未變更時，相關產品會重設並變成空白。 此項修正後，次要管理員使用者按一下儲存按鈕，產品未重設且儲存成功。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_：無法匯出超過200個訂單
   * _修正附註_：為了修正問題，將HTTP要求從GET變更為POST，已略過先前提交之選定ID的要求大小伺服器限制。 之前，由於GET請求大小的伺服器限制，因此會發生問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_：結帳頁面驗證訊息不正確。
   * _修正附註_：如果任何必要欄位留空（例如「位址」），伺服器端驗證將不會顯示訊息。 使用者端驗證將確保必填欄位錯誤通知出現，指出「這是必填欄位」。 以前，如果任何必填欄位留空，除了使用者端驗證訊息之外，還會顯示「需要地址」訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_：管理員使用者的密碼重設範本問題
   * _修正附註_：問題已透過使用正確金鑰解決，現在電子郵件範本中包含管理員使用者名稱，並正確完成主旨。 以前，該問題源自所使用的過時的鍵值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3171_： COD不適用於允許的特定國家/地區
   * _修正附註_：現在只要有需要，且允許的特定國家/地區可以使用「貨到付款」   AC-3216如預期運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>

### 管理員UI、效能

* _ACP2E-3169_：更新至2.4.5-p8後，從管理員建立訂單時發生500錯誤
   * _修正附註_：先前，啟用HTML縮制時，無法下管理員的訂單。 現在，啟用HTML縮制後，管理員的訂單就可以成功下達。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>

### 管理UI，運送

* _ACP2E-2519_：優惠券代碼計數不會在   如果訂單是多次出貨，則會顯示「管理優惠券代碼」標籤中的「使用時間」欄。
   * _修正附註_：先前當以多筆運送方式下訂單時，在[管理優惠券代碼]索引標籤的[使用時間]欄中，優惠券代碼計數未更新。 現在，正確計數會顯示在兩個「使用時間」中，以反映多重送貨的所需值。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/4745100c>

### Analytics/報表

* _ACP2E-2570_：進階報告無法運作
   * _修正附註_：系統現在支援以10,000批次載入和寫入報表，為超大型資料集產生進階報表資料檔案。 以前，進階報告模組無法為超大型資料集產生資料檔案，導致在執行analytics_collect_data cron作業期間出現「MySQL伺服器已消失」錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_：管理員訂購產品報告日期範圍可見性問題。
   * _修正附註_：使用者將能夠從「訂購產品」報表中選取任何日期。 先前，重新整理表格後，選取「起始」日期會重設「截止」日期。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_：不正確的curl標頭，導致newrelic:create:deploy-marker無法運作
   * _修正附註_：系統現在已正確設定curl標頭的格式，允許newrelic:create:deploy-marker命令在New Relic中成功建立部署標籤。 之前，不正確的curl標題無法在New Relic中建立部署標籤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37641>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>

### Analytics/報表，B2B

* _ACP2E-2300_： B2B - Sitemap包含未指派給共用目錄的產品/類別
   * _修正附註_：將Sitemap產生的類別和產品限製為僅指派給公用共用類別和/或類別許可權設定的類別和產品。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/報表、雲端

* _ACP2E-3067_：Magento會捨棄大部分New Relic cron交易#34108
   * _修正附註_： AC正在向NewRelic正確報告cron工作相關交易。 以前，某些cron工作相關交易在NR中顯示為「OtherTransaction/Action/unknown」
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_：「我的訂單」區段上有不必要的框線
   * _修正附註_：先前已建立其他套用其他CSS類別的容器（訂單參考），導致不必要的框線出現在「我的訂單」區段內的訂單編號下方，而現在未顯示。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>

### B2B，框架

* _AC-9607_：篩選公司格線，然後嘗試格線CSV匯出會失敗並擲回例外狀況
   * _GitHub程式碼貢獻_： &lt;https://github.com/magento/magento2/ （內部，未合併）>

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
* _AC-11876_： [問題] 2.4.7中的銷售規則回歸
   * _修正備註_：系統現在可正確驗證銷售規則，當產品狀況不符合任何產品名稱時，無法套用優惠券代碼至購物車。 以前，即使產品狀況與任何產品名稱不符，也可以套用銷售規則，並針對運費金額提供折扣。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38671>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_： [問題]郵遞區號變更後，載入程式會封鎖送貨方法、送貨費率驗證規則
   * _修正附註_：系統現在會正確處理自訂送貨方法，而不使用送貨費率驗證規則，確保載入器在結帳期間變更送貨地址中的郵遞區號後，不會封鎖送貨方法。 先前，在結帳期間變更送貨地址中的郵遞區號，會導致載入程式封鎖送貨方法，而且在使用沒有運費驗證規則的自訂送貨方法時無法消失。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38742>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_：優惠券代碼功能在Magento2.4.7的結帳頁面中無法正常運作
   * _修正備註_：系統現在會在虛擬和可下載產品的結帳頁面上啟用折扣代碼/優惠券輸入欄位，讓使用者如預期套用折扣代碼。 之前已停用折扣代碼/優惠券輸入，且按鈕標題文字顯示為「取消優惠券」，以防止使用者套用折扣代碼。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38826>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/1bafc571>
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
* _ACP2E-2704_：正在取得無法傳送Cookie。 嘗試重新排序時的「影像訊息」大小
   * _修正備註_：重新排序程式現在不會產生自己的錯誤。 它將依賴購物車列出內建專案檢查。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_：結帳時未選取預設送貨地址
   * _修正附註_：預設送貨地址正在啟用地址搜尋的內容中選取事件。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_： [CLOUD] graphql addProductsToCart api問題包含自訂選項
   * _修正附註_： GraphQL使用不同的自訂選項，將相同的產品正確地新增至購物車
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_：結帳為新客戶時，有多個地址新增至帳戶
   * _修正附註_：系統現在只會在訂單無法建立時儲存一次新的客戶地址，以防止在訂單放置錯誤時建立多個相同的地址。 以前，每次嘗試下訂單時，系統都會儲存新地址，無論是否成功建立訂單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/001e5188>，<https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_：透過訪客訂單重新排序客戶訂單導致出現空購物車
   * _修正附註_：先前透過「訂單與退貨」頁面進行重新排序時，會將客戶重新導向至登入頁面。 套用此修正後，進行重新訂購時，註冊的客戶會被正確重新導向至「檢視購物車」頁面。 此流程的運作方式與訪客客戶相同。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_：角色資源有限的管理員使用者無法檢視購物車
   * _修正附註_：以前，受限制的管理員無法從相關網站的管理員面板中看到捨棄的購物車。 套用此修正後，受限制的管理員可以從管理員面板檢視捨棄的購物車。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>

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
* _AC-12076_： [問題]修正分層導覽上的篩選器專案用詞
   * _修正附註_：系統現在會在階層式導覽篩選專案中正確使用「item」和「items」等字詞，提高篩選說明的清晰度和準確性。 以前，這些字詞的使用不正確，導致導覽篩選選項的使用者可能混淆。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38789>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37852>
* _AC-12164_：自訂選項的日期和時間格式無法運作
   * _修正附註_：系統現在可正確將設定的日期格式套用至日期型別的產品自訂選項，確保日期格式可在前端正確顯示。 先前，日期格式設定的變更不會反映在日期型別的產品自訂選項的前端。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32990>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38925>
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
   * _修正附註_：修正客戶群組相關資訊因要求中X-Magento-Vary的舊值而儲存在錯誤區段的問題
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_：刪除套件組合選項時發生錯誤
   * _修正附註_：系統現在會正確刪除套件組合選項，而不會觸發錯誤或造成頁面無回應。 先前，嘗試刪除套件組合選項會導致「頁面無回應」錯誤並阻止產品儲存。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_： [雲端]影像檔案不存在於New Relic錯誤記錄檔中
   * _修正附註_：系統現在會將自訂預留位置影像同步至本機儲存體，以確保在使用AWS S3等遠端儲存體時，這些影像可正確轉譯。 先前，自訂預留位置影像在使用遠端儲存空間時無法轉譯，導致影像顯示中斷和錯誤記錄。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_： [Cloud]產品媒體庫GQL回應未依影像位置排序
   * _修正附註_：系統現在會依在GraphQL回應中的位置正確排序媒體集中的專案，確保顯示順序準確。 先前，媒體集中的專案並未依位置排序，導致顯示順序不正確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37671>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_： [雲端]子類別專案未顯示在管理後端的Widget編輯上
   * _修正附註_：在新Widget頁面上的類別樹狀目錄應該不會再有載入5級以上類別的問題。 以前，在載入超過第5級類別的樹狀結構時，會遺漏某些類別。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>

### 目錄，框架

* _ACP2E-2949_： [雲端]後續追蹤：檢查資料是否有變更時，資料比較中的不相符
   * _修正附註_：以往，儲存物件在每次都呼叫時不會有任何資料變更（針對任何數值資料欄位，如int/float/double）。 它會觸發標幟_hasDataChanges設為true並呼叫save函式。 它也不會檢查由字串封裝的浮動數字。 此修正套用後，只有在資料變更時，儲存函式才會呼叫。 int/float/double-check的資料值，其值會傳遞至函式，且會執行嚴格的型別比對
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>

### 目錄， GraphQL

* _ACP2E-3090_：在GraphQL中處理類別篩選器： includeDirectChildrenOnly和category_uid
   * _修正附註_：依category_uid篩選時，只會擷取直接子類別。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/93d50f8d>

### 目錄、定價、測試和預覽

* _ACP2E-2672_： [Cloud]特殊價格API端點同時更新大量產品時傳回錯誤
   * _修正附註_：現在特殊價格大量更新API將為每個日期範圍建立單一行銷活動，而不是為每個產品和日期範圍建立多個排程更新。 此外，它也會支援並行API請求，以更快處理大量SKU。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/f89a447e>

### 目錄、產品

* _AC-7050_：編輯產品中的類別選擇樹狀結構順序與目錄 — >類別中的設定順序不同
   * _修正附註_：系統現在會以目錄 — >類別中設定的相同順序，在產品編輯區段中正確顯示類別選取樹狀結構，讓大型目錄中的產品管理更容易。 以前，產品編輯區段中的類別樹狀結構會以類別建立的順序顯示，無論在目錄 — >類別中設定的顯示順序為何。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36101>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36104>

### 目錄，搜尋

* _ACP2E-2757_：產品未顯示在類別和搜尋上，但直接連結正常運作
   * _修正附註_：以往，具有price_* attribute_code的Yes/No自訂屬性無法與索引搭配使用。 進行此修正後，「是/否」自訂屬性會如預期運作。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_： [雲端]某些類別頁面上的彈性搜尋錯誤
   * _修正附註_：先前已提及組態票證，當我們為多個產品定價0時，會在前端類別頁面擲回例外狀況。 套用此修正後，當多個產品價格0且我們在前端載入類別頁面時，不會擲回任何例外狀況，並將成功載入類別頁面。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8931218>

### 雲端

* _ACP2E-3010_： [Cloud] PHPSESSID正在變更每個POST要求
   * _修正附註_：如果已啟用L2 Redis快取，且客戶已從後端更新，則PHPSESSID不再針對登入客戶的前端區域的POST請求重新產生
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>

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
* _AC-9638_： [問題]產品頁面上WYSIWYG編輯器中的檔案上傳問題
   * _修正附註_：系統現在可正確顯示資料夾樹狀結構，並允許在產品頁面上的WYSIWYG編輯器中上傳影像，即使先展開「影像和視訊」索引標籤亦然。 先前，展開「影像和影片」索引標籤後，導致資料夾樹狀結構未顯示，以及嘗試在WYSIWYG編輯器中上傳影像時出現錯誤訊息。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38026>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_： [內部部署]動態區塊問題
   * _修正附註_：動態區塊中的Widget現在已正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a12063bd>
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
* _ACP2E-3127_： imagecreatetruecolor()：引數#2 ($height)必須大於0。 無法上傳特定影像
   * _修正附註_：解決透過媒體集上傳高度為0的影像時，造成管理員發生錯誤的問題，並成功使用sync命令同步資產。 先前無法透過媒體集上傳影像，當特定影像在媒體集中時，同步命令也會失敗。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_： Prototype.js Array.from與Google Maps API發生衝突
   * _修正附註_： Google地圖現在會在PageBuilder編輯器中正確轉譯。 以前，Javascript錯誤會導致Google地圖無法正確呈現。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/148c3ead>

### 客戶/

* _AC-12162_：前端 — 客戶建立頁面中的出生日期驗證失敗
   * _修正附註_：確認所有驗證都應該在upgrade moment.js系統相依性升級至最新的次要版本之後運作
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/de4dfb8e>

### 框架

* _AC-10654_： V1/customers/password端點問題/問題
   * _修正附註_：現在透過API處理密碼變更請求時，系統會遵守管理GUI內設定的限制，避免可能濫用密碼重設功能。 以前，API可以在管理GUI中定義的規則之外處理密碼變更請求，在已知有效電子郵件時，可能會允許不斷重設電子郵件。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38238>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10838_：目錄搜尋索引程式錯誤索引程式
   * _修正附註_：系統現在會順利完成重新索引命令，不會發生任何錯誤，無論使用PHP編譯的libxml版本為何。 以前，當使用特定版本的libxml編譯PHP時，執行「重新索引」命令會導致「索引處理期間目錄搜尋索引處理錯誤」錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38254>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38553>，<https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_：已將created_at、status和grand_total篩選器新增至客戶「訂單」查詢，並修正多個篩選器失敗
   * _修正附註_：系統現在支援在客戶「訂單」查詢中使用created_at、status和grand_total篩選器，並已解決多個篩選器未正確套用的問題。 以前，系統不支援這些篩選器，且無法在查詢中使用多個篩選器時套用所有篩選器。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38392>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36949>
* _AC-10971_： https://github.com/magento/magento2/issues/38415
   * _修正附註_： PHP 8.2/8.3，目前只有一個相依性失敗php linter： league/flysystem
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub程式碼貢獻_：系統現在支援PHP 8.2/8.3，將league/flysystem套件更新至3.0.20版，確保不會發生PHP Linting錯誤。 以前，透過PHP 8.3的PHP Linter執行PHP檔案時，會導致league/flysystem封裝出現Linting錯誤。
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
* _AC-11651_：Magento嘗試修改LoggerProxy的__wakeUp方法中的唯讀屬性
   * _修正附註_：系統現在允許修改LoggerProxy的__wakeUp方法中先前唯讀的屬性，以確保順利運作，而不會強制使用者採用因應措施。 先前，嘗試重新指派LoggerProxy的__wakeUp方法中唯讀屬性的值會造成問題。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38526>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_：
   * _修正附註_：調查php-amqplib/php-amqplib最新版本
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub程式碼貢獻_：請確定最新版本的php-amqplib/php-amqplib最新版本應該相容
* _AC-11696_： ChangelogBatchWalker無法在多個執行緒中運作
   * _修正附註_：系統現在支援MView索引的處理程式復本，以防止在多個執行緒上執行索引器時出現錯誤。 以前，在多個執行緒上執行ChangelogBatchWalker會導致刪除其他執行緒使用的表格，進而在索引器執行期間造成錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38246>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38248>
* _AC-11781_： [問題]重新命名錯誤的變數
   * _修正附註_：系統現在會正確命名包含仍可退款的金額的變數，以防止在偵錯期間產生混淆。 之前，此變數被錯誤地命名為totalReturn，這可能導致開發人員誤解。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38609>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36205>
* _AC-11808_：
   * _修正附註_：調查並升級Adobe Commerce核心相依性清單
   * _GitHub程式碼貢獻_：需要升級Adobe Commerce核心相依性清單 
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
* _AC-11905_： [問題]靜態內容部署 — 型別錯誤
   * _修正附註_：系統現在會在靜態內容部署期間正確處理空白的LESS檔案，並顯示「LESS檔案是空白的」錯誤訊息。 以前，在部署期間遇到空的LESS檔案時，會擲回不正確的型別錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38682>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38683>
* _AC-12002_： [問題] [檢視]已移除連結和指令碼標籤中的額外空間
   * _修正附註_：系統現在可確保連結和指令碼標籤中沒有額外的空格，提供更乾淨且更有效率的程式碼。 之前，連結和指令碼標籤中的屬性之間可能會出現雙空格字元。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/32920>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32919>
* _AC-12022_：
   * _修正附註_：將獨白/獨白系統相依性升級至最新的主要版本
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub程式碼貢獻_：系統已更新為使用最新主要版本的「獨白/獨白」程式庫，確保相容性並改善效能。 以前，系統使用的是「monolog/monolog」程式庫的過時版本，這可能會導致潛在的問題和限制。
* _AC-12023_：
   * _修正附註_：將wikimedia/less.php相依性升級至最新的主要版本
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub程式碼貢獻_：系統已更新為使用「wikimedia/less.php」程式庫的最新主要版本5.x，確保相容性和最新功能。 之前，系統使用的程式庫版本已過時，這可能會導致安全性問題。
* _AC-12024_：
   * _修正附註_：將jquery/validate程式庫相依性升級至最新的次要版本
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub程式碼貢獻_：將jquery/validate程式庫相依性升級至最新的次要版本
* _AC-12025_：
   * _修正附註_：將moment.js系統相依性升級至最新的次要版本
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub程式碼貢獻_：將moment.js系統相依性升級至最新的次要版本
* _AC-12267_：
   * _修正附註_：支援Redis工作階段的連線重試，並與colimollenhour/php-redis-session-abstract v2.0.0相容
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub程式碼貢獻_：請確定最新版本的colimollenhour/php-redis-session-abstract v2.0.0與adobe commerce相容
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
* _AC-12866_：
   * _修正附註_：移除棄用 — PhpUnit10整合測試
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub程式碼貢獻_：解決PHPUnit棄用問題
* _AC-12868_：
   * _修正附註_：移除棄用 — PhpUnit10 WebApi測試
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub程式碼貢獻_：解決PHPUnit棄用問題
* _AC-12869_： [問題]修正Magento模組中參考的不正確類別。
   * _修正附註_：系統現在會正確參考模組中的類別，確保作業更順暢，並防止因不存在類別而當機。 這包括Indexer和Creditmemo模組中的錯誤修正，以及PrintAction類別中HttpGetActionInterface的實作。 以前，不正確的類別引用會導致錯誤和潛在的系統當機，並且某些功能(例如creditmemoPDF檔案的檔案名稱和庫存的重新索引)無法如預期運作。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/39126>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37784>
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
* _AC-8714_：
   * _修正附註_：塗漆7.3 — 預設類別的子類別連結/選項未顯示在商店首頁上
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/d1c335aa>， &lt;https://github.com/magento/magento2/ （內部，未合併）>>
   * _GitHub程式碼貢獻_： Storefront首頁現在會如預期顯示預設類別子類別。 過去，購物者只能透過URL存取子類別。
* _AC-8714_：塗漆7.3 — 預設類別的子類別連結/選項未顯示在商店首頁上
   * _修正附註_： Storefront首頁現在會如預期顯示預設類別子類別。 過去，購物者只能透過URL存取子類別。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/d1c335aa>，&lt;https://github.com/magento/magento2/ （內部，未合併）>
* _AC-8984_： [問題]在某些安裝程式cli命令的輸出中新增一些顏色
   * _修正附註_：系統現在會為某些安裝程式命令列介面(CLI)命令的輸出加入更多色彩，增強可讀性和使用者體驗。 以前，由於缺少色彩差異，這些指令的輸出比較難以讀取。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/29335>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/29298>
* _AC-9630_：當新增具有必要州/地區的新國家時，升級Magento會重設general/region/state_required。
   * _修正附註_：系統現在只會在新增具有必要狀態的新國家/地區時，將修改過的國家新增至「一般/區域/州_必要」設定，以防止假設該區域已停用的自訂程式碼發生任何中斷。 以前，新增具有必要狀態的國家會將「一般/地區/州_必要」設定重設為具有必要狀態的預設國家/地區，這可能會中斷業務。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37796>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38076>
* _AC-9712_： https://github.com/magento/magento2/issues/37841
   * _修正附註_：具有複雜`calc`運算式的php &amp; nodejs程式庫(grunt)之間較少編譯的差異
   * _GitHub問題_： &lt;&lt;https://github.com/magento/magento2/ （內部，未合併）>>
   * _GitHub程式碼貢獻_：修正php &amp; nodejs程式庫(grunt)之間較少編譯的差異
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

### 框架，GraphQL

* _AC-7976_： [問題]已針對GraphQL結構描述推出自訂純量型別的支援
   * _修正附註_：系統現在支援GraphQL結構描述的自訂純量型別，可讓開發人員定義自訂純量型別和實作。 此功能在表達可能需要驗證的值時特別有用，例如HTML、電子郵件、URL、日期等，以及在更進階的情況下，例如EAV屬性。 之前，系統不支援在GraphQL中處理自訂純量型別。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/36877>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/34651>，<https://github.com/magento/magento2/commit/0574ac23>

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

### 安裝與管理

* _ACP2E-2102_：管理面板中沒有清漆7的匯出VCL按鈕
   * _修正附註_：「Export VCL for Varnish 7」按鈕已新增至「管理」面板。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>

### 庫存/MSI

* _AC-11593_：新增具有屬性的地圖時，Google google API金鑰無法運作
   * _修正附註_：系統現在支援最新的Google Maps API 3.56版，可讓使用者從PageBuilder功能表成功將地圖內容區塊新增到舞台，不會發生任何錯誤。 之前，由於Google地圖API版本的相容性問題，使用者無法新增地圖內容區塊，導致出現「發生錯誤」錯誤訊息。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_： [雲端]產品清單的關鍵問題為空白空間
   * _修正附註_：當產品設定為「無庫存」時，系統現在可正確顯示產品清單，不含空白字元，確保可用產品顯示一致且準確。 之前，將產品設為「無庫存」會導致產品清單中出現空白字元，中斷版面配置，並可能讓客戶感到困惑。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>，<https://github.com/magento/inventory/commit/b59e48ca>

### 訂購

* _AC-10828_：後端訂單總覽畫面：訂單料號層次上未顯示延期交貨數量
   * _修正備註_：系統現在會在後端訂單總覽畫面的quantity欄中顯示延期交貨料號的數目。 這可確保使用者可以準確地追蹤順序中所有專案的狀態。 以前，「數量」欄位只會顯示已訂購、已開立商業發票及已出貨的料號數目，而不會顯示延期交貨的料號數目。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38252>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38320>
* _AC-10994_： [問題]訂單地址轉譯器中使用的存放區識別碼錯誤
   * _修正附註_：系統現在會在轉譯訂單位址時，正確使用與訂單相關聯的商店ID，確保位址已根據其各自的商店ID正確格式化。 先前，系統未正確使用目前的商店ID，若需要傳送來自不同商店的多份訂單電子郵件，可能導致地址格式不正確。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38412>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37932>
* _AC-11798_： [問題]送貨價格在列印的pdf中顯示不同
   * _修正備註_：系統現在會根據稅捐組態設定，以印刷PDF正確顯示出貨價格，確保銷售訂單商業發票檢視頁面與列印商業發票之間的一致性。 以前，無論稅捐組態設定為何，列印PDF中顯示的出貨價格都會排除稅捐。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38608>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38595>，<https://github.com/magento/magento2/commit/1bafc571>
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

### 訂購，退貨

* _ACP2E-2982_：訂單退款導致重複銷退折讓單
   * _修正備註_：當同時執行兩個相同的請求時，透過REST API發出退款，將不再建立重複的銷退折讓單。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/a4fbf702>

### 訂購，稅金

* _ACP2E-3003_： [CLOUD] RESTFUL訂單API中的base_row_total在啟用跨境交易並套用優惠券折扣時不正確
   * _修正備註_：現在，當啟用跨境交易並套用優惠券折扣時，會從RESTFUL訂單API傳回正確的base_row_total。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/9af794a4>

### 其他開發人員工具

* _AC-10658_： [問題]修正visual.phtml中的HTML語法錯誤
   * _修正附註_：系統現在會正確關閉visual.phtml檔案中的開始標籤，確保正確的HTML語法。 之前，啟動標籤未正確關閉，導致HTML語法錯誤。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38247>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37457>
* _AC-11474_： [問題]在bin/magento maintenance：status命令中將「作用中」變更為「已啟用」
   * _修正附註_：系統現在為維護模式命令提供更準確的狀態訊息，將狀態從「作用中」變更為「已啟用」，以及從「非作用中」變更為「已停用」。 之前，維護模式命令的狀態訊息會顯示為「作用中」或「非作用中」，這可能會造成混淆。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38486>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38410>
* _AC-12571_：導覽至類別樹狀結構會導致Redis發生錯誤：「Redis工作階段超過同時連線」
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38851>
   * _GitHub程式碼貢獻_： &lt;https://github.com/magento/magento2/ （內部，未合併）>

### 付款

* _ACP2E-2841_：每次在檢視交易畫面上按一下擷取按鈕時，Payflow都會建立新交易
   * _修正附註_：系統現在會正確擷取交易資訊，而不需在每次按一下檢視交易畫面上的擷取按鈕時建立新的付款交易。 先前，按一下「擷取」按鈕會錯誤地為已支付的訂單建立新的付款交易。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_：加拿大貝寶商家帳戶的PDP中未顯示Paylater訊息
   * _修正備註_：系統現在會在「產品詳細資料頁面(PDP)」上正確顯示加拿大PayPal商家帳戶的PayLater訊息，而可從帳戶帳單地址或出貨來決定買方的國家/地區。 以前，由於缺少引數，不會顯示PayLater訊息，這會導致瀏覽器主控台發生錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/6a185204>

### 效能

* _AC-12000_： [問題]程式碼清理並新增重要標題區塊，以及在資產之前移動重要css
   * _修正附註_：系統現在包含新的關鍵Head區塊，並在資產之前移動關鍵CSS，以便在前端進行更多自訂和效能最佳化。 過去，關鍵CSS並不位於資產之前，限制了自訂和最佳化機會。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38748>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/35580>
* _AC-12176_：當mysql主機包含連線埠資訊時，主題編譯中斷
   * _修正備註_：系統現在可以正確處理包含連線埠資訊的MySQL主機組態，確保主題編譯成功。 以前，如果資料庫連線中的MySQL主機組態包含連線埠資訊，主題編譯將會失敗。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38799>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38842>
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

### 產品

* _AC-10535_：可設定關聯產品名稱中的特殊字元正在轉換成HTML實體。
   * _修正附註_：系統現在會在編輯可設定產品時，正確保留關聯產品名稱中的特殊字元，以防止這些字元轉換為HTML實體。 先前，編輯可設定產品時，關聯產品名稱中的特殊字元會轉換為HTML實體。
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
* _AC-5969_： AlertProcessor — 引數#2數($storeId)必須是int型別，必須提供字串
   * _修正附註_：系統現在會確認商店識別碼為正確的資料型別，以正確觸發產品警示電子郵件。 以前，由於商店識別碼中的型別不符，不會傳送產品警報電子郵件。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/35602>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_： [雲端] addFilterToMap函式無法用於某些資料行
   * _修正附註_：現在，可以在順序格線中使用自訂模組。 先前使用自訂模組時發生錯誤。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/3a7c4d17>

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

### SEO

* _AC-11907_：以重音符號新增URL重寫會造成無限載入
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38692>
   * _GitHub程式碼貢獻_： &lt;https://github.com/magento/magento2/ （內部，未合併）>
* _ACP2E-2641_：多重存放區錯誤的類別URL重寫為第三層級類別
   * _修正附註_：使用自訂範圍URL索引鍵為父系的子系產生正確的URL重寫
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_：「產品名稱」欄位中的雙位元組字元（特殊字元）會封鎖後端中的產品建立
   * _修正附註_：已新增新設定，可讓您將音譯套用至產品URL。 設定可在以下位置使用：商店>設定>目錄>目錄>搜尋引擎最佳化：「為產品URL套用音譯」
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>

### 安全性

* _AC-11855_： [問題]遺失字型CSP付款器快顯功能表
   * _修正附註_：系統現在允許載入字型&#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;，而不違反內容安全性原則指令，確保正確顯示Paylater快顯視窗。 先前，由於違反內容安全性原則指示，導致播放器快顯視窗顯示問題，因此拒絕載入字型。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38624>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/37401>

### 送貨

* _AC-10757_： [問題]修正tracking.phtml中的錯字 — 將JS函式「currier」重新命名為「carrier」
   * _修正附註_：系統現在正確使用辭彙「carrier」，而不是在順序追蹤範本中使用的JavaScript處理常式函式中拼錯的「currier」，以確保正確的函式命名和程式碼明確無誤。 先前，我們使用拼字錯誤的辭彙「currier」，這可能會導致程式碼基底的混淆和不一致。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/34523>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/33414>
* _AC-11938_： UPS REST 「出貨不能以KGS/IN、LBS/CM或OZS/CM作為測量單位」
   * _修正附註_：請確定結帳和購物車中應該顯示UPS費率。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38618>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/493e01f5>
* _ACP2E-2738_：追蹤視窗顯示錯誤的預期傳送日期
   * _修正備註_：顯示Fedex電信業者的正確交貨日期。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_：即使套用免運費，仍顯示表格費率
   * _修正附註_：即使優惠券套用後免費送貨變為可用，現在仍會顯示表格費率送貨方法
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_： MFTF測試AdminCreatingShippingLabelTest失敗，因為Jenkins環境中未新增認證
   * _修正備註_： mftf測試修正
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ea79f7dd>

### 目標定位

* _AC-9432_： [問題]允許在維護允許清單中使用CIDR範圍
   * _修正附註_：系統現在支援在維護模式允許IP清單中使用CIDR範圍，讓一系列IP位址略過維護模式。 以前，維護模式僅允許IP清單允許個人IP地址繞過維護模式。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37943>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/30699>

### 測試架構

* _AC-11491_：
   * _修正附註_： [略過]需要再次取消略過整合測試
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _GitHub程式碼貢獻_：取消略過此PR中跳過的所有整合測試 — https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_：由於JSON欄型別，整合測試未通過testDbSchemaUpToDate
   * _修正附註_：系統現在會在整合測試期間正確辨識資料庫結構描述中的JSON資料行型別，避免因資料庫結構描述與宣告式結構描述不符而造成測試失敗。 以前，系統錯誤地將JSON欄型別識別為MariaDB中的LONGTEXT，導致整合測試失敗。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/ef81f5a2>

### UI框架

* _AC-12128_：
   * _修正附註_： [Cloud] Prototype.js安全性弱點CVE-2020-27511
   * _GitHub問題_： &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub程式碼貢獻_：應解決安全性弱點CVE-2020-27511
* _AC-12128_： [Cloud] Prototype.js安全性弱點CVE-2020-27511
   * _修正附註_：安全性弱點CVE-2020-27511應解決
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_： Grunt Less使用pub/前置詞作為原始程式集
   * _修正備註_：系統現在會在使用grunt時，針對路徑產生較少/css來源地圖（不含/pub前置詞），因此不需要在Web伺服器設定中進行因應措施。 之前，在原始碼對應路徑中使用/pub首碼時，需要在Web伺服器中指定特定的設定才能正常運作。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/38837>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/38840>
* _AC-12950_：在composer.json中更新tinymce 7.3.0並從tinymce 7的檔案中移除
   * _修正附註_：讓TinyMCE 7.x成為Adobe Commerce 2.4.8-beta1的支援版本
   * _GitHub程式碼貢獻_： &lt;https://github.com/magento/magento2/ （內部，未合併）>
* _AC-1306_：正在為停用的模組部署靜態內容
   * _修正附註_：系統現在會從最終的CSS輸出檔案中排除與已停用模組相關的CSS，確保不會載入不必要的樣式。 以前，與已停用模組相關的CSS會包含在最終的CSS輸出檔案中，導致載入額外且不必要的樣式。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/24666>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/32922>
* _AC-9007_： [問題]請勿在前端載入後端區塊內容
   * _修正附註_：系統現在會確保前端未載入後端區塊內容，防止建立不必要的後端工作階段和潛在的工作階段鎖定。 以前，系統在前端錯誤載入後端區塊內容，導致建立後端工作階段和潛在的工作階段鎖定。
   * _GitHub問題_： <https://github.com/magento/magento2/issues/37617>
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_：啟用Recaptcha時檢查禮品卡餘額時發生例外狀況
   * _修正附註_：使用者將可以在檢視和編輯購物車畫面中擷取禮品卡餘額。 以往，啟用reCAPTCHA時不會顯示這些詳細資料。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_： [說明]功能要求ADA合規性
   * _修正附註_：系統現在會移除不支援的CSS屬性，並將它們取代為print.css檔案中支援的屬性，以確保ADA法規遵循。 以往，使用不受支援的CSS屬性會導致瀏覽器相容性問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_： [Cloud] AC 2.4.4-p8的effect-drop.js中的混淆程式庫程式碼
   * _修正附註_：系統現在正確實作effect-drop.js程式庫，確保jQuery UI效果正常運作。 之前，effect-drop.js程式庫錯誤地以effect-clip.js程式庫覆寫，導致jQuery UI效果可能發生問題。
   * _GitHub程式碼貢獻_： <https://github.com/magento/magento2/commit/35b1b1da>
