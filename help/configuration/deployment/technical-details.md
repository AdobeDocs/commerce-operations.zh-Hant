---
title: 技術細節
description: 閱讀有關管道部署的技術細節、設定型別和建議的工作流程。
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# 技術細節

本主題說明Commerce 2.2和更新版本中管道部署的技術實作詳細資訊。 改良功能可劃分為下列領域：

- [設定管理](#configuration-management)
- [管理員中的變更](#changes-in-the-admin)
- [安裝和移除cron](#install-and-remove-cron)

此主題也會討論用於管道部署的[建議工作流程](#recommended-workflow)，並提供一些範例來協助您瞭解其運作方式。

開始之前，請先檢閱開發、組建和生產系統的[必要條件](../deployment/prerequisites.md)。

## 設定管理

若要讓您同步化及維護開發及生產系統的組態，請使用下列覆寫配置。

![如何決定組態變數值](../../assets/configuration/override-flow-diagram.png)

如圖所示，組態值使用順序如下：

1. 環境變數（如果存在）會覆寫所有其他值。
1. 從共用組態檔`env.php`和`config.php`。 `env.php`中的值會覆寫`config.php`中的值。
1. 從儲存在資料庫中的值。
1. 如果這些來源中沒有任何值，則會使用預設值或NULL。

### 管理共用設定

共用組態儲存在`app/etc/config.php`中，應該是在原始檔控制中。

在開發中的管理員(或雲端基礎結構&#x200B;_整合_&#x200B;上的Adobe Commerce)系統中設定共用設定，並使用`config.php`命令[`magento app:config:dump`將設定寫入](../cli/export-configuration.md)。

### 管理系統特定設定

系統特定組態儲存在`app/etc/env.php`中，它應該&#x200B;_不_&#x200B;在原始檔控制中。

在您的開發(或雲端基礎結構整合上的Adobe Commerce)系統中，於Admin中設定系統專屬設定，並使用`env.php`命令[`magento app:config:dump`將設定寫入](../cli/export-configuration.md)。

這個命令也會將敏感設定寫入`env.php`。

### 管理敏感設定

敏感設定也儲存在`app/etc/env.php`中。

您可以透過下列任何方式管理敏感設定：

- 環境變數
- 使用`env.php`命令[`magento config:set:sensitive`將敏感設定儲存在生產系統上的](../cli/set-configuration-values.md)中

### 在Admin中鎖定的組態設定

`config.php`或`env.php`中的任何組態設定已在Admin中鎖定；也就是說，這些設定無法在Admin中變更。
使用[`magento config:set`或`magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set)命令變更`config.php`或`env.php`檔案中的設定。

## Commerce管理員

在生產模式中，管理員會顯示下列行為：

- 您無法在「管理員」中啟用或停用快取型別
- 開發人員設定無法使用（**商店** >設定> **設定** >進階> **開發人員**），包括：

   - 簡化CSS、JavaScript和HTML
   - 合併CSS與JavaScript
   - 伺服器端或使用者端LESS編譯
   - 內嵌翻譯
   - 如前所述，`config.php`或`env.php`中的任何組態設定已鎖定，無法在Admin中編輯。
   - 您只能將管理員地區設定變更為已部署主題使用的語言

     下圖顯示管理員中&#x200B;**帳戶設定** > **介面地區設定**&#x200B;清單的範例，其中只顯示兩個已部署的地區設定：

     ![您只能將Admin地區設定變更為已部署的地區設定](../../assets/configuration/split-deploy-admin-locale.png)

- 您無法使用Admin變更任何範圍的地區設定。

  建議您先進行這些變更，然後再切換至生產模式。

  您仍然可以使用環境變數或路徑為`config:set`的`general/locale/code` CLI命令來設定地區設定。

## 安裝和移除cron

在2.2版中，我們首次提供[`magento cron:install`命令](../cli/configure-cron-jobs.md)來協助您設定cron工作。 這個命令會將crontab設定為執行命令的使用者。

您也可以使用`magento cron:remove`命令移除crontab。

## 建議的管道部署工作流程

下圖顯示我們建議您使用管道部署來管理設定的方式。

![建議的管道部署工作流程](../../assets/configuration/split-deploy-workflow.png)

### 開發系統

在您的開發系統上，您在[管理員]中進行組態變更，並產生共用組態`app/etc/config.php`和系統特定組態`app/etc/env.php`。 檢查Commerce程式碼和共用設定至原始檔控制，並將其推送至組建伺服器。

您也應在開發系統上安裝擴充功能並自訂Commerce程式碼。

在您的開發系統上：

1. 在「管理員」中設定設定。

1. 使用`magento app:config:dump`命令將組態寫入檔案系統。

   - `app/etc/config.php`是共用組態，包含所有設定&#x200B;_（除了_&#x200B;個敏感及系統特定設定之外）。 這個檔案應該在原始檔控制中。
   - `app/etc/env.php`是系統專屬的設定，其中包含特定系統專屬的設定（例如主機名稱和連線埠號碼）。 這個檔案應該&#x200B;_不_&#x200B;在原始檔控制中。

1. 將修改後的程式碼和共用設定新增到原始檔控制。

1. 若要在開發期間移除產生的php程式碼和靜態資產檔案，請執行以下命令：

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

執行清除資產的命令後，Commerce會產生工作檔案。

>[!WARNING]
>
>請謹慎使用上述方法。 刪除`.htacces`或`generated`資料夾中的`pub`檔案可能會導致問題。

### 建置系統

組建系統會編譯程式碼，並針對在Commerce中註冊的主題產生靜態檢視檔案。 不需要連線至Commerce資料庫，只需要使用Commerce程式碼基底。

在您的建置系統上：

1. 從原始檔控制提取共用組態檔。
1. 使用`magento setup:di:compile`命令編譯程式碼。
1. 使用`magento setup:static-content:deploy -f`命令更新靜態檔案檢視檔案。
1. 將更新簽入原始檔控制。

>[!INFO]
>
>檢視靜態檢視檔案的[部署策略](../cli/static-view-file-strategy.md)。

### 生產系統

在您的生產系統（即您的即時商店）上，您會從原始檔控制提取產生的資產和程式碼更新，並使用命令列或環境變數設定系統專屬和敏感的組態設定。

在您的生產系統上：

1. 啟動維護模式。
1. 從原始檔控制提取程式碼和設定更新。
1. 如果您使用Adobe Commerce，請停止佇列背景工作。
1. 使用`magento app:config:import`命令將組態變更匯入生產系統。
1. 如果您安裝的元件變更了資料庫結構描述，請執行`magento setup:upgrade --keep-generated`以更新資料庫結構描述和資料，並保留產生的靜態檔案。
1. 若要設定系統特定設定，請使用`magento config:set`命令或環境變數。
1. 若要設定敏感設定，請使用`magento config:sensitive:set`命令或環境變數。
1. 清除（也稱為&#x200B;_排清_）快取。
1. 結束維護模式。

## 組態管理命令

我們提供下列指令來協助您管理組態：

- [`magento app:config:dump`](../cli/export-configuration.md)將管理員組態設定寫入`config.php`和`env.php` （機密設定除外）
- [`magento config:set`](../cli/set-configuration-values.md)以設定生產系統上的系統特定設定值。

  使用選用的`--lock`選項來鎖定Admin中的選項（也就是讓設定無法編輯）。 如果設定已經鎖定，請使用`--lock`選項變更設定。

- [`magento config:sensitive:set`](../cli/set-configuration-values.md)以在生產系統上設定敏感設定值。
- [`magento app:config:import`](../cli/import-configuration.md)將組態變更從`config.php`和`env.php`匯入至生產系統。

## 設定管理範例

本節顯示管理組態的範例，讓您瞭解如何變更`config.php`和`env.php`。

### 變更預設地區設定

此區段顯示當您使用管理員（`config.php`商店&#x200B;**>設定>**&#x200B;組態&#x200B;**>一般>**&#x200B;一般&#x200B;**>**&#x200B;地區設定選項&#x200B;**）變更預設權重單位時對**&#x200B;所做的變更。

在管理員中進行變更後，請執行`bin/magento app:config:dump`將值寫入`config.php`。 值會寫入`general`下的`locale`陣列，因為`config.php`中的下列程式碼片段顯示：

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

### 變更數個組態設定

本節將討論進行下列組態變更：

- 正在新增網站、商店和商店檢視（**商店** >設定> **所有商店**）
- 變更預設電子郵件網域（**商店** >設定> **設定** >客戶> **客戶設定**）
- 設定PayPal API使用者名稱和API密碼（**商店** >設定> **設定** >銷售> **付款方式** > **PayPal** > **必要的PayPal設定**）

在管理員中進行變更後，請在開發系統上執行`bin/magento app:config:dump`。 這次，並非所有變更都會寫入`config.php`；事實上，只有網站、商店和商店檢視會寫入該檔案，如下列程式碼片段所示。

### config.php

`config.php`包含：

- 網站、商店和商店檢視的變更。
- 非系統特定搜尋引擎設定
- 不敏感的PayPal設定
- 通知您從`config.php`省略的敏感設定的註解

`websites`陣列：

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

`groups`陣列：

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

`stores`陣列：

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

`payment`陣列：

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

預設的電子郵件網域系統特定組態設定已寫入`app/etc/env.php`。

PayPal設定不會寫入這兩個檔案，因為`bin/magento app:config:dump`命令不會寫入敏感性設定。 您必須使用下列命令在生產系統上設定PayPal設定：

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
