---
source-git-commit: 92685411a41cb03f1ac9408b0cef2fe83b4a2a16
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 1%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**版本**： 3.0.25

此參考包含9個可透過`bin/uct`命令列工具使用的命令。
初始清單是在Adobe Commerce使用`bin/uct list`命令自動產生的。

## 一般

在[總覽](/help/upgrade/upgrade-compatibility-tool/overview.md)中進一步瞭解工具。

>[!NOTE]
>
>`composer update`命令無法升級此工具 — 您必須[下載並安裝最新版本](/help/upgrade/upgrade-compatibility-tool/run.md)。

此參考檔案是從應用程式原始碼產生。 若要變更檔案，您應在相關[程式碼基底](https://github.com/magento)存放庫中開啟對應命令的提取要求。 如需詳細資訊，請參閱[程式碼貢獻](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)。

### 全域選項

#### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

#### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

#### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

#### `--version`，`-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

#### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

#### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

#### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

提供殼層完成建議的內部命令

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--shell`，`-s`

殼層型別(「bash」、「fish」、「zsh」)

- 需要值

#### `--input`，`-i`

輸入權杖的陣列（例如COMP_WORDS或argv）

- 預設： `[]`
- 需要值

#### `--current`，`-c`

游標所在的「輸入」陣列索引（例如COMP_CWORD）

- 需要值

#### `--api-version`，`-a`

完成指令碼的API版本

- 需要值

#### `--symfony`，`-S`

已棄用

- 需要值


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

傾印殼層完成指令碼

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion )"
```

### 引數

#### `shell`

如果未指定shell型別（例如&quot;bash&quot;），則會使用&quot;$SHELL&quot;環境變數的值

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--debug`

追蹤完成偵錯記錄

- 預設： `false`
- 不接受值


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

顯示命令的說明

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### 引數

#### `command_name`

命令名稱

- 預設： `help`

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--format`

輸出格式（txt、xml、json或md）

- 預設： `txt`
- 需要值

#### `--raw`

輸出原始指令說明

- 預設： `false`
- 不接受值


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

清單命令

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### 引數

#### `namespace`

名稱空間名稱

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--raw`

輸出原始命令清單

- 預設： `false`
- 不接受值

#### `--format`

輸出格式（txt、xml、json或md）

- 預設： `txt`
- 需要值

#### `--short`

略過描述命令引數的方式

- 預設： `false`
- 不接受值


## `refactor`

```bash
bin/uct refactor <path>
```

解決可自動修正的問題。 將更新所提供路徑中的程式碼。

### 引數

#### `path`

解決中問題的路徑。

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

升級相容性工具是命令列工具，可分析安裝在Adobe Commerce執行個體中的所有非Adobe Commerce模組，以針對特定版本檢查執行個體。 傳回在升級至新版Adobe Commerce程式碼之前必須解決之錯誤和警告的清單。

### 引數

#### `dir`

Adobe Commerce安裝目錄。

- 必填


#### `vanilla-dir`

Adobe Commerce一般安裝目錄。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--output`，`-o`

匯出輸出的檔案路徑（Json格式）

- 接受值


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

允許列出兩個所選版本之間的Adobe Commerce DB結構描述差異。 可用版本： 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2 - p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4 - p1 | 2.3.4 - p2 | 2.3.5 | 2.3.5 - p1 | 2.3.5 - p2 | 2.3.6 | 2.3.6 - p1 | 2.3.7 | 2.3.7 - p1 | 2.3.7 - p2 | 2.3.7 - p3 | 2.3.7 - p4 | 2.4.0 | 2.4.0 - p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2 - p1 | 2.4.2 - p2 | 2.4.3 | 2.4.3-p1 | 2.4.3 - p2 | 2.4.3 - p3 | 2.4.4 | 2.4.4 - p1 | 2.4.5 | 2.4.4 - p2 | 2.4.5 - p1 | 2.4.4 - p3 | 2.4.4 - p4 | 2.4.4 - p5 | 2.4.5 - p2 | 2.4.5 - p3 | 2.4.5 - p4 | 2.4.6 | 2.4.6 - p1 | 2.4.6 - p2 | 2.4.7-beta1 | 2.4.4 - p6 | 2.4.5 - p5 | 2.4.6 - p3 | 2.4.7-beta2 | 2.4.4 - p7 | 2.4.5 - p6 | 2.4.6 - p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6 - p5 | 2.4.5 - p7 | 2.4.4 - p8 | 2.4.4 - p9 | 2.4.5 - p8 | 2.4.6 - p6 | 2.4.7 - p1 | 2.4.4-p10 | 2.4.5 - p9 | 2.4.6 - p7 | 2.4.7 - p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6 - p8 | 2.4.7 - p3 | 2.4.8-beta1 | 2.4.4-p12 | 2.4.5-p11 | 2.4.6 - p9 | 2.4.7 - p4 | 2.4.8-beta2 | 2.4.4-p13 | 2.4.5-p12 | 2.4.6-p10 | 2.4.7 - p5 | 2.4.8 | 2.4.9-alpha2 | 2.4.8 - p2 | 2.4.7 - p7 | 2.4.6-p12 | 2.4.5-p14 | 2.4.4-p15 | 2.4.9-alpha1 | 2.4.8 - p1 | 2.4.7 - p6 | 2.4.6-p11 | 2.4.5-p13 | 2.4.4-p14 | 2.4.9-alpha3 | 2.4.8 - p3 | 2.4.7 - p8 | 2.4.6-p13 | 2.4.5-p15 | 2.4.4-p16

### 引數

#### `current-version`

目前版本（例如2.3.2）。

- 必填


#### `target-version`

目標版本（例如2.4.5）。

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

GraphQL結構描述相容性驗證

### 引數

#### `schema1`

端點URL指向第一個GraphQL結構描述。

- 必填


#### `schema2`

指向第二個GraphQL結構的端點URL。

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--output`，`-o`

匯出輸出的檔案路徑（JSON格式）

- 接受值


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

升級相容性工具是命令列工具，可分析安裝在其中的所有模組，以針對特定版本檢查Adobe Commerce自訂執行個體。 傳回升級至最新版Adobe Commerce之前必須解決之錯誤和警告的清單。

### 引數

#### `dir`

Adobe Commerce安裝目錄。

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--current-version`，`-a`

如果省略，將會使用目前的Adobe Commerce版本、Adobe Commerce安裝版本。

- 接受值

#### `--coming-version`，`-c`

目標Adobe Commerce版本。 如果省略，將使用最新發行的Adobe Commerce穩定版本。 可用的Adobe Commerce版本： 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7 - p2 \| 2.3.7 - p3 \| 2.3.7 - p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3 - p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4 - p3 \| 2.4.4 - p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.4-p12 \| 2.4.4-p13 \| 2.4.4-p14 \| 2.4.4-p15 \| 2.4.4-p16 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5 - p3 \| 2.4.5 - p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.5-p11 \| 2.4.5-p12 \| 2.4.5-p13 \| 2.4.5-p14 \| 2.4.5-p15 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6 - p3 \| 2.4.6 - p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.6-p9 \| 2.4.6-p10 \| 2.4.6-p11 \| 2.4.6-p12 \| 2.4.6-p13 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7 - p1 \| 2.4.7 - p2 \| 2.4.7 - p3 \| 2.4.7 - p4 \| 2.4.7 - p5 \| 2.4.7-p6 \| 2.4.7 - p7 \| 2.4.7-p8 \| 2.4.8-beta1 \| 2.4.8-beta2 \| 2.4.8 \| 2.4.8-p1 \| 2.4.8-p2 \| 2.4.8 - p3 \| 2.4.9-alpha1 \| 2.4.9-alpha2 \| 2.4.9-alpha3

- 接受值

#### `--json-output-path`

輸出將匯出為JSON格式的檔案路徑

- 接受值

#### `--html-output-path`

輸出將匯出為HTML格式的檔案路徑

- 接受值

#### `--min-issue-level`

您要在報告中看到的最低問題層級（警告、錯誤或嚴重）。

- 預設： `warning`
- 接受值

#### `--ignore-current-version-compatibility-issues`，`-i`

忽略目前和未來版本的常見問題

- 預設： `false`
- 不接受值

#### `--context`

執行內容。 此選項僅供整合之用，不會影響執行結果。

- 需要值

