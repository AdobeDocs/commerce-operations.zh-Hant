---
title: ACSD-55610：部份取消的訂單折扣金額不正確
description: 套用ACSD-55610修補程式，修正部分取消訂單折扣金額不正確的Adobe Commerce問題。
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: b7b94c9d-e027-4601-837b-d70b7ff8bd2c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55610：部份取消的訂單折扣金額不正確

ACSD-55610修補程式修正部分取消的訂單折扣金額不正確的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-55610。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

部份取消的訂單折扣金額不正確。

<u>要再現的步驟</u>：

1. 建立購物車價格規則。

   * *[!UICONTROL Rule Name]*： *冬季優惠*
   * *[!UICONTROL Active]* = *是*
   * *[!UICONTROL Websites]* = *主要網站*
   * 選擇所有客戶群組。
   * 選取特定抵用券。
   * *[!UICONTROL Coupon Code]*： *WINTER10*
   * *[!UICONTROL Conditions]*： *[!UICONTROL If ALL of these conditions are TRUE]*： *小計(不包括 稅金)等於或大於75*
   * 套用&#x200B;*[!UICONTROL Percent of product price discount]*。
   * *[!UICONTROL Discount Amount]*： *10*
   * *[!UICONTROL Discard subsequent rules]*： *是*

1. 建立三個價格設定為100的產品。
1. 將這三個產品新增到購物車。
1. 套用抵用券。
1. 下訂單。
1. 為訂單中的一個專案開立商業發票，然後將其出貨。
1. 取消其他兩個專案。
1. 檢查`base_discount_canceled`欄。

<u>預期結果</u>：

`base_discount_cancelled`中的折扣金額正確反映。

<u>實際結果</u>：

`base_discount_cancelled`不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
