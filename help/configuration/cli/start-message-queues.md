---
title: 啟動訊息佇列取用者
description: 瞭解如何啟動訊息佇列消費者。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# 啟動訊息佇列取用者

{{file-system-owner}}

您必須啟動[訊息佇列取用者](../queues/consumers.md)以啟用非同步操作，例如Inventory management大量動作和REST大量與非同步端點。 若要啟用B2B功能，您必須啟動多個取用者。 協力廠商模組可能也需要您啟動自訂消費者。

若要檢視所有使用者的清單，請執行下列動作：

```bash
bin/magento queue:consumers:list
```

若要啟動訊息佇列取用者：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用所有可用訊息後，該命令即終止。 您可以手動或使用cron作業再次執行此命令。 您也可以執行多個`magento queue:consumers:start`命令的執行個體來處理大型訊息佇列。 例如，您可以將`&`附加至命令，以便在背景執行、返回提示字元並繼續執行命令：

```bash
bin/magento queue:consumers:start <consumer_name> &
```

如需有關命令選項、引數和值的詳細資訊，請參閱&#x200B;_命令列工具參考_&#x200B;的Commerce區段中的[`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart)。

>[!INFO]
>
>`--multi-process`選項存在於`queue:consumers:start`命令中，但若要以平行處理序執行消費者，請在`/app/etc/env.php`中設定[`multiple_processes`](../queues/manage-message-queues.md#configuration)選項。 否則，如果使用`--multi-process`選項呼叫`queue:consumers:start`，則它僅適用於單一執行緒。
