---
title: ACSD-66963：虛擬產品折扣的「estimateTotals」突變傳回null
description: 套用ACSD-66963修補程式來修正Adobe Commerce問題，其中當折扣代碼套用至僅包含虛擬產品的購物車時，「estimateTotals」會針對折扣傳回*null*。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963：虛擬產品折扣的`estimateTotals`突變傳回null

ACSD-66963修補程式修正了當折扣代碼套用至僅包含虛擬產品的購物車時，`estimateTotals`傳回&#x200B;*null*&#x200B;折扣的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66963。 請注意，此問題已在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當折扣代碼套用至僅包含虛擬產品的購物車時，`estimateTotals`突變傳回&#x200B;*null*&#x200B;折扣。

<u>要再現的步驟</u>：

1. 建立僅包含虛擬產品的購物車。
1. 套用折扣代碼：

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>預期結果</u>：

僅包含虛擬產品的購物車折扣資訊。

    &quot;
    {
    &quot;資料&quot;： {
    &quot;estimateTotals&quot;： {
    &quot;cart&quot;： {
    &quot;prices&quot;： {
    &quot;discounts&quot;： [
    {
    &quot;amount&quot;： {
    &quot;value&quot;： 100.5，
    &quot;currency&quot;： &quot;USD&quot;
    }，
    &quot;label&quot;： &quot;第二個測試折扣代碼&quot;，
    &quot;coupon&quot;： {
    &quot;code&quot;： &quot;z3r0c00l&quot;
    }，
    &quot;applied_to&quot;： &quot;ITEM&quot;，
    &quot;type&quot;： null
    }
    ]
    }
    }
    }
    }，
    &quot;extensions&quot;：{}
    }
    &quot;&#39;

<u>實際結果</u>：

僅含虛擬產品的購物車折扣資訊傳回為&#x200B;*null*。

    &quot;&#39;
    {
    &quot;資料&quot;： {
    &quot;estimateTotals&quot;： {
    &quot;cart&quot;： {
    &quot;prices&quot;： {
    &quot;discounts&quot;： null
    }
    }
    }
    }，
    &quot;extensions&quot;： {}
    }
    &quot;&#39;

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
