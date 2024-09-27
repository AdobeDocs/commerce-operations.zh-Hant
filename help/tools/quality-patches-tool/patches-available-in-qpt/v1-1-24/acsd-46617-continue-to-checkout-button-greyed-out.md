---
title: 「ACSD-46617：小計大於設定的最小訂購量時，**[!UICONTROL Continue to Checkout]**按鈕會變成灰色」
description: 套用ACSD-46617修補程式以解決Adobe Commerce的問題，即使**[!UICONTROL Continue to Checkout]**小計大於設定的最小訂購量，按鈕仍會呈現灰色。
feature: Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617：小計大於&quot;[!UICONTROL Minimum Order Amount]&quot;時，&quot;[!UICONTROL Continue to Checkout]&quot;按鈕會變成灰色

此ACSD-46617修補程式解決&#x200B;**[!UICONTROL Continue to Checkout]**&#x200B;按鈕灰顯的問題，即使小計大於設定的最小訂購量。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-46617。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使小計大於設定的最小訂購量，**[!UICONTROL Continue to Checkout]**&#x200B;按鈕也會呈現灰色。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]**&#x200B;並設定下列專案：
   * [!UICONTROL Enable]： *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. 建立[!UICONTROL Cart Price Rule]。
   * [!UICONTROL Coupon Code]： *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]： *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]：
      * [!UICONTROL Apply]： *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]： *[!UICONTROL Yes]*
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

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
