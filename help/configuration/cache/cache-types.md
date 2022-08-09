---
title: 快取類型
description: 將快取前端與快取類型關聯。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# 快取類型

以下步驟將快取前端與快取類型關聯。

## 步驟1:定義快取前端

Commerce應用程式具有 `default` 快取前端可用於任何 [快取類型](../cli/manage-cache.md#clean-and-flush-cache-types)。 本節討論如何選擇使用不同名稱定義快取前端，如果希望自定義前端，則最好使用該名稱。

>[!INFO]
>
>使用 `default` 快取類型，您不需要修改 `env.php` 一點也不；修改Commerce的全球 `di.xml`。 請參閱 [低級快取選項](cache-options.md)。

您必須指定自定義快取前端 `app/etc/env.php` 或商業的全球 `app/etc/di.xml`。

以下示例說明如何在 `env.php` 檔案，該檔案將覆蓋 `di.xml` 檔案：

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

位置 `<unique frontend id>` 是一個唯一的名稱，用於標識您的前台 `<cache options>` 這些選項在每種快取類型（資料庫、Redis等）的特定主題中討論。

## 步驟2:配置快取

可以在中指定前端和後端快取配置選項 `env.php` 或 `di.xml`。 此任務是可選的。

`env.php` 示例：

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

何處

- `<frontend_type>` 是低級前端快取類型。 指定與相容的類的名稱 `Zend\Cache\Core`。
如果忽略 `<frontend_type>`。 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 的子菜單。

- `<frontend_option>`。 `<frontend_option_value>` 是Commerce框架在建立前端快取時作為關聯陣列傳遞的選項的名稱和值。
- `<backend_type>` 是低級後端快取類型。 指定與相容的類的名稱 `Zend_Cache_Backend` 和工具 `Zend_Cache_Backend_Interface`。
- `<backend_option>` 和 `<backend_option_value>` 是Commerce框架建立後作為關聯陣列傳遞給後端快取的選項的名稱和值。

查看 [Laminas文檔](https://docs.laminas.dev/) 查看最新的Zend資訊。
