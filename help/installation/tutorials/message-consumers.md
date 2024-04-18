---
title: 設定訊息使用者
description: 請依照下列步驟設定Adobe Commerce訊息佇列取用者的行為。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# 設定訊息使用者

執行此指令之前，您必須執行下列動作 *或* 您必須 [安裝應用程式](../advanced.md)：

* [建立或更新部署設定](deployment.md)
* [建立資料庫綱要](database.md)

## 設定消費者行為

若要設定消費者行為，可在設定函式中傳送索引鍵/值組：

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 引數說明

{{$include /help/_includes/cli-consumers.md}}
