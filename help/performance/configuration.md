---
title: 配置最佳做法
description: 使用這些最佳做法優化您的Adobe Commerce或Magento Open Source部署的響應時間。
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 0%

---

# 配置最佳做法

Commerce提供了許多設定和工具，您可以使用這些設定和工具來縮短頁面上的響應時間，並提供更高的吞吐量。

## 克龍·喬布斯

中的所有非同步操作 [!DNL Commerce] 使用Linux `cron` 的子菜單。 請參閱 [配置並運行cron](../configuration/cli/configure-cron-jobs.md) 正確配置。

## 索引器

索引器可以在 **[!UICONTROL Update on Save]** 或 **[!UICONTROL Update on Schedule]** 的子菜單。 的 **[!UICONTROL Update on Save]** 模式會在目錄或其他資料更改時立即索引。 此模式假定儲存中更新和瀏覽操作強度較低。 在高負載期間，它會導致顯著的延遲和資料不可用。 我們建議使用 **按計畫更新** 模式，因為它儲存有關資料更新的資訊，並通過特定cron作業按背景中的部分執行索引。 可以更改每個 [!DNL Commerce] 索引器  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 的下界。

>[!TIP]
>
>與其他MariaDB或 [!DNL MySQL] 版本。 我們建議修改預設的MariaDB配置設定，如 [安裝先決條件](../installation/prerequisites/database/mysql.md)。

## 快取

在生產中啟動儲存時，請激活 **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** 的子菜單。 我們強烈建議使用 [!DNL Varnish]因為它是一種高效的生產頁快取解決方案。

## 非同步電子郵件通知

啟用「非同步電子郵件通知」設定會將處理簽出和訂單處理電子郵件通知的進程移到後台。 要啟用此功能，請轉到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**。 請參閱 [銷售電子郵件](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 的 _Magento Open Source使用手冊_ 的子菜單。

## 非同步訂單資料處理

有時，在店面進行密集銷售的同時 [!DNL Commerce] 正在執行密集訂單處理。 您可以配置 [!DNL Commerce] 在資料庫級別上區分這兩種通信模式，以避免相應表中讀寫操作之間的衝突。 您可以非同步儲存和索引訂單資料。 訂單將放在臨時儲存中，並批量移動到訂單管理網格中，不會發生任何衝突。 您可以從 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**。 請參閱 [計畫網格更新](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 的 _Magento Open Source使用手冊_ 的子菜單。

>[!WARNING]
>
>的 **[!UICONTROL Developer]** 選項 [開發人員模式](../configuration/cli/set-mode.md)。 [Adobe Commerce在雲基礎架構上](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支援 `Developer` 的子菜單。

## 延遲庫存更新

在密集銷售時， [!DNL Commerce] 可以延遲與訂單相關的庫存更新。 這樣可以最大限度地減少操作次數並加快訂單放置過程。 但是，此選項風險很大，只有在商店中激活「延交」訂單時才可使用，因為此選項可能導致負庫存數量。 此選項可以顯著改善可根據需要輕鬆重新填充庫存的商店的結帳流程。 要激活站點上延遲的庫存更新，請轉到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**。 請參閱 [管理庫存](https://docs.magento.com/user-guide/catalog/inventory.html) 的 _Adobe Commerce使用手冊_ 的子菜單。

>[!INFO]
>
>此選項僅在以下情況下可用 **[!UICONTROL Backorder with any mode]** 的子菜單。

>[!INFO]
>
>此選項也適用於 [非同步訂單放置](high-throughput-order-processing.md#asynchronous-order-placement) 與 [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html)。

## 客戶端優化設定

提高您的店面響應能力 [!DNL Commerce] 實例，轉到「預設」或「開發人員」模式下的「管理員」並更改以下設定：

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 設定組 | 設定 | 值 |
| ------------------- | -------------------------- | ------ |
| 網格設定 | 非同步索引 | 啟用 |
| CSS設定 | 微型CSS檔案 | 是 |
| [!DNL JavaScript] 設定 | 微型 [!DNL JavaScript] 檔案 | 是 |
| [!DNL JavaScript] 設定 | 啟用 [!DNL JavaScript] 捆綁 | 是 |
| 模板設定 | 微型HTML | 是 |

>[!INFO]
>
>的 **[!UICONTROL Developer]** 選項 [開發人員模式](../configuration/cli/set-mode.md)。 [Adobe [!DNL Commerce] 雲基礎架構](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支援 `Developer` 的子菜單。

激活 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 選項，您允許Commerce將所有JS資源合併到一個或一組裝載在儲存前頁中的捆綁包中。 捆綁JS會減少對伺服器的請求，從而提高頁面效能。 它還幫助瀏覽器在第一次調用時快取JS資源，並重新使用這些資源進行所有進一步瀏覽。 此選項還帶來延遲評估，因為所有JS都作為文本載入。 只有在頁面上觸發特定操作後，才啟動代碼的分析和評估。 但是，對於第一頁載入時間非常關鍵的儲存，不建議使用此設定，因為所有JS內容都將在第一次調用時載入。

>[!INFO]
>
>請參閱 [Adobe Commerce雲基礎架構和Adobe Commerce上的CSS和Javascript檔案優化](https://support.magento.com/hc/en-us/articles/360044482152) 在Adobe Commerce幫助中心_中，瞭解有關優化CSS和Javascript的詳細資訊。

### 捆綁提示

* 我們建議您使用第三方工具進行精簡和捆綁(例如 [r.js](https://requirejs.org/))。 [!DNL Commerce] 內置機制不是最佳機制，而是作為備用備選機制發運。
* 激活HTTP2協定是使用JS捆綁的好選擇。 該協定提供了幾乎相同的好處。
* 我們不建議使用不建議使用的設定，如合併JS和CSS檔案，因為它們只設計用於頁面HEAD部分中同步載入的JS。 使用此技術可導致綁定，並要求JS邏輯工作不正確。

## 客戶細分驗證

具有大量 [客戶細分](https://docs.magento.com/user-guide/marketing/customer-segments.html) 客戶操作（如客戶登錄和將產品添加到購物車）可能會導致效能嚴重下降。

客戶操作會觸發客戶段的驗證過程，這可能導致效能下降。 預設情況下，Adobe Commerce即時驗證每個段，以定義哪些客戶段匹配哪些客戶段不匹配。

為避免效能下降，可以設定 **[!UICONTROL Real-time Check if Customer is Matched by Segment]** 系統配置選項 **否** 通過單個組合條件SQL查詢驗證客戶段。

要啟用此優化，請轉到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**。

如果系統中有許多客戶段，此設定將提高客戶段驗證的效能。 但是，它不能 [拆分資料庫](../configuration/storage/multi-master.md) 或當沒有註冊客戶時。

## 資料庫維護計畫 {#database}

我們建議為您的暫存和生產實例執行定期資料庫備份。 由於備份操作的I/O密集性，您可能會遇到備份速度較慢和潛在問題。 由於爭用可用資源，同時運行多個環境的資料庫進程可能會運行較慢。

為了獲得更好的效能，請安排備份在非高峰時間連續運行。 該方法避免了I/O爭用，並縮短了完成時間，特別是對於較小的實例、較大的資料庫等。

例如，我們建議在您的商店遇到訪問次數較低時，先安排生產資料庫的備份，然後安排臨時資料庫。

## 限制網格中的產品數

為了提高大目錄下產品網格的效能，建議使用 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** 系統配置設定。

預設情況下禁用此系統配置設定。 通過啟用它，可以將網格中的產品數量限制為特定值。 **[!UICONTROL Records Limit]** 是預設最小值為 `20000`。
當 **[!UICONTROL Limit Number of Products in Grid]** 啟用設定，並且網格中的產品數大於記錄限制，然後返回有限的記錄集合。 達到限制後，將從網格標題中隱藏找到的總記錄、選定記錄數和分頁元素。

當網格中產品總數有限時，不影響產品網格的質量動作。 它只影響產品網格表示層。 例如， `20000` 產品，用戶按一下 **[!UICONTROL Select All]**&#x200B;的子菜單。 **[!UICONTROL Update attributes]** 成批操作，並更新某些屬性。 因此，所有產品都會更新，而不是有限的 `20000` 記錄。

產品網格限制僅影響UI元件使用的產品集合。 因此，並非所有產品網格都受此限制的影響。 只有那些正在使用 `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`。
您只能限制以下頁面上的產品網格集合：

* 目錄產品網格
* 添加相關/追加銷售/交叉銷售產品網格
* 將產品添加到捆綁產品
* 將產品添加到組產品
* 「管理員：建立順序」頁

如果您不希望產品網格受到限制，我們鼓勵您更準確地使用篩選器來收集結果，以使項目少於 **[!UICONTROL Records Limit]**。
