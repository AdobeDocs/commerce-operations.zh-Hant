---
title: ACSD-56158：將多個稅捐規則套用至購物車時，GraphQL回應中的稅捐值錯誤
description: 套用ACSD-56158修補程式，修正Adobe Commerce將多個稅捐規則套用至購物車時，GraphQL回應中的稅捐值呈現不正確的問題。
feature: GraphQL, Taxes
role: Admin, Developer
exl-id: dc22861c-cd41-402f-be37-d02c02b59433
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-56158：將多個稅捐規則套用至購物車時，GraphQL回應中的稅捐值錯誤

ACSD-56158修補程式修正將多個稅捐規則套用至購物車時，GraphQL回應中的稅捐值呈現不正確的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44時，即可使用此修補程式。 修補程式ID為ACSD-56158。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5-p5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將多個稅捐規則套用至購物車時，GraphQL回應中的稅捐值呈現不正確。

<u>要再現的步驟</u>：

1. 建立具有美國地址的客戶。
1. 導覽至「管理面板」。
1. 建立價格為$100的產品。
1. 對美國地址建立兩種稅率：一種為10%，另一種為5%。
1. 從&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Rule]**&#x200B;為美國設定兩個稅捐規則。
1. 指定一個稅率給一個規則。
1. 從前端，以具有美國地址的客戶身分登入，然後將產品新增到購物車。
1. 透過GraphQL產生客戶代號。
1. 透過GraphQL產生購物車ID。
1. 透過GraphQL取得客戶的購物車，檢查套用的稅捐是否正確：

   ```GraphQL
   {
       cart(cart_id: "o3Yqt6zkn8ncOzFxGnR1IWdT..") {
           id
           email
           billing_address {
               city
               country {
                   code
                   label
               }
               firstname
               lastname
               company
               postcode
               vat_id
               region {
                   code
                   label
               }
               street
               telephone
           }
           shipping_addresses {
               firstname
               lastname
               company
               street
               city
               postcode
               vat_id
               region {
                   code
                   label
               }
               country {
                   code
                   label
               }
               telephone
               available_shipping_methods {
                   amount {
                       currency
                       value
                   }
                   available
                   carrier_code
                   carrier_title
                   error_message
                   method_code
                   method_title
                   price_excl_tax {
                       value
                       currency
                   }
                   price_incl_tax {
                       value
                       currency
                   }
               }
               selected_shipping_method {
                   amount {
                       value
                       currency
                   }
                   carrier_code
                   carrier_title
                   method_code
                   method_title
               }
           }
           available_payment_methods {
               code
               title
           }
           selected_payment_method {
               code
               title
           }
           applied_coupons {
               code
           }
           prices {
               grand_total {
                   value
                   currency
               }
               subtotal_excluding_tax {
                   value
                   currency
               }
               subtotal_including_tax {
                   value
                   currency
               }
               applied_taxes {
                   label
                   amount {
                       currency
                       value
                   }
               }
           }
       }
   }    
   ```

<u>預期結果</u>：

各稅率會顯示其本身的稅捐金額：

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 10
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 5
        }
    }
]
```

<u>實際結果</u>：

各規則傳回的稅捐金額總計：

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    }
]
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
