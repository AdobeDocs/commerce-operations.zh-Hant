---
source-git-commit: ebd32f3fac571efa729122d0e84471b6de540630
workflow-type: tm+mt
source-wordcount: '14684'
ht-degree: 0%

---
# bin/magento(Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**:2.4.5 <!-- app.version -->

此參考包含111個命令，可透過 `bin/magento` 命令列工具。
初始清單會使用 `bin/magento list` 命令。
使用 [&quot;添加CLI命令&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) 添加自定義CLI命令的指南。

>[!NOTE]
>
>您可以呼叫 `bin/magento` CLI命令使用快捷方式，而不是完整命令名。 例如，您可以呼叫 `bin/magento setup:upgrade` 使用 `bin/magento s:up`, `bin/magento s:upg`. 請參閱 [快速鍵語法](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) 了解如何將快捷方式與任何CLI命令一起使用。

>[!NOTE]
>
>此引用從應用程式碼庫中生成。 若要變更內容，您可以在 [基底](https://github.com/magento) 存放庫，並提交變更以供審核。 另一種方式是 _給我們反饋_ （尋找右上方的連結）。 如需貢獻准則，請參閱 [代碼貢獻](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

顯示命令幫助

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `list`

清單命令

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
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

## `admin:adobe-ims:disable`

停用Adobe IMS模組

```bash
bin/magento admin:adobe-ims:disable
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:adobe-ims:enable`

啟用Adobe IMS模組。

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--organization-id`, `-o`



設定Adobe IMS設定的組織ID。 啟用模組時需要
- 接受值



### `--client-id`, `-c`



設定Adobe IMS設定的用戶端ID。 啟用模組時需要
- 接受值



### `--client-secret`, `-s`



為Adobe IMS設定設定用戶端密碼。 啟用模組時需要
- 接受值



### `--2fa`, `-t`



檢查Adobe Admin Console中是否已為「組織」啟用2FA。 啟用模組時需要
- 接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:adobe-ims:info`

Adobe IMS模組設定資訊

```bash
bin/magento admin:adobe-ims:info
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:adobe-ims:status`

Adobe IMS模組狀態

```bash
bin/magento admin:adobe-ims:status
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:user:create`

建立管理員

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:user:unlock`

解除鎖定管理員帳戶

```bash
bin/magento admin:user:unlock <username>
```

<!-- app.name --> <!-- command.usage -->

### `username`

要解鎖的管理員用戶名
- 必填

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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:config:dump`

建立應用程式轉儲

```bash
bin/magento app:config:dump [<config-types>...]
```

<!-- app.name --> <!-- command.usage -->

### `config-types`

以空格分隔的配置類型清單或忽略以轉儲所有 [範圍，主題，系統，i18n]

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:config:import`

將資料從共用配置檔案導入適當的資料儲存

```bash
bin/magento app:config:import
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:config:status`

檢查配置傳播是否需要更新

```bash
bin/magento app:config:status
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `braintree:migrate`

從Magento1資料庫遷移儲存的卡

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

主機名/IP。 埠為可選
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



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:clean`

清除快取類型

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的快取類型清單或忽略以應用於所有快取類型。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆蓋引導的參數
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:disable`

禁用快取類型

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的快取類型清單或忽略以應用於所有快取類型。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆蓋引導的參數
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:enable`

啟用快取類型

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的快取類型清單或忽略以應用於所有快取類型。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆蓋引導的參數
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:flush`

刷新快取類型使用的快取儲存

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的快取類型清單或忽略以應用於所有快取類型。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆蓋引導的參數
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:status`

檢查快取狀態

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--bootstrap`

添加或覆蓋引導的參數
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `catalog:images:resize`

建立調整大小的產品影像

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--async`, `-a`



以非同步模式調整影像大小
- 預設值： `false`
- 不接受值


### `--skip_hidden_images`

不處理標籤為在產品頁面中隱藏的影像
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `catalog:product:attributes:cleanup`

移除未使用的產品屬性。

```bash
bin/magento catalog:product:attributes:cleanup
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cms:wysiwyg:restrict`

設定要強制執行使用者HTML內容驗證或改為顯示警告

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

<!-- app.name --> <!-- command.usage -->

### `restrict`

y\n
- 必填

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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `config:sensitive:set`

設定敏感配置值

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

<!-- app.name --> <!-- command.usage -->

### `path`

組/節/field_name的配置路徑
<!-- argument -->

### `value`

設定值
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--interactive`, `-i`



啟用互動模式以設定所有敏感變數
- 預設值： `false`
- 不接受值


### `--scope`

配置範圍，如果未設定，則使用「default」
- 預設值： `default`
- 接受值


### `--scope-code`

配置的作用域代碼，預設為空字串
- 預設值：&quot;
- 接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `config:set`

更改系統配置

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

<!-- app.name --> <!-- command.usage -->

### `path`

以格式表示的section/group/field_name配置路徑
- 必填

   <!-- argument -->

### `value`

設定值
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

配置範圍（預設、網站或儲存）
- 預設值： `default`
- 需要值


### `--scope-code`

範圍代碼（僅當範圍不是「預設」時為必要）
- 需要值



### `--lock-env`, `-e`



阻止在管理員中修改的鎖定值(將保存在app/etc/env.php中)
- 預設值： `false`
- 不接受值



### `--lock-config`, `-c`



鎖定值並與其他安裝共用值，防止在管理員中進行修改(將儲存在app/etc/config.php中)
- 預設值： `false`
- 不接受值



### `--lock`, `-l`



已棄用，請改用 — lock-env選項。
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `config:show`

顯示給定路徑的配置值。 如果未指定路徑，則會顯示所有儲存的值

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

配置路徑，例如section_id/group_id/field_id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

配置的範圍，如果未指定，則使用「預設」範圍
- 預設值： `default`
- 接受值


### `--scope-code`

範圍代碼(僅在範圍不為時為必需 `default`)
- 預設值：&quot;
- 接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cron:install`

為當前用戶生成並安裝crontab

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



強制安裝任務
- 預設值： `false`
- 不接受值



### `--non-optional`, `-d`



僅安裝非可選（預設）任務
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cron:remove`

從crontab中刪除任務

```bash
bin/magento cron:remove
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cron:run`

按計畫運行作業

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--group`

僅從指定組運行作業
- 需要值


### `--bootstrap`

添加或覆蓋引導的參數
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `customer:hash:upgrade`

根據最新演算法升級客戶的雜湊

```bash
bin/magento customer:hash:upgrade
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `deploy:mode:set`

設定應用程式模式。

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

<!-- app.name --> <!-- command.usage -->

### `mode`

要設定的應用程式模式。 可用選項為「開發人員」或「生產」
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-compilation`, `-s`



略過靜態內容的清除和重新產生（產生的程式碼、預先處理的CSS，以及pub/static/中的資產）
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `deploy:mode:show`

顯示當前應用程式模式。

```bash
bin/magento deploy:mode:show
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:di:info`

提供有關命令的依賴項插入配置的資訊。

```bash
bin/magento dev:di:info <class>
```

<!-- app.name --> <!-- command.usage -->

### `class`

類名
- 必填

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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:email:newsletter-compatibility-check`

掃描電子報範本，以了解潛在的變數使用相容性問題

```bash
bin/magento dev:email:newsletter-compatibility-check
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:email:override-compatibility-check`

掃描電子郵件範本覆寫，以找出潛在的變數使用相容性問題

```bash
bin/magento dev:email:override-compatibility-check
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:profiler:disable`

禁用探查器。

```bash
bin/magento dev:profiler:disable
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:profiler:enable`

啟用探查器。

```bash
bin/magento dev:profiler:enable [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

探查器類型
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:query-log:disable`

禁用資料庫查詢日誌

```bash
bin/magento dev:query-log:disable
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:query-log:enable`

啟用資料庫查詢日誌

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--include-all-queries`

記錄所有查詢。 [true\|false]
- 預設值： `true`
- 接受值


### `--query-time-threshold`

查詢時間閾值。
- 預設值： `0.001`
- 接受值


### `--include-call-stack`

包括調用堆棧。 [true\|false]
- 預設值： `true`
- 接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:source-theme:deploy`

收集並發佈主題的源檔案。

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

<!-- app.name --> <!-- command.usage -->

### `file`

要預先處理的檔案（應指定檔案，但不應加上副檔名）
- 預設值： `css/styles-mcss/styles-l`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

源檔案的類型： [less]
- 預設值： `less`
- 需要值


### `--locale`

地區： [en_US]
- 預設值： `en_US`
- 需要值


### `--area`

區域： [frontend\|adminhtml]
- 預設值： `frontend`
- 需要值


### `--theme`

主題： [供應商/主題]
- 預設值： `Magento/luma`
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:template-hints:disable`

禁用前端模板提示。 可能需要快取刷新。

```bash
bin/magento dev:template-hints:disable
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:template-hints:enable`

啟用前端模板提示。 可能需要快取刷新。

```bash
bin/magento dev:template-hints:enable
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:template-hints:status`

顯示前端模板提示狀態。

```bash
bin/magento dev:template-hints:status
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:tests:run`

執行測試

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

要執行的測試類型。 可用類型：all, unit，整合， integration all，靜態，靜態，完整，舊，預設
- 預設值： `default`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--arguments`, `-c`



PHPUnit的其他參數。 範例：&quot;-c&#39;-filter=MyTest&#39;&quot;（無空格）
- 預設值：&quot;
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:urn-catalog:generate`

為IDE生成URN到*.xsd映射的目錄，以突出顯示xml。

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

輸出目錄的檔案路徑。 對於PhpStorm，請使用。idea/misc.xml
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--ide`

將產生目錄的格式。 支援： [弗斯托姆，弗斯科德]
- 預設值： `phpstorm`
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:xml:convert`

使用XSL樣式表轉換XML檔案

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

<!-- app.name --> <!-- command.usage -->

### `xml-file`

要轉換的XML檔案的路徑
- 必填

   <!-- argument -->

### `processor`

要應用到XML檔案的XSL樣式表的路徑
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--overwrite`, `-o`



覆蓋XML檔案
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `downloadable:domains:add`

將網域新增至白名單中的可下載網域

```bash
bin/magento downloadable:domains:add [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

網域名稱

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `downloadable:domains:remove`

從可下載的網域白名單中移除網域

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

域名

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `downloadable:domains:show`

顯示可下載的網域白名單

```bash
bin/magento downloadable:domains:show
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `encryption:payment-data:update`

使用最新的加密密碼重新加密加密的信用卡資料。

```bash
bin/magento encryption:payment-data:update
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `i18n:collect-phrases`

探索程式碼基底中的片語

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

<!-- app.name --> <!-- command.usage -->

### `directory`

要分析的目錄路徑。 若已設定 — magento標幟，則不需要
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--output`, `-o`



輸出檔案的路徑（包括檔案名）。 若未指定檔案，預設值為stdout。
- 需要值



### `--magento`, `-m`



使用 — magento參數來剖析目前的Magento程式碼基底。 如果指定了目錄，請忽略參數。
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `i18n:pack`

保存語言包

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

<!-- app.name --> <!-- command.usage -->

### `source`

具有翻譯的源字典檔案的路徑
- 必填

   <!-- argument -->

### `locale`

字典的目標區域設定，例如&quot;de_DE&quot;
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--mode`, `-m`



字典的儲存模式 — &quot;replace&quot; — 以新語言包替換語言包 — &quot;merge&quot; — 合併語言包，預設為&quot;replace&quot;
- 預設值： `replace`
- 需要值



### `--allow-duplicates`, `-d`



使用 — allow-duplicates參數允許保存翻譯的重複項。 否則請忽略參數。
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `i18n:uninstall`

卸載語言包

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

<!-- app.name --> <!-- command.usage -->

### `package`

語言包名稱

- 預設值： `[]`
- 必填

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--backup-code`, `-b`



執行代碼和配置檔案備份（不包括臨時檔案）
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:info`

顯示允許的索引器

```bash
bin/magento indexer:info
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:reindex`

重新索引資料

```bash
bin/magento indexer:reindex [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

以空格分隔的索引類型清單或忽略以應用於所有索引。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:reset`

將索引器狀態重置為無效

```bash
bin/magento indexer:reset [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

以空格分隔的索引類型清單或忽略以應用於所有索引。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:set-dimensions-mode`

設定索引器Dimension模式

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

索引器名稱 [catalog_product_price]
<!-- argument -->

### `mode`

索引器維模式catalog_product_price none,website,customer_group,website_and_customer_group
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:set-mode`

設定索引模式類型

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

<!-- app.name --> <!-- command.usage -->

### `mode`

索引器模式類型 [即時|計畫]
<!-- argument -->

### `index`

以空格分隔的索引類型清單或忽略以應用於所有索引。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:show-dimensions-mode`

顯示索引器Dimension模式

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

以空格分隔的索引類型清單或忽略以應用於所有索引(catalog_product_price)

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:show-mode`

顯示索引模式

```bash
bin/magento indexer:show-mode [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

以空格分隔的索引類型清單或忽略以應用於所有索引。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:status`

顯示索引器的狀態

```bash
bin/magento indexer:status [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

以空格分隔的索引類型清單或忽略以應用於所有索引。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:adminuri`

顯示Magento管理URI

```bash
bin/magento info:adminuri
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:backups:list`

打印可用備份檔案的清單

```bash
bin/magento info:backups:list
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:currency:list`

顯示可用貨幣清單

```bash
bin/magento info:currency:list
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:dependencies:show-framework`

顯示對Magento框架的依賴項數

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



報表檔案名
- 預設值： `framework-dependencies.csv`
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules`

顯示模組之間的依賴項數

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



報表檔案名
- 預設值： `modules-dependencies.csv`
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules-circular`

顯示模組之間的循環依賴項數

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



報表檔案名
- 預設值： `modules-circular-dependencies.csv`
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:language:list`

顯示可用語言區域設定的清單

```bash
bin/magento info:language:list
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:timezone:list`

顯示可用時區清單

```bash
bin/magento info:timezone:list
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `inventory:reservation:create-compensations`

通過提供的報酬參數建立保留

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

<!-- app.name --> <!-- command.usage -->

### `compensations`

格式「」的報酬參數清單&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--raw`, `-r`



原始輸出
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `inventory:reservation:list-inconsistencies`

顯示所有可銷售數量不一致的訂單和產品

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--complete-orders`, `-c`



僅顯示完成訂單的不一致
- 預設值： `false`
- 不接受值



### `--incomplete-orders`, `-i`



僅顯示未完成訂單的不一致
- 預設值： `false`
- 不接受值



### `--bunch-size`, `-b`



定義一次要載入的訂單數
- 預設值： `50`
- 接受值



### `--raw`, `-r`



原始輸出
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `inventory-geonames:import`

下載並導入源選擇算法的地理名稱

```bash
bin/magento inventory-geonames:import <countries>...
```

<!-- app.name --> <!-- command.usage -->

### `countries`

要導入的國家/地區代碼清單

- 預設值： `[]`
- 必填

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:allow-ips`

設定維護模式豁免IP

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

<!-- app.name --> <!-- command.usage -->

### `ip`

允許的IP位址

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--none`

清除允許的IP地址
- 預設值： `false`
- 不接受值


### `--add`

將IP位址新增至現有清單
- 預設值： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:disable`

禁用維護模式

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

允許的IP地址（使用「無」清除允許的IP清單）
- 預設值： `[]`
- 需要值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:enable`

啟用維護模式

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

允許的IP地址（使用「無」清除允許的IP清單）
- 預設值： `[]`
- 需要值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:status`

顯示維護模式狀態

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `media-content:sync`

將內容與資產同步

```bash
bin/magento media-content:sync
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `media-gallery:sync`

同步資料庫中的媒體儲存和媒體資產

```bash
bin/magento media-gallery:sync
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:config:status`

檢查&#39;app/etc/config.php&#39;檔案中的模組配置，並報告是否為最新

```bash
bin/magento module:config:status
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:disable`

禁用指定的模組

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

模組名稱

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



略過相依性檢查
- 預設值： `false`
- 不接受值


### `--all`

禁用所有模組
- 預設值： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的靜態視圖檔案。 必要，如果模組具有靜態檢視檔案
- 預設值： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:enable`

啟用指定的模組

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

模組名稱

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



略過相依性檢查
- 預設值： `false`
- 不接受值


### `--all`

啟用所有模組
- 預設值： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的靜態視圖檔案。 必要，如果模組具有靜態檢視檔案
- 預設值： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:status`

顯示模組的狀態

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

<!-- app.name --> <!-- command.usage -->

### `module-names`

可選模組名稱

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--enabled`

僅打印已啟用的模組
- 預設值： `false`
- 不接受值


### `--disabled`

僅打印禁用的模組
- 預設值： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:uninstall`

卸載由撰寫器安裝的模組

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

<!-- app.name --> <!-- command.usage -->

### `module`

模組名稱

- 預設值： `[]`
- 必填

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--remove-data`, `-r`



移除模組安裝的資料
- 預設值： `false`
- 不接受值


### `--backup-code`

執行代碼和配置檔案備份（不包括臨時檔案）
- 預設值： `false`
- 不接受值


### `--backup-media`

進行介質備份
- 預設值： `false`
- 不接受值


### `--backup-db`

進行完整資料庫備份
- 預設值： `false`
- 不接受值


### `--non-composer`

所有模組，將在此過去，將非以撰寫器為基礎
- 預設值： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的靜態視圖檔案。 必要，如果模組具有靜態檢視檔案
- 預設值： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `newrelic:create:deploy-marker`

檢查項的部署隊列，並建立相應的部署標籤。

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

<!-- app.name --> <!-- command.usage -->

### `message`

部署消息？
- 必填

   <!-- argument -->

### `change_log`

更改日誌？
- 必填

   <!-- argument -->

### `user`

部署用戶
<!-- argument -->

### `revision`

修訂
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `queue:consumers:list`

MessageQueue使用者清單

```bash
bin/magento queue:consumers:list
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `queue:consumers:start`

啟動MessageQueue使用者

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

<!-- app.name --> <!-- command.usage -->

### `consumer`

要啟動的消費者的名稱。
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--max-messages`

在處理終止前由消費者處理的消息數。 如果未指定 — 在處理所有已排隊的消息後終止。
- 需要值


### `--batch-size`

每批報文的數量。 僅適用於批次消費者。
- 需要值


### `--area-code`

首選區域（全局、adminhtml等……）預設為全局。
- 需要值


### `--single-thread`

此選項可防止同時執行一個使用者的多個復本。
- 預設值： `false`
- 不接受值


### `--multi-process`

每個消費者的程式數。
- 接受值


### `--pid-file-path`

用於保存PID的檔案路徑（不建議使用此選項，請改用單線程）
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `remote-storage:sync`

將媒體檔案與遠程儲存同步。

```bash
bin/magento remote-storage:sync
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `sampledata:deploy`

部署範例資料模組以進行撰寫器式Magento安裝

```bash
bin/magento sampledata:deploy [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

不執行撰寫器更新而更新composer.json
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `sampledata:remove`

從composer.json中移除所有範例資料套件

```bash
bin/magento sampledata:remove [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

不執行撰寫器更新而更新composer.json
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `sampledata:reset`

重置所有示例資料模組以重新安裝

```bash
bin/magento sampledata:reset
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-forgot-password`

管理員使用者忘記密碼表單停用reCAPTCHA

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-login`

為管理員使用者登入表單停用reCAPTCHA

```bash
bin/magento security:recaptcha:disable-for-user-login
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:tfa:google:set-secret`

設定用於產生Google OTP的機密。

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

<!-- app.name --> <!-- command.usage -->

### `user`

使用者名稱
- 必填

   <!-- argument -->

### `secret`

機密
- 必填

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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:tfa:providers`

列出所有可用的提供程式

```bash
bin/magento security:tfa:providers
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:tfa:reset`

重設一個使用者的設定

```bash
bin/magento security:tfa:reset <user> <provider>
```

<!-- app.name --> <!-- command.usage -->

### `user`

使用者名稱
- 必填

   <!-- argument -->

### `provider`

提供者代碼
- 必填

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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:backup`

備份Magento應用程式代碼庫、介質和資料庫

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--code`

執行代碼和配置檔案備份（不包括臨時檔案）
- 預設值： `false`
- 不接受值


### `--media`

進行介質備份
- 預設值： `false`
- 不接受值


### `--db`

進行完整資料庫備份
- 預設值： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:config:set`

建立或修改部署配置

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

後端Frontname（如果遺失則會自動產生）
- 需要值


### `--enable-debug-logging`

啟用偵錯記錄
- 需要值


### `--enable-syslog-logging`

啟用syslog日誌記錄
- 需要值


### `--remote-storage-driver`

遠程儲存驅動程式
- 需要值


### `--remote-storage-prefix`

遠程儲存前置詞
- 預設值：&quot;
- 需要值


### `--remote-storage-endpoint`

遠程儲存端點
- 需要值


### `--remote-storage-bucket`

遠端儲存貯體
- 需要值


### `--remote-storage-region`

遠程儲存區
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

Amqp virtualhost
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

消費者是否應等待來自佇列的訊息？ 1 — 是，0 — 否
- 需要值


### `--queue-default-connection`

消息隊列預設連接。 可以是&#39;db&#39;、&#39;amqp&#39;或自訂佇列系統。必須安裝並設定佇列系統，否則無法正確處理訊息。
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



如果指定，則跳過資料庫連接驗證
- 預設值： `false`
- 不接受值


### `--http-cache-hosts`

http快取主機
- 需要值


### `--db-ssl-key`

客戶端密鑰檔案的完整路徑，以便通過SSL建立資料庫連接
- 預設值：&quot;
- 需要值


### `--db-ssl-cert`

客戶端證書檔案的完整路徑，以便通過SSL建立資料庫連接
- 預設值：&quot;
- 需要值


### `--db-ssl-ca`

伺服器證書檔案的完整路徑，以便通過SSL建立資料庫連接
- 預設值：&quot;
- 需要值


### `--db-ssl-verify`

驗證伺服器認證
- 預設值： `false`
- 不接受值


### `--session-save`

會話保存處理程式
- 需要值


### `--session-save-redis-host`

使用UNIX套接字時，完全限定的主機名、IP地址或絕對路徑
- 需要值


### `--session-save-redis-port`

Redis伺服器偵聽埠
- 需要值


### `--session-save-redis-password`

密碼伺服器密碼
- 需要值


### `--session-save-redis-timeout`

連線逾時（秒）
- 需要值


### `--session-save-redis-persistent-id`

啟用永久連接的唯一字串
- 需要值


### `--session-save-redis-db`

密文資料庫號
- 需要值


### `--session-save-redis-compression-threshold`

減少壓縮閾值
- 需要值


### `--session-save-redis-compression-lib`

Redis壓縮庫。 值： gzip（預設值）、lzf、lz4、snappy
- 需要值


### `--session-save-redis-log-level`

密文日誌級別。 值：0（最少詳細）到7（最詳細）
- 需要值


### `--session-save-redis-max-concurrency`

可等待一個會話上鎖定的進程數上限
- 需要值


### `--session-save-redis-break-after-frontend`

嘗試中斷前端工作階段的鎖定之前等待的秒數
- 需要值


### `--session-save-redis-break-after-adminhtml`

嘗試中斷管理員工作階段的鎖定之前等待的秒數
- 需要值


### `--session-save-redis-first-lifetime`

第一次寫入時非機器人作業的存留期（以秒為單位）（使用0來停用）
- 需要值


### `--session-save-redis-bot-first-lifetime`

第一次寫入時機器人作業的存留期（以秒為單位）（使用0來停用）
- 需要值


### `--session-save-redis-bot-lifetime`

後續寫入時機器人作業的存留期（使用0停用）
- 需要值


### `--session-save-redis-disable-locking`

雷迪斯禁用鎖定。 值： false（預設值）, true
- 需要值


### `--session-save-redis-min-lifetime`

Redis最小工作階段存留期（以秒為單位）
- 需要值


### `--session-save-redis-max-lifetime`

紅色工作階段存留期（以秒為單位）
- 需要值


### `--session-save-redis-sentinel-master`

雷迪斯哨兵大師
- 需要值


### `--session-save-redis-sentinel-servers`

Redis Sentinel伺服器，逗號分隔
- 需要值


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主版。 值：false（預設）, true
- 需要值


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連接重試。
- 需要值


### `--cache-backend`

預設快取處理常式
- 需要值


### `--cache-backend-redis-server`

Redis伺服器
- 需要值


### `--cache-backend-redis-db`

快取的資料庫號
- 需要值


### `--cache-backend-redis-port`

Redis伺服器偵聽埠
- 需要值


### `--cache-backend-redis-password`

密碼伺服器密碼
- 需要值


### `--cache-backend-redis-compress-data`

設為0可停用壓縮（預設為1，已啟用）
- 需要值


### `--cache-backend-redis-compression-lib`

要使用的壓縮庫 [snappy,lzf,l4z,zstd,gzip] （保留為空白以自動決定）
- 需要值


### `--cache-id-prefix`

快取金鑰的ID首碼
- 需要值


### `--allow-parallel-generation`

允許以非阻塞方式生成快取
- 預設值： `false`
- 不接受值


### `--page-cache`

預設快取處理常式
- 需要值


### `--page-cache-redis-server`

Redis伺服器
- 需要值


### `--page-cache-redis-db`

快取的資料庫號
- 需要值


### `--page-cache-redis-port`

Redis伺服器偵聽埠
- 需要值


### `--page-cache-redis-password`

密碼伺服器密碼
- 需要值


### `--page-cache-redis-compress-data`

設為1可壓縮完整頁快取（使用0可禁用）
- 需要值


### `--page-cache-redis-compression-lib`

要使用的壓縮程式庫 [snappy,lzf,l4z,zstd,gzip] （保留為空白以自動決定）
- 需要值


### `--page-cache-id-prefix`

快取金鑰的ID首碼
- 需要值


### `--lock-provider`

鎖定提供程式名稱
- 需要值


### `--lock-db-prefix`

安裝特定的鎖定前置詞以避免鎖定衝突
- 需要值


### `--lock-zookeeper-host`

連接到Zookeeper群集的主機和埠。 例如：127.0.0.1:2181
- 需要值


### `--lock-zookeeper-path`

Zookeeper保存鎖的路徑。 預設路徑為：/magento/locks
- 需要值


### `--lock-file-path`

保存檔案鎖的路徑。
- 需要值


### `--document-root-is-pub`

要顯示的標幟為Pub位於根，只能是true或false
- 需要值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-data:upgrade`

在資料庫中安裝和升級資料

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-patch`

生成修補程式並將其放入特定資料夾。

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

<!-- app.name --> <!-- command.usage -->

### `module`

模組名稱
- 必填

   <!-- argument -->

### `patch`

修補程式名稱
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--revertable`

檢查修補程式是否可還原。
- 預設值： `false`
- 接受值


### `--type`

了解應生成的修補程式類型。 可用值： `data`, `schema`.
- 預設值： `data`
- 接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-whitelist`

生成允許由聲明安裝程式編輯的表和列的白名單

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--module-name`

將產生白名單的模組名稱
- 預設值： `all`
- 接受值



### `--help`, `-h`



顯示此幫助消息
- 預設值： `false`
- 不接受值



### `--quiet`, `-q`



不輸出任何消息
- 預設值： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-schema:upgrade`

安裝和升級資料庫架構

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式
- 預設值： `false`
- 接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db:status`

檢查資料庫架構或資料是否需要升級

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:di:compile`

生成DI配置和所有可自動生成的丟失類

```bash
bin/magento setup:di:compile
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:install`

安裝Magento應用程式

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

後端Frontname（如果遺失則會自動產生）
- 需要值


### `--enable-debug-logging`

啟用偵錯記錄
- 需要值


### `--enable-syslog-logging`

啟用syslog日誌記錄
- 需要值


### `--remote-storage-driver`

遠程儲存驅動程式
- 需要值


### `--remote-storage-prefix`

遠程儲存前置詞
- 預設值：&quot;
- 需要值


### `--remote-storage-endpoint`

遠程儲存端點
- 需要值


### `--remote-storage-bucket`

遠端儲存貯體
- 需要值


### `--remote-storage-region`

遠程儲存區
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

Amqp virtualhost
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

消費者是否應等待來自佇列的訊息？ 1 — 是，0 — 否
- 需要值


### `--queue-default-connection`

消息隊列預設連接。 可以是&#39;db&#39;、&#39;amqp&#39;或自訂佇列系統。必須安裝並設定佇列系統，否則無法正確處理訊息。
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



如果指定，則跳過資料庫連接驗證
- 預設值： `false`
- 不接受值


### `--http-cache-hosts`

http快取主機
- 需要值


### `--db-ssl-key`

客戶端密鑰檔案的完整路徑，以便通過SSL建立資料庫連接
- 預設值：&quot;
- 需要值


### `--db-ssl-cert`

客戶端證書檔案的完整路徑，以便通過SSL建立資料庫連接
- 預設值：&quot;
- 需要值


### `--db-ssl-ca`

伺服器證書檔案的完整路徑，以便通過SSL建立資料庫連接
- 預設值：&quot;
- 需要值


### `--db-ssl-verify`

驗證伺服器認證
- 預設值： `false`
- 不接受值


### `--session-save`

會話保存處理程式
- 需要值


### `--session-save-redis-host`

使用UNIX套接字時，完全限定的主機名、IP地址或絕對路徑
- 需要值


### `--session-save-redis-port`

Redis伺服器偵聽埠
- 需要值


### `--session-save-redis-password`

密碼伺服器密碼
- 需要值


### `--session-save-redis-timeout`

連線逾時（秒）
- 需要值


### `--session-save-redis-persistent-id`

啟用永久連接的唯一字串
- 需要值


### `--session-save-redis-db`

密文資料庫號
- 需要值


### `--session-save-redis-compression-threshold`

減少壓縮閾值
- 需要值


### `--session-save-redis-compression-lib`

Redis壓縮庫。 值： gzip（預設值）、lzf、lz4、snappy
- 需要值


### `--session-save-redis-log-level`

密文日誌級別。 值：0（最少詳細）到7（最詳細）
- 需要值


### `--session-save-redis-max-concurrency`

可等待一個會話上鎖定的進程數上限
- 需要值


### `--session-save-redis-break-after-frontend`

嘗試中斷前端工作階段的鎖定之前等待的秒數
- 需要值


### `--session-save-redis-break-after-adminhtml`

嘗試中斷管理員工作階段的鎖定之前等待的秒數
- 需要值


### `--session-save-redis-first-lifetime`

第一次寫入時非機器人作業的存留期（以秒為單位）（使用0來停用）
- 需要值


### `--session-save-redis-bot-first-lifetime`

第一次寫入時機器人作業的存留期（以秒為單位）（使用0來停用）
- 需要值


### `--session-save-redis-bot-lifetime`

後續寫入時機器人作業的存留期（使用0停用）
- 需要值


### `--session-save-redis-disable-locking`

雷迪斯禁用鎖定。 值： false（預設值）, true
- 需要值


### `--session-save-redis-min-lifetime`

Redis最小工作階段存留期（以秒為單位）
- 需要值


### `--session-save-redis-max-lifetime`

紅色工作階段存留期（以秒為單位）
- 需要值


### `--session-save-redis-sentinel-master`

雷迪斯哨兵大師
- 需要值


### `--session-save-redis-sentinel-servers`

Redis Sentinel伺服器，逗號分隔
- 需要值


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel驗證主版。 值：false（預設）, true
- 需要值


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel連接重試。
- 需要值


### `--cache-backend`

預設快取處理常式
- 需要值


### `--cache-backend-redis-server`

Redis伺服器
- 需要值


### `--cache-backend-redis-db`

快取的資料庫號
- 需要值


### `--cache-backend-redis-port`

Redis伺服器偵聽埠
- 需要值


### `--cache-backend-redis-password`

密碼伺服器密碼
- 需要值


### `--cache-backend-redis-compress-data`

設為0可停用壓縮（預設為1，已啟用）
- 需要值


### `--cache-backend-redis-compression-lib`

要使用的壓縮庫 [snappy,lzf,l4z,zstd,gzip] （保留為空白以自動決定）
- 需要值


### `--cache-id-prefix`

快取金鑰的ID首碼
- 需要值


### `--allow-parallel-generation`

允許以非阻塞方式生成快取
- 預設值： `false`
- 不接受值


### `--page-cache`

預設快取處理常式
- 需要值


### `--page-cache-redis-server`

Redis伺服器
- 需要值


### `--page-cache-redis-db`

快取的資料庫號
- 需要值


### `--page-cache-redis-port`

Redis伺服器偵聽埠
- 需要值


### `--page-cache-redis-password`

密碼伺服器密碼
- 需要值


### `--page-cache-redis-compress-data`

設為1可壓縮完整頁快取（使用0可禁用）
- 需要值


### `--page-cache-redis-compression-lib`

要使用的壓縮程式庫 [snappy,lzf,l4z,zstd,gzip] （保留為空白以自動決定）
- 需要值


### `--page-cache-id-prefix`

快取金鑰的ID首碼
- 需要值


### `--lock-provider`

鎖定提供程式名稱
- 需要值


### `--lock-db-prefix`

安裝特定的鎖定前置詞以避免鎖定衝突
- 需要值


### `--lock-zookeeper-host`

連接到Zookeeper群集的主機和埠。 例如：127.0.0.1:2181
- 需要值


### `--lock-zookeeper-path`

Zookeeper保存鎖的路徑。 預設路徑為：/magento/locks
- 需要值


### `--lock-file-path`

保存檔案鎖的路徑。
- 需要值


### `--document-root-is-pub`

要顯示的標幟為Pub位於根，只能是true或false
- 需要值


### `--base-url`

商店的URL應可在使用。 已棄用，請使用config:set with path web/unsecure/base_url
- 需要值


### `--language`

預設語言代碼。 已棄用，請使用config:set與路徑一般/地區/代碼一起使用
- 需要值


### `--timezone`

預設時區代碼。 已棄用，請使用config:set與路徑一般/地區/時區
- 需要值


### `--currency`

預設貨幣代碼。 已棄用，請使用config:set with path currency/options/base, currency/options/default, and currency/options/allow
- 需要值


### `--use-rewrites`

使用重寫。 已棄用，請使用config:set與路徑web/seo/use_rewrites一起使用
- 需要值


### `--use-secure`

使用安全URL。 僅在SSL可用時啟用此選項。 已棄用，請使用config:set與路徑web/secure/use_in_frontend一起使用
- 需要值


### `--base-url-secure`

SSL連線的基礎URL。 已棄用，請使用config:set with path web/secure/base_url
- 需要值


### `--use-secure-admin`

使用SSL執行管理介面。 已棄用，請使用config:set與路徑web/secure/use_in_adminhtml一起使用
- 需要值


### `--admin-use-security-key`

是否在Magento管理URL和表單中使用「安全索引鍵」功能。 已棄用，請使用config:set與路徑admin/security/use_form_key一起使用
- 需要值


### `--admin-user`

管理員使用者
- 接受值


### `--admin-password`

管理員密碼
- 接受值


### `--admin-email`

管理電子郵件
- 接受值


### `--admin-firstname`

管理員名字
- 接受值


### `--admin-lastname`

管理員姓氏
- 接受值


### `--search-engine`

搜尋引擎。 值：elasticsearch5, elasticsearch6, elasticsearch7
- 需要值


### `--elasticsearch-host`

Elasticsearch伺服器主機。
- 需要值


### `--elasticsearch-port`

Elasticsearch伺服器埠。
- 需要值


### `--elasticsearch-enable-auth`

設為1以啟用驗證。 （預設為0，已停用）
- 需要值


### `--elasticsearch-username`

Elasticsearch使用者名稱。 僅適用於啟用HTTP驗證時
- 需要值


### `--elasticsearch-password`

Elasticsearch密碼。 僅適用於啟用HTTP驗證時
- 需要值


### `--elasticsearch-index-prefix`

Elasticsearch索引前置詞。
- 需要值


### `--elasticsearch-timeout`

Elasticsearch伺服器逾時。
- 需要值


### `--cleanup-database`

在安裝之前清除資料庫
- 預設值： `false`
- 不接受值


### `--sales-order-increment-prefix`

銷售訂單編號前置詞
- 需要值


### `--use-sample-data`

使用範例資料
- 預設值： `false`
- 不接受值


### `--enable-modules`

以逗號分隔的模組名稱清單。 安裝期間必須包含此資訊。 可用的魔術參數為&quot;all&quot;。
- 接受值


### `--disable-modules`

以逗號分隔的模組名稱清單。 在安裝期間必須避免此情況。 可用的魔術參數為&quot;all&quot;。
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

安全安裝帶有破壞性操作轉儲（如列刪除）的Magento
- 接受值


### `--data-restore`

從轉儲中還原已刪除的資料
- 接受值


### `--dry-run`

Magento安裝將以乾式運行模式運行
- 預設值： `false`
- 接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:performance:generate-fixtures`

生成夾具

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

<!-- app.name --> <!-- command.usage -->

### `profile`

配置檔案配置檔案的路徑
- 必填

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-reindex`, `-s`



跳過重新索引
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:rollback`

回退Magento應用程式代碼庫、媒體和資料庫

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--code-file`, `-c`



var/backups中代碼備份檔案的基本名稱
- 需要值



### `--media-file`, `-m`



var/backups中介質備份檔案的基本名稱
- 需要值



### `--db-file`, `-d`



var/backups中資料庫備份檔案的基本名稱
- 需要值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:static-content:deploy`

部署靜態檢視檔案

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

<!-- app.name --> <!-- command.usage -->

### `languages`

要輸出靜態視圖檔案的ISO-639語言代碼的空格分隔清單。

- 預設值： `[]`

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



以任何模式部署檔案。
- 預設值： `false`
- 不接受值



### `--strategy`, `-s`



使用指定策略部署檔案。
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



僅生成指定主題的靜態視圖檔案。
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

為這些區域設定的檔案建立符號連結，這些檔案為部署而傳遞，但沒有自定義。
- 預設值： `false`
- 不接受值


### `--content-version`

如果在多個節點上執行部署，則可使用靜態內容的自訂版本，以確保靜態內容版本相同且快取正常運作。
- 需要值


### `--refresh-content-version-only`

只能使用重新整理靜態內容版本來重新整理瀏覽器快取和CDN快取中的靜態內容。
- 預設值： `false`
- 不接受值


### `--no-javascript`

請勿部署JavaScript檔案。
- 預設值： `false`
- 不接受值


### `--no-js-bundle`

請勿部署JavaScript套件組合檔案。
- 預設值： `false`
- 不接受值


### `--no-css`

請勿部署CSS檔案。
- 預設值： `false`
- 不接受值


### `--no-less`

請勿部署LESS檔案。
- 預設值： `false`
- 不接受值


### `--no-images`

請勿部署映像。
- 預設值： `false`
- 不接受值


### `--no-fonts`

請勿部署字型檔案。
- 預設值： `false`
- 不接受值


### `--no-html`

請勿部署HTML檔案。
- 預設值： `false`
- 不接受值


### `--no-misc`

請勿部署其他類型的檔案（.md、.jbf、.csv等）。
- 預設值： `false`
- 不接受值


### `--no-html-minify`

請勿縮制HTML檔案。
- 預設值： `false`
- 不接受值


### `--no-parent`

不編譯父主題。 僅支援快速標準策略。
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:store-config:set`

安裝儲存配置。 自2.2.0起已棄用。請改用config:set

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--base-url`

商店的URL應可在使用。 已棄用，請使用config:set with path web/unsecure/base_url
- 需要值


### `--language`

預設語言代碼。 已棄用，請使用config:set與路徑一般/地區/代碼一起使用
- 需要值


### `--timezone`

預設時區代碼。 已棄用，請使用config:set與路徑一般/地區/時區
- 需要值


### `--currency`

預設貨幣代碼。 已棄用，請使用config:set with path currency/options/base, currency/options/default, and currency/options/allow
- 需要值


### `--use-rewrites`

使用重寫。 已棄用，請使用config:set與路徑web/seo/use_rewrites一起使用
- 需要值


### `--use-secure`

使用安全URL。 僅在SSL可用時啟用此選項。 已棄用，請使用config:set與路徑web/secure/use_in_frontend一起使用
- 需要值


### `--base-url-secure`

SSL連線的基礎URL。 已棄用，請使用config:set with path web/secure/base_url
- 需要值


### `--use-secure-admin`

使用SSL執行管理介面。 已棄用，請使用config:set與路徑web/secure/use_in_adminhtml一起使用
- 需要值


### `--admin-use-security-key`

是否在Magento管理URL和表單中使用「安全索引鍵」功能。 已棄用，請使用config:set與路徑admin/security/use_form_key一起使用
- 需要值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:uninstall`

卸載Magento應用程式

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:upgrade`

升級Magento應用程式、資料庫資料和架構

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep-generated`

防止刪除生成的檔案。 除了部署至生產環境時，我們不勸阻使用此選項。 有關詳細資訊，請咨詢您的系統整合商或管理員。
- 預設值： `false`
- 不接受值


### `--convert-old-scripts`

允許將舊指令碼(InstallSchema、UpgradeSchema)轉換為db_schema.xml格式
- 預設值： `false`
- 接受值


### `--safe-mode`

安全安裝帶有破壞性操作轉儲（如列刪除）的Magento
- 接受值


### `--data-restore`

從轉儲中還原已刪除的資料
- 接受值


### `--dry-run`

Magento安裝將以乾式運行模式運行
- 預設值： `false`
- 接受值


### `--magento-init-params`

添加到任何命令以自定義Magento初始化參數例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基礎][path]=/var/www/example.com&amp;MAGE_DIRS[快取][path]=/var/tmp/cache」
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `store:list`

顯示商店清單

```bash
bin/magento store:list
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `store:website:list`

顯示網站清單

```bash
bin/magento store:website:list
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `theme:uninstall`

卸載主題

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

<!-- app.name --> <!-- command.usage -->

### `theme`

主題的路徑。 主題路徑應指定為完整路徑，即區域/供應商/名稱。 例如前端/Magento/空白

- 預設值： `[]`
- 必填

- 陣列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--backup-code`

執行代碼備份（不包括臨時檔案）
- 預設值： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的靜態視圖檔案。
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `varnish:vcl:generate`

生成清漆VCL並回聲到命令行

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access-list`

可清除清漆的IP訪問清單
- 預設值： `localhost`
- 需要值


### `--backend-host`

Web後端的主機
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

寬限期（以秒為單位）
- 預設值： `300`
- 需要值


### `--output-file`

要寫入vcl的檔案路徑
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



增加訊息的詳細程度：正常輸出為1，較詳細輸出為2，除錯為3
- 預設值： `false`
- 不接受值



### `--version`, `-V`



顯示此應用程式版本
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



### `--no-interaction`, `-n`



不要提出任何互動式問題
- 預設值： `false`
- 不接受值 <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->