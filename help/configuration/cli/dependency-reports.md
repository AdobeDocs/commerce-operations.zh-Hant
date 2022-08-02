---
title: 依賴關係報告
description: 建立顯示模組、循環和框架依賴項的合計的報告。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---


# 依賴關係報告

{{file-system-owner}}

您可以運行以下類型的報告：

- **模組依賴項**:顯示模組之間依賴關係的總數以及依賴關係是硬的還是軟的。
- **循環依賴項**:顯示每個模組的依賴關係鏈總數以及循環依賴關係的數量和清單。
- **框架依賴項**:按模組顯示對Commerce框架的依賴項總數（包括每個庫的框架條目總數）。

注釋中的依賴關係也是依賴關係。

## 運行依賴關係報告

命令選項：

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

下表說明了此命令的選項、參數和值。

| 參數 | 值 | 需要？ |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | 模組依賴性報告。 | 是 |
| `show-modules-circular` | 循環依賴項報告。 | 是 |
| `show-framework` | 框架依賴性報告。 | 是 |
| `-d --directory` | 開始搜索報表資料的基目錄路徑。 | 否 |
| `-o --output` | 指定報表的逗號分隔值(csv)輸出檔案的絕對檔案系統路徑和檔案名。 | 否 |

如果沒有將目錄或檔案名作為參數傳遞，則以下應用程式根目錄用作預設目錄，並且使用以下預設檔案名：

| 命令 | 檔案名 |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### 「Sample module dependencies 」報告

以下是示例模組依賴關係報告的輸出部分：

```terminal
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### 循環依賴關係報告示例

以下是示例循環依賴關係報告的輸出部分：

```terminal
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### 框架相關性報告示例

以下是示例框架相關性報告輸出的一部分：

```terminal
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
