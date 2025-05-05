---
title: 升級資料庫結構和資料
description: 請依照下列步驟升級Adobe Commerce資料庫架構。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# 升級資料庫結構和資料

使用此命令之前，您必須[安裝應用程式](../advanced.md)。

## 升級資料庫結構和資料

每當您執行導致資料庫綱要或資料變更的動作時，都必須執行本節中討論的命令來更新它們。 原因的部分清單如下：

* 您使用命令列升級應用程式
* 您使用命令列安裝或更新元件
* 您使用命令列來啟用或停用元件

>[!NOTE]
>
>*元件*&#x200B;可以是模組、佈景主題或語言套件；元件是否來自Commerce Marketplace並不重要。

1. 開始升級：

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   其中`--keep-generated`是不更新[靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md)的可選引數。 此選用引數僅供經驗豐富的系統整合經銷商在有限的情況下使用&#x200B;*之*。 在[生產模式](../../configuration/bootstrap/application-modes.md#production-mode)中只應使用&#x200B;*1&rbrace;。*&#x200B;它應該&#x200B;*不*&#x200B;用於[開發人員模式](../../configuration/bootstrap/application-modes.md#developer-mode)。

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```
