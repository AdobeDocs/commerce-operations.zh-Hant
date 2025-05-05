---
title: ACSD-59083：在同時mview更新期間找不到基底資料表或檢視的錯誤
description: 套用ACSD-59083修補程式以修正Adobe Commerce問題，該問題導致某些資料庫更新作業失敗，並出現錯誤「找不到基底資料表或檢視」。
feature: System
role: Admin, Developer
source-git-commit: 7f091ff8db7973c4290e0412d19e9088f1220cef
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-59083：在同時`mview`更新期間找不到&#x200B;*基底資料表或檢視*&#x200B;個錯誤

ACSD-59083修補程式修正了同時執行`mview`更新時，某些資料庫更新作業失敗並出現「找不到基底資料表或檢視」錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-59083。 請注意，問題已在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.5-p5

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當`mview`更新同時執行時，某些資料庫更新作業會導致「找不到基底資料表或檢視」錯誤。

<u>要再現的步驟</u>：

1. 將索引子模式設定為&#x200B;**[!UICONTROL Update on Schedule]**。
1. 使用下列SQL命令將記錄插入`cl`資料表：

   ```
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. 安裝`setup/performance-toolkit/profiles/ce/small.xml`設定檔。
1. 在檔案`magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php`的第72行新增中斷點。
1. 清除快取。
1. 按一下任何產品上的&#x200B;**[!UICONTROL Add to Cart]**。
1. 在執行點選中斷點時啟動cron工作。
1. 在啟動cron工作後繼續此程式。

<u>預期結果</u>：

資料庫作業順利執行且沒有錯誤。

<u>實際結果</u>：

執行期間發生錯誤：

```
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
