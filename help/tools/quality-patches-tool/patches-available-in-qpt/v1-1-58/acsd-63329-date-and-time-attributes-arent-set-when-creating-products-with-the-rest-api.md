---
title: ACSD-63329：使用REST API建立產品時未設定日期和時間屬性
description: 套用ACSD-63329修補程式，修正使用REST API建立產品時，未設定日期和時間欄位預設值的Adobe Commerce問題。
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329：使用REST API建立產品時，未設定日期和時間欄位的預設值

ACSD-63329修補程式修正使用REST API建立新產品時，未設定日期和時間欄位的預設值的問題： `/rest/default/V1/products`。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63329。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用REST API建立產品時，未設定日期和時間欄位的預設值： `/rest/default/V1/products`

<u>要再現的步驟</u>：

1. 建立&#x200B;**[!UICONTROL Product]**&#x200B;屬性，將其預設值設為`12/31/2020`，並將&#x200B;**[!UICONTROL Catalog Input Type for Store Owner]**&#x200B;設為&#x200B;***[!UICONTROL Date]***&#x200B;或&#x200B;***[!UICONTROL Date and Time]***。
1. 建立另一個文字型別屬性，並將預設值設定為&#x200B;***測試值***。
1. 使用`/rest/all/V1/products/`的REST API POST要求建立新產品。

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. 檢查為上述屬性儲存的值。

<u>預期結果</u>：

使用API建立產品時，預設值應該儲存在&#x200B;**[!UICONTROL Date/Datetime]**&#x200B;型別屬性中。

<u>實際結果</u>：

已為&#x200B;**[!UICONTROL Text]**&#x200B;屬性儲存預設值，但不為&#x200B;**[!UICONTROL Date type]**&#x200B;屬性儲存預設值。 **[!UICONTROL Date]**&#x200B;屬性的值是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
