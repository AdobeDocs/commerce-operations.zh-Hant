---
title: 設定快取前端
description: 瞭解如何定義快取前端，並將其與Adobe Commerce中的快取型別建立關聯。 探索env.php和di.xml的組態語法。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ae31702797c8754a719e5a5eb39a3924e723c87a
workflow-type: tm+mt
source-wordcount: 454
ht-degree: 0%

---

# 設定快取前端

快取前端是Commerce與快取儲存後端之間的介面。 您可以定義多個前端，每個前端都有不同的後端設定，然後將特定的[快取型別](../cli/manage-cache.md#clean-and-flush-cache-types)指派給每個前端。

如果您想要針對不同型別的快取資料使用不同的快取後端或設定，這會很有用。 例如，您可能會想要在專用的Redis資料庫上進行`full_page`快取，同時使用單獨的資料庫進行`default`快取。

{{cloud-cache-config}}

## 使用預設前端

Commerce提供適用於所有快取型別的`default`快取前端。 它藉由實作[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)前端快取來擴充[Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)。

在大多數情況下，您不需要自訂前端。 您只需要設定後端。 請參閱[快取後端選項](cache-options.md)。

## 定義自訂快取前端

下列步驟將逐步說明將快取前端與快取型別建立關聯的步驟。

### 步驟1：定義快取前端並指派快取型別

若要定義自訂快取前端，請將組態新增至`app/etc/env.php` （覆寫`di.xml`）：

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

其中：

- `<unique frontend id>` — 識別前端的唯一名稱（例如，`default`、`page_cache`、`stale_cache_enabled`）
- `<cache options>` — 此前端的後端型別和選項（請參閱[快取選項](cache-options.md)）
- `<cache type>` — 要指派給此前端的Commerce快取型別（例如，`config`、`layout`、`block_html`、`full_page`）

>[!TIP]
>
>**現代Symfony快取實作(2.4.9+)：**&#x200B;從Commerce 2.4.9開始，您可以將`redis`、`valkey`或`file`等簡化的後端型別與現代Symfony快取實作搭配使用。 請參閱[使用Redis作為預設快取](redis-pg-cache.md)和[使用Valkey作為預設快取](valkey-pg-cache.md)以取得詳細資料。

### 步驟2：設定前端和後端選項

您可以在`env.php`或`di.xml`中指定前端和後端快取組態選項。 此為選擇性工作。 如果您未指定選項，Commerce會使用預設的前端和後端設定。

`env.php`範例：

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

其中：

- `<frontend_type>` — 低階前端快取型別。指定與`Zend\Cache\Core`相容的類別名稱。
如果省略，則使用[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)。

- `<frontend_option>`， `<frontend_option_value>` — Commerce架構在建立時以關聯陣列形式傳遞給前端快取的選項名稱和值。

- `<backend_type>` — 低階後端快取型別。 您可以指定：
   - **現代Symfony快取（2.4.9+，建議）**：簡化名稱，如`redis`、`valkey`或`file`
   - **舊版（Zend型）**：與實作`Zend_Cache_Backend_Interface`的`Zend_Cache_Backend`相容的完整類別名稱

- `<backend_option>`， `<backend_option_value>` — Commerce架構在建立時以關聯陣列形式傳遞給後端快取的選項名稱和值。

>[!NOTE]
>
>**舊版與現代實作：**
>
>- **舊版（Zend型）**： `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **現代（Symfony快取）**： `'backend' => 'redis'` （建議用於Commerce 2.4.9+）
>
>現代Symfony快取實作可透過PSR-6法規遵循、Igbinary序列化、gzip壓縮、Lua指令碼和持續連線提供更優異的效能。

請參閱[Laminas檔案](https://docs.laminas.dev/)，瞭解Zend型選項。 如需Symfony快取組態，請參閱本檔案中的[Redis](redis-pg-cache.md)和[Valkey](valkey-pg-cache.md)文章。
