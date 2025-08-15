---
title: MDVA-42046：指派給產品屬性的值不正確
description: MDVA-42046修補程式修正了更新具有日期輸入欄位的產品時，為產品屬性指派的值不正確的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-42046。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046：指派給產品屬性的值不正確

MDVA-42046修補程式修正了更新具有日期輸入欄位的產品時，為產品屬性指派的值不正確的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-42046。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.3.5-p2和2.4.0 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

儲存具有`news_from_date`和/或`news_to_date`欄位的產品後，這些欄位的值會重設為預設值。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 匯出在步驟一中建立的產品。
1. 在匯出的CSV檔案中，在`news_from_date`和`news_to_date`欄位中放入一些值。 例如：2021-05-15和2021-06-18。
1. 使用修改過的CSV檔案匯入產品。
1. 在產品格線中新增其他欄「將產品設為新的開始日期」和「將產品設為新的結束日期」。
1. 開啟產品的編輯頁面，若未進行任何變更，請按一下[儲存]。**&#x200B;**
1. 返回產品格線並檢查產品的資料。

<u>預期結果</u>：

「將產品設為新的開始日期」和「將產品設為新的結束日期」都與儲存前相同。

<u>實際結果</u>：

* 「將產品設為新的起始日期」和「將產品設為新的終止日期」欄中的值已變更。

* 「將產品設為新的開始日期」欄會顯示目前的日期，「將產品設為新的結束日期」欄是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
