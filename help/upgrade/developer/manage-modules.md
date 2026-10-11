---
title: 管理模組和擴充功能（開發人員）
description: 使用命令列介面和撰寫器套件管理員來管理Adobe Commerce模組和擴充功能。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%
---
# 管理模組和擴充功能

貢獻開發人員透過在Adobe Commerce `composer.json`檔案中指定其版本來升級模組與擴充功能。 如果您不是貢獻開發人員，請參閱[執行升級](../implementation/perform-upgrade.md)。

您可以將`require`區段新增至`composer.json`檔案，也可以使用`composer require`命令，如下所示：

{{$include /help/_includes/server-login.md}}

您有以下選項：

## 取得可用的模組版本

命令使用方式：

```shell
composer show --all <vendor>/<name>
```

例如：

```shell
composer show --all example/module
```

## 使用`composer require`命令

命令使用方式：

```shell
composer require <vendor>/<name>:<version>
```

例如：

```shell
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

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
