---
title: ACSD-60326：對客戶[!UICONTROL Returns]狀態的GraphQL查詢發生錯誤
description: 套用ACSD-60326修補程式以修正Adobe Commerce問題，該問題導致客戶[!UICONTROL Returns]狀態的GraphQL查詢發生錯誤。
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326：對客戶[!UICONTROL Returns]狀態的GraphQL查詢發生錯誤

ACSD-60326修補程式修正了客戶[!UICONTROL Returns]狀態的GraphQL查詢中發生錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51時，即可使用此修補程式。 修補程式ID為ACSD-60326。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

對客戶[!UICONTROL Returns]狀態的GraphQL查詢發生錯誤。

<u>要再現的步驟</u>：

1. 使用範例資料初始化新的執行個體。
1. 在&#x200B;*[!UICONTROL Admin]*&#x200B;側邊欄上，前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**&#x200B;並將&#x200B;**[!UICONTROL Enable RMA on Storefront]**&#x200B;設為&#x200B;*是*。
1. 前往&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]**&#x200B;並填寫地址。
1. 變更客戶`roni_cost@example.com`的密碼。
1. 登入管理面板，並使用下列產品為客戶`roni_cost@example.com`下訂單：
   * *WSH12-32-Red*
   * *WSH12-32 — 紫色*
   * *WSH12-32 — 綠色*
1. 為此訂單建立&#x200B;*[!UICONTROL Invoice]*&#x200B;和&#x200B;*[!UICONTROL Shipment]*。
1. 選取&#x200B;**[!UICONTROL Create Returns]**。
1. 前往&#x200B;**[!UICONTROL Return Items]** > **[!UICONTROL Add Items]**&#x200B;並：
   * 選取&#x200B;*WSH12-32-Red*&#x200B;和&#x200B;*WSH12-32 — 紫色*
   * 按一下&#x200B;**[!UICONTROL Add Selected Products to returns]**：
      * 設定&#x200B;**[!UICONTROL Requested]** = *1*
      * 將&#x200B;**[!UICONTROL Return Reason]**&#x200B;設為&#x200B;*服務不足*
      * 將&#x200B;**[!UICONTROL Item Condition]**&#x200B;設為&#x200B;*已開啟*
      * 將&#x200B;**[!UICONTROL Resolution]**&#x200B;設為&#x200B;*退款*
   * 按一下&#x200B;**[!UICONTROL Submit Returns]**。
1. 開啟&#x200B;**[!UICONTROL Returns]**&#x200B;並選取左側的&#x200B;**[!UICONTROL Return Items]**。
   * 設定兩個產品的&#x200B;**[!UICONTROL Authorized]** = *1*
   * 將&#x200B;**[!UICONTROL Status]**&#x200B;設定為&#x200B;*WSH12-32-Purple*&#x200B;的&#x200B;*已授權*
   * 將&#x200B;**[!UICONTROL Status]**&#x200B;設定為&#x200B;*WSH12-32-Red*&#x200B;的&#x200B;*Denied*
   * 按一下&#x200B;**[!UICONTROL Save]**
1. 使用相同的產品建立新訂單。
1. 為相同的產品建立&#x200B;*[!UICONTROL Invoice]*、*[!UICONTROL Shipment]*&#x200B;和&#x200B;*[!UICONTROL Returns]*。 授權兩者並繼續，直到[!UICONTROL Returns]程式結束。
1. 使用下列GraphQL查詢產生客戶Token：

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. 使用接收的Token進行授權並執行下列查詢：

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>預期結果</u>：

查詢未顯示任何錯誤。 第二次傳回的狀態不是&#x200B;*null*。

<u>實際結果</u>：

查詢傳回內部伺服器錯誤：

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
