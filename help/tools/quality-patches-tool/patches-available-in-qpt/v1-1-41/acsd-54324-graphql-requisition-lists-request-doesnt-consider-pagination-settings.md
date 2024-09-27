---
title: 「ACSD-54324：GraphQL requisition_lists請求不考慮分頁設定」
description: 套用ACSD-54324修補程式，修正Adobe Commerce中GraphQL「requisition_lists」請求不考慮分頁設定並傳回所有結果的問題。
feature: B2B, Customers, GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-54324： GraphQL `requisition_lists`請求不考慮分頁設定

ACSD-54324修補程式修正GraphQL `requisition_lists`請求未考慮分頁設定的問題，並傳回所有結果。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.41時，即可使用此修補程式。 修補程式ID為ACSD-54324。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL `requisition_lists`要求不考慮分頁設定，並傳回所有結果。

<u>要再現的步驟</u>：

1. 登入管理員，並瀏覽至「**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**」。

   * 將&#x200B;*[!UICONTROL Enable Requisition List]*&#x200B;設為&#x200B;*是*。

1. 登入前端，並從頂端功能表或從&#x200B;**[!UICONTROL My Account]**&#x200B;移至&#x200B;**[!UICONTROL My Requisition Lists]**，然後建立多個請購單（範例： 7）。
1. 產生客戶Token後，請針對客戶執行以下GraphQL `requisition_lists`查詢。

   * 請確定頁面大小小於您建立的請購單清單總數（範例：4）

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. 請注意，`total_count`欄位的值顯示7，而它應顯示4。

   當專案數應與&#x200B;*頁面大小*&#x200B;相同時，也會顯示7。

<u>預期結果</u>：

* 列為&#x200B;*頁面大小*&#x200B;的數字傳回到`total_count`下，而不是記錄總數。
* 專案數量與&#x200B;*頁面大小*&#x200B;相同。

<u>實際結果</u>：

即使提及&#x200B;*頁面大小*，傳回到`total_count`下的記錄總數。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
