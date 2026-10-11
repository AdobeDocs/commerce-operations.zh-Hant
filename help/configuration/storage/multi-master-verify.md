---
title: 驗證分割資料庫
description: 瞭解如何驗證Commerce分割資料庫設定是否正常運作。
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
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
source-wordcount: '155'
ht-degree: 0%
---
# 驗證分割資料庫

{{ee-only}}

{{deprecate-split-db}}

組態之後，主要資料庫的設定如下：

- 主要Commerce資料庫： 369個表格
- Commerce報價資料庫： 11個表格
- Commerce銷售資料庫：55個資料表

若要驗證分割資料庫是否正常運作，請執行以下工作，並使用如[phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin)的資料庫工具，驗證資料是否已新增至資料庫表格：

| 要驗證的內容 | 如何驗證 |
| -------------- | ------------- |
| 報價資料庫正在運作 | 將專案新增至購物車。 確認已將資料列新增至報價資料庫的`quote`、`quote_address`和`quote_item`資料表。 |
| 銷售資料庫運作中 | 完成訂單（任何付款方式，包括支票/匯票）。 確認資料列已新增至銷售資料庫的`sales_order_address`、`sales_order_item`和`sales_order_payment`資料表。 |

>[!WARNING]
>
>您必須手動備份另外兩個資料庫執行處理。 Commerce僅備份主要資料庫執行個體。 [`magento setup:backup --db`](../../installation/tutorials/backup.md)命令和Admin選項不會備份其他表格。
