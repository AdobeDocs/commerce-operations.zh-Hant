---
title: ACSD-63062：具有多個重疊規則的購物車折扣計算不正確
description: 套用ACSD-63062修補程式，以修正套用多個重疊規則時發生錯誤購物車折扣計算的Adobe Commerce問題。
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062：具有多個重疊規則的購物車折扣計算不正確

ACSD-63062修補程式修正了套用多個重疊規則時發生錯誤購物車折扣計算的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-63062。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用多個重疊規則時，會發生錯誤的購物車折扣計算。

<u>要再現的步驟</u>：

1. 使用範例資料安裝新的執行個體。
1. 建立三個簡單的產品：

   * 簡單1:1080美元
   * 簡單2:260美元
   * 簡單3:280美元

1. 建立四個&#x200B;*[!UICONTROL Cart Price Rules]*，如下所示：

   * 規則1：

      * *[!UICONTROL Priority]*： 100
      * *[!UICONTROL Conditions]*&#x200B;索引標籤：如果總數量等於或大於3，請使用簡單2 ($280)產品
      * *[!UICONTROL Actions]*&#x200B;標籤： SKU簡單2
      * *[!UICONTROL Fixed Amount Discount]*： $80

   * 規則2：

      * *[!UICONTROL Priority]*： 200
      * *[!UICONTROL Actions]*&#x200B;標籤： SKU簡單2
      * *[!UICONTROL Percentage of Product Price Discount]*： 20%

   * 規則3：

      * *[!UICONTROL Priority]*： 300
      * *[!UICONTROL Conditions]*&#x200B;索引標籤：小計等於或大於$1000
      * 整個購物車的&#x200B;*[!UICONTROL Fixed Amount Discount]*： $100

   * 規則4：

      * *[!UICONTROL Priority]*： 400
      * *[!UICONTROL Conditions]*&#x200B;索引標籤：如果總數量等於或大於2，請使用簡單1 ($1080)產品
      * *[!UICONTROL Actions]*&#x200B;標籤： SKU簡單1
      * 整個購物車的&#x200B;*[!UICONTROL Fixed Amount Discount]*： $960

1. 前往店面，將下列具有指定數量的產品加入購物車：

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. 檢查購物車。

<u>預期結果</u>：

適用的折扣為$1352。

<u>實際結果</u>：

適用的折扣為$1525.33。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
