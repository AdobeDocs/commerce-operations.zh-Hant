---
title: ACSD-51204：建立銷退折讓單後，產品沒有退回存貨
description: 套用ACSD-51204修補程式，以修正Adobe Commerce產品在建立銷退折讓單後未退回庫存的問題。
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%
---
# ACSD-51204：建立銷退折讓單後，產品沒有退回存貨

ACSD-51204修補程式修正建立銷退折讓單後產品未退回庫存的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-51204。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

已售出的產品在建立銷退折讓單後沒有退回存貨。

<u>要再現的步驟</u>：

1. 安裝&#x200B;**[!UICONTROL Adobe Commerce]**&#x200B;並啟用&#x200B;**[!UICONTROL Inventory Management Module]**，僅使用預設的&#x200B;*來源*&#x200B;和&#x200B;*stock*。
1. 新增數量為&#x200B;*10*&#x200B;的&#x200B;**[!UICONTROL new product]**。
1. 將產品指派給&#x200B;**[!UICONTROL default stock]**。
1. 在店面，將產品加入購物車並下訂單，訂購全部可用數量10。
1. 在管理面板中，產生訂單的&#x200B;*發票*&#x200B;和&#x200B;*出貨*。
1. 針對所有專案選取&#x200B;*返回庫存*&#x200B;核取方塊，藉此建立&#x200B;**[!UICONTROL Credit Memo]**。
1. 在管理員中檢查產品的&#x200B;**[!UICONTROL Salable Quantity]**。

<u>預期結果</u>：

產品的可銷售數量必須傳回&#x200B;*10*。

<u>實際結果</u>：

產品的可銷售數量保留為&#x200B;*0*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
