---
title: 「MDVA-39482：如果以'0'數量匯入並啟用延期交貨，則產品無庫存」
description: MDVA-39482修正啟用MSI和延期交貨且缺貨臨界值設定為負值時，以「0」數量匯入產品缺貨的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-39482。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482：如果以「0」數量匯入並啟用延期交貨，則產品無庫存

MDVA-39482修正啟用MSI和延期交貨且缺貨臨界值設定為負值時，以「0」數量匯入產品缺貨的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-39482。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用MSI和延期交貨且缺貨臨界值設定為負值時，如果以「0」數量匯入產品，則產品缺貨。

<u>必要條件</u>：

1. 必須安裝MSI和範例資料。
1. 移至&#x200B;**商店** > **組態** > **目錄** > **詳細目錄**：
   * 將延期交貨設為「允許數量低於0」
   * 將無庫存臨界值設為「–10」

<u>要再現的步驟</u>：

1. 確定SKU為&#x200B;**庫存**，且數量為&#x200B;**24-MB01**。
1. 匯入「庫存來源」的CSV。 請務必在「實體型別」中選取「庫存來源」：

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. 在匯入庫存來源後，檢查產品的庫存狀態。

<u>預期結果</u>：

24-MB01在店面有&#x200B;**庫存**。

<u>實際結果</u>：

24-MB01在店面有&#x200B;**無庫存**。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的[修補程式區段。
