---
title: MDVA-31763：目錄價格規則會還原，直到手動重新編列索引為止
description: MDVA-31763修補程式可解決在手動重新索引之前目錄價格規則會還原的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-31763。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763：目錄價格規則會還原，直到手動重新編列索引為止

MDVA-31763修補程式可解決在手動重新索引之前目錄價格規則會還原的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-31763。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在可設定的產品上執行`catalogrule_product`部分索引器時，目錄規則會消失。

<u>要再現的步驟</u>：

1. 登入管理員後端。
1. 移至&#x200B;**商店** > **屬性** > **產品**&#x200B;並搜尋「製造商」屬性。
   * 新增幾個選項，並將[用於促銷規則條件]設定為&#x200B;*是*。
1. 移至&#x200B;**存放區** > **屬性** > **屬性集**。
   * 選取預設屬性集，並將「manufacturer」屬性加入其中。
1. 建立具有一些變數的可設定產品。
1. 設定先前建立之可設定產品的「製造商」屬性值。
1. 建立目錄規則：
   * 使用中=是
   * 網站=主要網站
   * 客戶群組=未登入
   * 條件：製造商= \&lt;可設定產品的選取值>
   * 動作：任何折扣
1. 執行完整索引。
1. 檢查PDP上的產品價格，並確定價格正確。
1. 更新已建立之可設定產品的「權重」屬性。
1. 檢查PDP上的產品價格。

<u>預期結果</u>：

在可設定產品上設定的目錄價格規則在部分重新索引期間不會移除。

<u>實際結果</u>：

在部分重新索引期間，針對可設定產品設定的目錄價格規則會消失。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
