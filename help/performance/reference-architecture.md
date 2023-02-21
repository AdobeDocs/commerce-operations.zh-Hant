---
title: 參考架構
description: 檢閱建議的Adobe Commerce和Magento Open Source部署參考架構圖表。
source-git-commit: 065c56f20ba5b1eef8c331c5c2f5649902f1442b
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# 參考架構

本主題說明一般建議的Adobe Commerce設定，以及使用在資料中心（非虛擬化）中實際托管的純伺服器（其中資源不會與其他使用者共用）來Magento Open Source執行個體。 您的托管提供者（尤其是專門從事商務高效能托管的提供者）可能會建議不同的設定，此設定對您的需求同樣或更有效。

有關雲端基礎架構環境的Adobe Commerce，請參閱 [入門架構](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] 參考架構圖

此 [!DNL Commerce] 參考架構圖代表設定可擴充功能的最佳實務方法 [!DNL Commerce] 頁簽。

圖表中每個元素的顏色會指出元素是Magento Open Source或Adobe Commerce的一部分，以及是否必要。

* Magento Open Source需要橘色元素
* 灰色元素是Magento Open Source的選用元素
* 藍色元素是Adobe Commerce的選用元素

![商務參考架構圖](../assets/performance/images/ref-architecture-2.3.png)

以下各節將針對商務參考架構圖表的每個區段提供建議和考量事項。

### [!DNL Varnish]

* A [!DNL Varnish] 群集可以擴展為網站的流量
* 根據所需的快取頁數調整執行個體大小
* 在高流量網站上，使用 [!DNL Varnish] 主版，確保快取刷新每個Web層一個請求（最多）

### Web

* 為通信和冗餘啟用節點規模
* 一個節點是主節點並運行cron
* 或者，使用專用的管理員和工作節點

### 快取

* 考慮為工作階段實作個別的Redis例項
* 每個快取都可以有Redis例項
* 調整實例大小以包含最大的預期快取大小

### 資料庫和隊列

* 高流量網站可使用從資料庫調整資料庫效能，並針對訂單/購物車分割資料庫(在Adobe Commerce中)
* 考慮使用從資料庫以啟用快速恢復和資料備份
* 低流量網站可將影像儲存在資料庫中

### 搜尋 {#search-heading}

* 根據搜尋流量調整例項數

### 儲存

* 考慮將GFS或GlusterFS用於發佈/媒體儲存
* 或者，將資料庫儲存用於低流量站點

### 建議 [!DNL Varnish] 參考架構

Magento支援數個全頁快取引擎(檔案、記憶體快取、密文、 [!DNL Varnish])立即可用，並透過擴充功能擴充涵蓋範圍。 [!DNL Varnish] 是建議的全頁快取引擎。  [!DNL Commerce] 支援許多不同的 [!DNL Varnish] 設定。

對於不需要高可用性的網站，建議使用簡單 [!DNL Varnish] 設定，並終止Nginx SSL。

![簡單 [!DNL Varnish] 配置SSL終止](../assets/performance/images/single-varnish-with-ssl-termination.png)

對於需要高可用性的站點，建議使用2層 [!DNL Varnish] 使用SSL終止負載平衡器進行設定。

![高可用性二層 [!DNL Varnish] 使用SSL終止負載平衡器進行配置](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
