---
title: MDVA-39993：透過API完成的詳細目錄變更未反映在店面上
description: MDVA-39993修補程式可解決透過API完成的詳細目錄變更未反映在店面的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-39993。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993：透過API完成的詳細目錄變更未反映在店面上

MDVA-39993修補程式可解決透過API完成的詳細目錄變更未反映在店面的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-39993。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.3.7-p2和2.4.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過API完成的詳細目錄變更未反映在店面產品頁面上。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 確認佇列已設定為在cron執行的情況下執行，且cron已安裝並執行中。
1. 建立可設定的產品(COC001)，具有兩種顏色（黑色和紅色）以及兩種尺寸（M和L）。
1. 選擇無庫存(COC001-Red-M)。
1. 在店面載入可設定的產品頁面，然後嘗試按一下每個顏色。 當您按一下&#x200B;**紅色**&#x200B;時，應該忽略大小&#x200B;**M**，因為它已無庫存。
1. 使用下列API端點和裝載建立COC001-Red-M庫存量：

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. 從後端檢查此簡單產品，並確認其已更新為有貨。
1. 從前端載入可設定的產品，然後按一下每個顏色。 按一下&#x200B;**Red**&#x200B;時，請注意大小&#x200B;**M**。

<u>預期結果</u>：

COC001-Red-M選項並未刪減，因為我們已透過API將其更新為庫存狀態。

<u>實際結果</u>：

COC001-Red-M選項即使有庫存，仍會被劃掉。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
