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
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# 快取概述和設定選項

Adobe Commerce使用多個快取層來減少重複處理、降低資料庫負載並改善回應時間。 這些層會在請求和資產傳送中的不同時間點作業：

- **應用程式快取**&#x200B;會儲存使用Commerce快取型別產生或處理的資料。
- **HTTP全頁快取**&#x200B;會在完成HTTP回應到達Commerce應用程式之前儲存這些回應。
- **L2快取**&#x200B;可以在共用遠端快取儲存體前的每個Web節點上新增本機快取。
- **靜態內容快取**&#x200B;可讓瀏覽器重複使用CSS、JavaScript、影像和其他靜態資源。

此頁面提供這些圖層的概念概觀，及其設定指南的連結。 如需後端選擇、實作詳細資料和特定版本的設定，請參閱[快取後端選項和儲存參考](cache-options.md)。

## 快取圖層

### 應用程式快取

Commerce應用程式快取的組織方式如下：

>[!BEGINSHADEBOX]

快取型別→快取前端→快取後端

>[!ENDSHADEBOX]

**快取型別**&#x200B;可識別要快取的資料型別，例如設定、配置、封鎖HTML或整頁內容。 **快取前端**&#x200B;會將一或多個快取型別連線到儲存體。 **快取後端**&#x200B;提供儲存實作。

當需要不同的快取設定或儲存體時，您可以將不同的快取型別指派給不同的前端。 如需設定詳細資料，請參閱[設定快取前端和型別](cache-types.md)。

### 全頁HTTP快取

HTTP全頁快取會在HTTP或CDN層儲存完整的回應。 對於生產部署：

- **Adobe Commerce內部部署**—Adobe建議使用[Varnish](config-varnish.md)進行整頁快取。 Varnish在網頁伺服器前作為反向Proxy運作。
- 雲端基礎結構上的&#x200B;**Adobe Commerce**&#x200B;使用[Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"}作為邊緣和整頁快取階層。 雲端基礎結構不使用單獨管理的Varnish服務。

>[!NOTE]
>
>變更Commerce應用程式快取後端不會設定Varnish或Fastly。 全頁HTTP快取會與低階應用程式快取分開設定和管理。

### L2快取

L2 （或兩級快取）可在每個Commerce Web節點上新增本機快取，同時保留共用遠端快取儲存空間。 經常存取的資料可在本機提供，減少與多節點部署中遠端快取的通訊。

L2設定和支援的實施因Commerce版本和部署型別而異。 如需詳細資訊，請參閱[L2快取組態](level-two-cache.md)。

### 靜態內容快取

Commerce可透過將部署版本新增至靜態資源（例如CSS、JavaScript和影像）的URL，藉此改善瀏覽器快取功能。 內容變更時，URL會變更，導致瀏覽器請求新資源，而不是使用舊的快取復本。

## 部署特定設定

下列設定工作會因部署型別而異。

| 任務 | 內部部署 | 雲端基礎結構 |
| --- | --- | --- |
| 應用程式快取後端 | [快取後端選項和儲存參考](cache-options.md) | [Valkey與Redis服務組態的最佳實務](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| HTTP全頁快取 | [設定亮漆](config-varnish.md) | [Fastly服務總覽](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) |

下列工作適用於所有部署型別：

- **設定快取型別和前端** [設定快取前端和型別](cache-types.md)以將快取型別與快取前端相關聯。
- **設定L2快取**—[L2快取設定](level-two-cache.md)。
- **設定靜態內容的瀏覽器快取失效**—[靜態內容簽署和瀏覽器快取失效](static-content-signing.md)。
