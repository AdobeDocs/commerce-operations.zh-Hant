---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 5%

---
# Adobe Commerce技術檔案

我們歡迎社群以及檔案團隊外部的Adobe員工出力貢獻。

## Adobe開放原始碼行為準則

本專案已採用 [Adobe 開放原始碼管理辦法](code-of-conduct.md)或 [.NET Foundation 管理辦法](https://dotnetfoundation.org/code-of-conduct)。如需詳細資訊，請參閱[貢獻](contributing.md)一文。

## 關於您對Adobe內容的貢獻

請參閱 [Adobe檔案投稿人指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

貢獻方式取決於您的身分和您要貢獻的變更型別：

### 微幅變更

若您出於好意想貢獻微幅更新內容，請前往文章，並按一下 **編輯** 文章中的連結，會前往文章的GitHub來源。 然後，只需使用GitHub UI進行更新即可。 檢視一般 [Adobe檔案投稿人指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 以取得詳細資訊。

Adobe使用條款涵蓋您在本存放庫為檔案和程式碼範例提交的小幅更正或釐清。

### 來自社群成員的重大變更或新文章

如果您是Adobe社群的一員，且想建立新文章或提交重大變更，請使用Git存放庫中的「問題」標籤來提交問題，以開始與檔案團隊對話。 一旦您同意了計畫，就需要與員工合作，透過結合公共和私有存放庫的工作來幫助引入新內容。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### 來自Adobe員工的重大變更

若您是Adobe Experience Cloud解決方案產品團隊的技術撰寫人員、專案經理或開發人員，且您的工作正是貢獻或撰寫技術文章，請使用的私人存放庫： `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 工具與設定

社群投稿人可以使用GitHub UI進行基本編輯或建立存放庫復本，以做出重大貢獻。

請參閱 [Adobe檔案投稿人指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 以取得詳細資訊。

## 如何使用Markdown將主題格式化

此存放庫中的所有文章皆使用GitHub Flavored Markdown。 如果您不熟悉Markdown，請參閱：

* [Markdown基本介紹](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [可列印的Markdown速查表](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 範本

此 `_jekyll` 目錄包含樣板化主題和必要資產。
使用Liquid範本語言的範本位於 `_jekyll/templated` 作為HTML檔案的目錄。
此 `_jekyll/_data` 目錄中包含的檔案包含用來呈現範本的資料。

若要轉譯所有範本：

1. 導覽至 `_jekyll` 目錄。

   cd _jekyll

1. 執行轉譯指令碼。

```
_scripts/render
```

> **注意：** 您必須從以下位置執行指令碼： `_jekyll` 目錄。
> **注意：** 您必須安裝Ruby才能執行此指令碼。

指令碼會執行轉譯並將轉譯的範本寫入至 `help/_includes/templated` 目錄。

請參閱Jekyll檔案，以取得更多關於 [資料檔案](https://jekyllrb.com/docs/datafiles)， [液體濾鏡](https://jekyllrb.com/docs/liquid/filters/)和其他功能。
