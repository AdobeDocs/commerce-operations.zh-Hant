---
source-git-commit: 1f8fda87e0d39fdcf2372f72373a0b2ea486d25a
workflow-type: tm+mt
source-wordcount: '21185'
ht-degree: 0%

---
# bin/magento (Adobe Commerce內部部署)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**版本**： 2.4.7-p1

此參考包含141個可透過`bin/magento`命令列工具使用的命令。
初始清單是在Adobe Commerce使用`bin/magento list`命令自動產生的。
使用[「新增CLI命令」](https://developer.adobe.com/commerce/php/development/cli-commands/)指南來新增自訂CLI命令。

>[!NOTE]
>
>您可以使用捷徑來呼叫`bin/magento` CLI命令，而不使用完整的命令名稱。 例如，您可以使用`bin/magento s:up`、`bin/magento s:upg`呼叫`bin/magento setup:upgrade`。 請參閱[捷徑語法](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax)，瞭解如何使用捷徑與任何CLI命令。

>[!NOTE]
>
>此參考是從應用程式程式碼基底產生的。 若要變更內容，您可以更新[程式碼基底](https://github.com/magento)存放庫中對應命令實作的原始程式碼，並提交變更以供檢閱。 另一種方式是&#x200B;_提供意見反應_ （在右上角尋找連結）。 如需貢獻准則，請參閱[程式碼貢獻](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)。

## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

提供殼層完成建議的內部命令


### `--shell`，`-s`

殼層型別(「bash」、「fish」、「zsh」)

- 需要值

### `--input`，`-i`

輸入權杖陣列(例如COMP_WORDS或argv)

- 預設： `[]`
- 需要值

### `--current`，`-c`

游標所在的「輸入」陣列索引(例如COMP_CWORD)

- 需要值

### `--api-version`，`-a`

完成指令碼的API版本

- 需要值

### `--symfony`，`-S`

已棄用

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


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


### `shell`

如果未指定shell型別（例如&quot;bash&quot;），則會使用&quot;$SHELL&quot;環境變數的值


### `--debug`

追蹤完成偵錯記錄

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

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

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

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

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

停用Adobe IMS模組


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

啟用Adobe IMS模組。


### `--organization-id`，`-o`

設定Adobe IMS設定的組織ID 。 啟用模組時需要

- 接受值

### `--client-id`，`-c`

設定Adobe IMS設定的使用者端ID。 啟用模組時需要

- 接受值

### `--client-secret`，`-s`

設定Adobe IMS設定的使用者端密碼。 啟用模組時需要

- 接受值

### `--2fa`，`-t`

檢查Adobe Admin Console中是否為「組織」啟用2FA。 啟用模組時需要

- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Adobe IMS模組設定資訊


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Adobe IMS模組的狀態


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

建立管理員


### `--admin-user`

（必要）管理員使用者

- 需要值

### `--admin-password`

（必要）管理員密碼

- 需要值

### `--admin-email`

（必要）管理員電子郵件

- 需要值

### `--admin-firstname`

（必要）管理員名字

- 需要值

### `--admin-lastname`

（必要）管理員姓氏

- 需要值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


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


### `username`

要解除鎖定的管理員使用者名稱

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

建立應用程式的傾印



### `config-types`

以空格分隔的設定型別清單，或省略以傾印所有[範圍、系統、佈景主題、i18n]

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `app:config:import`

```bash
bin/magento app:config:import
```

從共用組態檔匯入資料至適當的資料儲存體


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `app:config:status`

```bash
bin/magento app:config:status
```

檢查設定傳播是否需要更新


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

從Magento1資料庫移轉儲存的卡片


### `--host`

主機名稱/IP。 連線埠是選用的

- 需要值

### `--dbname`

資料庫名稱

- 需要值

### `--username`

資料庫使用者名稱。 必須有讀取存取權

- 需要值

### `--password`

密碼

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

清除快取型別



### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`

- 陣列

### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

停用快取型別



### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`

- 陣列

### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

啟用快取型別



### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`

- 陣列

### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

清除快取型別使用的快取儲存體



### `types`

以空格分隔的快取型別清單，或省略以套用至所有快取型別。

- 預設： `[]`

- 陣列

### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

檢查快取狀態


### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

建立調整大小的產品影像


### `--async`，`-a`

在非同步模式下調整影像大小

- 預設： `false`
- 不接受值

### `--skip_hidden_images`

不要處理產品頁面中標籤為隱藏的影像

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

移除未使用的產品屬性。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

設定是否要強制使用者HTML內容驗證，或改為顯示警告



### `restrict`

y\n

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

設定敏感的設定值



### `path`

設定路徑，例如group/section/field_name


### `value`

設定值


### `--interactive`，`-i`

啟用互動模式以設定所有敏感變數

- 預設： `false`
- 不接受值

### `--scope`

設定範圍（若未設定）請使用「預設」

- 預設： `default`
- 接受值

### `--scope-code`

設定的範圍代碼，預設為空字串

- 預設： &quot;
- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

變更系統組態



### `path`

區段/群組/欄位名稱格式的設定路徑

- 必填

### `value`

設定值

- 必填

### `--scope`

設定範圍（預設、網站或商店）

- 預設： `default`
- 需要值

### `--scope-code`

範圍代碼（只有在範圍不是「預設」時才需要）

- 需要值

### `--lock-env`，`-e`

鎖定值，防止在Admin中進行修改(將儲存於app/etc/env.php)

- 預設： `false`
- 不接受值

### `--lock-config`，`-c`

鎖定並與其他安裝專案共用值，防止在Admin中進行修改(將儲存在app/etc/config.php中)

- 預設： `false`
- 不接受值

### `--lock`，`-l`

已棄用，請改用 — lock-env選項。

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

顯示指定路徑的設定值。 如果未指定路徑，則會顯示所有儲存的值



### `path`

設定路徑，例如section_id/group_id/field_id


### `--scope`

設定範圍（如果未指定），則會使用「預設」範圍

- 預設： `default`
- 接受值

### `--scope-code`

範圍代碼（只有在範圍不是`default`時才需要）

- 預設： &quot;
- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

產生並安裝目前使用者的crontab


### `--force`，`-f`

強制安裝任務

- 預設： `false`
- 不接受值

### `--non-optional`，`-d`

僅安裝非選擇性（預設）工作

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cron:remove`

```bash
bin/magento cron:remove
```

從crontab移除任務


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

依排程執行工作


### `--group`

僅從指定的群組執行工作

- 需要值

### `--exclude-group`

從指定的群組排除工作

- 預設： `[]`
- 接受多個值

### `--bootstrap`

新增或覆寫啟動程式的引數

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

根據最新演演算法升級客戶的雜湊


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

設定應用程式模式。



### `mode`

要設定的應用程式模式。 可用選項為「開發人員」或「生產」

- 必填

### `--skip-compilation`，`-s`

略過清除和重新產生靜態內容（產生的程式碼、預先處理的CSS和pub/static/中的資產）

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

顯示目前的應用程式模式。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:di:info`

```bash
bin/magento dev:di:info <class>
```

提供指令的相依性插入組態的資訊。



### `class`

類別名稱

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

掃描Newsletter範本以找出潛在的變數使用相容性問題


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

掃描電子郵件範本覆寫，以找出潛在的變數使用相容性問題


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

停用效能分析工具。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

啟用效能分析工具。



### `type`

效能分析工具型別


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

停用資料庫查詢記錄


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

啟用資料庫查詢記錄


### `--include-all-queries`

記錄所有查詢。 [true\|false]

- 預設： `true`
- 接受值

### `--query-time-threshold`

查詢時間臨界值。

- 預設： `0.001`
- 接受值

### `--include-call-stack`

包含呼叫棧疊。 [true\|false]

- 預設： `true`
- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

收集和發佈佈景主題的來源檔案。



### `file`

要預先處理的檔案（請指定不帶副檔名的檔案）

- 預設： `css/styles-mcss/styles-l`

- 陣列

### `--type`

來源檔案型別： [less]

- 預設： `less`
- 需要值

### `--locale`

地區設定： [en_US]

- 預設： `en_US`
- 需要值

### `--area`

區域： [frontend\|adminhtml]

- 預設： `frontend`
- 需要值

### `--theme`

佈景主題： [廠商/佈景主題]

- 預設： `Magento/luma`
- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

停用前端範本提示。 可能需要快取排清。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

啟用前端範本提示。 可能需要快取排清。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

顯示前端範本提示狀態。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

執行測試



### `type`

要執行的測試型別。 可用型別：全部、單位、整合、整合 — 全部、靜態、靜態 — 全部、完整性、舊版、預設

- 預設： `default`


### `--arguments`，`-c`

PHPUnit的其他引數。 範例：「 — c」 — filter=MyTest&#39;」（無空格）

- 預設： &quot;
- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

產生URN的目錄至*.xsd對應，以便IDE反白顯示xml。



### `path`

輸出目錄的檔案路徑。 若為PhpStorm，請使用。idea/misc.xml

- 必填

### `--ide`

產生目錄時所用的格式。 支援： [phpstorm， vscode]

- 預設： `phpstorm`
- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

使用XSL樣式表轉換XML檔案



### `xml-file`

要轉換的XML檔案的路徑

- 必填

### `processor`

要套用至XML檔案的XSL樣式表路徑

- 必填

### `--overwrite`，`-o`

覆寫XML檔案

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

將網域新增至可下載的網域白名單



### `domains`

網域名稱

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

從可下載的網域白名單移除網域



### `domains`

網域名稱

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

顯示可下載的網域白名單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

使用最新的加密密碼重新加密已加密的信用卡資料。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

在此例項的Adobe I/O事件中建立自訂事件提供者。 如果您未指定標籤和說明選項，則必須在系統app/etc/event-types.json檔案中定義它們。


### `--label`

用於定義自訂提供者的標籤。

- 接受值

### `--description`

提供者的說明。

- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:generate:module`

```bash
bin/magento events:generate:module
```

根據外掛程式清單產生模組


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

傳回指定事件的裝載。



### `event-code`

事件代碼

- 必填

### `--depth`

要傳回的事件裝載中的層級數

- 預設： `2`
- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:list`

```bash
bin/magento events:list
```

顯示訂閱事件清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

傳回指定模組中定義的可訂閱事件清單



### `module_name`

模組名稱

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

從組態清單（XML和應用程式組態）以Adobe I/O建立中繼資料


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:provider:info`

```bash
bin/magento events:provider:info
```

傳回已設定之事件提供者的詳細資訊


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

列出App Builder專案中的事件註冊


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

訂閱事件



### `event-code`

事件代碼

- 必填

### `--force`，`-f`

強制訂閱指定的事件，即使它尚未在本機定義。

- 預設： `false`
- 不接受值

### `--fields`

事件資料裝載中的欄位清單。

- 預設： `[]`
- 需要值

### `--parent`

具有規則的事件訂閱的父事件代碼。

- 需要值

### `--rules`

事件訂閱的規則清單，其中每個規則的格式為「field\|operator\|value」。

- 預設： `[]`
- 需要值

### `--priority`，`-p`

加速此事件的傳輸。 為需要立即傳送的事件指定此選項。 依預設，事件會由cron每分鐘傳送一次。

- 預設： `false`
- 不接受值

### `--destination`，`-d`

此事件的目的地。 針對應傳送至自訂目的地的事件指定此選項。

- 預設： `default`
- 需要值

### `--hipaaAuditRequired`

表示事件包含須接受HIPAA稽核的資料。

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

同步處理此執行個體的事件中繼資料


### `--delete`，`-d`

刪除不再需要的事件中繼資料

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

移除所提供事件的訂閱



### `event-code`

要取消訂閱的事件代碼

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

探索程式碼基底中的片語



### `directory`

要剖析的目錄路徑。 若已設定 — magento旗標，則不需要


### `--output`，`-o`

輸出檔案的路徑（包括檔案名稱）。 若未指定檔案，預設值為stdout。

- 需要值

### `--magento`，`-m`

使用 — magento引數來剖析目前的Magento程式碼基底。 若指定目錄，則省略引數。

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

儲存語言套件



### `source`

包含翻譯的來源字典檔案路徑

- 必填

### `locale`

字典的目標地區設定，例如&quot;de_DE&quot;

- 必填

### `--mode`，`-m`

字典儲存模式 — 「取代」 — 以新語言套件取代語言套件 — 「合併」 — 合併語言套件，預設為「取代」

- 預設： `replace`
- 需要值

### `--allow-duplicates`，`-d`

使用 — allow-duplicates引數以允許儲存轉譯的重複專案。 否則，請忽略引數。

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

解除安裝語言套件



### `package`

語言套件名稱

- 預設： `[]`

- 必填
- 陣列

### `--backup-code`，`-b`

進行程式碼和組態檔備份（不包括暫存檔案）

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:info`

```bash
bin/magento indexer:info
```

顯示允許的索引子


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

重新索引資料



### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

將索引子狀態重設為無效



### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

設定索引子Dimension模式



### `indexer`

索引子名稱[catalog_product_price|catalogpermissions_category]


### `mode`

索引器維度模式catalog_product_price          none，website，customer_group，website_and_customer_group catalogpermissions_category    無，customer_group


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

設定索引模式型別



### `mode`

索引器模式型別[即時|排程]


### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

設定指定的索引器狀態



### `status`

索引器狀態型別[無效|已暫停|有效]

- 必填

### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

顯示索引子Dimension模式



### `indexer`

以空格分隔的索引型別清單，或省略以套用至所有索引(catalog_product_price、catalogpermissions_category)

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

顯示索引模式



### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

顯示索引器的狀態



### `index`

以空格分隔的索引型別清單，或省略以套用至所有索引。

- 預設： `[]`

- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:adminuri`

```bash
bin/magento info:adminuri
```

顯示Magento管理員URI


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:backups:list`

```bash
bin/magento info:backups:list
```

列印可用備份檔案的清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:currency:list`

```bash
bin/magento info:currency:list
```

顯示可用貨幣的清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

顯示Magento架構的相依性數目


### `--output`，`-o`

報表檔案名稱

- 預設： `framework-dependencies.csv`
- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

顯示模組之間的相依性數目


### `--output`，`-o`

報表檔案名稱

- 預設： `modules-dependencies.csv`
- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

顯示模組之間的循環相依性數目


### `--output`，`-o`

報表檔案名稱

- 預設： `modules-circular-dependencies.csv`
- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:language:list`

```bash
bin/magento info:language:list
```

顯示可用語言地區設定的清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

顯示可用時區清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

依據提供的薪酬引數建立預留



### `compensations`

補償引數清單，格式為「：：：」

- 預設： `[]`

- 陣列

### `--raw`，`-r`

原始輸出

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

顯示所有具有可銷售數量不一致的訂單與產品


### `--complete-orders`，`-c`

僅顯示完整訂單的不一致

- 預設： `false`
- 不接受值

### `--incomplete-orders`，`-i`

僅顯示未完成訂單的不一致

- 預設： `false`
- 不接受值

### `--bunch-size`，`-b`

定義將同時載入多少訂單

- 預設： `50`
- 接受值

### `--raw`，`-r`

原始輸出

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

下載並匯入來源選擇演演算法的地理名稱



### `countries`

要匯入的國家代碼清單

- 預設： `[]`

- 必填
- 陣列

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

設定維護模式劐免IP



### `ip`

允許的IP位址

- 預設： `[]`

- 陣列

### `--none`

清除允許的IP地址

- 預設： `false`
- 不接受值

### `--add`

將IP位址新增至現有清單

- 預設： `false`
- 不接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

停用維護模式


### `--ip`

允許的IP位址（使用「無」清除允許的IP清單）

- 預設： `[]`
- 需要值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

啟用維護模式


### `--ip`

允許的IP位址（使用「無」清除允許的IP清單）

- 預設： `[]`
- 需要值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

顯示維護模式狀態


### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `media-content:sync`

```bash
bin/magento media-content:sync
```

將內容與資產同步


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

同步資料庫中的媒體儲存和媒體資產


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `module:config:status`

```bash
bin/magento module:config:status
```

檢查「app/etc/config.php」檔案中的模組設定，並報告模組設定是否為最新狀態


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

停用指定的模組



### `module`

模組名稱

- 預設： `[]`

- 陣列

### `--force`，`-f`

略過相依性檢查

- 預設： `false`
- 不接受值

### `--all`

停用所有模組

- 預設： `false`
- 不接受值

### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。 如果模組有靜態檢視檔案，則為必要

- 預設： `false`
- 不接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

啟用指定的模組



### `module`

模組名稱

- 預設： `[]`

- 陣列

### `--force`，`-f`

略過相依性檢查

- 預設： `false`
- 不接受值

### `--all`

啟用所有模組

- 預設： `false`
- 不接受值

### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。 如果模組有靜態檢視檔案，則為必要

- 預設： `false`
- 不接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

顯示模組的狀態



### `module-names`

選用模組名稱

- 預設： `[]`

- 陣列

### `--enabled`

僅列印已啟用的模組

- 預設： `false`
- 不接受值

### `--disabled`

僅列印停用的模組

- 預設： `false`
- 不接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

解除安裝撰寫器安裝的模組



### `module`

模組名稱

- 預設： `[]`

- 必填
- 陣列

### `--remove-data`，`-r`

移除模組安裝的資料

- 預設： `false`
- 不接受值

### `--backup-code`

進行程式碼和組態檔備份（不包括暫存檔案）

- 預設： `false`
- 不接受值

### `--backup-media`

進行媒體備份

- 預設： `false`
- 不接受值

### `--backup-db`

進行完整的資料庫備份

- 預設： `false`
- 不接受值

### `--non-composer`

所有過去模組皆會採用非撰寫器型

- 預設： `false`
- 不接受值

### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。 如果模組有靜態檢視檔案，則為必要

- 預設： `false`
- 不接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

檢查部署佇列中是否有專案，並建立適當的部署標籤。



### `message`

部署訊息？

- 必填

### `change_log`

變更記錄？

- 必填

### `user`

部署使用者


### `revision`

修訂


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

MessageQueue取用者清單


```
This command shows list of MessageQueue consumers.
```

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

重新啟動MessageQueue使用者


```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


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


### `consumer`

要啟動的消費者名稱。

- 必填

### `--max-messages`

處理序終止前，消費者要處理的訊息數目。 如果未指定 — 在處理所有佇列的訊息後終止。

- 需要值

### `--batch-size`

每批次的訊息數。 僅適用於批次消費者。

- 需要值

### `--area-code`

偏好區域（全域、adminhtml等）預設為全域。

- 需要值

### `--single-thread`

此選項可防止同時執行一個使用者的多個復本。

- 預設： `false`
- 不接受值

### `--multi-process`

每個取用者的處理序數目。

- 接受值

### `--pid-file-path`

儲存PID的檔案路徑（此選項已過時，改用 — 單一執行緒）

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

將媒體檔案與遠端儲存裝置同步。


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

將摘要資料重新同步至SaaS服務。


### `--feed`

要完全重新同步至SaaS服務的摘要名稱。 可用摘要： Payment Services訂單生產、Payment Services訂單沙箱、Payment Services訂單狀態生產、Payment Services訂單狀態沙箱、Payment Services商店生產、Payment Services商店沙箱

- 需要值

### `--no-reindex`

執行只將摘要資料重新提交至SaaS服務的作業。 不會重新編列索引。 （此選項不適用於產品、產品概述、價格摘要）

- 預設： `false`
- 不接受值

### `--cleanup-feed`

強制在同步之前清除摘要索引器表格。

- 預設： `false`
- 不接受值

### `--dry-run`

試試。 將不會匯出資料。 若要將裝載儲存至記錄檔var/log/saas-export.log ，請使用環境變數EXPORTER_EXTENDED_LOG=1執行。

- 預設： `false`
- 不接受值

### `--thread-count`

設定同步處理執行緒計數。

- 需要值

### `--batch-size`

設定同步批次大小

- 需要值

### `--continue-resync`

繼續從上次儲存的位置重新同步（此選項適用於產品、產品版本、價格摘要）

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

部署範例資料模組，以進行Composer型Magento安裝


### `--no-update`

更新composer.json而不執行composer更新

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

從composer.json移除所有範例資料套件


### `--no-update`

更新composer.json而不執行composer更新

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

重設所有範例資料模組以重新安裝


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

停用管理員使用者忘記密碼表單的reCAPTCHA


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

停用管理員使用者登入表單的reCAPTCHA


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

設定用於產生Google OTP的密碼。



### `user`

使用者名稱

- 必填

### `secret`

密碼

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

列出所有可用的提供者


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

重設一位使用者的設定



### `user`

使用者名稱

- 必填

### `provider`

提供者代碼

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

執行應用程式伺服器


### `--port`，`-p`

伺服器連線埠

- 預設： `9501`
- 接受值

### `--background`，`-b`

背景模式旗標

- 預設： `0`
- 接受值

### `--workerNum`，`-wn`

要啟動的工作者處理序數目

- 預設： `4`
- 接受值

### `--dispatchMode`，`-dm`

將連線分派到工作者處理序的模式

- 預設： `3`
- 接受值

### `--maxRequests`，`-mr`

工作者處理序重新啟動前的最大要求數

- 預設： `10000`
- 接受值

### `--area`，`-a`

應用程式伺服器區域

- 預設： `graphql`
- 接受值

### `--magento-init-params`，`-mip`

magento bootstrap初始引數

- 預設： &quot;
- 接受值

### `--maxWaitTime`，`-mwt`

重新載入後等候背景工作程式的時間長度(例如 設定變更)，然後將其刪除

- 預設： `3600`
- 接受值

### `--state-monitor`

啟用狀態監視。 僅用於偵錯狀態問題！

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

ApplicationServer狀態監視器的彙總輸出


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

備份Magento應用程式程式碼基底、媒體和資料庫


### `--code`

進行程式碼和組態檔備份（不包括暫存檔案）

- 預設： `false`
- 不接受值

### `--media`

進行媒體備份

- 預設： `false`
- 不接受值

### `--db`

進行完整的資料庫備份

- 預設： `false`
- 不接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:config:set`

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

建立或修改部署設定


### `--enable-debug-logging`

啟用偵錯記錄

- 需要值

### `--enable-syslog-logging`

啟用Syslog記錄

- 需要值

### `--backend-frontname`

後端前端名稱（如果遺失，則會自動產生）

- 需要值

### `--remote-storage-driver`

遠端儲存驅動程式

- 需要值

### `--remote-storage-prefix`

遠端儲存首碼

- 預設： &quot;
- 需要值

### `--remote-storage-endpoint`

遠端儲存端點

- 需要值

### `--remote-storage-bucket`

遠端儲存貯體

- 需要值

### `--remote-storage-region`

遠端儲存區域

- 需要值

### `--remote-storage-key`

遠端儲存存取金鑰

- 預設： &quot;
- 需要值

### `--remote-storage-secret`

遠端儲存秘密金鑰

- 預設： &quot;
- 需要值

### `--remote-storage-path-style`

遠端儲存路徑樣式

- 預設： `0`
- 需要值

### `--id_salt`

graphql Salt

- 需要值

### `--config-async`

啟用非同步管理設定儲存？ 1 — 是，0 — 否

- 需要值

### `--checkout-async`

啟用非同步訂單處理？ 1 — 是，0 — 否

- 需要值

### `--amqp-host`

Amqp伺服器主機

- 預設： &quot;
- 需要值

### `--amqp-port`

Amqp伺服器連線埠

- 預設： `5672`
- 需要值

### `--amqp-user`

Amqp伺服器使用者名稱

- 預設： &quot;
- 需要值

### `--amqp-password`

Amqp伺服器密碼

- 預設： &quot;
- 需要值

### `--amqp-virtualhost`

Amqp virtualhost

- 預設： `/`
- 需要值

### `--amqp-ssl`

Amqp SSL

- 預設： &quot;
- 需要值

### `--amqp-ssl-options`

Amqp SSL選項(JSON)

- 預設： &quot;
- 需要值

### `--consumers-wait-for-messages`

消費者是否應該等候佇列中的訊息？ 1 — 是，0 — 否

- 需要值

### `--queue-default-connection`

訊息佇列預設連線。 可以是&#39;db&#39;、&#39;amqp&#39;或自訂佇列系統。必須安裝並設定佇列系統，否則將無法正確處理訊息。

- 需要值

### `--deferred-total-calculating`

啟用延後總計計算？ 1 — 是，0 — 否

- 需要值

### `--key`

加密金鑰

- 需要值

### `--db-host`

資料庫伺服器主機

- 需要值

### `--db-name`

資料庫名稱

- 需要值

### `--db-user`

資料庫伺服器使用者名稱

- 需要值

### `--db-engine`

資料庫伺服器引擎

- 需要值

### `--db-password`

資料庫伺服器密碼

- 需要值

### `--db-prefix`

資料庫表格前置詞

- 需要值

### `--db-model`

資料庫型別

- 需要值

### `--db-init-statements`

資料庫初始命令集

- 需要值

### `--skip-db-validation`，`-s`

若指定，則會略過資料庫連線驗證

- 預設： `false`
- 不接受值

### `--http-cache-hosts`

http快取主機

- 需要值

### `--db-ssl-key`

使用者端金鑰檔案的完整路徑，以透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

### `--db-ssl-cert`

使用者端憑證檔案的完整路徑，以便透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

### `--db-ssl-ca`

伺服器憑證檔案的完整路徑，以透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

### `--db-ssl-verify`

驗證伺服器認證

- 預設： `false`
- 不接受值

### `--session-save`

工作階段儲存處理常式

- 需要值

### `--session-save-redis-host`

使用UNIX通訊端時完整的主機名稱、IP位址或絕對路徑

- 需要值

### `--session-save-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--session-save-redis-password`

Redis伺服器密碼

- 需要值

### `--session-save-redis-timeout`

連線逾時（以秒為單位）

- 需要值

### `--session-save-redis-persistent-id`

啟用持續連線的唯一字串

- 需要值

### `--session-save-redis-db`

Redis資料庫編號

- 需要值

### `--session-save-redis-compression-threshold`

Redis壓縮臨界值

- 需要值

### `--session-save-redis-compression-lib`

Redis壓縮程式庫。 值： gzip （預設）、lzf、lz4、snappy

- 需要值

### `--session-save-redis-log-level`

Redis記錄層級。 值： 0 （最少詳細）至7 （最詳細）

- 需要值

### `--session-save-redis-max-concurrency`

可等候鎖定一個工作階段的最大處理序數目

- 需要值

### `--session-save-redis-break-after-frontend`

嘗試中斷前端工作階段鎖定之前要等待的秒數

- 需要值

### `--session-save-redis-break-after-adminhtml`

嘗試解除管理員工作階段鎖定之前的等待秒數

- 需要值

### `--session-save-redis-first-lifetime`

非機器人第一次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

### `--session-save-redis-bot-first-lifetime`

機器人首次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

### `--session-save-redis-bot-lifetime`

機器人後續寫入的工作階段期限（使用0可停用）

- 需要值

### `--session-save-redis-disable-locking`

Redis會停用鎖定。 值： false （預設）， true

- 需要值

### `--session-save-redis-min-lifetime`

Redis最小工作階段存留期（以秒為單位）

- 需要值

### `--session-save-redis-max-lifetime`

Redis最長工作階段存留期（以秒為單位）

- 需要值

### `--session-save-redis-sentinel-master`

Redis Sentinel主版

- 需要值

### `--session-save-redis-sentinel-servers`

Redis Sentinel伺服器，以逗號分隔

- 需要值

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主版。 值： false （預設）， true

- 需要值

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連線重試。

- 需要值

### `--cache-backend`

預設快取處理常式

- 需要值

### `--cache-backend-redis-server`

Redis伺服器

- 需要值

### `--cache-backend-redis-db`

快取的資料庫編號

- 需要值

### `--cache-backend-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--cache-backend-redis-password`

Redis伺服器密碼

- 需要值

### `--cache-backend-redis-compress-data`

設為0可停用壓縮（預設為1，已啟用）

- 需要值

### `--cache-backend-redis-compression-lib`

壓縮程式庫使用[snappy，lzf，l4z，zstd，gzip] （留空將自動決定）

- 需要值

### `--cache-backend-redis-use-lua`

設為1以啟用lua （預設為0，已停用）

- 需要值

### `--cache-id-prefix`

快取金鑰的ID首碼

- 需要值

### `--allow-parallel-generation`

允許以非封鎖方式產生快取

- 預設： `false`
- 不接受值

### `--page-cache`

預設快取處理常式

- 需要值

### `--page-cache-redis-server`

Redis伺服器

- 需要值

### `--page-cache-redis-db`

快取的資料庫編號

- 需要值

### `--page-cache-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--page-cache-redis-password`

Redis伺服器密碼

- 需要值

### `--page-cache-redis-compress-data`

設為1可壓縮整頁快取（使用0可停用）

- 需要值

### `--page-cache-redis-compression-lib`

使用[snappy，lzf，l4z，zstd，gzip]的壓縮程式庫（留空將自動決定）

- 需要值

### `--page-cache-id-prefix`

快取金鑰的ID首碼

- 需要值

### `--lock-provider`

鎖定提供者名稱

- 需要值

### `--lock-db-prefix`

安裝特定的鎖定首碼以避免鎖定衝突

- 需要值

### `--lock-zookeeper-host`

要連線至Zookeeper叢集的主機與連線埠。 例如： 127.0.0.1:2181

- 需要值

### `--lock-zookeeper-path`

Zookeeper儲存鎖定的路徑。 預設路徑為： /magento/locks

- 需要值

### `--lock-file-path`

儲存檔案鎖定的路徑。

- 需要值

### `--document-root-is-pub`

要顯示的旗標為Pub位於根目錄，只能為true或false

- 需要值

### `--backpressure-logger`

背壓記錄器處理常式

- 需要值

### `--backpressure-logger-redis-server`

Redis伺服器

- 需要值

### `--backpressure-logger-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--backpressure-logger-redis-timeout`

Redis伺服器逾時

- 需要值

### `--backpressure-logger-redis-persistent`

Redis永久

- 需要值

### `--backpressure-logger-redis-db`

Redis db編號

- 需要值

### `--backpressure-logger-redis-password`

Redis伺服器密碼

- 需要值

### `--backpressure-logger-redis-user`

Redis伺服器使用者

- 需要值

### `--backpressure-logger-id-prefix`

金鑰的ID首碼

- 需要值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

在資料庫中安裝和升級資料


### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

產生修補程式並將其放在特定資料夾中。



### `module`

模組名稱

- 必填

### `patch`

修補程式名稱

- 必填

### `--revertable`

檢查修補程式是否可回覆。

- 預設： `false`
- 接受值

### `--type`

找出應產生的修補程式型別。 可用值： `data`， `schema`。

- 預設： `data`
- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

產生允許宣告安裝程式編輯的表格和欄的白名單


### `--module-name`

產生白名單的模組名稱

- 預設： `all`
- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

將簽出引號相關表格移至個別的DB伺服器


### `--host`

從屬DB伺服器主機

- 預設： `localhost`
- 需要值

### `--dbname`

從屬資料庫名稱

- 需要值

### `--username`

從屬資料庫使用者名稱

- 預設： `root`
- 需要值

### `--password`

從屬資料庫使用者密碼

- 接受值

### `--connection`

從屬連線名稱

- 預設： `default`
- 接受值

### `--resource`

從屬資源名稱

- 預設： `default`
- 接受值

### `--maxAllowedLag`

允許的延遲從屬連線上限（以秒為單位）

- 預設： &quot;
- 接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

將簽出引號相關表格移至個別的DB伺服器。 自2.4.2起已棄用，將移除


### `--host`

簽出DB伺服器主機

- 需要值

### `--dbname`

簽出資料庫名稱

- 需要值

### `--username`

簽出DB使用者名稱

- 需要值

### `--password`

簽出資料庫使用者密碼

- 接受值

### `--connection`

簽出連線名稱

- 預設： `checkout`
- 接受值

### `--resource`

簽出資源名稱

- 預設： `checkout`
- 接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

將銷售相關資料表移至個別的DB伺服器。 自2.4.2起已棄用，將移除


### `--host`

銷售資料庫伺服器主機

- 需要值

### `--dbname`

銷售資料庫名稱

- 需要值

### `--username`

銷售資料庫使用者名稱

- 需要值

### `--password`

銷售資料庫使用者密碼

- 接受值

### `--connection`

銷售連線名稱

- 預設： `sales`
- 接受值

### `--resource`

銷售資源名稱

- 預設： `sales`
- 接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

安裝及升級資料庫結構描述


### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式

- 預設： `false`
- 接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

檢查資料庫結構描述或資料是否需要升級


### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

產生DI組態以及所有可自動產生的遺漏類別


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:install`

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

安裝Magento應用程式


### `--enable-debug-logging`

啟用偵錯記錄

- 需要值

### `--enable-syslog-logging`

啟用Syslog記錄

- 需要值

### `--backend-frontname`

後端前端名稱（如果遺失，則會自動產生）

- 需要值

### `--remote-storage-driver`

遠端儲存驅動程式

- 需要值

### `--remote-storage-prefix`

遠端儲存首碼

- 預設： &quot;
- 需要值

### `--remote-storage-endpoint`

遠端儲存端點

- 需要值

### `--remote-storage-bucket`

遠端儲存貯體

- 需要值

### `--remote-storage-region`

遠端儲存區域

- 需要值

### `--remote-storage-key`

遠端儲存存取金鑰

- 預設： &quot;
- 需要值

### `--remote-storage-secret`

遠端儲存秘密金鑰

- 預設： &quot;
- 需要值

### `--remote-storage-path-style`

遠端儲存路徑樣式

- 預設： `0`
- 需要值

### `--id_salt`

graphql Salt

- 需要值

### `--config-async`

啟用非同步管理設定儲存？ 1 — 是，0 — 否

- 需要值

### `--checkout-async`

啟用非同步訂單處理？ 1 — 是，0 — 否

- 需要值

### `--amqp-host`

Amqp伺服器主機

- 預設： &quot;
- 需要值

### `--amqp-port`

Amqp伺服器連線埠

- 預設： `5672`
- 需要值

### `--amqp-user`

Amqp伺服器使用者名稱

- 預設： &quot;
- 需要值

### `--amqp-password`

Amqp伺服器密碼

- 預設： &quot;
- 需要值

### `--amqp-virtualhost`

Amqp virtualhost

- 預設： `/`
- 需要值

### `--amqp-ssl`

Amqp SSL

- 預設： &quot;
- 需要值

### `--amqp-ssl-options`

Amqp SSL選項(JSON)

- 預設： &quot;
- 需要值

### `--consumers-wait-for-messages`

消費者是否應該等候佇列中的訊息？ 1 — 是，0 — 否

- 需要值

### `--queue-default-connection`

訊息佇列預設連線。 可以是&#39;db&#39;、&#39;amqp&#39;或自訂佇列系統。必須安裝並設定佇列系統，否則將無法正確處理訊息。

- 需要值

### `--deferred-total-calculating`

啟用延後總計計算？ 1 — 是，0 — 否

- 需要值

### `--key`

加密金鑰

- 需要值

### `--db-host`

資料庫伺服器主機

- 需要值

### `--db-name`

資料庫名稱

- 需要值

### `--db-user`

資料庫伺服器使用者名稱

- 需要值

### `--db-engine`

資料庫伺服器引擎

- 需要值

### `--db-password`

資料庫伺服器密碼

- 需要值

### `--db-prefix`

資料庫表格前置詞

- 需要值

### `--db-model`

資料庫型別

- 需要值

### `--db-init-statements`

資料庫初始命令集

- 需要值

### `--skip-db-validation`，`-s`

若指定，則會略過資料庫連線驗證

- 預設： `false`
- 不接受值

### `--http-cache-hosts`

http快取主機

- 需要值

### `--db-ssl-key`

使用者端金鑰檔案的完整路徑，以透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

### `--db-ssl-cert`

使用者端憑證檔案的完整路徑，以便透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

### `--db-ssl-ca`

伺服器憑證檔案的完整路徑，以透過SSL建立資料庫連線

- 預設： &quot;
- 需要值

### `--db-ssl-verify`

驗證伺服器認證

- 預設： `false`
- 不接受值

### `--session-save`

工作階段儲存處理常式

- 需要值

### `--session-save-redis-host`

使用UNIX通訊端時完整的主機名稱、IP位址或絕對路徑

- 需要值

### `--session-save-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--session-save-redis-password`

Redis伺服器密碼

- 需要值

### `--session-save-redis-timeout`

連線逾時（以秒為單位）

- 需要值

### `--session-save-redis-persistent-id`

啟用持續連線的唯一字串

- 需要值

### `--session-save-redis-db`

Redis資料庫編號

- 需要值

### `--session-save-redis-compression-threshold`

Redis壓縮臨界值

- 需要值

### `--session-save-redis-compression-lib`

Redis壓縮程式庫。 值： gzip （預設）、lzf、lz4、snappy

- 需要值

### `--session-save-redis-log-level`

Redis記錄層級。 值： 0 （最少詳細）至7 （最詳細）

- 需要值

### `--session-save-redis-max-concurrency`

可等候鎖定一個工作階段的最大處理序數目

- 需要值

### `--session-save-redis-break-after-frontend`

嘗試中斷前端工作階段鎖定之前要等待的秒數

- 需要值

### `--session-save-redis-break-after-adminhtml`

嘗試解除管理員工作階段鎖定之前的等待秒數

- 需要值

### `--session-save-redis-first-lifetime`

非機器人第一次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

### `--session-save-redis-bot-first-lifetime`

機器人首次寫入工作階段的期限（以秒為單位） （使用0可停用）

- 需要值

### `--session-save-redis-bot-lifetime`

機器人後續寫入的工作階段期限（使用0可停用）

- 需要值

### `--session-save-redis-disable-locking`

Redis會停用鎖定。 值： false （預設）， true

- 需要值

### `--session-save-redis-min-lifetime`

Redis最小工作階段存留期（以秒為單位）

- 需要值

### `--session-save-redis-max-lifetime`

Redis最長工作階段存留期（以秒為單位）

- 需要值

### `--session-save-redis-sentinel-master`

Redis Sentinel主版

- 需要值

### `--session-save-redis-sentinel-servers`

Redis Sentinel伺服器，以逗號分隔

- 需要值

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主版。 值： false （預設）， true

- 需要值

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連線重試。

- 需要值

### `--cache-backend`

預設快取處理常式

- 需要值

### `--cache-backend-redis-server`

Redis伺服器

- 需要值

### `--cache-backend-redis-db`

快取的資料庫編號

- 需要值

### `--cache-backend-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--cache-backend-redis-password`

Redis伺服器密碼

- 需要值

### `--cache-backend-redis-compress-data`

設為0可停用壓縮（預設為1，已啟用）

- 需要值

### `--cache-backend-redis-compression-lib`

壓縮程式庫使用[snappy，lzf，l4z，zstd，gzip] （留空將自動決定）

- 需要值

### `--cache-backend-redis-use-lua`

設為1以啟用lua （預設為0，已停用）

- 需要值

### `--cache-id-prefix`

快取金鑰的ID首碼

- 需要值

### `--allow-parallel-generation`

允許以非封鎖方式產生快取

- 預設： `false`
- 不接受值

### `--page-cache`

預設快取處理常式

- 需要值

### `--page-cache-redis-server`

Redis伺服器

- 需要值

### `--page-cache-redis-db`

快取的資料庫編號

- 需要值

### `--page-cache-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--page-cache-redis-password`

Redis伺服器密碼

- 需要值

### `--page-cache-redis-compress-data`

設為1可壓縮整頁快取（使用0可停用）

- 需要值

### `--page-cache-redis-compression-lib`

使用[snappy，lzf，l4z，zstd，gzip]的壓縮程式庫（留空將自動決定）

- 需要值

### `--page-cache-id-prefix`

快取金鑰的ID首碼

- 需要值

### `--lock-provider`

鎖定提供者名稱

- 需要值

### `--lock-db-prefix`

安裝特定的鎖定首碼以避免鎖定衝突

- 需要值

### `--lock-zookeeper-host`

要連線至Zookeeper叢集的主機與連線埠。 例如： 127.0.0.1:2181

- 需要值

### `--lock-zookeeper-path`

Zookeeper儲存鎖定的路徑。 預設路徑為： /magento/locks

- 需要值

### `--lock-file-path`

儲存檔案鎖定的路徑。

- 需要值

### `--document-root-is-pub`

要顯示的旗標為Pub位於根目錄，只能為true或false

- 需要值

### `--backpressure-logger`

背壓記錄器處理常式

- 需要值

### `--backpressure-logger-redis-server`

Redis伺服器

- 需要值

### `--backpressure-logger-redis-port`

Redis伺服器接聽連線埠

- 需要值

### `--backpressure-logger-redis-timeout`

Redis伺服器逾時

- 需要值

### `--backpressure-logger-redis-persistent`

Redis永久

- 需要值

### `--backpressure-logger-redis-db`

Redis db編號

- 需要值

### `--backpressure-logger-redis-password`

Redis伺服器密碼

- 需要值

### `--backpressure-logger-redis-user`

Redis伺服器使用者

- 需要值

### `--backpressure-logger-id-prefix`

金鑰的ID首碼

- 需要值

### `--base-url`

商店的URL預計可在。 已棄用，請使用config：set以及路徑web/unsecure/base_url

- 需要值

### `--language`

預設語言代碼。 已棄用，請使用config：set搭配路徑general/locale/code

- 需要值

### `--timezone`

預設時區代碼。 已棄用，請使用config：set搭配路徑general/locale/timezone

- 需要值

### `--currency`

預設貨幣代碼。 已棄用，請使用config：set以及路徑currency/options/base、currency/options/default和currency/options/allow

- 需要值

### `--use-rewrites`

使用rewrites。 已棄用，請使用config：set搭配路徑web/seo/use_rewrites

- 需要值

### `--use-secure`

使用安全URL。 只有在SSL可用時才啟用此選項。 已棄用，將config：set與路徑web/secure/use_in_frontend一起使用

- 需要值

### `--base-url-secure`

SSL連線的基礎URL。 已棄用，請使用config：set搭配路徑web/secure/base_url

- 需要值

### `--use-secure-admin`

使用SSL執行管理介面。 已棄用，請使用config：set搭配路徑web/secure/use_in_adminhtml

- 需要值

### `--admin-use-security-key`

是否在Magento管理員URL和表單中使用「安全性金鑰」功能。 已棄用，請使用config：set以及路徑admin/security/use_form_key

- 需要值

### `--admin-user`

管理員使用者

- 接受值

### `--admin-password`

管理員密碼

- 接受值

### `--admin-email`

管理員電子郵件

- 接受值

### `--admin-firstname`

管理員名字

- 接受值

### `--admin-lastname`

管理員姓氏

- 接受值

### `--search-engine`

搜尋引擎。 值： elasticsearch7， elasticsearch8， opensearch

- 需要值

### `--elasticsearch-host`

Elasticsearch伺服器主機。

- 需要值

### `--elasticsearch-port`

Elasticsearch的伺服器連線埠。

- 需要值

### `--elasticsearch-enable-auth`

設為1以啟用驗證。 （預設為0，已停用）

- 需要值

### `--elasticsearch-username`

使用者名稱Elasticsearch。 僅在啟用HTTP驗證時適用

- 需要值

### `--elasticsearch-password`

密碼Elasticsearch。 僅在啟用HTTP驗證時適用

- 需要值

### `--elasticsearch-index-prefix`

索引首碼Elasticsearch。

- 需要值

### `--elasticsearch-timeout`

Elasticsearch伺服器逾時。

- 需要值

### `--opensearch-host`

OpenSearch伺服器主機。

- 需要值

### `--opensearch-port`

OpenSearch伺服器連線埠。

- 需要值

### `--opensearch-enable-auth`

設為1以啟用驗證。 （預設為0，已停用）

- 需要值

### `--opensearch-username`

OpenSearch使用者名稱。 僅在啟用HTTP驗證時適用

- 需要值

### `--opensearch-password`

OpenSearch密碼。 僅在啟用HTTP驗證時適用

- 需要值

### `--opensearch-index-prefix`

OpenSearch索引前置詞。

- 需要值

### `--opensearch-timeout`

OpenSearch伺服器逾時。

- 需要值

### `--cleanup-database`

安裝前先清理資料庫

- 預設： `false`
- 不接受值

### `--sales-order-increment-prefix`

銷售訂單編號前置詞

- 需要值

### `--use-sample-data`

使用範例資料

- 預設： `false`
- 不接受值

### `--enable-modules`

逗號分隔模組名稱清單。 安裝期間必須包括此專案。 可用的魔術引數「all」。

- 接受值

### `--disable-modules`

逗號分隔模組名稱清單。 安裝期間必須避免此情況。 可用的魔術引數「all」。

- 接受值

### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式

- 預設： `false`
- 接受值

### `--interactive`，`-i`

互動式Magento安裝

- 預設： `false`
- 不接受值

### `--safe-mode`

在破壞性作業（例如移除欄）上安全安裝包含傾印的Magento

- 接受值

### `--data-restore`

從傾印還原移除的資料

- 接受值

### `--dry-run`

Magento安裝將以試執行模式執行

- 預設： `false`
- 接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

產生夾具



### `profile`

設定檔設定檔的路徑

- 必填

### `--skip-reindex`，`-s`

略過重新索引

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

回覆Magento應用程式程式碼基底、媒體及資料庫


### `--code-file`，`-c`

var/backups中程式碼備份檔案的基本名稱

- 需要值

### `--media-file`，`-m`

var/backups中媒體備份檔案的基本名稱

- 需要值

### `--db-file`，`-d`

var/backups中db備份檔案的基本名稱

- 需要值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

部署靜態檢視檔案



### `languages`

要輸出靜態檢視檔案的ISO-639語言代碼清單（以空格分隔）。

- 預設： `[]`

- 陣列

### `--force`，`-f`

以任何模式部署檔案。

- 預設： `false`
- 不接受值

### `--strategy`，`-s`

使用指定的策略部署檔案。

- 預設： `quick`
- 接受值

### `--area`，`-a`

只產生指定區域的檔案。

- 預設： `all`
- 接受多個值

### `--exclude-area`

不要產生指定區域的檔案。

- 預設： `none`
- 接受多個值

### `--theme`，`-t`

只為指定的主題產生靜態檢視檔案。

- 預設： `all`
- 接受多個值

### `--exclude-theme`

不要產生指定主題的檔案。

- 預設： `none`
- 接受多個值

### `--language`，`-l`

只產生指定語言的檔案。

- 預設： `all`
- 接受多個值

### `--exclude-language`

不要產生指定語言的檔案。

- 預設： `none`
- 接受多個值

### `--jobs`，`-j`

使用指定的作業數目啟用平行處理。

- 預設： `0`
- 接受值

### `--max-execution-time`

部署靜態處理序的最大預期執行時間（以秒為單位）。

- 預設： `900`
- 接受值

### `--symlink-locale`

為這些區域設定的檔案建立符號連結，這些檔案會傳遞以進行部署，但沒有自訂。

- 預設： `false`
- 不接受值

### `--content-version`

如果在多個節點上執行部署，則可以使用靜態內容的自訂版本，以確保靜態內容版本相同且快取可正常運作。

- 需要值

### `--refresh-content-version-only`

重新整理靜態內容的版本只能用於重新整理瀏覽器快取和CDN快取中的靜態內容。

- 預設： `false`
- 不接受值

### `--no-javascript`

請勿部署JavaScript檔案。

- 預設： `false`
- 不接受值

### `--no-js-bundle`

請勿部署JavaScript套件組合檔案。

- 預設： `false`
- 不接受值

### `--no-css`

請勿部署CSS檔案。

- 預設： `false`
- 不接受值

### `--no-less`

請勿部署LESS檔案。

- 預設： `false`
- 不接受值

### `--no-images`

請勿部署影像。

- 預設： `false`
- 不接受值

### `--no-fonts`

不要部署字型檔案。

- 預設： `false`
- 不接受值

### `--no-html`

請勿部署HTML檔案。

- 預設： `false`
- 不接受值

### `--no-misc`

請勿部署其他型別的檔案（.md、.jbf、.csv等）。

- 預設： `false`
- 不接受值

### `--no-html-minify`

請勿縮制HTML檔案。

- 預設： `false`
- 不接受值

### `--no-parent`

請勿編譯父系主題。 僅在快速和標準策略中支援。

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

安裝存放區設定。 自2.2.0版起已棄用。請改用config：set


### `--base-url`

商店的URL預計可在。 已棄用，請使用config：set以及路徑web/unsecure/base_url

- 需要值

### `--language`

預設語言代碼。 已棄用，請使用config：set搭配路徑general/locale/code

- 需要值

### `--timezone`

預設時區代碼。 已棄用，請使用config：set搭配路徑general/locale/timezone

- 需要值

### `--currency`

預設貨幣代碼。 已棄用，請使用config：set以及路徑currency/options/base、currency/options/default和currency/options/allow

- 需要值

### `--use-rewrites`

使用rewrites。 已棄用，請使用config：set搭配路徑web/seo/use_rewrites

- 需要值

### `--use-secure`

使用安全URL。 只有在SSL可用時才啟用此選項。 已棄用，將config：set與路徑web/secure/use_in_frontend一起使用

- 需要值

### `--base-url-secure`

SSL連線的基礎URL。 已棄用，請使用config：set搭配路徑web/secure/base_url

- 需要值

### `--use-secure-admin`

使用SSL執行管理介面。 已棄用，請使用config：set搭配路徑web/secure/use_in_adminhtml

- 需要值

### `--admin-use-security-key`

是否在Magento管理員URL和表單中使用「安全性金鑰」功能。 已棄用，請使用config：set以及路徑admin/security/use_form_key

- 需要值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

解除安裝Magento應用程式


### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

升級Magento應用程式、資料庫資料和結構描述


### `--keep-generated`

防止刪除產生的檔案。 我們不鼓勵使用此選項，除非是部署至生產環境。 請洽詢您的系統整合商或管理員，以取得更多資訊。

- 預設： `false`
- 不接受值

### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式

- 預設： `false`
- 接受值

### `--safe-mode`

在破壞性作業（例如移除欄）上安全安裝包含傾印的Magento

- 接受值

### `--data-restore`

從傾印還原移除的資料

- 接受值

### `--dry-run`

Magento安裝將以試執行模式執行

- 預設： `false`
- 接受值

### `--magento-init-params`

新增至任何命令以自訂Magento初始化引數，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `store:list`

```bash
bin/magento store:list
```

顯示商店清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `store:website:list`

```bash
bin/magento store:website:list
```

顯示網站清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

建立程式碼備份


### `--name`

傾印名稱

- 接受值

### `--output`，`-o`

輸出路徑

- 接受值

### `--logs`，`-l`

包含記錄

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

建立資料庫備份


### `--name`

傾印名稱

- 接受值

### `--output`，`-o`

輸出路徑

- 接受值

### `--logs`，`-l`

包含記錄

- 預設： `false`
- 不接受值

### `--ignore-sanitize`，`-i`

忽略處理

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

檢查所需的備份公用程式


### `--hide-paths`

僅檢查所需的主控台公用程式

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

建立公用程式路徑清單


### `--force`，`-f`

強制

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

解除安裝主題



### `theme`

佈景主題的路徑。 主題路徑應指定為完整路徑，即area/vendor/name。 例如，前端/Magento/空白

- 預設： `[]`

- 必填
- 陣列

### `--backup-code`

進行程式碼備份（不包括暫存檔案）

- 預設： `false`
- 不接受值

### `--clear-static-content`，`-c`

清除產生的靜態檢視檔案。

- 預設： `false`
- 不接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

產生清漆VCL並將其回溯至命令列


### `--access-list`

可以清除清漆的IP存取清單

- 預設： `localhost`
- 需要值

### `--backend-host`

Web後端的主機

- 預設： `localhost`
- 需要值

### `--backend-port`

Web後端的連線埠

- 預設： `8080`
- 需要值

### `--export-version`

清漆檔案的版本

- 預設： `6`
- 需要值

### `--grace-period`

寬限期（以秒為單位）

- 預設： `300`
- 需要值

### `--input-file`

要從中產生vcl的輸入檔案

- 需要值

### `--output-file`

要寫入vcl的檔案路徑

- 需要值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

執行註冊的webhook以進行開發。



### `name`

Webhook名稱

- 必填

### `payload`

JSON格式的webhook裝載

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

根據webhook註冊產生外掛程式


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

傳回指定webhook的裝載。



### `webhook-name`

Webhook方法名稱

- 必填

### `webhook-type`

Webhook型別（前、後）

- 預設： `before`


### `--depth`

要傳回的webhook承載中的層數

- 預設： `3`
- 接受值

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `webhooks:list`

```bash
bin/magento webhooks:list
```

顯示已訂閱Webhook的清單


### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

傳回指定模組支援的webhook方法名稱清單



### `module_name`

模組名稱

- 必填

### `--help`，`-h`

顯示指定指令的說明。 當沒有指定命令時，顯示清單命令的說明

- 預設： `false`
- 不接受值

### `--quiet`，`-q`

不輸出任何訊息

- 預設： `false`
- 不接受值

### `--verbose`，`-v|-vv|-vvv`

增加訊息的詳細程度：1代表一般輸出，2代表較詳細輸出，3代表偵錯

- 預設： `false`
- 不接受值

### `--version`，`-V`

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

### `--no-interaction`，`-n`

請勿詢問任何互動式問題

- 預設： `false`
- 不接受值
