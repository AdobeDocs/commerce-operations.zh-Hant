---
title: 驗證剝離資料庫
description: 瞭解如何驗證Commerce剝離資料庫配置是否正常工作。
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 驗證剝離資料庫

{{ee-only}}

{{deprecate-split-db}}

配置後，主資料庫的配置如下：

- 主Commerce資料庫：369個表
- 商業報價資料庫：11個表
- 商業銷售資料庫：55個表

要驗證拆分資料庫是否正常工作，請執行以下任務並驗證是否使用資料庫工具(如 [phmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| 驗證內容 | 如何驗證 |
| -------------- | ------------- |
| quote資料庫正在工作 | 將物料添加到購物車。 驗證是否已將行添加到報價資料庫的 `quote`。 `quote_address`, `quote_item` 的下界。 |
| 銷售資料庫正在工作 | 完成訂單（任何付款方式，包括支票/貨幣訂單）。 驗證是否已將行添加到您的銷售資料庫的 `sales_order_address`。 `sales_order_item`, `sales_order_payment` 的下界。 |

>[!WARNING]
>
>必須手動備份另外兩個資料庫實例。 Commerce只備份主資料庫實例。 的 [`magento setup:backup --db`](../../installation/tutorials/backup.md) 命令和管理選項不備份其他表。
