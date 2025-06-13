---
title: ACSD-49973：改善透過 [!DNL GraphQL]擷取套件產品的效能
description: 套用ACSD-49973修補程式以修正透過 [!DNL GraphQL]擷取套件產品時發生效能降低的Adobe Commerce問題。
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-49973：改善透過[!DNL GraphQL]擷取套件產品的效能

ACSD-49973修補程式可改善透過[!DNL GraphQL]擷取套件產品的效能。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30時，即可使用此修補程式。 修補程式ID為ACSD-49973。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過[!DNL GraphQL]擷取套件組合產品時，會發生效能降低。

<u>必要條件</u>：

使用[效能工具組](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html)建立2000套件組合產品。

<u>要再現的步驟</u>：

1. 啟用[!DNL DB]查詢記錄器：

   ```
   bin/magento dev:query-log:enable
   ```

1. 執行下列[!DNL GraphQL]查詢：

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. 檢查`var/log/db.log`以取得對`catalog_product_bundle_selection`資料表的要求。

<u>預期結果</u>：

對`catalog_product_bundle_selection`資料表的要求不應出現在`var/log/db.log`中。

<u>實際結果</u>：

同時觸發對`catalog_product_bundle_selection`資料表的2000個要求，導致效能降低。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相關閱讀

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
