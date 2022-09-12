---
title: 管理快取
description: 管理快取類型並查看快取狀態。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---


# 管理快取

{{file-system-owner}}

## 快取類型

商務2具有以下快取類型：

| 快取類型「友好」名稱 | 快取類型代碼名 | 說明 |
|--- |--- |--- |
| 設定 | 設定 | 商務會從所有模組收集配置、合併該配置，並將合併的結果保存到快取。 此快取還包含儲存在檔案系統和資料庫中的儲存特定設定。 修改組態檔後，清除或清除此快取類型。 |
| 版面 | 配置 | 編譯的頁面配置（即所有元件的佈局元件）。 修改配置檔案後，清除或刷新此快取類型。 |
| 塊HTML輸出 | block_html | HTML每個區塊的頁面片段。 修改檢視層後，清除或排清此快取類型。 |
| 集合資料 | 集合 | 資料庫查詢的結果。 如有必要，商務會自動清除此快取，但協力廠商開發人員可將任何資料放入快取的任何區段中。 如果您的自訂模組使用導致快取項目（商務無法清除）的邏輯，請清除或排清此快取類型。 |
| DDL | db_ddl | 資料庫架構。 如有必要，商務會自動清除此快取，但協力廠商開發人員可將任何資料放入快取的任何區段中。 在對資料庫架構進行自定義更改後，清除或刷新此快取類型。 （換句話說，商務不會自行更新。） 自動更新資料庫架構的一種方式是使用 `magento setup:db-schema:upgrade` 命令。 |
| 編譯的配置 | cimpled_config | 編譯配置 |
| 實體屬性值(EAV) | eav | 與EAV屬性相關的元資料（例如，儲存標籤、到相關PHP代碼的連結、屬性呈現、搜索設定等）。 通常不需要清除或刷新此快取類型。 |
| 頁面快取 | full_page | 產生的HTML頁面。 如有必要，商務會自動清除此快取，但協力廠商開發人員可將任何資料放入快取的任何區段中。 修改影響HTML輸出的程式碼層級後，清除或排清此快取類型。 建議保持此快取已啟用，因為快取HTML可大幅提升效能。 |
| 反射 | 反射 | 移除Webapi模組和客戶模組之間的相依性。 |
| 翻譯 | 翻譯 | 從所有模組合併翻譯後，將清理合併快取。 |
| 整合設定 | config_integration | 編譯整合。 變更或新增整合後，清除或清除此快取。 |
| 整合API設定 | config_integration_api | 編譯商店整合的整合API設定。 |
| 網站服務設定 | config_webservice | 快取Web API結構。 |
| 客戶通知 | customer_notification | 在使用者介面中顯示的暫時通知。 |

## 查看快取狀態

要查看快取的狀態，請輸入

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

範例如下：

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

通過此命令，您可以啟用或禁用所有快取類型或僅指定的快取類型。 禁用快取類型在開發期間非常有用，因為您無需刷新快取即可查看更改的結果；但是，禁用快取類型會對效能產生不利影響。

>[!INFO]
>
>從2.2版開始，在生產模式中執行商務時，您只能使用命令列來啟用或停用快取類型。 如果以開發人員模式執行商務，您可以使用命令列或手動啟用或停用快取類型。 在執行此動作之前，您必須手動 `<magento_root>/app/etc/env.php` 可由 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).

您可以清除(亦稱為 _刷新_ 或 _重新整理_)快取類型，使用命令列或管理員。

命令選項：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

其中省略 `[type]` 同時啟用或禁用所有快取類型。 此 `type` 選項是以空格分隔的快取類型清單。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

要列出快取類型及其狀態，請執行以下操作：

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
>自2.3.4版起，Commerce會在擷取所有系統EAV屬性時快取這些屬性。 以此方式快取EAV屬性可改善效能，因為它可減少對資料庫的插入/選取請求數量。 但是，它也會增加快取網路大小。 開發人員可以執行 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 命令。 在中時，您也可以由管理員執行 [開發人員模式](../bootstrap/application-modes.md) 設定 **商店** >設定 **設定** > **進階** > **開發人員** > **快取設定** > **快取用戶定義的屬性** to **是**.

## 清除和刷新快取類型

若要從快取中清除過期項目，您可以 _清潔_ 或 _刷新_ 快取類型：

- 清除快取類型只會從啟用的商務快取類型中刪除所有項目。 換言之，此選項不會影響其他程式或應用程式，因為它只會清除商務使用的快取。

   禁用的快取類型未清除。

   >[!TIP]
   >
   >升級Magento Open Source或Adobe Commerce版本、從Magento Open Source升級至Adobe Commerce，或為Adobe Commerce或任何模組安裝B2B後，請一律清除快取。

- 清除快取類型會清除快取儲存，這可能會影響使用相同儲存的其他進程應用程式。

如果您已嘗試清除快取，但仍有無法隔離的問題，請刷新快取類型。

命令用法：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

其中 `[type]` 是以空格分隔的快取類型清單。 省略 `[type]` 同時清除或刷新所有快取類型。 例如，要刷新所有快取類型，請輸入

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
>您也可以清除和清除「管理員」中的快取類型。 前往 **系統** > **工具** > **快取管理**. **刷新快取儲存** 等於 `bin/magento cache:flush`. **刷新Magento快取** 等於 `bin/magento cache:clean`.
