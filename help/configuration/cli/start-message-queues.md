---
title: 啟動消息隊列消費者
description: 了解如何啟動訊息佇列消費者。
source-git-commit: 3e3dac0c75622b210cf1168639b8804003f3c538
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 啟動消息隊列消費者

{{file-system-owner}}

您必須啟動 [消息隊列使用者](../queues/consumers.md) 啟用非同步操作，例如Inventory management大量動作和REST大量和非同步端點。 若要啟用B2B功能，您必須啟動多個消費者。 協力廠商模組可能也會要求您啟動自訂消費者。

要查看所有消費者的清單，請執行以下操作：

```bash
bin/magento queue:consumers:list
```

要啟動消息隊列使用者，請執行以下操作：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用所有可用消息後，命令將終止。 您可以手動或透過cron工作再次執行命令。 您也可以執行 `magento queue:consumers:start` 處理大消息隊列的命令。 例如，您可以附加 `&` 要在後台運行該命令，請返回提示，然後繼續運行命令：

```bash
bin/magento queue:consumers:start <consumer_name> &
```

請參閱 [佇列:consumers:開始](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) 的「商務」區段 _命令行工具參考_ 有關命令選項、參數和值的詳細資訊。

>[!INFO]
>
>此 `--multi-process` 選項在 `queue:consumers:start` 命令，但要使用並行進程運行用戶，請配置 [`multiple_processes`](../queues/manage-message-queues.md#configuration) 選項 `/app/etc/env.php`. 否則，若 `queue:consumers:start` 是以呼叫 `--multi-process` 選項，它只適用於單個執行緒。
