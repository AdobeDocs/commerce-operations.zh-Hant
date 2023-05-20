---
title: 顯示或更改管理URI
description: 按照以下步驟查看和修改您的Adobe Commerce或Magento Open Source管理應用程式的URI。
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# 顯示或更改管理URI

在運行此命令之前，必須 [建立或更新部署配置](deployment.md)。

## 顯示管理URI

本節討論如何使用命令行顯示管理統一資源標識符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。

命令選項：

```bash
bin/magento info:adminuri
```

示例結果如下：

```terminal
Admin Panel URI: /admin_1wgrah
```

您還可以在中查看管理URI `<magento_root>/app/etc/env.php`。 下面是代碼段：

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 更改管理URL

要更改管理URI，請使用 [`magento setup:config:set`](deployment.md) 的子菜單。
