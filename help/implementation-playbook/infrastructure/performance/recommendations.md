---
title: 效能最佳化建議
description: 依照下列建議最佳化Adobe Commerce實作的效能。
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 31c71af854a59381c7793f26ed9b121cd9bcac83
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 0%

---


# 效能最佳化審查

即使效能最佳化可能來自許多方面，但對於大多數情境，還是有一些需要考量的一般建議。 一般建議包括基礎架構元素的設定最佳化、Adobe Commerce後端設定，以及架構擴充性規劃。

>[!TIP]
>
>請參閱 [_效能最佳實務指南_](../../../performance/overview.md) 以取得效能最佳化的詳細資訊。

## 基礎架構

以下各節說明基礎架構最佳化的建議。

### DNS查閱

DNS查詢是尋找網域名稱所屬之IP位址的程式。 瀏覽器必須等到DNS查閱完成，才能下載每個請求的任何內容。 減少DNS查詢對於改善整體頁面載入時間非常重要。

### 內容傳遞網路(CDN)

使用CDN來最佳化資產下載效能。 Adobe Commerce使用Fastly。 如果您有內部部署的Adobe Commerce實作，您也應該考慮新增CDN層。

### Web延遲

資料中心的位置會影響前端使用者的網頁延遲。

### 網路頻寬

充足的網路頻寬是Web節點、資料庫、快取/工作階段伺服器和其他服務之間資料交換的主要需求之一。

由於Adobe Commerce會有效利用快取來達到高效能，因此您的系統可主動與Redis等快取伺服器交換資料。 如果Redis安裝在遠端伺服器上，您必須在Web節點和快取伺服器之間提供足夠的網路通道，以防止讀取/寫入作業出現瓶頸。

### 作業系統（作業系統）

與其他高負載Web應用程式相比，Adobe Commerce的作業系統設定和最佳化相當類似。 隨著伺服器處理的同時連線數目增加，可用的通訊端數目可以完全配置。

### Web節點的CPU

一個CPU核心能夠有效地處理大約2-4個Adobe Commerce請求，而不需要快取。 若要確定需要多少個Web節點/核心來處理所有傳入的請求而不將其放入佇列，請使用以下方程式：

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM設定

最佳化這些設定取決於不同專案的效能測試結果。

- **ByteCode** — 若要在PHP 7上以Adobe Commerce的最大速度運行，您必須啟動 `opcache` 模組，並正確加以設定。

- **APCU**—Adobe建議啟用PHP APCu擴充功能，並設定Composer以最佳化效能。 此擴充功能會快取已開啟檔案的檔案位置，進而提高Adobe Commerce伺服器呼叫（包括頁面、Ajax呼叫和端點）的效能。

- **Realpath_cacheconfiguration** — 最佳化 `realpath_cache` 可讓PHP處理序快取檔案的路徑，而不是在每次頁面載入時查詢它們。

### 網頁伺服器

使用nginx做為Web伺服器只需要稍作重新配置。 nginx網頁伺服器提供更好的效能，而且使用Adobe Commerce的範例設定檔案即可輕鬆設定([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample))。

- 正確使用TCP設定PHP-FPM

- 啟用HTTP/2和Gzip

- 最佳化工作者連線

### 資料庫

本檔案未提供深入的MySQL調整指示，因為每個存放區和環境都不同，但Adobe可以提出一般建議。

Adobe Commerce資料庫（以及任何其他資料庫）對可用於儲存資料和索引的記憶體量很敏感。 為了有效使用MySQL資料索引，可用的記憶體量至少應該接近資料庫中儲存之資料大小的一半。

最佳化 `innodb_buffer_pool_instances` 設定，以避免多個執行緒嘗試存取相同執行個體時發生問題。 的值 `max_connections` 引數應與應用程式伺服器中設定的PHP執行緒總數相關。 使用下列公式計算的最佳值 `innodb-thread-concurrency`：

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### 工作階段快取

工作階段快取是為Redis的個別執行個體設定的良好候選專案。 此快取型別的記憶體設定應考慮網站的購物車放棄策略，以及工作階段預計會保留在快取中的時間。

Redis應配置足夠的記憶體，以保留記憶體中的所有其他快取，達到最佳效能。 區塊快取是決定要設定的記憶體數量的關鍵因素。 區塊快取會隨著網站上的頁數（SKU數量x商店檢視數量）而成長。

### 頁面快取

Adobe強烈建議您在您的Adobe Commerce存放區中使用Varnish來取得完整頁面快取。 此 `PageCache` 程式碼基底中仍存在模組，但應僅將其用於開發目的。

將Varnish安裝在Web層前面的獨立伺服器上。 它應接受所有傳入請求並提供快取頁面副本。 為了讓Varnish能有效處理安全頁面，可在Varnish前面放置SSL終止Proxy。 Nginx可用於此用途。

雖然Varnish整頁快取記憶體失效有效，但Adobe建議為Varnish配置足夠的記憶體，以便在記憶體中儲存最常用的分頁。

### 訊息佇列

Message Queue Framework (MQF)系統允許模組將訊息發佈至佇列。 它也會定義非同步接收訊息的消費者。 Adobe Commerce支援 [!DNL RabbitMQ] 作為傳訊代理人，提供可擴充的平台以傳送及接收訊息。

### 效能測試和監控

我們一律建議您在每個生產版本之前進行效能測試，以取得電子商務平台功能的預估值。 啟動後持續監控，並針對處理尖峰時間制定擴充性與備份計畫。

>[!NOTE]
>
> 雲端基礎結構上的Adobe Commerce已套用上述的基礎結構和架構最佳化，但DNS查詢除外，因為它不在範圍內。

### 搜尋 {#search-heading}

Elasticsearch （或OpenSearch）自Adobe Commerce 2.4版起為必填，但最佳作法也是為2.4版之前的版本啟用。

## 運作模型

除了前述常見的基礎架構最佳化建議之外，還有一些方法可針對特定業務模式和規模提升效能。 因為每種案例都不一樣，本檔案並未針對所有案例提供深入調整指示，但Adobe可提供一些高階選項供您參考。

### Headless架構

有一個專屬於 [headless](../../architecture/headless/adobe-commerce.md). 總而言之，它將店面圖層與平台本身分開。 這仍是相同的後端，但Adobe Commerce不再直接處理請求，而是僅透過GraphQL API支援自訂店面。

### 讓Adobe Commerce保持更新

Adobe Commerce在執行最新版本時永遠會有更好的效能。 即便在每個新版本發行後無法讓Adobe Commerce保持最新狀態，仍建議使用 [升級](../../../upgrade/overview.md) 當Adobe Commerce推出顯著的效能最佳化時。

例如，在2020年，Adobe發佈了Redis層的最佳化，修正了許多低效率、連線問題，以及Redis和Adobe Commerce之間不必要的資料傳輸。 整體效能介於2.3和2.4之間，不分晝夜，而且由於Redis最佳化，在購物車、結帳、同時使用者等方面都有顯著改善。

### 最佳化資料模型

許多問題源自資料，包括錯誤的資料模型、結構不正確的資料以及缺少索引的資料。

如果您正在測試一些連線，這看起來不錯，但在您部署到生產後，您可能會看到效能嚴重下降。 系統整合經銷商必須瞭解如何設計資料模型（尤其是產品屬性）、避免新增不必要的屬性，以及保留影響商業邏輯的強制屬性（例如定價、庫存可用性和搜尋），這點很重要。

對於不會影響商業邏輯但仍必須存在於店面中的屬性，請將它們合併為幾個屬性（例如JSON格式）。

為了最佳化平台效能，如果店面不需要商業邏輯，也不需要從PIM或ERP取得的資料或屬性，就不需要將該屬性新增到Adobe Commerce中。

### 針對擴充能力而設計

對於執行行銷活動且經常面臨流量尖峰時間的企業而言，擴充性非常重要。 可擴充的架構和應用程式設計可在高峰期增加資源，並在高峰期後減少資源。
