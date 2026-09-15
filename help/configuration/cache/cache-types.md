---
title: 設定快取前端和型別
description: 瞭解如何定義快取前端，並將其與Adobe Commerce中的快取型別建立關聯。 探索env.php的設定語法。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%
---
# 設定快取前端和型別

快取前端會將Commerce快取型別連線到快取儲存體。 您可以定義多個前端並為每個前端指派特定的快取型別。

>[!BEGINSHADEBOX]

使用下列關係來判斷快取型別儲存其資料的位置：

快取型別→快取前端→快取後端

>[!ENDSHADEBOX]

如需Commerce快取架構的概觀，請參閱[快取概觀和設定選項](caching-overview.md)。

>[!NOTE]
>
>對於雲端基礎結構上的Adobe Commerce，請使用雲端指南中說明的[雲端部署設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml)。 請勿直接編輯`app/etc/env.php`。 部署工具會產生此檔案並覆寫手動變更。

## 使用預設前端

Commerce提供預設前端，可供所有快取型別使用。

在大多數情況下，您不需要定義自訂前端。 如果所有快取型別都可以使用相同的後端和後端選項，請使用預設的前端並設定其後端。 如需後端特定的設定，請參閱[快取後端選項](cache-options.md)。

對於2.4.9之前的Adobe Commerce版本，預設前端會使用舊版Zend型快取實作。 `Magento\Framework\Cache\Core`前端延伸`Zend_Cache_Core`。 Adobe Commerce 2.4.9及更新版本使用現代化的Symfony實作。 如需特定版本的指南，請參閱[快取後端選項](cache-options.md)。

## 定義自訂前端

當一或多個快取型別需要與預設前端不同的後端設定時，請使用自訂快取前端。

對於內部部署，請在`app/etc/env.php`中定義前端。 然後指派一或多個快取型別給它：

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

其中：

- `<frontend-id>`是前端的唯一識別碼，例如`default`或`page_cache`。
- `<backend-type>`會識別前端所使用的後端。 支援的值取決於Adobe Commerce發行版本和選取的後端。
- `backend_options`包含所選後端的選項。
- `<cache-type-id>`是Commerce快取型別，例如`config`、`layout`、`block_html`或`full_page`。


如需後端型別、支援的選項和發行版本特定組態範例，請參閱[快取後端選項](cache-options.md)。

## 將快取型別指派給前端

`type`設定會將快取型別對應到前端：

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

其中：

- `<frontend_type>` — 低階前端快取型別。 指定與`Zend_Cache_Core`相容的類別名稱。
如果省略，則使用[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)。

- `<frontend_option>`， `<frontend_option_value>` — Commerce架構在建立時以關聯陣列形式傳遞給前端快取的選項名稱和值。

- `<backend_type>` — 低階後端快取型別。 您可以指定：
  - **Symfony快取（2.4.9+，建議）**：簡化名稱，如`valkey`或`file`
  - **Zend型**：與實作`Zend_Cache_Backend_Interface`的`Zend_Cache_Backend`相容的完整類別名稱

- `<backend_option>`， `<backend_option_value>` — Commerce架構在建立時以關聯陣列形式傳遞給後端快取的選項名稱和值。

>[!NOTE]
>
>對於後端值格式，例如Zend型類別名稱與Symfony快取簡化名稱（例如`valkey`或`file`），請參閱[快取後端選項](cache-options.md)。

>[!MORELIKETHIS]
>
>- 效能最佳化的[L2快取組態](level-two-cache.md)
>- [管理快取](../cli/manage-cache.md)
