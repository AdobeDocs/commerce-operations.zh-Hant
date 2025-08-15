---
title: ACSD-47908： *應為小於或等於0的值*結帳時發生錯誤
description: 套用ACSD-47908修補程式來修正Adobe Commerce錯誤*在結帳期間於出貨步驟上選取來源和數量時，必須有一個小於或等於0的值*。
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-47908： *結帳期間應該有小於或等於0的值*&#x200B;錯誤

ACSD-47908修補程式修正了錯誤&#x200B;*在結帳期間於送貨步驟中選取來源和數量時，應該會有一個小於或等於0的值*。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-47908。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

結帳時，在出貨步驟中選取來源和數量時，擲回下列錯誤： *應該為小於或等於0的值*。

<u>必要條件</u>：

安裝Adobe Commerce Inventory management (MSI)模組。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]**」並設定多個來源。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]**」並建立新庫存。
   * 現在將來源指派給新庫存。
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;並編輯至少一個產品。
   * 確定產品已指定給新的來源，並指定可用數量。
1. 前往&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;並建立新訂單。
1. 將這些產品新增至訂單並放置。
1. 按一下&#x200B;**[!UICONTROL Ship]**。
1. 選取出貨來源。
1. 指定要出貨的每一料號數量。
1. 重新載入頁面。
1. 按一下&#x200B;**[!UICONTROL Proceed to Shipment]**。

<u>預期結果</u>：

新出貨頁面會順利開啟。

<u>實際結果</u>：

* 無法驗證輸入的數量。
* 擲回下列錯誤： *請輸入小於或等於0*&#x200B;的值。

  然而，錯誤不一致，且可能不會一律出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
