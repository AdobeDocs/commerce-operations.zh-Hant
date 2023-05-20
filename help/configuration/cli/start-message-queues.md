---
title: 啟動消息隊列使用者
description: 瞭解如何啟動消息隊列使用者。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 啟動消息隊列使用者

{{file-system-owner}}

必須啟動 [消息隊列使用者](../queues/consumers.md) 啟用非同步操作，如Inventory management成批操作和REST批量和非同步端點。 要啟用B2B功能，必須啟動多個使用者。 第三方模組可能還要求您啟動自定義使用者。

要查看所有使用者的清單，請執行以下操作：

```bash
bin/magento queue:consumers:list
```

要啟動消息隊列使用者，請執行以下操作：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

消耗所有可用消息後，命令將終止。 您可以再次手動或使用cron作業運行該命令。 您還可以運行 `magento queue:consumers:start` 命令以處理大消息隊列。 例如，您可以追加 `&` 命令以在後台運行它，返回提示符並繼續運行命令：

```bash
bin/magento queue:consumers:start <consumer_name> &
```

請參閱 [隊列:consumers:開始](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) 中的 _命令行工具參考_ 的子菜單。

>[!INFO]
>
>的 `--multi-process` 中 `queue:consumers:start` 命令，但要使用並行進程運行使用者，請配置 [`multiple_processes`](../queues/manage-message-queues.md#configuration) 選項 `/app/etc/env.php`。 否則，如果 `queue:consumers:start` 調用 `--multi-process` 選項，它僅在單個線程上工作。
