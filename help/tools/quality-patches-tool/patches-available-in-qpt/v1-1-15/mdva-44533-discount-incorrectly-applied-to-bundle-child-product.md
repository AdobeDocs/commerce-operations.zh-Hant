---
title: 'MDVA-44533：折扣未正確套用至套件式子產品'
description: MDVA-44533修補程式修正套用折扣至捆綁子產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-44533。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-44533：折扣未正確套用至套件式子產品

MDVA-44533修補程式修正套用折扣至捆綁子產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-44533。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

折扣套用至捆綁子產品的方式不正確。

<u>要再現的步驟</u>：

1. 建立價格為50美元的簡單產品。
1. 建立隨附產品，並將簡單產品指派為該隨附產品的唯一選項。
1. 建立購物車價格規則，包含：

   * 條件：如果總金額大於130$
   * 動作：套用10$的固定金額折扣

1. 前往店面，將套件組合產品新增至購物車，數量為= 1。
1. 前往購物車並確認搭售產品的總成本為50$，且折扣不適用。
1. 將數量變更為2並更新購物車。 套裝產品的總成本現在應該是100$。

<u>預期結果</u>：

不會套用折扣，因為小計為100\$，在規則條件中小於130\$。

<u>實際結果</u>：

已套用折扣。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。