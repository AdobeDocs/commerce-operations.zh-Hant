---
title: 設定最佳實務
description: 使用這些最佳實務來最佳化Adobe Commerce或Magento Open Source部署的回應時間。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---


# 設定最佳實務

商務提供許多設定和工具，您可用來改善頁面的回應時間，並提供更高的吞吐量。

## Cron作業

中的所有非同步操作 [!DNL Commerce] 使用Linux執行 `cron` 命令。 請參閱 [設定並執行cron](../configuration/cli/configure-cron-jobs.md) 才能正確設定。

## 索引器

索引器可以在 **[!UICONTROL Update on Save]** 或 **[!UICONTROL Update on Schedule]** 模式。 此 **[!UICONTROL Update on Save]** 模式會在目錄或其他資料變更時立即進行索引。 此模式假設您商店中的更新和瀏覽操作強度較低。 它可能導致在高負載期間出現顯著延遲，以及資料不可用。 建議您使用 **按計畫更新** 模式，因為它儲存有關資料更新的資訊，並通過特定cron作業按背景中的部分執行索引。 您可以變更每個 [!DNL Commerce] 索引器  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 設定頁面。

在MariaDB 10.4上重新編製索引所需的時間比其他MariaDB或 [!DNL MySQL] 版本。 建議修改預設的MariaDB配置，並設定下列參數：

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## 快取

在生產環境中啟動儲存時，請啟動 **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** 頁面。 強烈建議使用 [!DNL Varnish]，因為這是有效的生產頁面快取解決方案。

## 非同步電子郵件通知

啟用「非同步電子郵件通知」設定會將處理結帳和訂單處理電子郵件通知的程式移至背景。 若要啟用此功能，請前往 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. 請參閱 [銷售電子郵件](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 在 _Magento Open Source使用手冊_ 以取得更多資訊。

## 非同步訂單資料處理

有時候，在店面進行密集銷售的同時 [!DNL Commerce] 執行密集訂單處理。 您可以設定 [!DNL Commerce] 在資料庫級別上區分這兩種通信模式，以避免相應表中的讀操作和寫操作之間的衝突。 您可以非同步儲存及索引順序資料。 訂單放置在臨時儲存中，並批量移動到「訂單管理」網格中，不會發生任何衝突。 您可以透過 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. 請參閱 [計畫網格更新](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 在 _Magento Open Source使用手冊_ 以取得更多資訊。

>[!WARNING]
>
>此 **[!UICONTROL Developer]** 標籤和選項僅適用於 [開發人員模式](../configuration/cli/set-mode.md). [Adobe Commerce雲基礎架構](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支援 `Developer` 模式。

## 延期庫存更新

在集約銷售時， [!DNL Commerce] 可以推遲與訂單相關的股票更新。 這樣可以最大限度地減少操作數，並加快訂單放置過程。 但是，此選項有風險，只能在商店中激活「延交訂單」時使用，因為此選項可能導致負庫存量。 此選項可大幅改善商店的結帳流程，讓他們可輕鬆隨選重新填入庫存。 若要在您的網站上啟用延期的庫存更新，請前往 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. 請參閱 [管理庫存](https://docs.magento.com/user-guide/catalog/inventory.html) 在 _Adobe Commerce使用手冊_ 以取得更多資訊。

>[!INFO]
>
>只有在 **[!UICONTROL Backorder with any mode]** 已啟用。

## 用戶端最佳化設定

改善您 [!DNL Commerce] 例項，前往「管理員」的「預設」或「開發人員」模式，並變更下列設定：

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 設定群組 | 設定 | 值 |
| ------------------- | -------------------------- | ------ |
| 網格設定 | 非同步索引 | 啟用 |
| CSS設定 | 縮制CSS檔案 | 是 |
| [!DNL JavaScript] 設定 | Minify [!DNL JavaScript] 檔案 | 是 |
| [!DNL JavaScript] 設定 | 啟用 [!DNL JavaScript] 捆綁 | 是 |
| 範本設定 | 微型HTML | 是 |

>[!INFO]
>
>此 **[!UICONTROL Developer]** 標籤和選項僅適用於 [開發人員模式](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] 雲基礎架構](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支援 `Developer` 模式。

當您啟用 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 選項，您可讓商務將所有JS資源合併為一或一組在店面頁面中載入的套件。 將JS捆綁會減少對伺服器的要求，進而改善頁面效能。 也可協助瀏覽器在第一次呼叫時快取JS資源，並重複使用這些資源以供後續瀏覽。 此選項也會帶來延遲評估，因為所有JS都會以文字載入。 只有在頁面上觸發特定動作後，才會啟動程式碼的分析和評估。 不過，若儲存的第一個頁面載入時間極其重要，則不建議使用此設定，因為所有JS內容都會在第一次呼叫時載入。

>[!INFO]
>
>請參閱 [在雲端基礎架構和Adobe Commerce上，在Adobe Commerce上最佳化CSS和Javascript檔案](https://support.magento.com/hc/en-us/articles/360044482152) 在Adobe Commerce說明中心_ ，以取得關於最佳化CSS和Javascript的詳細資訊。

### 捆綁提示

* 建議您使用協力廠商工具進行縮制和捆綁(例如 [r.js](https://requirejs.org/))。 [!DNL Commerce] 內建機制並非最佳機制，會以備援替代方式提供。
* 與使用JS捆綁相比，啟動HTTP2通訊協定可能是個不錯的選擇。 協定提供的好處幾乎相同。
* 我們不建議使用已棄用的設定，例如合併JS和CSS檔案，因為這些設定是專為頁面的「HEAD」區段中同步載入的JS所設計。 使用此技術可能會導致捆綁，並要求JS邏輯無法正常運作。

## 資料庫維護計畫 {#database}

建議您為測試和生產執行個體執行定期資料庫備份。 由於備份操作的I/O密集性，您可能會遇到備份速度較慢和潛在問題。 由於可用資源爭用，同時運行多個環境的資料庫進程可能運行速度較慢。

為了獲得更好的效能，請安排備份連續運行，一次運行一次，在非高峰時間運行。 此方法可避免I/O爭用，並縮短完成時間，尤其是對於較小的實例、較大的資料庫等。

例如，建議您在商店遇到較低造訪次數時，先排程生產資料庫的備份，再排程中繼資料庫。
