---
title: 設定umask（可選）
description: 通過限制檔案系統權限來改善Adobe Commerce或Magento Open Source本地安裝的安全狀態。
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 設定umask（可選）

Web伺服器組必須對檔案系統中的某些目錄具有寫權限；但是，您可能需要更嚴格的安全性，尤其是在生產方面。 我們為您提供了進一步限制這些權限的靈活性 [umask(](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)。

我們的解決方案是使您可以選擇建立名為 `magento_umask` 在應用程式根目錄中，該目錄限制Web伺服器組和其他所有人的權限。

>[!NOTE]
>
>我們建議僅更改單用戶或共用主機系統上的umask。 如果您有專用應用伺服器，則組必須具有對檔案系統的寫訪問權限；umask從組中刪除寫訪問權限。

預設umask（無） `magento_umask` 指定) `002`，即：

* 775，表示用戶完全控制，組完全控制，並使每個人都能夠遍歷目錄。 這些權限通常是共用主機提供程式所必需的。

* 664，表示用戶可寫，組可寫，其他所有人只讀

一個常見建議是使用 `022` 的 `magento_umask` 檔案，即：

* 目錄755:完全控制用戶，其他人可以遍歷目錄。
* 檔案644:用戶的讀寫權限，以及其他人的只讀權限。

設定 `magento_umask`:

1. 在命令行終端中，以 [檔案系統所有者](../prerequisites/file-system/overview.md)。
1. 導航到應用程式安裝目錄：

   ```bash
   cd <Application install directory>
   ```

1. 使用以下命令建立名為 `magento_umask` 寫下 `umask` 值得。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   您現在應該有一個名為 `magento_umask` 的 `<Magento install dir>` 唯一的內容是 `umask` 數。

1. 註銷並以 [檔案系統所有者](../prerequisites/file-system/overview.md) 按鈕。
