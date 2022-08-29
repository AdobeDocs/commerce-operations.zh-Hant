---
title: 遷移概述
description: 瞭解如何開始將資料從Magento1遷移到Magento2, [!DNL Data Migration Tool]。
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# 遷移概述

開始遷移之前，請停止所有Magento1 cron作業。

在遷移過程中，請遵循以下常規規則成功遷移：

1. **不要** 在Magento1管理中進行更改，但訂單管理（發運、建立發票和貸項通知單）除外
1. **不要** 更改任何代碼
1. **不要** 更改Magento2管理員和 [店面](https://glossary.magento.com/storefront)

>[!TIP]
>
>允許Magento1店面中的所有操作。

## 運行 [!DNL Data Migration Tool]

本部分說明如何運行 [!DNL Data Migration Tool] 遷移設定、資料或增量更改。

### 第一步

1. 以具有向檔案系統寫入權限的用戶身份或切換到身份登錄到應用程式伺服器。 請參閱 [切換到檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。

   如果使用bash shell，則可以使用以下語法切換到檔案系統所有者並同時輸入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果檔案系統所有者不允許登錄，可以執行以下操作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 要從任何目錄運行Magento命令，請添加 `<magento_root>/bin` 到系統 `PATH`。

   由於shell的語法不同，因此請參考引用，如 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)。

   CentOS的bash shell示例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   （可選）您可以通過以下方式運行命令：

   - `cd <magento_root>/bin` 把它們 `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` 是Web伺服器docroot的子目錄。

除此處提及的命令參數外，請參見 [常見參數](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands.html#instgde-cli-subcommands-common)

### 命令語法

下面是典型的命令示例：

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

位置：

- `<mode>` 可能： [`settings`](settings.md)。 [`data`](data.md)或 [`delta`](delta.md)
- `[-r|--reset]` 是從頭開始遷移的可選參數。 您可以使用此參數來測試遷移。
- `[-a|--auto]` 是一個可選參數，可防止在遇到完整性檢查錯誤時停止遷移。
- `{<path to config.xml>}` 是到 `config.xml`;此參數是必需的。

>[!NOTE]
>
>日誌寫入 `<magento_root>/var/` 的子菜單。


## 遷移順序

建立 [!DNL Data Migration Tool]，我們假定了以下資料傳輸序列：

1. [設定](settings.md)
1. [資料](data.md)
1. [更改](delta.md)

我們強烈建議按相同順序遷移資料。
