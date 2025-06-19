---
title: ACSD-61200：修正銷售總額計算中的折扣稅捐補償
description: 套用ACSD-61200修補程式以修正銷售總額計算中遺漏*[!UICONTROL Discount Tax Compensation Amount]*和*[!UICONTROL Shipping Discount Tax Compensation Amount]*，造成銷售訂單資料與優惠券報表資料不一致的Adobe Commerce問題。
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200：修正銷售總額計算中的折扣稅捐補償

ACSD-61200修補程式修正了&#x200B;*[!UICONTROL Total Amount]*&#x200B;和&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;計算中缺少&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;的問題，導致銷售訂單資料與優惠券報告資料之間出現差異。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61200。 請注意，此問題已排程在Adobe Commerce 2.4.8版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

- Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

- Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於銷售總額計算中遺失&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*，導致銷售訂單和優惠券報表資料不正確。

<u>要再現的步驟</u>：

1. 建立[!UICONTROL Tax Zone]和[!UICONTROL Tax Rule]。
1. 設定下列稅捐組態：
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. 更新「訂單」、「商業發票」及「銷退折讓單」的下列顯示設定：
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. 建立附有10%折扣優惠券的[!UICONTROL Cart Price Rule]。
1. 使用優惠券完成訂單，並產生商業發票與出貨。
1. 前往「**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]**」並產生報表。
1. 比較訂單摘要與報表中的資料。

<u>預期結果</u>：

*[!UICONTROL Total Amount]*&#x200B;和&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;計算包含&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*，將訂單摘要與報表資料比對。

<u>實際結果</u>：

銷售訂單資料與抵用券報表資料不符，因為計算中遺漏&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;與&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

- Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
- 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

[[!DNL Quality Patches Tool] 已發行：「工具」指南中用於自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
