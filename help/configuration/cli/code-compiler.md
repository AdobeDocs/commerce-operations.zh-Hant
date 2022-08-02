---
title: 代碼編譯器
description: 瞭解如何從命令行運行代碼編譯器。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# 代碼編譯器

{{file-system-owner}}

代碼編譯包括以下內容（無特定順序）:

- 應用程式碼生成（工廠、代理）
- 區域配置聚合（已優化） [依賴注入](https://glossary.magento.com/dependency-injection) 每個區域的配置)
- 攔截器生成（攔截器的優化代碼生成）
- 攔截快取生成
- 儲存庫代碼生成（為API生成的代碼）
- 生成服務資料屬性 [擴展](https://glossary.magento.com/extension) 資料對象的類

可以在 [\Magento\Setup\Module\Di\App\Task\Operation][operation] 命名空間。

要運行單租戶編譯器：

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

要在安裝Commerce應用程式之前編譯代碼，請執行以下操作：

在某些情況下，在安裝Commerce應用程式之前，可能需要編譯代碼。

1. 啟用模組。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   使用 `[-c|--clear-static-content]` 選項清除 [靜態內容](https://glossary.magento.com/static-content)。 如果以前已啟用或禁用了模組，並且必須清除之前為這些模組生成的靜態內容，則必須執行此操作。

   請參閱 [啟用模組](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html)。

1. 編譯代碼。

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

要編譯沒有資料庫的代碼，請參見 [部署靜態視圖檔案而不安裝Magento](../cli/static-view-file-deployment.md)。

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
