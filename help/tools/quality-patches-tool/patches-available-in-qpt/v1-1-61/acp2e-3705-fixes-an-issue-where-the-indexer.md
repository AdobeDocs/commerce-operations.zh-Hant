---
title: ACP2E-3705：設置“MAGE_INDEXER_THREADS_COUNT”時，“indexer_update_all_views”cron 執行失敗
description: 套用 ACP2E-3705 修補程式以修復Adobe Systems商務問題，即設置“MAGE_INDEXER_THREADS_COUNT”時“indexer_update_all_views”cron 執行失敗。
feature: Catalog Management, B2B
role: Admin, Developer
source-git-commit: 4f719c62fdd9fd960548799c9872f73c76997278
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACP2E-3705：`indexer_update_all_views`設置 cron 時執行失敗`MAGE_INDEXER_THREADS_COUNT`

>[!NOTE]
>
>此修補程式將替換 [2.4.7 及更高版本的 ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) 。

ACP2E-3705 修補程式修復了 時 cron 執行失敗`MAGE_INDEXER_THREADS_COUNT`的問題`indexer_update_all_views`。此修補程式在安裝 1.1.61 時 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 可用。 修補程式 ID 為 ACP2E-3705。 請注意，此問題已計劃在 Adobe Systems Commerce 2.4.9 中修正。

## 受影響的產品和版本

**此修補程式是為商務版本Adobe Systems建立的：**

* Adobe Systems Commerce （所有部署方法） 2.4.7-p4

**與 Adobe Systems Commerce 版本相容：**

* Adobe Systems Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於具有新版本 [!DNL Quality Patches Tool] 的其他版本。 要檢查修補程式是否與您的 Adobe Systems Commerce 版本相容，請將軟體包更新 `magento/quality-patches` 到最新版本，並在 ： [[!DNL Quality Patches Tool]Search 上檢查修補程序頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)的相容性。 使用修補程序 ID 作為查找修補程序的搜尋關鍵字。

## 問題

當設置為&#x200B;*大於 2* 的值時`MAGE_INDEXER_THREADS_COUNT`，`indexer_update_all_views`cron 執行將失敗，具體會影響[!UICONTROL Customer Segments]啟用了 B2B 的索引器。

<u>重現</u>步驟：

1. 套用 QPT 補丁 [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)。
1. 轉到 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**。
1. 開啟 **[!UICONTROL Category Permissions]**。
1. 將以下索引器 **[!UICONTROL Update on Schedule]** 設定為模式：

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. 建立一些產品並將它們指派給類別。
1. 執行完全重新索引。
1. 跳到類別並設定 **[!UICONTROL Category Permissions]**。
1. 運行`indexer_update_all_views`設置為 *8* 的 `MAGE_INDEXER_THREADS_COUNT` cron 作業。

<u>預期成果</u>：

重新索引已完成，且未出現任何錯誤。

<u>實際結果</u>：

cron 作業遇到 `indexer_update_all_views` 以下錯誤：

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## 套用修補程式

要應用單個修補程式，請根據您的部署方法使用以下連結：

* Adobe Systems本地商務或Magento Open Source：[[!DNL Quality Patches Tool] 指南中的[!DNL Quality Patches Tool]>使用方式](/help/tools/quality-patches-tool/usage.md)。
* Adobe Systems Commerce on 雲端基礎結構： 雲基礎架構上的 Commerce 指南 中的升級和修補程式>套用修補程式。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：工具指南中高品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 的自助服務工具。
