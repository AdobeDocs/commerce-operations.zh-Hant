---
title: ACSD-51884：調整大小命令上的產品影像快取路徑不正確
description: 套用ACSD-51884修補程式，修正Adobe Commerce產品影像快取路徑在執行resize命令後會變得不正確的問題。
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-51884：調整大小命令上的產品影像快取路徑不正確

ACSD-51884修補程式修正了執行resize命令後，產品影像快取路徑變得不正確的內部錯誤問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.37時，即可使用此修補程式。 修補程式ID為ACSD-51884。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

調整大小命令上的產品影像快取路徑不正確。

<u>要再現的步驟</u>：

1. 建立新網站/商店/商店。
1. 建立產品並將其指派給兩個網站，然後上傳產品影像。
1. 建立新主題(請參閱附加的Adobe.zip)。
1. 在`app/design/Adobe/theme/etc/view.xml`變更中：

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

至

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. 將主題套用至先前建立的商店評論。
1. 請檢視第2個網站的產品頁面。 產品影像可正確顯示。
1. 使用排清快取：
   `bin/magento cache:flush`
1. 請檢視第2個網站的產品頁面。

<u>預期結果</u>：

產品影像可正確顯示。

<u>實際結果</u>：

產品影像不存在。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
