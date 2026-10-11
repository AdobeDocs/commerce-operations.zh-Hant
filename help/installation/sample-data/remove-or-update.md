---
title: 移除或更新範例資料模組
description: 請依照下列步驟管理Adobe Commerce範例資料模組。
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%
---
# 移除或更新範例資料模組

本主題說明如何：

* [從Adobe Commerce安裝`composer.json`移除範例資料模組](#remove-sample-data-modules)。 這個選項&#x200B;*不會*&#x200B;從資料庫移除範例資料。

* [準備更新範例資料](#prepare-to-update-sample-data) （例如，在更新Magento應用程式之前）。

## 移除範例資料模組

輸入下列命令：

```shell
bin/magento sampledata:remove
```

範例資料模組的完整清單如下：

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

## 準備更新範例資料

此命令可讓您在更新Adobe Commerce之前更新範例資料。

若要準備要更新的範例資料，請輸入以下命令：

```shell
bin/magento sampledata:reset
```

之後，[更新應用程式](../tutorials/uninstall.md#update-the-application)。
