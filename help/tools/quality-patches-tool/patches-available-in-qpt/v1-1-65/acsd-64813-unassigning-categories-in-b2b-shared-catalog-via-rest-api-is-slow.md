---
title: ACSD-64813：透過REST API取消指派[!DNL B2B]共用目錄中的類別緩慢
description: 套用ACSD-64813修補程式，修正透過REST API在[!DNL B2B]共用目錄中取消指派類別緩慢的Adobe Commerce問題。
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%
---
# ACSD-64813：透過REST API取消指派[!DNL B2B]共用目錄中的類別緩慢

ACSD-64813修補程式修正了透過REST API在[!DNL B2B]共用目錄中取消指派類別緩慢的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACSD-64813。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過REST API取消指派[!DNL B2B]共用目錄中的類別緩慢。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL B2B]**、**[!UICONTROL Company]**&#x200B;和&#x200B;**[!UICONTROL Shared Catalog]**。
1. 產生30,000種使用中的庫存產品。
1. 建立[自訂共用目錄](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls)並指派所有產品給它。
1. 在預設根類別下建立新類別，並指派一些產品給它。
1. 使用管理權杖以新類別識別碼呼叫REST API端點`rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories`。

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. 確認回應為&#x200B;*true*。
1. 執行`bin/magento cron:run`兩次或執行重新索引。
1. 使用管理權杖以新類別識別碼呼叫REST API端點`rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories`。

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u>預期結果</u>：

操作應在合理的時間內完成（在幾分鐘內）。

<u>實際結果</u>：

執行約需30分鐘或導致逾時錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
