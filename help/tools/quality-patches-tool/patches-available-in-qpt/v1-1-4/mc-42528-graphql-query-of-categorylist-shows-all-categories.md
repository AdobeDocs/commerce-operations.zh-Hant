---
title: 「MC-42528：categoryList的GraphQL查詢顯示所有類別」
description: MC-42528修補程式可解決當特定類別的瀏覽類別設定為「拒絕」時，「categoryList」的GraphQL查詢會傳回指派和未指派類別的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4時，即可使用此修補程式。 修補程式ID為MC-42528。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MC-42528：categoryList的GraphQL查詢顯示所有類別

MC-42528修補程式可解決當特定類別的瀏覽類別設定為「拒絕」時，`categoryList`的GraphQL查詢會同時傳回指派和未指派類別的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4時，即可使用此修補程式。 修補程式ID為MC-42528。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`categoryList`的GraphQL查詢會傳回已指派和未指派的類別。

<u>要再現的步驟</u>：

1. 建立兩個類別：CAT1和CAT2，並為每個類別指派幾個產品。
1. 建立私人共用目錄。
1. 建立公司使用者，並將其指派給建立的共用目錄。
1. 將CAT1指派給自訂目錄，並將類別許可權設定為「允許」瀏覽類別（適用於私人目錄的客戶群組）。
1. 將CAT2的類別許可權設定為「拒絕」瀏覽類別（適用於私人目錄的客戶群組）。
1. 以公司使用者身分執行`categoryList`或`categories` GraphQL查詢。

<u>預期結果</u>：

回應中只會顯示CAT1。

<u>實際結果</u>：

無論類別的瀏覽許可權為何，所有類別都會顯示在回應中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
