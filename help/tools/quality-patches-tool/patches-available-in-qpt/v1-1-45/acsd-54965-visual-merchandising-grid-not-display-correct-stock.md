---
title: 'ACSD-54965： [!UICONTROL Visual Merchandising]格線未顯示正確的庫存'
description: 套用ACSD-54965修補程式來修正Adobe Commerce的問題，也就是當產品被指派給自訂庫存時，[!UICONTROL Visual Merchandising]格線無法顯示正確的庫存。
feature: Merchandising, Categories
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965： [!UICONTROL Visual Merchandising]格線未顯示正確的庫存

ACSD-54965修補程式修正將產品指派給自訂庫存時，[!UICONTROL Visual Merchandising]格線未顯示正確庫存的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45時，即可使用此修補程式。 修補程式ID為ACSD-54965。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將產品指派給自訂庫存時，[!UICONTROL Visual Merchandising]格線未顯示正確的庫存。

<u>要再現的步驟</u>：

1. 建立新的來源。
1. 建立新庫存。
1. 建立兩個產品：
   * 一個產品僅具有自訂庫存。
   * 一個產品僅具有預設庫存。
1. 將這些產品新增至類別。
1. 移至[!UICONTROL visual Merchandising]格線(*[!UICONTROL Products in Category]*)。

<u>實際結果</u>：

在&#x200B;*[!UICONTROL All Store Views]*&#x200B;範圍內，含有自訂庫存的產品未顯示任何數量。 只有在選取&#x200B;*[!UICONTROL Default Store View]*&#x200B;範圍時，自訂庫存才會顯示產品的數量。

<u>預期結果</u>：

如果範圍是&#x200B;*[!UICONTROL All Store Views]*，格線會顯示所有庫存資訊。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
