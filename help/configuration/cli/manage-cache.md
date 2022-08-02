---
title: 管理快取
description: 管理快取類型並查看快取狀態。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# 管理快取

{{file-system-owner}}

## 快取類型

Commerce 2具有以下快取類型：

| 快取類型「友好」名稱 | 快取類型代碼名稱 | 說明 |
|--- |--- |--- |
| 配置 | 配置 | Commerce從所有模組收集配置，合併它，並將合併結果保存到快取。 此快取還包含儲存在檔案系統和資料庫中的儲存特定設定。 修改配置檔案後清除或刷新此快取類型。 |
| 佈局 | 佈局 | 已編譯的頁面佈局（即所有元件的佈局元件）。 修改佈局檔案後清除或刷新此快取類型。 |
| 塊HTML輸出 | 塊_html | HTML每個塊的頁段。 修改視圖層後清除或刷新此快取類型。 |
| 收集資料 | 集合 | 資料庫查詢的結果。 如有必要，Commerce會自動清理此快取，但第三方開發人員可以將任何資料放在快取的任何段中。 如果自定義模組使用導致Commerce無法清除的快取項的邏輯，則清除或刷新此快取類型。 |
| DDL | db_ddl | 資料庫架構。 如有必要，Commerce會自動清理此快取，但第三方開發人員可以將任何資料放在快取的任何段中。 在對資料庫架構進行自定義更改後清除或刷新此快取類型。 （換句話說，Commerce不會自我更新。） 自動更新資料庫模式的一種方法是 `magento setup:db-schema:upgrade` 的子菜單。 |
| 已編譯配置 | 編譯配置 | 編譯配置 |
| 實體屬性值(EAV) | 房 | 與EAV屬性相關的元資料（例如，儲存標籤、與相關PHP代碼的連結、屬性呈現、搜索設定等）。 通常不應清除或刷新此快取類型。 |
| 頁快取 | 全頁 | 生成的HTML頁。 如有必要，Commerce會自動清理此快取，但第三方開發人員可以將任何資料放在快取的任何段中。 修改影響HTML輸出的代碼級別後，清除或刷新此快取類型。 建議保持此快取已啟用，因為快取HTML可顯著提高效能。 |
| 反射 | 反射 | 刪除Webapi模組和Customer模組之間的依賴關係。 |
| 翻譯 | 翻譯 | 合併所有模組的轉換後，將清除合併快取。 |
| 整合配置 | config_integration | 已編譯整合。 更改或添加整合後清除或刷新此快取。 |
| 整合API配置 | config_integration_api | 已編譯儲存整合的整合API配置。 |
| Web服務配置 | config_webservice | 快取Web API結構。 |
| 客戶通知 | customer_notification | 在用戶介面中顯示的臨時通知。 |

## 查看快取狀態

要查看快取的狀態，請輸入

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

示例如下：

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## 啟用或禁用快取類型

此命令使您能夠啟用或禁用所有快取類型或僅啟用指定的快取類型。 禁用快取類型在開發過程中非常有用，因為您無需刷新快取即可看到更改的結果；但是，禁用快取類型會對效能產生不利影響。

>[!INFO]
>
>從2.2版開始，在生產模式下運行Commerce時，只能使用命令行啟用或禁用快取類型。 如果在開發人員模式下運行Commerce，則可以使用命令行或手動啟用或禁用快取類型。 在執行此操作之前，必須手動 `<magento_root>/app/etc/env.php` 可寫 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html)。

您可以清除(也稱為 _衝_ 或 _刷新_)使用命令行或Admin的快取類型。

命令選項：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

省略 `[type]` 同時啟用或禁用所有快取類型。 的 `type` 選項是分隔空格的快取類型清單。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

要列出快取類型及其狀態：

```bash
bin/magento cache:status
```

例如，要禁用完整頁快取和DDL快取：

```bash
bin/magento cache:disable db_ddl full_page
```

示例結果：

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>啟用快取類型會自動清除該快取類型。

>[!INFO]
>
>從2.3.4版開始，Commerce在檢索所有系統EAV屬性時都會快取這些屬性。 以這種方式快取EAV屬性可提高效能，因為它減少了向DB插入/選擇請求的數量。 但是，它也增加了快取網路大小。 開發人員可以通過運行 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 的子菜單。 也可以通過管理員在 [開發人員模式](../bootstrap/application-modes.md) 設定 **商店** >設定 **配置** > **高級** > **開發人員** > **快取設定** > **快取用戶定義的屬性** 至 **是**。

## 清除和刷新快取類型

要從快取中清除過期項，您可以 _乾淨_ 或 _衝_ 快取類型：

- 清除快取類型僅從啟用的Commerce快取類型中刪除所有項。 換句話說，此選項不會影響其他進程或應用程式，因為它只清除Commerce使用的快取。

   未清除禁用的快取類型。

   >[!TIP]
   >
   >升級Magento Open Source或Adobe Commerce版本、從Magento Open Source升級到Adobe Commerce或為Adobe Commerce或任何模組安裝B2B後，請始終清除快取。

- 刷新快取類型會清除快取儲存，這可能會影響使用相同儲存的其他進程應用程式。

如果您已嘗試清除快取，但仍有無法隔離的問題，則刷新快取類型。

命令用法：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

位置 `[type]` 是分隔空格的快取類型清單。 省略 `[type]` 同時清除或刷新所有快取類型。 例如，要刷新所有快取類型，請輸入

```bash
   bin/magento cache:flush
```

示例結果：

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   config_webservice
   translate
```

>[!TIP]
>
>您還可以清除和刷新管理中的快取類型。 轉到 **系統** > **工具** > **快取管理**。 **刷新快取儲存** 等於 `bin/magento cache:flush`。 **刷新Magento快取** 等於 `bin/magento cache:clean`。
