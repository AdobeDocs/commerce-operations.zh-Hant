---
title: config.php參考
description: 請參閱config.php檔案中的值清單。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# config.php參考

此 `config.php` 檔案包含下列章節：

| 名稱 | 說明 |
| --------- | -------------------|
| `i18n` | 所有內嵌轉譯資料。 不支援從本節讀取。 |
| `modules` | 已啟用和已禁用模組的清單。 |
| `scopes` | 包含相關資訊的商店、商店群組和網站的清單。 |
| `system` | 靜態內容部署所需的系統配置。 |
| `themes` | 已安裝主題的配置。 |

## 模組

包含模組及其狀態的陣列。 如果模組已啟用，則值為1。 否則，值為0。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

深入了解 [模組].

## 作用域

包含範圍配置值的陣列。 其子節點如下：

| 名稱 | 說明 |
| ---------- | -----------------------------------|
| `websites` | 網站設定 |
| `groups` | 儲存配置 |
| `stores` | 儲存檢視設定 |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

深入了解 [商務範圍][scopes].

## 系統

包含系統欄位配置值的陣列。

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

深入了解 [系統特定配置](config-reference-sens.md).

## 主題

包含主題配置的值陣列。

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

深入了解 [主題].

<!-- link definitions -->

[模組]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings
[主題]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/
