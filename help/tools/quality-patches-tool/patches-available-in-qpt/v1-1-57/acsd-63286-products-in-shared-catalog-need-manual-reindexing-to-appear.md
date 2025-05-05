---
title: ACSD-63286：指派給共用目錄的產品需要手動重新索引才能顯示
description: 套用ACSD-63286修補程式以修正Adobe Commerce問題，該問題導致透過API指派給共用目錄的產品在執行手動重新索引前不會出現在店面上。
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286：指派給共用目錄的產品需要手動重新索引才能顯示

ACSD-63286修補程式修正了手動重新索引執行前，透過API指派給共用目錄的產品未出現在店面的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-63286。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當透過API將產品指派給共用目錄時，在部分索引器和消費者cron工作執行後，它們不會出現在前端。 但是，在手動完全重新索引後，它們確實會出現。

<u>要再現的步驟</u>：

1. 將[!DNL RabbitMQ]設定為佇列服務。
1. 建立共用目錄並將其指派給公司。
1. 建立簡單產品並將其指派至類別。
1. 執行部分重新索引。

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 使用下列API要求將建立的產品指派給共用目錄`pub/rest/all/V1/sharedCatalog/<id>/assignProducts`：

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 執行下列cron以清除佇列並執行部分重新索引。

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 以公司使用者身分登入前端。
1. 檢查前端類別頁面。 新指派的產品不可見。
1. 執行手動重新索引：

   ```
   bin/magento index:reindex
   ```

<u>預期結果</u>：

產品會出現在前端，不需要手動重新索引。

<u>實際結果</u>：

產品只有在手動重新索引後才會出現在前端。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
