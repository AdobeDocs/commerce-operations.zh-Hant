---
title: ACSD-48910：指定多個來源的套件產品在發票和出貨後無庫存
description: 套用ACSD-48910修補程式，修正Adobe Commerce問題，即訂單開立商業發票及出貨後，指定給多個來源的套件產品會缺貨，即使訂單仍具有非零數量亦然。
feature: Products, Inventory
role: Admin, Developer
exl-id: c8d86531-2db5-4115-92d5-a8d391c4f75d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-48910：指定多個來源的套件產品在發票和出貨後無庫存

ACSD-48910修補程式修正了即使在訂單仍然具有非零數量時，指定給多個來源的套件產品在開立商業發票及出貨後無存貨的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-48910。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

指派給多個來源的套件式產品在發票和運送後會失去庫存，即使它仍然可用。

<u>要再現的步驟</u>：

1. 建立兩個網站。
1. 建立兩個商店/商店檢視（每個網站一個）。
1. 建立兩個簡單的產品（數量= 10），並將它們同時指派給庫存和網站。
1. 建立套件式產品，並將這些簡單產品加入其中。 將套件產品指派給兩個網站。
1. 前往店面，將套件產品加入購物車。
1. 結帳並下訂單。
1. 從「管理員」，開立商業發票並送出訂單。

<u>預期結果</u>：

由於我們只購買了10個專案中的1個，因此該套件產品會維持庫存狀態。

<u>實際結果</u>：

隨附的產品會將其狀態變更為無庫存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
