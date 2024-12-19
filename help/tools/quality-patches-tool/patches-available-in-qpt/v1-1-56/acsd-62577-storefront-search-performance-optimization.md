---
title: ACSD-62577：店面搜尋效能最佳化
description: 套用ACSD-62577修補程式以修正Adobe Commerce問題，該問題導致店面搜尋效能因大型「search_query」表格導致查詢執行速度緩慢而降低。
feature: Search
role: Admin, Developer
source-git-commit: dbb185fb44b491b9e8d12290d75538d98c911eac
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577：店面搜尋效能最佳化

ACSD-62577修補程式透過最佳化查詢和表格索引，修正店面搜尋查詢效能緩慢的問題。 此修補程式可用於[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56。修補程式ID為ACSD-62577。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6、2.4.7-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

大型的`search_query`資料表會顯著減慢店面搜尋的速度，因為查詢效率不高且缺少最佳化的資料表索引，所以會增加前端回應時間。

<u>要再現的步驟</u>：

1. 使用效能工具組`small.xml`設定Adobe Commerce Develop。
1. 存取SQL命令列，並使用下列命令刪除`search_query`表格：

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. 將大量記錄填入`search_query`表格，例如： 400萬筆記錄。
1. 觸發重新索引和排清快取。

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. 啟用資料庫偵錯記錄檔：

   ```
   bin/magento dev:query-log:enable  
   ```

1. 在店面搜尋列中搜尋字詞，例如
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. 檢查`db.log`是否有下列SQL的查詢執行時間：

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>預期結果</u>：

查詢執行時間已最佳化，因此處理大型`search_query`資料表時，回應時間的增加不那麼明顯。

<u>實際結果</u>：

由於處理大型`search_query`資料表的效率低，查詢執行時間大幅增加：

```
TIME: 10.8520 seconds  
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
