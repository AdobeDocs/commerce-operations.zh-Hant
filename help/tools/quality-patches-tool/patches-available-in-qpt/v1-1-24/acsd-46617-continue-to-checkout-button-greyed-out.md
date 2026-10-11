---
title: ACSD-46617：小計大於設定的最小訂購量時，**[!UICONTROL Continue to Checkout]**按鈕會變成灰色
description: 套用ACSD-46617修補程式以解決Adobe Commerce的問題，即使**[!UICONTROL Continue to Checkout]**小計大於設定的最小訂購量，按鈕仍會呈現灰色。
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 6%
---
# ACSD-46617：小計大於&quot;[!UICONTROL Minimum Order Amount]&quot;時，&quot;[!UICONTROL Continue to Checkout]&quot;按鈕會變成灰色

此ACSD-46617修補程式解決&#x200B;**[!UICONTROL Continue to Checkout]**&#x200B;按鈕灰顯的問題，即使小計大於設定的最小訂購量。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-46617。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使小計大於設定的最小訂購量，**[!UICONTROL Continue to Checkout]**&#x200B;按鈕也會呈現灰色。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]**&#x200B;並設定下列專案：
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;
     [!UICONTROL Minimum Amount]&#x200B;: *2*

1. 建立[!UICONTROL Cart Price Rule]。
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
     * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
     * &#x200B;
       [!UICONTROL Discount Amount]&#x200B;: *92*
     * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. 建立價格為$25的產品。
1. 將產品新增至購物車。
1. 前往購物車，選取$5 **[!UICONTROL Flat Rate shipping]**&#x200B;方法並套用優惠券代碼。
1. 前往結帳、完成送貨，然後導覽至&#x200B;**[!UICONTROL Paytment]**&#x200B;區段。
1. 返回購物車。

<u>預期結果</u>：

最小訂單金額沒有錯誤，因為總計$2.4大於所需金額$2。

<u>實際結果</u>：

* 即使總計$2.4大於最小訂單金額$2，最小訂單金額仍然存在錯誤。
* **[!UICONTROL Continue to Checkout]**&#x200B;按鈕呈現灰色。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
