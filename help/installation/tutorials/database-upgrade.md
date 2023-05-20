---
title: 升級資料庫架構和資料
description: 按照以下步驟升級您的Adobe Commerce或Magento Open Source資料庫架構。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 升級資料庫架構和資料

使用此命令之前，必須 [安裝應用程式](../advanced.md)。

## 升級資料庫架構和資料

每當執行導致資料庫架構或資料更改的操作時，必須運行本節中討論的命令來更新它們。 以下是部分原因：

* 您使用命令行升級了應用程式
* 使用命令行安裝或更新元件
* 您使用命令行啟用或禁用元件

>[!NOTE]
>
>A *元件* 可以是模組、主題或語言包；元件是否來自Commerce Marketplace並不重要。

1. 啟動升級：

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   位置 `--keep-generated` 是不更新的可選參數 [靜態視圖檔案](../../configuration/cli/static-view-file-deployment.md)。 此可選參數供使用 *僅* 在有限的情況下，由經驗豐富的系統整合商提供。 應使用 *僅* 在 [生產模式](../../configuration/bootstrap/application-modes.md#production-mode)。 應該 *不* 用於 [開發者模式](../../configuration/bootstrap/application-modes.md#developer-mode)。

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```
