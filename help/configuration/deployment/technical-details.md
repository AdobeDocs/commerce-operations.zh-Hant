---
title: 技術詳細資訊
description: 閱讀有關管道部署、配置類型和建議工作流的技術詳細資訊。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# 技術詳細資訊

本主題討論有關Commerce 2.2及更高版本中管道部署的技術實施詳細資訊。 改進可分為以下幾個方面：

- [配置管理](#configuration-management)
- [管理員中的更改](#changes-in-the-admin)
- [安裝並刪除cron](#install-and-remove-cron)

本主題還討論 [建議的工作流](#recommended-workflow) 為管道部署提供了一些示例，以幫助您瞭解其工作原理。

開始之前，請查看 [開發、構建和生產系統的先決條件](../deployment/prerequisites.md)。

## 配置管理

要使您能夠同步和維護開發和生產系統的配置，請使用以下覆蓋方案。

![如何確定配置變數值](../../assets/configuration/override-flow-diagram.png)

如圖所示，配置值按以下順序使用：

1. 如果環境變數存在，則覆蓋所有其他值。
1. 從共用配置檔案 `env.php` 和 `config.php`。 中的值 `env.php` 覆蓋值 `config.php`。
1. 從儲存在資料庫中的值。
1. 如果這些源中的任何一個中不存在值，則使用預設值或NULL。

### 管理共用配置

共用配置儲存在 `app/etc/config.php`，它應該在原始碼管理中。

在開發中的管理中(或在雲基礎架構上的Adobe Commerce)設定共用配置 _整合_)系統並將配置寫入 `config.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md)。

### 管理特定於系統的配置

系統特定的配置儲存在 `app/etc/env.php`，應 _不_ 在原始碼管理中。

在開發(或Adobe Commerce雲基礎架構整合)系統的管理中設定特定於系統的配置，並將配置寫入 `env.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md)。

此命令還將敏感設定寫入 `env.php`。

### 管理敏感配置

敏感配置也儲存在 `app/etc/env.php`。

可以通過以下任何一種方式管理敏感配置：

- 環境變數
- 將敏感配置保存到 `env.php` 使用 [`magento config:set:sensitive` 命令](../cli/set-configuration-values.md)

### 已在管理員中鎖定配置設定

中的任何配置設定 `config.php` 或 `env.php` 鎖定在管理員中；即，這些設定在管理員中無法更改。
使用 [`magento config:set` 或 `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) 命令更改 `config.php` 或 `env.php` 的子菜單。

## 商務管理員

管理員在生產模式下顯示以下行為：

- 不能在管理中啟用或禁用快取類型
- 開發人員設定不可用(**商店** >設定> **配置** >高級> **開發人員**)，包括：

   - Minify CSS、JavaScript和HTML
   - 合併CSS和JavaScript
   - 伺服器端或客戶端LESS編譯
   - 內聯翻譯
   - 如前所述， `config.php` 或 `env.php` 已鎖定，無法在管理員中編輯。
   - 您只能將管理區域設定更改為已部署主題所使用的語言

      下圖顯示了 **帳戶設定** > **介面區域設定** 僅顯示兩個已部署的區域設定的管理中的清單：

      ![您只能將管理區域設定更改為已部署的區域設定](../../assets/configuration/split-deploy-admin-locale.png)

- 不能使用管理員更改任何作用域的區域設定配置。

   我們建議在切換到生產模式之前進行這些更改。

   您仍然可以使用環境變數或 `config:set` 帶路徑的CLI命令 `general/locale/code`。

## 安裝並刪除cron

在版本2.2中，我們首次通過提供 [`magento cron:install` 命令](../cli/configure-cron-jobs.md)。 此命令將crontab設定為運行該命令的用戶。

此外，還可以使用 `magento cron:remove` 的子菜單。

## 建議的管道部署工作流

下圖顯示了我們建議如何使用管道部署來管理配置。

![建議的管道部署工作流](../../assets/configuration/split-deploy-workflow.png)

### 開發系統

在開發系統上，在管理中更改配置並生成共用配置， `app/etc/config.php` 和系統特定配置， `app/etc/env.php`。 將Commerce代碼和共用配置檢查到原始碼管理中，並將其推送到生成伺服器。

您還應在開發系統上安裝擴展並自定義Commerce代碼。

在您的開發系統上：

1. 在管理中設定配置。

1. 使用 `magento app:config:dump` 命令將配置寫入檔案系統。

   - `app/etc/config.php` 是包含所有設定的共用配置 _除_ 敏感和系統特定的設定。 此檔案應位於原始碼管理中。
   - `app/etc/env.php` 是特定於系統的配置，它包含特定系統（例如，主機名和埠號）所獨有的設定。 此檔案應 _不_ 在原始碼管理中。

1. 將修改的代碼和共用配置添加到原始碼管理。

1. 要在開發過程中刪除生成的php代碼和靜態資產檔案，請運行以下命令：

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

運行清除資產的命令後，Commerce將生成工作檔案。

>[!WARNING]
>
>注意以上方法。 刪除 `.htacces`檔案 `generated` 或 `pub` 資料夾可能導致問題。

### 生成系統

生成系統編譯代碼並生成在Commerce中註冊的主題的靜態視圖檔案。 它不需要連接到Commerce資料庫；只需要商務基礎。

在生成系統上：

1. 從原始碼管理中拉出共用配置檔案。
1. 使用 `magento setup:di:compile` 命令來編譯代碼。
1. 使用 `magento setup:static-content:deploy -f` 命令以更新靜態檔案視圖檔案。
1. 將更新檢查到原始碼管理中。

>[!INFO]
>
>請參閱 [靜態視圖檔案的部署策略](../cli/static-view-file-strategy.md)。

### 生產系統

在生產系統（即即時儲存）上，您可以從原始碼管理中提取生成的資產和代碼更新，並使用命令行或環境變數設定特定於系統的敏感配置設定。

在生產系統上：

1. 啟動維護模式。
1. 從原始碼管理中獲取代碼和配置更新。
1. 如果你使用Adobe Commerce，請停止排隊員。
1. 使用 `magento app:config:import` 命令，以導入生產系統中的配置更改。
1. 如果安裝了更改了資料庫架構的元件，請運行 `magento setup:upgrade --keep-generated` 更新資料庫模式和資料，保留生成的靜態檔案。
1. 要設定系統特定的設定，請使用 `magento config:set` 命令或環境變數。
1. 要設定敏感設定，請使用 `magento config:sensitive:set` 命令或環境變數。
1. 清潔(也稱為 _衝_)快取。
1. 結束維護模式。

## 配置管理命令

我們提供以下命令幫助您管理配置：

- [`magento app:config:dump`](../cli/export-configuration.md) 將管理配置設定寫入 `config.php` 和 `env.php` （敏感設定除外）
- [`magento config:set`](../cli/set-configuration-values.md) 設定生產系統上系統特定設定的值。

   使用可選 `--lock` 選項，鎖定管理中的選項（即，使設定不可編輯）。 如果某個設定已鎖定，請使用 `--lock` 按鈕。

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) 設定生產系統上敏感設定的值。
- [`magento app:config:import`](../cli/import-configuration.md) 要導入配置更改，請 `config.php` 和 `env.php` 生產系統。

## 配置管理示例

本節顯示管理配置的示例，以便您瞭解如何對 `config.php` 和 `env.php`。

### 更改預設區域設定

此部分顯示對 `config.php` 使用Admin更改預設重量單位時(**商店** >設定> **配置** >常規> **常規** > **區域設定選項**)。

在管理員中進行更改後，運行 `bin/magento app:config:dump` 將值寫入 `config.php`。 值將寫入 `general` 陣列 `locale` 代碼段 `config.php` 顯示：

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### 更改多個配置設定

本節將討論進行以下配置更改：

- 添加網站、商店和商店視圖(**商店** >設定> **所有商店**)
- 更改預設電子郵件域(**商店** >設定> **配置** >客戶> **客戶配置**)
- 設定PayPal API用戶名和密碼(**商店** >設定> **配置** >銷售> **付款方法** > **貝帕爾** > **所需的PayPal設定**)

在管理員中進行更改後，運行 `bin/magento app:config:dump` 你的開發系統。 這次，並非所有更改都寫入 `config.php`;事實上，只有網站、商店和商店視圖才會作為以下片段顯示寫入該檔案。

### config.php

`config.php` 包含：

- 對網站、商店和商店視圖的更改。
- 非系統特定的搜索引擎設定
- 非敏感PayPal設定
- 通知您從中省略的敏感設定的注釋 `config.php`

`websites` 陣列：

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` 陣列：

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` 陣列：

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` 陣列：

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

預設電子郵件域系統特定的配置設定將寫入 `app/etc/env.php`。

PayPal設定將寫入兩個檔案，因為 `bin/magento app:config:dump` 命令不寫入敏感設定。 必須使用以下命令在生產系統上設定PayPal設定：

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
