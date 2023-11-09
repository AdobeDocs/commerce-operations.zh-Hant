---
source-git-commit: 2727ddb18995ac2163276a0aa8573161add48971
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 3%

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

對於某些主題，我們會使用資料檔案和範本來產生已發佈內容。 此方法的使用案例包括：

* 發佈大量以程式設計方式產生的內容
* 為需要機器可讀檔案格式（例如YAML）以進行整合（例如全網站分析工具）的多重系統的客戶提供單一信任來源

樣板化內容的範例包括但不限於：

* [CLI工具參考](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [產品可用性表格](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [系統需求表](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### 產生樣板化內容

一般而言，大部分的作者只需要將發行版本新增到產品可用性和系統需求表格。 所有其他樣板化內容的維護工作都是自動化的，或由專門的團隊成員管理。 這些指示適用於「大部分」作者。

>**注意：**
>
>* 產生樣板化內容需要在終端機中的命令列上工作。
>* 您必須安裝Ruby才能執行轉譯指令碼。 另請參閱 [_jekyll/.ruby-version](_jekyll/.ruby-version) 以取得所需的版本。

如需範本化內容的檔案結構說明，請參閱下列內容：

* `_jekyll` — 包含範本化主題和必要資產
* `_jekyll/_data` — 包含用於呈現範本的電腦可讀檔案格式
* `_jekyll/templated` — 包含使用Liquid範本語言的HTML型範本檔案
* `help/_includes/templated` — 包含在中範本化內容的產生輸出 `.md` 檔案格式，因此可在Experience League主題中發佈；轉譯指令碼會自動將產生的輸出寫入此目錄中

若要更新樣板化內容，請執行下列動作：

1. 在文字編輯器中，開啟資料檔案，位置為 `/jekyll/_data` 目錄。 例如：

   * [產品可用性表格](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)： `/jekyll/_data/product-availability.yml`
   * [系統需求表](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)： `/jekyll/_data/system-requirements.yml`

1. 使用現有的YAML結構來建立專案。

   例如，若要將Adobe Commerce版本新增至產品可用性表格，請在每個專案新增以下內容： `extensions` 和 `services` 的區段 `/jekyll/_data/product-availability.yml` 檔案（視需要修改版本號碼）：

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. 導覽至 `_jekyll` 目錄。

   ```
   cd _jekyll
   ```

1. 產生樣板化內容並將輸出寫入 `help/_includes/templated` 目錄。

   ```
   rake render
   ```

   >**注意：** 您必須從以下位置執行指令碼： `_jekyll` 目錄。 如果您是第一次執行指令碼，您必須先安裝Ruby相依性 `bundle install` 命令。

1. 確認預期的 `help/_includes/templated` 檔案已修改。

   ```
   git status
   ```

   您應該會看到類似下列的輸出：

   ```
   modified:   _data/product-availability.yml
   modified:   ../help/_includes/templated/product-availability-extensions.md
   ```

請參閱Jekyll檔案，以取得更多關於 [資料檔案](https://jekyllrb.com/docs/datafiles)， [液體濾鏡](https://jekyllrb.com/docs/liquid/filters/)和其他功能。
