---
title: 「ACSD-48404： *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*按下瀏覽器的[上一步]按鈕時導致錯誤」
description: 套用ACSD-48404修補程式來修正Adobe Commerce問題，其中*[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*會在按下瀏覽器的「上一步」按鈕時造成錯誤。
feature: Categories
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-48404： *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]*&#x200B;在按下瀏覽器的返回按鈕時導致錯誤

ACSD-48404修補程式修正了&#x200B;*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]*&#x200B;在按下瀏覽器的返回按鈕時導致錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-48404。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]*&#x200B;會在按下瀏覽器的返回按鈕時造成錯誤。


<u>要再現的步驟</u>：

1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**，並將&#x200B;*[!UICONTROL Remember Category Pagination]*&#x200B;設定為&#x200B;*是*。
1. 在店面開啟類別。
1. 在&#x200B;*[!UICONTROL Show Per Page]*&#x200B;下拉式清單中選取非預設值的值。 選取選項後，頁面會重新載入。
1. 重新載入頁面後，按一下目錄頁面上的任何產品。
1. 在開啟的產品詳細資料頁面上，按一下瀏覽器的&#x200B;**[!UICONTROL Back]**&#x200B;按鈕。

<u>預期結果</u>：

目錄頁面會再次開啟。

<u>實際結果</u>：

類別頁面傳回錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
