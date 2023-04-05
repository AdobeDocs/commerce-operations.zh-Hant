---
title: 設定操作模式
description: 閱讀有關設定Adobe Commerce操作模式的資訊。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# 設定操作模式

{{file-system-owner}}

為了提高安全性和易用性，我們添加了一個命令，用於切換 [應用模式](../bootstrap/application-modes.md) 從開發人員到生產人員，反之亦然。

生產模式的效能較佳，因為靜態檢視檔案會填入 `pub/static` 目錄和，因為程式碼編譯。

>[!INFO]
>
>在2.0.6版及更新版本中，當您在預設、開發和生產模式之間切換時，商務不會明確設定檔案或目錄權限。 與其他模式不同，開發人員和生產模式會設定在 `env.php` 檔案。 Adobe Commerce on cloud infrastructure僅支援生產和維護模式。
>
>請參閱 [開發和生產中的商務所有權和權限](../deployment/file-system-permissions.md).

當您變更為開發人員或生產模式時，我們會清除下列目錄的內容：

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` 檔案未移除
- `pub/static` 包含指定靜態內容版本的檔案；此檔案未刪除

>[!INFO]
>
>依預設，商務會使用 `var` 用於儲存快取、日誌和已編譯代碼的目錄。 您可以自訂此目錄，但在本指南中，假設 `var`.

## 顯示當前模式

要執行此操作，最簡單的方法是運行此命令作為 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md). 如果您有共用托管，這是您的提供者提供您登入伺服器的使用者。 如果您有專用伺服器，則它通常是商務伺服器上的本地用戶帳戶。

命令用法：

```bash
bin/magento deploy:mode:show
```

畫面上會顯示類似下列的訊息：

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

其中：

- **`{mode}`** 可以是 `default`, `developer`，或 `production`

## 變更模式

命令用法：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

其中：

- **`{mode}`** 為必要項目；它可以是 `developer` 或 `production`

- **`--skip-compilation`** 是可用來略過的選用參數 [代碼編譯](../cli/code-compiler.md) 當您變更為生產模式時。

範例如下。

### 變更為生產模式

```bash
bin/magento deploy:mode:set production
```

顯示的訊息類似下列：

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### 變更為開發人員模式

從生產模式更改為開發人員模式時，應清除生成的類和對象管理器實體（如代理），以防止出現意外錯誤。 執行此動作後，您可以變更模式。 使用下列步驟：

1. 如果您要從生產模式變更為開發人員模式，請刪除 `generated/code` 和 `generated/metadata` 目錄：

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. 設定模式：

   ```bash
   bin/magento deploy:mode:set developer
   ```

   會顯示下列訊息：

   ```terminal
   Enabled developer mode.
   ```

### 變更為預設模式

```bash
bin/magento deploy:mode:set default
```

會顯示下列訊息：

```terminal
Enabled default mode.
```

### 從任何位置運行CLI命令

[從任何位置運行CLI命令](../cli/config-cli.md#config-install-cli-first).

如果您尚未新增 `<Commerce-install-directory>/bin` 系統 `PATH`，則單獨運行命令時可能會出現錯誤。
