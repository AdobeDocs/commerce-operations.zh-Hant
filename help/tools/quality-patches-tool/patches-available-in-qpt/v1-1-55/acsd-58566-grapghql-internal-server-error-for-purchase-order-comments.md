---
title: ACSD-58566：採購單註釋的GraphQL內部伺服器錯誤
description: 套用ACSD-58566修補程式以修正Adobe Commerce問題，該問題導致在「addPurchaseOrderComment」變異中查詢「created_at」欄位時，GraphQL傳回內部伺服器錯誤。
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566：採購單註釋的GraphQL內部伺服器錯誤

ACSD-58566修補程式修正了查詢`addPurchaseOrderComment`突變中的`created_at`欄位傳回null值而非預期日期時間的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-58566。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

查詢`addPurchaseOrderComment`變異中的`created_at`欄位時，GraphQL傳回內部伺服器錯誤。

<u>必要條件</u>：

已安裝B2B模組，且已啟用公司和採購單。

<u>要再現的步驟</u>：

1. 為公司使用者產生客戶權杖。
1. 依序執行下列的GraphQL請求：
   1. 使用`customerCart`建立&#x200B;*購物車*。
   1. 使用`addProductsToCart`將產品新增至&#x200B;*購物車*。
   1. 使用`placePurchaseOrder`下訂單。
   1. 使用`addPurchaseOrderComment`新增註解至採購單。

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>預期結果</u>：

`created_at`欄位會傳回採購單註解的日期時間。

<u>實際結果</u>：

顯示null而不是`created_at`日期。

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

[[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
