---
title: ACSD-64523： REST端點無法驗證必要欄位
description: 套用ACSD-64523修補程式以修正REST端點「[V1/import/csv]」無法驗證必要欄位的問題，這允許建立產品而不提供必要欄位。
feature: REST, Products, Admin Workspace
role: Admin, Developer
exl-id: 21aecd6d-06e4-4f2b-904a-27487ba74968
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-64523： REST端點無法驗證必要欄位

ACSD-64523修補程式修正REST端點[V1/import/csv]無法驗證必要欄位的問題，允許建立不含必要資料的產品。 若要解決此問題，請更新Authorization標頭。安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

REST端點`[V1/import/csv]`無法驗證必要欄位，允許建立產品而不提供這些必要欄位。

<u>要再現的步驟</u>：

1. 執行以下裝載（更新Authorization標頭）：

   ```
   curl --location 'http://<domain>/rest/default/V1/import/json' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: Bearer xxxxx' \
   --data '{
       "source": {
           "locale": "en_AU",
           "entity": "catalog_product",
           "behavior": "append",
           "validation_strategy": "validation-stop-on-errors",
           "allowed_error_count": 0,
           "items": [
               {
                   "sku": "product_sku",
                   "product_online": "no",
                   "attribute_set_code": "Default",
                   "product_type": "configurable",
                   "product_websites": "base",
                   "store_view_code": "default",
                   "name": null,
                   "description": null,
                   "short_description": null,
                   "weight": null,
                   "tax_class_name": null,
                   "visibility": null,
                   "price": null,
                   "url_key": null,
                   "cost": null,
                   "additional_attributes": {
                       "special_price": "",
                       "retail_price": ""
                   },
                   "configurable_variations": []
               }
           ]
       }
   }'
   ```

<u>預期結果</u>：

應用程式應防止儲存不含必填欄位的產品。

<u>實際結果</u>：

已成功儲存產品，但未指定產品名稱（這是必要的屬性）。 因此，我們無法存取後端產品格線，並出現下列錯誤。

`Warning: Undefined array key "name" in /app/code/Magento/Catalog/Ui/Component/Listing/Columns/Thumbnail.php on line 91`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
