---
title: 進階設定
description: 檢閱專為處理大量資料而設計的大型企業系統的最佳實務和建議。
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# 進階設定

[!DNL Commerce] 是一款高度靈活且可擴充的產品，包含各種規模商家的解決方案。 本節涵蓋設定的最佳實務和建議 [!DNL Commerce] 以處理大量資料、極端負載和其他企業案例。

## 校準索引效能

在處理大量資料時，重新索引可能會成為一個問題。 此 [!DNL Commerce] Team選取了載入最多的索引並啟用批次索引，這可讓您設定要在每個疊代上處理的資料部分。 如此一來，使用者就可以根據資料庫中的資料型別和大小調整批次大小。

若要管理此設定，請編輯 `batchRowsCount` 中的引數 `di.xml` 對應模組的檔案。 下列索引支援此功能：

* 類別產品索引（目錄模組）
* 價格索引（目錄模組）
* EAV索引（目錄模組）
* 庫存索引（CatalogInventory模組）

您可以調整索引器批次大小變數，以調整索引器效能。 這會控制索引器一次處理多少個實體。 在部分情況下，我們發現索引時間已大幅減少。

例如，如果您執行類似B2B Medium的設定檔，您可以覆寫設定值 `batchRowsCount` 在 `app/code/Magento/catalog/etc/di.xml` 並覆寫預設值 `5000` 至 `1000`. 預設情況下，完整索引時間從4小時縮短至2小時 [!DNL MySQL] 設定。

>[!NOTE]
>
>我們尚未啟用目錄規則索引器的批次處理程式。 具有大量目錄規則的商戶需要調整其 [!DNL MySQL] 設定以最佳化索引時間。 在此案例中，編輯 [!DNL MySQL] 組態檔和配置更多記憶體給TMP_TABLE_SIZE和MAX_HEAP_TABLE_SIZE組態值（兩者預設為16M）將改善此索引器的效能，但會導致 [!DNL MySQL] 耗用更多RAM。

### 依網站限制客戶群組和共用目錄

大量產品SKU、網站、客戶群組或共用目錄將會影響產品價格和目錄規則索引器的執行時間。 這是因為所有網站預設都會指派給所有客戶群組（共用目錄）。

若要減少索引時間，您可以 [從客戶群組中排除某些網站（共用目錄）](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## 設定紅色

有時候，一個Redis例項不足以處理傳入的請求。 我們建議您使用數個解決方案來處理這種情況。

首先， [!DNL Commerce] 可讓您為每種快取型別設定個別的快取儲存體。 這可讓您安裝與在Magento中註冊的快取型別數目相同數目的個別Redis執行個體。 實際上，您可能會想要將Redis例項用於最常使用的快取，例如設定、配置和區塊。

另一種解決方案是將設定快取放在檔案系統上，並將其他快取移動到Redis伺服器。 使用此解決方案，您需要個別工具，以集中讓所有網路節點上的設定快取失效。

您也可以使用Redis叢集，以自動增加的節點數目來執行平行讀取/寫入作業。 [!DNL Commerce] 不提供此情況下的設定，但可透過次要自訂來啟動。

## 設定 [!DNL RabbitMQ]

Adobe Commerce支援透過實作的訊息佇列 [!DNL RabbitMQ]. [!DNL Commerce] 使用此服務執行許多非同步操作，包括B2B目錄操作和非同步庫存更新。 所有用於將更多作業新增至作業伺服器的介面都會隨產品分發，並可在第三方擴充功能的範圍內用於自訂非同步邏輯實施。 如同任何其他的整合， [!DNL Commerce] 提供下列專案的設定檔範例： [!DNL RabbitMQ] 包含所有建議的設定，並已完全準備好用於生產。

## 分割資料庫

>[!WARNING]
>
>分割資料庫功能為 [已棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 在Adobe Commerce 2.4.2版中。 另請參閱 [從分割資料庫還原為單一資料庫](../configuration/storage/revert-split-database.md).

Adobe Commerce可讓您設定可擴充的資料庫儲存空間，以符合成長中企業的需求。 您可以設定三個獨立的主資料庫，提供特定網域：

* 主要（目錄）資料庫
* 簽出資料庫
* 訂單管理系統(OMS)資料庫

若要設定其他資料庫，您必須建立空的資料庫，然後執行下列其中一個命令：

用於簽出主資料庫

```bash
bin/magento setup:db-schema:split-quote
```

針對OMS主資料庫

```bash
bin/magento setup:db-schema:split-sales
```

這些命令會將特定網域表格從主要資料庫移轉至網域資料庫。 它們也會變更 [!DNL Commerce] 設定，以允許處理對應的連線和限制。

藉由擁有用於結帳與Order Management的個別資料庫，您可以在資料庫伺服器之間分配負載。 您可以每秒提供更多結帳與處理更多訂單，而不會影響目錄與其他作業的可用性。 我們建議將資料庫分割為快閃或作用中銷售期間，或永久用於自然高負載的專案。 目前資料在資料庫之間的移轉，應在系統管理員的監督下執行。  在生產模式時不分割資料庫。

除了master資料庫， [!DNL Commerce] 可讓您設定多個從屬資料庫（系統中宣告的每個資料資源各一個）。 從屬資料庫可作為主資料庫或其中一個網域主資料庫的完整復本。 它會針對特定資源的讀取作業發出。

您可以執行下列命令來新增從屬資料庫：

```bash
bin/magento setup:db-schema:add-slave
```

此命令會執行組態變更，但不會設定復寫本身。 這應該以手動方式完成。

分割主資料庫並設定從屬資料庫之後， [!DNL Commerce] 自動調整與特定資料庫的連線，根據要求型別(POST、PUT、GET等)和資料資源做出決策。 如果 [!DNL Commerce] 或其擴充功能會對GET要求執行寫入作業，系統會自動將連線從屬資料庫切換至主資料庫。 它對master資料庫的運作方式相同：當您使用與出庫相關的表格時，系統會將所有查詢重新導向至特定資料庫。 同時，所有與目錄相關的查詢將移至主資料庫。

如需有關設定以及多重主設定/從屬設定的優點之詳細資訊，請參閱
[分割資料庫效能解決方案](../configuration/storage/multi-master.md).

## 提供媒體內容

Magento未提供任何特定整合來服務和提供媒體內容。 您可以在Magento中一起使用所有常見方法。

提供媒體內容的最簡單方式是在 [!DNL Varnish] 伺服器。 此方法假設使用共用檔案系統來儲存媒體內容，或是使用專用伺服器指向 [!DNL Varnish].

對於中負載和高負載環境，我們建議使用內容傳遞網路(CDN)服務，例如Fastly、Akamai等。 使用這些服務時， [!DNL Commerce] 使用傳統提取方法來更新內容。 您必須設定 [!DNL Commerce] 使用對應CDN服務的URL。 將媒體內容移至CDN可顯著減輕執行個體的負載。

## 設定記錄儲存

記錄檔的儲存及其對其他磁碟作業的影響，會影響Web節點的可用性，尤其是在高負載的情況下。 如果您不需要，我們建議您將記錄最小化。 您也可以設定記錄功能，讓記錄功能以高速存取的個別儲存系統寫入。 請注意，任何存取記錄儲存的瓶頸都可能會直接影響內送要求的處理，這些要求會記錄寫入或讀取作業作為其流程的一部分。
