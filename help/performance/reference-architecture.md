---
title: 參考體系結構
description: 查看建議的Adobe Commerce和Magento Open Source部署參考體系結構圖。
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# 參考體系結構

本主題介紹一種通用的建議設定，用於使用物理托管在資料中心（未虛擬化）中且資源不與其他用戶共用的普通伺服器進行Adobe Commerce和Magento Open Source實例。 您的托管提供商，尤其是如果它專門從事商務高效能托管業務，可能會建議使用同樣或更有效的其他設定來滿足您的要求。

有關Adobe Commerce雲基礎架構環境的資訊，請參見 [入門級體系結構](https://devdocs.magento.com/cloud/architecture/starter-architecture.html)。

## [!DNL Commerce] 參考體系結構圖

的 [!DNL Commerce] 參考體系結構圖表示設定可擴展的最佳做法 [!DNL Commerce] 的子菜單。

圖中每個元素的顏色指示該元素是Magento Open Source還是Adobe Commerce的一部分，以及是否需要。

* 橙色元素是Magento Open Source
* 灰色元素是可選的Magento Open Source
* 藍色元素是Adobe Commerce的可選

![商業參考體系結構圖](../assets/performance/images/ref-architecture-2.3.png)

以下各節為「商業參考體系結構」圖的每個部分提供了建議和注意事項。

### [!DNL Varnish]

* A [!DNL Varnish] 群集可以擴展到站點的流量
* 根據所需的快取頁數調整實例大小
* 在高流量站點上，使用 [!DNL Varnish] Master確保在快取上刷新每個Web層一個請求（最多）

### Web

* 為通信量和冗餘啟用節點規模
* 一個節點是主節點並運行cron
* 或者，使用專用的Admin和Worker節點

### 快取

* 考慮為會話實施單獨的Redis實例
* 每個快取可以有一個Redis實例
* 將實例大小設定為包含最大預期快取大小

### 資料庫和隊列

* 高流量站點可以使用從屬資料庫調整資料庫效能，並為訂單/購物車拆分資料庫(在Adobe Commerce)
* 考慮使用從屬DB來啟用快速恢復和資料備份
* 低流量站點可以將映像儲存在資料庫中

### 搜索

* 根據搜索流量調整實例數

### 儲存

* 考慮將GFS或GlusterFS用於pub/媒體儲存
* 或者，對低流量站點使用資料庫儲存

### 推薦 [!DNL Varnish] 參考體系

Magento支援多個全頁快取引擎(檔案、Memcache、Redis、 [!DNL Varnish])開箱即用，並通過擴展擴展擴展覆蓋。 [!DNL Varnish] 是建議的全頁快取引擎。  [!DNL Commerce] 支援多種不同的 [!DNL Varnish] 配置。

對於不需要高可用性的站點，我們建議使用一個簡單的 [!DNL Varnish] 設定，並終止Nginx SSL。

![簡單 [!DNL Varnish] 使用SSL終止進行配置](../assets/performance/images/single-varnish-with-ssl-termination.png)

對於需要高可用性的站點，我們建議使用2層 [!DNL Varnish] 使用SSL終止負載平衡器進行配置。

![高可用性兩層 [!DNL Varnish] 使用SSL終止負載平衡器進行配置](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
