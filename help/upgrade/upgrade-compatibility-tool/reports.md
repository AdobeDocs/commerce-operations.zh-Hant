---
title: '"[!DNL Upgrade Compatibility Tool] reports」'
description: 請依照下列步驟執行 [!DNL Upgrade Compatibility Tool] Adobe Commerce專案。
source-git-commit: 147ecbc66eaf370e7ffaad0b6fce8b41f40b70df
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# 報表

{{commerce-only}}

經分析， [!DNL Upgrade Compatibility Tool] 可匯出包含每個檔案問題清單的報表，指定其嚴重性、錯誤碼和錯誤說明。 此 [!DNL Upgrade Compatibility Tool] 將報表匯出為兩種不同格式：

- A [JSON檔案](reports.md#json-file).
- 安 [HTML報表](reports.md#html-report).

請參閱以下報表的命令列介面範例：

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

檢查 [錯誤訊息參考](../upgrade-compatibility-tool/error-messages.md) 主題，以取得此報表可產生之不同錯誤的詳細資訊。

此報表也包含詳細摘要，顯示：

- *最新版本*:當前安裝的版本。
- *目標版本*:要升級到的版本。
- *執行時間*:建立報表所花費的分析時間(mm:ss)。
- *需要更新的模組*:包含相容性問題且需要更新的模組的百分比。
- *需要更新的檔案*:包含相容性問題且需要更新的檔案的百分比。
- *嚴重錯誤總數*:發現的嚴重錯誤數。
- *總錯誤*:找到的錯誤數。
- *警告總數*:找到的警告數。
- *記憶體峰值使用率*:最大記憶體量 [!DNL Upgrade Compatibility Tool] 已在執行期間達到。

請參閱下列命令列介面範例：

```terminal
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

您可以在執行 [!DNL Upgrade Compatibility Tool] 在命令列介面上。 此 `JSON` 檔案包含與 [!DNL Upgrade Compatibility Tool] 輸出：

- 已識別問題的清單。
- 分析摘要。

對於每個遇到的問題，報告都提供詳細資訊，如問題的嚴重性和說明。

若要匯出此 `JSON` 檔案放入不同的輸出資料夾：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

其中引數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `[=JSON-OUTPUT-PATH]`:要導出的路徑目錄 `JSON` 輸出檔案。

>[!NOTE]
>
> 輸出資料夾的預設路徑為 `var/output/[TIME]-results.json`.

## HTML報表

在命令列介面上執行工具時，或透過 [!DNL Site-Wide Analysis Tool]. 「HTML」報表也包含：

- 已識別問題的清單。
- 分析摘要。

![HTML報告 — 摘要](../../assets/upgrade-guide/uct-html-summary.png)

在 [!DNL Upgrade Compatibility Tool] 分析。

您可以根據最低問題層級(預設值為 `WARNING`)。

右上角有一個下拉式清單，可讓您選取不同的層級。 已識別問題的清單會據此篩選。

![HTML報表 — 下拉式清單使用量](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 問題層級較低的問題會遭移除，但您會收到通知，以便隨時了解每個模組所識別的問題。

「HTML」報表也包含四個不同的圖表：

- **按問題嚴重性列出的模組**:按模組顯示嚴重性分佈。
- **按問題嚴重性列出的檔案**:按檔案顯示嚴重性分佈。
- **按問題總數排序的模組**:顯示10個最易損的模組，並考慮警告、錯誤和嚴重錯誤。
- **具有相對大小和問題的模組**:模組包含的檔案越多，其圓圈就越大。 模組的問題越多，其圓圈就越紅。

這些圖表允許您識別最易損害的模組，以及執行升級需要更多工作的模組。

![HTML報告 — 圖表](../../assets/upgrade-guide/uct-html-diagrams.png)

HTML報表圖表也會據此更新，惟下列情況除外： `Modules with relative sizes and issues`，此元素會以 `min-issue-level` 那是最初設定的。

如果您想查看 `Modules with relative sizes and issues` 圖表中，必須重新運行為 `--min-issue-level` 選項。

![HTML報表 — 泡泡圖圖](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

要將此HTML報告導出到其他輸出資料夾：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

其中引數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `[=HTML-OUTPUT-PATH]`:要導出的路徑目錄 `.html` 輸出檔案。

>[!NOTE]
>
> 輸出資料夾的預設路徑為 `var/output/[TIME]-results.html`.
