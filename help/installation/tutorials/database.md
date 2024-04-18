---
title: 建立資料庫綱要
description: 請依照下列步驟，為您的Adobe Commerce專案建立資料庫。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# 建立資料庫綱要

執行此命令之前，您必須 [建立或更新部署設定](deployment.md).

## 設定資料庫並新增資料

命令使用方式：

```bash
bin/magento setup:db-schema:upgrade
```

若要檢視資料庫的狀態，請輸入

```bash
bin/magento setup:db:status
```
