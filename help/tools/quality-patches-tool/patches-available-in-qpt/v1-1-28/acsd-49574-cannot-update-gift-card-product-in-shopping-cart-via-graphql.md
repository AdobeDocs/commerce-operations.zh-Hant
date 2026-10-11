---
title: ACSD-49574：無法透過GraphQL更新購物車中的禮品卡產品
description: 套用ACSD-49574修補程式，修正無法透過GraphQL更新購物車中禮品卡產品的Adobe Commerce問題。
feature: Admin Workspace, Gift, GraphQL, Orders, Products, Shopping Cart
role: Admin
exl-id: 31dede84-3733-4481-b21d-526494eb8e9b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '381'
ht-degree: 0%
---
# ACSD-49574：無法透過GraphQL更新購物車中的禮品卡產品

ACSD-49574修補程式修正無法透過GraphQL更新購物車中的禮品卡產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-49574。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法透過GraphQL更新購物車中的禮品卡產品。

<u>要再現的步驟</u>：

1. 建立禮品卡產品。
1. 透過GraphQL將禮品卡產品加入購物車。
1. 嘗試使用`updateCartItems`變異，透過GraphQL更新購物車中的禮品卡產品欄位。

   GraphQL使用範例：

   ```GraphQL
   mutation ($cartId: String!, $cartItems: [CartItemUpdateInput!]!){
       updateCartItems(
           input: {
               cart_id: $cartId,
               cart_items: $cartItems
           }
       )   {
           cart {
               id
               items {
                   uid
                   quantity
                   product {
                       sku
                   }
                   ... on GiftCardCartItem {
                       sender_name
                       sender_email
                       recipient_name
                       recipient_email
                       message
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   
   variables
   {
       "cartId": "sDrOu06VYlGejhDivQMcnmcNPSxTMUDd",
       "cartItems": [
           {
               "cart_item_id": 113,
               "quantity": 1,
               "customizable_options": [{
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX25hbWU=",
                       "value_string": "sender_name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX2VtYWls",
                       "value_string": "sender_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X25hbWU=",
                       "value_string": "recipient name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X2VtYWls",
                       "value_string": "recipient_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfbWVzc2FnZQ==",
                       "value_string": "message"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvY3VzdG9tX2dpZnRjYXJkX2Ftb3VudA==",
                       "value_string": "10"
                   }
               ]
           }]
   }
   ```

<u>預期結果</u>：

所有禮品卡產品欄位(sender_name、sender_email、recipient_name、recipient_email、message、amount)都使用`updateCartItems`變異進行更新。

<u>實際結果</u>：

僅更新金額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
