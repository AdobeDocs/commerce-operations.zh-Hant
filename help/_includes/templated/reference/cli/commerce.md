---
source-git-commit: 27e7a262fd1d8092045f5ebe2f88caaec37a6b0d
workflow-type: tm+mt
source-wordcount: '29783'
ht-degree: 0%

---
# magento-cloud(Adobe Commerce雲基礎架構)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**:1.42.0

此引用包含134個通過 `magento-cloud` 命令行工具。
初始清單是使用 `magento-cloud list` 的上界。

>[!NOTE]
>
>此引用是從應用程式碼庫生成的。 要更改內容，可以在中更新相應命令實現的原始碼 [雞](https://github.com/magento) 並提交更改以供審閱。 另一種方法是 _給我們反饋_ （查找右上方的連結）。 有關繳款指南，請參閱 [代碼貢獻](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)。

## `_completion`

BASH完成掛接。

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

### `--generate-hook`, `-g`

生成為此應用程式設定完成的BASH代碼。

- 預設值： `false`
- 不接受值

### `--program`, `-p`

應觸發完成的程式名 &lt;comment>（預設為絕對應用程式路徑）&lt;/comment>。

- 需要值

### `--multiple`, `-m`

生成的掛接可用於多個應用程式。

- 預設值： `false`
- 不接受值

### `--shell-type`

設定殼類型（zsh或bash）。 否則，將自動確定。

- 接受值


## `bot`

Magento雲機器人

```bash
magento-cloud bot [--party] [--parrot]
```

### `--party`



- 預設值： `false`
- 不接受值

### `--parrot`



- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `clear-cache`

清除CLI快取

```bash
magento-cloud clear-cache
```


```bash
clearcache
```


```bash
cc
```

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `decode`

對編碼字串(如MAGENTO_CLOUD_VARIABLES)進行解碼

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

要解碼的變數值

- 必需

### `--property`, `-P`

要在變數中查看的屬性

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `docs`

開啟聯機文檔

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

搜索詞

- 預設值： `[]`

- 陣列

### `--browser`

用於開啟URL的瀏覽器。 將0設定為無。

- 需要值

### `--pipe`

輸出要停止的URL。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `help`

顯示命令的幫助

```bash
magento-cloud help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

命令名

- 預設值： `help`


### `--format`

輸出格式（txt、xml、json或md）

- 預設值： `txt`
- 需要值

### `--raw`

輸出原始命令幫助

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `legacy-migrate`

從舊檔案結構遷移

```bash
magento-cloud legacy-migrate [--no-backup]
```

### `--no-backup`

不要建立項目的備份。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `list`

列出命令

```bash
magento-cloud list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```


### `command`

要執行的命令

- 必需

### `namespace`

命名空間名稱


### `--raw`

輸出原始命令清單

- 預設值： `false`
- 不接受值

### `--format`

輸出格式（txt、xml、json或md）

- 預設值： `txt`
- 需要值

### `--all`

顯示所有命令，包括隱藏的命令

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `multi`

對多個項目執行命令

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd> (<cmd>)...
```


### `cmd`

要執行的命令

- 預設值： `[]`

- 必需
- 陣列

### `--projects`, `-p`

項目ID的清單，用逗號和/或空格分隔

- 需要值

### `--continue`

即使遇到異常，仍繼續運行命令

- 預設值： `false`
- 不接受值

### `--sort`

用於對項目選項清單排序的屬性

- 預設值： `title`
- 需要值

### `--reverse`

衝銷項目選項的順序

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `web`

開啟Web UI

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--browser`

用於開啟URL的瀏覽器。 將0設定為無。

- 需要值

### `--pipe`

輸出要停止的URL。

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `welcome`

歡迎使用Magento雲

```bash
magento-cloud welcome
```

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `winky`



```bash
magento-cloud winky
```

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `activity:cancel`

取消活動

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

活動ID。 預設為最近的可取消活動。


### `--type`

按類型篩選（選擇預設活動時）。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作類型的通配符，例如「%var%」以選擇與變數相關的活動。

- 預設值： `[]`
- 需要值

### `--exclude-type`

按類型排除（選擇預設活動時）。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作通配符以排除類型。

- 預設值： `[]`
- 需要值

### `--all`, `-a`

檢查所有環境中的最近活動（選擇預設活動時）

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `activity:get`

查看有關單個活動的詳細資訊

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

活動ID。 預設為最近的活動。


### `--property`, `-P`

要查看的屬性

- 需要值

### `--type`

按類型篩選（選擇預設活動時）。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作類型的通配符，例如「%var%」以選擇與變數相關的活動。

- 預設值： `[]`
- 需要值

### `--exclude-type`

按類型排除（選擇預設活動時）。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作通配符以排除類型。

- 預設值： `[]`
- 需要值

### `--state`

按狀態篩選（選擇預設活動時）:in_progress 、 pending 、 complete或canceled。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--result`

按結果篩選（選擇預設活動時）:成功或失敗

- 需要值

### `--incomplete`, `-i`

僅包括未完成的活動（選擇預設活動時）。 這是對 &lt;info>-state=正在進行，掛起&lt;/info>

- 預設值： `false`
- 不接受值

### `--all`, `-a`

檢查所有環境中的最近活動（選擇預設活動時）

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `activity:list`

獲取環境或項目的活動清單

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
activities
```


```bash
act
```

### `--type`, `-t`

按類型篩選活動如果將清單指定為單個值(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作類型的通配符，例如「%var%」以選擇與變數相關的活動。

- 預設值： `[]`
- 需要值

### `--exclude-type`, `-x`

按類型排除活動。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作通配符以排除類型。

- 預設值： `[]`
- 需要值

### `--limit`

限制顯示的結果數

- 預設值： `10`
- 需要值

### `--start`

將只列出在此日期之前建立的活動

- 需要值

### `--state`

按狀態篩選活動：in_progress 、 pending 、 complete或canceled。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--result`

按結果篩選活動：成功或失敗

- 需要值

### `--incomplete`, `-i`

僅列出未完成的活動

- 預設值： `false`
- 不接受值

### `--all`, `-a`

列出所有環境中的活動

- 預設值： `false`
- 不接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：id*、created*、description*、progress*、state*、result*、completed、environments、type(* = default columns)。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `activity:log`

顯示活動的日誌

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

活動ID。 預設為最近的活動。


### `--refresh`

活動刷新間隔（秒）。 設定為0可禁用刷新。

- 預設值： `3`
- 需要值

### `--timestamps`, `-t`

在每個消息旁顯示時間戳

- 預設值： `false`
- 不接受值

### `--type`

按類型篩選（選擇預設活動時）。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作類型的通配符，例如「%var%」以選擇與變數相關的活動。

- 預設值： `[]`
- 需要值

### `--exclude-type`

按類型排除（選擇預設活動時）。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作通配符以排除類型。

- 預設值： `[]`
- 需要值

### `--state`

按狀態篩選（選擇預設活動時）:in_progress 、 pending 、 complete或canceled。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--result`

按結果篩選（選擇預設活動時）:成功或失敗

- 需要值

### `--incomplete`, `-i`

僅包括未完成的活動（選擇預設活動時）。 這是對 &lt;info>-state=正在進行，掛起&lt;/info>

- 預設值： `false`
- 不接受值

### `--all`, `-a`

檢查所有環境中的最近活動（選擇預設活動時）

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `api:curl`

在Magento雲API上運行已驗證的cURL請求

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [--] [<path>]
```


### `path`

API路徑


### `--request`, `-X`

要使用的請求方法

- 需要值

### `--data`, `-d`

要發送的資料

- 需要值

### `--json`

要發送的JSON資料

- 需要值

### `--include`, `-i`

在輸出中包括標題

- 預設值： `false`
- 不接受值

### `--head`, `-I`

僅提取標頭

- 預設值： `false`
- 不接受值

### `--disable-compression`

不使用curl — 壓縮標誌

- 預設值： `false`
- 不接受值

### `--enable-glob`

啟用curl globbing（刪除 — globoff標誌）

- 預設值： `false`
- 不接受值

### `--fail`, `-f`

失敗，錯誤響應沒有輸出

- 預設值： `false`
- 不接受值

### `--header`, `-H`

額外標頭

- 預設值： `[]`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `app:config-get`

查看應用的配置

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--property`, `-P`

要查看的配置屬性

- 需要值

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--identity-file`, `-i`

[已棄用選項，不再使用]

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `app:list`

列出項目中的應用

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
apps
```

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：name*、type*、disk、path、size（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `auth:api-token-login`

使用API令牌登錄Magento雲

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `auth:browser-login`

通過瀏覽器登錄Magento雲

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```


```bash
login
```

### `--force`, `-f`

再次登錄，即使已登錄

- 預設值： `false`
- 不接受值

### `--browser`

用於開啟URL的瀏覽器。 將0設定為無。

- 需要值

### `--pipe`

輸出要停止的URL。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `auth:info`

顯示帳戶資訊

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

要查看的帳戶屬性


### `--no-auto-login`

跳過自動登錄。 如果未登錄，將不輸出任何內容，並且退出代碼將為0（假設沒有其他錯誤）。

- 預設值： `false`
- 不接受值

### `--property`, `-P`

要查看的帳戶屬性（備用語法）

- 需要值

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `auth:logout`

註銷Magento雲

```bash
magento-cloud logout [-a|--all] [--other]
```


```bash
logout
```

### `--all`, `-a`

從所有本地會話註銷

- 預設值： `false`
- 不接受值

### `--other`

從其他本地會話註銷

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>使用用戶名和密碼登錄Magento雲

```bash
magento-cloud auth:password-login
```


```bash
auth:login
```

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `auth:token`

獲取請求Magento雲API的OAuth 2訪問令牌

```bash
magento-cloud auth:token [-H|--header] [-W|--no-warn]
```

### `--header`, `-H`

在令牌前加「授權：生成RFC 6750報頭的承載者」

- 預設值： `false`
- 不接受值

### `--no-warn`, `-W`

取消預設打印到stderr的警告。 與重定向stderr相比，此選項更為首選，因為這將隱藏其他可能有用的消息。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `blackfire:setup`

為項目設定Blackfire.io整合

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--server_id`

伺服器ID

- 需要值

### `--server_token`

伺服器令牌

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `blue-green:conclude`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 阿爾法 ]&lt;/>完成藍綠部署

```bash
magento-cloud blue-green:conclude [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `blue-green:deploy`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 阿爾法 ]&lt;/>執行藍綠部署

```bash
magento-cloud blue-green:deploy [--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`

設定最新版本的工藝路線百分比

- 預設值： `100`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `blue-green:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 阿爾法 ]&lt;/>啟用藍綠部署

```bash
magento-cloud blue-green:enable [-%|--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`, `-%`

設定最新版本的工藝路線百分比

- 預設值： `100`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `certificate:add`

向項目添加SSL證書

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--cert`

證書檔案的路徑

- 需要值

### `--key`

證書私鑰檔案的路徑

- 需要值

### `--chain`

證書鏈檔案的路徑

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `certificate:delete`

從項目中刪除證書

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

證書ID（或其開頭）

- 必需

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `certificate:get`

查看證書

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] <id>
```


### `id`

證書ID（或其開頭）

- 必需

### `--property`, `-P`

要查看的證書屬性

- 需要值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `certificate:list`

列出項目證書

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
certificates
```


```bash
certs
```

### `--domain`

按域名篩選（不區分大小寫的搜索）

- 需要值

### `--exclude-domain`

排除證書，按域名匹配（不區分大小寫的搜索）

- 需要值

### `--issuer`

按頒發者篩選

- 需要值

### `--only-auto`

僅顯示自動設定的證書

- 預設值： `false`
- 不接受值

### `--no-auto`

僅顯示手動添加的證書

- 預設值： `false`
- 不接受值

### `--ignore-expiry`

顯示過期和未過期的證書

- 預設值： `false`
- 不接受值

### `--only-expired`

僅顯示過期的證書

- 預設值： `false`
- 不接受值

### `--no-expired`

僅顯示未過期的證書（預設）

- 預設值： `false`
- 不接受值

### `--pipe-domains`

僅返回證書所涵蓋的域名清單

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：已建立、域、過期、ID、頒發者。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `commit:get`

顯示提交詳細資訊

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--] [<commit>]
```


### `commit`

提交SHA。 這也可以接受「HEAD」和父提交的插入符號(^)或顎化符(~)尾碼。

- 預設值： `HEAD`


### `--property`, `-P`

要顯示的commit屬性。

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--format`

已棄用

- 需要值

### `--columns`

已棄用

- 預設值： `[]`
- 需要值

### `--no-header`

已棄用

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `commit:list`

清單提交

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


```bash
commits
```


### `commit`

啟動Git提交SHA。 這也可以接受「HEAD」和父提交的插入符號(^)或顎化符(~)尾碼。


### `--limit`

要顯示的提交數。

- 預設值： `10`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：作者，日期，沙，摘要。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `db:dump`

建立遠程資料庫的本地轉儲

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```


```bash
sql-dump
```


```bash
environment:sql-dump
```

### `--schema`

要轉儲的架構。 省略以使用預設架構（通常為&quot;main&quot;）。

- 需要值

### `--file`, `-f`

轉儲的自定義檔案名

- 需要值

### `--directory`, `-d`

轉儲的自定義目錄

- 需要值

### `--gzip`, `-z`

使用gzip壓縮轉儲

- 預設值： `false`
- 不接受值

### `--timestamp`, `-t`

將時間戳添加到轉儲檔案名

- 預設值： `false`
- 不接受值

### `--stdout`, `-o`

輸出到STDOUT而不是檔案

- 預設值： `false`
- 不接受值

### `--table`

要包括的表

- 預設值： `[]`
- 需要值

### `--exclude-table`

要排除的表

- 預設值： `[]`
- 需要值

### `--schema-only`

僅轉儲架構，無資料

- 預設值： `false`
- 不接受值

### `--charset`

轉儲的字元集編碼

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `db:size`

估計資料庫的磁碟使用率

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

### `--bytes`, `-B`

以位元組為單位顯示大小。

- 預設值： `false`
- 不接受值

### `--cleanup`, `-C`

檢查表是否可以清理並顯示建議（僅限InnoDb）。

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：max、percent_used、used。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `db:sql`

在遠程資料庫上運行SQL

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```


```bash
sql
```


```bash
environment:sql
```


### `query`

要執行的SQL陳述式


### `--raw`

生成原始、非表格輸出

- 預設值： `false`
- 不接受值

### `--schema`

要使用的架構。 省略以使用預設架構（通常為&quot;main&quot;）。 傳遞空字串以不使用任何架構。

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `domain:add`

向項目添加新域

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

域名

- 必需

### `--cert`

此域的證書檔案的路徑

- 需要值

### `--key`

提供的證書的私鑰檔案的路徑。

- 需要值

### `--chain`

提供的證書的證書鏈檔案或檔案的路徑

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `domain:delete`

從項目中刪除域

```bash
magento-cloud domain:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

域名

- 必需

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `domain:get`

顯示域的詳細資訊

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] [<name>]
```


### `name`

域名


### `--property`, `-P`

要查看的域屬性

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `domain:list`

獲取所有域的清單

```bash
magento-cloud domains [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
domains
```

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：name*、ssl*、created_at*、updated_at（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `domain:update`

更新域

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

域名

- 必需

### `--cert`

此域的證書檔案的路徑

- 需要值

### `--key`

提供的證書的私鑰檔案的路徑。

- 需要值

### `--chain`

提供的證書的證書鏈檔案或檔案的路徑

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:activate`

激活環境

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

要激活的環境

- 預設值： `[]`

- 陣列

### `--parent`

在激活前設定新環境父項

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:branch`

分支環境

```bash
magento-cloud branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


```bash
branch
```


### `id`

新環境的ID（分支名稱）


### `parent`

新環境的父級


### `--title`

新環境的標題

- 需要值

### `--type`

新環境的類型

- 需要值

### `--force`

即使無法在本地檢出分支，也建立新環境

- 預設值： `false`
- 不接受值

### `--no-clone-parent`

不克隆父分支的資料

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:checkout`

檢出環境

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


```bash
checkout
```


### `id`

要簽出的環境的ID。 例如：&quot;sprint2&quot;


### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:curl`

在環境的API上運行經過驗證的cURL請求

```bash
magento-cloud environment:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

API路徑


### `--request`, `-X`

要使用的請求方法

- 需要值

### `--data`, `-d`

要發送的資料

- 需要值

### `--json`

要發送的JSON資料

- 需要值

### `--include`, `-i`

在輸出中包括標題

- 預設值： `false`
- 不接受值

### `--head`, `-I`

僅提取標頭

- 預設值： `false`
- 不接受值

### `--disable-compression`

不使用curl — 壓縮標誌

- 預設值： `false`
- 不接受值

### `--enable-glob`

啟用curl globbing（刪除 — globoff標誌）

- 預設值： `false`
- 不接受值

### `--fail`, `-f`

失敗，錯誤響應沒有輸出

- 預設值： `false`
- 不接受值

### `--header`, `-H`

額外標頭

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:delete`

刪除一個或多個環境

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--type TYPE] [-t|--only-type ONLY-TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [--inactive] [--merged] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


```bash
environment:deactivate
```


### `environment`

要刪除的環境。 %字元可用作通配符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`

- 陣列

### `--delete-branch`

刪除Git分支（非活動環境）

- 預設值： `false`
- 不接受值

### `--no-delete-branch`

不刪除Git分支（非活動環境）

- 預設值： `false`
- 不接受值

### `--type`

刪除類型的所有環境（添加到選定的任何其他環境）如果將清單指定為單個值(如&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--only-type`, `-t`

僅刪除特定類型的環境如果將清單指定為單個值(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--exclude`

不要刪除的環境。 %字元可用作通配符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--exclude-type`

不要刪除的環境類型如果清單被指定為單個值(如&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--inactive`

刪除所有非活動環境（添加到選定的任何其他環境）

- 預設值： `false`
- 不接受值

### `--merged`

刪除所有合併的環境（添加到所選的其他環境）

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:http-access`

更新環境的HTTP訪問設定

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
httpaccess
```

### `--access`

以「permission:address」格式訪問限制。 使用0清除所有地址。

- 預設值： `[]`
- 需要值

### `--auth`

HTTP Basic身份驗證憑據格式為「username:password」。 使用0清除所有憑據。

- 預設值： `[]`
- 需要值

### `--enabled`

是否應啟用訪問控制：1要啟用，0要禁用

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:info`

讀取或設定環境的屬性

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
environment:metadata
```


### `property`

屬性的名稱


### `value`

為屬性設定新值


### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:init`

從公共Git儲存庫初始化環境

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

Git儲存庫的URL

- 必需

### `--profile`

配置檔案的名稱

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:list`

獲取環境清單

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
environments
```


```bash
env
```

### `--no-inactive`, `-I`

不顯示非活動環境

- 預設值： `false`
- 不接受值

### `--pipe`

輸出環境ID的簡單清單。

- 預設值： `false`
- 不接受值

### `--refresh`

是否刷新清單。

- 預設值： `1`
- 需要值

### `--sort`

要排序的屬性

- 預設值： `title`
- 需要值

### `--reverse`

按反向（降序）順序排序

- 預設值： `false`
- 不接受值

### `--type`

按環境類型篩選清單。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：id*、title*、status*、type*、created、machine_name、updated（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:logs`

讀取環境日誌

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [--] [<type>]
```


```bash
log
```


```bash
logs
```


### `type`

日誌類型，例如&quot;access&quot;或&quot;error&quot;


### `--lines`

要顯示的行數

- 預設值： `100`
- 需要值

### `--tail`

連續跟蹤日誌

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:merge`

合併環境

```bash
magento-cloud merge [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
merge
```


### `environment`

要合併的環境


### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:push`

將代碼推送到環境

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


```bash
push
```


### `source`

源引用：分支名稱或提交哈希

- 預設值： `HEAD`


### `--target`

目標分支名稱

- 需要值

### `--force`, `-f`

允許非快速轉發更新

- 預設值： `false`
- 不接受值

### `--force-with-lease`

如果遠程跟蹤分支是最新的，則允許非快速轉發更新

- 預設值： `false`
- 不接受值

### `--set-upstream`, `-u`

將目標環境設定為源分支的上游

- 預設值： `false`
- 不接受值

### `--activate`

在推送之前激活環境

- 預設值： `false`
- 不接受值

### `--branch`

已棄用：別名 — 激活

- 預設值： `false`
- 不接受值

### `--parent`

設定新環境父項（僅與 — activate一起使用）

- 需要值

### `--type`

設定環境類型（僅與 — activate一起使用）

- 需要值

### `--no-clone-parent`

不克隆父分支的資料（僅與 — activate一起使用）

- 預設值： `false`
- 不接受值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:redeploy`

重新部署環境

```bash
magento-cloud redeploy [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
redeploy
```

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:relationships`

顯示環境的關係

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


```bash
relationships
```


### `environment`

環境


### `--property`, `-P`

要查看的關係屬性

- 需要值

### `--refresh`

是否刷新關係

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:scp`

使用scp將檔案複製到當前環境並從當前環境複製檔案

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


```bash
scp
```


### `files`

要複製的檔案。 使用遠程：定義遠程位置的前置詞。

- 預設值： `[]`

- 陣列

### `--recursive`, `-r`

遞歸複製整個目錄

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:set-remote`

將遠程環境設定為映射到分支

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```


### `environment`

環境電腦名。 設定為0可刪除分支的映射

- 必需

### `branch`

要映射的Git分支（預設為當前分支）


### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:ssh`

SSH到當前環境

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


```bash
ssh
```


### `cmd`

要在環境中運行的命令。

- 預設值： `[]`

- 陣列

### `--pipe`

僅輸出SSH URL。

- 預設值： `false`
- 不接受值

### `--all`

輸出所有SSH URL（用於每個應用）。

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:synchronize`

同步環境的代碼和/或來自其父代的資料

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


```bash
sync
```


### `synchronize`

要同步的內容：&quot;code&quot;、&quot;data&quot;或兩者

- 預設值： `[]`

- 陣列

### `--rebase`

通過基於而不是合併來同步代碼

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:url`

獲取環境的公共URL

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
url
```

### `--primary`, `-1`

僅返回主路由的URL

- 預設值： `false`
- 不接受值

### `--browser`

用於開啟URL的瀏覽器。 將0設定為無。

- 需要值

### `--pipe`

輸出要停止的URL。

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `environment:xdebug`

在環境中開啟到Xdebug的通道

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```


```bash
xdebug
```

### `--port`

本地埠

- 預設值： `9000`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:activity:get`

查看有關單個整合活動的詳細資訊

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

整合ID。 留空以從清單中進行選擇。


### `activity`

活動ID。 預設為最近的整合活動。


### `--property`, `-P`

要查看的屬性

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

[不建議使用的選項]

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:activity:list`

獲取整合活動清單

```bash
magento-cloud i:act [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


```bash
i:act
```


```bash
integration:activities
```


### `id`

整合ID。 留空以從清單中進行選擇。


### `--type`

按類型篩選活動。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--exclude-type`, `-x`

按類型排除活動。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。 %字元可用作通配符以排除類型。

- 預設值： `[]`
- 需要值

### `--limit`

限制顯示的結果數

- 預設值： `10`
- 需要值

### `--start`

將只列出在此日期之前建立的活動

- 需要值

### `--state`

按州篩選活動。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--result`

按結果篩選活動

- 需要值

### `--incomplete`, `-i`

僅列出未完成的活動

- 預設值： `false`
- 不接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：id*、created*、description*、type*、state*、result*，已完成（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

[不建議使用的選項]

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:activity:log`

顯示整合活動的日誌

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

整合ID。 留空以從清單中進行選擇。


### `activity`

活動ID。 預設為最近的整合活動。


### `--timestamps`, `-t`

在每個消息旁顯示時間戳

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

[不建議使用的選項]

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:add`

向項目添加整合

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--type`

整合類型(「bitbucket」、「bitbucketserver」、「github」、「gitlab」、「webhook」、「health.email」、「health.pagerduty」、「health.slack」、「health.webhook」、「script」、「newrelic」、「splunk」、「sumologic」、「syslogic」)

- 需要值

### `--base-url`

伺服器安裝的基URL

- 需要值

### `--username`

Bitbucket伺服器用戶名

- 需要值

### `--token`

整合的驗證或訪問令牌

- 需要值

### `--key`

Bitbucket OAuth使用者密鑰

- 需要值

### `--secret`

Bitbucket OAuth消費者機密

- 需要值

### `--license-key`

New Relic日誌許可證密鑰

- 需要值

### `--server-project`

項目(例如&#39;namespace/repo)

- 需要值

### `--repository`

要跟蹤的儲存庫(例如&#39;owner/repository&#39;)

- 需要值

### `--build-merge-requests`

GitLab:將合併請求構建為環境

- 預設值： `true`
- 需要值

### `--build-pull-requests`

將每個拉入請求構建為環境

- 預設值： `true`
- 需要值

### `--build-draft-pull-requests`

生成草稿拉取請求

- 預設值： `true`
- 需要值

### `--build-pull-requests-post-merge`

根據合併後狀態生成拉入請求

- 預設值： `false`
- 需要值

### `--build-wip-merge-requests`

GitLab:構建WIP合併請求

- 預設值： `true`
- 需要值

### `--merge-requests-clone-parent-data`

GitLab:合併請求的克隆資料

- 預設值： `true`
- 需要值

### `--pull-requests-clone-parent-data`

克隆父環境的資料以獲取請求

- 預設值： `true`
- 需要值

### `--resync-pull-requests`

在每個生成上重新同步拉取請求環境資料

- 預設值： `false`
- 需要值

### `--fetch-branches`

從遠程（作為非活動環境）獲取所有分支

- 預設值： `true`
- 需要值

### `--prune-branches`

刪除遠程上不存在的分支

- 預設值： `true`
- 需要值

### `--url`

整合的URL或API終結點

- 需要值

### `--shared-key`

網鈎：JWS共用密鑰

- 需要值

### `--file`

包含要上載的指令碼的本地檔案的名稱

- 需要值

### `--events`

要執行操作的事件清單，如環境推送

- 預設值： `*`
- 需要值

### `--states`

要執行操作（例如，待處理）的狀態清單(_P)

- 預設值： `complete`
- 需要值

### `--environments`

要包括的環境ID

- 預設值： `*`
- 需要值

### `--excluded-environments`

要排除的環境ID

- 預設值： `[]`
- 需要值

### `--from-address`

[可選] 警報電子郵件的自定義地址

- 需要值

### `--recipients`

收件人電子郵件地址

- 預設值： `[]`
- 需要值

### `--channel`

Slack頻道

- 需要值

### `--routing-key`

PagerDuty路由鍵

- 需要值

### `--category`

用於篩選的Sumo邏輯類別

- 需要值

### `--index`

Splunk指數

- 需要值

### `--sourcetype`

Splunk事件源類型

- 需要值

### `--protocol`

Syslog傳輸協定(「tcp」、「udp」、「tls」)

- 預設值： `tls`
- 需要值

### `--syslog-host`

Syslog中繼/收集器主機

- 需要值

### `--syslog-port`

Syslog中繼/收集器埠

- 需要值

### `--facility`

Syslog工具

- 預設值： `1`
- 需要值

### `--message-format`

Syslog消息格式（&#39;rfc3164&#39;或&#39;rfc5424&#39;）

- 預設值： `rfc5424`
- 需要值

### `--auth-mode`

驗證模式（「prefix」或「structured_data」）

- 預設值： `prefix`
- 需要值

### `--auth-token`

驗證令牌

- 需要值

### `--verify-tls`

是否應啟用HTTPS證書驗證（推薦）

- 預設值： `true`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:delete`

從項目中刪除整合

```bash
magento-cloud integration:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

整合ID。 留空以從清單中進行選擇。


### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:get`

查看整合的詳細資訊

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<id>]
```


### `id`

整合ID。 留空以從清單中進行選擇。


### `--property`, `-P`

要查看的整合屬性

- 接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:list`

查看項目整合清單

```bash
magento-cloud integrations [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
integrations
```

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：id,summary, type。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:update`

更新整合

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

要更新的整合的ID


### `--type`

整合類型(「bitbucket」、「bitbucketserver」、「github」、「gitlab」、「webhook」、「health.email」、「health.pagerduty」、「health.slack」、「health.webhook」、「script」、「newrelic」、「splunk」、「sumologic」、「syslogic」)

- 需要值

### `--base-url`

伺服器安裝的基URL

- 需要值

### `--username`

Bitbucket伺服器用戶名

- 需要值

### `--token`

整合的驗證或訪問令牌

- 需要值

### `--key`

Bitbucket OAuth使用者密鑰

- 需要值

### `--secret`

Bitbucket OAuth消費者機密

- 需要值

### `--license-key`

New Relic日誌許可證密鑰

- 需要值

### `--server-project`

項目(例如&#39;namespace/repo)

- 需要值

### `--repository`

要跟蹤的儲存庫(例如&#39;owner/repository&#39;)

- 需要值

### `--build-merge-requests`

GitLab:將合併請求構建為環境

- 預設值： `true`
- 需要值

### `--build-pull-requests`

將每個拉入請求構建為環境

- 預設值： `true`
- 需要值

### `--build-draft-pull-requests`

生成草稿拉取請求

- 預設值： `true`
- 需要值

### `--build-pull-requests-post-merge`

根據合併後狀態生成拉入請求

- 預設值： `false`
- 需要值

### `--build-wip-merge-requests`

GitLab:構建WIP合併請求

- 預設值： `true`
- 需要值

### `--merge-requests-clone-parent-data`

GitLab:合併請求的克隆資料

- 預設值： `true`
- 需要值

### `--pull-requests-clone-parent-data`

克隆父環境的資料以獲取請求

- 預設值： `true`
- 需要值

### `--resync-pull-requests`

在每個生成上重新同步拉取請求環境資料

- 預設值： `false`
- 需要值

### `--fetch-branches`

從遠程（作為非活動環境）獲取所有分支

- 預設值： `true`
- 需要值

### `--prune-branches`

刪除遠程上不存在的分支

- 預設值： `true`
- 需要值

### `--url`

整合的URL或API終結點

- 需要值

### `--shared-key`

網鈎：JWS共用密鑰

- 需要值

### `--file`

包含要上載的指令碼的本地檔案的名稱

- 需要值

### `--events`

要執行操作的事件清單，如環境推送

- 預設值： `*`
- 需要值

### `--states`

要執行操作（例如，待處理）的狀態清單(_P)

- 預設值： `complete`
- 需要值

### `--environments`

要包括的環境ID

- 預設值： `*`
- 需要值

### `--excluded-environments`

要排除的環境ID

- 預設值： `[]`
- 需要值

### `--from-address`

[可選] 警報電子郵件的自定義地址

- 需要值

### `--recipients`

收件人電子郵件地址

- 預設值： `[]`
- 需要值

### `--channel`

Slack頻道

- 需要值

### `--routing-key`

PagerDuty路由鍵

- 需要值

### `--category`

用於篩選的Sumo邏輯類別

- 需要值

### `--index`

Splunk指數

- 需要值

### `--sourcetype`

Splunk事件源類型

- 需要值

### `--protocol`

Syslog傳輸協定(「tcp」、「udp」、「tls」)

- 預設值： `tls`
- 需要值

### `--syslog-host`

Syslog中繼/收集器主機

- 需要值

### `--syslog-port`

Syslog中繼/收集器埠

- 需要值

### `--facility`

Syslog工具

- 預設值： `1`
- 需要值

### `--message-format`

Syslog消息格式（&#39;rfc3164&#39;或&#39;rfc5424&#39;）

- 預設值： `rfc5424`
- 需要值

### `--auth-mode`

驗證模式（「prefix」或「structured_data」）

- 預設值： `prefix`
- 需要值

### `--auth-token`

驗證令牌

- 需要值

### `--verify-tls`

是否應啟用HTTPS證書驗證（推薦）

- 預設值： `true`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `integration:validate`

驗證現有整合

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--] [<id>]
```


### `id`

整合ID。 留空以從清單中進行選擇。


### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `local:build`

在本地構建當前項目

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```


```bash
build
```


### `app`

指定要生成的應用程式

- 預設值： `[]`

- 陣列

### `--abslinks`, `-a`

使用絕對連結

- 預設值： `false`
- 不接受值

### `--source`, `-s`

源目錄。 預設為當前項目根。

- 需要值

### `--destination`, `-d`

每個應用的Web根目錄將連結到的目標。 預設值：_ww

- 需要值

### `--copy`, `-c`

複製到生成目錄，而不是從源連結

- 預設值： `false`
- 不接受值

### `--clone`

使用Git將當前HEAD克隆到生成目錄

- 預設值： `false`
- 不接受值

### `--run-deploy-hooks`

運行deploy和/或post_deploy掛接

- 預設值： `false`
- 不接受值

### `--no-clean`

不刪除舊版本

- 預設值： `false`
- 不接受值

### `--no-archive`

不建立或使用生成存檔

- 預設值： `false`
- 不接受值

### `--no-backup`

不備份上一版本

- 預設值： `false`
- 不接受值

### `--no-cache`

禁用快取

- 預設值： `false`
- 不接受值

### `--no-build-hooks`

不運行生成後掛接

- 預設值： `false`
- 不接受值

### `--no-deps`

不在本地安裝生成依賴項

- 預設值： `false`
- 不接受值

### `--working-copy`

德拉什：使用git克隆每個Drupal模組的儲存庫，而不是簡單地下載版本

- 預設值： `false`
- 不接受值

### `--concurrency`

德拉什：設定將同時處理的併發項目數

- 預設值： `4`
- 需要值

### `--lock`

德拉什：建立或更新鎖定檔案（僅適用於Drash版本7+）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `local:clean`

刪除舊項目生成

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```


```bash
clean
```

### `--keep`

要保留的最大生成數

- 預設值： `5`
- 需要值

### `--max-age`

生成的最大時間（以秒為單位）。 如果未設定，則忽略。

- 需要值

### `--include-active`

也刪除活動生成

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `local:dir`

查找本地項目根

```bash
magento-cloud dir [<subdir>]
```


```bash
dir
```


### `subdir`

要查找的子目錄（「local」、「web」或「shared」）


### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `metrics:disk-usage`

顯示服務上的磁碟使用情況

```bash
magento-cloud disk [-s|--service SERVICE] [--type TYPE] [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-B|--bytes] [-1|--latest] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
disk
```

### `--service`, `-s`

服務名稱

- 需要值

### `--type`

服務類型（如果未提供服務名），如mysql、pgsql、mongodb等。 類型版本不是必需的。

- 需要值

### `--range`, `-r`

時間範圍。 將在此持續時間內載入度量，直到結束時間（ — 到）。 可以指定單位：小時(h)、分鐘(m)或秒(s)。 最小 &lt;comment>5米&lt;/comment>，最大值 &lt;comment>8小時&lt;/comment> 或更多（取決於項目），預設 &lt;comment>10米&lt;/comment>。

- 需要值

### `--interval`, `-i`

時間間隔。 預設為範圍的劃分。 可以指定單位：小時(h)、分鐘(m)或秒(s)。 最小 &lt;comment>1米&lt;/comment>，最大值 &lt;comment>1小時&lt;/comment>。

- 需要值

### `--to`

結束時間。 預設為現在。

- 需要值

### `--bytes`, `-B`

以位元組為單位顯示大小

- 預設值： `false`
- 不接受值

### `--latest`, `-1`

僅顯示最新的單個資料點

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：timestamp*, used*, limit*,%*, ipercent*, imit, interval, iused（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `mount:download`

使用rsync從裝載下載檔案

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--all`, `-a`

從所有裝載下載

- 預設值： `false`
- 不接受值

### `--mount`, `-m`

裝載（作為應用程式相對路徑）

- 需要值

### `--target`

要下載檔案的目錄。 如果使用 — all ，則裝載路徑將被追加

- 需要值

### `--source-path`

使用裝載的源路徑（而不是裝載路徑）作為目標的子目錄，當使用 — all時

- 預設值： `false`
- 不接受值

### `--delete`

是否刪除目標目錄中的無關檔案

- 預設值： `false`
- 不接受值

### `--exclude`

要從下載中排除的檔案（模式）

- 預設值： `[]`
- 需要值

### `--include`

要包括在下載中的檔案（模式）

- 預設值： `[]`
- 需要值

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `mount:list`

獲取裝載清單

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```


```bash
mounts
```

### `--paths`

僅輸出裝載路徑（每行一條）

- 預設值： `false`
- 不接受值

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：定義，路徑。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `mount:size`

檢查裝載的磁碟使用情況

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```

### `--bytes`, `-B`

以位元組為單位顯示大小

- 預設值： `false`
- 不接受值

### `--refresh`

刷新快取

- 預設值： `false`
- 不接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：availe、max、mounts、percent_used、sizes、used。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `mount:upload`

使用rsync將檔案上載到裝載

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--source`

包含要上載的檔案的目錄

- 需要值

### `--mount`, `-m`

裝載（作為應用程式相對路徑）

- 需要值

### `--delete`

是否在裝載中刪除無關檔案

- 預設值： `false`
- 不接受值

### `--exclude`

要從上載中排除的檔案（陣列）

- 預設值： `[]`
- 需要值

### `--include`

要包括在上載中的檔案（模式）

- 預設值： `[]`
- 需要值

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--worker`

工作人員名稱

- 需要值

### `--instance`, `-I`

實例ID

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:clear-build-cache`

清除項目的生成快取

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT]
```

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:curl`

對項目的API運行經過驗證的cURL請求

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--] [<path>]
```


### `path`

API路徑


### `--request`, `-X`

要使用的請求方法

- 需要值

### `--data`, `-d`

要發送的資料

- 需要值

### `--json`

要發送的JSON資料

- 需要值

### `--include`, `-i`

在輸出中包括標題

- 預設值： `false`
- 不接受值

### `--head`, `-I`

僅提取標頭

- 預設值： `false`
- 不接受值

### `--disable-compression`

不使用curl — 壓縮標誌

- 預設值： `false`
- 不接受值

### `--enable-glob`

啟用curl globbing（刪除 — globoff標誌）

- 預設值： `false`
- 不接受值

### `--fail`, `-f`

失敗，錯誤響應沒有輸出

- 預設值： `false`
- 不接受值

### `--header`, `-H`

額外標頭

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:get`

本地克隆項目

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


```bash
get
```


### `project`

項目ID


### `directory`

要克隆到的目錄。 預設為項目標題


### `--environment`, `-e`

要克隆的環境ID。 預設為項目預設值或第一個可用環境

- 需要值

### `--depth`

建立淺克隆：限制歷史記錄中的提交數

- 需要值

### `--build`

克隆後生成項目

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:info`

讀取或設定項目的屬性

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
project:metadata
```


### `property`

屬性的名稱


### `value`

為屬性設定新值


### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:list`

獲取所有活動項目的清單

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
projects
```


```bash
pro
```

### `--pipe`

輸出項目ID的簡單清單。 禁用分頁。

- 預設值： `false`
- 不接受值

### `--host`

按區域主機名篩選（完全匹配）

- 需要值

### `--title`

按標題篩選（不區分大小寫的搜索）

- 需要值

### `--my`

僅顯示您擁有的項目

- 預設值： `false`
- 不接受值

### `--refresh`

是否刷新清單

- 預設值： `1`
- 需要值

### `--sort`

要排序的屬性

- 預設值： `title`
- 需要值

### `--reverse`

按反向（降序）順序排序

- 預設值： `false`
- 不接受值

### `--page`

頁碼。 這可啟用分頁，儘管有配置或 — count。 如果指定了 — pipe，則忽略。

- 需要值

### `--count`, `-c`

每頁要顯示的項目數。 使用0禁用分頁。 如果指定了 — page，則忽略。

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`

要顯示的列。 可用列：id*、title*、region*、createdat、endpoint、organizationid、organizationlabel、organizationname、regionlabel、status、uiurl（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:set-remote`

為當前Git儲存庫設定遠程項目

```bash
magento-cloud project:set-remote [<project>]
```


### `project`

項目ID


### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>從項目中刪除變數

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

變數名稱

- 必需

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>查看項目的變數

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<name>]
```


```bash
project-variables
```


```bash
pvget
```


```bash
project:variable:list
```


### `name`

變數的名稱


### `--pipe`

僅輸出完整變數值（必須指定&quot;name&quot;）

- 預設值： `false`
- 不接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>為項目設定變數

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
pvset
```


### `name`

變數名稱

- 必需

### `value`

變數值

- 必需

### `--json`

將值標籤為JSON

- 預設值： `false`
- 不接受值

### `--no-visible-build`

在生成時不公開此變數

- 預設值： `false`
- 不接受值

### `--no-visible-runtime`

在運行時不公開此變數

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `repo:cat`

在項目儲存庫中讀取檔案

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

檔案的路徑

- 必需

### `--commit`, `-c`

提交SHA。 這也可以接受「HEAD」和父提交的插入符號(^)或顎化符(~)尾碼。

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `repo:ls`

列出項目儲存庫中的檔案

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

子目錄的路徑


### `--directories`, `-d`

僅顯示目錄

- 預設值： `false`
- 不接受值

### `--files`, `-f`

僅顯示檔案

- 預設值： `false`
- 不接受值

### `--git-style`

類似於&quot;git ls-tree&quot;的樣式輸出

- 預設值： `false`
- 不接受值

### `--commit`, `-c`

提交SHA。 這也可以接受「HEAD」和父提交的插入符號(^)或顎化符(~)尾碼。

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `repo:read`

讀取項目儲存庫中的目錄或檔案

```bash
magento-cloud read [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


```bash
read
```


### `path`

目錄或檔案的路徑


### `--commit`, `-c`

提交SHA。 這也可以接受「HEAD」和父提交的插入符號(^)或顎化符(~)尾碼。

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `route:get`

查看有關路由的詳細資訊

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

路由的原始URL


### `--id`

要選擇的路由ID

- 需要值

### `--primary`, `-1`

選擇主工藝路線

- 預設值： `false`
- 不接受值

### `--property`, `-P`

要顯示的屬性

- 需要值

### `--refresh`

繞過路由快取

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

[已棄用選項，不再使用]

- 需要值

### `--identity-file`, `-i`

[已棄用選項，不再使用]

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `route:list`

列出環境的所有路由

```bash
magento-cloud routes [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


```bash
routes
```


```bash
environment:routes
```


### `environment`

環境ID


### `--refresh`

繞過路由快取

- 預設值： `false`
- 不接受值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：route*、type*、to*、url（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `self:install`

安裝或更新CLI配置檔案

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```


```bash
local:install
```

### `--shell-type`

用於自動完成的shell類型（bash或zsh）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `self:stats`

查看GitHub包下載的統計資訊

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--page`, `-p`

頁碼

- 預設值： `1`
- 需要值

### `--count`, `-c`

每頁結果(最大值：100)

- 預設值： `20`
- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`

要顯示的列。 可用列：資產、日期、下載、發佈。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `self:update`

將CLI更新為最新版本

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```


```bash
self-update
```


```bash
update
```

### `--no-major`

僅在次要版本或修補程式版本之間更新

- 預設值： `false`
- 不接受值

### `--unstable`

更新到新的不穩定版本（如果可用）

- 預設值： `false`
- 不接受值

### `--manifest`

覆蓋清單檔案位置

- 需要值

### `--current-version`

覆蓋當前版本

- 需要值

### `--timeout`

版本檢查超時

- 預設值： `30`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `service:list`

列出項目中的服務

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
services
```

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：磁碟、名稱、大小、類型。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `service:mongo:dump`

從MongoDB建立資料的二進位存檔轉儲

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongodump
```

### `--collection`, `-c`

要轉儲的集合

- 需要值

### `--gzip`, `-z`

使用gzip壓縮轉儲

- 預設值： `false`
- 不接受值

### `--stdout`, `-o`

輸出到STDOUT而不是檔案

- 預設值： `false`
- 不接受值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `service:mongo:export`

從MongoDB導出資料

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongoexport
```

### `--collection`, `-c`

要導出的集合

- 需要值

### `--jsonArray`

將資料導出為單個JSON陣列

- 預設值： `false`
- 不接受值

### `--type`

導出類型，如&quot;csv&quot;

- 需要值

### `--fields`, `-f`

要導出的欄位

- 預設值： `[]`
- 需要值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `service:mongo:restore`

將資料的二進位存檔轉儲還原到MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongorestore
```

### `--collection`, `-c`

要還原的集合

- 需要值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `service:mongo:shell`

使用MongoDB shell

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongo
```

### `--eval`

將JavaScript片段傳遞到shell

- 需要值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `service:redis-cli`

訪問Redis CLI

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```


```bash
redis
```


### `args`

要添加到Redis命令的參數


### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ β ]&lt;/>在會話之間切換

```bash
magento-cloud session:switch [<id>]
```


### `id`

新會話ID


### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `snapshot:create`

建立環境快照

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
backup
```


```bash
backup:create
```


```bash
environment:backup
```


### `environment`

環境


### `--live`

即時備份：不要阻止環境。 如果設定，則會使環境處於運行狀態，並在備份期間開啟連接。 這樣可減少停機時間，並有可能以不一致的狀態備份資料。

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--unsafe`

棄用選項：使用 — 實際

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `snapshot:list`

列出環境的可用快照

```bash
magento-cloud snapshots [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
snapshots
```


```bash
backups
```


```bash
backup:list
```

### `--limit`

[已棄用]  — 此選項未使用

- 需要值

### `--start`

[已棄用]  — 此選項未使用

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `snapshot:restore`

恢復環境快照

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


```bash
environment:restore
```


```bash
backup:restore
```


### `snapshot`

快照的名稱。 預設至最近一次


### `--target`

要恢復的環境。 預設為快照的當前環境

- 需要值

### `--branch-from`

如果 — target尚不存在，則指定新環境的父環境

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ β ]&lt;/>運行源操作

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```


### `operation`

操作名稱

- 必需

### `--variable`

在操作期間設定的變數，格式為 &lt;info>類型：名稱=值&lt;/info>

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `ssh-cert:info`

顯示有關當前SSH證書的資訊

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

### `--no-refresh`

如果證書無效，則不刷新它

- 預設值： `false`
- 不接受值

### `--property`, `-P`

要顯示的證書屬性

- 需要值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `ssh-cert:load`

生成SSH證書

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

### `--refresh-only`

如有必要，僅刷新證書（不寫入SSH配置）

- 預設值： `false`
- 不接受值

### `--new`

強制刷新證書

- 預設值： `false`
- 不接受值

### `--new-key`

[已棄用] 使用 — 改為新建

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `ssh-key:add`

添加新SSH密鑰

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```


### `path`

現有SSH公鑰的路徑


### `--name`

用於標識密鑰的名稱

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `ssh-key:delete`

刪除SSH密鑰

```bash
magento-cloud ssh-key:delete [<id>]
```


### `id`

要刪除的SSH密鑰的ID


### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `ssh-key:list`

獲取帳戶中的SSH密鑰清單

```bash
magento-cloud ssh-keys [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
ssh-keys
```

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：id*、title*、path*、指紋（* =預設列）。 字元「+」可用作預設列的佔位符。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `subscription:info`

讀取或修改訂閱屬性

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<property>] [<value>]
```


### `property`

屬性的名稱


### `value`

為屬性設定新值


### `--id`, `-s`

訂閱ID

- 需要值

### `--date-fmt`

日期格式（作為PHP日期格式字串）

- 預設值： `c`
- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `tunnel:close`

關閉SSH隧道

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

關閉所有隧道

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `tunnel:info`

查看SSH隧道的關係資訊

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

### `--property`, `-P`

要查看的關係屬性

- 需要值

### `--encode`, `-c`

輸出為base64編碼的JSON

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `tunnel:list`

列出SSH隧道

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
tunnels
```

### `--all`, `-a`

查看所有隧道

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `tunnel:open`

開啟SSH隧道以訪問應用的關係

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

允許遠程主機連接到本地轉發埠

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `tunnel:single`

開啟到應用關係的單個SSH通道

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

### `--port`

本地埠

- 需要值

### `--gateway-ports`, `-g`

允許遠程主機連接到本地轉發埠

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--app`, `-A`

遠程應用程式名稱

- 需要值

### `--relationship`, `-r`

要使用的服務關係

- 需要值

### `--identity-file`, `-i`

要使用的SSH標識（私鑰）

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `user:add`

向項目添加用戶

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

用戶的電子郵件地址


### `--role`, `-r`

用戶的項目角色（「admin」或「viewer」）或環境類型角色(如「staging:contributor」或「production:viewer」)。 要從環境類型中刪除用戶，請將角色設定為「無」。 %字元可用作環境類型的通配符，例如「%:viewer」為用戶提供所有類型的「viewer」角色。 角色可以縮寫，如「生產：v」。

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `user:delete`

從項目中刪除用戶

```bash
magento-cloud user:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

用戶的電子郵件地址

- 必需

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `user:get`

查看用戶的角色

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


```bash
user:role
```


### `email`

用戶的電子郵件地址


### `--level`, `-l`

角色級別（「project」或「environment」）

- 需要值

### `--pipe`

將角色輸出到stdout（進行任何更改後）

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--role`, `-r`

[已棄用：使用用戶：更新以更改用戶的角色]

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `user:list`

列出項目用戶

```bash
magento-cloud users [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
users
```

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：電子郵件、ID、名稱、角色。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `user:update`

更新項目上的用戶角色

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

用戶的電子郵件地址


### `--role`, `-r`

用戶的項目角色（「admin」或「viewer」）或環境類型角色(如「staging:contributor」或「production:viewer」)。 要從環境類型中刪除用戶，請將角色設定為「無」。 %字元可用作環境類型的通配符，例如「%:viewer」為用戶提供所有類型的「viewer」角色。 角色可以縮寫，如「生產：v」。

- 預設值： `[]`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:create`

建立變數

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

變數名稱


### `--level`, `-l`

設定變數（「project」或「environment」）的級別

- 需要值

### `--name`

變數名稱

- 需要值

### `--value`

變數的值

- 需要值

### `--json`

變數是否為JSON格式

- 預設值： `false`
- 需要值

### `--sensitive`

變數是否敏感

- 預設值： `false`
- 需要值

### `--prefix`

變數名稱的前置詞(例如&#39;none&#39;或&#39;env:&#39;)

- 預設值： `none`
- 需要值

### `--enabled`

是否應啟用變數

- 預設值： `true`
- 需要值

### `--inheritable`

變數是否可由子環境繼承

- 預設值： `true`
- 需要值

### `--visible-build`

變數是否應在生成時可見

- 需要值

### `--visible-runtime`

變數是否應在運行時可見

- 預設值： `true`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:delete`

刪除變數

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

變數名稱

- 必需

### `--level`, `-l`

變數級（「project」、「environment」、「p」或「e」）

- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>禁用已啟用的環境級變數

```bash
magento-cloud variable:disable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

變數的名稱

- 必需

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>啟用禁用的環境級變數

```bash
magento-cloud variable:enable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

變數的名稱

- 必需

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:get`

查看變數

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```


```bash
vget
```


### `name`

變數的名稱


### `--property`, `-P`

查看單個變數屬性

- 需要值

### `--level`, `-l`

變數級（「project」、「environment」、「p」或「e」）

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--pipe`

[棄用選項] 僅輸出變數值

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:list`

列出變數

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
variables
```


```bash
var
```

### `--level`, `-l`

變數級（「project」、「environment」、「p」或「e」）

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：is_enabled 、級別、名稱、值。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>為環境設定變數

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
vset
```


### `name`

變數名稱

- 必需

### `value`

變數值

- 必需

### `--json`

將值標籤為JSON

- 預設值： `false`
- 不接受值

### `--disabled`

將變數標籤為禁用

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `variable:update`

更新變數

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

變數名稱

- 必需

### `--level`, `-l`

變數級（「project」、「environment」、「p」或「e」）

- 需要值

### `--value`

變數的值

- 需要值

### `--json`

變數是否為JSON格式

- 預設值： `false`
- 需要值

### `--sensitive`

變數是否敏感

- 預設值： `false`
- 需要值

### `--enabled`

是否應啟用變數

- 預設值： `true`
- 需要值

### `--inheritable`

變數是否可由子環境繼承

- 預設值： `true`
- 需要值

### `--visible-build`

變數是否應在生成時可見

- 需要值

### `--visible-runtime`

變數是否應在運行時可見

- 預設值： `true`
- 需要值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--no-wait`, `-W`

不要等待操作完成

- 預設值： `false`
- 不接受值

### `--wait`

等待操作完成（預設）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `version:list`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 阿爾法 ]&lt;/>列出環境版本

```bash
magento-cloud versions [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
versions
```

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值


## `worker:list`

獲取所有已部署工作人員的清單

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
workers
```

### `--refresh`

是否刷新快取

- 預設值： `false`
- 不接受值

### `--project`, `-p`

項目ID或URL

- 需要值

### `--host`

已棄用選項，不再使用

- 需要值

### `--environment`, `-e`

環境ID

- 需要值

### `--format`

輸出格式：表、csv、tsv或純

- 預設值： `table`
- 需要值

### `--columns`, `-c`

要顯示的列。 可用列：命令、名稱、類型。 如果清單是作為單個值給出(例如，&quot;a,b,c&quot;)將用逗號和/或空格分隔。

- 預設值： `[]`
- 需要值

### `--no-header`

不輸出表標題

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示此幫助消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--yes`, `-y`

對確認問題回答「是」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--no-interaction`

不要問任何互動問題；接受預設值。 等效於使用環境變數： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- 預設值： `false`
- 不接受值

### `--ansi`

強制ANSI輸出

- 預設值： `false`
- 不接受值

### `--no-ansi`

禁用ANSI輸出

- 預設值： `false`
- 不接受值

### `--no`, `-n`

對確認問題回答「否」；接受其他問題的預設值；禁用交互

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值
