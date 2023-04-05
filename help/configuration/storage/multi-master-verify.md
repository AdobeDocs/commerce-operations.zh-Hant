---
title: 驗證拆分資料庫
description: 了解如何驗證商務分割資料庫設定是否正常運作。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# 驗證拆分資料庫

{{ee-only}}

{{deprecate-split-db}}

配置後，主資料庫的配置如下：

- 主要商務資料庫：369表
- 商務報價資料庫：11表
- 商務銷售資料庫：55表

要驗證拆分資料庫是否正常工作，請執行以下任務，並使用資料庫工具(如 [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| 驗證項目 | 如何驗證 |
| -------------- | ------------- |
| 報價資料庫正在運行 | 新增項目至購物車。 驗證是否已將行添加到報價資料庫的 `quote`, `quote_address`，和 `quote_item` 表格。 |
| 銷售資料庫正在運行 | 完成訂單（任何付款方法，包括支票/貨幣訂單）。 驗證行已添加到銷售資料庫的 `sales_order_address`, `sales_order_item`，和 `sales_order_payment` 表格。 |

>[!WARNING]
>
>您必須手動備份另外兩個資料庫實例。 商務僅備份主資料庫實例。 此 [`magento setup:backup --db`](../../installation/tutorials/backup.md) 命令和管理選項不備份其他表。
