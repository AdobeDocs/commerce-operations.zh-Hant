---
title: 顯示或更改管理URI
description: 請依照下列步驟來檢視和修改Adobe Commerce或Magento Open Source管理應用程式的URI。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# 顯示或更改管理URI

在運行此命令之前，您必須 [建立或更新部署配置](deployment.md).

## 顯示管理URI

本節討論如何使用命令行來顯示管理統一資源標識符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。

命令選項：

```bash
bin/magento info:adminuri
```

示例結果如下：

```terminal
Admin Panel URI: /admin_1wgrah
```

您也可以在 `<magento_root>/app/etc/env.php`. 程式碼片段如下：

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 變更管理URL

要更改管理URI，請使用 [`magento setup:config:set`](deployment.md) 命令。
