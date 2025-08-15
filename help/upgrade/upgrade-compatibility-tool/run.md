---
title: 執行 [!DNL Upgrade Compatibility Tool]
description: 請依照下列步驟，在Adobe Commerce專案的命令列介面中執行 [!DNL Upgrade Compatibility Tool] 。
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: bfb952d29bd3d7fc7147107216981e05202e44aa
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# 下載[!DNL Upgrade Compatibility Tool]

{{commerce-only}}

若要在命令列介面中開始使用[!DNL Upgrade Compatibility Tool]，請執行以下命令來下載它：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

您可能需要使用`chmod`命令授與工具可執行檔許可權：

```bash
chmod +x ./uct/bin/uct
```

## 命令列介面中的[!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool]是一種工具，可透過分析安裝在其中的所有模組來針對特定版本檢查Adobe Commerce自訂執行個體。 它會傳回在升級至最新版Adobe Commerce之前必須解決的嚴重問題、錯誤和警告清單。

請參閱此[教學課程影片](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)，深入瞭解[!DNL Upgrade Compatibility Tool]。

命令列介面中[!DNL Upgrade Compatibility Tool]的可用命令：

| **命令** | **描述** |
|----------------|-----------------|
| `upgrade:check` | 這個命令會透過分析安裝在[!DNL Upgrade Compatibility Tool]中的所有模組來執行它。 |
| `dbschema:diff` | 這個命令會顯示兩個指定Adobe Commerce版本之間資料庫架構的所有差異。 |
| `core:code:changes` | 這個命令會將您目前的Adobe Commerce安裝與乾淨的vanilla安裝進行比較。 |
| `refactor` | 這個命令會自動修正一組減少的問題。 |
| `graphql:compare` | 此命令提供選項，讓您內檢兩個GraphQL端點並比較其結構。 |
| `list` | 此命令會傳回所有[!DNL Upgrade Compatibility Tool]可用命令的清單。 |
| `help` | 此命令會傳回`help`所有可用的[!DNL Upgrade Compatibility Tool]選項。 此指令可與先前指令一起執行，也可以與選項一起執行。 |

## 使用`upgrade:check`命令

`upgrade:check`命令會檢查該特定Adobe Commerce執行個體的核心程式碼變更，以及其中安裝的所有自訂程式碼變更。

`upgrade:check`命令是執行工具的主要命令：

```bash
bin/uct upgrade:check <dir>
```

其中`<dir>`值是您的Adobe Commerce執行個體所在的目錄。

`upgrade:check`命令的可用選項：

| **命令** | **可用選項** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help：傳回所有可用選項。</li><li>—current-version：目前的Adobe Commerce版本。 如果省略，則會使用安裝的Adobe Commerce版本。</li><li> — 最小問題層級：您可以根據最小問題層級篩選問題（預設值為「警告」）。</li><li>—ignore-current-version-compatibility-issues （或 — i）：如果您不想在報表中包含目前版本的嚴重問題、錯誤和警告。</li><li> — 即將推出的版本（或 — c）：鎖定特定的Adobe Commerce版本。 如果省略，將使用最新可用的。</li></ul> |

[!DNL Upgrade Compatibility Tool]可讓您執行具有`upgrade:check`選項的`--ignore-current-version-compatibility-issues`命令。 當您只想在[!DNL Upgrade Compatibility Tool]報告中取得從目前版本更新到目標版本所引入的新問題時，請使用此選項：

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> 這僅適用於PHP API驗證。

### 正在新增`--coming-version`選項

您可以使用`>=2.3`選項，將目前的Adobe Commerce安裝與任何Adobe Commerce版本`--coming-version`進行比較。

執行`upgrade:check`命令時，您必須提供版本作為引數：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

其中`-c, --coming-version[=COMING-VERSION]`參考Adobe Commerce目標版本。

執行`--coming-version`有一些限制：

- 此引數是指可識別特定版本Adobe Commerce的任何標籤。
- 必須明確提供此值；僅提供其值無法運作。
- 提供不含任何引號的標籤版本（不單引號或雙引號）： ~~&#39;2.4.1-develop&#39;~~。
- 您不應提供比目前已安裝版本舊或比2.3 （目前支援的最舊版本）舊的版本。

## 使用`dbschema:diff`命令

您可以擷取兩個Adobe Commerce版本的資料庫架構之間的差異。

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

其中引數如下：

- `<current-version>`：任何可供比較的Adobe Commerce版本。
- `<target-version>`：還有任何Adobe Commerce版本可供比較。

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

## 使用`core:code:changes`命令

您可以比較目前的Adobe Commerce安裝，以驗證Adobe Commerce的核心程式碼是否已修改為實作自訂。 這個命令只會顯示核心修改的清單：

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

其中引數如下：

- `<dir>`： Adobe Commerce安裝目錄。
- `<vanilla dir>`： Adobe Commerce vanilla安裝目錄。

`core:code:changes`命令的可用選項：

| **命令** | **可用選項** |
|----------------|-----------------|
| `core:code:changes` | `--help`：傳回所有可用的`--help`選項。 |

>[!NOTE]
>
> 最佳實務是將自訂程式碼排除在核心程式碼之外。 如需更多升級最佳實務，請參閱Adobe Commerce 2.4 [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf)。

### Vanilla安裝

_vanilla_&#x200B;安裝是特定發行版本之指定版本標籤或分支的全新安裝。

`bin/uct core:code:changes`命令會檢查系統中是否有vanilla執行個體。 如果這是第一次使用vanilla安裝，互動式命令列問題會提示您從Adobe Commerce存放庫(`https://repo.magento.com/`)下載vanilla專案。

您可以執行包含[!DNL Upgrade Compatibility Tool]選項的`--vanilla-dir`命令，以指定Adobe Commerce vanilla安裝目錄。

如需詳細資訊，請參閱[部署vanilla執行個體](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance)主題。

## 使用`refactor`命令

[!DNL Upgrade Compatibility Tool]能夠自動修正縮減的問題集：

- 允許在不傳遞引數的情況下使用，但具有此類使用方式的函式現已棄用。
- 在Magento範本中使用`$this`。
- 在私用方法中使用PHP關鍵字`final`。

為此，請執行`refactor`命令：

```bash
bin/uct refactor <dir>
```

其中`<dir>`值是您的Adobe Commerce執行個體所在的目錄。

`refactor`命令的可用選項：

| **命令** | **可用選項** |
|----------------|-----------------|
| `refactor` | `--help`：傳回所有可用的`--help`選項。 |

## 使用`graphql:compare`命令

此命令為[!DNL Upgrade Compatibility Tool]提供選項，以便內嵌兩個GraphQL端點，並比較其結構描述，以找出兩者之間的重大變更和危險變更：

```bash
bin/uct graphql:compare <schema1> <schema2>
```

其中引數如下：

- `<schema1>`：現有安裝的端點URL。
- `<schema2>`： vanilla安裝的端點URL。

`graphql:compare`命令的可用選項：

| **命令** | **可用選項** |
|----------------|-----------------|
| `graphql:compare` | `--help`：傳回所有可用的`--help`選項。 |

## 使用`list`命令

若要傳回[!DNL Upgrade Compatibility Tool]個可用命令的清單，請執行：

```bash
bin/uct list
```

## 使用`help`命令

若要檢視[!DNL Upgrade Compatibility Tool]命令的一般選項和說明，請執行：

```bash
bin/uct --help
```

這會針對命令列介面中的`help`傳回包含所有可用[!DNL Upgrade Compatibility Tool]選項的清單：

```
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

執行特定命令時，可以將`--help`作為選項執行。 它會傳回指定命令的`--help`選項。

具有`upgrade:check`選項的`--help`命令範例：

```bash
bin/uct upgrade:check --help
```

這會傳回可為`upgrade:check`命令執行的特定選項：

```
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

- 避免有兩個名稱相同的模組。
- 遵循Adobe Commerce [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/)。
- Adobe Commerce 2.4 [升級指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf)最佳作法。
- 針對雲端基礎結構[!DNL Upgrade Compatibility Tool]專案上的[[!DNL Site-Wide Analysis Tool]Adobe Commerce，從](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) [執行](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}。

## 最佳化您的結果

[!DNL Upgrade Compatibility Tool]提供的報告包含結果，其中包含專案中依預設識別的所有問題。 您可以最佳化結果，將重點放在您必須修正才能完成升級的問題上：

- 當您只想在`--ignore-current-version-compatibility-issues`報表中取得從目前版本更新至目標版本所引入的新問題時，請使用選項[!DNL Upgrade Compatibility Tool]。
- 新增`--min-issue-level`選項，此設定可設定最低問題層級，以協助僅排定您升級時最重要的問題的優先順序。
- [!DNL Upgrade Compatibility Tool]至少需要2GB RAM才能執行。 建議使用此設定來避免因記憶體不足限制所造成的問題。 如果您以低[!DNL Upgrade Compatibility Tool]設定執行`upgrade:check`命令，`memory_limit`會顯示問題。
