---
title: 覆蓋配置設定
description: 瞭解如何使用環境變數覆蓋配置設定。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---


# 覆蓋配置設定

本主題討論如何導出知道配置路徑的環境變數名稱。 可以使用環境變數覆蓋Adobe Commerce配置設定。 例如，您可以覆蓋生產系統上付款處理者的即時URL的值。

可以覆蓋 _任何_ 使用環境變數進行配置設定；但是，Adobe建議您使用共用配置檔案維護一致的設定， `config.php`，以及系統特定的配置檔案， `env.php`，如 [部署一般概述](../deployment/overview.md)。

>[!TIP]
>
>查看 [配置環境](https://devdocs.magento.com/cloud/env/variables-intro.html) 主題 _Commerce Cloud指南_ 有關在雲基礎架構上使用Adobe Commerce變數的詳細資訊。

## 環境變數

環境變數名稱由其範圍和其特定格式的配置路徑組成。 以下各節將更詳細地討論如何確定變數名稱。

可將變數用於以下任一項：

- [敏感值](config-reference-sens.md) 必須使用環境變數或 [`magento config:sensitive:set`](../cli/set-configuration-values.md) 的子菜單。
- 系統特定的值必須使用：

   - 環境變數
   - 的 [`magento config:set`](../cli/set-configuration-values.md) 命令
   - 管理員後跟 [`magento app:config:dump` 命令](../cli/export-configuration.md)

配置路徑可在以下位置找到：

- [敏感和特定於系統的配置路徑參考](config-reference-sens.md)
- [付款配置路徑引用](config-reference-payment.md)
- [Commerce B2B擴展配置路徑參考](config-reference-b2b.md)
- [其他配置路徑引用](config-reference-general.md)

### 變數名稱

系統設定變數名稱的一般格式如下：

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 可以選擇：

- 全局範圍(即 _全部_ 範圍)

   全局作用域變數具有以下格式：

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 特定範圍（即，該設定僅影響指定的商店視圖或網站）

   例如，儲存視圖範圍變數具有以下格式：

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   有關作用域的詳細資訊，請參見：

   - [步驟1:查找網站或商店視圖範圍值](#step-1-find-the-website-or-store-view-scope-value)
   - [Commerce User Guide（Commerce使用手冊）主題](https://docs.magento.com/user-guide/configuration/scope.html)
   - [範圍快速參考](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` 是用雙下划線字元替換的配置路徑 `/`。 有關詳細資訊，請參見 [步驟2:設定系統變數](#step-2-set-global-website-or-store-view-variables)。

### 變數格式

`<SCOPE>` 與 `<SYSTEM__VARIABLE__NAME>` 下划線字元。

`<SYSTEM__VARIABLE__NAME>` 從配置設定派生 _配置路徑_，這是 `/` 唯一標識特定設定的分隔字串。 替換每個 `/` 配置路徑中的字元，包含兩個下划線字元以建立系統變數。

如果配置路徑包含下划線字元，則下划線字元仍保留在變數中。

配置路徑的完整清單可在以下位置找到：

- [敏感和特定於系統的配置路徑參考](config-reference-sens.md)
- [付款配置路徑引用](config-reference-payment.md)
- [Commerce Enterprise B2B擴展配置路徑參考](config-reference-b2b.md)
- [其他配置路徑引用](config-reference-general.md)

## 步驟1:查找網站或商店視圖範圍值

本節討論如何查找和設定每個系統配置值 _範圍_ （商店視圖或網站）。 要設定全局範圍變數，請參見 [步驟2:設定全局、網站或儲存視圖變數](#step-2-set-global-website-or-store-view-variables)。

範圍值來自 `store`。 `store_group`, `store_website` 的下界。

- 的 `store` 表指定儲存視圖名稱和代碼
- 的 `store_website` 表指定網站名稱和代碼

您還可以使用管理員查找代碼值。

如何讀取表：

- `Path in Admin` 列

   逗號前的值是管理導航中的路徑。 逗號後的值是右窗格中的選項。

- `Variable name` column是相應環境變數的名稱。

   如果需要，可以選擇將這些配置參數的系統值指定為環境變數。

   - 整個變數名稱始終為ALL CAPS
   - 使用 `CONFIG__` （注意兩個下划線字元）
   - 您可以找到 `<STORE_VIEW_CODE>` 或 `<WEBSITE_CODE>` Admin或Commerce資料庫中變數名稱的一部分，如以下各節所示。
   - 您可以找到 `<SYSTEM__VARIABLE__NAME>` 如所討論 [步驟2:設定全局、網站或儲存視圖變數](#step-2-set-global-website-or-store-view-variables)。

### 在管理員中查找網站或商店視圖範圍

下表概述了如何在管理中查找網站或儲存視圖值。

| 說明 | 管理中的路徑 | 變數名稱 |
|--------------|--------------|----------------------|
| 建立、編輯、刪除儲存視圖 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| 建立、編輯、刪除網站 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

例如，要在「管理：

1. 以有權查看網站的用戶身份登錄到管理員。
1. 按一下 **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**。
1. 按一下網站或商店視圖的名稱。

   右窗格的顯示方式與下面類似。

   ![查找網站代碼](../../assets/configuration/website-code.png)

1. 範圍名稱顯示在 **[!UICONTROL Code]** 的子菜單。
1. 繼續 [步驟2:設定全局、網站或儲存視圖變數](#step-2-set-global-website-or-store-view-variables)。

### 在資料庫中查找網站或儲存視圖範圍

要從資料庫中獲取這些值，請執行以下操作：

1. 以 [檔案系統所有者](https://glossary.magento.com/magento-file-system-owner) 如果你還沒做。
1. 輸入以下命令：

   ```bash
   mysql -u <database-username> -p
   ```

1. 在 `mysql>` 提示，按所示順序輸入以下命令：

   ```shell
   use <database-name>;
   ```

1. 使用以下SQL查詢查找相關值：

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   示例如下：

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. 使用 `code` 列，而不是 `name` 值。

   例如，要為Test網站設定配置變數，請使用以下格式：

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   何處 `<SYSTEM__VARIABLE__NAME>` 來自下一節。

## 步驟2:設定全局、網站或儲存視圖變數

本節討論如何設定系統變數。

- 要為全局範圍（即所有網站、商店和商店視圖）設定值，請使用 `CONFIG__DEFAULT__`。

- 要為特定商店視圖或網站設定值，請按中所述啟動變數名稱 [步驟1:查找範圍值](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 變數名稱的最後一部分是配置路徑，該路徑對於每個配置設定都是唯一的。

[查看一些示例](#examples)。

下表顯示了幾個示例變數。

| 說明 | 管理中的路徑（省略） **商店** > **設定** > **配置**) | 變數名稱 |
|--------------|--------------|----------------------|
| Elasticsearch伺服器主機名 | 目錄> **目錄**。 **Elasticsearch伺服器主機名** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch伺服器埠 | 目錄> **目錄**。 **Elasticsearch伺服器埠** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 裝運國原產地 | 銷售> **裝運設定** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| 自定義管理URL | 高級> **管理** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| 自定義管理路徑 | 高級> **管理** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 示例

本節說明如何查找某些示例變數的值。

### Elasticsearch伺服器主機名

要查找全局HTML小型化的變數名：

1. 確定範圍。

   它是全局範圍，因此變數名稱以 `CONFIG__DEFAULT__`

1. 變數名稱的其餘部分為 `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`。

   **結果**:變數名稱為 `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 裝運國原產地

要查找發運國家/地區來源的變數名稱，請執行以下操作：

1. 確定範圍。

   查找 [資料庫](#find-a-website-or-store-view-scope-in-the-database) 如步驟1所述：查找網站或商店視圖範圍值。 (您還可以在管理員中找到值，如 [步驟2中的表：設定全局、網站或儲存視圖變數](#step-2-set-global-website-or-store-view-variables)。

   例如，範圍可能是 `CONFIG__WEBSITES__DEFAULT`。

1. 變數名稱的其餘部分為 `SHIPPING__ORIGIN__COUNTRY_ID`。

   **結果**:變數名稱為 `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 如何使用環境變數

使用PHP將配置值設定為變數 [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 關聯陣列。 可以在Commerce運行時運行的任何PHP指令碼中設定值。

>[!TIP]
>
>在中設定變數值 `index.php` 或 `pub/index.php` 由於可以根據web伺服器配置使用不同的應用程式入口點，因此並不總能按預期運行。 通過放置 `$_ENV` 指令 `app/bootstrap.php` 檔案，無論不同的應用程式入口點如何， `$_ENV` 指令自 `app/bootstrap.php` 作為Commerce體系結構的一部分載入檔案。

設定2的示例 `$_ENV` 值如下：

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

分步示例如所示 [使用環境變數設定配置值](../deployment/example-environment-variables.md)。

>[!WARNING]
>
>- 使用在 `$_ENV` 陣列，必須設定 `variables_order = "EGPCS"`（環境、獲取、發佈、Cookie和伺服器） `php.ini` 的子菜單。 有關詳細資訊，請參閱 [PHP文檔](https://www.php.net/manual/en/ini.core.php)。
>
>- 對於雲基礎架構上的Adobe Commerce，如果您嘗試使用 [Project Web介面](https://devdocs.magento.com/cloud/project/project-webint-basic.html#project-conf-env-var)，必須在變數名前加上 `env:`。 例如：
>
>![環境變數示例](https://devdocs.magento.com/common/images/cloud/cloud_env_var_example.png)
