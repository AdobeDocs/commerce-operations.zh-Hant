---
title: "運行 [!DNL Upgrade Compatibility Tool]"
description: 請依照下列步驟執行 [!DNL Upgrade Compatibility Tool] 填入Adobe Commerce專案的命令列介面。
source-git-commit: 653d755023f96c0a6acc312f74fd4a0292f13a73
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---


# 下載 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

若要開始使用 [!DNL Upgrade Compatibility Tool] 在命令行介面中，通過運行以下命令來下載它：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

您可能需要為提供工具執行檔的權限 `chmod` 命令：

```bash
chmod +x ./uct/bin/uct
```

## 此 [!DNL Upgrade Compatibility Tool] 命令行介面

此 [!DNL Upgrade Compatibility Tool] 是一種工具，可透過分析Adobe Commerce中安裝的所有模組，根據特定版本檢查自訂例項。 它會傳回重要問題、錯誤和警告的清單，在升級至最新版Adobe Commerce之前必須解決這些問題。

看這個 [影片教學課程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)以進一步了解 [!DNL Upgrade Compatibility Tool].

適用於 [!DNL Upgrade Compatibility Tool] 在命令行介面中：

| **命令** | **說明** |
|----------------|-----------------|
| `upgrade:check` | 此命令運行 [!DNL Upgrade Compatibility Tool] 分析安裝在其中的所有模組。 |
| `dbschema:diff` | 此命令顯示兩個指定的Adobe Commerce版本之間資料庫架構的所有差異。 |
| `core:code:changes` | 此命令會將您目前的Adobe Commerce安裝與乾淨的Vanilla安裝進行比較。 |
| `refactor` | 此命令會自動修正縮減的問題集。 |
| `graphql:compare` | 此命令提供查看兩個GraphQL端點並比較其結構的選項。 |
| `list` | 此命令返回所有 [!DNL Upgrade Compatibility Tool] 可用命令。 |
| `help` | 此命令返回所有可用值 `help`選項 [!DNL Upgrade Compatibility Tool]. 此命令可以運行，也可以運行前面命令的選項。 |

## 使用 `upgrade:check` 命令

此 `upgrade:check` 命令會檢查該特定Adobe Commerce例項的核心程式碼變更，以及其中安裝的所有自訂程式碼變更。

此 `upgrade:check` 命令是執行工具的主命令：

```bash
bin/uct upgrade:check <dir>
```

其中 `<dir>` value是您的Adobe Commerce執行個體所在的目錄。

適用於 `upgrade:check` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `upgrade:check` | <ul><li> — 幫助：傳回所有可用選項。</li><li>—current-version:最新Adobe Commerce版本。 此參數為必要項目，且必須一律使用。</li><li> — 最小問題級別：您可以根據最低問題級別（預設值為「警告」）篩選問題。</li><li>—ignore-current-version-compatibility-issues（或 — i）:如果您不想在報表中納入目前版本的重大問題、錯誤和警告。</li><li> — 即將發行版本（或 — c）:鎖定特定Adobe Commerce版本。 若省略，則會使用最新的可用項目。</li></ul> |

此 [!DNL Upgrade Compatibility Tool] 可讓您執行 `upgrade:check` 命令 `--ignore-current-version-compatibility-issues` 選項。 如果您只想取得從您目前的版本更新至您 [!DNL Upgrade Compatibility Tool] 報告：

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> 這僅適用於PHP API驗證。

### 新增 `--coming-version` 選項

您可以比較目前的Adobe Commerce安裝與任何Adobe Commerce版本 `>=2.3` 使用 `--coming-version` 選項。

您必須在執行 `upgrade:check` 命令：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

其中 `-c, --coming-version[=COMING-VERSION]` 是指Adobe Commerce目標版本。

執行 `--coming-version`:

- 此參數指的是可識別特定版本Adobe Commerce的任何標籤。
- 必須明確提供這一條；僅提供其值無法運作。
- 提供不含任何引號的標籤版本（非單引號或雙引號）: ~~&#39;2.4.1-develop&#39;~~.
- 您不應提供比目前安裝的版本舊，也不應提供比2.3舊，這是目前支援的最舊版本。

## 使用 `dbschema:diff` 命令

您可以擷取兩個Adobe Commerce版本之資料庫架構之間的差異。

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

其中引數如下：

- `<current-version>`:任何Adobe Commerce版本進行比較。
- `<target-version>`:以及任何Adobe Commerce版本以供比較。

執行範例：

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## 使用 `core:code:changes` 命令

您可以比較目前的Adobe Commerce安裝，以驗證Adobe Commerce的核心代碼是否已修改以實作自訂。 此命令僅顯示核心修改的清單：

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

其中引數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `<vanilla dir>`:Adobe Commerce香草安裝目錄。

適用於 `core:code:changes` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `core:code:changes` | `--help`:傳回所有可用 `--help` 選項。 |

>[!NOTE]
>
> 將自訂程式碼排除在核心程式碼之外是最佳作法。 請參閱Adobe Commerce 2.4 [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 以了解更多升級最佳實務。

### 香草裝置

A _香草_ 安裝是針對特定發行版本而全新安裝指定版本標籤或分支。

此 `bin/uct core:code:changes` 命令會檢查您的系統中是否有vanilla執行個體。 如果這是第一次使用Vanilla安裝，互動式命令列問題會提示您從Adobe Commerce存放庫(`https://repo.magento.com/`)。

您可以執行 [!DNL Upgrade Compatibility Tool] 命令 `--vanilla-dir` 選項，指定Adobe Commerce vanilla安裝目錄。

請參閱 [部署Vanilla實例](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) 主題以取得詳細資訊。

## 使用 `refactor` 命令

此 [!DNL Upgrade Compatibility Tool] 能夠自動修正縮減的問題集：

- 允許在不傳遞引數的情況下使用的函式，但此類用法現已過時。
- 使用 `$this` 在Magento範本中。
- PHP關鍵字的用法 `final` 在私人方法中。

為此，請執行 `refactor` 命令：

```bash
bin/uct refactor <dir>
```

其中 `<dir>` value是您的Adobe Commerce執行個體所在的目錄。

適用於 `refactor` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `refactor` | `--help`:傳回所有可用 `--help` 選項。 |

## 使用 `graphql:compare` 命令

此命令提供 [!DNL Upgrade Compatibility Tool] 若要查看兩個GraphQL端點，並比較其結構，以找出其中的突破與危險變更：

```bash
bin/uct graphql:compare <schema1> <schema2>
```

其中引數如下：

- `<schema1>`:現有安裝的端點URL。
- `<schema2>`:安裝Vanilla的端點URL。

適用於 `graphql:compare` 命令：

| **命令** | **可用選項** |
|----------------|-----------------|
| `graphql:compare` | `--help`:傳回所有可用 `--help` 選項。 |

## 使用 `list` 命令

返回 [!DNL Upgrade Compatibility Tool] 可用命令，運行：

```bash
bin/uct list
```

## 使用 `help` 命令

若要查看 [!DNL Upgrade Compatibility Tool] 命令常規選項和幫助，運行

```bash
bin/uct --help
```

這會傳回清單，其中所有項目皆可使用 `help` 選項 [!DNL Upgrade Compatibility Tool] 在命令行介面中：

```terminal
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

可以運行 `--help` 作為運行特定命令時的選項。 它會傳回 `--help` 指定命令的選項。

範例 `upgrade:check` 命令 `--help` 選項：

```bash
bin/uct upgrade:check --help
```

這會傳回可針對 `upgrade:check` 命令：

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## 遵循Adobe Commerce最佳實務

- 請避免有兩個模組具有相同名稱。
- 關注Adobe Commerce [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 最佳實務。
- 執行 [!DNL Upgrade Compatibility Tool] 從 [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) for [Adobe Commerce雲基礎架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} 專案。

## 最佳化結果

此 [!DNL Upgrade Compatibility Tool] 預設會提供包含結果的報表，內含專案上識別的所有問題。 您可以最佳化結果，以著重於完成升級所必須修正的問題：

- 使用選項 `--ignore-current-version-compatibility-issues` 時，您只會從您的目前版本取得 [!DNL Upgrade Compatibility Tool] 報表。
- 新增 `--min-issue-level` 選項，此設定可設定最低問題層級，以協助您排定升級中最重要問題的優先順序。
- 此 [!DNL Upgrade Compatibility Tool] 至少需要2GB RAM才能運行。 建議使用此設定，以避免因記憶體限制不足而造成的問題。 此 [!DNL Upgrade Compatibility Tool] 如果執行 `upgrade:check` 命令 `memory_limit` 設定。
