---
title: 使用多個清漆實例進行快取清除
description: 瞭解快取清除如何與多個清漆實例一起使用。
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 快取清除多個清漆實例

Adobe Commerce和Magento Open Source支援機箱外的多個清漆實例。

本主題顯示了使用Commerce配置多個清漆實例的基本資訊。

## 清除多個清漆實例的配置

在使用配置清漆主機後，Commerce清除清漆主機 [`magento setup:config:set`](../../installation/tutorials/deployment.md) 的子菜單。

您應使用 `--http-cache-hosts` 參數，指定以逗號分隔的清漆主機和偵聽埠清單。 （不要將主機與空格字元分開。）

參數格式必須為 `<hostname or ip>:<listen port>`，在 `<listen port>` 如果是埠80。

比如說，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

然後，在刷新Commerce快取(也稱為 _清洗_ 快取)或使用命令行。

要使用Admin刷新快取，請按一下 **系統** >工具> **快取管理**，然後按一下 **刷新Magento快取** 頁面頂部。 （也可以刷新單個快取類型。）

要從cli刷新多個清漆實例的快取，請使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
