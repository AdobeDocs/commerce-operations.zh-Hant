---
title: ACSD-49042：無法從店面訂購無限延期交貨的產品
description: 套用ACSD-49042修補程式來修正Adobe Commerce問題，此問題導致無法從店面訂購無限延期交貨的產品。
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49042：無法從店面訂購無限延期交貨的產品

ACSD-49042修補程式修正無法從店面訂購無限延期交貨的產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-49042。 請注意，問題已在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當無法從店面訂購具有無限延期交貨的產品時，就會發生錯誤。

<u>要再現的步驟</u>：

1. 設定下列組態設定：
   * **[!UICONTROL Display Out of Stock Products]**&#x200B;已設定為&#x200B;*[!UICONTROL Yes]*。
   * **[!UICONTROL Backorders]**&#x200B;已設定為&#x200B;*[!UICONTROL Allow Qty Below 0]*。
1. 新增新的&#x200B;**[!DNL custom stock]**&#x200B;和&#x200B;**[!DNL custom source]**。
1. 將產品指派給&#x200B;**[!DNL custom source]**，並確定為其設定了詳細目錄編號（例如： *10*）。
1. 在產品編輯頁面上，開啟&#x200B;**[!UICONTROL Advanced Inventory]**。 設定購物車中的&#x200B;**[!UICONTROL minimum quantity]** （例如： *160*）。 數量必須高於存貨。
1. 前往店面購買產品以建立預訂。
1. 將&#x200B;**[!UICONTROL product quantity]**&#x200B;變更為&#x200B;*0*。 關鍵點是在有預訂時從&#x200B;**[!DNL Admin panel]**&#x200B;儲存產品。
1. 開啟店面上的&#x200B;**[!UICONTROL product page]**，並嘗試將產品加入購物車。

<u>預期結果</u>：

可以將產品加入購物車，因為允許數量低於&#x200B;*0*&#x200B;的延期交貨。

<u>實際結果</u>：

產品顯示為無庫存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
