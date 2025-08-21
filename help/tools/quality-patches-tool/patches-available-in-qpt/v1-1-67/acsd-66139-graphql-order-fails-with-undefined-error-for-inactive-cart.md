---
title: ACSD-66139：非作用中購物車的GraphQL訂購失敗並出現「未定義」錯誤
description: 套用ACSD-66139修補程式以修正Adobe Commerce問題，其中針對不存在或非使用中的購物車下訂單時，GraphQL在轉譯錯誤訊息時傳回「未定義」錯誤碼，而非特定錯誤碼。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 16d95ae0d58dfdc88a5fab725a37d353d3ee5c96
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# ACSD-66139：非作用中購物車的GraphQL訂購失敗並出現「UNDEFINED」錯誤

ACSD-66139修補程式修正了以下問題：當訂購不存在的或非使用中的購物車時，GraphQL傳回&#x200B;*UNDEFINED*&#x200B;錯誤碼，而不是錯誤訊息轉譯時傳回的特定錯誤碼。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為ACSD-66139。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新到最新版本，並在[[!DNL Quality Patches Tool]：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)上檢查相容性。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果錯誤訊息已轉譯，GraphQL在訂購不存在的或非使用中的購物車時會傳回&#x200B;*UNDEFINED*&#x200B;錯誤碼，而不是特定錯誤碼。

<u>要再現的步驟</u>：

1. 新增`app/i18n/Magento/de_DE/de_DE.csv`並包含下列錯誤字串轉譯：

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. 在「管理員」面板中建立商店檢視。 前往&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**。 按一下「**[!UICONTROL Create Store View]**」，然後針對&#x200B;**[!UICONTROL Code]**&#x200B;輸入代碼`test`。
1. 將`german`語言指派給新建立的存放區檢視。
1. 執行`setup:upgrade`和`setup:static-content:deploy -f`。
1. 使用標頭&#39;Store:test&#39;執行下列GraphQL查詢：

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>預期結果</u>：

更正錯誤回應：

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>實際結果</u>：

傳回的`error_code`是&#x200B;*未定義*：

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
