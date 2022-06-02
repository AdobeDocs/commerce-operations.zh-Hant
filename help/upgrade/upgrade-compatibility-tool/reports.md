---
title: '"[!DNL Upgrade Compatibility Tool] 報告」'
description: 按照以下步驟運行 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# 報表

{{commerce-only}}

由於分析，本公司 [!DNL Upgrade Compatibility Tool] 導出一個報告，其中包含每個檔案的問題清單，其中指定其嚴重性、錯誤代碼和錯誤說明。

請參閱以下示例：

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

檢查 [錯誤消息引用](../upgrade-compatibility-tool/error-messages.md) 的子菜單。

報告還包括一個詳細摘要，其中顯示：

- *當前版本*:當前安裝的版本。
- *目標版本*:要升級到的版本。
- *執行時間*:分析生成報告所花的時間(mm:ss)。
- *需要更新的模組*:包含相容性問題並需要更新的模組的百分比。
- *需要更新的檔案*:包含相容性問題並需要更新的檔案的百分比。
- *嚴重錯誤總數*:發現的嚴重錯誤數。
- *錯誤總數*:找到的錯誤數。
- *警告總數*:找到的警告數。

請參閱以下示例：

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>預設情況下， [!DNL Upgrade Compatibility Tool] 將報告導出為兩種不同格式： `json` 和 `html`。

## JSON檔案

JSON檔案包含的輸出上顯示的完全相同的資訊：

- 已確定問題的清單。
- 分析摘要。

對於每個遇到的問題，報告都提供詳細資訊，如問題的嚴重性和說明。

要將此報表導出到其他輸出資料夾，請運行：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `[=JSON-OUTPUT-PATH]`:要導出的路徑目錄 `.json` 輸出檔案。

>[!NOTE]
>
>輸出資料夾的預設路徑是 `var/output/[TIME]-results.json`。

## HTML報告

HTML檔案還包含分析摘要和已確定問題的清單。 在命令行介面上或通過 [!DNL Site-Wide Analysis Tool]。

![HTML報告 — 摘要](../../assets/upgrade-guide/uct-html-summary.png)

您可以在 [!DNL Upgrade Compatibility Tool] 分析：

![HTML報告 — 詳細資訊](../../assets/upgrade-guide/uct-html-details.png)

HTML報告還包括四個不同的圖表：

- **按問題嚴重性劃分的模組**:按模組顯示嚴重性分佈。
- **按問題嚴重性列出的檔案**:按檔案顯示嚴重性分佈。
- **按問題總數排序的模組**:顯示10個最易損的模組，並考慮警告、錯誤和嚴重錯誤。
- **具有相對大小和問題的模組**:模組包含的檔案越多，其圓就越大。 模組問題越多，其圓就越紅。

通過這些圖表，您可以（一目瞭然地）確定最易損壞的部件以及執行升級需要更多工作的部件。

![HTML報告 — 圖](../../assets/upgrade-guide/uct-html-diagrams.png)

您可以根據最小問題級別篩選報告中顯示的問題。 預設值為 `WARNING`.

右上角有一個下拉清單，允許您根據必需品選擇其他下拉清單。 將相應地篩選已確定問題的清單。

![HTML報告 — 下拉用法](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

請注意，問題級別較低的問題已消除，但您會收到通知，因此您始終瞭解每個模組所發現的問題。

圖也會相應更新，但是 `Modules with relative sizes and issues`，它與 `min-issue-level` 最初設立的。

如果要查看不同的結果，則需要重新運行為 `--min-issue-level` 的雙曲餘切值。

![HTML報告 — 氣泡圖圖](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

要將此報告導出到其他輸出資料夾中，請運行：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

其中參數如下：

- `<dir>`:{{site.data.var.ee}}安裝目錄。
- `[=HTML-OUTPUT-PATH]`:要導出的路徑目錄 `.html` 輸出檔案。

>[!NOTE]
>
> 輸出資料夾的預設路徑是 `var/output/[TIME]-results.html`。
