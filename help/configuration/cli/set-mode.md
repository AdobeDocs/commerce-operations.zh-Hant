---
title: 設定作業模式
description: 閱讀有關設定Adobe Commerce操作模式的資訊。
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# 設定作業模式

{{file-system-owner}}

為了改善安全性與易用性，我們新增了將[應用程式模式](../bootstrap/application-modes.md)從開發人員切換至生產環境，反之亦然。

生產模式的效能較佳，因為靜態檢視檔案已填入`pub/static`目錄，而且因為程式碼編譯。

>[!INFO]
>
>在2.0.6版或更新版本中，當您在預設、開發和生產模式之間切換時，Commerce不會明確設定檔案或目錄許可權。 與其他模式不同，開發人員和生產模式設定在`env.php`檔案中。 雲端基礎結構上的Adobe Commerce僅支援生產和維護模式。
>
>檢視開發和生產中的[Commerce擁有權和許可權](../deployment/file-system-permissions.md)。

當您變更為開發人員或生產模式時，我們會清除以下目錄的內容：

```
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- 未移除`.htaccess`個檔案
- `pub/static`包含指定靜態內容版本的檔案；此檔案未移除

>[!INFO]
>
>依預設，Commerce會使用`var`目錄來儲存快取、記錄檔和編譯的程式碼。 您可以自訂此目錄，但本指南假設為`var`。

## 顯示目前模式

最簡單的方法就是以[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)的身份執行此命令。 如果您有共用託管，這是提供者可讓您登入伺服器的使用者。 如果您有私人伺服器，則通常是Commerce伺服器上的本機使用者帳戶。

命令使用方式：

```bash
bin/magento deploy:mode:show
```

系統會顯示類似下列的訊息：

```
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

其中：

- **`{mode}`**&#x200B;可以是`default`、`developer`或`production`

## 變更模式

命令使用方式：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

其中：

- **`{mode}`**&#x200B;為必要項；它可以是`developer`或`production`

- **`--skip-compilation`**&#x200B;是選用引數，當您變更至生產模式時，可用來略過[程式碼編譯](../cli/code-compiler.md)。

範例如下。

### 變更為生產模式

```bash
bin/magento deploy:mode:set production
```

類似下列顯示的訊息：

```
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

當您從生產模式變更為開發人員模式時，您應該清除產生的類別和Object Manager實體（例如代理程式），以避免意外的錯誤。 執行此操作後，您可以變更模式。 使用下列步驟：

1. 如果您要從生產模式變更為開發人員模式，請刪除`generated/code`和`generated/metadata`目錄的內容：

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. 設定模式：

   ```bash
   bin/magento deploy:mode:set developer
   ```

   系統會顯示下列訊息：

   ```
   Enabled developer mode.
   ```

### 變更為預設模式

```bash
bin/magento deploy:mode:set default
```

系統會顯示下列訊息：

```
Enabled default mode.
```

### 隨處執行CLI命令

[從任何地方執行CLI命令](../cli/config-cli.md#config-install-cli-first)。

如果您尚未將`<Commerce-install-directory>/bin`新增至系統`PATH`，則自行執行命令時可能會發生錯誤。
