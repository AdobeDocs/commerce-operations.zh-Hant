---
title: 從組態檔匯入資料
description: 瞭解如何從組態檔匯入Adobe Commerce組態設定。 探索管道部署和資料庫匯入程式。
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# 匯入組態設定

{{file-system-owner}}

當您使用Commerce 2.2 [管線部署模型](../deployment/technical-details.md)設定生產系統時，必須&#x200B;_從_&#x200B;和`config.php`匯入`env.php`組態設定至資料庫。
這些設定包括配置路徑和值、網站、商店、商店檢視和主題。

匯入網站、商店、商店檢視和主題後，您可以在生產系統上建立產品屬性，並將其套用至網站、商店和商店檢視。

>[!INFO]
>
>`bin/magento app:config:import`命令未處理儲存在環境變數中的組態。

## 匯入命令

在您的生產系統上，執行下列命令，將組態檔（`config.php`和`env.php`）中的資料匯入資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

使用選用的`[-n, --no-interaction]`旗標來匯入資料，而不進行任何互動。

如果您輸入`bin/magento app:config:import`而沒有選擇性的標幟，則必須確認變更。

例如，如果設定檔案包含一個新網站和一個新商店，則會顯示下列訊息：

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

若要繼續匯入，請輸入`yes`。

如果部署組態檔包含要匯入的一些資料，則會顯示類似下列的訊息：

```
Start import:
Some information about importing
```

如果部署組態檔案未包含任何要匯入的資料，則會顯示類似下列的訊息：

```
Start import:
Nothing to import
```

## 匯入的內容

以下幾節將詳細討論我們匯入的資料。

### 系統組態

Commerce直接使用`system`或`config.php`檔案中`env.php`陣列的值，而非將其匯入資料庫，因為這些值需要一些前置和後置處理動作。

例如，必須使用後端模型驗證設定路徑`web/secure/base_url`的值。

#### 後端模型

後端模型是處理系統組態變更的機制。
您在`<module_name>/adminhtml/system.xml`中定義後端模組。

所有後端模型都必須延伸[`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php)類別。

匯入後端模型時，不會儲存設定值。

### 網站、商店和商店群組設定

我們匯入下列型別的組態。
（這些組態位於`scopes`中的`config.php`陣列下。）

- `websites`：網站相關設定
- `groups`：儲存相關設定
- `stores`：存放區檢視相關設定

上述組態可以下列模式匯入：

- `create`： `config.php`包含生產環境中不存在的新實體(`websites`、`groups`、`stores`)
- `update`： `config.php`包含與生產環境不同的實體(`websites`、`groups`、`stores`)
- `delete`： `config.php` _不_&#x200B;包含存在於生產環境中的實體(`websites`、`groups`、`stores`)

>[!INFO]
>
>我們不會匯入與存放區相關聯的根類別。 您必須使用Commerce管理員將根類別與存放區相關聯。

### 主題設定

主題設定包含在Commerce系統中註冊的所有主題；資料直接來自`theme`資料庫表格。 （主題設定在`themes`中的`config.php`陣列中。）

#### 佈景主題資料的結構

陣列索引鍵是完整主題路徑： `area` + `theme path`

例如，`frontend/Magento/luma`。
`frontend`為區域且`Magento/luma`為主題路徑。

陣列的值是有關佈景主題的資料：程式碼、標題、路徑、上層ID

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
>- _主題註冊_。 如果在`config.php`中定義了佈景主題資料，但檔案系統中沒有佈景主題的原始程式碼，則會忽略佈景主題（亦即未註冊）。
>- _主題移除_。 如果`config.php`中不存在主題，但檔案系統上存在原始程式碼，則不會移除主題。
