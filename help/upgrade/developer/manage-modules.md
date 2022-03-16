---
title: 管理模組和擴展
description: 使用命令行介面和Composer包管理器管理Adobe Commerce和Magento Open Source模組及擴展。
source-git-commit: 7bcfbc4483f4b6d4c1a5e852adbd1cd81bc136b7
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 2%

---


# 管理模組和擴展

派遣開發人員通過在Adobe Commerce或Magento Open Source中指定其版本來升級模組和擴展 `composer.json` 的子菜單。 如果您不是派遣開發人員，請參閱 [執行升級](../implementation/perform-upgrade.md)。

可以添加 `require` 的 `composer.json` 檔案，或 `composer require` 命令，如下所示：

{{$include /help/_includes/server-login.md}

您有以下選項：

## 獲取可用模組版本

命令用法：

```bash
composer show --all <vendor>/<name>
```

例如：

```bash
composer show --all example/module
```

## 使用 `composer require` 命令

命令用法：

```bash
composer require <vendor>/<name>:<version>
```

例如：

```bash
composer require example/module:1.0.0
```

Composer正在更新依賴項並安裝模組，請稍候。

## 添加 `require` composer.json檔案的部分

1. 開啟 `composer.json` 的子菜單。

1. 添加 `require` 的子菜單。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 保存對 `composer.json` 並退出文本編輯器。

1. 解決依賴項，並將精確版本寫入 `composer.lock` 的子菜單。

   ```bash
   composer update
   ```
