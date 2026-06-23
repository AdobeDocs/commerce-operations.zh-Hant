---
title: 快取概述和設定選項
description: 瞭解Adobe Commerce中的快取，包括後端儲存、前端設定，以及使用Varnish、Redis、Valkey和L2快取的全頁快取。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: dbc1f6d0edff87130604d4762477ee5892a7aafc
workflow-type: tm+mt
source-wordcount: 589
ht-degree: 0%

---

# 快取概述和設定選項

Adobe Commerce仰賴多層快取架構來減少資料庫負載、將備援處理減至最少，並加速頁面傳送。 在應用程式層級，Commerce會維護十幾種[快取型別](../cli/manage-cache.md#clean-and-flush-cache-types) （例如組態、配置、區塊HTML和集合），每個型別都可以路由至專用儲存後端，例如[Redis](config-redis.md)或[Valkey](config-valkey.md)。 對於內部部署中的整頁快取，Adobe強烈建議[Varnish](config-varnish.md)。 雲端部署上的Commerce使用Fastly。 其他圖層（例如[L2快取](level-two-cache.md)和[靜態內容簽署](static-content-signing.md)）可進一步改善高流量、多節點部署的效能。

本指南說明每個快取階層如何運作，並示範如何設定前端、後端和進階選項以符合您的部署需求。

## 快取前端

快取前端是Commerce與快取儲存後端之間的介面。 您可以定義多個前端，每個前端都有不同的後端設定，然後將特定的[快取型別](../cli/manage-cache.md#clean-and-flush-cache-types)指派給每個前端。  如需設定詳細資料，請參閱[設定快取前端](cache-types.md)。

## 快取後端

快取後端是快取資料的基本儲存機制。 Commerce提供預設的檔案系統後端，但您可以設定其他後端（例如Redis或Valkey），以提升效能和擴充性。 如需可用選項的詳細資訊，請參閱[快取後端選項](cache-options.md)。

## 使用Varnish的全頁快取

[清漆快取](config-varnish.md)是快取記憶體中完整頁面的HTTP加速器。 對於內部部署生產環境，Adobe強烈建議使用Varnish，因為它比內建全頁快取快很多。 雲端環境上的Commerce使用[Fastly](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly)進行整頁快取，而非Varnish。

>[!NOTE]
>
>Varnish會在您的網頁伺服器前以反向Proxy的方式運作，不需要變更Commerce快取後端設定。

## L2 （兩級）快取

使用遠端快取（Redis或Valkey）做為真值來源時，[L2快取](level-two-cache.md)會將快取資料儲存在每個網頁節點的本機。 這樣可減少網頁節點與遠端快取之間的網路流量，進而改善高流量網站的效能。

## 靜態內容快取

[靜態內容簽署](static-content-signing.md)會將部署版本內嵌在檔案URL中，讓靜態資源（CSS、JavaScript、影像）的瀏覽器快取失效。

## 快取術語

[!DNL Commerce]使用下列快取術語：

- **Frontend** — 快取儲存體的介面或閘道，由[Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)實作。
- **快取型別** — 隨[!DNL Commerce]提供的內建型別之一（例如`config`、`layout`、`block_html`、`full_page`）或[自訂型別](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)。
- **後端** — 指定由[Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)實作的[快取儲存體](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)的詳細資料。
- **雙層後端** — 將快取記錄儲存在兩個後端：本機（快速）快取和遠端（共用）快取。 請參閱[L2快取組態](level-two-cache.md)。

## 設定選項

對於前端到型別的對應和快取設定語法：

**內部部署** — 快取設定儲存在兩個檔案中：

- `<magento_root>/app/etc/di.xml` — 全域相依性插入設定。 修改此檔案以變更提供的`default`快取前端。
- `<magento_root>/app/etc/env.php` — 環境特定的設定。 修改此檔案以設定自訂快取前端。 此檔案會覆寫`di.xml`中的對等組態。

如需詳細資訊，請參閱：

- [設定快取前端](cache-types.md) — 將快取前端與特定快取型別建立關聯
- [快取後端選項](cache-options.md) — 後端選項參考

雲端上的&#x200B;**Adobe Commerce** — 使用`.magento.env.yaml`中的`CACHE_CONFIGURATION`設定快取。 檢視[Redis與Valkey服務組態的最佳實務](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md)。
