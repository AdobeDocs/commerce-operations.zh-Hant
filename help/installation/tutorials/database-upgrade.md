---
title: 升級資料庫架構和資料
description: 請依照下列步驟，升級您的Adobe Commerce或Magento Open Source資料庫架構。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# 升級資料庫架構和資料

使用此命令之前，您必須 [安裝應用程式](../advanced.md).

## 升級資料庫架構和資料

每當您執行導致 [資料庫模式](https://glossary.magento.com/database-schema) 或要更改的資料，必須運行本節中討論的命令來更新它們。 部分原因清單如下：

* 您使用命令行升級了應用程式
* 使用命令行安裝或更新元件
* 您使用命令行啟用或禁用元件

>[!NOTE]
>
>A *元件* 可以是模組、主題或語言包；元件是否來自Commerce Marketplace並不重要。

1. 開始升級：

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   其中 `--keep-generated` 是不更新的選用引數 [靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md). 此選用引數可供使用 *僅限* 在有限的情況下，由經驗豐富的系統整合商提供。 應使用 *僅限* in [生產模式](../../configuration/bootstrap/application-modes.md#production-mode). 應該 *not* 用於 [開發人員模式](../../configuration/bootstrap/application-modes.md#developer-mode).

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```
