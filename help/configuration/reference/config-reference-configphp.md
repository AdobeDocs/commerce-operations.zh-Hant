---
title: config.php參考
description: 瞭解Adobe Commerce設定的config.php檔案值和區段。 探索模組、範圍、系統設定和部署最佳實務。
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 1%

---

# config.php參考

`config.php`檔案包含下列區段：

| 名稱 | 說明 |
| --------- | -------------------|
| `i18n` | 所有內嵌翻譯資料。 不支援讀取此區段。 |
| `modules` | 啟用和停用模組的清單。 |
| `scopes` | 包含相關資訊的商店、商店群組和網站清單。 |
| `system` | 靜態內容部署所需的系統設定。 |
| `themes` | 已安裝主題的設定。 |

## 模組

包含模組的陣列及其狀態。 如果已啟用模組，則值為1。 否則，值為0。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

深入瞭解[模組](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html)。

## 範圍

包含範圍設定值的陣列。 它有下列子節點：

| 名稱 | 說明 |
| ---------- | -----------------------------------|
| `websites` | 網站組態 |
| `groups` | 儲存設定 |
| `stores` | 存放區檢視設定 |

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

深入瞭解[Commerce領域](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)。

## 系統

包含系統欄位設定值的陣列。

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

深入瞭解[系統特定組態](config-reference-sens.md)。

## 主題

包含佈景主題設定的值陣列。

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

深入瞭解[主題](https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/)。

