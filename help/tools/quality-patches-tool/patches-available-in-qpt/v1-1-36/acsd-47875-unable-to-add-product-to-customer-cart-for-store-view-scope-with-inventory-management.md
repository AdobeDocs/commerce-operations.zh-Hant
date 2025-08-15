---
title: ACSD-47875：無法透過庫存管理將產品新增到購物車以商店檢視範圍
description: 套用ACSD-47875修補程式以修正Adobe Commerce問題，該問題導致無法針對具有庫存管理的特定商店檢視範圍，從管理員將產品新增到客戶購物車中。
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-47875：無法透過庫存管理將產品新增到購物車以商店檢視範圍

ACSD-47875修補程式修正無法從Admin針對具有庫存管理的特定商店檢視範圍將產品新增到客戶購物車的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.36時，即可使用此修補程式。 修補程式ID為ACSD-47875。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者無法針對已安裝MSI的特定商店檢視範圍，使用管理員中的&#x200B;**[!UICONTROL Manage Shopping Cart]**&#x200B;功能將產品新增到客戶購物車。

<u>必要條件</u>：

[!DNL Adobe Commerce Inventory Management (MSI)]模組已安裝且已啟用。

<u>要再現的步驟</u>：

1. 建立網站、商店和商店檢視。
1. 建立&#x200B;*預設*&#x200B;以外的其他來源。
1. 建立新庫存，並將其指派給新網站和新來源。
1. 為新網站建立新客戶。
1. 僅將產品指派給新網站；從預設網站取消指派。

   * 指派新的來源，並將數量&#x200B;*設為0*&#x200B;以上，並將預設來源設為&#x200B;*0*。

1. 移至Admin中的&#x200B;**[!UICONTROL Customer Edit]**&#x200B;頁面。 按一下&#x200B;**[!UICONTROL Manage Shopping Cart]**。
1. 將存放區檢視範圍變更為新的存放區檢視。
1. 前往&#x200B;**[!UICONTROL Products]**&#x200B;區段並搜尋產品。
1. 選取產品並按一下&#x200B;**[!UICONTROL Add selections to my cart]**。

<u>預期結果</u>：

產品會新增至購物車。

<u>實際結果</u>：

* 擲回下列錯誤： *您嘗試新增的產品無法使用。*
* 產品未新增至購物車。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
