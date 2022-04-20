---
title: 配置最佳做法
description: 使用這些最佳做法優化您的Adobe Commerce或Magento Open Source部署的響應時間。
source-git-commit: 09c4d0e09354230c8779b930f085d8c7c131b85b
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# 配置最佳做法

Commerceo提供了許多設定和工具，您可以使用這些設定和工具來縮短頁面上的響應時間，並提供更高的吞吐量。

## 克龍·喬布斯

中的所有非同步操作 [!DNL Commerce] 使用Linux `cron` 的子菜單。 請參閱 [配置並運行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 正確配置。

## 索引器

索引器可以在 **[!UICONTROL Update on Save]** 或 **[!UICONTROL Update on Schedule]** 的子菜單。 的 **[!UICONTROL Update on Save]** 模式會在目錄或其他資料更改時立即索引。 此模式假定儲存中更新和瀏覽操作強度較低。 在高負載期間，它會導致顯著的延遲和資料不可用。 我們建議使用 **按計畫更新** 模式，因為它儲存有關資料更新的資訊，並通過特定cron作業按背景中的部分執行索引。 可以更改每個 [!DNL Commerce] 索引器  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 的下界。

與其他MariaDB或 [!DNL MySQL] 版本。 作為解決方法，我們建議修改預設的MariaDB配置並設定以下參數：

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## 快取

在生產中啟動儲存時，請激活 **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** 的子菜單。 我們強烈建議使用 [!DNL Varnish]因為它是一種高效的生產頁快取解決方案。

## 非同步電子郵件通知

啟用「非同步電子郵件通知」設定會將處理簽出和訂購處理電子郵件通知的流程移到後台。 要啟用此功能，請轉到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**。 請參閱 [銷售電子郵件](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 的 _Magento Open Source使用手冊_ 的子菜單。

## 非同步訂單資料處理

有時，在店面進行密集銷售的同時 [!DNL Commerce] 正在執行密集訂單處理。 您可以配置 [!DNL Commerce] 在資料庫級別上區分這兩種通信模式，以避免相應表中讀寫操作之間的衝突。 您可以非同步儲存和索引訂單資料。 訂單將放在臨時儲存中，並批量移動到訂單管理網格中，不會發生任何衝突。 您可以從 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**。 請參閱 [計畫網格更新](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 的 _Magento Open Source使用手冊_ 的子菜單。

>[!WARNING]
>
>的 **[!UICONTROL Developer]** 選項 [開發人員模式](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html)。 [Adobe Commerce在雲基礎架構上](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支援 `Developer` 的子菜單。

## 延遲庫存更新

在密集銷售時， [!DNL Commerce] 可以延遲與訂單相關的庫存更新。 這樣可以最大限度地減少操作次數並加快訂單放置過程。 但是，此選項風險很大，只有在商店中激活「延交」訂單時才可使用，因為此選項可能導致負庫存數量。 此選項可以顯著改善可根據需要輕鬆重新填充庫存的商店的結帳流程。 要激活站點上延遲的庫存更新，請轉到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**。 請參閱 [管理庫存](https://docs.magento.com/user-guide/catalog/inventory.html) 的 _Adobe Commerce使用手冊_ 的子菜單。

>[!INFO]
>
>此選項僅在以下情況下可用 **[!UICONTROL Backorder with any mode]** 的子菜單。

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
>的 **[!UICONTROL Developer]** 選項 [開發人員模式](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html)。 [Adobe [!DNL Commerce] 雲基礎架構](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支援 `Developer` 的子菜單。

激活 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 選項，您允許Commerce將所有JS資源合併到一個或一組裝載在儲存前頁中的捆綁包中。 捆綁JS會減少對伺服器的請求，從而提高頁面效能。 它還幫助瀏覽器在第一次調用時快取JS資源，並重新使用這些資源進行所有進一步瀏覽。 此選項還帶來延遲評估，因為所有JS都作為文本載入。 只有在頁面上觸發特定操作後，才啟動代碼的分析和評估。 但是，對於第一頁載入時間非常關鍵的儲存，不建議使用此設定，因為所有JS內容都將在第一次調用時載入。

>[!INFO]
>
>請參閱 [Adobe Commerce雲基礎架構和Adobe Commerce上的CSS和Javascript檔案優化](https://support.magento.com/hc/en-us/articles/360044482152) 在Adobe Commerce幫助中心_中，瞭解有關優化CSS和Javascript的詳細資訊。

### 捆綁提示

* 我們建議您使用第三方工具進行精簡和捆綁(例如 [r.js](http://requirejs.org/))。 [!DNL Commerce] 內置機制不是最佳機制，而是作為備用備選機制發運。
* 激活HTTP2協定是使用JS捆綁的好選擇。 該協定提供了幾乎相同的好處。
* 我們不建議使用不建議使用的設定，如合併JS和CSS檔案，因為它們只設計用於頁面HEAD部分中同步載入的JS。 使用此技術可導致綁定，並要求JS邏輯工作不正確。

## 資料庫維護計畫 {#database}

我們建議為您的暫存和生產實例執行定期資料庫備份。 由於備份操作的I/O密集性，您可能會遇到備份速度較慢和潛在問題。 由於爭用可用資源，同時運行多個環境的資料庫進程可能會運行較慢。

為了獲得更好的效能，請安排備份在非高峰時間連續運行。 該方法避免了I/O爭用，並縮短了完成時間，特別是對於較小的實例、較大的資料庫等。

例如，我們建議在您的商店遇到訪問次數較低時，先安排生產資料庫的備份，然後安排臨時資料庫。
