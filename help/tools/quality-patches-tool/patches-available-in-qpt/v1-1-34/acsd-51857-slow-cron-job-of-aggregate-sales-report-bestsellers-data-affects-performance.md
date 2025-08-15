---
title: ACSD-51857： 'aggregate_sales_report_bestsellers_data'的緩慢cron工作會影響效能
description: 套用ACSD-51857修補程式以修正緩慢cron工作'aggregate_sales_report_bestsellers_data'影響大型'sales_order'和'sales_order_item'資料庫表格的Adobe Commerce問題。
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857： `aggregate_sales_report_bestsellers_data`的緩慢cron工作會影響效能

ACSD-51857修補程式修正緩慢cron工作`aggregate_sales_report_bestsellers_data`影響大型`sales_order`和`sales_order_item`資料庫表格的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34時，即可使用此修補程式。 修補程式ID為ACSD-51857。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`aggregate_sales_report_bestsellers_data`在`sales_order`和`sales_order_item`資料庫資料表上的Cron工作效能緩慢。

為解決此問題，擷取報表資料的主要資料查詢已重新寫入更有效率的表單。 它現在使用子查詢來決定資料子集。

為了使子查詢儘快運作，已根據`sales_order`、`SALES_ORDER_STORE_STATE_CREATED`和`store_id`資料行，為`state`資料庫資料表`created_at`新增索引。

<u>必要條件</u>

確保每天有大量訂單。

<u>要再現的步驟</u>

1. 執行`aggregate_sales_report_bestsellers_data` cron工作。
1. 檢查&#x200B;**[!UICONTROL Bestsellers]**&#x200B;標籤下要顯示在管理員控制面板中的資料。

<u>預期結果</u>：

*[!UICONTROL Quantity per source]*&#x200B;標籤下的&#x200B;**[!UICONTROL Configuration]**&#x200B;不應為空白。

<u>實際結果</u>：

*[!UICONTROL Quantity per source]*&#x200B;標籤下的&#x200B;**[!UICONTROL Configuration]**&#x200B;是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
