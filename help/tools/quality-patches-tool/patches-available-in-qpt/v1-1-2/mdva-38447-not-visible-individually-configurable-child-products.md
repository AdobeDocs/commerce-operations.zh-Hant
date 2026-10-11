---
title: MDVA-38447：GraphQL回應中傳回「無法個別顯示」可設定的子產品，且MySQL查詢緩慢
description: MDVA-38447 Adobe Commerce修補程式修正了GraphQL回應中傳回「無法個別顯示」可設定子產品的問題，以及使用類別篩選器的GraphQL產品查詢緩慢MySQL查詢。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-38447。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# MDVA-38447：GraphQL回應中傳回「無法個別顯示」可設定的子產品，且MySQL查詢緩慢

MDVA-38447 Adobe Commerce修補程式修正了GraphQL回應中傳回「無法個別顯示」可設定子產品的問題，以及使用類別篩選器的GraphQL產品查詢緩慢MySQL查詢。 安裝[品質修補工具(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-38447。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL回應中會傳回「無法個別顯示」可設定的子產品，並使用類別篩選降低GraphQL產品查詢的MySQL查詢速度。

<u>必要條件</u>：

必須安裝B2B模組。

<u>要再現的步驟</u>：

1. 建立可設定的產品，將簡單產品設定為&#x200B;**不個別顯示**。
1. 執行&#x200B;**完整重新索引**。
1. 執行&#x200B;**GraphQL查詢**，例如：

<pre>查詢getFilteredProducts(
  $filter： ProductAttributeFilterInput！
  $sort： ProductAttributeSortInput！
  $search：字串
  $pageSize： Int！
  $currentPage： Int！
) &lbrace;
  products(
    篩選器：$filter
    排序：$sort
    搜尋：$search
    pageSize： $pageSize
    currentPage： $currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_pages
      current_page
      page_size
    &rbrace;
    專案&lbrace;
      名稱
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

變數：

<pre>{"filter"：{"user_group"：{"eq"："}&#x200B;}，"search"："config-100"，"sort"：{}，"pageSize"：200，"currentPage"：1}
</pre>

<u>預期結果</u>：

回應時不會傳回可見度設為「個別不可見」的產品。

<u>實際結果</u>：

回應時會傳回可見度設為「個別不可見」的產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解Adobe Commerce的品質修補程式，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)中可用的修補程式區段。
