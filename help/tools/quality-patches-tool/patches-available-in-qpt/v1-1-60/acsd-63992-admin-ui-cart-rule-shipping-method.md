---
title: ACSD-63992：管理UI中有優惠券和送貨方法條件錯誤的[!UICONTROL Cart Price Rule]
description: 套用ACSD-63992修補程式以修正Adobe Commerce問題，該問題導致無法透過Admin UI正確套用具有優惠券和基於送貨方法的[!UICONTROL Cart Price Rule]條件。
feature: Price Rules, Admin Workspace
role: Admin, Developer
source-git-commit: ef17f2f75eae16e3efada4ea08ee0f068fd60702
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-63992：管理UI中有優惠券和送貨方法條件錯誤的[!UICONTROL Cart Price Rule]

ACSD-63992修補程式修正了無法透過Admin UI正確套用具有抵用券和基於送貨方法之條件的[!UICONTROL Cart Price Rule]的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60時，即可使用此修補程式。 修補程式ID為ACSD-63992。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當購物車規則在&#x200B;**[!UICONTROL Conditions]**&#x200B;區段中包含送貨方法的條件時，透過「管理面板」建立訂單時不會套用相關優惠券代碼。 相反地，系統顯示以下錯誤：

_&lt;>優惠券代碼無效。 請驗證程式碼，然後再試一次。_

<u>要再現的步驟</u>：

1. 建立購物車價格規則並描述其條件：
   * 在&#x200B;*[!UICONTROL Conditions]*&#x200B;底下：新增條件以包含送貨方法（例如，*[!UICONTROL Flat Rate]*）。
   * 在&#x200B;*[!UICONTROL Rule Information]*&#x200B;下：將&#x200B;**[!UICONTROL Coupon]**&#x200B;設為&#x200B;*[!UICONTROL Specific Coupon]*，然後輸入&#x200B;**[!UICONTROL Coupon Code]**&#x200B;作為&#x200B;*TEST*。
1. 從「管理面板」建立新訂單，並在&#x200B;**[!UICONTROL Apply Coupon]**&#x200B;欄位中輸入優惠券代碼&#x200B;*TEST*。

<u>預期結果</u>：

已成功套用抵用券。

<u>實際結果</u>：

出現下列錯誤訊息：

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
