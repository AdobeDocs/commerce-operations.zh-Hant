---
title: ACSD-64112：設定「MAGE_INDEXER_THREADS_COUNT」時，「indexer_update_all_views」cron執行失敗
description: 套用ACSD-64112修補程式以修正設定「MAGE_INDEXER_THREADS_COUNT」時，「indexer_update_all_views」cron執行失敗的Adobe Commerce問題。
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112：設定`MAGE_INDEXER_THREADS_COUNT`時，`indexer_update_all_views` cron執行失敗

>[!NOTE]
>
>已針對2.4.7以上的Adobe Commerce版本，將此修補程式取代為[ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md)。

ACSD-64112修補程式修正設定`MAGE_INDEXER_THREADS_COUNT`時`indexer_update_all_views` cron執行失敗的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-64112。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p10

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當`MAGE_INDEXER_THREADS_COUNT`設定為大於2的值時，`indexer_update_all_views` cron執行失敗，特別影響已啟用B2B的[!UICONTROL Customer Segments]索引器。

<u>要再現的步驟</u>：

1. 使用B2B安裝乾淨的執行個體。
1. 啟用&#x200B;**[!UICONTROL B2B Company]**&#x200B;和&#x200B;**[!UICONTROL Shared Catalog]**。
1. 建立類別。
1. 建立一些產品並將其指派給類別。
1. 執行完整重新索引。
1. 將下列索引子設定為&#x200B;**[!UICONTROL Update on Schedule]**：

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. 前往後端並載入新建立的類別。
1. 按一下&#x200B;**[!UICONTROL Category Permissions]**&#x200B;並為現有客戶群組建立&#x200B;**[!UICONTROL New Permission]**。
1. 請確定`catalogpermissions_category`索引子有待處理專案。 執行以下命令來確認這一點：

   ```
   bin/magento indexer:status
   ```

1. 在`env.php`中設定下列索引子執行緒計數：

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. 執行cron工作：

   ```
   bin/magento cron:run
   ```

<u>預期結果</u>：

cron工作應該會順利執行。

<u>實際結果</u>：

`indexer_update_all_views` cron工作遇到下列錯誤：

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 安裝修補程式後所需的其他步驟

（本節為選用；套用修補程式修正問題後，可能需要執行一些步驟。） 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
