---
title: 覆蓋配置設定
description: 了解如何使用環境變數來覆寫組態設定。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 覆蓋配置設定

本主題討論如何通過配置路徑導出環境變數名稱。 您可以使用環境變數覆寫Adobe Commerce組態設定。 例如，您可以在生產系統上覆寫付款處理者的即時URL值。

您可以覆寫 _any_ 使用環境變數進行配置設定；不過，Adobe建議您使用共用組態檔來維持一致的設定， `config.php`，以及系統特定的設定檔案， `env.php`，如 [部署一般概述](../deployment/overview.md).

>[!TIP]
>
>查看 [配置環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) 中的主題 _雲端基礎架構商務指南_.

## 環境變數

環境變數名稱由其範圍以及特定格式的配置路徑組成。 以下幾節將詳細討論如何判斷變數名稱。

您可以對下列任何項目使用變數：

- [敏感值](config-reference-sens.md) 必須使用環境變數或 [`magento config:sensitive:set`](../cli/set-configuration-values.md) 命令。
- 系統特定值必須使用：

   - 環境變數
   - 此 [`magento config:set`](../cli/set-configuration-values.md) 命令
   - 管理員後面接著 [`magento app:config:dump` 命令](../cli/export-configuration.md)

配置路徑位於：

- [敏感和系統特定配置路徑參考](config-reference-sens.md)
- [付款配置路徑參考](config-reference-payment.md)
- [商務B2B擴充功能設定路徑參考](config-reference-b2b.md)
- [其他設定路徑參考](config-reference-general.md)

### 變數名稱

系統設定變數名稱的一般格式如下：

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 可以是：

- 全局範圍(即 _all_ 範圍)

   全局範圍變數的格式如下：

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 特定範圍（即，設定只會影響指定的商店檢視或網站）

   例如，儲存視圖範圍變數具有以下格式：

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   有關作用域的詳細資訊，請參閱：

   - [步驟1:查找網站或儲存視圖範圍值](#step-1-find-the-website-or-store-view-scope-value)
   - [範圍的商務使用手冊主題](https://docs.magento.com/user-guide/configuration/scope.html)
   - [範圍快速參考](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` 是配置路徑，其中雙底線字元取代 `/`. 如需詳細資訊，請參閱 [步驟2:設定系統變數](#step-2-set-global-website-or-store-view-variables).

### 變數格式

`<SCOPE>` 從 `<SYSTEM__VARIABLE__NAME>` 兩個底線字元。

`<SYSTEM__VARIABLE__NAME>` 衍生自組態設定的 _配置路徑_，此 `/` 唯一識別特定設定的分隔字串。 取代 `/` 字元（在配置路徑中），使用兩個下划線字元建立系統變數。

如果配置路徑包含下划線字元，則下划線字元仍保留在變數中。

您可以在下列位置找到完整的設定路徑清單：

- [敏感和系統特定配置路徑參考](config-reference-sens.md)
- [付款配置路徑參考](config-reference-payment.md)
- [商務企業B2B擴充功能組態路徑參考](config-reference-b2b.md)
- [其他設定路徑參考](config-reference-general.md)

## 步驟1:查找網站或儲存視圖範圍值

本節將討論如何查找和設定每個 _範圍_ （商店檢視或網站）。 若要設定全域範圍變數，請參閱 [步驟2:設定全域、網站或儲存檢視變數](#step-2-set-global-website-or-store-view-variables).

範圍值來自 `store`, `store_group`，和 `store_website` 表格。

- 此 `store` 表指定儲存視圖名稱和代碼
- 此 `store_website` 表格指定網站名稱和代碼

您也可以使用「管理員」來尋找代碼值。

如何閱讀表格：

- `Path in Admin` 欄

   逗號前面的值是管理員導覽中的路徑。 逗號後面的值是右窗格中的選項。

- `Variable name` column是相應環境變數的名稱。

   您可以選擇將這些配置參數的系統值指定為環境變數（如果需要）。

   - 整個變數名稱一律為大寫
   - 以啟動變數名稱 `CONFIG__` （注意兩個下划線字元）
   - 您可以找到 `<STORE_VIEW_CODE>` 或 `<WEBSITE_CODE>` 管理員或商務資料庫中變數名稱的一部分，如下節所示。
   - 您可以找到 `<SYSTEM__VARIABLE__NAME>` 如 [步驟2:設定全域、網站或儲存檢視變數](#step-2-set-global-website-or-store-view-variables).

### 在管理員中尋找網站或商店檢視範圍

下表匯總了如何在管理員中查找網站或儲存視圖值。

| 說明 | 管理中的路徑 | 變數名稱 |
|--------------|--------------|----------------------|
| 建立、編輯、刪除商店視圖 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| 建立、編輯、刪除網站 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

例如，若要在管理員中尋找網站或儲存檢視範圍值：

1. 以獲授權檢視網站的使用者身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. 按一下網站或商店檢視的名稱。

   右窗格的顯示方式如下所示。

   ![尋找網站代碼](../../assets/configuration/website-code.png)

1. 範圍名稱顯示在 **[!UICONTROL Code]** 欄位。
1. 繼續 [步驟2:設定全域、網站或儲存檢視變數](#step-2-set-global-website-or-store-view-variables).

### 在資料庫中查找網站或儲存視圖範圍

要從資料庫獲取這些值：

1. 如果您尚未登入，請以檔案系統擁有者身分登入您的開發系統。
1. 輸入以下命令：

   ```bash
   mysql -u <database-username> -p
   ```

1. 在 `mysql>` 提示，按照所示順序輸入以下命令：

   ```shell
   use <database-name>;
   ```

1. 使用以下SQL查詢查找相關值：

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   範例如下：

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

   例如，若要設定測試網站的設定變數，請使用下列格式：

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   where `<SYSTEM__VARIABLE__NAME>` 會顯示於下一節。

## 步驟2:設定全域、網站或儲存檢視變數

本節探討如何設定系統變數。

- 若要設定全域範圍的值（即所有網站、商店和商店檢視），請以 `CONFIG__DEFAULT__`.

- 若要設定特定商店檢視或網站的值，請啟動變數名稱，如 [步驟1:查找範圍值](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 變數名稱的最後一部分是設定路徑，這對每個設定都是唯一的。

[請參閱一些範例](#examples).

下表顯示一些範例變數。

| 說明 | 管理中的路徑(省略 **商店** > **設定** > **設定**) | 變數名稱 |
|--------------|--------------|----------------------|
| Elasticsearch伺服器主機名 | 目錄> **目錄**, **Elasticsearch伺服器主機名** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch伺服器埠 | 目錄> **目錄**, **Elasticsearch伺服器埠** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 船運國家/地區原產 | 銷售> **運送設定** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| 自訂管理URL | 進階> **管理** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| 自訂管理路徑 | 進階> **管理** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 範例

本節說明如何尋找某些範例變數的值。

### Elasticsearch伺服器主機名

若要尋找全域HTML縮制的變數名稱：

1. 確定範圍。

   此為全域範圍，因此變數名稱的開頭為 `CONFIG__DEFAULT__`

1. 其餘的變數名稱為 `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **結果**:變數名稱為 `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 船運國家/地區原產

要查找發運國家/地區來源的變數名稱，請執行以下操作：

1. 確定範圍。

   在 [資料庫](#find-a-website-or-store-view-scope-in-the-database) 如步驟1所述：查找網站或儲存視圖範圍值。 (您也可以在「管理員」中找到值，如 [步驟2中的表格：設定全域、網站或儲存檢視變數](#step-2-set-global-website-or-store-view-variables)

   例如，範圍可能是 `CONFIG__WEBSITES__DEFAULT`.

1. 其餘的變數名稱為 `SHIPPING__ORIGIN__COUNTRY_ID`.

   **結果**:變數名稱為 `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 如何使用環境變數

使用PHP將配置值設定為變數 [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 關聯陣列。 您可以在Commerce運行時運行的任何PHP指令碼中設定值。

>[!TIP]
>
>在 `index.php` 或 `pub/index.php` 不一定能如預期般運作，因為可根據web伺服器組態使用不同的應用程式入口點。 通過 `$_ENV` 指令 `app/bootstrap.php` 檔案，無論應用程式入口點為何， `$_ENV` 指令始終執行，因為 `app/bootstrap.php` 檔案會載入為商務架構的一部分。

設定2的範例 `$_ENV` 值如下：

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

逐步範例如下所示： [使用環境變數設定設定值](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- 若要使用 `$_ENV` 陣列，您必須 `variables_order = "EGPCS"`（環境、取得、發佈、Cookie和伺服器）, `php.ini` 檔案。 如需詳細資訊，請參閱 [PHP文檔](https://www.php.net/manual/en/ini.core.php).
>
>- 若為雲端基礎架構上的Adobe Commerce，如果您嘗試使用 [項目Web介面](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)，您必須在變數名稱的開頭加上 `env:`. 例如：
>
>![環境變數範例](../../assets/configuration/cloud-console-envvariable.png)
