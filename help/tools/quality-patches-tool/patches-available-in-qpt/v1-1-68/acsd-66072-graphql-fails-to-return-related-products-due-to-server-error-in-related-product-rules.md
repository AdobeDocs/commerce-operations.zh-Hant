---
title: ACSD-66072：GraphQL無法在產品詳細資料頁面上傳回相關產品
description: 套用ACSD-66072修補程式以修正Adobe Commerce問題，此問題導致在設定相關產品規則時，由於內部伺服器錯誤，產品詳細資料頁面上無法透過GraphQL傳回相關產品。
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1cd5383d774ab0ed97b80a4abf7df5706706ea5
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66072：GraphQL無法在產品詳細資料頁面上傳回相關產品

ACSD-66072修補程式修正設定&#x200B;**[!UICONTROL Related Products Rule]**&#x200B;時，由於內部伺服器錯誤，產品詳細資料頁面上無法透過GraphQL傳回相關產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66072。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於設定&#x200B;**[!UICONTROL Related Products Rule]**&#x200B;時發生內部伺服器錯誤，產品詳細資料頁面上不會透過GraphQL傳回相關產品。

<u>要再現的步驟</u>：

1. 建立可設定的產品：
   * **產品1**： `config1`搭配`option1`
   * **產品2**： `config2`搭配`option2`

1. 建立產品並指派至類別
   * 建立&#x200B;**新類別**。
   * 將兩個產品（`config1`和`config2`）指派到此類別。

1. 導覽至「**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]**」，然後使用下列設定建立新規則：

   * **[!UICONTROL Priority]**： 1
   * **[!UICONTROL Applies To]**： **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**： 10
   * **[!UICONTROL Products to Match]**： **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**： `Product Category is the Same as Matched Product Categories`

1. 執行下列Magento CLI命令：

   ```bash
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. 使用下列裝載傳送POST要求給`../graphql`：

   ```
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u>預期結果</u>：

查詢傳回相關產品(`config1`)。

<u>實際結果</u>：

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

`var/log/exception.log`檔案包含：

```
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
