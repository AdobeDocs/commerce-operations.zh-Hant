---
source-git-commit: a5777f437430bc48b87aaea65c0e101d4ecd6574
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# magento-cloud(Adobe Commerce on cloud infrastructure)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**:1.38.1 <!-- app.version -->

此參考包含127個命令，可透過 `magento-cloud` 命令列工具。
初始清單會使用 `magento-cloud list` 命令。

>[!NOTE]
>
>此引用從應用程式碼庫中生成。 若要變更內容，您可以在 [基底](https://github.com/magento) 存放庫，並提交變更以供審核。 另一種方式是 _給我們反饋_ （尋找右上方的連結）。 如需貢獻准則，請參閱 [代碼貢獻](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BASH完成掛接。

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



生成設定此應用程式完成的BASH代碼。
- 預設值： `false`
- 不接受值



### `--program`, `-p`



應觸發完成的程式名 &lt;comment>（預設為絕對應用程式路徑）&lt;/comment>.
- 需要值



### `--multiple`, `-m`



生成的掛鈎可用於多個應用程式。
- 預設值： `false`
- 不接受值


### `--shell-type`

設定殼類型（zsh或bash）。 否則會自動確定。
- 接受值 <!-- options --> <!-- options.size -->

## `bot`

Magento雲端機器人

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `clear-cache`

清除CLI快取

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `decode`

將編碼字串(如MAGENTO_CLOUD_VARIABLES)解碼

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

要解碼的變數值
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要在變數中檢視的屬性
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `docs`

開啟線上檔案

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

搜尋詞

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

用來開啟URL的瀏覽器。 將0設定為無。
- 需要值


### `--pipe`

輸出要結束的URL。
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `help`

顯示命令的幫助

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

命令名稱
- 預設值： `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `legacy-migrate`

從舊版檔案結構移轉

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

請勿建立專案的備份。
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `list`

列出命令

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

命名空間名稱
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

要輸出原始命令清單
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（txt、xml、json或md）
- 預設值： `txt`
- 需要值 <!-- options --> <!-- options.size -->

## `multi`

在多個專案上執行命令

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

要執行的命令
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



專案ID清單，以逗號和/或空格分隔
- 需要值


### `--continue`

即使遇到異常，仍繼續運行命令
- 預設值： `false`
- 不接受值


### `--sort`

用來排序項目選項清單的屬性
- 預設值： `title`
- 需要值


### `--reverse`

反轉項目選項的順序
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `web`

開啟Web UI

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

用來開啟URL的瀏覽器。 將0設定為無。
- 需要值


### `--pipe`

輸出要結束的URL。
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `welcome`

歡迎使用Magento雲

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `activity:cancel`

取消活動

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

活動ID。 預設為最近的可取消活動。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

依類型篩選（選取預設活動時）
- 需要值



### `--all`, `-a`



檢查所有環境上的最近活動（選取預設活動時）
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `activity:get`

檢視單一活動的詳細資訊

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

活動ID。 預設為最近的活動。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要檢視的屬性
- 需要值


### `--type`

依類型篩選（選取預設活動時）
- 需要值


### `--state`

依狀態篩選（選取預設活動時）:in_progress、待定、完成或取消
- 預設值： `[]`
- 需要值


### `--result`

依結果篩選（選取預設活動時）:成功或失敗
- 需要值



### `--incomplete`, `-i`



僅包含未完成的活動（選取預設活動時）。 這是 &lt;info>—state=in_progress,pending&lt;/info>
- 預設值： `false`
- 不接受值



### `--all`, `-a`



檢查所有環境上的最近活動（選取預設活動時）
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `activity:list`

取得環境或專案的活動清單

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

依類型篩選活動
- 需要值


### `--limit`

限制顯示的結果數
- 預設值： `10`
- 需要值


### `--start`

僅列出此日期前建立的活動
- 需要值


### `--state`

依州篩選活動：in_progress、待定、完成或取消
- 預設值： `[]`
- 需要值


### `--result`

依結果篩選活動：成功或失敗
- 需要值



### `--incomplete`, `-i`



僅列出未完成的活動
- 預設值： `false`
- 不接受值



### `--all`, `-a`



列出所有環境上的活動
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `activity:log`

顯示活動的記錄

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

活動ID。 預設為最近的活動。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

活動刷新間隔（秒）。 設為0可禁用刷新。
- 預設值： `3`
- 需要值



### `--timestamps`, `-t`



在每則訊息旁顯示時間戳記
- 預設值： `false`
- 不接受值


### `--type`

依類型篩選（選取預設活動時）
- 需要值


### `--state`

依狀態篩選（選取預設活動時）:in_progress、待定、完成或取消
- 預設值： `[]`
- 需要值


### `--result`

依結果篩選（選取預設活動時）:成功或失敗
- 需要值



### `--incomplete`, `-i`



僅包含未完成的活動（選取預設活動時）。 這是 &lt;info>—state=in_progress,pending&lt;/info>
- 預設值： `false`
- 不接受值



### `--all`, `-a`



檢查所有環境上的最近活動（選取預設活動時）
- 預設值： `false`
- 不接受值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `api:curl`

在Magento雲端API上執行已驗證的cURL要求

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API路徑
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



要使用的要求方法
- 需要值



### `--data`, `-d`



要傳送的資料
- 需要值



### `--include`, `-i`



在輸出中包含標題
- 預設值： `false`
- 不接受值



### `--head`, `-I`



僅擷取標題
- 預設值： `false`
- 不接受值


### `--disable-compression`

請勿使用curl — 壓縮的標幟
- 預設值： `false`
- 不接受值


### `--enable-glob`

啟用curl全域（移除 — globoff標幟）
- 預設值： `false`
- 不接受值



### `--header`, `-H`



額外標題
- 預設值： `[]`
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:config-get`

檢視應用程式的設定

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



要檢視的設定屬性
- 需要值


### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:list`

列出專案中的應用程式

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `auth:api-token-login`

使用API代號登入Magento雲端

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `auth:browser-login`

透過瀏覽器登入Magento雲端

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



重新登入，即使已登入
- 預設值： `false`
- 不接受值


### `--browser`

用來開啟URL的瀏覽器。 將0設定為無。
- 需要值


### `--pipe`

輸出要結束的URL。
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `auth:info`

顯示您的帳戶資訊

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

要檢視的帳戶屬性
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要檢視的帳戶屬性（替代語法）
- 需要值


### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `auth:logout`

登出Magento雲

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>使用使用者名稱和密碼登入Magento雲端

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `auth:token`

取得OAuth 2存取權杖，以要求MagentoCloud API

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `blackfire:setup`

設定專案的Blackfire.io整合

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

伺服器ID
- 需要值


### `--server_token`

伺服器Token
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `certificate:add`

新增SSL憑證至專案

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

憑證檔案的路徑
- 需要值


### `--key`

證書私鑰檔案的路徑
- 需要值


### `--chain`

證書鏈檔案的路徑
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `certificate:delete`

從專案刪除憑證

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

憑證ID（或開頭）
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `certificate:get`

檢視憑證

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

憑證ID（或開頭）
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要檢視的憑證屬性
- 需要值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `certificate:list`

列出項目證書

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

依網域名稱篩選（不區分大小寫的搜尋）
- 需要值


### `--exclude-domain`

排除憑證，依網域名稱進行比對（不區分大小寫的搜尋）
- 需要值


### `--issuer`

依核發者篩選
- 需要值


### `--only-auto`

僅顯示自動布建的憑證
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

僅返回證書涵蓋的域名清單
- 預設值： `false`
- 不接受值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `commit:get`

顯示提交詳細資訊

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

提交SHA。 這也可以接受「HEAD」，並接受父項提交的脫字元號(^)或顎化符號(~)尾碼。
- 預設值： `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要顯示的提交屬性。
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `commit:list`

清單提交

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

起始Git提交SHA。 這也可以接受「HEAD」，並接受父項提交的脫字元號(^)或顎化符號(~)尾碼。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

要顯示的提交數。
- 預設值： `10`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `db:dump`

建立遠程資料庫的本地轉儲

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

要轉儲的架構。 忽略以使用預設架構（通常為「main」）。
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



向轉儲檔案名添加時間戳
- 預設值： `false`
- 不接受值



### `--stdout`, `-o`



輸出為STDOUT，而非檔案
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



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `db:size`

估計資料庫的磁碟使用情況

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



以位元組顯示大小。
- 預設值： `false`
- 不接受值



### `--cleanup`, `-C`



檢查表是否可以清理並顯示建議（僅限InnoDb）。
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `db:sql`

在遠程資料庫上運行SQL

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

要執行的SQL陳述式
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

生成原始、非表格輸出
- 預設值： `false`
- 不接受值


### `--schema`

要使用的結構。 忽略以使用預設架構（通常為「main」）。 傳遞空白字串以不使用任何架構。
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `domain:add`

新增網域至專案

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

域名
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

此域的證書檔案路徑
- 需要值


### `--key`

提供之憑證的私密金鑰檔案路徑。
- 需要值


### `--chain`

證書鏈檔案或提供證書的檔案的路徑
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `domain:delete`

從專案刪除網域

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

域名
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `domain:get`

顯示域的詳細資訊

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

域名
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要查看的域屬性
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `domain:list`

取得所有網域的清單

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `domain:update`

更新域

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

域名
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

此域的證書檔案路徑
- 需要值


### `--key`

提供之憑證的私密金鑰檔案路徑。
- 需要值


### `--chain`

證書鏈檔案或提供證書的檔案的路徑
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:activate`

啟動環境

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

要啟用的環境

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

在啟動前設定新環境父級
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:branch`

分支環境

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

新環境的ID（分支名稱）
<!-- argument -->

### `parent`

新環境的父環境
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

新環境的標題
- 需要值


### `--force`

建立新環境，即使無法在本地簽出分支
- 預設值： `false`
- 不接受值


### `--no-clone-parent`

不克隆父分支的資料
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
- 預設值： `false`
- 不接受值


### `--wait`

等待操作完成（預設）
- 預設值： `false`
- 不接受值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:checkout`

查看環境

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

要結帳的環境ID。 例如：&quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:delete`

刪除環境

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

要刪除的環境

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

也刪除遠端Git分支
- 預設值： `false`
- 不接受值


### `--no-delete-branch`

請勿刪除遠端Git分支
- 預設值： `false`
- 不接受值


### `--inactive`

刪除所有非作用中環境
- 預設值： `false`
- 不接受值


### `--merged`

刪除所有合併的環境
- 預設值： `false`
- 不接受值


### `--exclude`

不要刪除的環境
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:http-access`

更新環境的HTTP存取設定

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

存取限制的格式為「permission:address」。 使用0清除所有地址。
- 預設值： `[]`
- 需要值


### `--auth`

HTTP基本驗證憑證，格式為「username:password」。 使用0清除所有憑據。
- 預設值： `[]`
- 需要值


### `--enabled`

是否應啟用訪問控制：1要啟用，0要禁用
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:info`

讀取或設定環境的屬性

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

屬性的名稱
<!-- argument -->

### `value`

為屬性設定新值
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:init`

從公用Git存放庫初始化環境

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

Git存放庫的URL
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

設定檔的名稱
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:list`

取得環境清單

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




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

以反向（遞減）順序排序
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:logs`

讀取環境的日誌

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

記錄類型，例如&quot;access&quot;或&quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

要顯示的行數
- 預設值： `100`
- 需要值


### `--tail`

不斷跟蹤日誌
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:merge`

合併環境

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

要合併的環境
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:push`

推送程式碼至環境

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

來源參考：分支名稱或提交哈希
- 預設值： `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

目標分支名稱
- 需要值



### `--force`, `-f`



允許非快速轉發更新
- 預設值： `false`
- 不接受值


### `--force-with-lease`

如果遠端追蹤分支為最新狀態，則允許非快進更新
- 預設值： `false`
- 不接受值



### `--set-upstream`, `-u`



將目標環境設定為來源分支的上游
- 預設值： `false`
- 不接受值


### `--activate`

推送前啟動環境
- 預設值： `false`
- 不接受值


### `--branch`

已棄用：別名：激活
- 預設值： `false`
- 不接受值


### `--parent`

設定新環境父項（僅與 — activate或 — branch一起使用）
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
- 預設值： `false`
- 不接受值


### `--wait`

等待操作完成（預設）
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:redeploy`

重新部署環境

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:relationships`

顯示環境的關係

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要查看的關係屬性
- 需要值


### `--refresh`

是否刷新關係
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--app`, `-A`



遠程應用程式名稱
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:scp`

使用scp將檔案複製到當前環境並從當前環境複製

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

要複製的檔案。 使用遠程：前置詞來定義遠端位置。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



遞歸複製整個目錄
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:set-remote`

設定遠程環境以映射到分支

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境電腦名稱。 設定為0可刪除分支的映射
- 必填

   <!-- argument -->

### `branch`

要對應的Git分支（預設為目前分支）
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:ssh`

SSH到當前環境

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

要在環境中運行的命令。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

僅輸出SSH URL。
- 預設值： `false`
- 不接受值


### `--all`

輸出所有SSH URL（適用於每個應用程式）。
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:synchronize`

從環境的父代同步環境的代碼和/或資料

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

要同步的內容：&quot;code&quot;、&quot;data&quot;或兩者

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

借由基於來同步程式碼，而非合併
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:url`

取得環境的公用URL

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



僅返回主路由的URL
- 預設值： `false`
- 不接受值


### `--browser`

用來開啟URL的瀏覽器。 將0設定為無。
- 需要值


### `--pipe`

輸出要結束的URL。
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `environment:xdebug`

在環境上開啟Xdebug的通道

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

本地埠
- 預設值： `9000`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:activity:get`

檢視單一整合活動的詳細資訊

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

整合ID。 保留空白以從清單中選擇。
<!-- argument -->

### `activity`

活動ID。 預設為最新的整合活動。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要檢視的屬性
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



[已棄用選項，未使用]
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:activity:list`

取得整合的活動清單

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

整合ID。 保留空白以從清單中選擇。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

依類型篩選活動
- 需要值


### `--limit`

限制顯示的結果數
- 預設值： `10`
- 需要值


### `--start`

僅列出此日期前建立的活動
- 需要值


### `--state`

依州篩選活動
- 預設值： `[]`
- 需要值


### `--result`

依結果篩選活動
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



[已棄用選項，未使用]
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:activity:log`

顯示整合活動的記錄

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

整合ID。 保留空白以從清單中選擇。
<!-- argument -->

### `activity`

活動ID。 預設為最新的整合活動。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



在每則訊息旁顯示時間戳記
- 預設值： `false`
- 不接受值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



[已棄用選項，未使用]
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:add`

新增整合至專案

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

整合類型(「bitbucket」、「bitbucket_server」、「github」、「gitlab」、「hipchat」、「webhook」、「health.email」、「health.pagerdusty」、「health.slack」、「health.webhook」、「script」)
- 需要值


### `--base-url`

伺服器安裝的基礎URL
- 需要值


### `--username`

位元貯體伺服器使用者名稱
- 需要值


### `--token`

整合的存取權杖
- 需要值


### `--key`

Bitbucket OAuth使用者金鑰
- 需要值


### `--secret`

Bitbucket OAuth使用者密碼
- 需要值


### `--server-project`

專案(例如&#39;namespace/repo&#39;)
- 需要值


### `--repository`

要追蹤的存放庫(例如&#39;owner/repository&#39;)
- 需要值


### `--build-merge-requests`

GitLab:將合併請求建置為環境
- 預設值： `true`
- 需要值


### `--build-pull-requests`

將每個提取請求建置為環境
- 預設值： `true`
- 需要值


### `--build-draft-pull-requests`

建立草稿提取請求
- 預設值： `true`
- 需要值


### `--build-pull-requests-post-merge`

根據其合併後狀態建立提取請求
- 預設值： `false`
- 需要值


### `--build-wip-merge-requests`

GitLab:建置WIP合併請求
- 預設值： `true`
- 需要值


### `--merge-requests-clone-parent-data`

GitLab:合併請求的原地資料
- 預設值： `true`
- 需要值


### `--pull-requests-clone-parent-data`

原地複製上層環境的資料以請求提取
- 預設值： `true`
- 需要值


### `--resync-pull-requests`

在每個組建中重新同步提取請求環境資料
- 預設值： `false`
- 需要值


### `--fetch-branches`

從遠端擷取所有分支（作為非作用中環境）
- 預設值： `true`
- 需要值


### `--prune-branches`

刪除遠端上不存在的分支
- 預設值： `true`
- 需要值


### `--room`

HipChat室ID
- 需要值


### `--url`

Webhook:接收JSON資料的URL
- 需要值


### `--shared-key`

Webhook:JWS共用密鑰
- 需要值


### `--file`

包含要上傳指令碼的本機檔案名稱
- 需要值


### `--events`

要採取動作的事件清單，例如environment.push
- 預設值： `*`
- 需要值


### `--states`

要採取行動的國家清單，例如待定、in_progress、complete
- 預設值： `complete`
- 需要值


### `--environments`

要包含的環境ID
- 預設值： `*`
- 需要值


### `--excluded-environments`

要排除的環境ID
- 預設值： `[]`
- 需要值


### `--from-address`

[可選] 警報電子郵件的自訂寄件者地址
- 需要值


### `--recipients`

收件者電子郵件地址
- 預設值： `[]`
- 需要值


### `--channel`

Slack管道
- 需要值


### `--routing-key`

PagerDuty路由密鑰
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:delete`

從專案刪除整合

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

整合ID。 保留空白以從清單中選擇。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:get`

檢視整合的詳細資訊

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

整合ID。 保留空白以從清單中選擇。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



要檢視的整合屬性
- 接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:list`

檢視專案整合清單

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:update`

更新整合

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

要更新之整合的ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

整合類型(「bitbucket」、「bitbucket_server」、「github」、「gitlab」、「hipchat」、「webhook」、「health.email」、「health.pagerdusty」、「health.slack」、「health.webhook」、「script」)
- 需要值


### `--base-url`

伺服器安裝的基礎URL
- 需要值


### `--username`

位元貯體伺服器使用者名稱
- 需要值


### `--token`

整合的存取權杖
- 需要值


### `--key`

Bitbucket OAuth使用者金鑰
- 需要值


### `--secret`

Bitbucket OAuth使用者密碼
- 需要值


### `--server-project`

專案(例如&#39;namespace/repo&#39;)
- 需要值


### `--repository`

要追蹤的存放庫(例如&#39;owner/repository&#39;)
- 需要值


### `--build-merge-requests`

GitLab:將合併請求建置為環境
- 預設值： `true`
- 需要值


### `--build-pull-requests`

將每個提取請求建置為環境
- 預設值： `true`
- 需要值


### `--build-draft-pull-requests`

建立草稿提取請求
- 預設值： `true`
- 需要值


### `--build-pull-requests-post-merge`

根據其合併後狀態建立提取請求
- 預設值： `false`
- 需要值


### `--build-wip-merge-requests`

GitLab:建置WIP合併請求
- 預設值： `true`
- 需要值


### `--merge-requests-clone-parent-data`

GitLab:合併請求的原地資料
- 預設值： `true`
- 需要值


### `--pull-requests-clone-parent-data`

原地複製上層環境的資料以請求提取
- 預設值： `true`
- 需要值


### `--resync-pull-requests`

在每個組建中重新同步提取請求環境資料
- 預設值： `false`
- 需要值


### `--fetch-branches`

從遠端擷取所有分支（作為非作用中環境）
- 預設值： `true`
- 需要值


### `--prune-branches`

刪除遠端上不存在的分支
- 預設值： `true`
- 需要值


### `--room`

HipChat室ID
- 需要值


### `--url`

Webhook:接收JSON資料的URL
- 需要值


### `--shared-key`

Webhook:JWS共用密鑰
- 需要值


### `--file`

包含要上傳指令碼的本機檔案名稱
- 需要值


### `--events`

要採取動作的事件清單，例如environment.push
- 預設值： `*`
- 需要值


### `--states`

要採取行動的國家清單，例如待定、in_progress、complete
- 預設值： `complete`
- 需要值


### `--environments`

要包含的環境ID
- 預設值： `*`
- 需要值


### `--excluded-environments`

要排除的環境ID
- 預設值： `[]`
- 需要值


### `--from-address`

[可選] 警報電子郵件的自訂寄件者地址
- 需要值


### `--recipients`

收件者電子郵件地址
- 預設值： `[]`
- 需要值


### `--channel`

Slack管道
- 需要值


### `--routing-key`

PagerDuty路由密鑰
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `integration:validate`

驗證現有整合

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

整合ID。 保留空白以從清單中選擇。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `local:build`

在本機建立目前的專案

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

指定要構建的應用程式

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



使用絕對連結
- 預設值： `false`
- 不接受值



### `--source`, `-s`



源目錄。 預設為當前項目根。
- 需要值



### `--destination`, `-d`



每個應用程式的網頁根將符號連結至的目的地。 預設值：_www
- 需要值



### `--copy`, `-c`



複製到組建目錄，而不是從來源進行符號連結
- 預設值： `false`
- 不接受值


### `--clone`

使用Git將目前的HEAD複製至組建目錄
- 預設值： `false`
- 不接受值


### `--run-deploy-hooks`

運行deploy和/或post_deploy掛接
- 預設值： `false`
- 不接受值


### `--no-clean`

請勿移除舊組建
- 預設值： `false`
- 不接受值


### `--no-archive`

請勿建立或使用組建封存
- 預設值： `false`
- 不接受值


### `--no-backup`

不備份以前的版本編號
- 預設值： `false`
- 不接受值


### `--no-cache`

停用快取
- 預設值： `false`
- 不接受值


### `--no-build-hooks`

不運行構建後掛接
- 預設值： `false`
- 不接受值


### `--no-deps`

請勿在本機安裝組建相依性
- 預設值： `false`
- 不接受值


### `--working-copy`

德魯什：使用git複製每個Drupal模組的存放庫，而非直接下載版本
- 預設值： `false`
- 不接受值


### `--concurrency`

德魯什：設定同時處理的同時執行專案數量
- 預設值： `4`
- 需要值


### `--lock`

德魯什：建立或更新鎖定檔案（僅適用於Drush 7+版）
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `local:clean`

移除舊專案組建

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

要保留的組建數量上限
- 預設值： `5`
- 需要值


### `--max-age`

組建的最大年齡（以秒為單位）。 若未設定，則忽略。
- 需要值


### `--include-active`

也刪除活動的版本編號
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `local:dir`

查找本地項目根

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

要查找的子目錄（「local」、「web」或「shared」）
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `mount:download`

使用rsync從裝載下載檔案

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



從所有裝載下載
- 預設值： `false`
- 不接受值



### `--mount`, `-m`



裝載（作為應用程式相對路徑）
- 需要值


### `--target`

要下載檔案的目錄。 如果 — 全部被使用，則會附加裝載路徑
- 需要值


### `--source-path`

使用裝載的源路徑（而不是裝載路徑）作為目標的子目錄，當時 — all被使用
- 預設值： `false`
- 不接受值


### `--delete`

是否刪除目標目錄中無關的檔案
- 預設值： `false`
- 不接受值


### `--exclude`

要從下載中排除的檔案（模式）
- 預設值： `[]`
- 需要值


### `--include`

要包含在下載中的檔案（模式）
- 預設值： `[]`
- 需要值


### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `mount:list`

獲取裝載清單

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

僅輸出裝載路徑（每行一條）
- 預設值： `false`
- 不接受值


### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `mount:size`

檢查裝載的磁碟使用情況

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



以位元組顯示大小
- 預設值： `false`
- 不接受值


### `--refresh`

重新整理快取
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `mount:upload`

使用rsync將檔案上載到裝載

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

包含要上載的檔案的目錄
- 需要值



### `--mount`, `-m`



裝載（作為應用程式相對路徑）
- 需要值


### `--delete`

是否刪除裝入中無關的檔案
- 預設值： `false`
- 不接受值


### `--exclude`

要從上傳中排除的檔案（模式）
- 預設值： `[]`
- 需要值


### `--include`

要包含在上傳中的檔案（模式）
- 預設值： `[]`
- 需要值


### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

清除專案的組建快取

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:curl`

對專案API執行已驗證的cURL要求

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API路徑
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



要使用的要求方法
- 需要值



### `--data`, `-d`



要傳送的資料
- 需要值



### `--include`, `-i`



在輸出中包含標題
- 預設值： `false`
- 不接受值



### `--head`, `-I`



僅擷取標題
- 預設值： `false`
- 不接受值


### `--disable-compression`

請勿使用curl — 壓縮的標幟
- 預設值： `false`
- 不接受值


### `--enable-glob`

啟用curl全域（移除 — globoff標幟）
- 預設值： `false`
- 不接受值



### `--header`, `-H`



額外標題
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:get`

在本機複製專案

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

專案ID
<!-- argument -->

### `directory`

要克隆到的目錄。 預設為專案標題
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



要複製的環境ID。 預設為專案預設值，或第一個可用環境
- 需要值


### `--depth`

建立淺層克隆：限制歷史記錄中的提交數
- 需要值


### `--build`

複製後建立專案
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:info`

讀取或設定項目的屬性

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

屬性的名稱
<!-- argument -->

### `value`

為屬性設定新值
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:list`

取得所有作用中專案的清單

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

輸出專案ID的簡單清單
- 預設值： `false`
- 不接受值


### `--host`

依地區主機名稱篩選（完全相符）
- 需要值


### `--title`

依標題篩選（不區分大小寫搜尋）
- 需要值


### `--my`

僅顯示您擁有的專案
- 預設值： `false`
- 不接受值


### `--refresh`

是否要刷新清單
- 預設值： `1`
- 需要值


### `--sort`

要排序的屬性
- 預設值： `title`
- 需要值


### `--reverse`

以反向（遞減）順序排序
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:set-remote`

為目前的Git存放庫設定遠端專案

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

專案ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>從專案刪除變數

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數名稱
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>檢視專案的變數

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數的名稱
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

僅輸出完整變數值（必須指定&quot;name&quot;）
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>設定專案的變數

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數名稱
- 必填

   <!-- argument -->

### `value`

變數值
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

將值標示為JSON
- 預設值： `false`
- 不接受值


### `--no-visible-build`

建置時請勿公開此變數
- 預設值： `false`
- 不接受值


### `--no-visible-runtime`

在執行階段不要公開此變數
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `repo:cat`

讀取項目儲存庫中的檔案

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

檔案的路徑
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



提交SHA。 這也可以接受「HEAD」，並接受父項提交的脫字元號(^)或顎化符號(~)尾碼。
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `repo:ls`

列出項目儲存庫中的檔案

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

子目錄的路徑
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



僅顯示目錄
- 預設值： `false`
- 不接受值



### `--files`, `-f`



僅顯示檔案
- 預設值： `false`
- 不接受值


### `--git-style`

類似「git ls-tree」的樣式輸出
- 預設值： `false`
- 不接受值



### `--commit`, `-c`



提交SHA。 這也可以接受「HEAD」，並接受父項提交的脫字元號(^)或顎化符號(~)尾碼。
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `route:get`

查看有關路由的詳細資訊

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

路由的原始URL
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

要選擇的路由ID
- 需要值



### `--primary`, `-1`



選擇主路由
- 預設值： `false`
- 不接受值



### `--property`, `-P`



要顯示的屬性
- 需要值


### `--refresh`

略過路由的快取
- 預設值： `false`
- 不接受值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `route:list`

列出環境的所有路由

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

略過路由的快取
- 預設值： `false`
- 不接受值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `self:install`

安裝或更新CLI配置檔案

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

自動完成的殼類型（bash或zsh）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `self:stats`

檢視GitHub套件下載的統計資料

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



頁碼
- 預設值： `1`
- 需要值



### `--count`, `-c`



每頁結果數(最大值：100)
- 預設值： `20`
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `self:update`

將CLI更新為最新版本

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

僅在次要版本或修補版本之間更新
- 預設值： `false`
- 不接受值


### `--unstable`

更新為新的不穩定版本（如果有）
- 預設值： `false`
- 不接受值


### `--manifest`

覆寫資訊清單檔案位置
- 需要值


### `--current-version`

覆寫目前版本
- 需要值


### `--timeout`

版本檢查的逾時
- 預設值： `30`
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `service:list`

列出項目中的服務

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `service:mongo:dump`

從MongoDB建立資料的二進位歸檔轉儲

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



要轉儲的集合
- 需要值



### `--gzip`, `-z`



使用gzip壓縮轉儲
- 預設值： `false`
- 不接受值



### `--stdout`, `-o`



輸出為STDOUT，而非檔案
- 預設值： `false`
- 不接受值



### `--relationship`, `-r`



要使用的服務關係
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `service:mongo:export`

從MongoDB導出資料

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



要匯出的集合
- 需要值


### `--jsonArray`

將資料匯出為單一JSON陣列
- 預設值： `false`
- 不接受值


### `--type`

匯出類型，例如&quot;csv&quot;
- 需要值



### `--fields`, `-f`



要匯出的欄位
- 預設值： `[]`
- 需要值



### `--relationship`, `-r`



要使用的服務關係
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `service:mongo:restore`

將資料的二進位歸檔轉儲還原到MongoDB中

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



要還原的集合
- 需要值



### `--relationship`, `-r`



要使用的服務關係
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `service:mongo:shell`

使用MongoDB shell

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

將JavaScript片段傳遞至殼層
- 需要值



### `--relationship`, `-r`



要使用的服務關係
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `service:redis-cli`

訪問Redis CLI

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

要添加到Redis命令的參數
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



要使用的服務關係
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 測試版 ]&lt;/>在會話之間切換

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

新工作階段ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `snapshot:create`

建立環境的快照

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

即時備份：不要停止環境。 如果設定，則環境將保持運行並在備份期間開啟到連接。 這樣可以減少停機時間，並且有可能以不一致的狀態備份資料。
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `snapshot:list`

列出環境的可用快照

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

限制要列出的快照數
- 預設值： `10`
- 需要值


### `--start`

只列出此日期之前建立的快照
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `snapshot:restore`

恢復環境快照

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

快照的名稱。 預設為最近一個
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

要還原到的環境。 預設為快照的當前環境
- 需要值


### `--branch-from`

如果 — target尚不存在，則會指定新環境的父環境
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 測試版 ]&lt;/>運行源操作

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

操作名稱
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

要在操作期間設定的變數，格式為 &lt;info>type:name=value&lt;/info>
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `ssh-cert:info`

顯示目前SSH憑證的相關資訊

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

如果證書無效，則不刷新該證書
- 預設值： `false`
- 不接受值



### `--property`, `-P`



要顯示的憑證屬性
- 需要值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `ssh-cert:load`

產生SSH憑證

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

請視需要重新整理憑證（請勿寫入SSH設定）
- 預設值： `false`
- 不接受值


### `--new`

強制刷新證書
- 預設值： `false`
- 不接受值


### `--new-key`

[已棄用] 使用 — 新
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `ssh-key:add`

新增SSH金鑰

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

現有SSH公開金鑰的路徑
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

識別金鑰的名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `ssh-key:delete`

刪除SSH金鑰

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

要刪除的SSH金鑰ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `ssh-key:list`

取得帳戶中的SSH金鑰清單

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `subscription:info`

讀取或修改訂閱屬性

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

屬性的名稱
<!-- argument -->

### `value`

為屬性設定新值
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



訂閱ID
- 需要值


### `--date-fmt`

日期格式（作為PHP日期格式字串）
- 預設值： `c`
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `tunnel:close`

關閉SSH通道

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



關閉所有隧道
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `tunnel:info`

查看SSH隧道的關係資訊

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



要查看的關係屬性
- 需要值



### `--encode`, `-c`



輸出為base64編碼JSON
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--app`, `-A`



遠程應用程式名稱
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `tunnel:list`

列出SSH隧道

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



查看所有通道
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--app`, `-A`



遠程應用程式名稱
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `tunnel:open`

開啟應用程式關係的SSH通道

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



允許遠程主機連接到本地轉發埠
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--app`, `-A`



遠程應用程式名稱
- 需要值



### `--identity-file`, `-i`



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `tunnel:single`

開啟應用程式關係的單一SSH通道

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

本地埠
- 需要值



### `--gateway-ports`, `-g`



允許遠程主機連接到本地轉發埠
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
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



要使用的SSH身分（私密金鑰）
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `user:add`

新增使用者至專案

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

使用者的電子郵件地址
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



使用者的專案角色（「管理員」或「檢視者」）或環境特定角色(例如「master:contributor」或「stage:viewer」)。 字元%可作為環境ID中的萬用字元，例如「%:viewer」。 角色可縮寫，例如&#39;master:c&#39;。
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `user:delete`

從專案刪除使用者

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

使用者的電子郵件地址
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `user:get`

檢視使用者的角色

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

使用者的電子郵件地址
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



角色層級（「專案」或「環境」）
- 需要值


### `--pipe`

輸出角色以停止（進行任何變更後）
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `user:list`

列出專案使用者

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `user:update`

更新專案上的使用者角色

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

使用者的電子郵件地址
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



使用者的專案角色（「管理員」或「檢視者」）或環境特定角色(例如「master:contributor」或「stage:viewer」)。 字元%可作為環境ID中的萬用字元，例如「%:viewer」。 角色可縮寫，例如&#39;master:c&#39;。
- 預設值： `[]`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:create`

建立變數

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數名稱
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



設定變數的層級（「專案」或「環境」）
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

變數名稱的首碼(例如&#39;none&#39;或&#39;env:&#39;)
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

變數是否應在建置時顯示
- 預設值： `true`
- 需要值


### `--visible-runtime`

變數是否應在執行階段顯示
- 預設值： `true`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:delete`

刪除變數

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數名稱
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



變數層級（「專案」、「環境」、「p」或「e」）
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>停用已啟用的環境層級變數

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數的名稱
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>啟用已禁用的環境級變數

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數的名稱
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:get`

檢視變數

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數的名稱
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



檢視單一變數屬性
- 需要值



### `--level`, `-l`



變數層級（「專案」、「環境」、「p」或「e」）
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值


### `--pipe`

[棄用的選項] 僅輸出變數值
- 預設值： `false`
- 不接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:list`

清單變數

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



變數層級（「專案」、「環境」、「p」或「e」）
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
- 預設值： `[]`
- 需要值


### `--no-header`

不輸出表標題
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已棄用 ]&lt;/>為環境設定變數

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數名稱
- 必填

   <!-- argument -->

### `value`

變數值
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

將值標示為JSON
- 預設值： `false`
- 不接受值


### `--disabled`

將變數標示為已停用
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `variable:update`

更新變數

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

變數名稱
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



變數層級（「專案」、「環境」、「p」或「e」）
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

變數是否應在建置時顯示
- 預設值： `true`
- 需要值


### `--visible-runtime`

變數是否應在執行階段顯示
- 預設值： `true`
- 需要值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值



### `--no-wait`, `-W`



請勿等待操作完成
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `worker:list`

獲取所有已部署工作的清單

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

是否刷新快取
- 預設值： `false`
- 不接受值



### `--project`, `-p`



專案ID或URL
- 需要值


### `--host`

專案的API主機名稱
- 需要值



### `--environment`, `-e`



環境ID
- 需要值


### `--format`

輸出格式（「表格」、「csv」、「tsv」或「純」）
- 預設值： `table`
- 需要值


### `--columns`

要顯示的欄（逗號分隔清單或多個值）
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



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的密集度
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
- 預設值： `false`
- 不接受值



### `--yes`, `-y`



對任何是/否的問題回答「是」；停用互動
- 預設值： `false`
- 不接受值



### `--no`, `-n`



對任何是/否的問題回答「否」；停用互動
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->