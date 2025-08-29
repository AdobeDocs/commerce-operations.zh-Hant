---
title: ACSD-66302：依商店ID （而非網站）篩選的願望清單專案
description: 套用ACSD-66302修補程式以修正 [!DNL GraphQL] 要求中依商店ID而非網站篩選願望清單專案的Adobe Commerce問題。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: c1a9eadc-0321-4f5c-ba82-533286a1f24f
source-git-commit: bec27df19ce5d34be063dce3de74ffe253c3e8f4
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-66302：依商店ID （而非網站）篩選的願望清單專案

ACSD-66302修補程式修正了[!DNL GraphQL]要求中，依商店ID而非網站來篩選願望清單專案的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-66302。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

依商店ID （而非網站）篩選的願望清單專案不正確。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 建立其他商店評論。
1. 在Admin中，移至&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]**，並將&#x200B;**[!UICONTROL Enable Multiple Wish Lists]**&#x200B;設定為`Yes`。
1. 前往「**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**」，並將&#x200B;**[!UICONTROL Add Store Code to Urls]**&#x200B;設為`Yes`。
1. 建立客戶帳戶。
1. 使用[!DNL GraphQL]要求擷取客戶驗證權杖。
1. 客戶登入。
1. 選取&#x200B;**[!UICONTROL Default Store View]**&#x200B;並將產品新增至願望清單。
1. 將存放區檢視切換至&#x200B;*測試*。
1. 確認產品仍會出現在願望清單中（正確行為）。
1. 執行下列[!DNL GraphQL]查詢：

   ```
   {
     customer {
       wishlists {
         id
         name
         items_count
         items_v2 {
           items {
             id
             product {
               uid
               name
               sku
             }
           }
         }
       }
     }
   }
   ```

1. 在預設存放區上執行查詢 — 產品如預期般顯示。
1. 在測試存放區上執行相同的查詢 — 產品未出現。

<u>預期結果</u>：

透過[!DNL GraphQL]個查詢在相同網站內的所有商店檢視中應該可以看到產品。

<u>實際結果</u>：

切換商店檢視時，產品會從願望清單中消失。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
