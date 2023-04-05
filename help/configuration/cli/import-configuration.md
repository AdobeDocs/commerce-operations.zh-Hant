---
title: 從組態檔匯入資料
description: 從組態檔匯入Adobe Commerce組態設定。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# 導入配置設定

{{file-system-owner}}

使用商務2.2設定生產系統時 [管道部署模型](../deployment/technical-details.md)，您必須 _匯入_ 配置設定 `config.php` 和 `env.php` 進入資料庫。
這些設定包括配置路徑和值、網站、儲存、儲存檢視和主題。

匯入網站、商店、商店檢視和主題後，您可以建立產品屬性，並套用至生產系統上的網站、商店和商店檢視。

>[!INFO]
>
>此 `bin/magento app:config:import` 命令不處理儲存在環境變數中的配置。

## 匯入命令

在生產系統上，執行下列命令以從組態檔匯入資料(`config.php` 和 `env.php`)到資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

使用選填 `[-n, --no-interaction]` 標幟，即可在不進行任何互動的情況下匯入資料。

如果您輸入 `bin/magento app:config:import` 若沒有選用標幟，您必須確認變更。

例如，如果設定檔案包含一個新網站和一個新商店，則會顯示下列訊息：

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

若要繼續匯入，請輸入 `yes`.

如果部署配置檔案包含要導入的某些資料，則會顯示類似以下的消息：

```terminal
Start import:
Some information about importing
```

如果部署配置檔案不包含任何要導入的資料，則會顯示類似以下的消息：

```terminal
Start import:
Nothing to import
```

## 我們匯入的

以下幾節將詳細討論我們匯入的資料。

### 系統配置

商務會直接使用 `system` 陣列 `config.php` 或 `env.php` 檔案，而非將它們匯入資料庫，因為它們需要一些前置和後置處理動作。

例如，設定路徑的值 `web/secure/base_url` 必須用後端模型驗證。

#### 後端模型

後端模型是處理系統配置變更的機制。
您可以在 `<module_name>/adminhtml/system.xml`.

所有後端模型都必須擴充 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) 類別。

匯入後端模型時，不會儲存設定值。

### 網站、儲存和儲存組配置

我們匯入下列類型的設定。
(這些設定位於 `scopes` 陣列 `config.php`.)

- `websites`:網站相關配置
- `groups`:儲存相關配置
- `stores`:儲存檢視相關設定

可以以下列模式匯入前述設定：

- `create`: `config.php` 包含新實體(`websites`, `groups`, `stores`)，而生產環境中不存在
- `update`: `config.php` 包含實體(`websites`, `groups`, `stores`)，而與生產環境不同
- `delete`: `config.php` does _not_ 包含實體(`websites`, `groups`, `stores`)存在於生產環境中

>[!INFO]
>
>不會匯入與商店相關聯的根類別。 您必須使用商務管理員將根類別與商店建立關聯。

### 主題配置

主題配置包括在您的商務系統中註冊的所有主題；資料會直接從 `theme` 資料庫表。 (主題設定位於 `themes` 陣列 `config.php`.)

#### 主題資料的結構

陣列的關鍵是完整主題路徑： `area` + `theme path`

例如， `frontend/Magento/luma`.
`frontend` 是區域， `Magento/luma` 是主題路徑。

陣列的值是關於主題的資料：代碼，標題，路徑，上層id

完整範例：

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
>- _主題註冊_. 如果主題資料定義於 `config.php` 但檔案系統中不存在主題的原始碼，主題被忽略（即未註冊）。
>- _主題移除_. 如果主題未出現在 `config.php` 但檔案系統上存在原始碼，不會刪除主題。

