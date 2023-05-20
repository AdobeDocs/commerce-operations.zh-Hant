---
title: 啟用或禁用維護模式
description: 按照以下步驟定制客戶在您的Adobe Commerce或Magento Open Source部署停止進行維護時看到的內容。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# 啟用或禁用維護模式

下面的指南是標準維護模式頁。 如果需要使用自定義維護頁，請參見 [建立自定義維護頁](../../upgrade/troubleshooting/maintenance-mode-options.md) 主題。

Adobe Commerce和Magento Open Source使用 [維護模式](../../configuration/bootstrap/application-modes.md#maintenance-mode) 禁用引導。 在維護、升級或重新配置站點時，禁用引導會很有幫助。

應用程式檢測維護模式如下：

* 如果 `var/.maintenance.flag` 不存在，維護模式已關閉，應用程式正常運行。
* 否則，維護模式將開啟，除非 `var/.maintenance.ip` 存在。

   `var/.maintenance.ip` 可以包含IP地址清單。 如果使用HTTP訪問入口點，並且客戶端IP地址與該清單中的一個條目相對應，則維護模式將關閉。

## 安裝應用程式

在使用此命令啟用或禁用維護模式之前，必須 [安裝應用程式](../advanced.md)。

## 啟用或禁用維護模式

使用 `magento maintenance` 用於啟用或禁用維護模式的CLI命令。

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

的 `--ip=<ip address>` option是一個IP地址，可免除維護模式（例如，執行維護的開發人員）。 要在同一命令中免除多個IP地址，請多次使用該選項。

>[!NOTE]
>
>使用 `--ip=<ip address>` 與 `magento maintenance:disable` 保存IP清單供以後使用。 要清除免除IP的清單，請使用 `magento maintenance:enable --ip=none` 查看 [維護免除IP地址清單](#maintain-the-list-of-exempt-ip-addresses)。

的 `bin/magento maintenance:status` 命令顯示維護模式的狀態。

例如，要啟用無IP地址豁免的維護模式：

```bash
bin/magento maintenance:enable
```

要為除192.0.2.10和192.0.2.11之外的所有客戶端啟用維護模式：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

將應用程式置於維護模式後，必須停止所有消息隊列使用者進程。
查找這些進程的一種方法是運行 `ps -ef | grep queue:consumers:start` 命令，然後運行 `kill <process_id>` 命令。 在多節點環境中，在每個節點上重複此任務。

## 維護免除IP地址清單

要維護免除IP地址清單，您可以使用 `[--ip=<ip list>]` 選項，或者可以使用以下命令：

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

的 `<ip address> .. <ip address>` 語法是要免除的IP地址的可選空格分隔清單。

的 `--none` 選項清除清單。

## 多商店設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

如果要設定多個儲存，每個儲存具有不同的佈局和本地化內容，請傳遞 `$_GET['skin']` 參數。

在以下示例中，我們使用 `503` 類型錯誤模板檔案，需要本地化內容。

的建構子 `Error_Processor` 類接受 `skin` GET參數以更改佈局：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

也可以將此內容添加到 `.htaccess` 附加檔案 `skin` 的子菜單。

### $_GET[「外觀」] 參數

使用 `skin` 參數：

1. 檢查 `.maintenance.flag` 存在。
1. 請注意主機地址，它指 `HTTP_HOST`，或ENV變數等任何其他變數。
1. 檢查 `skin` 參數存在。
1. 使用下面的重寫規則設定參數。

   以下是一些重寫規則的示例：

   * 重寫條件 `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * 重寫條件 `%{HTTP_HOST} ^sub.example.com$`
   * 重寫條件 `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * 重寫規則 `^ %{REQUEST_URI}?skin=sub` [L]

1. 複製下列檔案：

   * `pub/errors/default/503.phtml` 至 `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` 至 `pub/errors/sub/styles.css`

1. 編輯這些檔案以在 `503.phtml` 檔案和自定義樣式 `styles.css` 的子菜單。

   確保路徑指向 `errors` 的子菜單。 目錄名必須與中指示的URL參數匹配 `RewriteRule`。 在上例中， `sub` 目錄，它在 `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>的 [nginx](../../configuration/multi-sites/ms-nginx.md) 必須為多儲存設定添加設定。
