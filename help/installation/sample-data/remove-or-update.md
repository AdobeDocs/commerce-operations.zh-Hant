---
title: 刪除或更新示例資料模組
description: 按照以下步驟管理Adobe Commerce和Magento Open Source示例資料模組。
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 刪除或更新示例資料模組

本主題討論如何：

* [刪除示例資料模組](#remove-sample-data-modules) Adobe Commerce或Magento Open Source裝置 `composer.json`。 此選項可以 *不* 從資料庫中刪除示例資料。

* [準備更新示例資料](#prepare-to-update-sample-data) (例如，在更新Magento應用程式之前)。

## 刪除示例資料模組

輸入以下命令：

```bash
bin/magento sampledata:remove
```

下面是示例資料模組的完整清單：

Adobe Commerce和Magento Open Source:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

Adobe Commerce:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## 準備更新示例資料

此命令使您能夠在更新Adobe Commerce或Magento Open Source之前更新示例資料。

要準備示例資料以進行更新，請輸入以下命令：

```bash
bin/magento sampledata:reset
```

之後， [更新應用程式](../tutorials/uninstall.md#update-the-application)。
