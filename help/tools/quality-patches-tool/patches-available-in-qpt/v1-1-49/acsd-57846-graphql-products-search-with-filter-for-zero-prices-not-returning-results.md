---
title: ACSD-57846：使用零價格篩選條件搜尋的GraphQL產品未傳回結果
description: 套用ACSD-57846修補程式以修正Adobe Commerce的問題，若從零開始篩選產品會導致對 [!DNL OpenSearch] 的請求格式錯誤，且不會傳回任何結果。
feature: GraphQL, Products
role: Admin, Developer
exl-id: ec523a54-201b-4a8f-85ce-cbe1d0bf1304
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-57846：使用零價格篩選條件搜尋的GraphQL產品未傳回結果

ACSD-57846修補程式修正了從零開始篩選產品會導致向[!DNL OpenSearch]提出的格式錯誤請求，且不會傳回任何結果的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49時，即可使用此修補程式。 修補程式ID為ACSD-57846。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在GraphQL產品搜尋中篩選價格為零的產品，會導致對[!DNL OpenSearch]的請求格式錯誤，且不會傳回任何結果。

<u>要再現的步驟</u>：

1. 使用兩個簡單產品建立類別：
   * 簡單1 — 價格$0
   * 簡單2 — 價格$10
1. 請確定兩個產品都在前端可見。
1. 傳送具有`price:{from:"1"}`的請求。

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"1"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

1. 這會傳回產品&#x200B;*simple2*。
1. 現在傳送含有`price:{from:"0"}`的請求。

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"0"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

<u>預期結果</u>：

傳回產品&#x200B;*simple1*&#x200B;和&#x200B;*simple2*。

<u>實際結果</u>：

不會傳回任何產品。

```json
{
    "data": {
        "products": {
            "totalResult": 0,
            "productItems": []
        }
    }
}
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
