---
title: 進階設定
description: 審查用於處理大量資料的大型企業系統的最佳做法和建議。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---


# 進階設定

[!DNL Commerce] 是高度靈活且可擴充的產品，包含適用於各種規模之商戶的解決方案。 本節說明設定的最佳實務和建議 [!DNL Commerce] 處理大量資料、極端負載和其他企業案例。

## 校準索引效能

在處理大量資料時，重新編製索引可能成為一個問題。 此 [!DNL Commerce] 團隊選擇了載入最多的索引和啟用的批處理索引，這允許您設定要在每個迭代上處理的一部分資料。 這樣，用戶就可以根據資料庫中資料的類型和大小調整批處理大小。

若要管理此設定，請編輯 `batchRowsCount` 參數 `di.xml` 相應模組的檔案。 下列索引支援此功能：

* 類別產品索引（目錄模組）
* 價格指數（目錄模組）
* EAV索引（目錄模組）
* 股票指數（CatalogInventory模組）

通過調整索引批次大小變數，可以調整索引器效能。 這控制索引器一次處理多少個實體。 在某些情況下，我們發現索引時間顯著減少。

例如，如果您執行的設定檔類似B2B媒體，則可以覆寫設定值 `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` 和覆寫的預設值 `5000` to `1000`. 這樣，在預設情況下，完整索引時間從4小時縮短到2小時 [!DNL MySQL] 設定。

>[!NOTE]
>
>尚未為目錄規則索引器啟用批次處理。 具有大量目錄規則的商戶需要調整 [!DNL MySQL] 優化索引時間的配置。 在此情況下，請編輯 [!DNL MySQL] 配置檔案並將更多記憶體分配給TMP_TABLE_SIZE和MAX_HEAP_TABLE_SIZE配置值（兩者的預設值為16M）將改善此索引器的效能，但將導致 [!DNL MySQL] 耗用更多RAM。

### 依網站限制客戶群組和共用目錄

大量產品SKU、網站、客戶群組或共用目錄都會影響產品價格和目錄規則索引器的執行時間。 這是因為依預設，所有網站都會指派給所有客戶群組（共用目錄）。

要縮短索引時間，您可以 [從客戶群組中排除某些網站（共用目錄）](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## 設定Redis

有時，一個Redis實例不足以處理傳入的請求。 我們可以建議幾種解決方案來解決此情況。

首先， [!DNL Commerce] 允許您為每個快取類型配置單獨的快取儲存。 這可讓您安裝與Magento中註冊的快取類型數量一樣多的個別Redis執行個體。 實際上，您可能希望Redis實例用於最常使用的快取，如配置、佈局和塊。

另一個解決方案是將配置快取放置在檔案系統上，並將其他快取移到Redis伺服器。 使用此解決方案，您需要個別工具，以集中失效所有Web節點上的組態快取。

您也可以使用Redis群集，該群集執行並行讀/寫操作，並自動增加節點數。 [!DNL Commerce] 不提供此情況的設定，但可透過微幅自訂來啟動。

## 設定 [!DNL RabbitMQ]

Magento Open Source與Adobe [!DNL Commerce] 支援通過 [!DNL RabbitMQ]. [!DNL Commerce] 使用此服務執行許多非同步操作，包括B2B目錄操作和非同步庫存更新。 用於向作業伺服器添加更多作業的所有介面均隨產品一起分發，並可用於第三方擴展範圍中的定製非同步邏輯實施。 和任何其他整合一樣， [!DNL Commerce] 提供的組態檔範例 [!DNL RabbitMQ] 包含所有建議的設定，且已完全準備好供生產使用。

## 分割資料庫

>[!WARNING]
>
>拆分資料庫功能是 [已棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 在2.4.2版Adobe Commerce中。 請參閱 [從拆分資料庫還原到單個資料庫](../configuration/storage/revert-split-database.md).

Adobe Commerce允許您配置可擴展的資料庫儲存，以滿足不斷增長的業務的需要。 您可以設定三個獨立的主資料庫，為特定域提供服務：

* 主（目錄）資料庫
* 簽出資料庫
* 訂單管理系統(OMS)資料庫

要配置其他資料庫，必須建立空資料庫並運行以下命令之一：

對於結帳主資料庫

```bash
bin/magento setup:db-schema:split-quote
```

用於OMS主資料庫

```bash
bin/magento setup:db-schema:split-sales
```

這些命令將特定域表從主資料庫遷移到域資料庫。 它們也會變更 [!DNL Commerce] 配置，以允許進行相應的連接和約束處理。

通過為結帳和Order Management分別設定資料庫，您可以在資料庫伺服器之間分配負載。 您可以提供更多結帳，並每秒處理更多訂單，而不會影響目錄和其他作業的可用性。 我們建議將資料庫拆分為快閃記憶體或活動銷售期間，或永久用於自然高負載項目。 資料庫之間的當前資料遷移應在系統管理員的監督下執行。  在「生產」模式下，請勿拆分資料庫。

除了主資料庫外， [!DNL Commerce] 允許配置多個從資料庫（系統中聲明的每個資料資源各一個）。 從資料庫用作主資料庫或域主資料庫之一的完整副本。 會針對特定資源的讀取操作而發出。

通過運行以下命令，可以添加從資料庫：

```bash
bin/magento setup:db-schema:add-slave
```

此命令執行配置更改，但不配置複製本身。 這應該手動完成。

拆分主資料庫並設定從資料庫後， [!DNL Commerce] 自動調整與特定資料庫的連線，根據請求類型(POST、PUT、GET等)和資料資源做出決策。 若 [!DNL Commerce] 或者其擴展對GET請求執行寫操作，系統自動將連接從從資料庫切換到主資料庫。 它與主資料庫的工作方式相同：當您使用與結帳相關的表格時，系統會將所有查詢重新導向至特定資料庫。 同時，所有與目錄相關的查詢都將轉到主資料庫。

有關配置以及多個主/從配置優勢的詳細資訊，請參見
[拆分資料庫效能解決方案](../configuration/storage/multi-master.md).

## 提供媒體內容

Magento不提供任何特定整合，以提供和傳送媒體內容。 所有常見方法都可在Magento中搭配使用。

提供媒體內容最簡單的方式，是透過 [!DNL Varnish] 伺服器。 此方法假設共用檔案系統用於儲存媒體內容，或使用指向 [!DNL Varnish].

若是中型和高負載環境，建議您使用內容傳遞網路(CDN)服務，例如Amply、Akamai等。 使用這些服務時， [!DNL Commerce] 內容更新會使用傳統的提取方法。 您必須設定 [!DNL Commerce] URL以搭配對應的CDN服務運作。 將媒體內容移至CDN後，例項的負載將大幅減輕。

## 配置日誌儲存

日誌的儲存及其對其他磁碟操作的影響會影響Web節點的可用性，特別是在高負載情況下。 如果您不需要，建議您盡量減少記錄。 您也可以配置日誌記錄，以便它寫入訪問速度快的單獨儲存系統。 請注意，訪問日誌儲存的任何瓶頸都可能直接影響作為其流程的一部分執行日誌寫入或讀取操作的傳入請求的處理。
