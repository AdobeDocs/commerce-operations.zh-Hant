---
title: MDVA-42520：使用「啟用跨境貿易」時套用兩次的稅率
description: MDVA-42520修補程式修正了使用**啟用跨境貿易**時套用稅率兩次的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11後，即可使用此修補程式。 修補程式ID為MDVA-42520。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-42520：使用「啟用跨境貿易」時套用兩次的稅率

MDVA-42520修補程式修正了使用&#x200B;**啟用跨境貿易**&#x200B;時套用稅率兩次的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11時，即可使用此修補程式。 修補程式ID為MDVA-42520。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用&#x200B;**啟用跨境貿易**&#x200B;時，會套用兩次稅率。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**公司**、**共用目錄**&#x200B;和&#x200B;**報價**
1. 根據熒幕擷圖設定稅捐。 請確定您已啟用&#x200B;**跨境貿易**。

   ![顯示跨境交易選項與稅率計算的稅務組態設定頁面](/help/assets/tools/tax_settings_1.png){width="700"}

1. 建立德國的稅率(10%)。
1. 建立稅捐規則以套用稅率。
1. 建立公司和自訂共用目錄。
1. 建立價格為100的產品，並將其包含在自訂共用目錄中，且提供20%的價格折扣。
1. 使用德國地址建立客戶，並將其指派給公司
1. 新增10項產品作為客戶至資訊卡。
1. 前往購物車要求報價。
1. 在後端開啟此報價單，並嘗試新增額外10%的折扣。

<u>預期結果</u>：

報價小計（含稅）與報價總計（含稅） = $720

<u>實際結果</u>：

報價小計（含稅）與報價總計（含稅） = $649.50。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
