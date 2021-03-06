---
title: '"運行 [!DNL Upgrade Compatibility Tool]"'
description: 按照以下步驟運行 [!DNL Upgrade Compatibility Tool] 在命令行介面上，為你的Adobe Commerce項目。
source-git-commit: a0bb188eea38688c5bfe68e8c6bb7b3d040f5e0a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 下載 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

開始使用 [!DNL Upgrade Compatibility Tool] 在命令行介面中，通過運行以下命令下載該命令：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

您可能需要為工具授予可執行權限 `chmod` 命令：

```bash
chmod +x ./uct/bin/uct
```

## 的 [!DNL Upgrade Compatibility Tool] 命令行介面中

的 [!DNL Upgrade Compatibility Tool] 是一種工具，它通過分析Adobe Commerce定制實例中安裝的所有模組來對照特定版本檢查該實例。 它返回一列重要問題、錯誤和警告，在升級到最新版本的Adobe Commerce之前必須解決這些問題。

查看 [視頻教程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)瞭解有關 [!DNL Upgrade Compatibility Tool]。

可用命令 [!DNL Upgrade Compatibility Tool] 在命令行介面中：

| **命令** | **說明** |
|----------------|-----------------|
| `upgrade:check` | 此命令運行 [!DNL Upgrade Compatibility Tool] 分析其中安裝的所有模組。 |
| `core:code:changes` | 此命令將您當前的Adobe Commerce安裝與乾淨的香草安裝進行比較。 |
| `refactor` | 此命令自動修復一組減少的問題。 |
| `graphql:compare` | 此命令提供了引入兩個GraphQL端點並比較其架構的選項。 |
| `list` | 此命令返回所有 [!DNL Upgrade Compatibility Tool] 的子菜單。 |
| `help` | 此命令返回所有可用 `help`選項 [!DNL Upgrade Compatibility Tool]。 此命令以及前面命令的選項也可以運行。 |

## 使用 `upgrade:check` 命令

的 `upgrade:check` 命令檢查該特定Adobe Commerce實例的核心代碼更改及其中安裝的所有自定義代碼更改。

的 `upgrade:check` 命令是執行工具的主命令：

```bash
bin/uct upgrade:check <dir>
```

位置 `<dir>` value是您的Adobe Commerce實例所在的目錄。

可用選項 `upgrade:check` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `upgrade:check` | <ul><li> — 幫助：返回所有可用選項。</li><li> — 最小問題級別：您可以根據最小問題級別（預設值為WARNING）篩選問題。</li><li> — 忽略當前版本相容性問題（或 — i）:如果您不想在報告中包含當前版本中的嚴重問題、錯誤和警告。</li><li> — 即將到來的版本（或 — c）:瞄準特定的Adobe Commerce版本。</li></ul> |

的 [!DNL Upgrade Compatibility Tool] 允許您運行 `upgrade:check` 命令 `--ignore-current-version-compatibility-issues` 的雙曲餘切值。 當您只想獲取從當前版本到目標版本的更新中引入的新問題時，請使用此選項 [!DNL Upgrade Compatibility Tool] 報告：

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> 這僅適用於PHP API驗證。

### 添加 `--coming-version` 選項

您可以將當前的Adobe Commerce安裝與任何Adobe Commerce版本進行比較 `>=2.3` 使用 `--coming-version` 的雙曲餘切值。

在運行 `upgrade:check` 命令：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

位置 `-c, --coming-version[=COMING-VERSION]` 指Adobe Commerce目標版本。

運行 `--coming-version`:

- 此參數引用標識特定版本的Adobe Commerce的任何標籤。
- 明確提供這一條是要求；只提供它的價值是行不通的。
- 提供不帶任何引號的標籤版本（不帶單引號，也不帶雙引號）: ~~「2.4.1發」~~。
- 您不應提供當前安裝的版本以及2.3版本以前的版本，而2.3版本是目前支援的最舊版本。

## 使用 `core:code:changes` 命令

您可以比較當前的Adobe Commerce安裝，以驗證是否修改了Adobe Commerce的核心代碼以實施自定義。 此命令僅顯示核心修改的清單：

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `<vanilla dir>`:Adobe Commerce香草安裝目錄。

可用選項 `core:code:changes` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `core:code:changes` | `--help`:返回所有可用 `--help` 頁籤 |

>[!NOTE]
>
> 最好將自定義代碼排除在核心代碼之外。 見Adobe Commerce2.4 [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 更多升級最佳做法。

### 香草裝置

A _香_ 安裝是為特定版本全新安裝指定的版本標籤或分支。

的 `bin/uct core:code:changes` 命令檢查系統中是否有香草實例。 如果這是首次使用香草安裝，則互動式命令行問題會提示您從Adobe Commerce儲存庫下載香草項目(`https://repo.magento.com/`)。

您可以運行 [!DNL Upgrade Compatibility Tool] 命令 `--vanilla-dir` 的子菜單。

查看 [部署香草實例](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 的子菜單。

## 使用 `refactor` 命令

的 [!DNL Upgrade Compatibility Tool] 能夠自動修復減少的問題集：

- 允許在不傳遞參數的情況下使用但使用此類用法的函式現在已棄用。
- 使用 `$this` Magento。
- PHP關鍵字的使用 `final` 用私人方法。

為此，執行 `refactor` 命令：

```bash
bin/uct refactor <dir>
```

位置 `<dir>` value是您的Adobe Commerce實例所在的目錄。

可用選項 `refactor` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `refactor` | `--help`:返回所有可用 `--help` 頁籤 |

## 使用 `graphql:compare` 命令

此命令將選項提供給 [!DNL Upgrade Compatibility Tool] 介紹兩個GraphQL端點，並比較其模式以查找它們之間的中斷和危險更改：

```bash
bin/uct graphql:compare <schema1> <schema2>
```

其中參數如下：

- `<schema1>`:現有安裝的終結點URL。
- `<schema2>`:香草安裝的終結點URL。

可用選項 `graphql:compare` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `graphql:compare` | `--help`:返回所有可用 `--help` 頁籤 |

## 使用 `list` 命令

返回清單 [!DNL Upgrade Compatibility Tool] 可用命令，運行：

```bash
bin/uct list
```

## 使用 `--help` 命令

查看 [!DNL Upgrade Compatibility Tool] 命令常規選項和幫助，運行：

```bash
bin/uct --help
```

這將返回一個包含所有可用項的清單 `help` 選項 [!DNL Upgrade Compatibility Tool] 在命令行介面中：

```terminal
- -m, --module-path[=MODULE-PATH]: Path of the modules to be analysed
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

但是，有可能 `--help` 作為選項。 這將返回特定 `--help` 選項。

示例 `upgrade:check` 命令 `--help` 選項：

```bash
bin/uct upgrade:check --help
```

這將返回可為 `upgrade:check` 命令：

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## 遵循Adobe Commerce最佳做法

- 避免使用兩個同名模組。
- 關注Adobe Commerce [編碼標準](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html)。
- Adobe Commerce2.4 [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 最佳實踐。

## 優化結果

的 [!DNL Upgrade Compatibility Tool] 提供一個報告，其中包含預設情況下在項目上確定的所有問題。 您可以優化結果，以專注於完成升級必須解決的問題：

- 使用選項 `--ignore-current-version-compatibility-issues` 當您只希望獲得從當前版本到目標版本的更新中引入的新問題時 [!DNL Upgrade Compatibility Tool] 報告。
- 添加 `--min-issue-level` 選項，此設定允許設定最小問題級別，以幫助您僅排定升級中最重要問題的優先順序。
- 的 [!DNL Upgrade Compatibility Tool] 至少需要2GB的RAM才能運行。 建議使用此設定以避免記憶體限制不足導致的問題。 的 [!DNL Upgrade Compatibility Tool] 如果運行 `upgrade:check` 低音命令 `memory_limit` 的子菜單。
- 如果只要分析某個供應商、模組甚至目錄，也可以將路徑指定為選項。 運行 `bin` 命令和添加的選項 `-m`。 這允許 [!DNL Upgrade Compatibility Tool] 獨立分析特定模組，並幫助解決執行時可能出現的記憶體問題 [!DNL Upgrade Compatibility Tool]。 指定 `-m` 選項，針對特定模組運行工具：

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `[=MODULE-PATH]`:特定模組路徑目錄。
