---
source-git-commit: 3ba17b62f595e5a02ca56753d81d67166ddbc413
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 5%

---
# Adobe Commerce使用者檔案

我們歡迎來自我們的社群，以及來自檔案團隊以外的Adobe員工貢獻心力。

## Adobe開放原始碼行為准則

本專案已採用 [Adobe 開放原始碼管理辦法](code-of-conduct.md)或 [.NET Foundation 管理辦法](https://dotnetfoundation.org/code-of-conduct)。如需詳細資訊，請參閱[貢獻](contributing.md)一文。

## 關於您對Adobe內容的貢獻

請參閱 [Adobe檔案貢獻者指南](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html).

您的投稿方式取決於您的身分，以及您要投稿的變更類型：

### 微幅變更

如果您出於好意要貢獻微幅更新，請造訪文章，然後按一下 **編輯** 文章中的連結，會前往文章的GitHub來源。 然後，只要使用GitHub UI進行更新即可。 請參閱一般 [Adobe檔案貢獻者指南](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html) 以取得更多資訊。

您在此存放庫中針對檔案和程式碼範例提交的微幅更正或釐清，皆受Adobe使用條款所涵蓋。

### 社群成員的重大變更或新文章

如果您是Adobe社群的一員，且想建立新文章或提交重大變更，請使用Git存放庫中的「問題」索引標籤來提交問題，以開始與檔案團隊對話。 在您同意計畫後，您需要與員工合作，透過公共和私人存放庫中的組合工作，協助帶入新內容。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### 來自Adobe員工的重大更改

若您是Adobe Experience Cloud解決方案產品團隊的技術撰寫人員、專案經理或開發人員，且您的工作正是貢獻或撰寫技術文章，請使用的私人存放庫，位於 `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 工具與設定

社群投稿人可使用GitHub UI進行基本編輯，或取用存放庫來進行重大投稿。

請參閱 [Adobe檔案貢獻者指南](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html) 以取得詳細資訊。

## 如何使用Markdown來設定主題格式

此存放庫中的所有文章都使用GitHub精選的Markdown。 如果您不熟悉Markdown，請參閱：

* [Markdown基本介紹](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [可列印的Markdown速查表](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 標籤

在公開存放庫中，自動化標籤會指派給提取請求，以協助我們管理提取請求工作流程，並協助您了解提取請求的執行狀況：

* **傳送至作者的變更**:提交人已收到擱置提取請求的通知。
* **準備合併**:準備由我們的提取請求審核團隊審核。

## 範本

此 `_jekyll` 目錄包含模板化主題和必需資產。
使用液體模板語言的模板位於 `_jekyll/templated` 目錄作為HTML檔案。
此 `_jekyll/_data` 目錄包含檔案，其中包含用於呈現模板的資料。

要呈現所有模板，請執行以下操作：

1. 導覽至 `_jekyll` 目錄。

   cd_jekyll

1. 執行呈現指令碼。

```
_scripts/render
```

> **注意：** 您必須從 `_jekyll` 目錄。
> **注意：** 必須安裝Ruby才能運行此指令碼。

指令碼會執行轉譯，並將轉譯的範本寫入 `help/_includes/templated` 目錄。

如需詳細資訊，請參閱Jekyll檔案 [資料檔案](https://jekyllrb.com/docs/datafiles) [液體過濾器](https://jekyllrb.com/docs/liquid/filters/)和其他功能。
