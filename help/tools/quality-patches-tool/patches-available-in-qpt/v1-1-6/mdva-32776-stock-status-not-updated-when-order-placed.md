---
title: MDVA-32776：庫存狀態未更新訂單位置
description: MDVA-32776修補程式修正了下訂單但未出貨時，庫存狀態未更新的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-32776。 請注意，問題已在Adobe Commerce 2.4.2中修正。
feature: Orders
role: Admin
exl-id: 6f872c72-c96f-4c23-b6df-44e3da3a81c2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776：庫存狀態未更新訂單位置

MDVA-32776修補程式修正了下訂單但未出貨時，庫存狀態未更新的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-32776。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.0

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

下單但未出貨時，存貨狀態不會更新。

<u>必要條件</u>：

1. 已安裝清查模組。
1. 顯示缺貨產品設定為&#x200B;*是*。

   若要設定，請移至&#x200B;**商店** > **組態** > **目錄** > **詳細目錄** > **顯示缺貨的產品** = *是*。

<u>要再現的步驟</u>：

1. 建立兩個數量= 11和22的簡單產品。
1. 使用在步驟一中建立的簡單產品建立群組產品。
1. 將其中一個產品數量設為11，並使另一個簡單產品無庫存，即可將已分組的產品新增至購物車。
1. 完成結帳並下訂單。

<u>預期結果</u>：

相關聯的簡單產品無庫存時，群組產品會顯示`out-of-stock`個標籤。

<u>實際結果</u>：

1. 數量= 11的簡單產品會顯示無庫存。
1. 已分組的產品未針對數量= 11的產品，顯示&#x200B;*無庫存*&#x200B;訊息。 不過，將此產品加入購物車會發生&#x200B;*無庫存*&#x200B;錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)中可用的修補程式區段。
