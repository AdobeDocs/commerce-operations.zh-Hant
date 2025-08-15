---
title: ACSD-61805：透過REST API更新延期交貨狀態後，修正店面的庫存問題
description: 套用ACSD-61805修補程式，修正透過REST API更新延期交貨狀態後，店面產品無存貨的Adobe Commerce問題
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61805：透過REST API更新延期交貨狀態後，修正店面的庫存問題

ACSD-61805修補程式修正透過REST API更新延期交貨狀態後，店面產品無存貨的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-61805。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過REST API更新延期交貨狀態後，店面上的產品維持無庫存。

<u>要再現的步驟</u>：

1. 安裝含有範例資料的乾淨執行個體。
1. 建立新的詳細目錄來源。
1. 建立新的存貨存量，並為其指派新的來源。
1. 將新來源指派給產品24-MB01。
1. 將兩個產品來源的&#x200B;**[!UICONTROL Source Item Status]**&#x200B;設定為`In Stock`。
1. 將兩個產品數量的數量(**[!UICONTROL QTY]**)設定為&#x200B;*0*。
1. 儲存產品。
1. 從此端點URL擷取管理權杖： `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. 使用端點更新產品： `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. 執行cron作業兩次（一次用於建立排程，另一次用於執行排程）：

   ```bash
   bin/magento cron:run
   ```

1. 前往前端並檢查產品。

<u>預期結果</u>：

產品應為&#x200B;*庫存*。

<u>實際結果</u>：

產品已缺貨&#x200B;**。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
