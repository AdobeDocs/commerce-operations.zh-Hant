---
title: ACSD-64546：在UPS標籤建立期間UI和陣列至字串轉換例外中的一般錯誤訊息
description: 套用ACSD-64546修補程式以修正UI中出現一般錯誤訊息，且在UPS標籤建立期間會記錄陣列至字串轉換例外狀況的Adobe Commerce問題。 修補程式可確保UI和記錄中顯示正確的錯誤。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546：UI中的一般錯誤訊息，以及UPS標籤建立期間的&#x200B;*陣列到字串的轉換*&#x200B;例外狀況

ACSD-64546修補程式修正UI中出現一般錯誤訊息，且UPS標籤建立期間會記錄&#x200B;*陣列至字串轉換*&#x200B;例外狀況的問題，確保UI和記錄中顯示正確的錯誤。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-64546。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

UI中會顯示一般錯誤訊息，且UPS標籤建立期間會發生&#x200B;*陣列到字串的轉換*&#x200B;例外狀況。

<u>要再現的步驟</u>：

1. 使用有效地址建立客戶帳戶。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]**」並新增有效地址。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]**」並新增有效地址。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]**」並設定UPS。
1. 使用[!UICONTROL UPS]下訂單。
1. 從資料庫中的`core_config_data`移除UPS使用者ID和密碼。
1. 清除設定快取。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;中開啟建立的訂單。
1. 建立新的出貨。
   1. 選取&#x200B;**[!UICONTROL Create Shipping Label]**&#x200B;核取方塊。
   1. 按一下&#x200B;**[!UICONTROL Submit shipment]**。
   1. 將產品新增至封裝。 指定封裝大小（長度、寬度和高度）。
   1. 按一下&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>：

實際錯誤訊息會顯示在UI和記錄中。

<u>實際結果</u>：

* UI中出現下列錯誤：
  *建立送貨標籤時發生錯誤。*
* *陣列到字串的轉換*&#x200B;例外狀況會防止在記錄中顯示或儲存實際的錯誤訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：
* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：
* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
