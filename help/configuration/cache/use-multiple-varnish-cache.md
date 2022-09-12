---
title: 使用多個清漆實例快取清除
description: 了解快取清除如何與多個清漆例項搭配運作。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---


# 快取清除多個清漆實例

Adobe Commerce和Magento Open Source支援多個現成可用的清漆例項。

本主題說明使用商務設定多個清漆例項的基本知識。

## 清除多個清漆實例的配置

在您使用 [`magento setup:config:set`](../../installation/tutorials/deployment.md) 命令。

您應使用 `--http-cache-hosts` 參數，指定以逗號分隔的清漆主機和偵聽埠清單。 （請勿以空格字元分隔主機。）

參數格式必須為 `<hostname or ip>:<listen port>`，此時您可以忽略 `<listen port>` 如果是埠80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

然後，您可以在重新整理「商務」快取時清除所有清漆主機(亦稱為 _清潔_ 快取)，或使用命令列。

若要使用「管理員」重新整理快取，請按一下 **系統** >工具> **快取管理**，然後按一下 **刷新Magento快取** 頁面頂端。 （您也可以重新整理個別的快取類型。）

要從cli刷新多個Rieshe實例的快取，請使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
