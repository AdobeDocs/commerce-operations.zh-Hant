---
title: MDVA-43862：由於GraphQL UpdateCartItems突變錯誤，客戶無法更新購物車專案
description: MDVA-43862修補程式解決客戶因GraphQL UpdateCartItems突變錯誤而無法更新購物車專案的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-43862。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: GraphQL, Orders, Shopping Cart
role: Admin
exl-id: d8a2579f-58f5-4407-8006-d58794a84b1f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43862：由於GraphQL UpdateCartItems突變錯誤，客戶無法更新購物車專案

MDVA-43862修補程式解決客戶因GraphQL UpdateCartItems突變錯誤而無法更新購物車專案的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-43862。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1、2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶無法更新購物車專案，因為GraphQL UpdateCartItems突變錯誤。

<u>要再現的步驟</u>：

1. 指派一個簡單(MH01-XL-Gray)來建立可設定的產品(MH01)。
1. 移至Commerce Admin > **目錄** > **產品** > **SKU** > **MH01** > **可自訂選項**。
1. 新增自訂選項至產品。
   * 選項標題： Option1
   * 選項型別：欄位
   * 必要：是
   * 價格： 10.00
   * 價格型別：固定
   * SKU： MHC1
   * 最大字元數：25
1. 執行以下GraphQL查詢以產生購物車ID。

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. 記下購物車ID代碼。
1. 執行以下查詢以將可設定的產品新增到購物車：

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. 您會注意到購物車已填入可設定專案。
1. 記下傳回的uid。
1. 再次執行以下查詢以更新購物車專案。

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. 觀察回應。

<u>預期結果</u>：

購物車已更新，且沒有任何問題。

<u>實際結果</u>：

您會收到下列錯誤：

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
