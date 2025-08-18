---
title: ACSD-67264：套件組合和可下載的產品頁面配置在各裝置間不一致
description: 套用ACSD-67264修補程式來修正Adobe Commerce套件組合和可下載頁面由於產品資訊媒體區塊重新排列而出現版面問題。
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264：套件組合和可下載的產品頁面配置在各裝置間不一致

ACSD-67264修補程式修正跨裝置的套件組合和可下載產品頁面配置不一致的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-67264。 請注意，此問題已在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於產品資訊媒體區塊重新排列，套裝和可下載產品頁面出現版面問題。

<u>要再現的步驟</u>：

1. 安裝範例資料。
1. 開啟套件組合產品頁面，並檢查案頭上的版面。
1. 將套件產品頁面新增至願望清單、導覽至願望清單、按一下編輯圖示，然後檢查版面。
1. 針對可下載的產品，重複步驟2和3。

<u>預期結果</u>：

隨附產品PDP轉譯且無任何問題。

<u>實際結果</u>：

捆綁產品PDP會以隨機空格轉譯。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]： Tools指南中用於品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具
