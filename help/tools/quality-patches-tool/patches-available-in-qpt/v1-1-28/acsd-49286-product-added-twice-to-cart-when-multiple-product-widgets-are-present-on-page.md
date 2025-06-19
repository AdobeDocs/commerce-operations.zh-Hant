---
title: ACSD-49286：出現多個產品Widget時，產品會新增到購物車兩次
description: 套用ACSD-49286修補程式來修正Adobe Commerce問題，此問題導致當頁面上出現多個產品Widget時，產品會新增至購物車兩次。
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286：出現多個產品Widget時，產品會新增到購物車兩次

ACSD-49286修補程式修正了當頁面上出現多個產品Widget時，產品會新增至購物車兩次的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-49286。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當頁面上出現多個產品Widget時，產品會新增至購物車兩次。

<u>要再現的步驟</u>：

1. 登入Admin並移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. 在內容區段中，使用[!DNL Page Builder]按一下&#x200B;**[!UICONTROL Edit]**。
1. 新增兩個資料列元素至&#x200B;**[!UICONTROL Content]**。
1. 將產品新增至兩個列元素。
1. 在第一列，將產品外觀設定為[!UICONTROL Product Grid]並選取要顯示的任何類別。
1. 在第二列，將產品外觀設定為[!UICONTROL Product Carousel]，並選取要顯示的其他類別。
1. 前往店面&#x200B;**[!UICONTROL Home Page]**，並從產品格線新增一項產品。
1. 從[!UICONTROL Product Carousel]新增其他產品。

<u>預期結果</u>：

將產品從[!UICONTROL Product Grid]加入購物車後，產品數量不應加倍。

<u>實際結果</u>：

從[!UICONTROL Product Grid]將產品加入購物車後，產品數量會加倍。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
