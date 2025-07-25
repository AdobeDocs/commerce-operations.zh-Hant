---
title: ACSD-66041：由於缺少CountryID，無法搜尋取車地點的愛爾蘭(IE)郵遞區號
description: 套用ACSD-66041修補程式，修正Adobe Commerce發生的問題，亦即愛爾蘭(IE)郵遞區號因缺少CountryID而無法搜尋取車地點。
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1f69d00e0ad0caf15643d0c218e1a2c264d3ad4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# ACSD-66041：由於遺失`CountryID`，無法搜尋取車地點的愛爾蘭(IE)郵遞區號

ACSD-66041修補程式修正了愛爾蘭(IE)郵遞區號因遺失`CountryID`而無法搜尋取車地點的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACSD-66041。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於遺失`CountryID`，無法搜尋取車地點的愛爾蘭(IE)郵遞區號。

<u>要再現的步驟</u>：

1. 執行下列GraphQL查詢：

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. 使用下列變數：

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u>預期結果</u>：

愛爾蘭郵遞區號可供搜尋取車地點。

<u>實際結果</u>：

* 傳回&#x200B;*內部伺服器錯誤*。
* `var/log/exception.log`包含下列錯誤：

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
