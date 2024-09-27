---
title: 'ACSD-53309：可自訂選項和[!UICONTROL Regular Price]標籤的稅捐沖銷不完整'
description: 套用ACSD-53309修補程式，以修正當選取可自訂選項時，'[!UICONTROL Regular Price]'標籤中未完全套用稅金的Adobe Commerce問題。
feature: Taxes, Shipping/Delivery
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53309：可自訂選項和&#39;[!UICONTROL Regular Price]&#39;標籤的稅捐應用模組不完整

ACSD-53309修補程式修正了選取可自訂選項時，&#39;[!UICONTROL Regular Price]&#39;標籤中未完全套用稅金的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-53309。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

選擇可自訂的選項時，稅捐未完全反映在&#39;[!UICONTROL Regular Price]&#39;標籤中。

<u>要再現的步驟</u>：

1. 登入「管理」面板。
1. 導覽至「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**」以設定稅捐設定。

   * [!UICONTROL Tax Classes]：

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]：

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]：

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]：

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]：

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. 設定&#x200B;**[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *英國*。

1. 建立下列&#x200B;*[!UICONTROL Tax Rate]*&#x200B;和&#x200B;*[!UICONTROL Tax Rules]*：

   * [!UICONTROL Country] =美國
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. 建立簡單產品並設定下列專案：
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * 在下拉式清單中，將型別設定為自訂選項，價格設定為15%
1. 前往店面中所做簡單專案的產品頁面。
1. 選擇已建立的自訂選項&#x200B;*15%*。

<u>預期結果</u>：

* 20%的稅適用於選取的自訂選項。
* &#39;[!UICONTROL Regular Price]&#39; = 151.80。

<u>實際結果</u>：

* 選取的自訂選項未套用20%稅捐。
* &#39;[!UICONTROL Regular Price]&#39; = 148.50。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
