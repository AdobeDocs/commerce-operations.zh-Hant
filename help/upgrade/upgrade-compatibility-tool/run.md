---
title: 運行 [!DNL Upgrade Compatibility Tool]
description: 按照以下步驟運行 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
source-git-commit: 64b061f3b2f93827bfdb904a6faddbd21f4da5e6
workflow-type: tm+mt
source-wordcount: '2057'
ht-degree: 0%

---


# 運行 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

的 [!DNL Upgrade Compatibility Tool] 是一個命令行工具，它通過分析Adobe Commerce定制實例中安裝的所有模組來對照特定版本檢查該實例。 它返回一列重要問題、錯誤和警告，在升級到最新版本的Adobe Commerce之前必須解決這些問題。

的 [!DNL Upgrade Compatibility Tool] 確定在嘗試升級到更新版本的Adobe Commerce之前必須在代碼中修復的潛在問題。

## 使用 `upgrade:check` 命令

的 `upgrade:check` 命令是執行工具的主命令：

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>的 `<dir>` value是您的Adobe Commerce實例所在的目錄。

的 `upgrade:check` 命令運行 [!DNL Upgrade Compatibility Tool] 並通過分析Adobe Commerce定制實例中安裝的所有模組，針對特定版本檢查該實例。 它返回一個重要問題、錯誤和警告的清單，在升級到最新版本的Adobe Commerce之前，必須解決這些問題。

>[!WARNING]
>
>僅在提供項目根目錄（或主目錄）時執行。

此命令檢查該特定Adobe Commerce實例的核心代碼更改及其中安裝的所有自定義代碼更改。

您可以運行 `core:code:changes` 命令，僅分析該特定Adobe Commerce實例的核心代碼更改。 請參閱 [核心代碼更改](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) 的子菜單。

您可以使用 `graphql:compare` 命令來比較兩個GraphQL模式以檢查它們之間的任何更改。 查看 [GraphQL架構相容性驗證](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) 的子菜單。

### Recommendations利用 `upgrade:check` 命令

- 的 [!DNL Upgrade Compatibility Tool] 至少需要2GB的RAM才能運行。 建議使用此設定以避免記憶體限制不足導致的問題。 的 [!DNL Upgrade Compatibility Tool] 如果運行 `upgrade:check` 低音命令 `memory_limit` 的子菜單。
- 指定 `-m` 選項，針對特定模組運行工具：

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `[=MODULE-PATH]`:特定模組路徑目錄。

### 使用 `--help` 選項

查看 [!DNL Upgrade Compatibility Tool] 命令常規選項和幫助，運行：

```bash
bin/uct --help
```

但是，有可能 `--help` 作為運行特定命令時的選項，例如 `bin/uct upgrade:check`。 這返回特定 `--help` 該命令的選項：

```bash
bin/uct upgrade:check --help
```

可用 `--help` 選項 `upgrade:check` 命令：

- `-m, --module-path[=MODULE-PATH]`:要分析的模組的路徑
- `-a, --current-version[=CURRENT-VERSION]`:如果省略，將使用當前Adobe Commerce版本、Adobe Commerce安裝版本。
- `-c, --coming-version[=COMING-VERSION]`:目標Adobe Commerce版本，如果省略，將使用最新發佈的Adobe Commerce版本。 提供所有可用Adobe Commerce版本的清單。
- `--json-output-path[=JSON-OUTPUT-PATH]`:將以json格式導出輸出的檔案的路徑。
- `--html-output-path[=HTML-OUTPUT-PATH]`:將以HTML格式導出輸出的檔案的路徑。
- `--min-issue-level`:要在報告中顯示的最小問題級別。 預設級別為 [警告]。
- `-i, --ignore-current-version-compatibility-issues`:當您不希望將已知的嚴重問題、錯誤和警告包括在 [!DNL Upgrade Compatibility Tool] 報告。
- `--context=CONTEXT`:執行上下文。 此選項用於整合目的，不影響執行結果。
- `-h, --help`:顯示該特定命令的幫助。 如果沒有提供命令， `list` 命令是預設結果。
- `-q, --quiet`:執行命令時不輸出任何消息。
- `-v, --version`:顯示應用程式版本。
- `--ansi, --no-ansi`:啟用ANSI輸出。
- `-n, --no-interaction`:執行命令時不要詢問任何交互問題。
- `-v, --vv, --vvv, --verbose`:增加輸出通信的詳細程度。 1表示正常輸出，2表示詳細輸出，3表示DEBUG輸出。

### 輸出

由於所執行之分析， [!DNL Upgrade Compatibility Tool] 導出一個報告，其中包含每個檔案的問題清單，其中指定其嚴重性、錯誤代碼和錯誤說明。

請參閱以下示例：

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

檢查 [錯誤消息引用](error-messages.md) 的子菜單。

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

#### JSON

JSON檔案包含的輸出上顯示的完全相同的資訊：

- 已確定問題的清單。
- 分析摘要。

對於每個遇到的問題，報告都提供詳細資訊，如問題的嚴重性和說明。

>[!NOTE]
>
>輸出資料夾的預設路徑是 `var/output/[TIME]-results.json`。

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

#### HTML

HTML檔案還包含分析摘要和已確定問題的清單。

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

您將能夠根據最小問題級別(預設情況下， [警告])。

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
>輸出資料夾的預設路徑是 `var/output/[TIME]-results.html`。

### 使用 `--ignore-current-version-compatibility-issues` 選項

的 [!DNL Upgrade Compatibility Tool] 允許您運行 `upgrade:check` 命令 `--ignore-current-version-compatibility-issues` 選項，因此它只顯示新的或未知的嚴重問題、錯誤和警告。 當您不希望將已知的嚴重問題、錯誤和警告包括在 [!DNL Upgrade Compatibility Tool] 報告。

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>這僅適用於PHP API驗證。

### 香草裝置

A _香_ 安裝是為特定版本全新安裝指定的版本標籤或分支。

的 `bin/uct core:code:changes` 命令檢查系統中是否有香草實例。 如果這是首次使用香草安裝，則互動式命令行問題會提示您從Adobe Commerce儲存庫下載香草項目(`https://repo.magento.com/`)。

您可以運行 [!DNL Upgrade Compatibility Tool] 命令 `--vanilla-dir` 的子菜單。

查看 [部署香草實例](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 的子菜單。

## 使用 `list` 命令

返回清單 [!DNL Upgrade Compatibility Tool] 可用命令，運行：

```bash
bin/uct list
```

的 `list` 命令返回以下內容：

- `-h, --help`:顯示該特定命令的幫助。 如果沒有提供命令， `list` 命令是預設結果。
- `-q, --quiet`:執行命令時不輸出任何消息。
- `-v, --version`:顯示應用版本。
- `--ansi, --no-ansi`:啟用ANSI輸出。
- `-n, --no-interaction`:執行命令時不要詢問任何交互問題。
- `-v, --vv, --vvv, --verbose`:增加輸出通信的詳細程度。 1表示正常輸出，2表示詳細輸出，3表示DEBUG輸出。

## 使用 `core:code:changes` 命令

您可以將當前的Adobe Commerce安裝與乾淨的香草安裝進行比較，以查看核心代碼是否進行了任何修改以實施新功能或自定義。 此驗證有助於根據這些更改估計升級所需的工作量。

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `<vanilla dir>`:Adobe Commerce香草安裝目錄。

運行此命令時存在一些限制：

- 僅在提供項目根目錄（或主目錄）時執行。
- 僅顯示核心修改的清單。

### 使用 `core:code:changes` 命令 `--help` 選項

可用 `--help` 選項 `core:code:changes` 命令：

- `-h, --help`:顯示該特定命令的幫助。 如果沒有提供命令， `list` 命令是預設結果。
- `-q, --quiet`:執行命令時不輸出任何消息。
- `-v, --version`:顯示應用版本。
- `--ansi, --no-ansi`:啟用ANSI輸出。
- `-n, --no-interaction`:執行命令時不要詢問任何交互問題。
- `-v, --vv, --vvv, --verbose`:增加輸出通信的詳細程度。 1表示正常輸出，2表示詳細輸出，3表示DEBUG輸出。

## 版本

您可以將當前的Adobe Commerce安裝與Adobe Commerce版本進行比較 `>=2.3`。

運行以下命令時，必須將版本作為參數提供：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

>[!NOTE]
>
>此參數提供所有可用Adobe Commerce版本的清單。

位置：

- `-c, --coming-version[=COMING-VERSION]`:Adobe Commerce的目標版本。

運行上一個命令時存在一些限制：

- 此參數引用標識特定版本的Adobe Commerce的任何標籤。
- 明確提供這一條是要求；只提供它的價值是行不通的。
- 提供不帶任何引號的標籤版本（不帶單引號，也不帶雙引號）: ~~「2.4.1發」~~。
- 您不應提供當前安裝的版本以及2.3版本以前的版本，而2.3版本是目前支援的最舊版本。

### 使用 `refactor` 命令

的 [!DNL Upgrade Compatibility Tool] 能夠自動修復減少的問題集：

- 允許在不傳遞參數的情況下使用但使用此類用法的函式現在已棄用。
- 使用 `$this` Magento。
- PHP關鍵字的使用 `final` 用私人方法。

運行：

```bash
bin/uct refactor <dir>
```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。

## GraphQL架構相容性驗證

的 [!DNL Upgrade Compatibility Tool] 還提供了以下選項：引入兩個GraphQL端點，並比較其架構，以查找它們之間的中斷和危險更改：

```bash
bin/uct graphql:compare <schema1> <schema2>
```

其中參數如下：

- `<schema1>`:現有安裝的終結點URL。
- `<schema2>`:香草安裝的終結點URL。

你一定是在 `instance before` 和 `instance after` 升級。

### GraphQL比較命令 `--help` 選項

可用 `--help` 選項 `graphql:compare` 命令：

- `-h, --help`:顯示該特定命令的幫助。 如果沒有提供命令， `list` 命令是預設結果。
- `-q, --quiet`:執行命令時不輸出任何消息。
- `-v, --version`:顯示應用版本。
- `--ansi, --no-ansi`:啟用ANSI輸出。
- `-n, --no-interaction`:執行命令時不要詢問任何交互問題。
- `-v, --vv, --vvv, --verbose`:增加輸出通信的詳細程度。 1表示正常輸出，2表示詳細輸出，3表示DEBUG輸出。

### 示例，列出GraphQL的嚴重問題、錯誤和警告

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

您可以運行 [!DNL Upgrade Compatibility Tool] 通過PhpStorm插件運行配置。 查看 [[!DNL Upgrade Compatibility Tool] 運行配置](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) 的子菜單。

查看 [視頻教程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/uct-phpstorm.html?lang=en) (06:30)瞭解如何使用 [!DNL Upgrade Compatibility Tool] 與MagentoPHPStorm插件一起使用。


## 建議的操作

### 優化結果

的 [!DNL Upgrade Compatibility Tool] 提供一個報告，其中包含預設情況下在項目上確定的所有問題。 您可以優化結果，以專注於完成升級必須解決的問題：

- 使用選項 `--ignore-current-version-compatibility-issues`，它針對您當前的Adobe Commerce版本隱藏所有已知的嚴重問題、錯誤和警告。 它僅針對您嘗試升級到的版本提供錯誤。
- 添加 `--min-issue-level` 選項，此設定允許設定最小問題級別，以幫助您僅排定升級中最重要問題的優先順序。
- 如果只要分析某個供應商、模組甚至目錄，也可以將路徑指定為選項。 運行 `bin` 命令和添加的選項 `-m`。 這允許 [!DNL Upgrade Compatibility Tool] 獨立分析特定模組，並幫助解決執行時可能出現的記憶體問題 [!DNL Upgrade Compatibility Tool]。

### 遵循Adobe Commerce最佳做法

- 避免使用兩個同名模組。
- 關注Adobe Commerce [編碼標準](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html)。

## 故障排除

### 分割錯誤

當兩個模組具有相同名稱時， [!DNL Upgrade Compatibility Tool] 顯示分段錯誤。

為避免此錯誤，建議運行 `bin` 命令和添加的選項 `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>的 `<dir>` value是您的Adobe Commerce實例所在的目錄。

的 `-m` 選項 [!DNL Upgrade Compatibility Tool] 獨立分析每個特定模組，以避免在Adobe Commerce實例中遇到兩個同名模組。

此命令選項還允許 [!DNL Upgrade Compatibility Tool] 要分析包含多個模組的資料夾：

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

此建議還有助於解決執行 [!DNL Upgrade Compatibility Tool]。

### 空輸出

>[!NOTE]
>
>的 `M2_VERSION` 是您要與您的Adobe Commerce實例進行比較的目標Adobe Commerce版本。

如果運行此命令後：

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

唯一的輸出是 `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

可能的原因是PHP記憶體限制。
通過設定 `memory_limit` 至 `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
