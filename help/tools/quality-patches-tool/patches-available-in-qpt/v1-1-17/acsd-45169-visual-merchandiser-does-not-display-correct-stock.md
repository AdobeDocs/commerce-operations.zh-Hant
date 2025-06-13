---
title: ACSD-45169：Visual Merchandiser針對可設定的產品顯示不正確的庫存和價格
description: ACSD-45169修補程式修正了以下問題：套用測試版更新後，Visual Merchandiser無法針對可設定產品顯示正確的庫存和價格。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45169。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
exl-id: 3f1218ee-2fd0-4f3e-80d7-7e6f9342e0fb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-45169：Visual Merchandiser針對可設定的產品顯示不正確的庫存和價格

ACSD-45169修補程式修正了以下問題：套用測試版更新後，Visual Merchandiser無法針對可設定產品顯示正確的庫存和價格。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45169。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用測試更新後， Visual Merchandiser沒有顯示可設定產品的正確庫存和價格。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 為簡單產品建立任何排程的更新（您只需要有不同的列和實體ID）。
1. 建立可設定的產品。
1. 將可設定的產品指派給類別。
1. 開啟類別，並在Visual Merchandiser區段底下觀察可設定的產品。

<u>預期結果</u>：

Visual Merchandiser會顯示正確的庫存和價格。

<u>實際結果</u>：

Visual Merchandiser顯示的庫存和價格不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
