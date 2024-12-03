---
title: MDVA-37748： GraphQL查詢傳回未指派給共用目錄的產品
description: MDVA-37748修補程式修正GraphQL查詢傳回未指派給共用目錄之產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-37748。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
exl-id: 8aa00953-dbf0-4533-9b53-b809bf59ec20
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-37748： GraphQL查詢傳回未指派給共用目錄的產品

MDVA-37748修補程式修正GraphQL查詢傳回未指派給共用目錄之產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-37748。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL查詢會傳回未指派給共用目錄的產品。

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 建立兩個產品並將其指派至類別：
   * 產品1 — 公開
   * 產品2

1. 將「產品1 — 公用」指派給「預設（一般）」共用目錄。
1. 建立其他自訂共用目錄並將其指派給「產品2」。
1. 建立新公司，並將其指派給在步驟三中建立的其他共用目錄。
1. 在cron執行/重新索引後，在前端驗證如果您未登入，是否可以看到「產品1 — 公開」。
1. 以步驟4所建立公司的管理員身分登入，驗證您僅看到「產品2」。
1. 使用下列GraphQL查詢請求授權Token：

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) {
        token
      }
    }
    </code>
    </pre>

1. 新增標頭&#x200B;**Authorization Bearer value-of-the-token**&#x200B;並執行下列GraphQL查詢：

   <pre>
    <code class="language-graphql">
    {
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) {
          total_count
          page_info {
            page_size
            current_page
          }
          aggregations {
            attribute_code
            count
            label
            options {
              label
              value
              count
            }
          }
          items {
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers{
              final_price{
                  value
                  currency
                }
              discount{
                  amount_off
                  percent_off
                }
              quantity
            }
            price_range {
             maximum_price {
              regular_price {
                value
              }
              final_price {
                value
              }
            }
            minimum_price {
              regular_price {
                value
              }
              final_price {
               value
              }
            }
          }
          image {
           url
          }
          thumbnail {
           url
          }
          small_image {
           url
          }
          media_gallery {
           url
          }
          ... on ConfigurableProduct {
            configurable_options {
             id

             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
               swatch_data {
                 value
               }
            }
            product_id
          }
          variants {
            product {
              id
              name
              sku
              #margin
              #margin_percentage
              image {
                url
              }
              small_image {
                url
              }
              thumbnail {
                url
              }
              media_gallery{
                url
              }
              attribute_set_id
              ... on PhysicalProductInterface {
                weight
              }
              price_range {
                minimum_price {
                  regular_price {
                    value
                    currency
                  }
                }
              }
            }
            attributes {
              label
              code
              value_index
            }
          }
        }
      }

    }
}
</code>
</pre>

<u>預期結果</u>：

GraphQL傳回的計數和產品只會考慮指派給與登入使用者相關聯之共用目錄的產品。

<u>實際結果</u>：

只傳回「產品2」，但`total_count`顯示兩個。

<pre>
<code class="language-graphql">
{
  "data": {
    "products": {
      "total_count": 2,
      "page_info": {
        "page_size": 100,
        "current_page": 1
      },
      "aggregations": [
        {
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": [
            {
              "label": "0-100",
              "value": "0_100",
              "count": 1
            },
            {
              "label": "100-200",
              "value": "100_200",
              "count": 1
            }
          ]
        },
        {
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": [
            {
              "label": "Cat 1",
              "value": "3",
              "count": 2
            }
          ]
        }
      ],
      "items": [
        {
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": {
            "html": ""
          },
          "short_description": {
            "html": ""
          },
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": [
            {
              "final_price": {
                "value": 90,
                "currency": "USD"
              },
              "discount": {
                "amount_off": 10,
                "percent_off": 10
              },
              "quantity": 1
            }
          ],
          "price_range": {
            "maximum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            },
            "minimum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            }
          },
          "image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          },
          "thumbnail": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          },
          "small_image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          },
          "media_gallery": []
        }
      ]
    }
  }
}
</code>
</pre>

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的[修補程式區段。
