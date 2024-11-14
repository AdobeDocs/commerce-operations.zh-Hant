---
title: 「MDVA-44147： [!DNL GraphQL] 要求未傳回[!UICONTROL Requisition Lists]」
description: MDVA-44147修補程式修正 [!DNL GraphQL] 要求未傳回[!UICONTROL Requisition Lists]的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44147。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: B2B, GraphQL
role: Admin
exl-id: 534c4e45-6521-45c0-ae4e-c60b754f432f
source-git-commit: fa95ca5ac2f7606386a785fb3b29f56672d555b1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-44147： [!DNL GraphQL]要求未傳回[!UICONTROL Requisition Lists]

MDVA-44147修補程式修正[!DNL GraphQL]要求未傳回[!UICONTROL Requisition Lists]的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44147。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL GraphQL]要求未傳回[!UICONTROL Requisition Lists]。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **設定** > **設定** > **一般** > **B2B功能**&#x200B;並啟用&#x200B;**[!UICONTROL Requisition List]**。
1. 以客戶身分登入，並將產品新增至[[!UICONTROL Requisition List]](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/requisition-lists/requisition-lists)。
1. 建立[客戶權杖](https://developer.adobe.com/commerce/webapi/graphql/mutations/generate-customer-token.html)。

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) {
          token
        }
      }
      </code>
      </pre>

1. 使用以下查詢來擷取客戶的所有[!UICONTROL Requisition Lists]。 使用值為`Bearer <customer_token>`的&#x200B;**Authorization**&#x200B;標頭。 如需詳細資訊，請參閱開發人員檔案中的[客戶查詢](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/)文章。

   要求：

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

   回應：

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "customer": {
          "requisition_lists": {
            "items": [
            {
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": {
                "items": [
                {
                  "uid": "MQ==",
                  "product": {
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    },
                    "quantity": 1
                  }
                  ],
                  "total_pages": 1
                }
              }
              ],
              "total_count": 1
            }
          }
        }
      }
      </code>
      </pre>

1. 從傳回的清單(MQ==)複製任何專案的UID，並使用以下查詢來取得由UID篩選的清單。

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20,
          filter: {
            uids: {
              eq: "MQ=="
            }
          }
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

<u>預期結果</u>：

傳回一個結果。

<u>實際結果</u>：

未傳回任何結果。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
