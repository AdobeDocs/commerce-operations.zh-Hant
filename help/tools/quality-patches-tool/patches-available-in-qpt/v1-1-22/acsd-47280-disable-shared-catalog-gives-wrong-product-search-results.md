---
title: '[!DNL ACSD-47280]：停用共用目錄會提供錯誤的產品搜尋結果'
description: 套用 [!DNL ACSD-47280] 修補程式，以修正共用目錄功能停用時顯示正確搜尋結果的問題。
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# [!DNL ACSD-47280]：停用共用目錄會提供錯誤的產品搜尋結果

[!DNL ACSD-47280]修補程式修正[!DNL shared catalog]功能停用時正確搜尋結果的顯示。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22時，即可使用此修補程式。 [!DNL patch ID]是[!DNL ACSD-47280]。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用[!DNL patch ID]作為搜尋關鍵字來尋找修補程式。

## 問題

停用[!DNL shared catalog]會提供錯誤的產品搜尋結果。

<u>必要條件</u>：

* 已安裝[!DNL B2B]個模組

<u>要再現的步驟</u>：

1. 建立第二個網站。
1. 將產品指派至第二個網站。
1. 使用[!DNL GraphQL]檢查&#x200B;**第二個網站**&#x200B;上的產品：

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. 在預設[!DNL scope]上啟用&#x200B;**[!UICONTROL Shared Catalog]**。
1. [!DNL GraphQL]要求不再顯示第二個網站的任何產品，此為正確結果。
1. 移至第二個網站的[!DNL scope]並停用&#x200B;**[!UICONTROL Company]**。

<u>預期結果</u>：

[!DNL GraphQL]要求仍應顯示第二個網站的產品。

<u>實際結果</u>：

[!DNL GraphQL]要求未顯示第二個網站的任何產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
