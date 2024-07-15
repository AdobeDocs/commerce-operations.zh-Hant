---
title: 檢查資料庫狀態
description: 請依照下列步驟檢查Adobe Commerce資料庫狀態。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# 檢查資料庫狀態

執行此命令之前，您必須[建立或更新部署組態](deployment.md)。

## 命令使用方式

檢查資料庫的狀態。

```bash
bin/magento setup:db:status
```

這個命令沒有引數或選項。

範例輸出如下：

```terminal
All modules are up to date.
```

指令會傳回下列其中一個退出代碼：

| 退出代碼 | 說明 | 建議的動作 |
|--------------|--------------|---------------|
| 0 | 一般 | 無 |
| 1 | 某些模組使用比資料庫更新或舊的程式碼版本 | 執行[`magento setup:upgrade`](database-upgrade.md)以更新資料庫結構描述，並從應用程式根目錄執行`composer update`以更新元件相依性 |
| 2 | `magento setup:upgrade`為必要項 | [`magento setup:upgrade`](database-upgrade.md)以更新資料庫結構描述 |
