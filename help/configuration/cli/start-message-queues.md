---
title: 啟動訊息佇列取用者
description: 瞭解如何為Adobe Commerce非同步操作啟動訊息佇列取用者。 探索消費者管理和B2B功能設定。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '189'
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

如需有關命令選項、引數和值的詳細資訊，請參閱[`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart)命令列工具參考&#x200B;_的Commerce區段中的_。

>[!INFO]
>
>`--multi-process`選項存在於`queue:consumers:start`命令中，但若要以平行處理序執行消費者，請在[`multiple_processes`](../queues/manage-message-queues.md#configuration)中設定`/app/etc/env.php`選項。 否則，如果使用`queue:consumers:start`選項呼叫`--multi-process`，則它僅適用於單一執行緒。
