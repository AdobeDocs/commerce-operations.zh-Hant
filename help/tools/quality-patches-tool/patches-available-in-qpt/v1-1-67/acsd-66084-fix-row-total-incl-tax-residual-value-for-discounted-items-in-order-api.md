---
title: ACSD-66084：針對訂單API回應中的完全折扣專案，「row_total_incl_tax」會傳回接近零的殘值，而不是0.00
description: 套用ACSD-66084修補程式以修正Adobe Commerce問題，亦即訂單API回應中，「row_total_incl_tax」傳回幾乎零的殘值，而非0.00完全折扣的專案。
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 01f7059e53590c4ff6602c41eb980ac7c141af33
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# ACSD-66084：針對訂單API回應中的完全折扣專案，`row_total_incl_tax`會傳回接近零的殘值，而非0.00

ACSD-66084修補程式修正了在訂單API回應中將`row_total_incl_tax`以接近零的殘值傳回，而非完全折扣專案的0.00的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為ACSD-66084。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在訂單API回應中，`row_total_incl_tax`會以接近零的殘值傳回，而非完全折扣專案的0.00。

<u>要再現的步驟</u>：

1. 建立有價格和特價的產品。 移至「**[!UICONTROL Catalog]**」>「**[!UICONTROL Products]**」>按一下「**[!UICONTROL Add Product]**」>在「**[!UICONTROL Price]**」下將「**[!UICONTROL Special Price]**」設為$25並將「**[!UICONTROL Advanced Pricing]**」設為$16.99。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]**」並新增20%的費率。 然後前往&#x200B;**[!UICONTROL Tax Rules]**並建立規則並指派
   **[!UICONTROL Taxable Goods]**&#x200B;作為產品稅捐類別。
1. 建立具有100%折扣與優惠券的銷售規則。 移至&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]**&#x200B;並新增包含100%折扣的規則，然後使用&#x200B;**[!UICONTROL Specific Coupon]**&#x200B;並輸入您的代碼。
1. 移至「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**」>並設定稅捐設定。
1. 啟用免費送貨。 前往「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**」。 將&#x200B;**[!UICONTROL Enabled]**&#x200B;設為&#x200B;**[!UICONTROL Yes]**&#x200B;並調整設定。
1. 前往產品頁面並選取&#x200B;**[!UICONTROL Add to Cart]**。 前往購物車並套用優惠券代碼。
1. 使用適用的稅捐區下訂單。
1. 透過REST API產生管理員Token (API)。
1. 透過REST API擷取訂單詳細資料。
1. 檢查回應中的`row_total_incl_tax`。

<u>預期結果</u>：

當專案完全折扣時，`row_total_incl_tax`應該傳回適當的貨幣值，例如`0.00`。

<u>實際結果</u>：

`row_total_incl_tax`傳回近零的浮點值，例如`3.5527136788005e-15`，該值不適用於貨幣顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
