---
title: 建立資料庫綱要
description: 請依照下列步驟，為您的Adobe Commerce專案建立資料庫。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# 建立資料庫綱要

執行此命令之前，您必須[建立或更新部署組態](deployment.md)。

## 設定資料庫並新增資料

命令使用方式：

```shell
bin/magento setup:db-schema:upgrade
```

若要檢視資料庫的狀態，請輸入

```shell
bin/magento setup:db:status
```
