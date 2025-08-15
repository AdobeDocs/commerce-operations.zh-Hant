---
title: ACP2E-3705：設定「MAGE_INDEXER_THREADS_COUNT」時，「indexer_update_all_views」cron執行失敗
description: 套用ACP2E-3705修補程式以修正Adobe Commerce問題，其中在設定「MAGE_INDEXER_THREADS_COUNT」時，「indexer_update_all_views」cron執行會失敗。
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705：設定`indexer_update_all_views`時，`MAGE_INDEXER_THREADS_COUNT` cron執行失敗

>[!NOTE]
>
>此修補程式取代2.4.7及更高版本的[ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)。

ACP2E-3705修補程式修正設定`indexer_update_all_views`時`MAGE_INDEXER_THREADS_COUNT` cron執行失敗的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACP2E-3705。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當`indexer_update_all_views`設定為大於`MAGE_INDEXER_THREADS_COUNT`2 *的值時，* cron執行失敗，特別影響已啟用B2B的[!UICONTROL Customer Segments]索引器。

<u>要再現的步驟</u>：

1. 套用QPT修補程式[ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**」。
1. 啟用&#x200B;**[!UICONTROL Category Permissions]**。
1. 將下列索引子設定為&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;模式：

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. 建立一些產品並將其指派給類別。
1. 執行完整重新索引。
1. 移至類別並設定&#x200B;**[!UICONTROL Category Permissions]**。
1. 執行`indexer_update_all_views` cron工作，並將`MAGE_INDEXER_THREADS_COUNT`設定為&#x200B;*8*。

<u>預期結果</u>：

重新索引完成，沒有發生任何錯誤。

<u>實際結果</u>：

`indexer_update_all_views` cron工作遇到下列錯誤：

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
