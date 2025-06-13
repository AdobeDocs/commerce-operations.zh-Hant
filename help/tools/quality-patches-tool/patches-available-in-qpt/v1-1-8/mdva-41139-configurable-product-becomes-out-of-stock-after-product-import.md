---
title: MDVA-41139：可設定的產品在產品匯入後無庫存
description: MDVA-41139修補程式修正了簡單產品其中一個來源的數量= 0時，可設定產品在產品匯入後無存貨的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-41139。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
exl-id: 7366230c-3b7f-4211-9f0d-55a528dffdbd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41139：可設定的產品在產品匯入後無庫存

MDVA-41139修補程式修正了簡單產品其中一個來源的數量= 0時，可設定產品在產品匯入後無存貨的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-41139。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當簡單產品的其中一個來源數量= 0時，產品匯入後可設定產品會變成無庫存。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 建立新的來源和庫存。
1. 建立可設定的產品，將子項產品指派給預設來源及新來源。
1. 設定每個子項產品的預設庫存值= 0，而其他庫存值> 0。
1. 可設定的產品有庫存。
1. 匯出此產品並再次匯入。

<u>預期結果</u>：

可設定產品有庫存，因為第二個來源的數量大於0。

<u>實際結果</u>：

可設定的產品沒有庫存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
