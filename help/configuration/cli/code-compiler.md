---
title: 代碼編譯器
description: 了解如何從命令列執行程式碼編譯器。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# 代碼編譯器

{{file-system-owner}}

程式碼編譯包含下列項目（無特定順序）:

- 應用程式代碼生成（工廠、代理）
- 區域配置聚合（每區域優化的依賴注入配置）
- 攔截器生成（攔截器優化代碼生成）
- 偵聽快取生成
- 存放庫程式碼產生（為API產生的程式碼）
- 服務資料屬性生成（為資料對象生成的擴展類）

您可以在 [\Magento\Setup\Module\Di\App\Task\Operation][operation] 命名空間。

要運行單租戶編譯器：

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

要在安裝Commerce應用程式之前編譯代碼，請執行以下操作：

在某些情況下，您可能需要在安裝商務應用程式之前編譯代碼。

1. 啟用模組。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   使用 `[-c|--clear-static-content]` 選項來清除靜態內容。 如果您先前已啟用或停用模組，且您必須清除先前為其產生的靜態內容，則此為必要操作。

   請參閱 [啟用模組](../../installation/tutorials/manage-modules.md).

1. 編譯程式碼。

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

要編譯不使用資料庫的代碼，請參見 [部署靜態視圖檔案，而不安裝Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
