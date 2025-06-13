---
title: ACSD-59952：刪除與其他共用目錄具有相同群組識別碼的共用目錄時發生錯誤
description: 套用ACSD-59952修補程式以修正Adobe Commerce問題，在刪除與其他共用目錄具有相同之「customer_group_id」的共用目錄時，系統擲回錯誤。
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952：刪除與其他共用目錄具有相同群組識別碼的共用目錄時發生錯誤

ACSD-59952修補程式修正刪除與其他共用目錄具有相同`customer_group_id`的共用目錄時擲回的錯誤。 它會進一步防止使用者建立這類共用目錄。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-59952。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法建立與其他共用目錄具有相同`customer_group_id`的新共用目錄。 但是，嘗試刪除具有相同`customer_group_id`的共用目錄時，會擲回錯誤。

<u>必要條件</u>：

安裝Adobe Commerce B2B模組。

<u>要再現的步驟</u>：

1. 使用下列REST API呼叫，建立指派給相同`customer_group_id`的多個共用目錄：

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. 嘗試使用下列REST API呼叫來刪除任何共用目錄：

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>預期結果</u>：

* 無法建立指派給相同`customer_group_id`的多個共用目錄。
* 上述案例中的共用目錄已成功刪除。

<u>實際結果</u>：

* 可以建立指派給相同`customer_group_id`的多個共用目錄。
* 嘗試刪除具有相同`customer_group_id`的共用目錄時，傳回下列錯誤： *無法刪除共用目錄*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
