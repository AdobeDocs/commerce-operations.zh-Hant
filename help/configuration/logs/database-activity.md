---
title: 記錄資料庫活動
description: 設定Commerce以使用記錄器介面記錄資料庫活動。
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# 記錄資料庫活動

下列範例顯示如何使用[`Magento\Framework\DB\LoggerInterface`][interface]來記錄資料庫活動，此範例有兩個實作：

- 未記錄任何內容（預設）： [`Magento\Framework\DB\Logger\Quiet`][quiet]
- 記錄至`var/log`目錄： [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>您可以使用Commerce CLI [啟用和停用資料庫記錄](../cli/enable-logging.md#database-logging)。

若要變更`\Magento\Framework\DB\Logger\LoggerProxy`的預設設定，請編輯您的`app/etc/di.xml`。

首先，將`loggerAlias`和`logCallStack`引數的預設值變更為：

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

之後，請提供`Magento\Framework\DB\Logger\File`的檔案路徑：

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

最後，編譯程式碼為：

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
