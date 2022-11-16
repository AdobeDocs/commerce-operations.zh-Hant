---
title: 啟用或禁用維護模式
description: 請依照下列步驟，自訂當您的Adobe Commerce或Magento Open Source部署因維護而停止時，客戶會看到的內容。
source-git-commit: bc025217ed7bc2195c0a2d919139abe13d184259
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---


# 啟用或禁用維護模式

以下指南說明標準維護模式頁面。 如果您需要使用自訂維護頁面，請參閱 [建立自訂維護頁面](../../upgrade/troubleshooting/maintenance-mode-options.md) 主題。

Adobe Commerce和Magento Open Source使用 [維護模式](../../configuration/bootstrap/application-modes.md#maintenance-mode) 禁用引導。 在維護、升級或重新配置站點時禁用引導是很有幫助的。

應用程式檢測維護模式如下：

* 若 `var/.maintenance.flag` 不存在，維護模式關閉，應用程式正常運行。
* 否則，除非 `var/.maintenance.ip` 存在。

   `var/.maintenance.ip` 可包含IP位址清單。 如果使用HTTP訪問入口點，且客戶端IP地址對應於該清單中的一個條目，則維護模式關閉。

## 安裝應用程式

使用此命令啟用或禁用維護模式之前，您必須 [安裝應用程式](../advanced.md).

## 啟用或禁用維護模式

使用 `magento maintenance` 啟用或禁用維護模式的CLI命令。

命令用法：

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

此 `--ip=<ip address>` 選項是可免除維護模式（例如，執行維護的開發人員）的IP位址。 若要在同一命令中免除多個IP位址，請使用選項多次。

>[!NOTE]
>
>使用 `--ip=<ip address>` with `magento maintenance:disable` 保存IP清單以供以後使用。 若要清除豁免IP清單，請使用 `magento maintenance:enable --ip=none` 或查看 [維護免稅IP地址清單](#maintain-the-list-of-exempt-ip-addresses).

此 `bin/magento maintenance:status` 命令顯示維護模式的狀態。

例如，要啟用不免除IP位址的維護模式：

```bash
bin/magento maintenance:enable
```

要為除192.0.2.10和192.0.2.11之外的所有客戶端啟用維護模式：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

將應用程式置於維護模式後，必須停止所有消息隊列使用者進程。
要尋找這些程式，一個方法是執行 `ps -ef | grep queue:consumers:start` 命令，然後運行 `kill <process_id>` 命令。 在多節點環境中，在每個節點上重複此任務。

## 維護免稅IP地址清單

若要維護豁免IP位址清單，您可以使用 `[--ip=<ip list>]` 選項，或者可以使用下列內容：

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

此 `<ip address> .. <ip address>` 語法是可選的以空格分隔的IP位址清單，可免除這些地址。

此 `--none` 選項會清除清單。

## 多商店設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

如果您想設定多個商店，每個商店的版面和本地化內容都不同，請傳遞 `$_GET['skin']` 參數。

在下列範例中，我們使用 `503` 類型錯誤範本檔案，需要本地化內容。

的建構子 `Error_Processor` 類別接受 `skin` GET參數來變更配置：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

這也可新增至 `.htaccess` 附加檔案 `skin` 參數。

### $_GET[&#39;skin&#39;] 參數

若要使用 `skin` 參數：

1. 檢查 `.maintenance.flag` 存在。
1. 請注意，主機位址是指 `HTTP_HOST`，或任何其他變數（例如ENV變數）。
1. 檢查 `skin` 參數存在。
1. 使用以下重寫規則設定參數。

   以下是重寫規則的一些範例：

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * 重寫規則 `^ %{REQUEST_URI}?skin=sub` [L]

1. 複製下列檔案：

   * `pub/errors/default/503.phtml` to `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` to `pub/errors/sub/styles.css`

1. 編輯這些檔案，以提供 `503.phtml` 檔案和自訂樣式 `styles.css` 檔案。

   確保路徑指向 `errors` 目錄。 目錄名稱必須符合 `RewriteRule`. 在上一個範例中， `sub` 目錄，此參數會指定為 `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>此 [nginx](../../configuration/multi-sites/ms-nginx.md) 必須為多商店設定新增設定。
