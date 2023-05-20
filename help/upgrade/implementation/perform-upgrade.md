---
title: 執行升級
description: 按照以下步驟升級Adobe Commerce或Magento Open Source項目。
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# 執行升級

如果通過以下方式安裝了軟體，則可以從命令行升級您的Adobe Commerce或Magento Open Source應用程式：

- 使用 `composer create-project` 的子菜單。
- 正在安裝壓縮存檔。

>[!NOTE]
>
>如果克隆了GitHub儲存庫，請不要使用此方法進行升級。 相反，請參閱 [升級基於Git的安裝](../developer/git-installs.md) 以獲取升級說明。

以下說明說明如何使用Composer進行升級。 Adobe Commerce2.4.2對作曲家二號進行了支援。 如果嘗試從&lt;2.4.1升級，則必須首先使用Composer 1升級到與Composer 2相容的版本(例如2.4.2) _先_ 升級到Composer 2以進行>2.4.2升級。 此外，您必須運行 [支援的版本](../../installation/system-requirements.md) PHP。

>[!WARNING]
>
>升級Adobe Commerce和Magento Open Source的程式已經改變。 必須安裝 `magento/composer-root-update-plugin` 包（請參見） [先決條件](../prepare/prerequisites.md))。 此外，升級命令已從 `composer require magento/<package_name>` 至 `composer require-commerce magento/<package_name>`。

## 開始之前

必須完成 [升級先決條件](../prepare/prerequisites.md) 在啟動升級過程之前準備環境。

## 管理包

>[!NOTE]
>
>有關指定不同版本級別的幫助，請參閱本節末尾的示例。 例如，次要版本、質量補丁和安全補丁。 Adobe Commerce客戶可在正式上市(GA)日期前兩週訪問修補程式。 預發行包僅通過Composer提供。 在正式啟動之前，您無法在下載門戶或GitHub上找到它們。 如果在Composer中找不到這些包，請與Adobe Commerce支援部門聯繫。

1. 切換到維護模式，以防止在升級過程中訪問您的儲存。

   ```bash
   bin/magento maintenance:enable
   ```

   請參閱 [啟用或禁用維護模式](../../installation/tutorials/maintenance-mode.md) 的雙曲餘切值。 （可選）您可以建立 [自定義維護模式頁](../troubleshooting/maintenance-mode-options.md)。

1. 在非同步進程（如消息隊列使用者）正在運行時啟動升級進程可能會導致資料損壞。 要防止資料損壞，請禁用所有cron作業。

   _Adobe Commerce在雲基礎架構方面：_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. 手動啟動所有消息隊列使用者，以確保所有消息都被使用。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   等待cron作業完成。 您可以使用進程查看器或運行 `ps aux | grep 'bin/magento queue'` 命令多次執行，直到所有進程完成。

1. 建立 `composer.json` 的子菜單。

   ```bash
   cp composer.json composer.json.bak
   ```

1. 根據您的需要添加或刪除特定包。

   例如，如果要從Magento Open Source升級到Adobe Commerce，請刪除Magento Open Source包。

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   您還可以升級示例資料。

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

1. 使用以下命令升級實例 `composer require-commerce` 命令語法：

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   命令選項包括：

   - `<product>`  — （必需）要升級的包。 對於內部部署安裝，此值必須為 `product-community-edition` 或 `product-enterprise-edition`。

   - `<version>`  — （必需）要升級到的Adobe Commerce或Magento Open Source的版本。 比如說， `2.4.3`。

   - `--no-update`  — （必需）禁用依賴項的自動更新。

   - `--interactive-root-conflicts`  — （可選）允許您交互查看和更新以前版本中的任何過期值，或與要升級到的版本不匹配的任何自定義值。

   - `--force-root-updates`  — （可選）用預期的Magento值覆蓋所有衝突的自定義值。

   - `--help`  — （可選）提供有關插件的使用情況詳細資訊。
   如果兩者都不 `--interactive-root-conflicts` 無 `--force-root-updates` 命令將保留衝突的現有值，並顯示警告消息。 要瞭解有關插件的詳細資訊，請參閱 [插件用法自述檔案](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md)。

1. 更新依賴項。

   ```bash
   composer update
   ```

### 示例 — 列出可用版本

要查看可用2.4.x版本的完整清單，請執行以下操作：

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 示例 — 次要版本

次要版本包含新功能、質量修復和安全修復。 使用Composer指定次要版本。 例如，要指定Magento Open Source2.4.3元包：

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### 示例 — 質量補丁

質量修補程式主要包含功能 _和_ 安全修復。 但是，它們有時可能包含新的、向後相容的功能。 使用Composer下載質量修補程式。 例如，要指定Magento Open Source2.4.1元包：

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

### 示例 — 安全修補程式

安全修補程式僅包含安全修復。 它們旨在使升級過程更快、更輕鬆。

安全修補程式使用Composer命名約定 `2.4.x-px`。 使用Composer指定修補程式。

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## 更新元資料

1. 更新 `"name"`。 `"version"`, `"description"` 的 `composer.json` 檔案。

   >[!NOTE]
   >
   >更新中的元資料 `composer.json` 檔案完全膚淺，不起作用。

1. 應用更新。

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
   >如果使用檔案系統以外的快取儲存，如Redis或Memcached，則還必須手動清除那裡的快取。

1. 更新資料庫架構和資料。

   ```bash
   bin/magento setup:upgrade
   ```

1. 禁用維護模式。

   ```bash
   bin/magento maintenance:disable
   ```

1. _（可選）_ 重新啟動清漆。

   如果將清漆用於頁面快取，請重新啟動它：

   ```bash
   service varnish restart
   ```

## 檢查您的工作

在Web瀏覽器中開啟您的店面URL以檢查升級是否成功。 如果升級失敗，則無法正確載入店面。

如果應用程式失敗，  `We're sorry, an error has occurred while generating this email.` 錯誤：

1. 重置 [檔案系統所有權和權限](../../installation/prerequisites/file-system/configure-permissions.md) 用戶 `root` 權限。
1. 清除以下目錄：
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. 再次在Web瀏覽器中檢查您的店面。
