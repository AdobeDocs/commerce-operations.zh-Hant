---
title: 執行單元測試
description: 執行Adobe Commerce程式碼庫中定義的單元測試。
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# 執行單元測試

{{file-system-owner}}

此命令會執行Commerce 2程式碼庫中定義的一組測試。 您可以執行所有測試或您選取的測試。 每當指定不支援的型別時，程式就會終止並列出所有可用的型別。 執行後，詳細報告隨即顯示，顯示測試回合和結果。

## 先決條件

執行此命令之前，下列&#x200B;_必須_&#x200B;為true：

- 必須啟用`Magento_Developer`模組。 您可以依照以下方式啟用它：

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  只有在必要時才使用`--force`選項。

- 您的系統必須設定為執行所需的測試。

例如，若要執行整合測試，您應該將`dev/tests/integration/etc/install-config-mysql.php.dist`複製到`dev/tests/integration/etc/install-config-mysql.php`，並修改它以符合您的環境。

## 正在執行測試

命令使用方式：

```bash
bin/magento dev:tests:run <test>
```

列出可用的測試型別：

```bash
bin/magento dev:tests:run --help
```

範例傳回：

```
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

例如，若要執行整合測試：

```bash
bin/magento dev:tests:run integration
```
