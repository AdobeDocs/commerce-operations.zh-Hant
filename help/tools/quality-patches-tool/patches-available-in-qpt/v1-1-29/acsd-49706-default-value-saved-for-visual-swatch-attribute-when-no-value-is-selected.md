---
title: ACSD-49706：未選取任何值時，為視覺色票屬性儲存的預設值
description: 套用ACSD-49706修補程式以修正Adobe Commerce的問題，亦即未選取任何值時，預設值會儲存為視覺色票屬性。
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706：未選取任何值時，為視覺色票屬性儲存的預設值

ACSD-49706修補程式修正了未選取值時為視覺色票屬性儲存預設值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49706。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

若未選取任何值，則會儲存視覺化色票屬性的預設值。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**。
1. 按一下&#x200B;**[!UICONTROL Add New Attribute]**。
1. 填寫欄位。

   * 例如，選擇輸入型別&#x200B;*[!UICONTROL Visual Swatch]*，然後新增多個選項（例如&#x200B;*Red*、*Green*）。 請務必選擇其中一個選項作為預設值。
   * 按一下&#x200B;**[!UICONTROL Save Attribute]**。

1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**。
1. 編輯&#x200B;*[!UICONTROL Default]*&#x200B;屬性集。
1. 將&#x200B;*[!UICONTROL New Attribute]*&#x200B;從欄&#x200B;*[!UICONTROL Unassigned Attributes]*&#x200B;移至中間欄中的&#x200B;*[!UICONTROL Product Details]*&#x200B;資料夾。

   * 按一下&#x200B;**[!UICONTROL Save]**。

1. 使用&#x200B;*[!UICONTROL Default]*&#x200B;屬性集建立新產品。

   * 將&#x200B;*[!UICONTROL New Attribute]*&#x200B;保留空白並儲存。

1. 儲存後，*[!UICONTROL New Attribute]*&#x200B;中就會顯示值。

<u>預期結果</u>：

預設不會指派任何值給&#x200B;*[!UICONTROL New Attribute]*。

<u>實際結果</u>：

儲存產品時，預設值會套用至屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
