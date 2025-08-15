---
title: MDVA-40896：非同步產品中出現「錯誤：TypeError：引數3」錯誤
description: MDVA-40896修補程式修正了傳遞至MagentoFrameworkWebapiServiceInputProcessor：：process()的「錯誤：型別錯誤：引數3」必須是型別陣列且字串已指定」錯誤會顯示在非同步產品大量API中的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-40896。 請注意，問題已在Adobe Commerce 2.4.4中修正。
feature: Products
role: Admin
exl-id: 24eedd8d-4ae1-4ebc-a3e4-993f0c361a67
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# MDVA-40896：非同步產品中出現「錯誤：TypeError：引數3」錯誤

MDVA-40896修補程式修正非同步產品批次API中顯示`Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given`錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-40896。 請注意，問題已在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

非同步產品大量API中顯示`Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given`錯誤。

<u>要再現的步驟</u>：

1. 使用下列裝載將要求傳送至`rest/all/async/bulk/V1/products/bySKU`端點：

```RESTAPI
[
  {
    "product": {
      "sku": "24-MB01",
      "price": 36,
      "extension_attributes": {
        "stock_item": {
          "qty": 100,
          "is_in_stock": true
        }
      },
      "custom_attributes": [
        {
          "attribute_code": "new",
          "value": "1"
        }
      ]
    }
  },
  {
    "product": {
      "sku": "24-MB04",
      "price": 28,
      "extension_attributes": {
        "stock_item": {
          "qty": 50,
          "is_in_stock": true
        }
      },
      "custom_attributes": [
        {
          "attribute_code": "new",
          "value": "0"
        }
      ]
    }
  }
]
```

<u>預期結果</u>：

系統會傳回產品詳細資料。

<u>實際結果</u>：

發生錯誤`Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given`。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
