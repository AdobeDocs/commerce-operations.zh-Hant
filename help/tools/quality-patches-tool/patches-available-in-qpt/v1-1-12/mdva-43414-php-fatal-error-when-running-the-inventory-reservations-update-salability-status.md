---
title: MDVA-43414：執行「inventory.reservations.updateSalabilityStatus」時發生PHP嚴重錯誤
description: MDVA-43414修補程式可解決在數值SKU上執行「inventory.reservations.updateSalabilityStatus」佇列使用者時發生的PHP嚴重錯誤。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-43414。 請注意，問題已在Adobe Commerce 2.4.2中修正。
feature: Inventory, Orders
role: Admin
exl-id: 893a5665-ff1b-4862-a984-d9abf642fba3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-43414：執行「inventory.reservations.updateSalabilityStatus」時發生PHP嚴重錯誤

MDVA-43414修補程式可解決在數值SKU上執行`inventory.reservations.updateSalabilityStatus`佇列取用者時所發生的PHP嚴重錯誤。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-43414。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在數值SKU上執行「inventory.reservations.updateSalabilityStatus」佇列使用者時發生PHP嚴重錯誤。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 建立自訂存貨來源，並將其指派給新的存貨存貨。
1. 使用自訂詳細目錄來源建立產品。
1. 請確定產品SKU是整數值。
1. 下訂單。
1. 執行`bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus`命令。

<u>預期結果</u>：

佇列會順利啟動。

<u>實際結果</u>：

發生PHP嚴重錯誤：

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
