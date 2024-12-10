---
title: ACSD-61756：由於缺少資料庫索引，「AdvancedSalesRule」篩選器的效能降低
description: 套用ACSD-61756修補程式以修正Adobe Commerce問題，該問題導致「magento_salesrule_filter」查詢在不使用索引的情況下執行完整表格掃描，在處理大量記錄時導致效能降低。 此修補程式會為'AdvancedSalesRule'篩選器新增遺失的資料庫索引，藉此改善效能。
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
source-git-commit: 23e92bb9032001134d2696be498a4c384f323c36
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756：由於缺少資料庫索引，`AdvancedSalesRule`個篩選器的效能降低

套用ACSD-61756修補程式，藉由新增遺漏的資料庫索引來改善`AdvancedSalesRule`篩選器的效能。 這修正了`magento_salesrule_filter`查詢在不使用索引的情況下執行完整表格掃描，導致在表格中有許多記錄時效能降低的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61756。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p9

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`magento_salesrule_filter`查詢在不使用索引的情況下執行完整資料表掃描，導致資料表中有許多記錄時，`AdvancedSalesRule`篩選器的效能降低。

<u>要再現的步驟</u>：

1. 使用多個有效銷售規則結帳。

<u>預期結果</u>：

改善銷售規則的效能。

<u>實際結果</u>：

查詢會執行完整表格掃描，而且無法利用索引，導致在表格中有許多記錄時效能降低。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。