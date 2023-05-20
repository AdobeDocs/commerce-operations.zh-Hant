---
title: 開發系統設定
description: 瞭解如何為Commerce應用程式建立開發系統。
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 開發系統設定

您可以擁有任意數量的開發系統，但前提是所有開發系統都符合以下條件：

- 它們都運行Commerce 2.2或更高版本
- 所有Commerce代碼都與生成和生產系統位於同一儲存庫中受原始碼管理
- 每個開發系統都應使用 [預設模式](../bootstrap/application-modes.md#default-mode) 或 [開發者模式](../bootstrap/application-modes.md#developer-mode)
- 它具有檔案系統所有權和權限集，如中所述 [開發、構建和生產系統的先決條件](../deployment/technical-details.md)。
- 確保以下所有內容 _排除_ 從原始碼管理：

   - `vendor` 目錄（和子目錄）
   - `generated` 目錄（和子目錄）
   - `pub/static` 目錄（和子目錄）
   - `app/etc/env.php` 檔案

- 確保 `app/etc/config.php` 是 _包括_ 在源控制項中

如果你使用Git `.gitignore` 檔案提供了前面的大部分內容。 查看 [`.gitignore` 參考](../reference/config-reference-gitignore.md)。
