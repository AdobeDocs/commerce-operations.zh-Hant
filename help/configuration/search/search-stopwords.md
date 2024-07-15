---
title: 設定搜尋停用詞
description: 瞭解如何使用CSV檔案管理Adobe Commerce的停用詞。
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 設定搜尋停用詞

一般而言，_停用詞_&#x200B;是搜尋引擎在處理文字後篩選掉的常用詞。 最初，當磁碟空間和記憶體極為有限時，每儲存KB意味著效能大幅提升。 因此，搜尋引擎透過忽略特定字詞並維持較小的索引來提升效能。

雖然我們目前擁有更多儲存空間，但效能仍然很重要。 Elasticsearch和OpenSearch就像其他搜尋引擎一樣，仍使用停用字詞來改善效能。

您必須使用位於`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`目錄或`<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`目錄中的CSV檔案來管理您的停用詞，這取決於您安裝Commerce軟體的方式。

如需Elasticsearch和OpenSearch如何使用停用字詞的詳細資訊，請參閱下列資源：

- [停用詞：效能與精確度](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [停用字詞的優點和缺點](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [使用停用詞](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [停用字詞與效能](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 設定停用詞

停用字詞位於`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`目錄中。 Adobe Commerce隨附一個CSV檔案，其中包含預設地區設定的停用詞，以及另一個檔案`stopwords.csv`，其中包含其他CSV檔案未表示的任何地區設定的停用詞。

停用字檔案快取的預設存留期為15分鐘。

### 編輯現有地區設定的停用詞

**若要編輯停用詞**：

1. 登入您的Commerce伺服器，或切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
1. 使用文字編輯器在`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`目錄中開啟停用字檔案。

   CSV檔案使用命名慣例`stopwords_<locale_code>.csv`。 例如，德文的Stopword檔案名為`stopwords_de_DE.csv`。

1. 在檔案中新增單字、移除單字或變更單字。

   （檔案中的每個停用字都會從新行開始。）

1. 儲存變更並退出文字編輯器。
1. 清除設定快取。

   - 管理員： **系統** >工具> **快取管理**。 選取「**組態**」核取方塊，並從上方清單按一下「**重新整理**」。 按一下&#x200B;**提交**&#x200B;以完成動作。

   - 命令列：以檔案系統擁有者的身分，輸入下列命令：

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. 在您的店面搜尋字詞，以檢查結果。

### 為新地區設定建立停用詞

**若要為地區設定**&#x200B;新增停用詞：

1. 登入您的Commerce伺服器，或切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。

1. 使用文字編輯器在`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`目錄中建立名為`stopwords_<locale_code>.csv`的停用字檔案。

   例如，若要為義大利語言環境建立停用詞，請將檔案命名為`stopwords_it_IT.csv`。

1. 在您的停用字檔案中，確定每個停用字都位於不同的行上。
1. 儲存變更並退出文字編輯器。
1. 在相同目錄中，在文字編輯器中開啟`esconfig.xml`。
1. 新增一行到`esconfig.xml`，如下所示：

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例如，若要新增義大利停用字檔案，請新增下列行：

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 將變更儲存至`esconfig.xml`並結束文字編輯器。
1. 清除設定快取。

   - 管理員： **系統** >工具> **快取管理**。 選取「**組態**」核取方塊，並從上方清單按一下「**重新整理**」。 按一下&#x200B;**提交**&#x200B;以完成動作。

   - 命令列：以檔案系統擁有者的身分，輸入下列命令：

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. 在您的店面搜尋字詞，以檢查結果。

## 變更停用字目錄

本節討論如何選擇性地從下列其中一項變更預設停用字目錄：

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

此位置視您安裝Commerce軟體的方式而定。 如果您複製Magento2 GitHub存放庫，則路徑位於`app/code`下。 如果您已安裝壓縮封存或中繼資料，則路徑在`vendor`之下。

**若要變更目錄**：

1. 以檔案系統擁有者的身分，在文字編輯器中開啟Elasticsearch`di.xml`。

   如果您複製存放庫，則它位於`app/code/Magento/Elasticsearch/etc/di.xml`

   如果您有封存或中繼資料，則位於`vendor/magento/module-elasticsearch/etc/di.xml`

1. 將`stopwordsDirectory`的值變更為所要的目錄：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 將變更儲存至`di.xml`並結束文字編輯器。

## 若要從模組變更目錄

1. [建立模組](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 在您的模組`etc/di.xml`中新增指示：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 在您的模組中，使用對應的CSV檔案建立目錄`etc/stopwords`。

1. 將變更儲存至`di.xml`並結束文字編輯器。
