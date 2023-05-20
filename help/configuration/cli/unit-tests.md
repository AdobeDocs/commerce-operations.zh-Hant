---
title: 運行單位test
description: 運行在Adobe Commerce代碼庫中定義的單位test。
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 運行單位test

{{file-system-owner}}

此命令運行在Commerce 2代碼庫中定義的一組test。 您可以運行所有選擇的test或test。 只要指定了不受支援的類型，程式就會終止並列出所有可用類型。 執行後，將顯示一個詳細報告，顯示test運行和結果。

## 先決條件

在運行此命令之前，請執行以下操作 _必須_ 是真的：

- 的 `Magento_Developer` 必須啟用模組。 您可以按如下方式啟用它：

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   使用 `--force` 選項。

- 必須設定系統以運行所需的test。

例如，要運行整合test，應複製 `dev/tests/integration/etc/install-config-mysql.php.dist` 至 `dev/tests/integration/etc/install-config-mysql.php` 並修改它以適應您的環境。

## 運行test

命令用法：

```bash
bin/magento dev:tests:run <test>
```

要列出可用test類型：

```bash
bin/magento dev:tests:run --help
```

示例返回：

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

例如，要運行整合test:

```bash
bin/magento dev:tests:run integration
```
