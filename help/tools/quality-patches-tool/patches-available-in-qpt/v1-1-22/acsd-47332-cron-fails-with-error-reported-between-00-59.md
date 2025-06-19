---
title: ACSD-47332： cron失敗，錯誤僅在00:00 UTC到00:59之間報告
description: 套用ACSD-47332修補程式來修正Adobe Commerce問題，該問題導致cron失敗並出現只有在它在00:00 UTC到00:59 UTC之間執行時才會報告的錯誤。
feature: Configuration
role: Admin
exl-id: ffe6c8f7-0e4c-4a22-853a-45d708bf8164
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-47332：只有在00:00到00:59 UTC之間執行時，cron才會失敗並回報錯誤

ACSD-47332修補程式修正cron失敗並出現錯誤的問題，此錯誤僅在00:00 UTC至00:59之間執行時報告。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22時，即可使用此修補程式。 修補程式ID為ACSD-47332。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Cron失敗並出現錯誤，僅在00:00到00:59 UTC之間執行時報告。

<u>要再現的步驟</u>：

1. 在00:00到00:59 UTC之間執行`catalog_index_refresh_price` CRON。

<u>預期結果</u>：

Cron未顯示錯誤。

<u>實際結果</u>：

Cron因下列錯誤而失敗。

```SQL
SQLSTATE[HY093]: Invalid parameter number: number of bound variables does not match number of tokens, query was: SELECT `cat`.`entity_id` FROM `c
  atalog_product_entity_datetime` AS `attr`
   LEFT JOIN `catalog_product_entity` AS `cat` ON cat.row_id= attr.row_id AND (cat.created_in <= 1 AND cat.updated_in > 1) WHERE (attr.attribute_id
   = '79') AND (attr.store_id = '0') AND (attr.value = DATE_FORMAT('2022-10-02', '%Y-%m-%d %H:%i:%s'))
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
