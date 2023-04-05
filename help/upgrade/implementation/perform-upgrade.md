---
title: 執行升級
description: 請依照下列步驟，升級Adobe Commerce或Magento Open Source專案。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# 執行升級

如果您是透過以下方式安裝軟體，可從命令列升級Adobe Commerce或Magento Open Source應用程式：

- 使用 `composer create-project` 命令。
- 安裝壓縮的封存。

>[!NOTE]
>
>如果您複製了GitHub存放庫，請勿使用此方法進行升級。 請改為參閱 [升級Git安裝](../developer/git-installs.md) 以取得升級指示。

下列指示顯示如何使用撰寫器進行升級。 Adobe Commerce 2.4.2推出對撰寫器2的支援。 如果您嘗試從&lt;2.4.1升級，必須先使用撰寫器1升級至與撰寫器2相容的版本（例如2.4.2） _befor_ 升級至Composer 2，以升級至>2.4.2。 此外，您必須執行 [支援的版本](../../installation/system-requirements.md) PHP的。

>[!WARNING]
>
>升級Adobe Commerce和Magento Open Source的程式已變更。 您必須安裝新版本的 `magento/composer-root-update-plugin` 套件(請參閱 [必要條件](../prepare/prerequisites.md))。 此外，升級命令已從 `composer require magento/<package_name>` to `composer require-commerce magento/<package_name>`.

## 開始之前

您必須完成 [升級必要條件](../prepare/prerequisites.md) 先準備環境，再開始升級程式。

## 管理套件

>[!NOTE]
>
>請參閱本節結尾的範例，以取得指定不同版本層級的說明。 例如，次要版本、品質修補程式和安全性修補程式。 Adobe Commerce客戶可在正式發行(GA)日期前兩週存取修補程式。 搶鮮版套件僅可透過撰寫器使用。 在正式發行前，您無法在下載入口網站或GitHub上找到這些檔案。 如果您在撰寫器中找不到這些套件，請聯絡Adobe Commerce支援。

1. 切換到維護模式，以防止在升級過程中訪問您的儲存。

   ```bash
   bin/magento maintenance:enable
   ```

   請參閱 [啟用或禁用維護模式](../../installation/tutorials/maintenance-mode.md) 的其他選項。 您可以視需要選擇建立 [「自定義維護模式」頁](../troubleshooting/maintenance-mode-options.md).

1. 在非同步進程（如消息隊列消費者）正在運行時啟動升級進程可能會導致資料損壞。 若要防止資料損毀，請停用所有cron作業。

   _Adobe Commerce雲基礎架構：_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. 手動啟動所有消息隊列使用者，以確保已使用所有消息。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   等待cron作業完成。 您可以使用進程查看器或運行 `ps aux | grep 'bin/magento queue'` 命令多次，直到所有進程完成。

1. 建立備份 `composer.json` 檔案。

   ```bash
   cp composer.json composer.json.bak
   ```

1. 根據您的需求新增或移除特定套件。

   例如，如果您要從Magento Open Source升級至Adobe Commerce，請移除Magento Open Source套件。

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   您也可以升級範例資料。

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
      ```

   - _Magento Open Source:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
      ```

1. 使用下列程式升級您的執行個體 `composer require-commerce` 命令語法：

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   命令選項包括：

   - `<product>`  — （必要）要升級的包。 對於本地安裝，此值必須是 `product-community-edition` 或 `product-enterprise-edition`.

   - `<version>`  — （必要）您要升級至的Adobe Commerce或Magento Open Source版本。 例如， `2.4.3`.

   - `--no-update`  — （必要）禁用依賴項的自動更新。

   - `--interactive-root-conflicts`  — （可選）允許您交互查看和更新以前版本中的任何過期值，或任何與要升級的版本不匹配的自定義值。

   - `--force-root-updates`  — （可選）用預期的Magento值覆蓋所有衝突的自定義值。

   - `--help`  — （可選）提供外掛程式的使用情況詳細資訊。
   若兩者皆非 `--interactive-root-conflicts` no `--force-root-updates` 指定時，該命令將保留衝突中的現有值並顯示警告消息。 若要進一步了解外掛程式，請參閱 [外掛程式使用情況自述檔案](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. 更新相依性。

   ```bash
   composer update
   ```

### 範例 — 列出可用版本

若要查看可用2.4.x版的完整清單：

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 範例 — 次要版本

次要版本包含新功能、品質修正和安全性修正。 使用撰寫器來指定次要版本。 例如，要指定Magento Open Source2.4.3元包：

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### 範例 — 品質修補程式

質量補丁主要包含功能 _和_ 安全性修正。 不過，有時候它們會包含新的回溯相容功能。 使用撰寫器來下載品質修補程式。 例如，要指定Magento Open Source2.4.1元包：

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### 示例 — 安全補丁

安全修補程式僅包含安全修正。 它們旨在讓升級流程更快更輕鬆。

安全修補程式使用撰寫器命名慣例 `2.4.x-px`. 使用撰寫器來指定修補程式。

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## 更新中繼資料

1. 更新 `"name"`, `"version"`，和 `"description"` 欄位 `composer.json` 檔案。

   >[!NOTE]
   >
   >更新中繼資料 `composer.json` 檔案完全是淺表型的，無法運作。

1. 套用更新。

   ```bash
   composer update
   ```

1. 清除 `var/` 和 `generated/` 子目錄：

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
   >如果使用檔案系統以外的快取儲存，如Redis或Memcached，則還必須手動清除該處的快取。

1. 更新資料庫架構和資料。

   ```bash
   bin/magento setup:upgrade
   ```

1. 禁用維護模式。

   ```bash
   bin/magento maintenance:disable
   ```

1. _（可選）_ 重新啟動清漆。

   如果您使用清漆來快取頁面，請重新啟動：

   ```bash
   service varnish restart
   ```

## 檢查您的工作

在網頁瀏覽器中開啟您的店面URL，以檢查升級是否成功。 如果升級失敗，您的店面將無法正確載入。

如果應用程式因  `We're sorry, an error has occurred while generating this email.` 錯誤：

1. 重設 [檔案系統所有權和權限](../../installation/prerequisites/file-system/configure-permissions.md) 使用 `root` 權限。
1. 清除下列目錄：
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. 再次在網頁瀏覽器中檢查您的店面。
