---
title: 配置搜索停止字
description: 瞭解如何使用CSV檔案管理Adobe Commerce的臨時措辭。
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 配置搜索停止字

總的來說， _倒話_ 是搜索引擎在處理文本後過濾掉的常用詞。 最初，當磁碟空間和記憶體極為有限時，每節省一千位元組就意味著效能有了顯著提高。 因此，搜索引擎通過忽略某些詞和保持索引小而獲得效能提升。

雖然我們現在有更多的儲存，但效能仍然很重要。 Elasticsearch和OpenSearch與其他搜索引擎一樣，仍然使用停止詞來提高效能。

必須使用位於 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 或 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` 目錄，具體取決於您安裝Commerce軟體的方式。

有關Elasticsearch和OpenSearch如何使用停止詞的詳細資訊，請參閱以下資源：

- [停止詞：效能與精度](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [權利倒置的利弊](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [使用停止字](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [停止詞和效能](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 配置停止字

停止字位於 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 的子菜單。 Adobe Commerce和Magento Open Source附帶一個CSV檔案，其中包含預設區域設定的停止語言和附加檔案， `stopwords.csv`，它具有不由其他CSV檔案表示的任何區域設定的停止字。

停止字檔案快取的預設生存期為15分鐘。

### 編輯現有區域設定的停止字

**編輯非索引字**:

1. 登錄到Commerce伺服器或切換到 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 使用文本編輯器在 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 的子菜單。

   CSV檔案使用命名約定 `stopwords_<locale_code>.csv`。 例如，德語的非索引字檔案被命名為 `stopwords_de_DE.csv`。

1. 在檔案中添加詞、刪除詞或更改詞。

   （檔案中的每個停止字都從新行開始。）

1. 保存更改並退出文本編輯器。
1. 清除配置快取。

   - 管理員： **系統** >工具> **快取管理**。 選擇 **配置** 複選框，並從上面的清單中按一下 **刷新**。 按一下 **提交** 完成操作。

   - 命令行：作為檔案系統所有者，輸入以下命令：

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. 通過搜索店面上的術語來檢查結果。

### 為新區域設定建立停止字

**為區域設定添加非索引字**:

1. 登錄到Commerce伺服器或切換到 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。

1. 使用文本編輯器建立名為的停止字檔案 `stopwords_<locale_code>.csv` 的 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 的子菜單。

   例如，要為義大利語區域設定建立非索引字，請將檔案命名為 `stopwords_it_IT.csv`。

1. 在您的非索引字檔案中，確保每個非索引字位於單獨的行上。
1. 保存更改並退出文本編輯器。
1. 在同一目錄中，開啟 `esconfig.xml` 的子菜單。
1. 將行添加到 `esconfig.xml` 如下：

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例如，要添加義大利語的停止字檔案，請添加以下行：

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 將更改保存到 `esconfig.xml` 並退出文本編輯器。
1. 清除配置快取。

   - 管理員： **系統** >工具> **快取管理**。 選擇 **配置** 複選框，並從上面的清單中按一下 **刷新**。 按一下 **提交** 完成操作。

   - 命令行：作為檔案系統所有者，輸入以下命令：

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. 通過搜索店面上的術語來檢查結果。

## 更改停止字目錄

本節討論如何從以下內容之一選擇更改預設的停止字目錄：

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

位置取決於您如何安裝Commerce軟體。 如果克隆了Magento2 GitHub儲存庫，則路徑位於 `app/code`。 如果安裝了壓縮的存檔或集合包，則路徑在 `vendor`。

**更改目錄**:

1. 作為檔案系統所有者，開啟Elasticsearch `di.xml` 的子菜單。

   如果克隆了儲存庫，則它位於 `app/code/Magento/Elasticsearch/etc/di.xml`

   如果你有檔案或暗藏，它位於 `vendor/magento/module-elasticsearch/etc/di.xml`

1. 更改 `stopwordsDirectory` 到所需目錄：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 將更改保存到 `di.xml` 並退出文本編輯器。

## 從模組更改目錄

1. [建立模組](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 在模組中 `etc/di.xml` 添加說明：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 在模組中，建立目錄 `etc/stopwords`，以及相應的CSV檔案。

1. 將更改保存到 `di.xml` 並退出文本編輯器。
