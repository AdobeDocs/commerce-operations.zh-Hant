---
title: 使用多個Varnish執行個體進行快取清除
description: 瞭解快取清除如何與多個Varnish執行個體搭配運作。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# 快取清除多個Varnish例項

Adobe Commerce可支援多個Varnish執行個體。

本主題說明使用Commerce設定多個Varnish執行個體的基本知識。

## 清除多個Varnish例項的設定

使用[`magento setup:config:set`](../../installation/tutorials/deployment.md)命令設定清漆主機後，Commerce會清除清漆主機。

您應該使用`--http-cache-hosts`引數來指定Varnish主機和接聽連線埠的逗號分隔清單。 （請勿以空格字元分隔主機。）

引數格式必須是`<hostname or ip>:<listen port>`，若是連線埠80，則可以省略`<listen port>`。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

當您在管理員中重新整理Commerce快取（也稱為&#x200B;_清除_&#x200B;快取）或使用命令列時，可以清除所有Varnish主機。

若要使用Admin重新整理快取，請按一下[工具] > [快取管理] **** ****，然後按一下頁面頂端的[排清Magento快取] **。**（您也可以重新整理個別快取型別。）

若要從cli重新整理多個Varnish執行個體的快取，請使用[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)命令做為[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
