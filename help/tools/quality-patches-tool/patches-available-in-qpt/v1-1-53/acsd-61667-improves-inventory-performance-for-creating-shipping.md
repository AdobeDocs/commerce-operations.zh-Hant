---
title: ACSD-61667：改善建立出貨時的存貨效能
description: 套用ACSD-60584修補程式，以提升存貨效能，方便建立出貨流程，因應多個貨源在店內取貨的情況。
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667：改善建立出貨時的存貨效能

ACSD-61667修補程式修正了在啟用[[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) （原為MSI）取貨商店且使用多個來源時，商家無法送貨訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-61667。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用MSI取貨商店時，您無法運送具有多個來源的訂單。 此修補程式可改善存貨效能，以建立出貨流程，因應多個貨源在店內取貨的情況。

<u>必要條件：</u>：

Adobe Commerce詳細目錄模組已安裝並啟用。

<u>要再現的步驟</u>：

1. 建立超過&#x200B;*10*&#x200B;個來源並啟用其收取位置。
1. 已在&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;下啟用收取商店。
1. 建立大量取貨訂單。
1. 移至&#x200B;**[!UICONTROL Admin login]**&#x200B;並選取&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**。
1. 篩選及檢查擱置中的訂單。
1. 按一下&#x200B;**[!UICONTROL Ship]**。

<u>預期結果</u>：

出貨頁面如預期般載入。

<u>實際結果</u>：

您收到&#x200B;*503最大執行逾時*&#x200B;錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
