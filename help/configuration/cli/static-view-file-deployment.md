---
title: 部署靜態視圖檔案
description: 了解如何在生產模式期間將靜態檔案寫入商務檔案系統。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---


# 部署靜態視圖檔案

{{file-system-owner}}

使用靜態視圖檔案部署命令可以寫 [靜態檔案](https://glossary.magento.com/static-files) 當商務軟體設定為 [生產模式](../bootstrap/application-modes.md#production-mode).

詞語 _靜態檢視檔案_ 是指下列項目：

- 「靜態」表示可對網站快取該檔案（即不會動態產生檔案）。 範例包括從LESS產生的影像和CSS。
- 「檢視」是指展示層（來自MVC）。

靜態檢視檔案位於 `<magento_root>/pub/static` 目錄中，有些快取於 `<magento_root>/var/view_preprocessed` 目錄。

靜態檢視檔案部署受應用程式模式影響，如下所示：

- [預設](../bootstrap/application-modes.md#default-mode) 和 [開發人員](../bootstrap/application-modes.md#developer-mode) 模式：商務會隨選產生，但其餘會快取至檔案中，以提高存取速度。
- [生產](../bootstrap/application-modes.md#production-mode) 模式：靜態檔案為 _not_ 產生或快取。

必須使用本主題中討論的命令手動將靜態視圖檔案寫入Commerce檔案系統；之後，您可以限制權限以限制您的漏洞，並防止意外或惡意覆寫檔案。

>[!WARNING]
>
>_僅開發人員模式_:安裝或啟用新模組時，可能會載入新的JavaScript、CSS、配置等。 若要避免靜態檔案的問題，您必須清除舊檔案，以確定您收到新模組的所有變更。 您可以透過數種方式清除產生的靜態檢視檔案。 請參閱 [清除靜態檔案快取主題以了解詳細資訊](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) 以取得更多資訊。

**部署靜態視圖檔案**:

1. 以或登入Commerce伺服器 [切換到檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 刪除 `<magento_root>/pub/static`，但 `.htaccess` 檔案。 請勿刪除此檔案。
1. 運行靜態視圖檔案部署工具 `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >如果您在「管理員」中啟用靜態檢視檔案合併，則 `pub/static` 目錄系統必須可寫。

   命令選項：

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

下表說明此命令的參數和值。

| 選項 | 說明 | 必要？ |
| ------ | ----------- | --------- |
| `<languages>` | 以空格分隔的清單 [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) 要輸出靜態視圖檔案的語言代碼。 (預設為 `en_US`.)<br>運行以查找清單： `bin/magento info:language:list` | 否 |
| `--language (-l)` | 僅生成指定語言的檔案。 預設值是為所有ISO-639語言代碼生成檔案，未指定任何選項。 一次可以指定一個語言代碼的名稱。 預設值為 **all**.<br>例如： `--language en_US --language es_ES` | 否 |
| `--exclude-language` | 生成指定語言代碼的檔案。 預設值（未指定選項）是不排除任何項目。 您可以指定一個語言代碼的名稱或以逗號分隔的語言代碼清單。 預設值為 **無**. | 否 |
| `--theme <theme>` | 要部署靜態內容的主題。 預設值為 **all**.<br>例如： `--theme Magento/blank --theme Magento/luma` | 否 |
| `--exclude-theme <theme>` | 部署靜態內容時要排除的主題。 預設值為 **無**.<br>例如， `--exclude-theme Magento/blank` | 否 |
| `--area (-a)` | 僅為指定區域生成檔案。 預設值是為所有區域生成檔案，未指定選項。 有效值為 `adminhtml` 和 `frontend`. 預設值為 **all**.<br>例如： `--area adminhtml` | 否 |
| `--exclude-area` | 不為指定區域生成檔案。 預設值（未指定選項）是不排除任何項目。 預設值為 **無**. | 否 |
| `--jobs (-j)` | 使用指定的作業數啟用並行處理。 預設值為0（不在並行進程中運行）。 預設值為 **0**. | 否 |
| `--symlink-locale` | 為這些區域設定的檔案建立符號連結，這些檔案為部署而傳遞，但沒有自定義。 | 否 |
| `--content-version=CONTENT-VERSION` | 如果在多個節點上執行部署，則可使用靜態內容的自訂版本，以確保靜態內容版本相同且快取正常運作。 | 否 |
| `--no-javascript` | 不部署JavaScript檔案 | 否 |
| `--no-css` | 請勿部署CSS檔案。 | 否 |
| `--no-less` | 請勿部署LESS檔案。 | 否 |
| `--no-images` | 請勿部署映像。 | 否 |
| `--no-fonts` | 請勿部署字型檔案。 | 否 |
| `--no-html` | 請勿部署HTML檔案。 | 否 |
| `--no-misc` | 不部署其他類型的檔案：MD, JBF, CSV, JSON, TXT, HTC,SWF | 否 |
| `--no-html-minify` | 請勿縮制HTML檔案。 | 否 |
| `-s <quick\|standard\|compact>` | 定義部署策略。 只有在有多個本機選項時，才使用這些選項。<ul><li>使用 [快速策略](static-view-file-strategy.md#quick-strategy) 以盡量縮短部署時間。 如果未指定，此為預設命令選項。</li><li>使用 [標準策略](static-view-file-strategy.md#standard-strategy) 部署所有包的所有靜態視圖檔案。</li><li>使用 [緊湊型策略](static-view-file-strategy.md#compact-strategy) 以節省伺服器上的磁碟空間。</li></ul> | 否 |
| `--no-parent` | 不為當前主題的父主題生成檔案。 如果您未明確使用嘗試部署的當前主題的父主題，則強烈建議使用此標誌。 這可大幅提高處理速度。 Commerce 2.4.2提供此標幟 | 否 |
| `--force (-f)` | 以任何模式部署檔案。 (依預設，靜態內容部署工具只能在生產模式中執行。 使用此選項，以預設或開發人員模式執行)。 | 否 |

>[!INFO]
>
>如果您同時指定 `<languages>` 和 `--language`, `<languages>` 優先。

## 範例

以下是一些示例命令。

### 排除主題和HTML縮制

以下命令為美國英語部署靜態內容(`en_US`)語言，會排除商務隨附的Luma主題，且不會縮制HTML檔案。

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

下列命令只會使用標準部署策略部署JavaScript（含4個作業）:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

以下命令只部署CSS和LESS，其中包含3個作業，並有快速部署策略：

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 為一個主題和一個區域生成靜態視圖檔案

以下命令為所有語言（僅前端區域）生成靜態視圖檔案，僅Commerce Luma主題，而不生成字型：

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

## 不安裝Commerce即可部署靜態視圖檔案

您可能希望在單獨的非生產環境中運行部署過程，以避免在敏感的生產電腦上執行任何生成過程。

要執行此操作，請執行下列步驟：

1. 執行 [`bin/magento app:config:dump`](../cli/export-configuration.md) 從生產系統匯出設定。
1. 將導出的檔案複製到非生產代碼庫。
1. 部署靜態視圖檔案： `bin/magento setup:static-content:deploy`

## 靜態檢視檔案部署工具疑難排解

[首先安裝Commerce軟體](../../installation/overview.md);否則，無法運行靜態視圖檔案部署工具。

**症狀**:運行靜態視圖檔案部署工具時，將顯示以下錯誤：

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**解決方案**:

使用下列步驟：

1. 使用安裝商務軟體 [命令行](../../installation/composer.md).
1. 以或身份登錄應用程式伺服器 [切換至](../../installation/prerequisites/file-system/overview.md)，即檔案系統所有者。
1. 刪除 `<app_root>/pub/static` 目錄，但 `.htaccess` 檔案。 請勿刪除此檔案。
1. 部署靜態視圖檔案： `bin/magento setup:static-content:deploy`

## 開發人員自訂靜態內容部署工具的提示

建立靜態內容部署工具的自定義實施時，僅對客戶端上應該可用的檔案使用原子檔案寫入。 如果您使用非原子檔案寫入，則這些檔案可能會載入到包含部分內容的用戶端上。

使其具有原子性的選項之一是，寫入臨時目錄中儲存的檔案，並在寫入結束後將其複製或移動到目標目錄（從載入到客戶端的位置）。 有關寫入檔案的詳細資訊，請參閱 [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
