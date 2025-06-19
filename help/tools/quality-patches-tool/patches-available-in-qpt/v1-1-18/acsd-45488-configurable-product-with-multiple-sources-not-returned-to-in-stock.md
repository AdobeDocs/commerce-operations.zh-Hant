---
title: ACSD-45488：具有多個來源的可設定產品未自動退回庫存中
description: ACSD-45488修補程式解決了具有多個來源的可設定產品無法自動退回到庫存中的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18後，即可使用此修補程式。 修補程式ID為ACSD-45488。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: Configuration, Orders, Products, Returns
role: Admin
exl-id: 53f34e8e-00bd-4386-bebf-b15882e36da1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488：具有多個來源的可設定產品未自動退回庫存中

ACSD-45488修補程式解決了具有多個來源的可設定產品無法自動退回到庫存中的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18時，即可使用此修補程式。 修補程式ID為ACSD-45488。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有多個來源的可設定產品不會自動傳回庫存中。

<u>要再現的步驟</u>：

1. 建立次要庫存來源。
1. 使用兩個相關聯的虛擬產品建立可設定的產品。
1. 將關聯產品指定至預設庫存來源，並將數量設為1。
1. 檢查來自`cataloginventory_stock_status`的`stock_status`。
1. 將兩個關聯產品設定為&#x200B;*缺貨*。
1. 檢查來自`cataloginventory_stock_status`的`stock_status`。
1. 將兩個關聯產品設定為&#x200B;*庫存*。
1. 檢查來自`cataloginventory_stock_status`的`stock_status`。

<u>預期結果</u>：

當相關產品設定為庫存時，可設定產品的庫存狀態會更新為&#x200B;*庫存*。

<u>實際結果</u>：

當相關產品設定為庫存時，可設定產品的庫存狀態未更新為&#x200B;*庫存*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
