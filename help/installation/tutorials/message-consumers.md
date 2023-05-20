---
title: 配置消息使用者
description: 按照以下步驟配置Adobe Commerce或Magento Open Source消息隊列使用者的行為。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# 配置消息使用者

在運行此命令之前，必須執行以下操作 *或* 必須 [安裝應用程式](../advanced.md):

* [建立或更新部署配置](deployment.md)
* [建立資料庫架構](database.md)

## 配置使用者行為

通過在設定函式中發送密鑰/值對來配置使用者行為：

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 參數說明

{{$include /help/_includes/cli-consumers.md}}
