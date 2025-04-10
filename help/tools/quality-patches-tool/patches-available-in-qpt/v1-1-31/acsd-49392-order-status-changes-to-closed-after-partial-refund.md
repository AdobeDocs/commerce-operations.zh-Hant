---
title: ACSD-49392：部分退款後，訂單狀態變更為已關閉
description: 套用ACSD-49392修補程式以修正Adobe Commerce問題，該問題導致捆綁產品的部分退款後，訂單狀態變更為已關閉。
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
source-git-commit: 67e050b4ceccc3f30bf8cd49125525b2e8d8b0dd
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392：部分退款後，訂單狀態變更為已關閉

>[!NOTE]
>
>修正程式ACSD-49392已由2.4.6-p7至2.4.6-p10版的修正程式[ACSD-57003](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing)取代。

ACSD-49392修補程式修正套件產品部分退款後，訂單狀態變更為已關閉的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.31時，即可使用此修補程式。 修補程式ID為ACSD-49392。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.3.7-p4和2.4.1 - 2.4.6-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在套裝產品的部分退款後，訂單狀態會變更為已關閉。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce並建立任何隨附產品，或使用現有的隨附產品。
1. 以這個數量大於1的套件產品下訂單。
1. 移至admin，從&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Order]**&#x200B;開啟步驟2中建立的訂單，並建立發票。 觀察訂單狀態。 它將會在處理中。
1. 建立部分銷退折讓單（不要退款給捆綁銷售中的所有產品）。
1. 檢查訂單狀態。

<u>預期結果</u>

為套件產品建立部份銷退折讓單後，訂單狀態為處理中。

<u>實際結果</u>

為套件產品建立部份銷退折讓單之後，訂單狀態為完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
