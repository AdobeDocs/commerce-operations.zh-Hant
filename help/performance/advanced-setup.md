---
title: 高級設定
description: 審查用於處理大量資料的大型企業系統的最佳做法和建議。
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---

# 高級設定

[!DNL Commerce] 是一種高度靈活且可擴展的產品，它包含各種規模的商戶的解決方案。 本節介紹有關配置的最佳做法和建議 [!DNL Commerce] 處理大量資料、極端負載等企業案例。

## 校準索引效能

在處理大量資料時，重新編製索引可能會成為一個問題。 的 [!DNL Commerce] 團隊選擇了載入量最大的索引和啟用的批處理索引，這允許您設定要在每個迭代上處理的資料的一部分。 這樣，用戶可以根據資料庫中資料的類型和大小調整批處理大小。

要管理此設定，請編輯 `batchRowsCount` 參數 `di.xml` 檔案。 以下索引支援此功能：

* 類別產品索引（目錄模組）
* 價格指數（目錄模組）
* EAV索引（目錄模組）
* 股票指數（CatalogInventory模組）

可以通過調整索引批處理大小變數來調整索引器效能。 這控制索引器一次處理多少個實體。 在某些情況下，我們發現索引時間顯著減少。

例如，如果運行的配置檔案與B2B介質類似，則可以覆蓋配置值 `batchRowsCount` 在 `app/code/Magento/catalog/etc/di.xml` 並覆蓋預設值 `5000` 至 `1000`。 這樣，在預設情況下，整個索引時間從4小時減少到2小時 [!DNL MySQL] 配置。

>[!NOTE]
>
>尚未為目錄規則索引器啟用批處理。 具有大量目錄規則的商家需要調整其 [!DNL MySQL] 配置以優化索引時間。 在這種情況下，編輯 [!DNL MySQL] 配置檔案並將更多記憶體分配給TMP_TABLE_SIZE和MAX_HEAP_TABLE_SIZE配置值（兩者的預設值為16M）將提高此索引器的效能，但將導致 [!DNL MySQL] 佔用更多記憶體。

### 按網站限制客戶組和共用目錄

大量產品SKU、網站、客戶組或共用目錄將影響產品價格和目錄規則索引器的運行時間。 這是因為預設情況下，所有網站都分配給所有客戶組（共用目錄）。

要縮短索引時間，您可以 [從客戶組中排除某些網站（共用目錄）](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites)。

## 設定Redis

有時，一個Redis實例不足以滿足傳入的請求。 我們可以建議幾種解決方案來解決這一情況。

首先， [!DNL Commerce] 允許您為每個快取類型配置單獨的快取儲存。 這允許您安裝與在Magento中註冊的快取類型數量一樣多的單獨Redis實例。 實際上，您可能希望Redis實例用於最常用的快取，如配置、佈局和塊。

另一個解決方案是將配置快取放置在檔案系統上，並將其他快取移到Redis伺服器。 使用此解決方案，您需要一個單獨的工具來集中失效所有Web節點上的配置快取。

您還可以使用Redis群集，該群集執行並行讀/寫操作，並自動增加節點數。 [!DNL Commerce] 不提供此情況的配置，但可以在進行少量自定義時啟動它。

## 設定 [!DNL RabbitMQ]

Magento Open Source和Adobe [!DNL Commerce] 支援消息隊列通過 [!DNL RabbitMQ]。 [!DNL Commerce] 使用此服務可執行大量非同步操作，包括B2B目錄操作和非同步股票更新。 用於向作業伺服器添加更多作業的所有介面都隨產品一起分發，並且可用於第三方擴展範圍內的自定義非同步邏輯實現。 和其他整合一樣， [!DNL Commerce] 提供了示例配置檔案 [!DNL RabbitMQ] 包含所有建議的設定，並且已完全準備好用於生產。

## 拆分資料庫

>[!WARNING]
>
>拆分資料庫功能 [棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 在Adobe Commerce2.4.2版。 請參閱 [從拆分資料庫還原到單個資料庫](../configuration/storage/revert-split-database.md)。

Adobe Commerce允許您配置可擴展的資料庫儲存以滿足不斷增長的業務需要。 您可以設定三個獨立的主資料庫，它們為特定域服務：

* 主（目錄）資料庫
* 簽出資料庫
* 訂單管理系統(OMS)資料庫

要配置其他資料庫，必須建立空資料庫並運行以下命令之一：

對於簽出主資料庫

```bash
bin/magento setup:db-schema:split-quote
```

用於OMS主資料庫

```bash
bin/magento setup:db-schema:split-sales
```

這些命令將特定域表從主資料庫遷移到域資料庫。 它們還改變 [!DNL Commerce] 配置，以允許相應的連接和約束處理。

通過使用單獨的資料庫進行簽出和Oracle Order Management，您可以在資料庫伺服器之間分配負載。 您可以提供更多簽出服務，並每秒處理更多訂單，而不會影響目錄和其他操作的可用性。 我們建議在快閃記憶體或活動銷售期間拆分資料庫，或永久地將它們用於自然高負載項目。 在系統管理員的監督下，應執行資料庫之間當前資料的遷移。  在生產模式下不拆分資料庫。

除了主資料庫， [!DNL Commerce] 允許您配置多個從屬資料庫（系統中聲明的每個資料資源都配置一個）。 從資料庫用作主資料庫或域主資料庫之一的完整副本。 為特定資源上的讀取操作發出該命令。

可以通過運行以下命令來添加從資料庫：

```bash
bin/magento setup:db-schema:add-slave
```

此命令執行配置更改，但不配置複製本身。 這應該手動完成。

拆分主資料庫並設定從資料庫後， [!DNL Commerce] 自動調節到特定資料庫的連接，根據請求類型(POST、PUT、GET等)和資料資源做出決策。 如果 [!DNL Commerce] 或者其擴展對GET請求執行寫操作，系統自動將連接從從資料庫切換到主資料庫。 它與主資料庫的工作方式相同：一旦您使用與簽出相關的表，系統將將所有查詢重定向到特定資料庫。 同時，所有與目錄相關的查詢都將轉到主資料庫。

有關多主/從配置的配置和優點的詳細資訊，請參閱
[拆分資料庫效能解決方案](../configuration/storage/multi-master.md)。

## 提供媒體內容

Magento不提供任何特定整合來提供和傳送媒體內容。 所有常用方法都可用於Magento。

服務媒體內容的最簡單方法是在 [!DNL Varnish] 伺服器。 此方法假定共用檔案系統用於儲存媒體內容或指定到 [!DNL Varnish]。

對於中高負載環境，我們建議使用Content Delivery Network(CDN)服務，如Ambeist、Akamai等。 在使用這些服務時， [!DNL Commerce] 使用經典抽取方法進行內容更新。 必須配置 [!DNL Commerce] 要使用相應CDN服務的URL。 通過將媒體內容移動到CDN，您將大大降低實例的負載。

## 配置日誌儲存

日誌的儲存及其對其他磁碟操作的影響會影響Web節點的可用性，特別是在高負載情況下。 如果您不需要日誌記錄，建議您盡量減少日誌記錄。 您還可以配置日誌記錄，以便它在訪問速度較高的單獨儲存系統中寫入。 請注意，訪問日誌儲存的任何瓶頸都會直接影響將日誌寫入或讀取操作作為其流程一部分的傳入請求的處理。
