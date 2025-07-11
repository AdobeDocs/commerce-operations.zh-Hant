---
title: ACSD-64118：相同產品的並行產品儲存請求會導致資料不一致和重複專案
description: 套用ACSD-64118修補程式以修正Adobe Commerce問題，即儲存和更新相同產品的並行請求會導致資料不一致或產品重複。
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4235511ccbef028e1564d7626daadaa5beae0fd4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-64118：相同產品的並行產品儲存請求會導致資料不一致和重複專案

ACSD-64118修補程式修正同時要求儲存和更新相同產品導致資料不一致或重複產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACSD-64118。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

同時要求儲存和更新相同產品會導致資料不一致或產品重複。

<u>要再現的步驟</u>：

1. 為`env.php`中的消費者設定多重處理序：

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. 新增其他商店和新商店至主要網站。
1. 傳送大量API要求至預設storeview端點`/rest/default/async/bulk/V1/products`，並搭配下列裝載以建立產品：

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. 使用相同的裝載將大量API要求傳送至新的storeview端點`/rest/store/async/bulk/V1/products`以更新產品。
1. 排清快取。
1. 執行cron工作。
1. 檢查`catalog_product_entity`表格中先前步驟的產品專案。

<u>預期結果</u>：

* 產品SKU的單一專案應出現在`catalog_product_entity`表格中。
* 第一個REST API請求應建立一個資料庫專案，所有後續請求都應更新該資料庫專案。

<u>實際結果</u>：

`catalog_product_entity`資料表中存在同一個SKU的多個專案。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
