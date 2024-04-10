---
title: 管理快取
description: 使用Commerce CLI從命令列管理快取型別並檢視快取狀態
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 1070291396144f866cadd5e42ebca3e77a484a9b
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 管理快取

{{file-system-owner}}

## 快取型別

您可以使用Adobe Commerce快取管理系統來改善網站的效能。 本主題說明系統管理員或有權存取Commerce應用程式伺服器的開發人員如何從命令列管理快取。

>[!NOTE]
>
>
>Commerce網站管理員可以使用「快取管理系統」工具從Admin管理快取。 另請參閱 [快取管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) 在 _Admin System指南_.


## 檢視快取狀態

從Commerce應用程式伺服器的命令列，使用 `cache:status` Commerce CLI命令。

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
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>如需Adobe Commerce支援之預設快取型別的詳細說明，請參閱 [快取](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) 在 _Admin System指南_.


## 啟用或停用快取型別

這個指令可讓您啟用或停用所有快取型別，或僅停用您指定的快取型別。 在開發期間，停用快取型別很有用，因為您可以看到變更的結果，而不必清除快取；但是，停用快取型別會對效能造成不良影響。

>[!INFO]
>
>從2.2版開始，在生產模式下執行Commerce時，您只能使用命令列啟用或停用快取型別。 如果在開發人員模式下執行Commerce，您可以使用命令列或手動啟用或停用快取型別。 在執行此操作之前，您必須手動進行 `<magento_root>/app/etc/env.php` 可由 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).

您可以清除(也稱為 _排清_ 或 _重新整理_)使用命令列或Admin的快取型別。

命令選項：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

省略 `[type]` 同時啟用或停用所有快取型別。 此 `type` option是以空格分隔的快取型別清單。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

若要列出快取型別及其狀態：

```bash
bin/magento cache:status
```

例如，若要停用完整頁面快取和DDL快取：

```bash
bin/magento cache:disable db_ddl full_page
```

範例結果：

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>啟用快取型別會自動清除該快取型別。

>[!INFO]
>
>自2.3.4版起，Commerce會在擷取所有系統EAV屬性時加以快取。 以這種方式快取EAV屬性可改善效能，因為它會減少對DB的插入/選取要求量。 不過，它也會增加快取網路大小。 開發人員可藉由執行 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 命令。 這亦可由管理員在中完成 [開發人員模式](../bootstrap/application-modes.md) 透過設定 **商店** >設定 **設定** > **進階** > **開發人員** > **快取設定** > **快取使用者定義的屬性** 至 **是**.

## 清除和排清快取型別

>[!NOTE]
>
>可同時自動讓多個頁面快取失效 **_不含_** 這些實體正在編輯。 例如，當目錄中的任何產品指派給任何類別時，或當任何 [!UICONTROL related product rule] 已修改。

若要從快取中永久刪除過期的專案，您可以 _清除_ 或 _排清_ 快取型別：

- 清除快取型別只會從已啟用的Commerce快取型別中刪除所有專案。 換言之，此選項不會影響其他程式或應用程式，因為它只會清除Commerce使用的快取。

  停用的快取型別不會清除。

  >[!TIP]
  >
  >升級Magento Open Source或Adobe Commerce版本、從Magento Open Source升級至Adobe Commerce，或安裝Adobe Commerce或任何模組適用的B2B後，請務必清理快取。

- 清除快取型別會清除快取儲存體，這可能會影響使用相同儲存體的其他程式應用程式。

如果您已經嘗試清除快取，但仍有無法隔離的問題，請排清快取型別。

命令使用方式：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

位置 `[type]` 是以空格分隔的快取型別清單。 省略 `[type]` 同時清除或排清所有快取型別。 例如，若要排清所有快取型別，請輸入

```bash
   bin/magento cache:flush
```

範例結果：

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
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>您也可以在Admin中清理和排清快取型別。 前往 **系統** > **工具** > **快取管理**. **排清快取儲存體** 相當於 `bin/magento cache:flush`. **排清Magento快取** 相當於 `bin/magento cache:clean`.
