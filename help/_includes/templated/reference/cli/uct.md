---
source-git-commit: 19d19ef385cf4aaee3a255930af8e6d3b81de23a
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**： 3.0.16

此參照包含9個指令，這些指令可透過 `bin/uct` 命令列工具。
初始清單會使用 `bin/uct list` Adobe Commerce的命令。

進一步瞭解中的工具 [概觀](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>此參考是從應用程式程式碼基底產生的。 若要變更內容，您可以更新中對應命令實施的原始碼 [程式碼基底](https://github.com/magento) 存放庫並提交您的變更以供檢閱。 另一種方式是 _提供意見反應_ （尋找右上方的連結）。 如需貢獻准則，請參閱 [程式碼協助撰寫](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

提供殼層完成建議的內部命令


### `--shell`， `-s`

殼層型別(「bash」)

- 需要值

### `--input`， `-i`

輸入權杖的陣列（例如COMP_WORDS或argv）

- 預設： `[]`
- 需要值

### `--current`， `-c`

游標所在的「輸入」陣列索引（例如COMP_CWORD）

- 需要值

### `--symfony`， `-S`

完成指令碼的版本

- 需要值

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

傾印殼層完成指令碼


```
The completion command dumps the shell completion script required
to use shell autocompletion (currently only bash completion is supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion bash | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion bash > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion bash)"
```


### `shell`

如果未指定shell型別（例如&quot;bash&quot;），則會使用&quot;$SHELL&quot;環境變數的值


### `--debug`

追蹤完成偵錯記錄

- 預設： `false`
- 不接受值

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

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


### `command_name`

命令名稱

- 預設： `help`


### `--format`

輸出格式（txt、xml、json或md）

- 預設： `txt`
- 需要值

### `--raw`

輸出原始指令說明

- 預設： `false`
- 不接受值

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

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


### `namespace`

名稱空間名稱


### `--raw`

輸出原始命令清單

- 預設： `false`
- 不接受值

### `--format`

輸出格式（txt、xml、json或md）

- 預設： `txt`
- 需要值

### `--short`

略過描述命令引數的方式

- 預設： `false`
- 不接受值

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `refactor`

```bash
bin/uct refactor <path>
```

解決可自動修正的問題。 將更新所提供路徑中的程式碼。



### `path`

解決中問題的路徑。

- 必填

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

升級相容性工具是命令列工具，可分析安裝在Adobe Commerce執行個體中的所有非Adobe Commerce模組，以針對特定版本檢查執行個體。 傳回在升級至新版Adobe Commerce程式碼之前必須解決之錯誤和警告的清單。



### `dir`

Adobe Commerce安裝目錄。

- 必填

### `vanilla-dir`

Adobe Commerce一般安裝目錄。


### `--output`， `-o`

匯出輸出的檔案路徑（Json格式）

- 接受值

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

允許列出兩個所選版本之間的Adobe Commerce DB結構描述差異。 可用版本： 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2 - p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4 - p1 | 2.3.4 - p2 | 2.3.5 | 2.3.5 - p1 | 2.3.5 - p2 | 2.3.6 | 2.3.6 - p1 | 2.3.7 | 2.3.7 - p1 | 2.3.7 - p2 | 2.3.7 - p3 | 2.3.7 - p4 | 2.4.0 | 2.4.0 - p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2 - p1 | 2.4.2 - p2 | 2.4.3 | 2.4.3-p1 | 2.4.3 - p2 | 2.4.3 - p3 | 2.4.4 | 2.4.4 - p1 | 2.4.5 | 2.4.4 - p2 | 2.4.5 - p1 | 2.4.4 - p3 | 2.4.4 - p4 | 2.4.4 - p5 | 2.4.5 - p2 | 2.4.5 - p3 | 2.4.5 - p4 | 2.4.6 | 2.4.6 - p1 | 2.4.6 - p2 | 2.4.7-beta1 | 2.4.4 - p6 | 2.4.5 - p5 | 2.4.6 - p3 | 2.4.7-beta2 | 2.4.4 - p7 | 2.4.5 - p6 | 2.4.6 - p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6 - p5 | 2.4.5 - p7 | 2.4.4 - p8



### `current-version`

目前版本（例如2.3.2）。

- 必填

### `target-version`

目標版本（例如2.4.5）。

- 必填

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

GraphQL結構描述相容性驗證



### `schema1`

端點URL指向第一個GraphQL結構描述。

- 必填

### `schema2`

指向第二個GraphQL結構的端點URL。

- 必填

### `--output`， `-o`

匯出輸出的檔案路徑（JSON格式）

- 接受值

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

升級相容性工具是命令列工具，可分析安裝在其中的所有模組，以針對特定版本檢查Adobe Commerce自訂執行個體。 傳回升級至最新版Adobe Commerce之前必須解決之錯誤和警告的清單。



### `dir`

Adobe Commerce安裝目錄。

- 必填

### `--current-version`， `-a`

如果省略，將會使用目前的Adobe Commerce版本、Adobe Commerce安裝版本。

- 接受值

### `--coming-version`， `-c`

目標Adobe Commerce版本。 如果省略，將使用最新發行的Adobe Commerce穩定版本。 可用的Adobe Commerce版本： 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7 - p2 \| 2.3.7 - p3 \| 2.3.7 - p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3 - p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4 - p3 \| 2.4.4 - p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5 - p3 \| 2.4.5 - p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6 - p3 \| 2.4.6 - p4 \| 2.4.6-p5 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7

- 接受值

### `--json-output-path`

輸出將匯出為JSON格式的檔案路徑

- 接受值

### `--html-output-path`

輸出將以HTML格式匯出的檔案路徑

- 接受值

### `--min-issue-level`

您要在報告中看到的最低問題層級（警告、錯誤或嚴重）。

- 預設： `warning`
- 接受值

### `--ignore-current-version-compatibility-issues`， `-i`

忽略目前和未來版本的常見問題

- 預設： `false`
- 不接受值

### `--context`

執行內容。 此選項僅供整合之用，不會影響執行結果。

- 需要值

### `--help`， `-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`， `-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`， `-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`， `-V`

顯示此應用程式版本

- 預設： `false`
- 不接受值

### `--ansi`

強制（或停用 — no-ansi） ANSI輸出

- 不接受值

### `--no-ansi`

否定「 — ansi」選項

- 預設： `false`
- 不接受值

### `--no-interaction`， `-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值

