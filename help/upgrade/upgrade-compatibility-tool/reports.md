---
title: '"[!DNL Upgrade Compatibility Tool] 報告」'
description: 按照以下步驟運行 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
source-git-commit: 1ce02c3215b01f64e86383938a257514f0e4257c
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# 報表

{{commerce-only}}

由於分析，本公司 [!DNL Upgrade Compatibility Tool] 可以導出包含每個檔案問題清單的報告，其中指定了其嚴重性、錯誤代碼和錯誤說明。 的 [!DNL Upgrade Compatibility Tool] 將報告導出為兩種不同格式：

- A [JSON檔案](reports.md#json-file)。
- 安 [HTML報告](reports.md#html-report)。

請參見以下報表的命令行介面示例：

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

檢查 [錯誤消息引用](../upgrade-compatibility-tool/error-messages.md) 主題，以瞭解有關此報告可能生成的不同錯誤的詳細資訊。

此報告還包括詳細摘要，其中顯示：

- *當前版本*:當前安裝的版本。
- *目標版本*:要升級到的版本。
- *執行時間*:分析生成報告所花的時間(mm:ss)。
- *需要更新的模組*:包含相容性問題並需要更新的模組的百分比。
- *需要更新的檔案*:包含相容性問題並需要更新的檔案的百分比。
- *嚴重錯誤總數*:發現的嚴重錯誤數。
- *錯誤總數*:找到的錯誤數。
- *警告總數*:找到的警告數。
- *記憶體峰值使用*:最大記憶體量 [!DNL Upgrade Compatibility Tool] 已在執行過程中到達。

請參見以下命令行介面示例：

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

您可以在運行 [!DNL Upgrade Compatibility Tool] 命令行介面。 的 `JSON` 檔案包含與 [!DNL Upgrade Compatibility Tool] 輸出：

- 已確定問題的清單。
- 分析摘要。

對於每個遇到的問題，報告都提供詳細資訊，如問題的嚴重性和說明。

導出此 `JSON` 檔案到其他輸出資料夾：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `[=JSON-OUTPUT-PATH]`:要導出的路徑目錄 `JSON` 輸出檔案。

>[!NOTE]
>
> 輸出資料夾的預設路徑是 `var/output/[TIME]-results.json`。

## HTML報告

在命令行介面上或通過 [!DNL Site-Wide Analysis Tool]。 HTML報告還包含：

- 已確定問題的清單。
- 分析摘要。

![HTML報告 — 摘要](../../assets/upgrade-guide/uct-html-summary.png)

您可以在 [!DNL Upgrade Compatibility Tool] 分析。

您可以根據最小問題級別(預設值為 `WARNING`)。

右上角有一個下拉菜單，允許您選擇其他級別。 相應地過濾所識別的問題清單。

![HTML報告 — 下拉用法](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 問題級別較低的問題已消除，但您會收到通知，因此您始終瞭解每個模組所發現的問題。

HTML報告還包括四個不同的圖表：

- **按問題嚴重性劃分的模組**:按模組顯示嚴重性分佈。
- **按問題嚴重性列出的檔案**:按檔案顯示嚴重性分佈。
- **按問題總數排序的模組**:顯示10個最易損的模組，並考慮警告、錯誤和嚴重錯誤。
- **具有相對大小和問題的模組**:模組包含的檔案越多，其圓就越大。 模組問題越多，其圓就越紅。

通過這些圖表，您可以確定最易損的模組以及執行升級需要更多工作的模組。

![HTML報告 — 圖](../../assets/upgrade-guide/uct-html-diagrams.png)

HTML報告圖也會相應更新，但 `Modules with relative sizes and issues`，它與 `min-issue-level` 是最初設計的。

如果要查看 `Modules with relative sizes and issues` 圖中，必須重新運行為 `--min-issue-level` 的雙曲餘切值。

![HTML報告 — 氣泡圖圖](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

要將此HTML報告導出到其他輸出資料夾：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

其中參數如下：

- `<dir>`: {{site.data.var.ee}} 安裝目錄。
- `[=HTML-OUTPUT-PATH]`:要導出的路徑目錄 `.html` 輸出檔案。

>[!NOTE]
>
> 輸出資料夾的預設路徑是 `var/output/[TIME]-results.html`。
