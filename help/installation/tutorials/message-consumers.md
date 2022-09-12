---
title: 配置消息使用者
description: 請依照下列步驟來設定Adobe Commerce或Magento Open Source訊息佇列使用者的行為。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---


# 配置消息使用者

在運行此命令之前，您必須執行以下操作 *或* 您必須 [安裝應用程式](../advanced.md):

* [建立或更新部署配置](deployment.md)
* [建立資料庫架構](database.md)

## 設定消費者行為

設定消費者行為的方式為在設定函式內傳送索引鍵/值組：

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 參數說明

{{$include /help/_includes/cli-consumers.md}}
