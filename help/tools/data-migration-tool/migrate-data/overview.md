---
title: 移轉概觀
description: 了解如何使用將資料從Magento1移轉至Magento2 [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# 移轉概觀

開始移轉前，請停止所有Magento1 cron作業。

在移轉程式中，請遵循下列一般規則，順利移轉：

1. **不要** 在「Magento1管理員」中進行更改，但訂單管理（發運、建立發票和貸項通知單）除外
1. **不要** 更改任何代碼
1. **不要** 在「Magento2管理員」中進行變更，並 [店面](https://glossary.magento.com/storefront)

>[!TIP]
>
>允許Magento1店面中的所有操作。

## 執行 [!DNL Data Migration Tool]

本節說明如何執行 [!DNL Data Migration Tool] 移轉設定、資料或增量變更。

### 第一步

1. 以具有向檔案系統寫入權限的用戶身份或切換到該用戶身份登錄到應用程式伺服器。 請參閱 [切換到檔案系統所有者](../../../installation/prerequisites/file-system/overview.md).

   如果使用bash shell，則可以使用以下語法切換到檔案系統所有者並同時輸入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果檔案系統擁有者不允許登入，您可以執行下列操作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 要從任何目錄運行Magento命令，請添加 `<magento_root>/bin` 系統 `PATH`.

   由於殼的語法不同，因此請查詢引用，如 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS的bash shell範例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   或者，您可以以下列方式運行命令：

   - `cd <magento_root>/bin` 以 `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` 是Web伺服器docroot的子目錄。

### 命令語法

以下是典型的命令範例：

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

- `<mode>` 可能是： [`settings`](settings.md), [`data`](data.md)，或 [`delta`](delta.md)
- `[-r|--reset]` 是從頭開始移轉的選用引數。 您可以使用此引數來測試移轉。
- `[-a|--auto]` 是可選引數，當遇到完整性檢查錯誤時，該引數會阻止遷移停止。
- `{<path to config.xml>}` 是的絕對檔案系統路徑 `config.xml`;此引數為必要項目。

>[!NOTE]
>
>記錄會寫入 `<magento_root>/var/` 目錄。


## 移轉順序

當我們建立 [!DNL Data Migration Tool]，我們假定了下列資料傳輸順序：

1. [設定](settings.md)
1. [資料](data.md)
1. [變更](delta.md)

強烈建議您以相同順序移轉資料。
