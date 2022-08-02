---
title: 日誌資料庫活動
description: 配置Commerce以使用記錄器介面記錄資料庫活動。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# 日誌資料庫活動

以下示例說明如何使用 [`Magento\Framework\DB\LoggerInterface`][interface]，它有兩個實現：

- 無記錄（預設）: [`Magento\Framework\DB\Logger\Quiet`][quiet]
- 日誌到 `var/log` 目錄： [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>可以使用Commerce CLI [啟用和禁用資料庫日誌記錄](../cli/enable-logging.md#database-logging)。

更改預設配置 `\Magento\Framework\DB\Logger\LoggerProxy`編輯 `app/etc/di.xml`。

首先，更改 `loggerAlias` 和 `logCallStack` 參數：

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

之後，提供 `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

最後，編譯代碼時使用：

```bash
bin/magento setup:di:compile
```

並使用以下方法清除快取：

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
