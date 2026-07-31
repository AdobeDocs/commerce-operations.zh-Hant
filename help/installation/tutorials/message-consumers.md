---
title: 設定訊息使用者
description: 請依照下列步驟設定Adobe Commerce訊息佇列取用者的行為。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
last-update: 2026-04-28T00:00:00Z
source-git-commit: 1166b8fbfeef21a51ad6e4e695aed2b25006230e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# 設定訊息使用者

在執行這個命令之前，您必須執行下列動作&#x200B;*或*，您必須[安裝應用程式](../advanced.md)：

* [建立或更新部署設定](deployment.md)
* [建立資料庫綱要](database.md)

## 設定消費者行為

若要設定消費者行為，可在設定函式中傳送索引鍵/值組：

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 引數說明

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
