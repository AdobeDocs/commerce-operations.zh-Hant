---
title: '"運行 [!DNL Upgrade Compatibility Tool]"'
description: 按照以下步驟運行 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---


# 下載 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

開始使用 [!DNL Upgrade Compatibility Tool] 在命令行介面中，通過運行以下命令下載該命令：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

>[!NOTE]
>
> 查看 [先決條件](../upgrade-compatibility-tool/prerequisites.md) 的子菜單。

## 運行 [!DNL Upgrade Compatibility Tool]

的 [!DNL Upgrade Compatibility Tool] 是一種工具，它通過分析Adobe Commerce定制實例中安裝的所有模組來對照特定版本檢查該實例。 它返回一列重要問題、錯誤和警告，在升級到最新版本的Adobe Commerce之前必須解決這些問題。

的 [!DNL Upgrade Compatibility Tool] 確定在嘗試升級到更新版本的Adobe Commerce之前必須在代碼中修復的潛在問題。

查看 [視頻教程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)瞭解有關 [!DNL Upgrade Compatibility Tool]。

## 建議的操作

### 優化結果

的 [!DNL Upgrade Compatibility Tool] 提供一個報告，其中包含預設情況下在項目上確定的所有問題。 您可以優化結果，以專注於完成升級必須解決的問題：

- 使用選項 `--ignore-current-version-compatibility-issues`，它針對您當前的Adobe Commerce版本隱藏所有已知的嚴重問題、錯誤和警告。 它僅針對您嘗試升級到的版本提供錯誤。
- 添加 `--min-issue-level` 選項，此設定允許設定最小問題級別，以幫助您僅排定升級中最重要問題的優先順序。
- 如果只要分析某個供應商、模組甚至目錄，也可以將路徑指定為選項。 運行 `bin` 命令和添加的選項 `-m`。 這允許 [!DNL Upgrade Compatibility Tool] 獨立分析特定模組，並幫助解決執行時可能出現的記憶體問題 [!DNL Upgrade Compatibility Tool]。

### 遵循Adobe Commerce最佳做法

- 避免使用兩個同名模組。
- 關注Adobe Commerce [編碼標準](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html)。

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
