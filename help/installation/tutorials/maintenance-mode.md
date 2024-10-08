---
title: 啟用或停用維護模式
description: 請依照下列步驟，自訂當您的Adobe Commerce部署因維護而停止時，客戶會看到的內容。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# 啟用或停用維護模式

下列指南參考標準維護模式頁面。 如果您需要使用自訂維護頁面，請參閱[建立自訂維護頁面](../../upgrade/troubleshooting/maintenance-mode-options.md)主題。

Adobe Commerce使用[維護模式](../../configuration/bootstrap/application-modes.md#maintenance-mode)來停用啟動程式。 在維護、升級或重新設定網站時，停用啟動載入功能會很有幫助。

應用程式會偵測維護模式，如下所示：

* 如果`var/.maintenance.flag`存在，則維護模式為開啟，應用程式將傳回503維護頁面。
* 如果`var/.maintenance.ip`存在，且使用者端IP對應至此檔案中的其中一個IP位址專案，則會忽略要求的維護頁面。

## 安裝應用程式

使用此命令啟用或停用維護模式之前，您必須[安裝應用程式](../advanced.md)。

## 啟用或停用維護模式

使用`magento maintenance` CLI命令來啟用或停用維護模式。

命令使用方式：

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

`--ip=<ip address>`選項是免除維護模式的IP位址（例如，進行維護的開發人員）。 若要免除相同命令中多個IP位址，請多次使用選項。

>[!NOTE]
>
>搭配`magento maintenance:disable`使用`--ip=<ip address>`可儲存IP清單以供稍後使用。 若要清除劐免IP清單，請使用`magento maintenance:enable --ip=none`或參閱[維護劐免IP位址清單](#maintain-the-list-of-exempt-ip-addresses)。

`bin/magento maintenance:status`命令會顯示維護模式的狀態。

例如，啟用沒有IP位址劐免的維護模式：

```bash
bin/magento maintenance:enable
```

若要為192.0.2.10和192.0.2.11以外的所有使用者端啟用維護模式：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

將應用程式置於維護模式後，您必須停止所有訊息佇列取用者處理作業。
尋找這些處理序的一種方式是執行`ps -ef | grep queue:consumers:start`命令，然後為每個消費者執行`kill <process_id>`命令。 在多節點環境中，對每個節點重複此工作。

## 維護劐免IP位址清單

若要維護免除IP位址清單，您可以使用上述命令中的`[--ip=<ip list>]`選項，或使用下列選項：

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

`<ip address> .. <ip address>`語法是可免除的選用空格分隔的IP位址清單。

`--none`選項會清除清單。

## 多存放區設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

如果您要設定多個商店，每個商店都有不同的版面配置和當地語系化的內容，請將`$_GET['skin']`引數傳遞給預期的處理器。

在下列範例中，我們使用`503`型別錯誤範本檔案，這需要當地語系化的內容。

`Error_Processor`類別的建構函式接受`skin`個GET引數以變更配置：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

您也可以將此專案新增至`.htaccess`檔案中的重寫規則，該規則會將`skin`引數附加至URL。

### $_GET[&#39;skin&#39;]引數

若要使用`skin`引數：

1. 檢查`.maintenance.flag`是否存在。
1. 記下參照`HTTP_HOST`的主機位址或任何其他變數（例如ENV變數）。
1. 檢查`skin`引數是否存在。
1. 使用下列重寫規則來設定引數。

   以下是重寫規則的一些範例：

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 複製下列檔案：

   * `pub/errors/default/503.phtml`至`pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css`至`pub/errors/sub/styles.css`

1. 編輯這些檔案以在`503.phtml`檔案中提供當地語系化的內容，並在`styles.css`檔案中提供自訂樣式。

   確定您的路徑指向`errors`目錄。 目錄名稱必須符合`RewriteRule`中指示的URL引數。 在上一個範例中，使用了`sub`目錄，它指定為`RewriteRule` (`skin=sub`)中的引數

>[!NOTE]
>
>必須為多存放區設定新增[nginx](../../configuration/multi-sites/ms-nginx.md)設定。
