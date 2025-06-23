---
title: ACSD-64813：透過REST API取消指派 [!DNL B2B] 共用目錄中的類別緩慢
description: 套用ACSD-64813修補程式，修正透過REST API在 [!DNL B2B] 共用目錄中取消指派類別緩慢的Adobe Commerce問題。
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0ed4bde6d78429da5a375a8c50f6b348db5a5ad5
workflow-type: tm+mt
source-wordcount: '368'
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
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過REST API取消指派[!DNL B2B]共用目錄中的類別緩慢。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL B2B]**、**[!UICONTROL Company]**&#x200B;和&#x200B;**[!UICONTROL Shared Catalog]**。
1. 產生30,000種使用中的庫存產品。
1. 建立[自訂共用目錄](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls)並指派所有產品給它。
1. 在預設根類別下建立新類別，並指派一些產品給它。
1. 使用管理權杖以新類別識別碼呼叫REST API端點`rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories`。

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

1. 確認回應為&#x200B;*true*。
1. 執行`bin/magento cron:run`兩次或執行重新索引。
1. 使用管理權杖以新類別識別碼呼叫REST API端點`rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories`。

```
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
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
