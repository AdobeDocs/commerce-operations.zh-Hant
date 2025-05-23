---
title: 執行升級
description: 請依照這些步驟升級Adobe Commerce的內部部署。
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# 執行升級

如果您是透過下列方式安裝軟體，則可以從命令列升級Adobe Commerce應用程式的&#x200B;_內部部署_&#x200B;部署：

- 正在使用`composer create-project`命令下載Composer中繼資料。
- 安裝壓縮的封存。

>[!NOTE]
>
>- 如需雲端基礎結構專案上的Adobe Commerce，請參閱雲端指南中的[升級Commerce版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=zh-Hant)。
>- 如果您複製GitHub存放庫，請勿使用此方法來升級。 請參閱[升級Git安裝](../developer/git-installs.md)。

下列指示說明如何使用Composer封裝管理員進行升級。 Adobe Commerce 2.4.2推出對Composer 2的支援。 如果您嘗試從&lt;2.4.1升級，您必須先使用Composer 1 _升級到Composer 2以進行>2.4.2升級之前_，升級到與Composer 2相容的版本（例如，2.4.2）。 此外，您必須執行[支援的PHP版本](../../installation/system-requirements.md)。

>[!WARNING]
>
>升級Adobe Commerce的程式已變更。 您必須安裝新版本的`magento/composer-root-update-plugin`套件（請參閱[必要條件](../prepare/prerequisites.md)）。 此外，用於升級的命令已從`composer require magento/<package_name>`變更為`composer require-commerce magento/<package_name>`。

## 開始之前

您必須先完成[升級必要條件](../prepare/prerequisites.md)，才能開始升級程式前準備環境。

## 管理套件

>[!NOTE]
>
>請參閱本節結尾的範例，以取得指定不同發行層級的說明。 例如，品質修補程式和安全修補程式。 如果您在Composer中找不到這些套件，請聯絡Adobe Commerce支援。

1. 切換到維護模式，以防止在升級過程中存取您的存放區。

   ```bash
   bin/magento maintenance:enable
   ```

   如需其他選項，請參閱[啟用或停用維護模式](../../installation/tutorials/maintenance-mode.md)。 您可以選擇建立[自訂維護模式頁面](../troubleshooting/maintenance-mode-options.md)。

1. 在非同步處理序（例如訊息佇列取用者）執行時啟動升級處理序，可能會導致資料損毀。 若要防止資料損毀，請停用所有cron工作。

   雲端基礎結構上的&#x200B;_Adobe Commerce：_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source：_

   ```bash
   bin/magento cron:remove
   ```

1. 手動啟動所有訊息佇列取用者，以確保所有訊息都已使用。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   等待cron工作完成。 您可以使用程式檢視器或多次執行`ps aux | grep 'bin/magento queue'`命令來監視工作的狀態，直到所有程式完成為止。

1. 建立`composer.json`檔案的備份。

   ```bash
   cp composer.json composer.json.bak
   ```

1. 根據您的需求，新增或移除特定套件。

   例如，如果您要從Magento Open Source升級至Adobe Commerce，請移除Magento Open Source套件。

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   您也可以升級範例資料。

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce：_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source：_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. 使用下列`composer require-commerce`命令語法升級您的執行個體：

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   命令選項包括：

   - `<product>` — （必要）要升級的套件。 對於內部部署安裝，此值必須是`product-community-edition`或`product-enterprise-edition`。

   - `<version>` — （必要）您要升級至的Adobe Commerce版本。 例如，`2.4.3`。

   - `--no-update` — （必要）停用相依性的自動更新。

   - `--interactive-root-conflicts` — （選擇性）可讓您以互動方式檢視及更新任何舊版中的過期值，或與您要升級至之版本不相符的任何自訂值。

   - `--force-root-updates` — （選擇性）以預期的Commerce值覆寫所有衝突的自訂值。

   - `--help` — （選擇性）提供外掛程式的使用方式詳細資料。

   如果未指定`--interactive-root-conflicts`或`--force-root-updates`，則命令會保留衝突的現有值，並顯示警告訊息。 若要進一步瞭解外掛程式，請參閱[外掛程式使用方式README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md)。

1. 更新相依性。

   ```bash
   composer update
   ```

### 範例 — 列出可用版本

若要檢視可用2.4.x版本的完整清單：

_Magento Open Source_：

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_：

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 範例 — 品質修補程式

品質修補程式主要包含功能性&#x200B;_和_&#x200B;安全性修正。 但是，它們有時可以包含向後相容的新功能。 使用Composer下載品質修補程式。

_Adobe Commerce_：

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_：

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### 範例 — 安全性修補程式

安全性修補程式僅包含安全性修正。 這些設定可讓升級程式更快、更輕鬆。 安全性修補程式使用Composer命名慣例`2.4.x-px`。

_Adobe Commerce_：

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_：

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## 更新中繼資料

1. 視需要更新`composer.json`檔案中的`"name"`、`"version"`和`"description"`欄位。

   >[!NOTE]
   >
   >更新`composer.json`檔案中的中繼資料完全是表面性的，無法運作。

1. 套用更新。

   ```bash
   composer update
   ```

1. 清除`var/`和`generated/`子目錄：

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >如果您使用檔案系統以外的快取儲存體，例如Redis或Memcached，您也必須手動清除其中的快取。

1. 更新資料庫結構和資料。

   ```bash
   bin/magento setup:upgrade
   ```

1. 停用維護模式。

   ```bash
   bin/magento maintenance:disable
   ```

1. _（選擇性）_&#x200B;重新啟動清漆。

   如果您使用Varnish來快取頁面，請重新啟動它：

   ```bash
   service varnish restart
   ```

## 檢查您的工作

若要檢查升級是否成功，請在網頁瀏覽器中開啟店面URL。 如果您的升級不成功，您的店面將無法正確載入。

如果應用程式失敗並出現`We're sorry, an error has occurred while generating this email.`錯誤：

1. 將[檔案系統擁有權和許可權重設為具有`root`許可權的使用者](../../installation/prerequisites/file-system/configure-permissions.md)。
1. 清除下列目錄：
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. 再次在網頁瀏覽器中檢視您的店面。
