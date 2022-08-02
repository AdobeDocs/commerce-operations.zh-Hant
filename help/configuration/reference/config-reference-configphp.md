---
title: config.php引用
description: 請參見config.php檔案中的值清單。
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# config.php引用

的 `config.php` 檔案包含以下部分：

| 名稱 | 說明 |
| --------- | -------------------|
| `i18n` | 所有內聯翻譯資料。 不支援從此部分讀取。 |
| `modules` | 已啟用和已禁用模組的清單。 |
| `scopes` | 包含相關資訊的商店、商店組和網站的清單。 |
| `system` | 靜態內容部署所需的系統配置。 |
| `themes` | 已安裝主題的配置。 |

## 模組

包含一組模組及其狀態。 如果已啟用模組，則值為1。 否則，值為0。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

瞭解有關 [模組]。

## 作用域

包含範圍配置值的陣列。 它具有以下子節點：

| 名稱 | 說明 |
| ---------- | -----------------------------------|
| `websites` | 網站配置 |
| `groups` | 儲存配置 |
| `stores` | 儲存視圖配置 |

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

瞭解有關 [商業範圍][scopes]。

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

瞭解有關 [特定於系統的配置](config-reference-sens.md)。

## 主題

包含主題配置的一組值。

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

瞭解有關 [主題]。

<!-- link definitions -->

[模組]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[主題]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html
