---
source-git-commit: 4b767014f325bef7e07cea11d01089206bf44caf
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---
# Adobe Commerce技術文檔

我們歡迎社區以及文檔團隊外的Adobe員工的貢獻。

## Adobe開放原始碼行為准則

本項目已通過 [Adobe開放原始碼行為准則](code-of-conduct.md) 或 [.NET Foundation行為准則](https://dotnetfoundation.org/code-of-conduct)。 有關詳細資訊，請參見 [貢獻](contributing.md) 文章。

## 關於您對Adobe內容的貢獻

查看 [Adobe文檔貢獻者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。

您如何貢獻取決於您是誰以及您希望貢獻的更改類型：

### 輕微更改

如果您出於好心而提供小小的更新，請訪問文章，然後按一下 **編輯** 連結到文章的GitHub源。 然後，只需使用GitHub UI進行更新即可。 請參閱常規 [Adobe文檔參與者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 的子菜單。

Adobe使用條款涵蓋您為此回購協定中的文檔和代碼實例提交的輕微更正或澄清。

### 社區成員的主要更改或新文章

如果您是Adobe社區的一部分，並且要建立新文章或提交重大更改，請使用Git儲存庫中的「問題」頁籤提交問題以開始與文檔團隊的對話。 一旦您同意了計畫，您就需要與員工合作，通過在公共和私有儲存庫中的工作組合來幫助將新內容引入。

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Adobe員工的主要變動

如果您是Adobe Experience Cloud解決方案產品團隊的技術編寫者、計畫經理或開發人員，並且您的工作是撰寫或撰寫技術文章，則應使用位於 `https://git.corp.adobe.com/AdobeDocs`。

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## 工具和設定

社區參與者可以使用GitHub UI進行基本編輯，或分叉回購以做出主要貢獻。

查看 [Adobe文檔貢獻者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) 的雙曲餘切值。

## 如何使用標籤格式化您的主題

此儲存庫中的所有文章都使用GitHub調味的標籤。 如果您不熟悉markdown ，請參閱：

* [標籤基礎](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [可打印的標籤](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## 模板

的 `_jekyll` 目錄包含模板化主題和必需資產。
使用液體模板語言的模板位於 `_jekyll/templated` 目錄作為HTML檔案。
的 `_jekyll/_data` 目錄包含包含用於呈現模板的資料的檔案。

要呈現所有模板，請執行以下操作：

1. 導航到 `_jekyll` 的子菜單。

   cd_jekyll

1. 運行呈現指令碼。

```
_scripts/render
```

> **注：** 必須從 `_jekyll` 的子菜單。
> **注：** 必須安裝Ruby才能運行此指令碼。

指令碼將運行渲染模板，並將渲染的模板寫入 `help/_includes/templated` 的子菜單。

有關詳細資訊，請參閱Jekyl文檔 [資料檔案](https://jekyllrb.com/docs/datafiles) [液體過濾器](https://jekyllrb.com/docs/liquid/filters/)、和其他功能。
