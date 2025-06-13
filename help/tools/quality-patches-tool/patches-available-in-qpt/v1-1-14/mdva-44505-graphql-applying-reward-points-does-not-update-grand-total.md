---
title: MDVA-44505：針對購物車套用獎勵點數的GraphQL查詢未更新總量
description: MDVA-44505修補程式解決以下問題：套用獎勵點的購物車的GraphQL查詢沒有考慮獎勵點，並傳回不正確的總計。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44505。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505：針對購物車套用獎勵點數的GraphQL查詢未更新總量

MDVA-44505修補程式解決以下問題：套用獎勵點的購物車的GraphQL查詢沒有考慮獎勵點，並傳回不正確的總計。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44505。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

針對套用獎勵積分購物車的GraphQL查詢不會考慮獎勵積分，並傳回不正確的總計。

<u>要再現的步驟</u>：

1. 設定獎勵點數。
1. 建立購物車並套用一些獎勵點。
1. 從`GraphQL`端點呼叫`GetCart`查詢並擷取您的購物車：

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. 檢查總計專案。
1. 現在使用rest API (`/rest/V1/carts/mine/totals`)檢查客戶的購物車總價。

<u>預期結果</u>：

購物車的GraphQL查詢傳回正確的總計，其中會考慮獎勵點。

<u>實際結果</u>：

GraphQL查詢不會考量獎勵點數，並傳回不正確的總量。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
