---
title: ACSD-50794：無法透過GraphQL從客戶訂單中移除贈品包裝
description: 套用ACSD-50794修補程式，修正Adobe Commerce使用者無法透過GraphQL從客戶訂單中移除贈品包裝的問題。
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%
---
# ACSD-50794：無法透過GraphQL從客戶訂單中移除贈品包裝

ACSD-50794修補程式修正使用者無法透過GraphQL從客戶訂單中移除贈品包裝的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-50794。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法透過GraphQL從客戶訂單中移除贈品包裝。

<u>要再現的步驟</u>：

1. 從前端建立客戶。
1. 建立簡單的產品。
1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]**&#x200B;並設定&#x200B;*[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*&#x200B;來啟用&#x200B;*[!UICONTROL Gift Messages]*。
1. 前往「**[!UICONTROL Stores]**」>「**[!UICONTROL Other Settings]**」>「**[!UICONTROL Gift Wrapping]**」建立&#x200B;*[!UICONTROL Gift Wrapping]*。
1. 取得客戶權杖。
1. 建立空的購物車customerCart。
   * 將產品加入購物車： `addProductsToCart`突變
   * 設定帳單地址： `setBillingAddressOnCart`突變
   * 設定送貨地址： `setShippingAddressesOnCart`突變
   * 設定送貨方法： `setShippingMethodsOnCart`變異（平面化）
   * 設定付款方法： `setPaymentMethodOnCart`突變(checkmo)
1. 現在使用此購物車查詢檢查禮品包裝&#x200B;*Uid*：

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. 使用`setGiftOptionsOnCart`設定禮品包裝。
1. 檢查購物車：購物車查詢。
1. 使用`setGiftOptionsOnCart`取消設定禮品包裝（將值設定為null）。
1. 再次檢查購物車：購物車查詢。
1. 排序： `placeOrder`突變。
1. 執行客戶查詢：客戶。

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u>預期結果</u>：

一旦使用者設定贈品包裝並取消設定，客戶查詢就會傳回null。

<u>實際結果</u>：

客戶查詢仍會傳回套用的贈品包裝。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
