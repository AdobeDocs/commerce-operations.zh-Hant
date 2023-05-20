---
title: 部署靜態視圖檔案
description: 學習在生產模式期間將靜態檔案寫入Commerce檔案系統。
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# 部署靜態視圖檔案

{{file-system-owner}}

使用靜態視圖檔案部署命令，可以在為Commerce軟體設定時將靜態檔案寫入Commerce檔案系統 [生產模式](../bootstrap/application-modes.md#production-mode)。

術語 _靜態視圖檔案_ 指：

- 「靜態」表示可以為站點快取該檔案（即，檔案不是動態生成的）。 示例包括從LESS生成的影像和CSS。
- 「視圖」是指表示層（從MVC）。

靜態視圖檔案位於 `<magento_root>/pub/static` 目錄中，有些快取在 `<magento_root>/var/view_preprocessed` 的下界。

靜態視圖檔案部署受應用程式模式的影響，如下所示：

- [預設](../bootstrap/application-modes.md#default-mode) 和 [開發者](../bootstrap/application-modes.md#developer-mode) 模式：Commerce會按需生成這些檔案，但其餘檔案會快取到檔案中以加快訪問速度。
- [生產](../bootstrap/application-modes.md#production-mode) 模式：靜態檔案為 _不_ 生成或快取。

必須使用本主題中討論的命令手動將靜態視圖檔案寫入Commerce檔案系統；之後，您可以限制權限以限制漏洞並防止意外或惡意覆蓋檔案。

>[!WARNING]
>
>_僅開發人員模式_:安裝或啟用新模組時，它可能會載入新的JavaScript、CSS、佈局等。 要避免靜態檔案出現問題，必須清除舊檔案，以確保獲得新模組的所有更改。 可以通過多種方式清除生成的靜態視圖檔案。 請參閱 [清除靜態檔案快取主題以瞭解詳細資訊](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) 的子菜單。

**部署靜態視圖檔案**:

1. 以或 [切換到檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 刪除 `<magento_root>/pub/static`，但 `.htaccess` 的子菜單。 不要刪除此檔案。
1. 運行靜態視圖檔案部署工具 `<magento_root>/bin/magento setup:static-content:deploy`。

   >[!INFO]
   >
   >如果在管理中啟用靜態視圖檔案合併， `pub/static` 目錄系統必須可寫。

   命令選項：

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

下表說明了此命令的參數和值。

| 選項 | 說明 | 需要？ |
| ------ | ----------- | --------- |
| `<languages>` | 空格分隔清單 [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) 要輸出靜態視圖檔案的語言代碼。 (預設值為 `en_US`。)<br>通過運行： `bin/magento info:language:list` | 否 |
| `--language (-l)` | 僅生成指定語言的檔案。 預設值是為所有ISO-639語言代碼生成檔案，但未指定任何選項。 一次可以指定一個語言代碼的名稱。 預設值為 **全部**。<br>例如： `--language en_US --language es_ES` | 否 |
| `--exclude-language` | 生成指定語言代碼的檔案。 預設值是不排除任何選項。 可以指定一種語言代碼的名稱或以逗號分隔的語言代碼清單。 預設值為 **無**。 | 否 |
| `--theme <theme>` | 要部署靜態內容的主題。 預設值為 **全部**。<br>例如： `--theme Magento/blank --theme Magento/luma` | 否 |
| `--exclude-theme <theme>` | 部署靜態內容時要排除的主題。 預設值為 **無**。<br>比如說， `--exclude-theme Magento/blank` | 否 |
| `--area (-a)` | 僅為指定區域生成檔案。 預設值是為所有區域生成檔案，但未指定任何選項。 有效值為 `adminhtml` 和 `frontend`。 預設值為 **全部**。<br>例如： `--area adminhtml` | 否 |
| `--exclude-area` | 不為指定區域生成檔案。 預設值是不排除任何選項。 預設值為 **無**。 | 否 |
| `--jobs (-j)` | 使用指定的作業數啟用並行處理。 預設值為0（不在並行進程中運行）。 預設值為 **0**。 | 否 |
| `--symlink-locale` | 為那些為部署傳遞但沒有自定義的區域設定的檔案建立符號連結。 | 否 |
| `--content-version=CONTENT-VERSION` | 如果在多個節點上運行部署，以確保靜態內容版本相同且快取工作正常，則可以使用靜態內容的自定義版本。 | 否 |
| `--no-javascript` | 不部署JavaScript檔案 | 否 |
| `--no-css` | 不要部署CSS檔案。 | 否 |
| `--no-less` | 不要部署LESS檔案。 | 否 |
| `--no-images` | 不部署映像。 | 否 |
| `--no-fonts` | 不部署字型檔案。 | 否 |
| `--no-html` | 不部署HTML檔案。 | 否 |
| `--no-misc` | 不部署其他類型的檔案：MD、JBF、CSV、JSON、TXT、HTC、SWF | 否 |
| `--no-html-minify` | 不要小化HTML檔案。 | 否 |
| `-s <quick\|standard\|compact>` | 定義部署策略。 僅當您有多個本地選項時才使用這些選項。<ul><li>使用 [快速策略](static-view-file-strategy.md#quick-strategy) 以最小化部署時間。 如果未指定，則為預設命令選項。</li><li>使用 [標準策略](static-view-file-strategy.md#standard-strategy) 部署所有包的所有靜態視圖檔案。</li><li>使用 [緊湊策略](static-view-file-strategy.md#compact-strategy) 以節省伺服器上的磁碟空間。</li></ul> | 否 |
| `--no-parent` | 不為當前主題的父主題生成檔案。 如果您未明確使用您嘗試部署的當前主題的父主題，強烈建議使用此標誌。 這顯著地提高了處理速度。 此標誌在Commerce 2.4.2中可用 | 否 |
| `--force (-f)` | 以任何模式部署檔案。 (預設情況下，靜態內容部署工具只能在生產模式下運行。 使用此選項在預設或開發模式下運行它)。 | 否 |

>[!INFO]
>
>如果同時為兩者指定值 `<languages>` 和 `--language`。 `<languages>` 優先。

## 示例

下面是一些示例命令。

### 排除主題和HTML縮小

以下命令為美國英語部署靜態內容(`en_US`)語言，不包括Commerce提供的Luma主題，並且不會減小HTML檔案。

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

示例輸出：

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

以下命令只使用標準部署策略部署帶有4個作業的JavaScript:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

以下命令僅部署CSS和LESS，其中包含3個作業，並部署快速部署策略：

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 為一個主題和一個區域生成靜態視圖檔案

以下命令為所有語言生成靜態視圖檔案，僅前端區域，僅Commerce Luma主題，而不生成字型：

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

示例輸出：

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## 部署靜態視圖檔案而不安裝Commerce

您可能希望在單獨的非生產環境中運行部署過程，以避免在敏感的生產電腦上執行任何生成過程。

為此，請執行以下步驟：

1. 運行 [`bin/magento app:config:dump`](../cli/export-configuration.md) 從生產系統導出配置。
1. 將導出的檔案複製到非生產代碼庫。
1. 部署靜態視圖檔案： `bin/magento setup:static-content:deploy`

## 對靜態視圖檔案部署工具進行故障排除

[首先安裝Commerce軟體](../../installation/overview.md);否則，無法運行靜態視圖檔案部署工具。

**症狀**:運行靜態視圖檔案部署工具時，將顯示以下錯誤：

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**解決方案**:

請執行以下步驟：

1. 使用 [命令行](../../installation/composer.md)。
1. 以或 [切換到](../../installation/prerequisites/file-system/overview.md)，檔案系統所有者。
1. 刪除 `<app_root>/pub/static` 目錄，但 `.htaccess` 的子菜單。 不要刪除此檔案。
1. 部署靜態視圖檔案： `bin/magento setup:static-content:deploy`

## 開發人員自定義靜態內容部署工具的提示

在建立靜態內容部署工具的自定義實現時，只對客戶端上應可用的檔案使用原子檔案寫入。 如果使用非原子檔案寫入，則這些檔案可能會載入到客戶端上，並包含部分內容。

使其具有原子性的選項之一是，寫入到臨時目錄中儲存的檔案，並在寫入結束後將它們複製或移動到目標目錄（從這些檔案載入到客戶端的位置）。 有關寫入檔案的詳細資訊，請參閱 [php fwrite](https://www.php.net/manual/en/function.fwrite.php)。
