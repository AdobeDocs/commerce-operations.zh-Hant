---
title: ACSD-66233：由於無回應的產品清單快顯視窗，管理員無法新增產品
description: 套用ACSD-66233修補程式以修正管理員無法將產品新增至類別的Adobe Commerce問題，因為Visual Merchandiser中的[!UICONTROL Add Product]快顯視窗無限期載入。
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
source-git-commit: 165b62a875747a846b15f8f86b036e67704ebc8e
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-66233：由於無回應的產品清單快顯視窗，管理員無法新增產品

ACSD-66233修補程式修正了管理員無法將產品新增至類別的問題，因為視覺化銷售器中的[!UICONTROL Add Product]快顯視窗會無限期載入。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66233。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

視覺化銷售工具中的[!UICONTROL Add Product]快顯視窗無限期載入，導致管理員無法將產品新增至類別的問題。

<u>要再現的步驟</u>：

1. 安裝並啟用清查模組。
1. 建立大量存貨來源（例如700）。
1. 建立多個存貨存貨（例如，12）並將存貨來源指派給它們。
1. 建立一些產品並將其指派給存貨來源。
1. 建立類別。
1. 展開[!UICONTROL Products in Category]區段。
1. 按一下[!UICONTROL Add Product]按鈕。
1. 觀察產品清單的快顯視窗。

<u>預期結果</u>：

產品清單會在合理的時間內載入快顯視窗中。

<u>實際結果</u>：

快顯視窗會無限期載入，且無法顯示產品清單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
