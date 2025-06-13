---
title: MDVA-40120：GraphQL產品DESC/ASC排序無法運作
description: MDVA-40120修補程式解決了GraphQL依DESC/ASC排序時，無法搭配具有相同關聯性或價格的產品運作的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-40120。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: GraphQL, Products
role: Admin
exl-id: 4df7f14d-181b-4f34-aff7-0af823632015
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-40120：GraphQL產品DESC/ASC排序無法運作

MDVA-40120修補程式解決了GraphQL依DESC/ASC排序時，無法搭配具有相同關聯性或價格的產品運作的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-40120。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

建立幾種價格相同的不同產品。

<u>要再現的步驟</u>：

1. 執行下列GraphQL查詢：

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. 檢查回應。
1. 在GraphQL查詢中將排序順序從&#x200B;**ASC**&#x200B;變更為&#x200B;**DESC**：

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. 檢查回應。

<u>預期結果</u>：

GraphQL回應中的產品清單應根據排序順序變更。

<u>實際結果</u>：

排序順序保持不變。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
