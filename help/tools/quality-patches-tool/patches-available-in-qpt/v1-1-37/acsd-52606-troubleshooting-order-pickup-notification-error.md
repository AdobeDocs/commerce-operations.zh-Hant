---
title: ACSD-52606：當使用者按一下「通知訂單已準備好取貨」時顯示的錯誤訊息
description: 套用ACSD-52606修補程式以修正Adobe Commerce問題，該問題導致使用者按一下**[!UICONTROL Notify Order is Ready for Pickup]**時顯示錯誤訊息。
feature: Orders, User Account
role: Admin, Developer
exl-id: d0b5a7a6-0d32-4019-8f28-60722fce1a99
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%
---
# ACSD-52606：當使用者按一下「通知訂單已準備好取貨」時顯示的錯誤訊息

ACSD-52606修補程式修正了使用者按一下&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;時，顯示錯誤訊息&#x200B;*您的訂單未準備好取貨*&#x200B;的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.37時，即可使用此修補程式。 修補程式ID為ACSD-52606。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤訊息&#x200B;*當使用者按一下&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;時，畫面會顯示您的訂單未準備好取貨*。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 安裝新的執行個體。
1. 建立新的來源和庫存。
1. 將新來源指派給預設網站。
1. 啟用新建立來源的取車地點。
1. 移至「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**」並啟用&#x200B;**[!UICONTROL In-Store Delivery]**。
1. 為所有庫存及&#x200B;*[!UICONTROL Manage Stock = No]*&#x200B;建立具有&#x200B;*QTY=0*&#x200B;的&#x200B;*庫存*&#x200B;簡單產品，並將其指派給兩個來源。
1. 從前端使用上一步驟中建立的產品建立訂單，選擇&#x200B;*[!UICONTROL In-Store Pickup]*&#x200B;作為傳遞方法。
1. 在Admin中，移至&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**。
1. 按一下&#x200B;**[!UICONTROL Notify order is ready for pickup]**。

<u>預期結果</u>：

您會收到無錯誤的通知。

<u>實際結果</u>：

您收到下列錯誤訊息： *您的訂單尚未準備好取貨*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
