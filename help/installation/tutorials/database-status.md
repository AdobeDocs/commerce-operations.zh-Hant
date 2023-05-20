---
title: 檢查資料庫狀態
description: 按照以下步驟檢查您的Adobe Commerce或Magento Open Source資料庫狀態。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---

# 檢查資料庫狀態

在運行此命令之前，必須 [建立或更新部署配置](deployment.md)。

## 命令用法

檢查資料庫的狀態。

```bash
bin/magento setup:db:status
```

此命令沒有參數或選項。

輸出示例如下：

```terminal
All modules are up to date.
```

該命令返回以下退出代碼之一：

| 退出代碼 | 說明 | 建議的操作 |
|--------------|--------------|---------------|
| 0 | 正常 | 無 |
| 1 | 某些模組使用比資料庫更新或更舊的代碼版本 | 運行 [`magento setup:upgrade`](database-upgrade.md) 更新資料庫架構並運行 `composer update` 從應用程式根目錄更新元件依賴項 |
| 2 | `magento setup:upgrade` 必填 | [`magento setup:upgrade`](database-upgrade.md) 更新資料庫模式 |
