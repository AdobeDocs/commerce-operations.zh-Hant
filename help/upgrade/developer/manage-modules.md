---
title: 管理模組和擴充功能（開發人員）
description: 使用命令列介面和撰寫器套件管理員來管理Adobe Commerce模組和擴充功能。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# 管理模組和擴充功能

貢獻開發人員透過在Adobe Commerce `composer.json`檔案中指定其版本來升級模組與擴充功能。 如果您不是貢獻開發人員，請參閱[執行升級](../implementation/perform-upgrade.md)。

您可以將`require`區段新增至`composer.json`檔案，也可以使用`composer require`命令，如下所示：

{{$include /help/_includes/server-login.md}}

您有以下選項：

## 取得可用的模組版本

命令使用方式：

```bash
composer show --all <vendor>/<name>
```

例如：

```bash
composer show --all example/module
```

## 使用`composer require`命令

命令使用方式：

```bash
composer require <vendor>/<name>:<version>
```

例如：

```bash
composer require example/module:1.0.0
```

Composer正在更新相依性並安裝模組，請稍候。

## 將`require`區段新增至composer.json檔案

1. 在文字編輯器中開啟`composer.json`。

1. 新增`require`區段。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 儲存您對`composer.json`檔案所做的變更，並結束文字編輯器。

1. 解決相依性並將確切版本寫入`composer.lock`檔案。

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
