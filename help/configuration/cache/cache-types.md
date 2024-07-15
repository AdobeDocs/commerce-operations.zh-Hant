---
title: 快取型別
description: 將快取前端與快取型別建立關聯。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# 快取型別

下列步驟將逐步說明將快取前端與快取型別建立關聯的步驟。

## 步驟1：定義快取前端

Commerce應用程式有`default`快取前端可用於任何[快取型別](../cli/manage-cache.md#clean-and-flush-cache-types)。 本節探討如何選擇性地定義具有不同名稱的快取前端，如果您希望自訂前端，這會比較好。

>[!INFO]
>
>若要使用`default`快取型別，您完全不需要修改`env.php`；您修改了Commerce的全域`di.xml`。 請參閱[低階快取選項](cache-options.md)。

您必須指定自訂快取前端`app/etc/env.php`或Commerce的全域`app/etc/di.xml`。

下列範例說明如何在`env.php`檔案中定義它，該檔案會覆寫`di.xml`檔案：

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
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

其中`<unique frontend id>`是用於識別前端的唯一名稱，`<cache options>`是各快取型別（資料庫、Redis等）專屬主題中討論的選項。

## 步驟2：設定快取

您可以在`env.php`或`di.xml`中指定前端和後端快取組態選項。 此為選擇性工作。

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

位置

- `<frontend_type>`是低階前端快取型別。 指定與`Zend\Cache\Core`相容的類別名稱。
若您省略`<frontend_type>`，則會使用[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)。

- `<frontend_option>`、`<frontend_option_value>`是Commerce架構在建立時以關聯陣列形式傳遞給前端快取的選項名稱和值。
- `<backend_type>`是低階後端快取型別。 指定與`Zend_Cache_Backend`相容且實作`Zend_Cache_Backend_Interface`的類別名稱。
- `<backend_option>`和`<backend_option_value>`是Commerce架構在建立後端cache時，以關聯陣列形式傳遞的選項名稱和值。

如需最新的Zend資訊，請參閱[Laminas檔案](https://docs.laminas.dev/)。
