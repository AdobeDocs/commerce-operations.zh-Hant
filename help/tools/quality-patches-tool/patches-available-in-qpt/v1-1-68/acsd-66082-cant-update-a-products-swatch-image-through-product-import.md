---
title: ACSD-66082：無法透過產品匯入更新產品的色票影像
description: 套用ACSD-66082修補程式以修正Adobe Commerce的問題，其中上傳swatch_image欄位設為EMPTY_VALUE的CSV檔案以取消設定色票影像會導致匯入程式失敗並出現錯誤。
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: bdd15514c6b6ece6c7f33a41267357b4a24261f1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-66082：無法透過產品匯入更新產品的色票影像

ACSD-66082修補程式修正無法透過產品匯入更新產品的色票影像的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66082。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

上傳CSV檔案時，`swatch_image`欄位設為`EMPTY_VALUE`以取消設定色票影像，會導致匯入程式因錯誤而失敗。

<u>要再現的步驟</u>：

1. 建立簡單的產品。 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。 按一下&#x200B;**[!UICONTROL Add Product]**&#x200B;按鈕旁的向下箭頭，然後選擇&#x200B;**[!UICONTROL Simple Product]**。 將其&#x200B;**[!UICONTROL SKU]**&#x200B;設定為&#x200B;*ABC*。
1. 將名為&#x200B;*testing.png*&#x200B;的PNG影像上傳至`var/import/images/`。
1. 建立包含下列內容的CSV檔案：

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. 移至&#x200B;**[!UICONTROL System]** > **[!UICONTROL Import]**，調整下列設定以匯入檔案：
   * **[!UICONTROL Entity type]**： *產品*
   * **[!UICONTROL Import Behavior]**： *新增/更新*
   * 按一下&#x200B;**[!UICONTROL Choose File]**&#x200B;以選取在上一步建立的CSV檔案進行匯入。 匯入成功，色票即會新增。
1. 使用以下內容更新CSV：

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. 重複匯入程式。

<u>預期結果</u>：

色票影像未設定。

<u>實際結果</u>：

匯入程式擲回錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
