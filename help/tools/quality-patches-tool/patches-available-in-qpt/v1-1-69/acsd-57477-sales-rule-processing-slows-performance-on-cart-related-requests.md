---
title: ACSD-57477：銷售規則處理會減緩購物車相關請求的效能
description: 套用ACSD-57477修補程式以修正Adobe Commerce問題，此問題發生在具有許多可用產品屬性（例如1000個屬性）的專案中，當使用變數執行AddProductsToCart GraphQL作業時，Commerce會嘗試載入所有這些產品屬性，並導致AddProductsToCart GraphQL作業發生效能緩慢問題。
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477：銷售規則處理會減緩購物車相關請求的效能

ACSD-57477修補程式修正了銷售規則處理導致購物車相關請求效能緩慢的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-57477。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果您將引數作為GraphQL變數傳送，銷售規則處理會導致購物車相關請求的效能緩慢。

<u>要再現的步驟</u>：

1. 新增1000個產品屬性。
1. 使用以下GraphQL查詢建立購物車。

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. 使用以下GraphQL查詢將產品新增到購物車。

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. 設定這些變數。

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. 只有當您以GraphQL變數的形式傳送引數時，才會發生此問題。 如果您將引數納入GraphQL查詢本身，則不會發生此問題。
1. 將引數新增至GraphQL查詢本身後，傳送相同的&#x200B;**加入購物車**&#x200B;請求。

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>預期結果</u>：

`AddProductsToCart` GraphQL作業效能不應降低。

<u>實際結果</u>：

`AddProductsToCart` GraphQL作業效能降低，因為引數以變數形式傳送時，它會載入所有產品屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]： Tools指南中用於品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具
