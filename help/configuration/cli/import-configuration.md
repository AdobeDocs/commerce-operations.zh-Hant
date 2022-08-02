---
title: 從配置檔案導入資料
description: 從配置檔案導入Adobe Commerce配置設定。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# 導入配置設定

{{file-system-owner}}

使用Commerce 2.2設定生產系統時 [流水線部署模型](../deployment/technical-details.md)，必須 _導入_ 配置設定 `config.php` 和 `env.php` 資料庫中。
這些設定包括配置路徑和值、網站、儲存、儲存視圖和主題。

導入網站、商店、商店視圖和主題後，您可以建立產品屬性並將其應用於生產系統上的網站、商店和商店視圖。

>[!INFO]
>
>的 `bin/magento app:config:import` 命令不處理儲存在環境變數中的配置。

## 導入命令

在生產系統上，運行以下命令以從配置檔案導入資料(`config.php` 和 `env.php`)到資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

使用可選 `[-n, --no-interaction]` 標籤以導入資料而不進行任何交互。

如果輸入 `bin/magento app:config:import` 如果沒有可選標誌，則需要您確認更改。

例如，如果配置檔案包含一個新網站和一個新商店，則會顯示以下消息：

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

要繼續導入，請輸入 `yes`。

如果部署配置檔案包含要導入的某些資料，則會顯示類似以下消息：

```terminal
Start import:
Some information about importing
```

如果部署配置檔案不包含任何要導入的資料，則會顯示類似以下消息：

```terminal
Start import:
Nothing to import
```

## 我們導入的

以下各節詳細討論了我們導入的資料。

### 系統配置

Commerce直接使用 `system` 陣列 `config.php` 或 `env.php` 而不是將檔案導入到資料庫中，因為它們需要一些預處理和後處理操作。

例如，配置路徑的值 `web/secure/base_url` 必須與 [後端](https://glossary.magento.com/backend) 模型。

#### 後端型號

後端模型是處理系統配置更改的機制。
在中定義後端模組 `<module_name>/adminhtml/system.xml`。

所有後端模型必須擴展 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) 類。

導入後端模型時，不會保存配置值。

### 網站、商店和商店組配置

我們導入以下類型的配置。
(這些配置位於 `scopes` 陣列 `config.php`。)

- `websites`:網站相關配置
- `groups`:儲存相關配置
- `stores`:儲存視圖相關配置

以下模式可以導入前面的配置：

- `create`: `config.php` 包含新實體(`websites`。 `groups`。 `stores`)在生產環境中缺失的
- `update`: `config.php` 包含實體(`websites`。 `groups`。 `stores`)與生產環境不同
- `delete`: `config.php` 是 _不_ 包含實體(`websites`。 `groups`。 `stores`)中的

>[!INFO]
>
>我們不導入根 [類別](https://glossary.magento.com/category) 與商店關聯。 必須使用Commerce將根類別與儲存關聯 [管理](https://glossary.magento.com/admin)。

### 主題配置

主題配置包括在您的Commerce系統中註冊的所有主題；資料直接來自 `theme` 資料庫表。 (主題配置位於 `themes` 陣列 `config.php`。)

#### 主題資料的結構

陣列的關鍵是完整主題路徑： `area` + `theme path`

比如說， `frontend/Magento/luma`。
`frontend` 是 `Magento/luma` 是 [主題](https://glossary.magento.com/theme) 路徑。

陣列的值是關於主題的資料：代碼、標題、路徑、父ID

完整示例：

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _主題註冊_。 如果在中定義主題資料 `config.php` 但檔案系統中不存在主題的原始碼，將忽略主題（即，未註冊）。
>- _主題刪除_。 如果中不存在主題 `config.php` 但檔案系統上存在原始碼，主題不會刪除。

