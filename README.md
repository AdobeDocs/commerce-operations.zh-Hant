---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 3%

---
# Adobe Commerce營運技術檔案

我們歡迎社群以及檔案團隊以外的Adobe員工出力貢獻。

## 影像最佳化的預先提交鉤點

此存放庫包括自動預先提交掛接，可在提交前最佳化影像。 **所有貢獻者都應該啟用這些鉤點**，以確保一致的影像最佳化並降低存放庫大小。

### 快速設定

複製存放庫後，請執行：

```bash
.githooks/setup-hooks.sh
```

### 鉤子會做什麼

- 自動偵測分階段影像檔案(PNG、JPG、JPEG、GIF、SVG)
- 執行`image_optim`以壓縮和最佳化影像
- 自動重新存放最佳化的影像
- 確保所有認可的影像都已適當最佳化

### 優點

- 縮小存放庫大小
- 加速說明檔案的頁面載入
- 所有貢獻者的影像品質一致
- 不需要手動最佳化

如需詳細的設定指示、疑難排解和組態，請參閱[`.githooks/README.md`](.githooks/README.md)。

## Adobe Open Source行為準則

本專案已採用 [Adobe 開放原始碼管理辦法](code-of-conduct.md)或 [.NET Foundation 管理辦法](https://dotnetfoundation.org/code-of-conduct)。如需詳細資訊，請參閱[貢獻](contributing.md)一文。

## 關於您對Adobe內容的貢獻

請參閱[Adobe檔案投稿人指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

貢獻方式取決於您的身分和您要貢獻的變更型別：

### 微幅變更

如果您要提出微幅更新，請瀏覽文章，然後按一下文章底部的意見區域，按一下&#x200B;**詳細的意見選項**，然後按一下&#x200B;**建議編輯**，即可前往GitHub的Markdown來源檔案。 使用GitHub UI進行更新。 如需詳細資訊，請參閱一般[Adobe檔案投稿人指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

您在本存放庫為檔案和程式碼範例提交的小幅更正或釐清均包含在Adobe使用條款中。

### 來自社群成員的重大變更或新文章

如果您是Adobe社群的一分子，且想建立新文章或提交重大變更，請使用Git存放庫中的「問題」索引標籤，提交問題以便與檔案團隊開始對話。 一旦您同意了計畫，就需要與員工合作，透過結合公共和私有存放庫的工作來幫助引入新內容。

### 來自Adobe員工的重大變更

若您是Adobe Experience Cloud解決方案產品團隊的技術撰寫人員、專案經理或開發人員，且您的工作正是貢獻或撰寫技術文章，請使用`https://git.corp.adobe.com/AdobeDocs`的私人存放庫。

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 工具與設定

社群投稿人可以使用GitHub UI進行基本編輯或建立存放庫復本，以做出重大貢獻。

如需詳細資訊，請參閱[Adobe檔案貢獻者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

## 如何使用Markdown將主題格式化

此存放庫中的所有文章皆使用GitHub Flavored Markdown。 如果您不熟悉Markdown，請參閱：

- [Markdown基本介紹](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [可列印的Markdown速查表](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 範本

對於某些主題，我們會使用資料檔案和範本來產生已發佈內容。 此方法的使用案例包括：

- 發佈大量以程式設計方式產生的內容
- 為需要機器可讀檔案格式（例如YAML）以進行整合（例如全網站分析工具）的多重系統的客戶提供單一信任來源

樣板化內容的範例包括但不限於：

- [CLI工具參考](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [產品可用性表格](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [系統需求表](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### 產生樣板化內容

一般而言，大部分的作者只需要將發行版本新增到產品可用性和系統需求表格。 所有其他樣板化內容的維護工作都是自動化的，或由專門的團隊成員管理。 這些指示適用於大部分的作者。

>**附註：**
>
>- 產生樣板化內容需要在終端機中的命令列上工作。
>- 您必須安裝Ruby才能執行轉譯指令碼。 如需所需版本，請參閱[_jekyll/.ruby-version] (_jekyll/.ruby-version)。

如需範本化內容的檔案結構說明，請參閱下列內容：

- `_jekyll` — 包含範本化主題和必要資產
- `_jekyll/_data` — 包含用來轉譯範本的電腦可讀檔案格式
- `_jekyll/templated` — 包含使用Liquid範本語言的HTML範本檔案
- `help/_includes/templated` — 包含範本化內容以`.md`檔案格式產生的輸出，以便在Experience League主題中發佈；轉譯指令碼會自動將產生的輸出寫入此目錄中

若要更新樣板化內容，請執行下列動作：

1. 在文字編輯器中，開啟`/jekyll/_data`目錄中的資料檔案。 例如：

   - [產品可用性表格](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)： `/jekyll/_data/product-availability.yml`
   - [系統需求表格](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)： `/jekyll/_data/system-requirements.yml`

1. 使用現有的YAML結構來建立專案。

   例如，若要將Adobe Commerce版本新增至產品可用性表格，請在`extensions`檔案的`services`和`/jekyll/_data/product-availability.yml`區段中的每個專案新增下列內容（視需要修改版本號碼）：

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. 導覽至`_jekyll`目錄。

   ```bash
   cd _jekyll
   ```

1. 產生樣板化內容並將輸出寫入`help/_includes/templated`目錄。

   ```bash
   bundle exec rake render
   ```

   >**注意：**&#x200B;您必須從`_jekyll`目錄執行指令碼。 如果這是您第一次執行指令碼，您必須先使用`bundle install`命令安裝Ruby相依性。 `adobe-comdox-exl-rake-tasks` gem提供核心Rake任務和相依性（Jekyll、Rake、影像最佳化），以便在所有Adobe Commerce檔案存放庫中提供更佳的可維護性。 此存放庫的特定自訂工作已在`Rakefile`中實作。

1. 導覽回`root`目錄。

   ```bash
   cd ..
   ```

1. 確認預期的`help/_includes/templated`檔案已修改。

   ```bash
   git status
   ```

   您應該會看到類似下列的輸出：

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. 推送您的變更。

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

請參閱Jekyll檔案以取得有關[資料檔](https://jekyllrb.com/docs/datafiles)、[Liquid濾鏡](https://jekyllrb.com/docs/liquid/filters/)和其他功能的詳細資訊。

## 可用的Rake任務

此存放庫使用`adobe-comdox-exl-rake-tasks` gem提供的Rake工作。 若要檢視所有可用的工作，請執行：

```bash
cd _jekyll
bundle exec rake --tasks
```
