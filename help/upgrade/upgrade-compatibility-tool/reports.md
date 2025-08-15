---
title: '[!DNL Upgrade Compatibility Tool]個報告'
description: 請依照下列步驟，在您的Adobe Commerce專案上執行 [!DNL Upgrade Compatibility Tool] 。
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# 報表

{{commerce-only}}

分析之後，[!DNL Upgrade Compatibility Tool]可以匯出一份報告，其中包含每個檔案的問題清單，指定其嚴重性、錯誤碼和錯誤描述。 [!DNL Upgrade Compatibility Tool]將報告匯出為兩種不同的格式：

- [JSON檔案](reports.md#json-file)。
- [HTML報告](reports.md#html-report)。

請參閱下列報告的命令列介面範例：

```
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

檢查[錯誤訊息參考](../upgrade-compatibility-tool/error-messages.md)主題，以取得關於此報告可以產生的不同錯誤的詳細資訊。

此報表也包含詳細摘要，其中顯示：

- *目前的版本*：目前安裝的版本。
- *目標版本*：您要升級的目標版本。
- *執行時間*：分析建立報告所花費的時間(mm:ss)。
- *需要更新的模組*：包含相容性問題且需要更新的模組百分比。
- *需要更新的檔案*：包含相容性問題且需要更新的檔案百分比。
- *嚴重錯誤總數*：找到嚴重錯誤的數目。
- *錯誤總數*：找到的錯誤數。
- *警告總數*：找到的警告數目。
- *記憶體尖峰使用量*： [!DNL Upgrade Compatibility Tool]在執行期間達到的記憶體數量上限。

請參閱下列命令列介面範例：

```
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## JSON檔案

在命令列介面上執行[!DNL Upgrade Compatibility Tool]時，您可以取得JSON檔案輸出。 `JSON`檔案包含與[!DNL Upgrade Compatibility Tool]輸出完全相同的資訊：

- 已識別問題的清單。
- 分析的摘要。

對於每個遇到的問題，報告都會提供詳細資訊，例如問題的嚴重性和說明。

若要將此`JSON`檔案匯出至其他輸出資料夾：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

其中引數如下：

- `<dir>`： Adobe Commerce安裝目錄。
- `[=JSON-OUTPUT-PATH]`：匯出`JSON`輸出檔案的路徑目錄。

>[!NOTE]
>
> 輸出資料夾的預設路徑為`var/output/[TIME]-results.json`。

## HTML報表

在命令列介面中或透過[!DNL Site-Wide Analysis Tool]執行工具時，您可以取得HTML報表。 HTML報表也包含：

- 已識別問題的清單。
- 分析的摘要。

![HTML報告 — 摘要](../../assets/upgrade-guide/uct-html-summary.png)

您可以在[!DNL Upgrade Compatibility Tool]分析期間輕鬆瀏覽已識別的問題。

您可以根據最低問題層級篩選報告中顯示的問題（預設值為`WARNING`）。

右上角有一個下拉式清單，可讓您選取不同層級。 識別的問題清單會據此篩選。

![HTML報告 — 下拉式清單使用情形](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 較低問題層級的問題會被刪除，但您會收到通知，讓您一律知道每個模組的已識別問題。

HTML報表也包含四個不同的圖表：

- **依問題嚴重程度的模組**：依模組顯示嚴重程度的分佈。
- **依問題嚴重程度的檔案**：依檔案顯示嚴重程度的分佈。
- **依問題總數排序的模組**：顯示前10個危害最大的模組，並考量警告、錯誤和嚴重錯誤。
- **具有相對大小和問題的模組**：模組包含的檔案越多，其圓圈越大。 模組出現的問題越多，其圓圈就越紅。

這些圖表可讓您識別最容易受損的模組，以及執行升級需要更多工作的模組。

![HTML報告 — 圖表](../../assets/upgrade-guide/uct-html-diagrams.png)

HTML報表圖表也會據此更新，但`Modules with relative sizes and issues`是唯一例外，這是使用原本設定的`min-issue-level`所產生。

如果要檢視`Modules with relative sizes and issues`圖表的不同結果，您必須重新執行命令，為`--min-issue-level`選項提供另一個值。

![HTML報告 — 泡泡圖圖表](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

若要將此HTML報表匯出至其他輸出資料夾：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

其中引數如下：

- `<dir>`： Adobe Commerce安裝目錄。
- `[=HTML-OUTPUT-PATH]`：匯出`.html`輸出檔案的路徑目錄。

>[!NOTE]
>
> 輸出資料夾的預設路徑為`var/output/[TIME]-results.html`。
