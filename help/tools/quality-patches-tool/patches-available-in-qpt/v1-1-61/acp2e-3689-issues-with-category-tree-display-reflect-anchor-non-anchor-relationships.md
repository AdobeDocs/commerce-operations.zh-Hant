---
title: ACP2E-3689：在較深的層級顯示類別樹狀結構並反映錨點/非錨點關係的多個問題
description: 套用ACP2E-3689修補程式來修正Adobe Commerce的問題，在超過深度的四個巢狀結構中顯示類別樹狀結構，並反映錨點/非錨點關係。
feature: Categories, Page Content
role: Admin, Developer
source-git-commit: af8b7b44274b828b3f60f92fd78f9f3d3983abb8
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# ACP2E-3689：在較深的層級顯示類別樹狀結構並反映錨點/非錨點關係的多個問題

>[!NOTE]
>
>此修補程式取代2.4.7及更高版本的[ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md)。

ACP2E-3689修補程式修正了在深度超過四的巢狀結構中顯示類別樹狀結構以及反映錨點/非錨點關係的多個問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACP2E-3689。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

較深入層級(4+)的類別樹狀結構無法正確顯示，且反映的是錨點/非錨點關係。

<u>要再現的步驟</u>：

1. 設定包含4個以上層級之巢狀類別的類別樹狀結構。
1. 展開在Admin中出現在不同位置的類別樹狀結構：
   1. 設定[!UICONTROL Related Products Rule]並根據類別設定條件。
   1. 建立Widget並在[!UICONTROL Layout Updates]中選取[!UICONTROL Anchor categories]。

<u>預期結果</u>：

類別樹狀結構的所有層級都會正確顯示。

<u>實際結果</u>：

只能使用類別樹狀結構的前幾個層級(&lt;4)。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
