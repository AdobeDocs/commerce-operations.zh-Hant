---
title: 「MDVA-40134：啟用共用目錄時，GraphQL未傳回相關產品」
description: MDVA-40134修補程式修正啟用共用目錄時，GraphQL未傳回相關產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-40134。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134：啟用共用目錄時，GraphQL未傳回相關產品

MDVA-40134修補程式修正啟用共用目錄時，GraphQL未傳回相關產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-40134。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

共用目錄啟用時，GraphQL不會傳回相關產品。

<u>必要條件</u>：

必須安裝B2B模組。
僅使用範例資料的執行個體必須是乾淨的。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **組態** > **一般** > **B2B功能**&#x200B;並啟用&#x200B;**公司和共用目錄**。
1. 移至&#x200B;**目錄** > **共用目錄**，並將所有產品新增至&#x200B;**一般目錄**。
1. 使用範例資料並修改Joust Duffle Bag (SKU 24-MB01)。
1. 在「**相關產品**」下方，新增兩個旅行袋（識別碼7和13）。
1. 傳送&#x200B;**Post**&#x200B;要求：

<pre>{
  products(filter： {sku： {eq： "24-MB01"}}， sort： {name： ASC}) {
    專案{
      related_products {
        uid
        名稱
      }
    }
  }
}</pre>

<u>預期結果</u>：

相關產品會顯示在GraphQL回應中。

<u>實際結果</u>：

使用者收到以下錯誤：

<pre>Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor：：getStoreId()的傳回值必須是int型別，null傳回{"exception"："[object] (GraphQL\\Error\\Error(code： 0)：Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor：：getStoreId()的傳回值必須是int型別，傳回null </pre>

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
