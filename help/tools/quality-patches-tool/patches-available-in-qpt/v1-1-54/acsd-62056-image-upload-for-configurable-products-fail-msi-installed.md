---
title: ACSD-62056：如果安裝了MSI，可設定產品的影像上傳會失敗
description: 套用ACSD-62056修補程式以修正安裝MSI後未新增可設定產品影像的Adobe Commerce問題。
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056：如果安裝了MSI，可設定產品的影像上傳會失敗

ACSD-62056修補程式修正安裝MSI後無法新增可設定產品影像的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-62056。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

編輯啟用[!UICONTROL Inventory Management/MSI]的可設定產品時，新增影像的選項無法運作。 這會同時影響[!UICONTROL Apply a single set of images to all SKUs]和[!UICONTROL Apply unique images by attribute to each SKU]選項。

<u>必要條件</u>：

[!UICONTROL Inventory Management/MSI]模組已安裝且已啟用。

<u>要再現的步驟</u>：

1. 建立新的來源。
1. 建立新庫存並指派新來源。
1. 編輯可設定的產品。
1. 按一下&#x200B;**[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**。
1. 選取下列任一項並新增影像。

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>預期結果</u>：

影像已新增。

<u>實際結果</u>：

未新增影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
