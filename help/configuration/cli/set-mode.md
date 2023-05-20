---
title: 設定操作模式
description: 閱讀有關設定Adobe Commerce操作模式的資訊。
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 設定操作模式

{{file-system-owner}}

為了提高安全性和易用性，我們添加了一個命令 [應用模式](../bootstrap/application-modes.md) 從開發商到生產商，反之亦然。

生產模式具有更好的效能，因為靜態視圖檔案填充在 `pub/static` 和因為代碼編譯。

>[!INFO]
>
>在2.0.6版和更高版本中，當您在預設、開發和生產模式之間切換時，Commerce不會顯式設定檔案或目錄權限。 與其他模式不同，在 `env.php` 的子菜單。 Adobe Commerce雲基礎架構僅支援生產和維護模式。
>
>請參閱 [商業所有權和開發和生產許可](../deployment/file-system-permissions.md)。

當您更改為開發人員或生產模式時，我們將清除以下目錄的內容：

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` 檔案未刪除
- `pub/static` 包含指定靜態內容版本的檔案；未刪除此檔案

>[!INFO]
>
>預設情況下，Commerce使用 `var` 儲存快取、日誌和編譯代碼的目錄。 您可以自定義此目錄，但在本指南中，假定它是 `var`。

## 顯示當前模式

執行此操作的最簡單方法是將此命令作為 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。 如果您有共用主機，則這是您的提供程式授予您登錄到伺服器的用戶。 如果您有專用伺服器，則它通常是Commerce伺服器上的本地用戶帳戶。

命令用法：

```bash
bin/magento deploy:mode:show
```

將顯示一條類似以下消息：

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

其中：

- **`{mode}`** 可以 `default`。 `developer`或 `production`

## 更改模式

命令用法：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

其中：

- **`{mode}`** 需要；它可以 `developer` 或 `production`

- **`--skip-compilation`** 是可用於跳過的可選參數 [代碼編譯](../cli/code-compiler.md) 的子菜單。

例子如下。

### 更改為生產模式

```bash
bin/magento deploy:mode:set production
```

類似於以下顯示的消息：

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

### 更改為開發人員模式

在從生產模式更改為開發模式時，應清除生成的類和Object Manager實體（如代理），以防止意外錯誤。 這樣做後，可以更改模式。 請執行以下步驟：

1. 如果要從生產模式更改為開發模式，請刪除 `generated/code` 和 `generated/metadata` 目錄：

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. 設定模式：

   ```bash
   bin/magento deploy:mode:set developer
   ```

   將顯示以下消息：

   ```terminal
   Enabled developer mode.
   ```

### 更改為預設模式

```bash
bin/magento deploy:mode:set default
```

將顯示以下消息：

```terminal
Enabled default mode.
```

### 從任何位置運行CLI命令

[從任何位置運行CLI命令](../cli/config-cli.md#config-install-cli-first)。

如果尚未添加 `<Commerce-install-directory>/bin` 到系統 `PATH`，則在自行運行命令時可能會出錯。
