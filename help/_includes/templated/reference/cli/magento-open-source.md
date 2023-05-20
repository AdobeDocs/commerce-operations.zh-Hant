---
source-git-commit: a1f99f839f11ab42356b87a69398999bb03cd544
workflow-type: tm+mt
source-wordcount: '17238'
ht-degree: 0%

---
# 賓/馬根托(Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**:2.4.6

此引用包含114個通過 `bin/magento` 命令行工具。
初始清單是使用 `bin/magento list` 的上界。
使用 [&quot;添加CLI命令&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) 的子菜單。

>[!NOTE]
>
>你可以打電話 `bin/magento` CLI命令使用快捷方式而不是完整命令名。 例如，您可以 `bin/magento setup:upgrade` 使用 `bin/magento s:up`。 `bin/magento s:upg`。 請參閱 [快捷方式語法](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) 瞭解如何將快捷方式與任何CLI命令一起使用。

>[!NOTE]
>
>此引用是從應用程式碼庫生成的。 要更改內容，可以在中更新相應命令實現的原始碼 [雞](https://github.com/magento) 並提交更改以供審閱。 另一種方法是 _給我們反饋_ （查找右上方的連結）。 有關繳款指南，請參閱 [代碼貢獻](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)。

## `_complete`

提供外殼完成建議的內部命令

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

shell類型(「bash」)

- 需要值

### `--input`, `-i`

輸入令牌的陣列（例如COMP_WORDS或argv）

- 預設值： `[]`
- 需要值

### `--current`, `-c`

游標所在的&quot;input&quot;陣列的索引（例如COMP_CWORD）

- 需要值

### `--symfony`, `-S`

完成指令碼的版本

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `completion`

轉儲shell完成指令碼

```bash
bin/magento completion [--debug] [--] [<shell>]
```


### `shell`

殼類型(例如&quot;bash&quot;)，如果未給定&quot;$SHELL&quot; env var的值，則將使用該值


### `--debug`

尾隨完成調試日誌

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `help`

顯示命令的幫助

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `list`

清單命令

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


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

### `--short`

跳過描述命令的參數

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `admin:adobe-ims:disable`

禁用Adobe IMS模組

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `admin:adobe-ims:enable`

啟用Adobe IMS模組。

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

為Adobe IMS配置設定組織ID。 啟用模組時需要

- 接受值

### `--client-id`, `-c`

為Adobe IMS配置設定客戶端ID。 啟用模組時需要

- 接受值

### `--client-secret`, `-s`

為Adobe IMS配置設定客戶端密碼。 啟用模組時需要

- 接受值

### `--2fa`, `-t`

檢查是否為Adobe Admin Console的組織啟用了2FA。 啟用模組時需要

- 接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `admin:adobe-ims:info`

Adobe IMS模組配置資訊

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `admin:adobe-ims:status`

Adobe IMS模組的狀態

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `admin:user:create`

建立管理員

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

（必需）管理員用戶

- 需要值

### `--admin-password`

（必需）管理員密碼

- 需要值

### `--admin-email`

（必需）管理員電子郵件

- 需要值

### `--admin-firstname`

（必需）管理員名

- 需要值

### `--admin-lastname`

（必需）管理員姓

- 需要值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `admin:user:unlock`

解鎖管理員帳戶

```bash
bin/magento admin:user:unlock <username>
```


### `username`

要解除鎖定的管理員用戶名

- 必需

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `app:config:dump`

建立應用程式轉儲

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

以空格分隔的配置類型清單或省略以轉儲所有 [範圍，系統，主題，i18n]

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `app:config:import`

將資料從共用配置檔案導入相應的資料儲存

```bash
bin/magento app:config:import
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `app:config:status`

檢查配置傳播是否需要更新

```bash
bin/magento app:config:status
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `braintree:migrate`

從Magento1資料庫遷移儲存的卡

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

主機名/IP。 埠是可選的

- 需要值

### `--dbname`

資料庫名稱

- 需要值

### `--username`

資料庫用戶名。 必須具有讀取訪問權限

- 需要值

### `--password`

密碼

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cache:clean`

清除快取類型

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的快取類型清單或省略以應用於所有快取類型。

- 預設值： `[]`

- 陣列

### `--bootstrap`

添加或覆蓋引導的參數

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cache:disable`

禁用快取類型

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的快取類型清單或省略以應用於所有快取類型。

- 預設值： `[]`

- 陣列

### `--bootstrap`

添加或覆蓋引導的參數

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cache:enable`

啟用快取類型

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的快取類型清單或省略以應用於所有快取類型。

- 預設值： `[]`

- 陣列

### `--bootstrap`

添加或覆蓋引導的參數

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cache:flush`

刷新快取類型使用的快取儲存

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的快取類型清單或省略以應用於所有快取類型。

- 預設值： `[]`

- 陣列

### `--bootstrap`

添加或覆蓋引導的參數

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cache:status`

檢查快取狀態

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

添加或覆蓋引導的參數

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `catalog:images:resize`

建立調整大小的產品映像

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

以非同步模式調整影像大小

- 預設值： `false`
- 不接受值

### `--skip_hidden_images`

不處理標籤為隱藏於產品頁面的影像

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `catalog:product:attributes:cleanup`

刪除未使用的產品屬性。

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cms:wysiwyg:restrict`

設定是強制用戶HTML內容驗證還是改為顯示警告

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

- 必需

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `config:sensitive:set`

設定敏感配置值

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

配置路徑，例如group/section/field_name


### `value`

配置值


### `--interactive`, `-i`

啟用交互模式以設定所有敏感變數

- 預設值： `false`
- 不接受值

### `--scope`

配置範圍（如果未設定）使用「default」

- 預設值： `default`
- 接受值

### `--scope-code`

配置的作用域代碼，預設為空字串

- 預設值：&quot;
- 接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `config:set`

更改系統配置

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

格式節/group/field_name中的配置路徑

- 必需

### `value`

配置值

- 必需

### `--scope`

配置範圍（預設、網站或儲存）

- 預設值： `default`
- 需要值

### `--scope-code`

作用域代碼（僅當作用域不是「default」時才需要）

- 需要值

### `--lock-env`, `-e`

阻止在Admin中修改的鎖定值(將保存在app/etc/env.php中)

- 預設值： `false`
- 不接受值

### `--lock-config`, `-c`

鎖定值並與其他安裝共用值，阻止在管理員中修改(將保存在app/etc/config.php中)

- 預設值： `false`
- 不接受值

### `--lock`, `-l`

不建議使用 — lock-env選項。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `config:show`

顯示給定路徑的配置值。 如果未指定路徑，則將顯示所有保存的值

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

配置路徑，例如section_id/group_id/field_id


### `--scope`

如果未指定配置範圍，則將使用「default」範圍

- 預設值： `default`
- 接受值

### `--scope-code`

範圍代碼(僅當範圍不是 `default`)

- 預設值：&quot;
- 接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cron:install`

為當前用戶生成並安裝crontab

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

強制安裝任務

- 預設值： `false`
- 不接受值

### `--non-optional`, `-d`

僅安裝非可選（預設）任務

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cron:remove`

從crontab中刪除任務

```bash
bin/magento cron:remove
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `cron:run`

按計畫運行作業

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

### `--group`

僅從指定的組運行作業

- 需要值

### `--bootstrap`

添加或覆蓋引導的參數

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `customer:hash:upgrade`

根據最新算法升級客戶的哈希

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `deploy:mode:set`

設定應用程式模式。

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

要設定的應用程式模式。 可用選項包括「開發人員」或「生產」

- 必需

### `--skip-compilation`, `-s`

跳過靜態內容的清除和再生（生成的代碼、預處理的CSS和pub/static/中的資產）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `deploy:mode:show`

顯示當前應用程式模式。

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:di:info`

提供有關命令的依賴項注入配置的資訊。

```bash
bin/magento dev:di:info <class>
```


### `class`

類名

- 必需

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:email:newsletter-compatibility-check`

掃描新聞稿模板以瞭解潛在的可變使用相容性問題

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:email:override-compatibility-check`

掃描電子郵件模板覆蓋的潛在變數使用相容性問題

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:profiler:disable`

禁用探查器。

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:profiler:enable`

啟用探查器。

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

探查器類型


### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:query-log:disable`

禁用DB查詢記錄

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:query-log:enable`

啟用DB查詢日誌記錄

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

記錄所有查詢。 [真\|假]

- 預設值： `true`
- 接受值

### `--query-time-threshold`

查詢時間閾值。

- 預設值： `0.001`
- 接受值

### `--include-call-stack`

包括調用堆棧。 [真\|假]

- 預設值： `true`
- 接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:source-theme:deploy`

收集和發佈主題的源檔案。

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

要預處理的檔案（應指定檔案，但不應副檔名）

- 預設值： `css/styles-mcss/styles-l`

- 陣列

### `--type`

源檔案類型： [少]

- 預設值： `less`
- 需要值

### `--locale`

區域設定： [en_US]

- 預設值： `en_US`
- 需要值

### `--area`

區域： [前端\\adminhtml]

- 預設值： `frontend`
- 需要值

### `--theme`

主題： [供應商/主題]

- 預設值： `Magento/luma`
- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:template-hints:disable`

禁用前端模板提示。 可能需要快取刷新。

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:template-hints:enable`

啟用前端模板提示。 可能需要快取刷新。

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:template-hints:status`

顯示前端模板提示狀態。

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:tests:run`

運行test

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

要運行的test類型。 可用類型：all，設備，整合， integration，全整合， static, static-all，靜態，完整性， legacy，預設

- 預設值： `default`


### `--arguments`, `-c`

PHPUnit的其他參數。 示例：&quot;-c&#39;-filter=MyTest&#39;&quot;（無空格）

- 預設值：&quot;
- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:urn-catalog:generate`

為IDE生成URN到*.xsd映射的目錄以突出顯示xml。

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

要輸出目錄的檔案路徑。 對於PhpStorm，請使用。idea/misc.xml

- 必需

### `--ide`

將生成目錄的格式。 支援： [風暴，風暴]

- 預設值： `phpstorm`
- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `dev:xml:convert`

使用XSL樣式表轉換XML檔案

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

要轉換的XML檔案的路徑

- 必需

### `processor`

要應用於XML檔案的XSL樣式表的路徑

- 必需

### `--overwrite`, `-o`

覆蓋XML檔案

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `downloadable:domains:add`

將域添加到可下載的域白名單

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

域名

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `downloadable:domains:remove`

從可下載域白名單中刪除域

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

域名

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `downloadable:domains:show`

顯示可下載的域白名單

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `encryption:payment-data:update`

使用最新加密密碼重新加密加密的信用卡資料。

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `i18n:collect-phrases`

發現代碼庫中的短語

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

要分析的目錄路徑。 如果設定了 — magento標誌，則不需要


### `--output`, `-o`

輸出檔案的路徑（包括檔案名）。 未指定檔案時，預設為stdout。

- 需要值

### `--magento`, `-m`

使用 — magento參數來分析當前Magento代碼庫。 如果指定了目錄，則省略參數。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `i18n:pack`

保存語言包

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

包含翻譯的源字典檔案的路徑

- 必需

### `locale`

字典的目標區域設定，例如&quot;de_DE&quot;

- 必需

### `--mode`, `-m`

字典的保存模式 — &quot;replace&quot; — 將語言包替換為新語言包 — &quot;merge&quot; — 合併語言包，預設為&quot;replace&quot;

- 預設值： `replace`
- 需要值

### `--allow-duplicates`, `-d`

使用 — allow-duplicates參數可保存轉換的重複項。 否則，請省略參數。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `i18n:uninstall`

卸載語言包

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

語言包名稱

- 預設值： `[]`

- 必需
- 陣列

### `--backup-code`, `-b`

備份代碼和配置檔案（不包括臨時檔案）

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:info`

顯示允許的索引器

```bash
bin/magento indexer:info
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:reindex`

重新索引資料

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

以空格分隔的索引類型清單或省略以應用於所有索引。

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:reset`

將索引器狀態重置為無效

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

以空格分隔的索引類型清單或省略以應用於所有索引。

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:set-dimensions-mode`

設定索引器Dimension模式

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

索引器名稱 [目錄_產品_價格]


### `mode`

索引器維模式catalog_product_price none,website,customer_group,website_and_customer_group


### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:set-mode`

設定索引模式類型

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

索引器模式類型 [即時|計畫]


### `index`

以空格分隔的索引類型清單或省略以應用於所有索引。

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:show-dimensions-mode`

顯示索引器Dimension模式

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

以空格分隔的索引類型清單或省略以應用於所有索引(catalog_product_price)

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:show-mode`

顯示索引模式

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

以空格分隔的索引類型清單或省略以應用於所有索引。

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `indexer:status`

顯示索引器的狀態

```bash
bin/magento indexer:status [<index>...]
```


### `index`

以空格分隔的索引類型清單或省略以應用於所有索引。

- 預設值： `[]`

- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:adminuri`

顯示Magento管理URI

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:backups:list`

打印可用備份檔案清單

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:currency:list`

顯示可用貨幣清單

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:dependencies:show-framework`

顯示Magento框架的依賴項數

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

報告檔案名

- 預設值： `framework-dependencies.csv`
- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:dependencies:show-modules`

顯示模組之間的依賴關係數

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

報告檔案名

- 預設值： `modules-dependencies.csv`
- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:dependencies:show-modules-circular`

顯示模組之間的循環相關性數

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

報告檔案名

- 預設值： `modules-circular-dependencies.csv`
- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:language:list`

顯示可用語言區域設定的清單

```bash
bin/magento info:language:list
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `info:timezone:list`

顯示可用時區清單

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `inventory:reservation:create-compensations`

通過提供的報酬參數建立保留

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

格式為「」的補償參數清單&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- 預設值： `[]`

- 陣列

### `--raw`, `-r`

原始輸出

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `inventory:reservation:list-inconsistencies`

顯示所有訂單和產品，其可出售數量不一致

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

僅顯示完成訂單的不一致

- 預設值： `false`
- 不接受值

### `--incomplete-orders`, `-i`

僅顯示未完成訂單的不一致

- 預設值： `false`
- 不接受值

### `--bunch-size`, `-b`

定義一次載入的訂單數

- 預設值： `50`
- 接受值

### `--raw`, `-r`

原始輸出

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `inventory-geonames:import`

下載和導入源選擇算法的地理名稱

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

要導入的國家/地區代碼清單

- 預設值： `[]`

- 必需
- 陣列

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `maintenance:allow-ips`

設定維護模式免除IP

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

允許的IP地址

- 預設值： `[]`

- 陣列

### `--none`

清除允許的IP地址

- 預設值： `false`
- 不接受值

### `--add`

將IP地址添加到現有清單

- 預設值： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `maintenance:disable`

禁用維護模式

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

允許的IP地址（使用「無」清除允許的IP清單）

- 預設值： `[]`
- 需要值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `maintenance:enable`

啟用維護模式

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

允許的IP地址（使用「無」清除允許的IP清單）

- 預設值： `[]`
- 需要值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `maintenance:status`

顯示維護模式狀態

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `media-content:sync`

將內容與資產同步

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `media-gallery:sync`

同步資料庫中的媒體儲存和媒體資產

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `module:config:status`

檢查「app/etc/config.php」檔案和報告中的模組配置（如果它們是最新的或不是最新的）

```bash
bin/magento module:config:status
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `module:disable`

禁用指定的模組

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

模組名稱

- 預設值： `[]`

- 陣列

### `--force`, `-f`

繞過相關性檢查

- 預設值： `false`
- 不接受值

### `--all`

禁用所有模組

- 預設值： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的靜態視圖檔案。 必要，如果模組具有靜態視圖檔案

- 預設值： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `module:enable`

啟用指定的模組

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

模組名稱

- 預設值： `[]`

- 陣列

### `--force`, `-f`

繞過相關性檢查

- 預設值： `false`
- 不接受值

### `--all`

啟用所有模組

- 預設值： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的靜態視圖檔案。 必要，如果模組具有靜態視圖檔案

- 預設值： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `module:status`

顯示模組的狀態

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

可選模組名稱

- 預設值： `[]`

- 陣列

### `--enabled`

僅打印已啟用的模組

- 預設值： `false`
- 不接受值

### `--disabled`

僅打印禁用的模組

- 預設值： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `module:uninstall`

卸載按合成器安裝的模組

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

模組名稱

- 預設值： `[]`

- 必需
- 陣列

### `--remove-data`, `-r`

刪除模組安裝的資料

- 預設值： `false`
- 不接受值

### `--backup-code`

備份代碼和配置檔案（不包括臨時檔案）

- 預設值： `false`
- 不接受值

### `--backup-media`

進行介質備份

- 預設值： `false`
- 不接受值

### `--backup-db`

執行完整的資料庫備份

- 預設值： `false`
- 不接受值

### `--non-composer`

所有模組（在此將過去）將基於非作曲家

- 預設值： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的靜態視圖檔案。 必要，如果模組具有靜態視圖檔案

- 預設值： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `newrelic:create:deploy-marker`

檢查項的部署隊列並建立適當的部署標籤。

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

部署消息？

- 必需

### `change_log`

更改日誌？

- 必需

### `user`

部署用戶


### `revision`

修訂


### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `queue:consumers:list`

MessageQueue使用者清單

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `queue:consumers:restart`

重新啟動MessageQueue使用者

```bash
bin/magento queue:consumers:restart
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `queue:consumers:start`

啟動MessageQueue使用者

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

要啟動的使用者的名稱。

- 必需

### `--max-messages`

在進程終止前由使用者處理的消息數。 如果未指定 — 在處理所有排隊的消息後終止。

- 需要值

### `--batch-size`

每批消息數。 僅適用於批使用者。

- 需要值

### `--area-code`

首選區域（全局、adminhtml等）預設為全局。

- 需要值

### `--single-thread`

此選項可防止同時運行一個使用者的多個副本。

- 預設值： `false`
- 不接受值

### `--multi-process`

每個使用者的進程數。

- 接受值

### `--pid-file-path`

用於保存PID的檔案路徑（不建議使用此選項，請改用單線程）

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `remote-storage:sync`

將媒體檔案與遠程儲存同步。

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `sampledata:deploy`

部署示例資料模組，用於基於合成器的Magento安裝

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

不執行合成器更新而更新composer.json

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `sampledata:remove`

從composer.json中刪除所有示例資料包

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

不執行合成器更新而更新composer.json

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `sampledata:reset`

重置所有示例資料模組以重新安裝

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `security:recaptcha:disable-for-user-forgot-password`

禁用管理員用戶忘記密碼表單的reCAPTCHA

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `security:recaptcha:disable-for-user-login`

禁用管理員用戶登錄表單的reCAPTCHA

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `security:tfa:google:set-secret`

設定用於GoogleOTP代的機密。

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

用戶名

- 必需

### `secret`

秘密

- 必需

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `security:tfa:providers`

列出所有可用提供程式

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `security:tfa:reset`

重置一個用戶的配置

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

用戶名

- 必需

### `provider`

提供程式碼

- 必需

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:backup`

備份Magento應用程式碼庫、介質和資料庫

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

備份代碼和配置檔案（不包括臨時檔案）

- 預設值： `false`
- 不接受值

### `--media`

進行介質備份

- 預設值： `false`
- 不接受值

### `--db`

執行完整的資料庫備份

- 預設值： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:config:set`

建立或修改部署配置

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--id_salt ID_SALT] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

啟用調試日誌記錄

- 需要值

### `--enable-syslog-logging`

啟用Syslog日誌記錄

- 需要值

### `--backend-frontname`

後端前端名稱（如果丟失，將自動生成）

- 需要值

### `--id_salt`

GraphQl鹽

- 需要值

### `--remote-storage-driver`

遠程儲存驅動程式

- 需要值

### `--remote-storage-prefix`

遠程儲存前置詞

- 預設值：&quot;
- 需要值

### `--remote-storage-endpoint`

遠程儲存終結點

- 需要值

### `--remote-storage-bucket`

遠程儲存桶

- 需要值

### `--remote-storage-region`

遠程儲存區域

- 需要值

### `--remote-storage-key`

遠程儲存訪問密鑰

- 預設值：&quot;
- 需要值

### `--remote-storage-secret`

遠程儲存密鑰

- 預設值：&quot;
- 需要值

### `--remote-storage-path-style`

遠程儲存路徑樣式

- 預設值： `0`
- 需要值

### `--amqp-host`

Amqp伺服器主機

- 預設值：&quot;
- 需要值

### `--amqp-port`

Amqp伺服器埠

- 預設值： `5672`
- 需要值

### `--amqp-user`

Amqp伺服器用戶名

- 預設值：&quot;
- 需要值

### `--amqp-password`

Amqp伺服器密碼

- 預設值：&quot;
- 需要值

### `--amqp-virtualhost`

Amqp虛擬主機

- 預設值： `/`
- 需要值

### `--amqp-ssl`

Amqp SSL

- 預設值：&quot;
- 需要值

### `--amqp-ssl-options`

Amqp SSL選項(JSON)

- 預設值：&quot;
- 需要值

### `--consumers-wait-for-messages`

消費者是否應等待隊列中的消息？ 1 — 是，0 — 否

- 需要值

### `--queue-default-connection`

消息隊列預設連接。 可以是「db」、「amqp」或自定義隊列系統。必須安裝和配置隊列系統，否則將無法正確處理消息。

- 需要值

### `--key`

加密密鑰

- 需要值

### `--db-host`

資料庫伺服器主機

- 需要值

### `--db-name`

資料庫名稱

- 需要值

### `--db-user`

資料庫伺服器用戶名

- 需要值

### `--db-engine`

資料庫伺服器引擎

- 需要值

### `--db-password`

資料庫伺服器密碼

- 需要值

### `--db-prefix`

資料庫表前置詞

- 需要值

### `--db-model`

資料庫類型

- 需要值

### `--db-init-statements`

資料庫初始命令集

- 需要值

### `--skip-db-validation`, `-s`

如果指定，則將跳過資料庫連接驗證

- 預設值： `false`
- 不接受值

### `--http-cache-hosts`

http快取主機

- 需要值

### `--db-ssl-key`

通過SSL建立資料庫連接的客戶端密鑰檔案的完整路徑

- 預設值：&quot;
- 需要值

### `--db-ssl-cert`

通過SSL建立資料庫連接的客戶端證書檔案的完整路徑

- 預設值：&quot;
- 需要值

### `--db-ssl-ca`

通過SSL建立資料庫連接的伺服器證書檔案的完整路徑

- 預設值：&quot;
- 需要值

### `--db-ssl-verify`

驗證伺服器證書

- 預設值： `false`
- 不接受值

### `--session-save`

會話保存處理程式

- 需要值

### `--session-save-redis-host`

完全限定的主機名、 IP地址或絕對路徑（如果使用UNIX套接字）

- 需要值

### `--session-save-redis-port`

Redis伺服器偵聽埠

- 需要值

### `--session-save-redis-password`

Redis伺服器密碼

- 需要值

### `--session-save-redis-timeout`

連接超時（秒）

- 需要值

### `--session-save-redis-persistent-id`

用於啟用永久連接的唯一字串

- 需要值

### `--session-save-redis-db`

Redis資料庫編號

- 需要值

### `--session-save-redis-compression-threshold`

Redis壓縮閾值

- 需要值

### `--session-save-redis-compression-lib`

Redis壓縮庫。 值： gzip（預設值）, lzf, lz4, snappy

- 需要值

### `--session-save-redis-log-level`

Redis日誌級別。 值：0（最少冗餘）到7（最詳細）

- 需要值

### `--session-save-redis-max-concurrency`

可等待一個會話上鎖定的進程的最大數量

- 需要值

### `--session-save-redis-break-after-frontend`

嘗試斷開前端會話的鎖之前等待的秒數

- 需要值

### `--session-save-redis-break-after-adminhtml`

嘗試為管理會話斷開鎖前等待的秒數

- 需要值

### `--session-save-redis-first-lifetime`

第一次寫入時非bot的會話的生存時間（秒）（使用0禁用）

- 需要值

### `--session-save-redis-bot-first-lifetime`

第一次寫入時bot的會話壽命（秒）（使用0禁用）

- 需要值

### `--session-save-redis-bot-lifetime`

後續寫入時bot的會話壽命（使用0禁用）

- 需要值

### `--session-save-redis-disable-locking`

Redis禁用鎖定。 值：false（預設值）,true

- 需要值

### `--session-save-redis-min-lifetime`

Redis最小會話生存時間（秒）

- 需要值

### `--session-save-redis-max-lifetime`

Redis最大會話生存時間（秒）

- 需要值

### `--session-save-redis-sentinel-master`

雷迪斯哨兵大師

- 需要值

### `--session-save-redis-sentinel-servers`

Redis Sentinel伺服器，逗號分隔

- 需要值

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主節點。 值：false（預設）,true

- 需要值

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連接重試。

- 需要值

### `--cache-backend`

預設快取處理程式

- 需要值

### `--cache-backend-redis-server`

Redis伺服器

- 需要值

### `--cache-backend-redis-db`

快取的資料庫編號

- 需要值

### `--cache-backend-redis-port`

Redis伺服器偵聽埠

- 需要值

### `--cache-backend-redis-password`

Redis伺服器密碼

- 需要值

### `--cache-backend-redis-compress-data`

設定為0以禁用壓縮（預設值為1，已啟用）

- 需要值

### `--cache-backend-redis-compression-lib`

要使用的壓縮庫 [snappy,lzf,l4z,zstd,gzip] （留空以自動確定）

- 需要值

### `--cache-id-prefix`

快取鍵的ID前置詞

- 需要值

### `--allow-parallel-generation`

允許以非阻塞方式生成快取

- 預設值： `false`
- 不接受值

### `--page-cache`

預設快取處理程式

- 需要值

### `--page-cache-redis-server`

Redis伺服器

- 需要值

### `--page-cache-redis-db`

快取的資料庫編號

- 需要值

### `--page-cache-redis-port`

Redis伺服器偵聽埠

- 需要值

### `--page-cache-redis-password`

Redis伺服器密碼

- 需要值

### `--page-cache-redis-compress-data`

設定為1以壓縮全頁快取（使用0禁用）

- 需要值

### `--page-cache-redis-compression-lib`

要使用的壓縮庫 [snappy,lzf,l4z,zstd,gzip] （留空以自動確定）

- 需要值

### `--page-cache-id-prefix`

快取鍵的ID前置詞

- 需要值

### `--lock-provider`

鎖定提供程式名稱

- 需要值

### `--lock-db-prefix`

安裝特定鎖前置詞以避免鎖衝突

- 需要值

### `--lock-zookeeper-host`

連接到Zookeeper群集的主機和埠。 例如：127.0.0.1:2181

- 需要值

### `--lock-zookeeper-path`

Zookeeper保存鎖的路徑。 預設路徑為：/magento/locks

- 需要值

### `--lock-file-path`

保存檔案鎖定的路徑。

- 需要值

### `--document-root-is-pub`

要顯示的標誌是Pub在根上，只能為true或false

- 需要值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:db-data:upgrade`

在資料庫中安裝和升級資料

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:db-declaration:generate-patch`

生成修補程式並將其放在特定資料夾中。

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

模組名稱

- 必需

### `patch`

修補程式名稱

- 必需

### `--revertable`

檢查修補程式是否可恢復。

- 預設值： `false`
- 接受值

### `--type`

查找應生成的修補程式類型。 可用值： `data`。 `schema`。

- 預設值： `data`
- 接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:db-declaration:generate-whitelist`

生成允許由聲明安裝程式編輯的表和列的白名單

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

將生成白名單的模組的名稱

- 預設值： `all`
- 接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:db-schema:upgrade`

安裝和升級資料庫架構

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式

- 預設值： `false`
- 接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:db:status`

檢查DB架構或資料是否需要升級

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:di:compile`

生成DI配置和所有可自動生成的缺失類

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:install`

安裝Magento應用程式

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--id_salt ID_SALT] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

啟用調試日誌記錄

- 需要值

### `--enable-syslog-logging`

啟用Syslog日誌記錄

- 需要值

### `--backend-frontname`

後端前端名稱（如果丟失，將自動生成）

- 需要值

### `--id_salt`

GraphQl鹽

- 需要值

### `--remote-storage-driver`

遠程儲存驅動程式

- 需要值

### `--remote-storage-prefix`

遠程儲存前置詞

- 預設值：&quot;
- 需要值

### `--remote-storage-endpoint`

遠程儲存終結點

- 需要值

### `--remote-storage-bucket`

遠程儲存桶

- 需要值

### `--remote-storage-region`

遠程儲存區域

- 需要值

### `--remote-storage-key`

遠程儲存訪問密鑰

- 預設值：&quot;
- 需要值

### `--remote-storage-secret`

遠程儲存密鑰

- 預設值：&quot;
- 需要值

### `--remote-storage-path-style`

遠程儲存路徑樣式

- 預設值： `0`
- 需要值

### `--amqp-host`

Amqp伺服器主機

- 預設值：&quot;
- 需要值

### `--amqp-port`

Amqp伺服器埠

- 預設值： `5672`
- 需要值

### `--amqp-user`

Amqp伺服器用戶名

- 預設值：&quot;
- 需要值

### `--amqp-password`

Amqp伺服器密碼

- 預設值：&quot;
- 需要值

### `--amqp-virtualhost`

Amqp虛擬主機

- 預設值： `/`
- 需要值

### `--amqp-ssl`

Amqp SSL

- 預設值：&quot;
- 需要值

### `--amqp-ssl-options`

Amqp SSL選項(JSON)

- 預設值：&quot;
- 需要值

### `--consumers-wait-for-messages`

消費者是否應等待隊列中的消息？ 1 — 是，0 — 否

- 需要值

### `--queue-default-connection`

消息隊列預設連接。 可以是「db」、「amqp」或自定義隊列系統。必須安裝和配置隊列系統，否則將無法正確處理消息。

- 需要值

### `--key`

加密密鑰

- 需要值

### `--db-host`

資料庫伺服器主機

- 需要值

### `--db-name`

資料庫名稱

- 需要值

### `--db-user`

資料庫伺服器用戶名

- 需要值

### `--db-engine`

資料庫伺服器引擎

- 需要值

### `--db-password`

資料庫伺服器密碼

- 需要值

### `--db-prefix`

資料庫表前置詞

- 需要值

### `--db-model`

資料庫類型

- 需要值

### `--db-init-statements`

資料庫初始命令集

- 需要值

### `--skip-db-validation`, `-s`

如果指定，則將跳過資料庫連接驗證

- 預設值： `false`
- 不接受值

### `--http-cache-hosts`

http快取主機

- 需要值

### `--db-ssl-key`

通過SSL建立資料庫連接的客戶端密鑰檔案的完整路徑

- 預設值：&quot;
- 需要值

### `--db-ssl-cert`

通過SSL建立資料庫連接的客戶端證書檔案的完整路徑

- 預設值：&quot;
- 需要值

### `--db-ssl-ca`

通過SSL建立資料庫連接的伺服器證書檔案的完整路徑

- 預設值：&quot;
- 需要值

### `--db-ssl-verify`

驗證伺服器證書

- 預設值： `false`
- 不接受值

### `--session-save`

會話保存處理程式

- 需要值

### `--session-save-redis-host`

完全限定的主機名、 IP地址或絕對路徑（如果使用UNIX套接字）

- 需要值

### `--session-save-redis-port`

Redis伺服器偵聽埠

- 需要值

### `--session-save-redis-password`

Redis伺服器密碼

- 需要值

### `--session-save-redis-timeout`

連接超時（秒）

- 需要值

### `--session-save-redis-persistent-id`

用於啟用永久連接的唯一字串

- 需要值

### `--session-save-redis-db`

Redis資料庫編號

- 需要值

### `--session-save-redis-compression-threshold`

Redis壓縮閾值

- 需要值

### `--session-save-redis-compression-lib`

Redis壓縮庫。 值： gzip（預設值）, lzf, lz4, snappy

- 需要值

### `--session-save-redis-log-level`

Redis日誌級別。 值：0（最少冗餘）到7（最詳細）

- 需要值

### `--session-save-redis-max-concurrency`

可等待一個會話上鎖定的進程的最大數量

- 需要值

### `--session-save-redis-break-after-frontend`

嘗試斷開前端會話的鎖之前等待的秒數

- 需要值

### `--session-save-redis-break-after-adminhtml`

嘗試為管理會話斷開鎖前等待的秒數

- 需要值

### `--session-save-redis-first-lifetime`

第一次寫入時非bot的會話的生存時間（秒）（使用0禁用）

- 需要值

### `--session-save-redis-bot-first-lifetime`

第一次寫入時bot的會話壽命（秒）（使用0禁用）

- 需要值

### `--session-save-redis-bot-lifetime`

後續寫入時bot的會話壽命（使用0禁用）

- 需要值

### `--session-save-redis-disable-locking`

Redis禁用鎖定。 值：false（預設值）,true

- 需要值

### `--session-save-redis-min-lifetime`

Redis最小會話生存時間（秒）

- 需要值

### `--session-save-redis-max-lifetime`

Redis最大會話生存時間（秒）

- 需要值

### `--session-save-redis-sentinel-master`

雷迪斯哨兵大師

- 需要值

### `--session-save-redis-sentinel-servers`

Redis Sentinel伺服器，逗號分隔

- 需要值

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主節點。 值：false（預設）,true

- 需要值

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連接重試。

- 需要值

### `--cache-backend`

預設快取處理程式

- 需要值

### `--cache-backend-redis-server`

Redis伺服器

- 需要值

### `--cache-backend-redis-db`

快取的資料庫編號

- 需要值

### `--cache-backend-redis-port`

Redis伺服器偵聽埠

- 需要值

### `--cache-backend-redis-password`

Redis伺服器密碼

- 需要值

### `--cache-backend-redis-compress-data`

設定為0以禁用壓縮（預設值為1，已啟用）

- 需要值

### `--cache-backend-redis-compression-lib`

要使用的壓縮庫 [snappy,lzf,l4z,zstd,gzip] （留空以自動確定）

- 需要值

### `--cache-id-prefix`

快取鍵的ID前置詞

- 需要值

### `--allow-parallel-generation`

允許以非阻塞方式生成快取

- 預設值： `false`
- 不接受值

### `--page-cache`

預設快取處理程式

- 需要值

### `--page-cache-redis-server`

Redis伺服器

- 需要值

### `--page-cache-redis-db`

快取的資料庫編號

- 需要值

### `--page-cache-redis-port`

Redis伺服器偵聽埠

- 需要值

### `--page-cache-redis-password`

Redis伺服器密碼

- 需要值

### `--page-cache-redis-compress-data`

設定為1以壓縮全頁快取（使用0禁用）

- 需要值

### `--page-cache-redis-compression-lib`

要使用的壓縮庫 [snappy,lzf,l4z,zstd,gzip] （留空以自動確定）

- 需要值

### `--page-cache-id-prefix`

快取鍵的ID前置詞

- 需要值

### `--lock-provider`

鎖定提供程式名稱

- 需要值

### `--lock-db-prefix`

安裝特定鎖前置詞以避免鎖衝突

- 需要值

### `--lock-zookeeper-host`

連接到Zookeeper群集的主機和埠。 例如：127.0.0.1:2181

- 需要值

### `--lock-zookeeper-path`

Zookeeper保存鎖的路徑。 預設路徑為：/magento/locks

- 需要值

### `--lock-file-path`

保存檔案鎖定的路徑。

- 需要值

### `--document-root-is-pub`

要顯示的標誌是Pub在根上，只能為true或false

- 需要值

### `--base-url`

應在中提供儲存的URL。 不建議使用，使用config:set with path web/unsecure/base_url

- 需要值

### `--language`

預設語言代碼。 不建議使用，使用config:set with path general/locale/code（使用通用/區域設定/代碼設定）

- 需要值

### `--timezone`

預設時區代碼。 不建議使用，使用config:set with path general/locale/timezone

- 需要值

### `--currency`

預設貨幣代碼。 不建議使用，使用config:set with path currency/options/base、currency/options/default和currency/options/allow

- 需要值

### `--use-rewrites`

使用重寫。 不建議使用，使用config:set with path web/seo/use_rewrites

- 需要值

### `--use-secure`

使用安全URL。 僅當SSL可用時才啟用此選項。 不建議使用，使用config:set with path web/secure/use_in_frontend

- 需要值

### `--base-url-secure`

SSL連接的基URL。 不建議使用，使用config:set with path web/secure/base_url

- 需要值

### `--use-secure-admin`

使用SSL運行管理介面。 不建議使用，使用config:set with path web/secure/use_in_adminhtml

- 需要值

### `--admin-use-security-key`

是否在Magento管理URL和表單中使用「安全密鑰」功能。 不建議使用，使用config:set with path admin/security/use_form_key

- 需要值

### `--admin-user`

管理員用戶

- 接受值

### `--admin-password`

管理員密碼

- 接受值

### `--admin-email`

管理員電子郵件

- 接受值

### `--admin-firstname`

管理員名

- 接受值

### `--admin-lastname`

管理員姓

- 接受值

### `--search-engine`

搜索引擎。 值：elasticsearch5, elasticsearch7, elasticsearch8, opensearch

- 需要值

### `--elasticsearch-host`

Elasticsearch伺服器主機。

- 需要值

### `--elasticsearch-port`

Elasticsearch伺服器埠。

- 需要值

### `--elasticsearch-enable-auth`

設定為1以啟用身份驗證。 （預設值為0，已禁用）

- 需要值

### `--elasticsearch-username`

Elasticsearch用戶名。 僅在啟用HTTP身份驗證時適用

- 需要值

### `--elasticsearch-password`

Elasticsearch密碼。 僅在啟用HTTP身份驗證時適用

- 需要值

### `--elasticsearch-index-prefix`

Elasticsearch索引前置詞。

- 需要值

### `--elasticsearch-timeout`

Elasticsearch伺服器超時。

- 需要值

### `--opensearch-host`

OpenSearch伺服器主機。

- 需要值

### `--opensearch-port`

OpenSearch伺服器埠。

- 需要值

### `--opensearch-enable-auth`

設定為1以啟用身份驗證。 （預設值為0，已禁用）

- 需要值

### `--opensearch-username`

OpenSearch用戶名。 僅在啟用HTTP身份驗證時適用

- 需要值

### `--opensearch-password`

OpenSearch密碼。 僅在啟用HTTP身份驗證時適用

- 需要值

### `--opensearch-index-prefix`

OpenSearch索引前置詞。

- 需要值

### `--opensearch-timeout`

OpenSearch伺服器超時。

- 需要值

### `--cleanup-database`

在安裝前清理資料庫

- 預設值： `false`
- 不接受值

### `--sales-order-increment-prefix`

銷售訂單編號前置詞

- 需要值

### `--use-sample-data`

使用示例資料

- 預設值： `false`
- 不接受值

### `--enable-modules`

逗號分隔的模組名稱清單。 安裝過程中必須包括該內容。 可用的幻數參數「all」。

- 接受值

### `--disable-modules`

逗號分隔的模組名稱清單。 安裝時必須避免出現這種情況。 可用的幻數參數「all」。

- 接受值

### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式

- 預設值： `false`
- 接受值

### `--interactive`, `-i`

互動式Magento安裝

- 預設值： `false`
- 不接受值

### `--safe-mode`

在破壞性操作（如刪除列）上安全安裝帶有轉儲的Magento

- 接受值

### `--data-restore`

從轉儲中還原已刪除的資料

- 接受值

### `--dry-run`

Magento安裝將以乾式運行模式運行

- 預設值： `false`
- 接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:performance:generate-fixtures`

生成夾具

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

配置檔案的路徑

- 必需

### `--skip-reindex`, `-s`

跳過重新索引

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:rollback`

回退Magento應用程式碼庫、媒體和資料庫

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

var/backups中代碼備份檔案的基名

- 需要值

### `--media-file`, `-m`

var/backups中介質備份檔案的基名

- 需要值

### `--db-file`, `-d`

var/backups中資料庫備份檔案的基名

- 需要值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:static-content:deploy`

部署靜態視圖檔案

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

要輸出靜態視圖檔案的ISO-639語言代碼的空格分隔清單。

- 預設值： `[]`

- 陣列

### `--force`, `-f`

以任何模式部署檔案。

- 預設值： `false`
- 不接受值

### `--strategy`, `-s`

使用指定的策略部署檔案。

- 預設值： `quick`
- 接受值

### `--area`, `-a`

僅為指定區域生成檔案。

- 預設值： `all`
- 接受多個值

### `--exclude-area`

不為指定區域生成檔案。

- 預設值： `none`
- 接受多個值

### `--theme`, `-t`

僅為指定的主題生成靜態視圖檔案。

- 預設值： `all`
- 接受多個值

### `--exclude-theme`

不生成指定主題的檔案。

- 預設值： `none`
- 接受多個值

### `--language`, `-l`

僅生成指定語言的檔案。

- 預設值： `all`
- 接受多個值

### `--exclude-language`

不生成指定語言的檔案。

- 預設值： `none`
- 接受多個值

### `--jobs`, `-j`

使用指定的作業數啟用並行處理。

- 預設值： `0`
- 接受值

### `--max-execution-time`

部署靜態進程的最大預期執行時間（以秒為單位）。

- 預設值： `900`
- 接受值

### `--symlink-locale`

為那些為部署傳遞但沒有自定義的區域設定的檔案建立符號連結。

- 預設值： `false`
- 不接受值

### `--content-version`

如果在多個節點上運行部署，以確保靜態內容版本相同且快取工作正常，則可以使用靜態內容的自定義版本。

- 需要值

### `--refresh-content-version-only`

刷新靜態內容的版本只能用於刷新瀏覽器快取和CDN快取中的靜態內容。

- 預設值： `false`
- 不接受值

### `--no-javascript`

不部署JavaScript檔案。

- 預設值： `false`
- 不接受值

### `--no-js-bundle`

不部署JavaScript包檔案。

- 預設值： `false`
- 不接受值

### `--no-css`

不要部署CSS檔案。

- 預設值： `false`
- 不接受值

### `--no-less`

不要部署LESS檔案。

- 預設值： `false`
- 不接受值

### `--no-images`

不部署映像。

- 預設值： `false`
- 不接受值

### `--no-fonts`

不部署字型檔案。

- 預設值： `false`
- 不接受值

### `--no-html`

不部署HTML檔案。

- 預設值： `false`
- 不接受值

### `--no-misc`

不部署其他類型（.md、.jbf、.csv等）的檔案。

- 預設值： `false`
- 不接受值

### `--no-html-minify`

不要小化HTML檔案。

- 預設值： `false`
- 不接受值

### `--no-parent`

不要編譯父主題。 僅在快速和標準策略中受支援。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:store-config:set`

安裝儲存配置。 自2.2.0以來已棄用。改用config:set

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

應在中提供儲存的URL。 不建議使用，使用config:set with path web/unsecure/base_url

- 需要值

### `--language`

預設語言代碼。 不建議使用，使用config:set with path general/locale/code（使用通用/區域設定/代碼設定）

- 需要值

### `--timezone`

預設時區代碼。 不建議使用，使用config:set with path general/locale/timezone

- 需要值

### `--currency`

預設貨幣代碼。 不建議使用，使用config:set with path currency/options/base、currency/options/default和currency/options/allow

- 需要值

### `--use-rewrites`

使用重寫。 不建議使用，使用config:set with path web/seo/use_rewrites

- 需要值

### `--use-secure`

使用安全URL。 僅當SSL可用時才啟用此選項。 不建議使用，使用config:set with path web/secure/use_in_frontend

- 需要值

### `--base-url-secure`

SSL連接的基URL。 不建議使用，使用config:set with path web/secure/base_url

- 需要值

### `--use-secure-admin`

使用SSL運行管理介面。 不建議使用，使用config:set with path web/secure/use_in_adminhtml

- 需要值

### `--admin-use-security-key`

是否在Magento管理URL和表單中使用「安全密鑰」功能。 不建議使用，使用config:set with path admin/security/use_form_key

- 需要值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:uninstall`

卸載Magento應用程式

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `setup:upgrade`

升級Magento應用程式、資料庫資料和架構

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

阻止刪除生成的檔案。 除了部署到生產環境外，我們不鼓勵使用此選項。 有關詳細資訊，請咨詢系統整合商或管理員。

- 預設值： `false`
- 不接受值

### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式

- 預設值： `false`
- 接受值

### `--safe-mode`

在破壞性操作（如刪除列）上安全安裝帶有轉儲的Magento

- 接受值

### `--data-restore`

從轉儲中還原已刪除的資料

- 接受值

### `--dry-run`

Magento安裝將以乾式運行模式運行

- 預設值： `false`
- 接受值

### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=開發者&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `store:list`

顯示儲存清單

```bash
bin/magento store:list
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `store:website:list`

顯示網站清單

```bash
bin/magento store:website:list
```

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `theme:uninstall`

卸載主題

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

主題的路徑。 主題路徑應指定為完整路徑，即區域/供應商/名稱。 例如，前端/Magento/空白

- 預設值： `[]`

- 必需
- 陣列

### `--backup-code`

執行代碼備份（不包括臨時檔案）

- 預設值： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的靜態視圖檔案。

- 預設值： `false`
- 不接受值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值


## `varnish:vcl:generate`

生成清漆VCL並回聲到命令行

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

可清除清漆的IP訪問清單

- 預設值： `localhost`
- 需要值

### `--backend-host`

Web後端主機

- 預設值： `localhost`
- 需要值

### `--backend-port`

Web後端的埠

- 預設值： `8080`
- 需要值

### `--export-version`

清漆檔案的版本

- 預設值： `4`
- 需要值

### `--grace-period`

寬限期（秒）

- 預設值： `300`
- 需要值

### `--output-file`

要寫入vcl的檔案的路徑

- 需要值

### `--help`, `-h`

顯示給定命令的幫助。 當沒有為 &lt;info>清單&lt;/info> 命令

- 預設值： `false`
- 不接受值

### `--quiet`, `-q`

不輸出任何消息

- 預設值： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加郵件的詳細程度：1表示正常輸出，2表示更詳細輸出，3表示調試

- 預設值： `false`
- 不接受值

### `--version`, `-V`

顯示此應用程式版本

- 預設值： `false`
- 不接受值

### `--ansi`

強制（或禁用 — 無 — ansi）ANSI輸出

- 不接受值

### `--no-ansi`

否定&quot;—ansi&quot;選項

- 預設值： `false`
- 不接受值

### `--no-interaction`, `-n`

不要問任何互動式問題

- 預設值： `false`
- 不接受值
