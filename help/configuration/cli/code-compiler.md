---
title: 代碼編譯器
description: 瞭解如何從命令行運行代碼編譯器。
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# 代碼編譯器

{{file-system-owner}}

代碼編譯包括以下內容（無特定順序）:

- 應用程式碼生成（工廠、代理）
- 區域配置聚合（每區域優化的依賴關係注入配置）
- 攔截器生成（攔截器的優化代碼生成）
- 攔截快取生成
- 儲存庫代碼生成（為API生成的代碼）
- 服務資料屬性生成（為資料對象生成的擴展類）

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

   使用 `[-c|--clear-static-content]` 選項以清除靜態內容。 如果以前已啟用或禁用了模組，並且必須清除之前為這些模組生成的靜態內容，則必須執行此操作。

   請參閱 [啟用模組](../../installation/tutorials/manage-modules.md)。

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
