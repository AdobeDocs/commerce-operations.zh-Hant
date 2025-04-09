---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '8253'
ht-degree: 1%

---
# bin/magento (Adobe Commerce內部部署)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**版本**： 2.4.8

此參考包含145個可透過`bin/magento`命令列工具使用的命令。
初始清單是在Adobe Commerce使用`bin/magento list`命令自動產生的。

## 一般

使用[「新增CLI命令」](https://developer.adobe.com/commerce/php/development/cli-commands/)指南來新增自訂CLI命令。

您可以使用捷徑來呼叫`bin/magento` CLI命令，而不使用完整的命令名稱。 例如，您可以使用， `bin/magento s:upg`進行呼叫。`bin/magento s:up``bin/magento setup:upgrade`請參閱 [快捷方式語法](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) ，瞭解如何將快捷方式與任何 CLI 命令一起使用。

此參考文件是從應用程式原始碼生成的。 若要更改文檔，應在相關 [代碼庫](https://github.com/magento) 存放庫中打開相應命令的提取請求。 有關詳細資訊，請參閱 [Code貢獻](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) 。

### 全域選項

#### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 違約： `false`
- 不接受值

#### `--quiet`，`-q`

不要輸出任何消息

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
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
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
bin/magento completion [--debug] [--] [<shell>]
```

傾印殼層完成指令碼

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
```

### 參數

#### `shell`

如果未給出外殼類型（例如“bash”），將使用“$SHELL”env var的值

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--debug`

追蹤完成偵錯記錄

- 預設： `false`
- 不接受值


## `help`

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

顯示命令的說明

```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

清單命令

```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
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


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

停用Adobe IMS模組

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

啟用Adobe Systems IMS 模組。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--organization-id`，`-o`

設定Adobe IMS設定的組織ID 。 啟用模組時需要

- 接受值

#### `--client-id`，`-c`

設定Adobe IMS設定的使用者端ID。 啟用模組時需要

- 接受值

#### `--client-secret`，`-s`

設定Adobe IMS設定的使用者端密碼。 啟用模組時需要

- 接受值

#### `--2fa`，`-t`

檢查是否為Adobe Admin Console中的組織啟用了 2FA。 啟用模組時需要

- 接受值


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Adobe IMS模組設定資訊

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Adobe IMS模組的狀態

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

建立管理員

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--admin-user`

（必要）管理員使用者

- 需要值

#### `--admin-password`

（必要）管理員密碼

- 需要值

#### `--admin-email`

（必要）管理員電子郵件

- 需要值

#### `--admin-firstname`

（必要）管理員名字

- 需要值

#### `--admin-lastname`

（必要）管理員姓氏

- 需要值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

解除鎖定管理員帳戶

```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```

### 引數

#### `username`

要解除鎖定的管理員使用者名稱

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

建立應用程式的傾印

### 引數

#### `config-types`

以空格分隔的設定型別清單，或省略以傾印所有[範圍、主題、系統、i18n]

- 違約： `[]`
- 陣列

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `app:config:import`

```bash
bin/magento app:config:import
```

匯入共用配置文件中的數據到適當的數據儲存

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `app:config:status`

```bash
bin/magento app:config:status
```

檢查設定傳播是否需要更新

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

從Magento 1資料庫遷移存儲的卡

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--host`

主機名稱/IP。 連線埠是選用的

- 需要值

#### `--dbname`

資料庫名稱

- 需要值

#### `--username`

資料庫使用者名稱。 必須有讀取存取權

- 需要值

#### `--password`

密碼

- 需要值


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

清除快取型別

### 引數

#### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

清除付款服務商家範圍快取

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

停用快取型別

### 引數

#### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

啟用快取型別

### 引數

#### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

清除快取型別使用的快取儲存體

### 引數

#### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

檢查快取狀態

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

建立調整大小的產品影像

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--async`，`-a`

在非同步模式下調整影像大小

- 預設： `false`
- 不接受值

#### `--skip_hidden_images`

不要處理產品頁面中標籤為隱藏的影像

- 預設： `false`
- 不接受值


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

移除未使用的產品屬性。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

設定是否要強制使用者HTML內容驗證，或改為顯示警告

### 引數

#### `restrict`

y\n

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

設定敏感的設定值

### 引數

#### `path`

配置路徑，例如 群組/section/field_name


#### `value`

設定值

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--interactive`，`-i`

啟用交互模式以設置所有敏感變數

- 預設： `false`
- 不接受值

#### `--scope`

設定範圍（若未設定）請使用「預設」

- 預設： `default`
- 接受值

#### `--scope-code`

設定的範圍代碼，預設為空字串

- 預設： &quot;
- 接受值


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

變更系統組態

### 引數

#### `path`

區段/群組/欄位名稱格式的設定路徑

- 必填


#### `value`

設定值

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--scope`

設定範圍（預設、網站或商店）

- 預設： `default`
- 需要值

#### `--scope-code`

作用域代碼 （僅當 範圍 不是「預設」時才需要）

- 需要值

#### `--lock-env`，`-e`

鎖定值，防止在Admin中進行修改(將儲存於app/etc/env.php)

- 預設： `false`
- 不接受值

#### `--lock-config`，`-c`

鎖定並與其他安裝專案共用值，防止在Admin中進行修改(將儲存在app/etc/config.php中)

- 預設： `false`
- 不接受值

#### `--lock`，`-l`

已棄用，請改用 — lock-env選項。

- 預設： `false`
- 不接受值


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

顯示指定路徑的設定值。 如果未指定路徑，則會顯示所有儲存的值

### 引數

#### `path`

設定路徑，例如section_id/group_id/field_id

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--scope`

設定範圍（如果未指定），則會使用「預設」範圍

- 預設： `default`
- 接受值

#### `--scope-code`

範圍代碼（只有在範圍不是`default`時才需要）

- 預設： &quot;
- 接受值


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

產生並安裝目前使用者的crontab

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--force`，`-f`

強制安裝任務

- 預設： `false`
- 不接受值

#### `--non-optional`，`-d`

僅安裝非選擇性（預設）工作

- 預設： `false`
- 不接受值


## `cron:remove`

```bash
bin/magento cron:remove
```

從crontab移除任務

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

按計劃運行作業

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--group`

僅從指定的群組執行工作

- 需要值

#### `--exclude-group`

從指定的群組排除工作

- 預設： `[]`
- 接受多個值

#### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

根據最新演演算法升級客戶的雜湊

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

設定應用程式模式。

### 引數

#### `mode`

要設定的應用程式模式。 可用選項為「開發人員」或「生產」

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--skip-compilation`，`-s`

略過清除和重新產生靜態內容（產生的程式碼、預先處理的CSS和pub/static/中的資產）

- 預設： `false`
- 不接受值


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

顯示目前的應用程式模式。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

提供指令的相依性插入組態的資訊。

### 引數

#### `class`

類別名稱

- 必填


#### `area`

區碼

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

掃描Newsletter範本以找出潛在的變數使用相容性問題

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

掃描電子郵件範本覆寫，以找出潛在的變數使用相容性問題

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

停用效能分析工具。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

啟用效能分析工具。

### 引數

#### `type`

效能分析工具型別

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

停用資料庫查詢記錄

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

啟用資料庫查詢記錄

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--include-all-queries`

記錄所有查詢。 [true\|false]

- 預設： `true`
- 接受值

#### `--query-time-threshold`

查詢時間臨界值。

- 預設： `0.001`
- 接受值

#### `--include-call-stack`

包含呼叫棧疊。 [true\|false]

- 預設： `true`
- 接受值


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

收集和發佈佈景主題的來源檔案。

### 引數

#### `file`

要預先處理的檔案（請指定不帶副檔名的檔案）

- 預設： `css/styles-mcss/styles-l`

- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--type`

來源檔案型別： [less]

- 預設： `less`
- 需要值

#### `--locale`

地區設定： [en_US]

- 預設： `en_US`
- 需要值

#### `--area`

區域： [frontend\|adminhtml]

- 預設： `frontend`
- 需要值

#### `--theme`

佈景主題： [廠商/佈景主題]

- 預設： `Magento/luma`
- 需要值


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

停用前端範本提示。 可能需要快取排清。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

啟用前端範本提示。 可能需要快取排清。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

顯示前端範本提示狀態。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

執行測試

### 引數

#### `type`

要執行的測試型別。 可用型別：全部、單位、整合、整合 — 全部、靜態、靜態 — 全部、完整性、舊版、預設

- 預設： `default`

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--arguments`，`-c`

PHPUnit的其他引數。 範例：「 — c」 — filter=MyTest&#39;」（無空格）

- 預設： &quot;
- 需要值


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

產生URN的目錄至*.xsd對應，以便IDE反白顯示xml。

### 引數

#### `path`

輸出目錄的檔案路徑。 若為PhpStorm，請使用。idea/misc.xml

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--ide`

產生目錄時所用的格式。 支援： [phpstorm， vscode]

- 預設： `phpstorm`
- 需要值


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

使用XSL樣式表轉換XML檔案

### 引數

#### `xml-file`

要轉換的XML檔案的路徑

- 必填


#### `processor`

要套用至XML檔案的XSL樣式表路徑

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--overwrite`，`-o`

覆寫XML檔案

- 預設： `false`
- 不接受值


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

將網域新增至可下載的網域白名單

### 引數

#### `domains`

網域名稱

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

從可下載的網域白名單移除網域

### 引數

#### `domains`

網域名稱

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

顯示可下載的網域白名單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

顯示可用資料重新加密程式的清單。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

使用目前的加密金鑰重新加密加密的資料。

### 引數

#### `encryptors`

要使用的重新加密程式清單（以空格分隔）。

- 預設： `[]`
- 陣列

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

更改env.php檔中的加密金鑰。

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--key`，`-k`

金鑰必須是 32 個字元長的字串。 如果未提供，將生成隨機金鑰。

- 接受值


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

使用最新的加密密碼重新加密已加密的信用卡資料。

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

為此執行個體建立Adobe Systems I/O 事件中的自訂事件提供程序。 如果未指定標籤和描述選項，則必須在 system app/etc/事件-types.json 檔中定義它們。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--label`

用於定義自訂提供者的標籤。

- 接受值

#### `--description`

提供者的說明。

- 接受值


## `events:generate:module`

```bash
bin/magento events:generate:module
```

根據外掛程式清單產生模組

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

傳回指定事件的裝載。

### 引數

#### `event-code`

事件代碼

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--depth`

要傳回的事件裝載中的層級數

- 預設： `2`
- 接受值


## `events:list`

```bash
bin/magento events:list
```

顯示訂閱事件清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

返回在指定模組中定義的可訂閱事件的清單

### 參數

#### `module_name`

模組名稱

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

從設定清單（XML和應用程式設定）在Adobe I/O中建立中繼資料

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `events:provider:info`

```bash
bin/magento events:provider:info
```

返回有關已配置事件提供程式的詳細資訊

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

列出App Builder專案中的事件註冊

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

訂閱事件

### 參數

#### `event-code`

事件程序代碼

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--force`，`-f`

強制訂閱指定的事件，即使它尚未在本機定義。

- 預設： `false`
- 不接受值

#### `--fields`

事件資料裝載中的欄位清單。

- 預設： `[]`
- 需要值

#### `--parent`

具有規則或別名之事件訂閱的父事件代碼。

- 需要值

#### `--rules`

事件訂閱的規則清單，其中每個規則的格式為「field\|operator\|value」。 若要使用此選項，您也必須指定「父項」選項。

- 預設： `[]`
- 需要值

#### `--priority`，`-p`

加速此事件的傳輸。 為需要立即傳送的事件指定此選項。 依預設，事件會由cron每分鐘傳送一次。

- 預設： `false`
- 不接受值

#### `--destination`，`-d`

此事件的目的地。 為應傳送至自定義目的地的事件指定此選項。

- 違約： `default`
- 需要值

#### `--hipaaAuditRequired`

表示事件包含須接受HIPAA稽核的資料。

- 預設： `false`
- 不接受值


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

同步處理此執行個體的事件中繼資料

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--delete`，`-d`

刪除不再需要的事件中繼資料

- 預設： `false`
- 不接受值


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

移除所提供事件的訂閱

### 引數

#### `event-code`

要取消訂閱的事件代碼

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

發現代碼庫中的短語

### 引數

#### `directory`

要剖析的目錄路徑。 若已設定 — magento旗標，則不需要

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--output`，`-o`

輸出檔案的路徑（包括檔名）。 如果未指定檔案，則預設為 stdout。

- 需要值

#### `--magento`，`-m`

使用 --magento 參數來剖析目前Magento程序代碼庫。 如果指定了目錄，請省略該參數。

- 預設： `false`
- 不接受值


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

儲存語言套件

### 引數

#### `source`

包含翻譯的來源字典檔案路徑

- 必填


#### `locale`

字典的目標地區設定，例如&quot;de_DE&quot;

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--mode`，`-m`

字典儲存模式 — 「取代」 — 以新語言套件取代語言套件 — 「合併」 — 合併語言套件，預設為「取代」

- 預設： `replace`
- 需要值

#### `--allow-duplicates`，`-d`

使用 — allow-duplicates引數以允許儲存轉譯的重複專案。 否則，請忽略引數。

- 預設： `false`
- 不接受值


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

卸載語言包

### 參數

#### `package`

語言套装名稱

- 預設： `[]`
- 必填

- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--backup-code`，`-b`

進行程式碼和組態檔備份（不包括暫存檔案）

- 預設： `false`
- 不接受值


## `indexer:info`

```bash
bin/magento indexer:info
```

顯示允許的索引子

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

重新索引數據

### 引數

#### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

將索引子狀態重設為無效

### 引數

#### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

設定索引器維度模式

### 引數

#### `indexer`

索引子名稱[catalog_product_price|catalogpermissions_category]


#### `mode`

索引器維度模式catalog_product_price          none，website，customer_group，website_and_customer_group catalogpermissions_category    無，customer_group

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

設定索引模式型別

### 引數

#### `mode`

索引器模式類型 [即時|計劃]


#### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

設定指定的索引器狀態

### 引數

#### `status`

索引器狀態型別[無效|已暫停|有效]

- 必填


#### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

顯示索引子Dimension模式

### 引數

#### `indexer`

以空格分隔的索引型別清單，或省略以套用至所有索引(catalog_product_price、catalogpermissions_category)

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

顯示索引模式

### 引數

#### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

顯示索引器的狀態

### 引數

#### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `info:adminuri`

```bash
bin/magento info:adminuri
```

顯示Magento管理員URI

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `info:backups:list`

```bash
bin/magento info:backups:list
```

列印可用備份檔案的清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `info:currency:list`

```bash
bin/magento info:currency:list
```

顯示可用貨幣的清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

顯示Magento架構的相依性數量

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--output`，`-o`

報表檔案名稱

- 預設： `framework-dependencies.csv`
- 需要值


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

顯示模組之間的相依性數目

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--output`，`-o`

報表檔案名稱

- 預設： `modules-dependencies.csv`
- 需要值


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

顯示模組之間的循環相依性數目

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--output`，`-o`

報表檔案名稱

- 預設： `modules-circular-dependencies.csv`
- 需要值


## `info:language:list`

```bash
bin/magento info:language:list
```

顯示可用語言地區設定的清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

顯示可用時區清單

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

通過提供補償論據建立保留

### 參數

#### `compensations`

“：： 格式中的補償參數清單

- 違約： `[]`
- 陣列

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--raw`，`-r`

原始輸出

- 違約： `false`
- 不接受值


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

顯示所有具有可銷售數量不一致的訂單與產品

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--complete-orders`，`-c`

僅顯示完整訂單的不一致

- 預設： `false`
- 不接受值

#### `--incomplete-orders`，`-i`

僅顯示未完成訂單的不一致

- 預設： `false`
- 不接受值

#### `--bunch-size`，`-b`

定義將同時載入多少訂單

- 預設： `50`
- 接受值

#### `--raw`，`-r`

原始輸出

- 預設： `false`
- 不接受值


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

下載並匯入來源選擇演演算法的地理名稱

### 引數

#### `countries`

要匯入的國家代碼清單

- 預設： `[]`
- 必填

- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

設定維護模式劐免IP

### 引數

#### `ip`

允許的IP位址

- 違約： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--none`

清除允許的IP地址

- 預設： `false`
- 不接受值

#### `--add`

將 IP 地址新增至現有清單

- 違約： `false`
- 不接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

停用維護模式

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--ip`

允許的IP位址（使用「無」清除允許的IP清單）

- 預設： `[]`
- 需要值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

啟用維護模式

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--ip`

允許的IP位址（使用「無」清除允許的IP清單）

- 預設： `[]`
- 需要值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

顯示維護模式狀態

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `media-content:sync`

```bash
bin/magento media-content:sync
```

將內容與資產同步

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

同步資料庫中的媒體儲存和媒體資產

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `module:config:status`

```bash
bin/magento module:config:status
```

檢查「app/etc/config.php」檔案中的模組設定，並報告模組設定是否為最新狀態

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

停用指定的模組

### 引數

#### `module`

模組名稱

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--force`，`-f`

略過相依性檢查

- 預設： `false`
- 不接受值

#### `--all`

停用所有模組

- 預設： `false`
- 不接受值

#### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。 如果模組有靜態檢視檔案，則為必要

- 預設： `false`
- 不接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

啟用指定的模組

### 引數

#### `module`

模組名稱

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--force`，`-f`

略過相依性檢查

- 預設： `false`
- 不接受值

#### `--all`

啟用所有模組

- 預設： `false`
- 不接受值

#### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。 如果模組有靜態檢視檔案，則為必要

- 預設： `false`
- 不接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

顯示模組的狀態

### 引數

#### `module-names`

選用模組名稱

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--enabled`

僅列印已啟用的模組

- 預設： `false`
- 不接受值

#### `--disabled`

僅列印停用的模組

- 預設： `false`
- 不接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

卸載由撰寫器安裝的模組

### 參數

#### `module`

模組的名稱

- 預設： `[]`
- 必填

- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--remove-data`，`-r`

移除模組安裝的資料

- 預設： `false`
- 不接受值

#### `--backup-code`

進行程式碼和組態檔備份（不包括暫存檔案）

- 預設： `false`
- 不接受值

#### `--backup-media`

進行媒體備份

- 預設： `false`
- 不接受值

#### `--backup-db`

進行完整的資料庫備份

- 預設： `false`
- 不接受值

#### `--non-composer`

所有過去模組皆會採用非撰寫器型

- 預設： `false`
- 不接受值

#### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。 如果模組有靜態檢視檔案，則為必要

- 預設： `false`
- 不接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

檢查部署佇列中是否有專案，並建立適當的部署標籤。

### 引數

#### `message`

部署訊息？

- 必填


#### `change_log`

變更記錄？

- 必填


#### `user`

部署使用者


#### `revision`

修訂

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

MessageQueue取用者清單

```
This command shows list of MessageQueue consumers.
```

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

重新啟動MessageQueue使用者

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

啟動MessageQueue取用者

```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```

### 引數

#### `consumer`

要啟動的消費者名稱。

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--max-messages`

處理序終止前，消費者要處理的訊息數目。 如果未指定 - 在處理所有排隊的消息后終止。

- 需要值

#### `--batch-size`

每批次的訊息數。 僅適用於批次消費者。

- 需要值

#### `--area-code`

偏好區域（全域、adminhtml等）預設為全域。

- 需要值

#### `--single-thread`

此選項可防止同時執行一個使用者的多個復本。

- 預設： `false`
- 不接受值

#### `--multi-process`

每個取用者的處理序數目。

- 接受值

#### `--pid-file-path`

儲存PID的檔案路徑（此選項已過時，改用 — 單一執行緒）

- 需要值


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

將媒體檔案與遠端儲存裝置同步。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

將摘要資料重新同步至SaaS服務。

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--feed`

要完全重新同步至SaaS服務的摘要名稱。 可用摘要： Payment Services訂單生產、Payment Services訂單沙箱、Payment Services訂單狀態生產、Payment Services訂單狀態沙箱、Payment Services商店生產、Payment Services商店沙箱

- 需要值

#### `--no-reindex`

執行只將摘要資料重新提交至SaaS服務的作業。 不會重新編列索引。 （此選項不適用於產品、產品概述、價格摘要）

- 預設： `false`
- 不接受值

#### `--cleanup-feed`

強制在同步之前清除摘要索引器表格。

- 預設： `false`
- 不接受值

#### `--dry-run`

試試。 不會匯出數據。 若要將裝載儲存至記錄檔var/log/saas-export.log ，請使用環境變數EXPORTER_EXTENDED_LOG=1執行。

- 預設： `false`
- 不接受值

#### `--thread-count`

設定同步處理執行緒計數。

- 需要值

#### `--batch-size`

設置同步批大小

- 需要值

#### `--continue-resync`

繼續從上次儲存的位置重新同步 （此選項適用於產品、產品覆蓋、價格饋送）

- 違約： `false`
- 不接受值

#### `--by-ids`

部分依照提供的識別碼清單重新同步。 （此選項適用於產品、產品覆寫和價格摘要）

- 需要值

#### `--id-type`

用於部分重新同步的識別碼類型 （例如： sku、productId 等）

- 需要值


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

為基於撰寫器的Magento安裝部署範例數據模組

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--no-update`

更新composer.json而不執行composer更新

- 預設： `false`
- 不接受值


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

拿掉 composer.json 的所有範例數據報

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--no-update`

在不執行撰寫器更新的情況下更新composer.json

- 預設： `false`
- 不接受值


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

重設所有範例資料模組以重新安裝

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

停用管理員使用者忘記密碼表單的reCAPTCHA

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

停用管理員使用者登入表單的reCAPTCHA

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

設定用於產生Google OTP的密碼。

### 引數

#### `user`

使用者名稱

- 必填


#### `secret`

密碼

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

列出所有可用的提供者

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

重設一位使用者的設定

### 引數

#### `user`

使用者名稱

- 必填


#### `provider`

提供者代碼

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

執行應用程式伺服器

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--port`，`-p`

伺服器連線埠

- 預設： `9501`
- 接受值

#### `--background`，`-b`

背景模式旗標

- 預設： `0`
- 接受值

#### `--workerNum`，`-wn`

要啟動的工作者處理序數目

- 預設： `4`
- 接受值

#### `--dispatchMode`，`-dm`

將連線分派到工作者處理序的模式

- 預設： `3`
- 接受值

#### `--maxRequests`，`-mr`

工作者處理序重新啟動前的最大要求數

- 預設： `10000`
- 接受值

#### `--area`，`-a`

應用程式伺服器區域

- 預設： `graphql`
- 接受值

#### `--magento-init-params`，`-mip`

magento bootstrap初始引數

- 預設： &quot;
- 接受值

#### `--maxWaitTime`，`-mwt`

重新載入後等候背景工作程式的時間長度(例如 設定變更)，然後將其刪除

- 預設： `3600`
- 接受值

#### `--state-monitor`

啟用狀態監視。 僅用於偵錯狀態問題！

- 預設： `false`
- 不接受值


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

ApplicationServer狀態監視器的彙總輸出

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

備份Magento應用程式的程式碼基底、媒體和資料庫

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--code`

進行程式碼和組態檔備份（不包括暫存檔案）

- 預設： `false`
- 不接受值

#### `--media`

進行媒體備份

- 預設： `false`
- 不接受值

#### `--db`

進行完整的資料庫備份

- 違約： `false`
- 不接受值

#### `--magento-init-params`

新增至任何命令以自定義Magento初始化參數 例如：“MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache”

- 需要值


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

建立或修改部署設定

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--remote-storage-driver`

遠端儲存驅動程式

- 需要值

#### `--remote-storage-prefix`

遠端儲存首碼

- 預設： &quot;
- 需要值

#### `--remote-storage-endpoint`

遠端儲存端點

- 需要值

#### `--remote-storage-bucket`

遠端儲存貯體

- 需要值

#### `--remote-storage-region`

遠端儲存區域

- 需要值

#### `--remote-storage-key`

遠端儲存存取金鑰

- 預設： &quot;
- 需要值

#### `--remote-storage-secret`

遠端儲存秘密金鑰

- 預設： &quot;
- 需要值

#### `--remote-storage-path-style`

遠端儲存路徑樣式

- 預設： `0`
- 需要值

#### `--backend-frontname`

後端前端名稱（如果遺失，則會自動產生）

- 需要值

#### `--enable-debug-logging`

啟用偵錯記錄

- 需要值

#### `--enable-syslog-logging`

啟用系統日誌記錄

- 需要值

#### `--id_salt`

graphql Salt

- 需要值

#### `--checkout-async`

啟用非同步訂單處理？ 1 — 是，0 — 否

- 需要值

#### `--config-async`

啟用非同步管理設定儲存？ 1 — 是，0 — 否

- 需要值

#### `--amqp-host`

Amqp 伺服器主機

- 預設值： &#39;&#39;
- 需要值

#### `--amqp-port`

Amqp server 連接埠

- 預設： `5672`
- 需要值

#### `--amqp-user`

Amqp伺服器使用者名稱

- 預設： &quot;
- 需要值

#### `--amqp-password`

Amqp伺服器密碼

- 預設： &quot;
- 需要值

#### `--amqp-virtualhost`

Amqp virtualhost

- 預設： `/`
- 需要值

#### `--amqp-ssl`

Amqp SSL

- 預設： &quot;
- 需要值

#### `--amqp-ssl-options`

Amqp SSL選項(JSON)

- 預設： &quot;
- 需要值

#### `--consumers-wait-for-messages`

消費者是否應該等候佇列中的訊息？ 1 — 是，0 — 否

- 需要值

#### `--queue-default-connection`

訊息佇列預設連線。 可以是&#39;db&#39;、&#39;amqp&#39;或自訂佇列系統。必須安裝並設定佇列系統，否則將無法正確處理訊息。

- 需要值

#### `--deferred-total-calculating`

啟用延後總計計算？ 1 — 是，0 — 否

- 需要值

#### `--key`

加密金鑰

- 需要值

#### `--db-host`

資料庫伺服器主機

- 需要值

#### `--db-name`

資料庫名稱

- 需要值

#### `--db-user`

資料庫伺服器使用者名稱

- 需要值

#### `--db-engine`

資料庫伺服器引擎

- 需要值

#### `--db-password`

資料庫伺服器密碼

- 需要值

#### `--db-prefix`

資料庫表格前置詞

- 需要值

#### `--db-model`

資料庫型別

- 需要值

#### `--db-init-statements`

資料庫初始命令集

- 需要值

#### `--skip-db-validation`，`-s`

若指定，則會略過資料庫連線驗證

- 預設： `false`
- 不接受值

#### `--http-cache-hosts`

http快取主機

- 需要值

#### `--db-ssl-key`

使用者端金鑰檔案的完整路徑，以透過SSL建立資料庫連線

- 預設值： &#39;&#39;
- 需要值

#### `--db-ssl-cert`

用戶端憑證檔的完整路徑，以便通過SSL建立資料庫連接

- 預設值： &#39;&#39;
- 需要值

#### `--db-ssl-ca`

伺服器憑證檔的完整路徑，以便通過SSL建立資料庫連接

- 預設值： &#39;&#39;
- 需要值

#### `--db-ssl-verify`

驗證伺服器認證

- 違約： `false`
- 不接受值

#### `--session-save`

工作階段儲存處理常式

- 需要值

#### `--session-save-redis-host`

使用UNIX通訊端時完整的主機名稱、IP位址或絕對路徑

- 需要值

#### `--session-save-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--session-save-redis-password`

Redis伺服器密碼

- 需要值

#### `--session-save-redis-timeout`

連線逾時（以秒為單位）

- 需要值

#### `--session-save-redis-retries`

Redis連線重試。

- 需要值

#### `--session-save-redis-persistent-id`

啟用持續連線的唯一字串

- 需要值

#### `--session-save-redis-db`

Redis資料庫編號

- 需要值

#### `--session-save-redis-compression-threshold`

Redis壓縮臨界值

- 需要值

#### `--session-save-redis-compression-lib`

Redis壓縮程式庫。 值： gzip （預設）、lzf、lz4、snappy

- 需要值

#### `--session-save-redis-log-level`

Redis記錄層級。 值： 0 （最少詳細）至7 （最詳細）

- 需要值

#### `--session-save-redis-max-concurrency`

可等候鎖定一個工作階段的最大處理序數目

- 需要值

#### `--session-save-redis-break-after-frontend`

嘗試中斷前端工作階段鎖定之前要等待的秒數

- 需要值

#### `--session-save-redis-break-after-adminhtml`

嘗試解除管理員工作階段鎖定之前的等待秒數

- 需要值

#### `--session-save-redis-first-lifetime`

非機器人第一次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

#### `--session-save-redis-bot-first-lifetime`

機器人首次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

#### `--session-save-redis-bot-lifetime`

機器人在後續寫入時的會話存留期（使用 0 表示禁用）

- 需要值

#### `--session-save-redis-disable-locking`

Redis會停用鎖定。 值： false （預設）， true

- 需要值

#### `--session-save-redis-min-lifetime`

Redis最小工作階段存留期（以秒為單位）

- 需要值

#### `--session-save-redis-max-lifetime`

Redis 最大會話 期限，以秒為單位

- 需要值

#### `--session-save-redis-sentinel-master`

Redis Sentinel主版

- 需要值

#### `--session-save-redis-sentinel-servers`

Redis Sentinel伺服器，以逗號分隔

- 需要值

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主版。 值： false （預設）， true

- 需要值

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連線重試。

- 需要值

#### `--cache-backend`

預設快取處理常式

- 需要值

#### `--cache-backend-redis-server`

Redis伺服器

- 需要值

#### `--cache-backend-redis-db`

快取的資料庫編號

- 需要值

#### `--cache-backend-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--cache-backend-redis-password`

Redis伺服器密碼

- 需要值

#### `--cache-backend-redis-compress-data`

設為0可停用壓縮（預設為1，已啟用）

- 需要值

#### `--cache-backend-redis-compression-lib`

壓縮程式庫使用[snappy，lzf，l4z，zstd，gzip] （留空將自動決定）

- 需要值

#### `--cache-backend-redis-use-lua`

設為1以啟用lua （預設為0，已停用）

- 需要值

#### `--cache-backend-redis-use-lua-on-gc`

設為0可停用記憶體回收上的lua （預設為1，已啟用）

- 需要值

#### `--cache-id-prefix`

快取金鑰的ID首碼

- 需要值

#### `--allow-parallel-generation`

允許以非封鎖方式產生快取

- 預設： `false`
- 不接受值

#### `--page-cache`

預設快取處理常式

- 需要值

#### `--page-cache-redis-server`

Redis 伺服器

- 需要值

#### `--page-cache-redis-db`

快取的資料庫編號

- 需要值

#### `--page-cache-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--page-cache-redis-password`

Redis伺服器密碼

- 需要值

#### `--page-cache-redis-compress-data`

設為1可壓縮整頁快取（使用0可停用）

- 需要值

#### `--page-cache-redis-compression-lib`

使用[snappy，lzf，l4z，zstd，gzip]的壓縮程式庫（留空將自動決定）

- 需要值

#### `--page-cache-id-prefix`

快取金鑰的ID首碼

- 需要值

#### `--lock-provider`

鎖定提供者名稱

- 需要值

#### `--lock-db-prefix`

安裝特定的鎖定首碼以避免鎖定衝突

- 需要值

#### `--lock-zookeeper-host`

要連線至Zookeeper叢集的主機與連線埠。 例如： 127.0.0.1：2181

- 需要值

#### `--lock-zookeeper-path`

動物園管理員將保存鎖的路徑。 默認路徑為： /magento/locks

- 需要值

#### `--lock-file-path`

儲存檔案鎖定的路徑。

- 需要值

#### `--document-root-is-pub`

要顯示的旗標為Pub位於根目錄，只能為true或false

- 需要值

#### `--backpressure-logger`

背壓記錄器處理常式

- 需要值

#### `--backpressure-logger-redis-server`

Redis伺服器

- 需要值

#### `--backpressure-logger-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--backpressure-logger-redis-timeout`

Redis伺服器逾時

- 需要值

#### `--backpressure-logger-redis-persistent`

Redis永久

- 需要值

#### `--backpressure-logger-redis-db`

Redis db編號

- 需要值

#### `--backpressure-logger-redis-password`

Redis伺服器密碼

- 需要值

#### `--backpressure-logger-redis-user`

Redis伺服器使用者

- 需要值

#### `--backpressure-logger-id-prefix`

金鑰的ID首碼

- 需要值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

在資料庫中安裝和升級資料

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--magento-init-params`

新增至任何命令以自定義Magento初始化參數 例如：“MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache”

- 需要值


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

產生修補程式並將其放在特定資料夾中。

### 引數

#### `module`

模組名稱

- 必填


#### `patch`

修補程式名稱

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--revertable`

檢查修補程式是否可回覆。

- 預設： `false`
- 接受值

#### `--type`

瞭解應生成哪種類型的修補程式。 可用值： `data`、 `schema`.

- 預設： `data`
- 接受值


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

產生允許宣告安裝程式編輯的表格和欄的白名單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--module-name`

產生白名單的模組名稱

- 預設： `all`
- 接受值


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

將簽出引號相關表格移至個別的DB伺服器

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--host`

從屬DB伺服器主機

- 預設： `localhost`
- 需要值

#### `--dbname`

從屬資料庫名稱

- 需要值

#### `--username`

從屬資料庫使用者名稱

- 預設： `root`
- 需要值

#### `--password`

從屬資料庫使用者密碼

- 接受值

#### `--connection`

從屬連線名稱

- 預設： `default`
- 接受值

#### `--resource`

從屬資源名稱

- 預設： `default`
- 接受值

#### `--maxAllowedLag`

允許的延遲從屬連線上限（以秒為單位）

- 預設： &quot;
- 接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

將簽出引號相關表格移至個別的DB伺服器。 自2.4.2起已棄用，將移除

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--host`

簽出DB伺服器主機

- 需要值

#### `--dbname`

簽出資料庫名稱

- 需要值

#### `--username`

簽出DB使用者名稱

- 需要值

#### `--password`

簽出資料庫使用者密碼

- 接受值

#### `--connection`

簽出連線名稱

- 預設： `checkout`
- 接受值

#### `--resource`

簽出資源名稱

- 預設： `checkout`
- 接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

將銷售相關資料表移至個別的DB伺服器。 自2.4.2起已棄用，將移除

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--host`

銷售資料庫伺服器主機

- 需要值

#### `--dbname`

銷售資料庫名稱

- 需要值

#### `--username`

銷售資料庫使用者名稱

- 需要值

#### `--password`

銷售資料庫使用者密碼

- 接受值

#### `--connection`

銷售連線名稱

- 預設： `sales`
- 接受值

#### `--resource`

銷售資源名稱

- 預設： `sales`
- 接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

安裝和升級資料庫綱要

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--convert-old-scripts`

允許轉換舊腳本（InstallSchema、UpgradeSchema）到 db_綱要.xml 格式

- 預設： `false`
- 接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

檢查資料庫結構描述或資料是否需要升級

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

產生DI組態以及所有可自動產生的遺漏類別

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

安裝Magento應用程式

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--remote-storage-driver`

遠端儲存驅動程式

- 需要值

#### `--remote-storage-prefix`

遠端儲存前綴

- 預設值： &#39;&#39;
- 需要值

#### `--remote-storage-endpoint`

遠端儲存 端點

- 需要值

#### `--remote-storage-bucket`

遠端儲存桶

- 需要值

#### `--remote-storage-region`

遠端儲存區域

- 需要值

#### `--remote-storage-key`

遠端儲存存取金鑰

- 預設： &quot;
- 需要值

#### `--remote-storage-secret`

遠端儲存秘密金鑰

- 預設： &quot;
- 需要值

#### `--remote-storage-path-style`

遠端儲存路徑樣式

- 預設： `0`
- 需要值

#### `--backend-frontname`

後端前端名稱（如果遺失，則會自動產生）

- 需要值

#### `--enable-debug-logging`

啟用偵錯記錄

- 需要值

#### `--enable-syslog-logging`

啟用Syslog記錄

- 需要值

#### `--id_salt`

graphql Salt

- 需要值

#### `--checkout-async`

啟用非同步訂單處理？ 1 — 是，0 — 否

- 需要值

#### `--config-async`

啟用非同步管理設定儲存？ 1 — 是，0 — 否

- 需要值

#### `--amqp-host`

Amqp伺服器主機

- 預設： &quot;
- 需要值

#### `--amqp-port`

Amqp伺服器連線埠

- 預設： `5672`
- 需要值

#### `--amqp-user`

Amqp伺服器使用者名稱

- 預設： &quot;
- 需要值

#### `--amqp-password`

Amqp伺服器密碼

- 預設： &quot;
- 需要值

#### `--amqp-virtualhost`

Amqp virtualhost

- 預設： `/`
- 需要值

#### `--amqp-ssl`

Amqp SSL

- 預設： &quot;
- 需要值

#### `--amqp-ssl-options`

Amqp SSL 選項 （JSON）

- 預設值： &#39;&#39;
- 需要值

#### `--consumers-wait-for-messages`

消費者是否應該等候佇列中的訊息？ 1 — 是，0 — 否

- 需要值

#### `--queue-default-connection`

訊息佇列預設連線。 可以是&#39;db&#39;、&#39;amqp&#39;或自訂佇列系統。必須安裝並設定佇列系統，否則將無法正確處理訊息。

- 需要值

#### `--deferred-total-calculating`

啟用延後總計計算？ 1 — 是，0 — 否

- 需要值

#### `--key`

加密金鑰

- 需要值

#### `--db-host`

資料庫伺服器主機

- 需要值

#### `--db-name`

資料庫名稱

- 需要值

#### `--db-user`

資料庫伺服器使用者名稱

- 需要值

#### `--db-engine`

資料庫伺服器引擎

- 需要值

#### `--db-password`

資料庫伺服器密碼

- 需要值

#### `--db-prefix`

資料庫表格前置詞

- 需要值

#### `--db-model`

資料庫型別

- 需要值

#### `--db-init-statements`

資料庫初始命令集

- 需要值

#### `--skip-db-validation`，`-s`

若指定，則會略過資料庫連線驗證

- 預設： `false`
- 不接受值

#### `--http-cache-hosts`

http快取主機

- 需要值

#### `--db-ssl-key`

使用者端金鑰檔案的完整路徑，以透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

#### `--db-ssl-cert`

使用者端憑證檔案的完整路徑，以便透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

#### `--db-ssl-ca`

伺服器憑證檔案的完整路徑，以透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

#### `--db-ssl-verify`

驗證伺服器認證

- 預設： `false`
- 不接受值

#### `--session-save`

工作階段儲存處理常式

- 需要值

#### `--session-save-redis-host`

使用UNIX通訊端時完整的主機名稱、IP位址或絕對路徑

- 需要值

#### `--session-save-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--session-save-redis-password`

Redis伺服器密碼

- 需要值

#### `--session-save-redis-timeout`

連線逾時（以秒為單位）

- 需要值

#### `--session-save-redis-retries`

Redis連線重試。

- 需要值

#### `--session-save-redis-persistent-id`

啟用持續連線的唯一字串

- 需要值

#### `--session-save-redis-db`

Redis資料庫編號

- 需要值

#### `--session-save-redis-compression-threshold`

Redis壓縮臨界值

- 需要值

#### `--session-save-redis-compression-lib`

Redis壓縮程式庫。 值： gzip （預設）、lzf、lz4、snappy

- 需要值

#### `--session-save-redis-log-level`

Redis記錄層級。 值： 0 （最少詳細）至7 （最詳細）

- 需要值

#### `--session-save-redis-max-concurrency`

可等候鎖定一個工作階段的最大處理序數目

- 需要值

#### `--session-save-redis-break-after-frontend`

嘗試中斷前端工作階段鎖定之前要等待的秒數

- 需要值

#### `--session-save-redis-break-after-adminhtml`

嘗試解除管理員工作階段鎖定之前的等待秒數

- 需要值

#### `--session-save-redis-first-lifetime`

非機器人第一次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

#### `--session-save-redis-bot-first-lifetime`

機器人首次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

#### `--session-save-redis-bot-lifetime`

機器人後續寫入的工作階段期限（使用0可停用）

- 需要值

#### `--session-save-redis-disable-locking`

Redis會停用鎖定。 值： false （預設）， true

- 需要值

#### `--session-save-redis-min-lifetime`

Redis最小工作階段存留期（以秒為單位）

- 需要值

#### `--session-save-redis-max-lifetime`

Redis最長工作階段存留期（以秒為單位）

- 需要值

#### `--session-save-redis-sentinel-master`

Redis Sentinel主版

- 需要值

#### `--session-save-redis-sentinel-servers`

Redis Sentinel 伺服器，以逗號分隔

- 需要值

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主版。 值： false （預設）， true

- 需要值

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連線重試。

- 需要值

#### `--cache-backend`

預設快取處理常式

- 需要值

#### `--cache-backend-redis-server`

Redis伺服器

- 需要值

#### `--cache-backend-redis-db`

快取的資料庫編號

- 需要值

#### `--cache-backend-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--cache-backend-redis-password`

Redis伺服器密碼

- 需要值

#### `--cache-backend-redis-compress-data`

設為0可停用壓縮（預設為1，已啟用）

- 需要值

#### `--cache-backend-redis-compression-lib`

壓縮程式庫使用[snappy，lzf，l4z，zstd，gzip] （留空將自動決定）

- 需要值

#### `--cache-backend-redis-use-lua`

設為1以啟用lua （預設為0，已停用）

- 需要值

#### `--cache-backend-redis-use-lua-on-gc`

設為0可停用記憶體回收上的lua （預設為1，已啟用）

- 需要值

#### `--cache-id-prefix`

快取金鑰的ID首碼

- 需要值

#### `--allow-parallel-generation`

允許以非封鎖方式產生快取

- 預設： `false`
- 不接受值

#### `--page-cache`

預設快取處理常式

- 需要值

#### `--page-cache-redis-server`

Redis伺服器

- 需要值

#### `--page-cache-redis-db`

快取的資料庫編號

- 需要值

#### `--page-cache-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--page-cache-redis-password`

Redis伺服器密碼

- 需要值

#### `--page-cache-redis-compress-data`

設為1可壓縮整頁快取（使用0可停用）

- 需要值

#### `--page-cache-redis-compression-lib`

使用[snappy，lzf，l4z，zstd，gzip]的壓縮程式庫（留空將自動決定）

- 需要值

#### `--page-cache-id-prefix`

快取金鑰的ID首碼

- 需要值

#### `--lock-provider`

鎖定提供者名稱

- 需要值

#### `--lock-db-prefix`

安裝特定的鎖定首碼以避免鎖定衝突

- 需要值

#### `--lock-zookeeper-host`

要連線至Zookeeper叢集的主機與連線埠。 例如： 127.0.0.1：2181

- 需要值

#### `--lock-zookeeper-path`

動物園管理員將保存鎖的路徑。 默認路徑為： /magento/locks

- 需要值

#### `--lock-file-path`

儲存檔案鎖定的路徑。

- 需要值

#### `--document-root-is-pub`

要顯示的旗標為Pub位於根目錄，只能為true或false

- 需要值

#### `--backpressure-logger`

背壓記錄器處理常式

- 需要值

#### `--backpressure-logger-redis-server`

Redis伺服器

- 需要值

#### `--backpressure-logger-redis-port`

Redis伺服器接聽連線埠

- 需要值

#### `--backpressure-logger-redis-timeout`

Redis伺服器逾時

- 需要值

#### `--backpressure-logger-redis-persistent`

Redis永久

- 需要值

#### `--backpressure-logger-redis-db`

Redis db編號

- 需要值

#### `--backpressure-logger-redis-password`

Redis伺服器密碼

- 需要值

#### `--backpressure-logger-redis-user`

Redis伺服器使用者

- 需要值

#### `--backpressure-logger-id-prefix`

金鑰的ID首碼

- 需要值

#### `--base-url`

商店的URL預計可在。 已棄用，請使用config：set以及路徑web/unsecure/base_url

- 需要值

#### `--language`

預設語言代碼。 已棄用，請使用config：set搭配路徑general/locale/code

- 需要值

#### `--timezone`

預設時區代碼。 已棄用，請使用config：set搭配路徑general/locale/timezone

- 需要值

#### `--currency`

預設貨幣代碼。 已棄用，請使用config：set以及路徑currency/options/base、currency/options/default和currency/options/allow

- 需要值

#### `--use-rewrites`

使用重寫。 不再提倡，使用 config：set with path web/seo/use_rewrites

- 需要值

#### `--use-secure`

使用安全URL。 只有在SSL可用時才啟用此選項。 已棄用，將config：set與路徑web/secure/use_in_frontend一起使用

- 需要值

#### `--base-url-secure`

SSL 連線的基本URL。 已棄用，請使用config：set搭配路徑web/secure/base_url

- 需要值

#### `--use-secure-admin`

使用 SSL 運行管理介面。 不再提倡，使用 config：set with path web/secure/use_in_adminhtml

- 需要值

#### `--admin-use-security-key`

是否要在Magento「管理員 URL 和窗體」中使用「安全密鑰」功能。 不再提倡，使用 config：set with path admin/security/use_form_key

- 需要值

#### `--admin-user`

管理員用戶

- 接受值

#### `--admin-password`

管理員密碼

- 接受值

#### `--admin-email`

管理員電子郵件

- 接受值

#### `--admin-firstname`

管理員名字

- 接受值

#### `--admin-lastname`

管理員姓氏

- 接受值

#### `--search-engine`

搜尋引擎。 值： elasticsearch8， opensearch

- 需要值

#### `--elasticsearch-host`

Elasticsearch伺服器主機。

- 需要值

#### `--elasticsearch-port`

Elasticsearch伺服器連接埠。

- 需要值

#### `--elasticsearch-enable-auth`

設置為 1 以啟用身份驗證。 （預設為 0，停用）

- 需要值

#### `--elasticsearch-username`

Elasticsearch使用者名稱。 僅在啟用HTTP驗證時適用

- 需要值

#### `--elasticsearch-password`

Elasticsearch密碼。 僅在啟用HTTP驗證時適用

- 需要值

#### `--elasticsearch-index-prefix`

Elasticsearch索引首碼。

- 需要值

#### `--elasticsearch-timeout`

Elasticsearch伺服器逾時。

- 需要值

#### `--opensearch-host`

OpenSearch 伺服器主機。

- 需要值

#### `--opensearch-port`

OpenSearch 伺服器連接埠。

- 需要值

#### `--opensearch-enable-auth`

設為1以啟用驗證。 （預設為0，已停用）

- 需要值

#### `--opensearch-username`

OpenSearch使用者名稱。 僅在啟用HTTP驗證時適用

- 需要值

#### `--opensearch-password`

OpenSearch密碼。 僅在啟用HTTP驗證時適用

- 需要值

#### `--opensearch-index-prefix`

OpenSearch索引前置詞。

- 需要值

#### `--opensearch-timeout`

OpenSearch伺服器逾時。

- 需要值

#### `--cleanup-database`

安裝前先清理資料庫

- 預設： `false`
- 不接受值

#### `--sales-order-increment-prefix`

銷售訂單編號前置詞

- 需要值

#### `--use-sample-data`

使用範例資料

- 預設： `false`
- 不接受值

#### `--enable-modules`

逗號分隔模組名稱清單。 安裝期間必須包括此專案。 可用的魔術引數「all」。

- 接受值

#### `--disable-modules`

逗號分隔模組名稱的清單。 在安裝過程中必須避免這種情況。 可用的魔術參數“全部”。

- 接受值

#### `--convert-old-scripts`

允許轉換舊腳本（InstallSchema、UpgradeSchema）到 db_綱要.xml 格式

- 預設： `false`
- 接受值

#### `--interactive`，`-i`

互動式Magento安裝

- 違約： `false`
- 不接受值

#### `--safe-mode`

在破壞性作業（例如移除欄）上安全安裝包含傾印的Magento

- 接受值

#### `--data-restore`

從傾印還原移除的資料

- 接受值

#### `--dry-run`

Magento安裝將以模擬執行模式執行

- 預設： `false`
- 接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

產生夾具

### 引數

#### `profile`

設定檔設定檔的路徑

- 必填

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--skip-reindex`，`-s`

略過重新索引

- 預設： `false`
- 不接受值


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

回覆Magento應用程式程式碼基底、媒體及資料庫

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--code-file`，`-c`

var/backups中程式碼備份檔案的基本名稱

- 需要值

#### `--media-file`，`-m`

var/backups中媒體備份檔案的基本名稱

- 需要值

#### `--db-file`，`-d`

var/backups中db備份檔案的基本名稱

- 需要值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

部署靜態檢視檔案

### 引數

#### `languages`

要輸出靜態檢視檔案的ISO-639語言代碼清單（以空格分隔）。

- 預設： `[]`
- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--force`，`-f`

以任何模式部署檔案。

- 預設： `false`
- 不接受值

#### `--strategy`，`-s`

使用指定的策略部署檔案。

- 預設： `quick`
- 接受值

#### `--area`，`-a`

只產生指定區域的檔案。

- 預設： `all`
- 接受多個值

#### `--exclude-area`

不要產生指定區域的檔案。

- 預設： `none`
- 接受多個值

#### `--theme`，`-t`

只為指定的主題產生靜態檢視檔案。

- 預設： `all`
- 接受多個值

#### `--exclude-theme`

不要產生指定主題的檔案。

- 預設： `none`
- 接受多個值

#### `--language`，`-l`

只產生指定語言的檔案。

- 預設： `all`
- 接受多個值

#### `--exclude-language`

不要產生指定語言的檔案。

- 預設： `none`
- 接受多個值

#### `--jobs`，`-j`

使用指定的作業數目啟用平行處理。

- 預設： `0`
- 接受值

#### `--max-execution-time`

部署靜態處理序的最大預期執行時間（以秒為單位）。

- 預設： `900`
- 接受值

#### `--symlink-locale`

為這些區域設定的檔案建立符號連結，這些檔案會傳遞以進行部署，但沒有自訂。

- 預設： `false`
- 不接受值

#### `--content-version`

如果在多個節點上執行部署，則可以使用靜態內容的自訂版本，以確保靜態內容版本相同且快取可正常運作。

- 需要值

#### `--refresh-content-version-only`

重新整理靜態內容的版本只能用於重新整理瀏覽器快取和CDN快取中的靜態內容。

- 預設： `false`
- 不接受值

#### `--no-javascript`

請勿部署JavaScript檔案。

- 預設： `false`
- 不接受值

#### `--no-js-bundle`

請勿部署JavaScript套件組合檔案。

- 預設： `false`
- 不接受值

#### `--no-css`

請勿部署CSS檔案。

- 預設： `false`
- 不接受值

#### `--no-less`

請勿部署LESS檔案。

- 預設： `false`
- 不接受值

#### `--no-images`

請勿部署影像。

- 預設： `false`
- 不接受值

#### `--no-fonts`

不要部署字型檔案。

- 預設： `false`
- 不接受值

#### `--no-html`

請勿部署HTML檔案。

- 預設： `false`
- 不接受值

#### `--no-misc`

請勿部署其他型別的檔案（.md、.jbf、.csv等）。

- 預設： `false`
- 不接受值

#### `--no-html-minify`

請勿縮制HTML檔案。

- 預設： `false`
- 不接受值

#### `--no-parent`

請勿編譯父系主題。 僅在快速和標準策略中支援。

- 預設： `false`
- 不接受值


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

安裝存放區設定。 自2.2.0版起已棄用。請改用config：set

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--base-url`

商店的URL預計可在。 已棄用，請使用config：set以及路徑web/unsecure/base_url

- 需要值

#### `--language`

默認語言代碼。 不再提倡，使用 config：set with path general/locale/code

- 需要值

#### `--timezone`

默認時區代碼。 不再提倡，使用 config：set with path general/locale/timezone

- 需要值

#### `--currency`

默認貨幣代碼。 不再提倡，使用 config：set with path currency/options/base、currency/options/default 和 currency/options/allow

- 需要值

#### `--use-rewrites`

使用重寫。 不再提倡，使用 config：set with path web/seo/use_rewrites

- 需要值

#### `--use-secure`

使用安全 URL。 只有在SSL可用時才啟用此選項。 已棄用，將config：set與路徑web/secure/use_in_frontend一起使用

- 需要值

#### `--base-url-secure`

SSL連線的基礎URL。 已棄用，請使用config：set搭配路徑web/secure/base_url

- 需要值

#### `--use-secure-admin`

使用SSL執行管理介面。 已棄用，請使用config：set搭配路徑web/secure/use_in_adminhtml

- 需要值

#### `--admin-use-security-key`

是否要在Magento管理員URL和表單中使用「安全性金鑰」功能。 已棄用，請使用config：set以及路徑admin/security/use_form_key

- 需要值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

解除安裝Magento應用程式

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

升級Magento應用程式、資料庫資料和結構描述

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--keep-generated`

防止刪除產生的檔案。 我們不鼓勵使用此選項，除非是部署至生產環境。 請洽詢您的系統整合商或管理員，以取得更多資訊。

- 預設： `false`
- 不接受值

#### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式

- 預設： `false`
- 接受值

#### `--safe-mode`

在破壞性作業（例如移除欄）上安全安裝包含傾印的Magento

- 接受值

#### `--data-restore`

從轉儲中還原已刪除的數據

- 接受值

#### `--dry-run`

Magento安裝將以模擬執行模式執行

- 違約： `false`
- 接受值

#### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值


## `store:list`

```bash
bin/magento store:list
```

顯示商店清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `store:website:list`

```bash
bin/magento store:website:list
```

顯示網站的清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

建立程式碼備份

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--name`

轉儲名稱

- 接受值

#### `--output`，`-o`

輸出路徑

- 接受值

#### `--logs`，`-l`

包含記錄

- 預設： `false`
- 不接受值


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

建立資料庫備份

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--name`

傾印名稱

- 接受值

#### `--output`，`-o`

輸出路徑

- 接受值

#### `--logs`，`-l`

包含記錄

- 預設： `false`
- 不接受值

#### `--ignore-sanitize`，`-i`

忽略處理

- 預設： `false`
- 不接受值


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

檢查所需的備份公用程式

### 選項

有關全域選項，請參閱 [全域選項](#global-options)。

#### `--hide-paths`

僅檢查所需的主控台公用程式

- 預設： `false`
- 不接受值


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

建立公用程式路徑清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--force`，`-f`

強制

- 預設： `false`
- 不接受值


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

解除安裝主題

### 引數

#### `theme`

佈景主題的路徑。 主題路徑應指定為完整路徑，即area/vendor/name。 例如，前端/Magento/空白

- 預設： `[]`
- 必填

- 陣列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--backup-code`

進行程式碼備份（不包括暫存檔案）

- 預設： `false`
- 不接受值

#### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。

- 預設： `false`
- 不接受值


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

產生清漆VCL並將其回溯至命令列

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--access-list`

可以清除清漆的IP存取清單

- 預設： `localhost`
- 需要值

#### `--backend-host`

Web後端的主機

- 預設： `localhost`
- 需要值

#### `--backend-port`

Web後端的連線埠

- 預設： `8080`
- 需要值

#### `--export-version`

清漆檔案的版本

- 預設： `6`
- 需要值

#### `--grace-period`

寬限期（以秒為單位）

- 預設： `300`
- 需要值

#### `--input-file`

要從中產生vcl的輸入檔案

- 需要值

#### `--output-file`

要寫入vcl的檔案路徑

- 需要值


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

運行已註冊的 Webhook 用於開發目的。

### 引數

#### `name`

網路鉤子名稱

- 必填


#### `payload`

JSON格式的webhook裝載

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

根據 Webhook 註冊生成外掛程式

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

返回指定 Webhook 的有效負載。

### 引數

#### `webhook-name`

Webhook方法名稱

- 必填


#### `webhook-type`

Webhook型別（前、後）

- 預設： `before`

### 選項

如需全域選項，請參閱[全域選項](#global-options)。

#### `--depth`

要傳回的webhook承載中的層數

- 預設： `3`
- 接受值


## `webhooks:list`

```bash
bin/magento webhooks:list
```

顯示已訂閱Webhook的清單

### 選項

如需全域選項，請參閱[全域選項](#global-options)。


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

傳回指定模組支援的webhook方法名稱清單

### 引數

#### `module_name`

模組名稱

- 必填

### 選項

如需全域選項，請參閱[全域選項](#global-options)。
