---
title: ACP2E-3841：使用子選取條件並啟用免運費時，多送貨產品的購物車價格規則無法正確套用
description: 套用ACP2E-3841修補程式，修正Adobe Commerce使用子選取條件並啟用免費運送時，多送貨產品的購物車價格規則無法正確套用的問題。
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 1abb32109d5ca4a90cdd1d210d1fae6a728699fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# ACP2E-3841：使用子選取條件並啟用免運費時，多送貨產品的購物車價格規則無法正確套用

ACP2E-3841修補程式修正了使用子選取條件並啟用免運費時，多送貨產品的購物車價格規則無法正確套用的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACP2E-3841。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p9

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用子選取條件並啟用免運費時，多送貨產品的購物車價格規則無法正確套用。

<u>必要條件</u>：

**設定：**
1. **[!UICONTROL Free Shipping]** = *已啟用*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**需要的類別：**
1. 類別測試1
1. 類別測試2

**所需產品：**
1. 產品測試1：
   1. 類別：類別測試1
   1. 價格：45美元
1. 產品測試2：
   1. 類別：類別測試2
   1. 價格：56.25美元 

      **（價格必須與此處顯示的相同，以確保測試正常運作。）**

**購物車價格規則：**

以管理員身分登入，並前往「**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**」。 請使用下列值：

**[!UICONTROL Rule Information]：**
1. **[!UICONTROL Rule Name]**：免費送貨測試
1. **[!UICONTROL Active]**： *是*
1. **[!UICONTROL Websites]**： *主要網站*
1. **[!UICONTROL Customer Groups]**： *未登入，一般，批發， Retailer*
1. **[!UICONTROL Coupon]**： *沒有優惠券*
1. **[!UICONTROL Uses per Customer]**： *0*
1. **[!UICONTROL Priority]**： *1*

**[!UICONTROL Conditions]：**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

動作：

**[!UICONTROL Percent of product price discount]** = *10*

<u>要再現的步驟</u>：

1. 登入店面。
2. 新增產品測試1。
3. 新增兩個數量的產品測試2。
4. 造訪購物車。
5. 選取&#x200B;**[!UICONTROL Check Out with Multiple Addresses]**。

<u>預期結果</u>：

沒有錯誤。

<u>實際結果</u>：

*500錯誤*

*訊息：已棄用的功能：從float 112.5到int的隱含轉換會遺失/app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php第214*&#x200B;行的精確度

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
