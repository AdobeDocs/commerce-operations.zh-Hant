---
title: ACSD-51238：更新可設定產品並編輯價格時，會移除存貨來源
description: 套用ACSD-51238修補程式來修正Adobe Commerce問題，此問題會在更新可設定產品並編輯價格時移除庫存來源。
feature: Configuration, Inventory, Orders, Products
role: Admin
exl-id: 785f012f-e064-4ac6-b559-9e9aa42c679c
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51238：更新可設定產品並編輯價格時，會移除存貨來源

ACSD-51238修補程式修正了更新可設定產品及編輯價格時，移除庫存來源的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-51238。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

更新可設定產品並編輯價格時，會移除存貨來源。

<u>要再現的步驟</u>：

1. 安裝&#x200B;**[!DNL Adobe Commerce]**&#x200B;與&#x200B;**[!DNL Inventory module]**
1. 移至&#x200B;**[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]**&#x200B;並建立&#x200B;*兩個來源*&#x200B;和&#x200B;*兩個庫存*。
1. 建立&#x200B;**[!UICONTROL configurable product]**&#x200B;並將其指派給&#x200B;**[!UICONTROL default sources]**&#x200B;或&#x200B;**[!UICONTROL newly created sources]**。
1. 按一下&#x200B;**[!UICONTROL next button]**&#x200B;並&#x200B;*儲存*&#x200B;產品。
1. 現在編輯相同的&#x200B;**[!UICONTROL Configurable Product]**&#x200B;並按一下&#x200B;**[!UICONTROL Configuration tab]**&#x200B;內的&#x200B;**[!UICONTROL Edit Configuration]**。
1. 在`Step 3: Bulk Images,Price and Quantity`中，變更`price`，並將`Quantity`和`Images`分別保留為`Skip quantity at this time`和`Skip image uploading at this time`。
1. 按一下&#x200B;**[!UICONTROL next button]**&#x200B;並產生產品。

<u>預期結果</u>

**[!UICONTROL Configuration tab]**&#x200B;內的每個來源數量不應為空白。

<u>實際結果</u>

**[!UICONTROL Configuration tab]**&#x200B;內的每個來源數量是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
