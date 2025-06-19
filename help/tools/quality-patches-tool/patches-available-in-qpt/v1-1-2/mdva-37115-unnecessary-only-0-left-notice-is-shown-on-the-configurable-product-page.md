---
title: MDVA-37115：產品頁面上會顯示「只剩下0個」通知
description: MDVA-37115修補程式解決了在可設定產品頁面上顯示不必要的*僅剩下0*通知的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-37115。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: Configuration, Products, Orders
role: Admin
exl-id: ba94b2fd-6a7d-4194-afd8-798854431b57
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-37115：產品頁面上會顯示「只剩下0個」通知

MDVA-37115修補程式解決了在可設定的產品頁面上顯示不必要的&#x200B;*僅剩下0*&#x200B;通知的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-37115。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署型別） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署型別） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

可設定的產品頁面上會顯示不必要的&#x200B;*僅剩下0個*&#x200B;通知。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 使用幾個選項建立可設定的產品。
1. 前往前端。
1. 開啟可設定的產品頁面並選取任何選項。

<u>預期結果</u>：

產品頁面上只顯示0個&#x200B;*通知，沒有*。

<u>實際結果</u>：

*剩餘0個*&#x200B;通知會顯示在產品頁面上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
