---
title: 管理模組和擴充功能
description: 使用命令列介面和撰寫器套件管理器管理Adobe Commerce和Magento Open Source模組及擴充功能。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# 管理模組和擴充功能

貢獻開發人員可在Adobe Commerce或Magento Open Source中指定其版本，以升級模組和擴充功能 `composer.json` 檔案。 如果您不是貢獻開發人員，請參閱 [執行升級](../implementation/perform-upgrade.md).

您可以新增 `require` 區段 `composer.json` 檔案，或使用 `composer require` 命令，如下所示：

1. 登入您的伺服器。
1. 切換至 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 更改到克隆應用程式的目錄。 例如，

   ```bash
   cd /var/www/magento2
   ```

您有下列選項：

## 取得可用模組版本

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

等待撰寫器更新相依性並安裝模組。

## 新增 `require` composer.json檔案的區段

1. 開啟 `composer.json` 在文字編輯器中。

1. 新增 `require` 區段。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 將變更儲存至 `composer.json` 檔案，然後退出文字編輯器。

1. 解析相依性，並將確切的版本寫入 `composer.lock` 檔案。

   ```bash
   composer update
   ```
