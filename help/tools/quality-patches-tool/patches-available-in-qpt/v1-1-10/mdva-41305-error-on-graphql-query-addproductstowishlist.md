---
title: 'MDVA-41305：可設定產品的GraphQL查詢addProductsToWishlist發生錯誤'
description: MDVA-41305修補程式解決使用者在GraphQL查詢可設定產品的「addProductsToWishlist」時發生錯誤。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-41305。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-41305：可設定產品的GraphQL查詢addProductsToWishlist發生錯誤

MDVA-41305修補程式解決使用者在GraphQL查詢`addProductsToWishlist`可設定產品時發生錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-41305。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者將可設定的產品（具有/沒有設定）新增到GraphQL的願望清單時，他們無法取得可設定的SKU和可設定的選項作為回應。

<u>要再現的步驟</u>：

1. 建立可設定的產品（使用藍色、灰色和一個自訂選項）。
1. 開啟前端；以客戶身分登入並建立願望清單(check wishlist_id)。
1. 開啟郵遞員並建立客戶代號：

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(email: "", password: "") {
        token
      }
     }
     </code>
     </pre>

1. 設定此Token以取得持有者授權。
1. 嘗試使用下列指示將可設定的產品&#x200B;*藍色*&#x200B;加入願望清單：

<pre>
<code class="language-graphql">
mutation {
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: [
     {
       sku: "conf2"
       selected_options: [
            "Y29uZmlndXJhYmxlLzkzLzUw"
       ]
       quantity: 1
       entered_options: [
         {
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         }
       ]
     }
    ]
  ) {
    wishlist {
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) {
        items {
         id
         quantity
         ... on ConfigurableWishlistItem  {
           child_sku
           customizable_options {
             customizable_option_uid
           }
         }
         product {
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface {
             options {
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption {
                value {
                  uid
                  sku
                  price
                  price_type
                  max_characters
                }
              }
            }
          }
          price_range {
            minimum_price {
              regular_price {
                currency
                value
              }
            }
            maximum_price {
               regular_price {
                 currency
                 value
               }
             }
           }
         }
       }
     }
   }
  user_errors {
    code
    message
   }
 }
}
</code>
</pre>

<u>預期結果</u>：

使用者可以在裝載中指定並新增至願望清單的回應中，看到已設定的一組產品選項。

<u>實際結果</u>：

使用者在回應中收到&#x200B;*內部伺服器錯誤*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。