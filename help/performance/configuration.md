---
title: 設定最佳實務
description: 使用這些最佳實務最佳化Adobe Commerce部署的回應時間。
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# 設定最佳實務

Commerce提供許多設定和工具，可用來改善頁面上的回應時間，並提供更高的輸送量。

## Cron工作

[!DNL Commerce]中的所有非同步作業都是使用Linux `cron`命令執行。 請參閱[設定並執行cron](../configuration/cli/configure-cron-jobs.md)以正確設定。

## 索引子

索引子可以在&#x200B;**[!UICONTROL Update on Save]**&#x200B;或&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;模式中執行。 **[!UICONTROL Update on Save]**&#x200B;模式會在目錄或其他資料變更時立即編制索引。 此模式假設您的存放區中的更新和瀏覽作業強度很低。 在高負載期間，這可能會導致嚴重的延遲和資料無法使用。 基於效能考量，我們建議使用排程&#x200B;**上的**&#x200B;更新，因為它會儲存資料更新的相關資訊，並透過特定的cron工作在背景依部分執行索引。 您可以在&#x200B;**[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]**&#x200B;設定頁面上個別變更每個[!DNL Commerce]索引器的模式。 [!UICONTROL Customer Grid]索引必須一律設定為&#x200B;**[!UICONTROL Update on Save]**&#x200B;模式。

>[!TIP]
>
>與其他MariaDB或[!DNL MySQL]版本相比，在MariaDB 10.4和10.6上重新索引需要更多時間。 我們建議您修改預設的MariaDB組態設定，其說明請參閱[安裝必備條件](../installation/prerequisites/database/mysql.md)。

## 快取

當您在生產環境中啟動商店時，請從「**[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]**」頁面啟動所有快取。 我們強烈建議使用[!DNL Varnish]，因為這是有效的生產頁面快取解決方案。

## 非同步電子郵件通知

啟用「非同步電子郵件通知」設定，將處理結帳和訂單處理電子郵件通知的流程移至背景。 若要啟用此功能，請移至&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**。 如需詳細資訊，請參閱&#x200B;_管理員使用手冊_&#x200B;中的[銷售電子郵件](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails)。

## 非同步處理訂單資料

有時候，店面上的密集銷售會在[!DNL Commerce]執行密集訂單處理的同時發生。 您可以設定[!DNL Commerce]來區分資料庫層級的這兩個流量模式，以避免對應資料表中的讀取和寫入作業發生衝突。 您可以非同步方式儲存及索引訂單資料。 訂單會暫時存放並大量移至Order Management網格，而不會出現任何衝突。 您可以從「**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**」啟用此選項。 如需詳細資訊，請參閱&#x200B;_管理員使用指南_&#x200B;中的[排程網格更新](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing)。

>[!WARNING]
>
>**[!UICONTROL Developer]**&#x200B;索引標籤和選項只能在[開發人員模式](../configuration/cli/set-mode.md)中使用。 雲端基礎結構上的[Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test)不支援`Developer`模式。

## 非同步設定儲存

對於具有大量存放區層級設定的專案，儲存存放區設定可能需要過多的時間或導致逾時。 _非同步設定_&#x200B;模組會執行使用消費者處理訊息佇列中儲存的cron工作，以啟用非同步設定儲存。 AsyncConfig預設為&#x200B;**已停用**。

您可以使用命令列介面啟用AsyncConfig：

```bash
bin/magento setup:config:set --config-async 1
```

`set`命令會將下列內容寫入`app/etc/env.php`檔案：

```conf
...
   'config' => [
       'async' => 1
   ]
```

啟動下列取用者，開始以先進先出方式處理佇列中的訊息：

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## 已延期的庫存更新

在密集銷售期間，[!DNL Commerce]可以延遲與訂單相關的庫存更新。 如此可儘量減少作業次數，並加快下單程式。 但是，此選項有風險，而且只能在啟用商店中的延期交貨訂單時使用，因為此選項可能導致存貨數量為負數。 此選項可大幅改善商店結帳流程的效能，這些商店可輕易地隨選重新補充庫存。 若要啟用您網站上的遞延庫存更新，請前往&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**。 如需詳細資訊，請參閱&#x200B;_Adobe Commerce使用手冊_&#x200B;中的[管理詳細目錄](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud)。

>[!INFO]
>
>此選項僅在啟動&#x200B;**[!UICONTROL Backorder with any mode]**&#x200B;時可用。

>[!INFO]
>
>此選項也可搭配[非同步訂購](high-throughput-order-processing.md#asynchronous-order-placement)和[Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html)使用。

## 使用者端最佳化設定

若要改善[!DNL Commerce]執行個體的店面回應能力，請以預設或開發人員模式前往「管理員」，並變更下列設定：

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]：**

| 設定群組 | 設定 | 值 |
| ------------------- | -------------------------- | ------ |
| 格線設定 | 非同步索引 | 啟用 |
| CSS設定 | 縮制CSS檔案 | 是 |
| [!DNL JavaScript]設定 | 最小化[!DNL JavaScript]個檔案 | 是 |
| [!DNL JavaScript]設定 | 啟用[!DNL JavaScript]組合 | 是 |
| 範本設定 | 縮小HTML | 是 |

>[!INFO]
>
>**[!UICONTROL Developer]**&#x200B;索引標籤和選項只能在[開發人員模式](../configuration/cli/set-mode.md)中使用。 雲端基礎結構](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test)上的[Adobe [!DNL Commerce] 不支援`Developer`模式。

當您啟用&#x200B;**[!UICONTROL Enable [!DNL JavaScript] Bundling]**&#x200B;選項時，可允許Commerce將所有JS資源合併為一個或一組載入店面頁面的組合。 整合JS可減少伺服器要求，進而改善頁面效能。 它還有助於瀏覽器在第一次呼叫時快取JS資源，並在所有進一步的瀏覽中重複使用。 此選項也會帶來延遲評估，因為所有JS都會載入為文字。 它只會在頁面上觸發特定動作後，才會起始程式碼分析和評估。 不過，不建議將此設定用於第一個頁面載入時間極為重要的存放區，因為所有JS內容都將在第一次呼叫時載入。

>[!INFO]
>
>如需最佳化CSS和Javascript的詳細資訊，請參閱Adobe Commerce說明中心雲端基礎結構上Adobe Commerce的[CSS和Javascript檔案最佳化，以及Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152)。

### 套件組合提示

* 建議您使用協力廠商工具進行縮制和組合（例如[r.js](https://requirejs.org/)）。 [!DNL Commerce]個內建機制並非最佳狀態，且已作為備援替代品出貨。
* 啟動HTTP/2通訊協定可能是使用JS套裝的好替代方案。 通訊協定具有許多相同的優點。 在雲端基礎結構專案中，Adobe Commerce預設會啟用此功能。
* 我們不建議使用已棄用的設定，例如合併JS和CSS檔案，因為這些設定是專為頁面的HEAD區段中同步載入的JS而設計。 使用此技術可能會導致套件組合，並要求JS邏輯無法正確運作。

## 客戶區段驗證

具有大量[客戶區段](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)的商家，可能會因為客戶動作（例如客戶登入以及將產品加入購物車）而發生效能大幅降低的情況。

客戶動作會觸發客戶區段的驗證程式，而此程式可能會導致效能降低。 依預設，Adobe Commerce會即時驗證每個區段，以定義哪些客戶區段符合，哪些客戶區段不符合。

為避免效能降低，您可以將&#x200B;**[!UICONTROL Real-time Check if Customer is Matched by Segment]**&#x200B;系統組態選項設為&#x200B;**否**，以透過單一合併條件SQL查詢來驗證客戶區段。

若要啟用此最佳化，請移至&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**。

如果系統中有許多客戶區段，此設定可改善客戶區段驗證的效能。 但是，它無法搭配[分割資料庫](../configuration/storage/multi-master.md)實作使用，或是沒有已註冊的客戶。

## 資料庫維護排程 {#database}

我們建議您為測試及生產執行個體執行定期的資料庫備份。 由於備份作業的I/O密集性質，您可能會遇到備份速度較慢和潛在的問題。 同時針對多個環境執行資料庫處理序可能會因為可用資源的爭用而變慢。

為提升效能，請將備份排程為在非尖峰時間連續執行（一次執行一個）。 此方法可避免I/O爭用，並減少完成時間，尤其是對於較小的執行個體、較大的資料庫等。

例如，建議您在商店遇到較低的造訪次數時，先排程生產資料庫的備份，接著再排程中繼資料庫。

## 限制格線中的產品數量

若要改善大型目錄的產品格線效能，建議使用&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]**&#x200B;系統組態設定來限制格線中的產品數量。

此系統組態設定預設為停用。 一旦啟用，您就可以將格線中的產品數量限製為特定值。 **[!UICONTROL Records Limit]**&#x200B;是可自訂的設定，預設最小值為`20000`。
當啟用**[!UICONTROL Limit Number of Products in Grid]**&#x200B;設定且網格中的產品數目大於記錄限制時，則會傳回有限的記錄集合。 當達到限制時，找到的記錄總數、選取的記錄數以及分頁元素將從網格標頭中隱藏。

當格線中的產品總數有限時，它不會影響產品格線大量動作。 它只會影響產品格線表示層。 例如，格線中的`20000`產品數目有限，使用者按一下&#x200B;**[!UICONTROL Select All]**，選取&#x200B;**[!UICONTROL Update attributes]**&#x200B;大量動作，並更新部分屬性。 因此，所有產品都會更新，而不是有限的`20000`記錄集合。

產品格線限制僅影響UI元件使用的產品集合。 因此，並非所有產品格點都受此限制影響。 僅限使用`Magento\Catalog\Ui\DataProvider\Product\ProductCollection`的客戶。
您只能在下列頁面上限制產品格線集合：

* 目錄產品格線
* 新增相關/向上銷售/交叉銷售產品網格
* 將產品新增至套件組合產品
* 新增產品至群組產品
* 管理員建立訂單頁面

如果您不希望產品格線受到限制，建議您更精確地使用篩選器，使結果集合的專案數少於&#x200B;**[!UICONTROL Records Limit]**。
