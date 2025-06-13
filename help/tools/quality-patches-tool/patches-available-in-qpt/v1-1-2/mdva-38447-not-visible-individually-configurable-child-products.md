---
title: MDVA-38447：GraphQL回應中傳回「無法個別顯示」可設定的子產品，且MySQL查詢緩慢
description: MDVA-38447 Adobe Commerce修補程式修正了GraphQL回應中傳回「無法個別顯示」可設定子產品的問題，以及使用類別篩選器的GraphQL產品查詢緩慢MySQL查詢。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-38447。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-38447：GraphQL回應中傳回「無法個別顯示」可設定的子產品，且MySQL查詢緩慢

MDVA-38447 Adobe Commerce修補程式修正了GraphQL回應中傳回「無法個別顯示」可設定子產品的問題，以及使用類別篩選器的GraphQL產品查詢緩慢MySQL查詢。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-38447。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

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

<pre>{"filter"：{"user_group"：{"eq"："}}，"search"："config-100"，"sort"：{}，"pageSize"：200，"currentPage"：1}
</pre>

<u>預期結果</u>：

回應時不會傳回可見度設為「個別不可見」的產品。

<u>實際結果</u>：

回應時會傳回可見度設為「個別不可見」的產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解Adobe Commerce的品質修補程式，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)中可用的修補程式區段。
