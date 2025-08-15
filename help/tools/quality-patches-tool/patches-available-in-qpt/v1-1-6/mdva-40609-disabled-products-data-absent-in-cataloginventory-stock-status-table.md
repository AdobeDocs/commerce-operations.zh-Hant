---
title: MDVA-40609： cataloginventory_stock_status表格中缺少已停用的產品資料
description: MDVA-40609修補程式可解決「cataloginventory_stock_status」索引表中未顯示已停用產品資料，導致顯示錯誤產品數量的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-40609。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: Catalog Management, Inventory, Orders, Products
role: Admin
exl-id: e207ee55-b6ce-4065-bae1-2be89dcf5092
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609： cataloginventory_stock_status表格中缺少已停用的產品資料

MDVA-40609修補程式解決停用產品資料未顯示在`cataloginventory_stock_status`索引表中，導致顯示不正確產品數量的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-40609。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

停用的產品資料未顯示在`cataloginventory_stock_status`索引表中，導致顯示不正確的產品數量。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 設定兩個有商店和商店檢視的網站。
1. 建立其他來源和庫存。
1. 新增簡單產品：
   * 將[啟用產品]設定為&#x200B;*否*。
   * 指定兩個來源，Source料號狀態=安裝及數量大於零。
1. 儲存產品。
1. 檢查&#x200B;**產品可銷售數量**&#x200B;索引標籤。

<u>預期結果</u>：

兩個庫存都輸入了大於零的值。

<u>實際結果</u>：

一種股票具有零值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[中可用的](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)修補程式區段。
