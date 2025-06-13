---
title: ACSD-51265：最佳化套件產品的重新索引
description: 套用ACSD-51265修補程式來修正Adobe Commerce問題，即當系統中捆綁的產品過多時，「catalog_product_price」重新索引效能偏低。
feature: Products, Price Indexer
role: Admin
exl-id: 1a173ca7-f99e-42d8-87d7-81a6b33f2d4d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-51265：最佳化套件產品的重新索引

ACSD-51265修補程式修正了系統中捆綁產品過多時，`catalog_product_price`重新索引效能偏低的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-51265。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當系統中有太多捆綁產品時，目錄產品價格重新索引效能會很低。

<u>要再現的步驟</u>：

1. 產生至少包含&#x200B;*10,000*&#x200B;套裝產品的目錄（含動態價格選項）。
1. 執行產品價格重新索引。

<u>預期結果</u>

產品價格重新索引僅需不到15分鐘的時間。

<u>實際結果</u>

產品價格重新索引需要一個多小時。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
