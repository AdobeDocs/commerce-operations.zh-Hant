---
title: ACSD-64431：請求中有優惠券代碼的「placeOrder」突變擲回內部伺服器錯誤
description: 套用ACSD-64431修補程式以修正Adobe Commerce問題，其中請求中包含優惠券程式碼資訊的「placeOrder」變異會擲回內部伺服器錯誤，而非成功下訂單。
feature: GraphQL, Orders, Promotions/Events
role: Admin, Developer
exl-id: 13918f3e-842b-4b2e-b2e2-2d8add542a87
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-64431：請求中有優惠券代碼的「placeOrder」突變擲回內部伺服器錯誤

ACSD-64431修補程式修正了要求中包含優惠券代碼資訊的`placeOrder`突變擲回內部伺服器錯誤，而非成功下訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-64431。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

要求中包含優惠券代碼資訊的`placeOrder`突變會擲回內部錯誤，而不是順利下訂單。

<u>要再現的步驟</u>：

1. 建立具有&#x200B;_SKU 2836611_&#x200B;的簡單產品。
1. 建立&#x200B;**[!UICONTROL Cart Price Rule]**、將&#x200B;**[!UICONTROL Coupon]**&#x200B;設為`Specific Coupon`並輸入&#x200B;_TEST1234_&#x200B;作為抵用券代碼。
1. 建立客戶：

   ```
   mutation {
   createCustomer(
       input: {
       firstname: "John"
       lastname: "Doe"
       email: "john.doe@example.com"
       password: "b1b2b3l@w+"
       is_subscribed: true
       }
   ) {
       customer {
       firstname
       lastname
       email
       is_subscribed
       }
   }
   }
   ```

1. 產生客戶權杖。 您可以針對後續請求使用此代號。

   ```
   mutation {
   generateCustomerToken(email: "john.doe@example.com", password: "b1b2b3l@w+") {
       token
   }
   }
   ```

1. 建立空的購物車。 儲存購物車ID並用於後續請求。

   ```
   mutation {
       createEmptyCart
   } 
   ```

1. 將產品新增至購物車：

   ```
   mutation {
       addProductsToCart(
           cartId: "xxxx"
           cartItems: [{ quantity: 1, sku: "2836611" }]
       ) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                           sku
                       }
                       ... on ConfigurableCartItem {
                           configurable_options {
                               configurable_product_option_uid
                               value_label
                           }
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
           }
           user_errors {
               code
               message
           }
       }
   }
   ```

1. 套用抵用券：

   ```
   mutation {
       applyCouponToCart(input: { cart_id: "xxxx", coupon_code: "TEST1234" }) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
               applied_coupons {
                   code
               }
               prices {
                   grand_total {
                       value
                       currency
                   }
               }
           }
       }
   }
   ```

1. 設定送貨地址：

   ```
   mutation {
       setShippingAddressesOnCart(
           input: {
               cart_id: "xxxxx"
               shipping_addresses: [
                   {
                       address: {
                           firstname: "John"
                           lastname: "Doe"
                           company: "Company Name"
                           street: ["3320 N Crescent Dr", "Beverly Hills"]
                           city: "Los Angeles"
                           region: "CA"
                           region_id: 12
                           postcode: "90210"
                           country_code: "US"
                           telephone: "123-456-0000"
                           save_in_address_book: false
                       }
                   }
               ]
           }
       ) {
           cart {
               shipping_addresses {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
                   available_shipping_methods {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                   }
               }
           }
       }
   }
   ```

1. 設定送貨方法：

   ```
   mutation {
       setShippingMethodsOnCart(
           input: {
               cart_id: "xxxx"
               shipping_methods: [{ carrier_code: "flatrate", method_code: "flatrate" }]
           }
       ) {
           cart {
               shipping_addresses {
                   selected_shipping_method {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   ```

1. 設定帳單地址：

   ```
   mutation {
       setBillingAddressOnCart(
           input: {
               cart_id: "xxxx"
               billing_address: {
                   address: {
                       firstname: "John"
                       lastname: "Doe"
                       company: "Company Name"
                       street: ["64 Strawberry Dr", "Beverly Hills"]
                       city: "Los Angeles"
                       region: "CA"
                       region_id: 12
                       postcode: "90210"
                       country_code: "US"
                       telephone: "123-456-0000"
                       save_in_address_book: true
                   }
               }
           }
       ) {
           cart {
               billing_address {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
               }
           }
       }
   }
   ```

1. 設定付款方式：

   ```
   mutation {
       setPaymentMethodOnCart(
           input: { cart_id: "xxxx", payment_method: { code: "checkmo" } }
       ) {
           cart {
               selected_payment_method {
                   code
               }
           }
       }
   }
   ```

1. 下訂單：

   ```
   mutation {
   placeOrder(
       input: {
       cart_id: "{{cart_id}}"
       }
   ) {
       orderV2 {
       number
       token
       }
       errors {
       message
       code
       }
   }
   }
   ```


<u>預期結果</u>：

應該下訂單。

<u>實際結果</u>：

出現下列錯誤訊息：
`"message": "Internal server error"`

`exception.log`包含下列錯誤：

```
    report.ERROR: "discount_model" value should be specifiedGraphQL (1:135)
    1: mutation { placeOrder(input: {cart_id: "xxxx"}) { orderV2 { total { discounts { amount { currency value } coupon { code } } } } errors { message code } } }
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
