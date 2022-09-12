---
title: 配置搜索停止詞
description: 了解如何使用CSV檔案管理Adobe Commerce的秒數。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# 配置搜索停止詞

一般來說， _停字詞_ 是搜尋引擎在處理文字後篩除的常見字詞。 最初，當磁碟空間和記憶體極為有限時，每節省一千位元組就意味著效能的顯著提高。 因此，搜索引擎通過忽略某些單詞，保持索引小，實現了效能提升。

儘管我們現在有更多的儲存，但效能仍然很重要。 Elasticsearch和OpenSearch與其他搜尋引擎一樣，仍使用停用字來改善效能。

您必須使用位於 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄或 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` 目錄，具體取決於您安裝商務軟體的方式。

有關Elasticsearch和OpenSearch如何使用停用詞的詳細資訊，請參閱以下資源：

- [停字：效能與精確度](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [辭匯的利弊](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [使用秒數](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [秒數和效能](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 設定秒數

停止字位於 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄。 Adobe Commerce和Magento Open Source隨附一個CSV檔案，其中包含預設地區設定的停止字詞，以及一個額外的檔案， `stopwords.csv`，其中包含任何地區設定的停止字詞，而其他CSV檔案不代表。

stopwords檔案的預設期限 [快取](https://glossary.magento.com/cache) 才15分鐘。

### 編輯現有區域設定的停止字

**要編輯停止詞**:

1. 登入您的Commerce伺服器，或切換至 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 使用文字編輯器，在 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄。

   CSV檔案使用命名慣例 `stopwords_<locale_code>.csv`. 例如，德文秒詞檔案的名稱為 `stopwords_de_DE.csv`.

1. 在檔案中新增字詞、移除字詞或變更字詞。

   （檔案中的每個秒數都會從新行開始。）

1. 儲存您的變更並退出文字編輯器。
1. 清除配置快取。

   - 管理員： **系統** >工具> **快取管理**. 選取 **設定** 核取方塊，然後從上方的清單按一下 **重新整理**. 按一下 **提交** 以完成動作。

   - 命令列：作為檔案系統所有者，輸入以下命令：

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. 在您的 [店面](https://glossary.magento.com/storefront).

### 為新區域設定建立停止字

**為區域設定添加秒數**:

1. 登入您的Commerce伺服器，或切換至 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).

1. 使用文本編輯器建立名為的秒詞檔案 `stopwords_<locale_code>.csv` 在 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目錄。

   例如，要為義大利語地區建立停止詞，請為檔案命名 `stopwords_it_IT.csv`.

1. 在您的秒數檔案中，確保每個秒數位於單獨的一行。
1. 儲存您的變更並退出文字編輯器。
1. 在相同目錄中，開啟 `esconfig.xml` 在文字編輯器中。
1. 新增行至 `esconfig.xml` 如下所示：

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例如，要添加義大利語禁用字檔案，請添加以下行：

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 將變更儲存至 `esconfig.xml` 並退出文字編輯器。
1. 清除配置快取。

   - 管理員： **系統** >工具> **快取管理**. 選取 **設定** 核取方塊，然後從上方的清單按一下 **重新整理**. 按一下 **提交** 以完成動作。

   - 命令列：作為檔案系統所有者，輸入以下命令：

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. 在店面上搜尋詞，以檢查結果。

## 更改秒數目錄

本節將討論如何從以下選項之一中選擇更改預設的秒數目錄：

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

位置取決於您安裝商務軟體的方式。 如果您複製了Magento2 GitHub存放庫，路徑位於 `app/code`. 如果安裝了壓縮的存檔或元資料包，則路徑在下 `vendor`.

**更改目錄**:

1. 作為檔案系統所有者，請開啟Elasticsearch `di.xml` 在文字編輯器中。

   如果複製了存放庫，該存放庫位於 `app/code/Magento/Elasticsearch/etc/di.xml`

   如果你有檔案或元資料庫，它位於 `vendor/magento/module-elasticsearch/etc/di.xml`

1. 變更 `stopwordsDirectory` 到所需目錄：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 將變更儲存至 `di.xml` 並退出文字編輯器。

## 從模組更改目錄

1. [建立模組](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 在模組中 `etc/di.xml` 新增指示：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 在模組中，建立目錄 `etc/stopwords`，以及對應的CSV檔案。

1. 將變更儲存至 `di.xml` 並退出文字編輯器。
