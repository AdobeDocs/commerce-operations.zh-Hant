---
title: 檢查資料庫狀態
description: 請依照下列步驟檢查Adobe Commerce資料庫狀態。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%
---
# 檢查資料庫狀態

執行此命令之前，您必須[建立或更新部署組態](deployment.md)。

## 命令使用方式

檢查資料庫的狀態。

```shell
bin/magento setup:db:status
```

這個命令沒有引數或選項。

範例輸出如下：

```text
All modules are up to date.
```

指令會傳回下列其中一個退出代碼：

| 退出代碼 | 說明 | 建議的動作 |
|--------------|--------------|---------------|
| 0 | 一般 | 無 |
| 1 | 某些模組使用比資料庫更新或舊的程式碼版本 | 執行[`magento setup:upgrade`](database-upgrade.md)以更新資料庫結構描述，並從應用程式根目錄執行`composer update`以更新元件相依性 |
| 2 | `magento setup:upgrade`為必要項 | [`magento setup:upgrade`](database-upgrade.md)以更新資料庫結構描述 |
