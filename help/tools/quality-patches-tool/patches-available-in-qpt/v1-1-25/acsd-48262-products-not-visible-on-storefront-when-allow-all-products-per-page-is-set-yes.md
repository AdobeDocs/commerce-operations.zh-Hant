---
title: 'ACSD-48262：當[!UICONTROL Allow All Products Per Page]設定為[!UICONTROL Yes]時，店面中不會顯示產品'
description: 套用ACSD-48262修補程式以修正[!UICONTROL Allow All Products Per Page]設定設為[!UICONTROL Yes]時店面中看不到產品的Adobe Commerce問題。
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48262：當[!UICONTROL Allow All Products Per Page]設定為&#x200B;*[!UICONTROL Yes]*&#x200B;時，店面中不會顯示產品

ACSD-48262修補程式修正當[!UICONTROL Allow All Products Per Page]設定設為&#x200B;*[!UICONTROL Yes]*&#x200B;時，在店面看不到產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25時，即可使用此修補程式。 修補程式ID為ACSD-48262。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

ACSD-48262修補程式修正當[!UICONTROL Allow All Products Per Page]設定設為&#x200B;*[!UICONTROL Yes]*&#x200B;時，在店面看不到產品的問題。

<u>要再現的步驟</u>：

1. 建立測試類別。
1. 在測試類別中建立測試產品。
1. 瀏覽產品以測試店面上的類別頁面，並確保產品可見。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]**」，並將「[!UICONTROL Allow All Products Per Page]」設定設為「*[!UICONTROL Yes]*」。
1. 清除快取。
1. 檢查店面的類別頁面。

<u>預期結果</u>：

產品隨即顯示。

<u>實際結果</u>：

產品不可見。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
