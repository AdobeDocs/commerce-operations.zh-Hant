---
title: ACSD-52921：向GraphQL請求無庫存可設定產品的購物車詳細資料時發生錯誤
description: 套用ACSD-52921修補程式以修正Adobe Commerce問題，該問題導致從GraphQL請求無存貨可設定產品的購物車詳細資料時發生內部錯誤。
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921：向GraphQL請求無庫存可設定產品的購物車詳細資料時發生錯誤

ACSD-52921修補程式修正向GraphQL請求無庫存可設定產品的購物車詳細資料時發生內部錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-52921。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

向GraphQL請求無庫存可設定產品的購物車詳細資料時發生內部錯誤。

<u>要再現的步驟</u>：

1. 使用幾個選項建立可設定的產品。
1. 從前端（訪客結帳）將以上可設定產品的選項新增到購物車。
1. 從上述建立報價的`[ quote_id_mask ]`資料庫資料表中取得`[ masked_id ]`。
1. 執行下列GraphQL查詢以取得上述訪客購物車詳細資料。

   新增從查詢中的步驟3收到的`[ masked_id ]`。

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. 這將傳回報價詳細資料，而不會出現任何問題。
1. 移至後端並將可設定產品的&#x200B;*[!UICONTROL Stock Status]*&#x200B;更新為&#x200B;*[!UICONTROL Out of Stock]*。
1. 執行與步驟4中相同的GraphQL查詢。

<u>預期結果</u>：

錯誤訊息在回應中會正確傳送/處理。

<u>實際結果</u>：

回應GraphQL查詢時擲回&#x200B;*500內部伺服器*&#x200B;錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相關閱讀

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
