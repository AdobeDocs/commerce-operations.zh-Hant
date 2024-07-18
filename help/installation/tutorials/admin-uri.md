---
title: 顯示或變更管理員URI
description: 請依照下列步驟檢視及修改Adobe Commerce管理員應用程式的URI。
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# 顯示或變更管理員URI

執行此命令之前，您必須[建立或更新部署組態](deployment.md)。

## 顯示管理員URI

本節討論如何使用命令列來顯示Admin Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。

命令選項：

```bash
bin/magento info:adminuri
```

範例結果如下：

```
Admin Panel URI: /admin_1wgrah
```

您也可以在`<magento_root>/app/etc/env.php`中檢視管理員URI。 程式碼片段如下：

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 變更管理員URL

若要變更管理員URI，請使用[`magento setup:config:set`](deployment.md)命令。
