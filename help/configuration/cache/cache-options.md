---
title: 快取後端選項和儲存參考
description: 瞭解Adobe Commerce中的快取後端選項，包括檔案系統、Redis、Valkey和資料庫儲存。 探索舊版和現代方法。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: a7e44e5b4ddeda89b9fee08aa29b1a31f521e90a
workflow-type: tm+mt
source-wordcount: 362
ht-degree: 0%

---

# 快取後端選項和儲存參考

{{cloud-cache-config}}

Commerce應用程式使用低階快取前端和後端來提供對快取儲存體的存取權。 Commerce支援數個快取後端和策略，分別適用於不同的使用案例。 此頁面說明可用的後端及其差異。

>[!NOTE]
>
>[Varnish](config-varnish.md)在HTTP層級處理整頁快取，不使用低層級快取後端。

## 後端快取選項

下表總結列出可用的後端快取：

| 後端 | 說明 | 設定指南 |
| ------- | ----------- | ------------------- |
| 檔案系統 | 預設。 將快取資料儲存在`var/cache/`下的檔案中。 不需要設定。 | 不適用 |
| [Redis](config-redis.md) | 記憶體中的資料存放區，用於高效能快取。 | [預設快取使用Redis](redis-pg-cache.md)<br>**注意：Adobe Commerce 2.4.9或更新於2.4.5-p16、2.4.6-p14、2.4.7-p9和2.4.8-p5的修補程式版本不支援Redis快取。 對於不支援Redis的快取設定，請使用Valkey。 如需依版本支援的快取服務，請參閱[系統需求](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/system-requirements)。 |
| [Valkey](config-valkey.md) | 開放原始碼、與Redis相容的替代方案。 | [使用預設快取的Valkey](valkey-pg-cache.md) |
| [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | 資料庫支援的快取。 | [建立自訂快取引擎](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} （Adobe開發人員檔案） |

{{redis-cache-support}}

## 實作方法

Commerce支援兩種後端實作方法。 您選擇的方法取決於您的Commerce版本：

>[!BEGINTABS]

>[!TAB 舊版Zend型快取（2.4.8和更早版本）]

對後端設定使用完整類別名稱：

| 後端 | 類別名稱 |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Valkey | `Magento\Framework\Cache\Backend\Valkey` |

這些與`Zend_Cache_Backend`介面相容。

**設定範例：**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB 現代Symfony快取（建議使用2.4.9及更新版本）]

>[!TIP]
>
>現代Symfony快取實作可透過PSR-6法規遵循、Igbinary序列化、gzip壓縮、Lua指令碼和持續連線提供更優異的效能。

使用簡化的後端型別名稱：

| 後端 | 輸入名稱 |
| ------- | --------- |
| Redis | `redis` |
| Valkey | `valkey` |
| 檔案系統 | `file` |

**設定範例：**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

如需完整的組態選項，請參閱：

- [預設快取使用Redis](redis-pg-cache.md)
- [使用Valkey作為預設快取](valkey-pg-cache.md)
- [L2快取設定](level-two-cache.md)

請參閱[Laminas檔案](https://docs.laminas.dev/)，瞭解舊版Zend型選項。
