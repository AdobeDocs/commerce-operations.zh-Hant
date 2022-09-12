---
title: 設定摘要（選用）
description: 限制檔案系統權限，以改善Adobe Commerce或Magento Open Source內部部署的安全狀態。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# 設定摘要（選用）

Web伺服器組必須具有對檔案系統中某些目錄的寫入權限；不過，您可能想要更嚴格的安全性，特別是在生產環境中。 我們提供彈性，讓您能使用 [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

我們的解決方案是讓您可選擇建立名為 `magento_umask` 在應用程式根目錄中，該目錄會限制Web伺服器組和其他所有人的權限。

>[!NOTE]
>
>我們建議僅變更單一使用者或共用托管系統上的仲裁。 如果您有專用應用伺服器，則組必須具有對檔案系統的寫訪問權限；umask會從組中刪除寫訪問權限。

預設值（無） `magento_umask` 指定) `002`，這表示：

* 775用於目錄，這表示用戶完全控制，組完全控制，並使每個人都能遍歷目錄。 共用托管提供者通常需要這些權限。

* 檔案為664，這表示用戶可寫，組可寫，其他所有人可只讀

常見的建議是使用 `022` 在 `magento_umask` 檔案，其意思是：

* 目錄為755:完全控制用戶，其他所有人都可以遍歷目錄。
* 644:使用者的讀寫權限，其他人則為唯讀權限。

若要設定 `magento_umask`:

1. 在命令列終端機中，以 [檔案系統所有者](../prerequisites/file-system/overview.md).
1. 導航到應用程式安裝目錄：

   ```bash
   cd <Application install directory>
   ```

1. 使用以下命令建立名為 `magento_umask` 寫 `umask` 值。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   您現在應該有一個檔案，名為 `magento_umask` 在 `<Magento install dir>` 唯一的內容是 `umask` 數字。

1. 登出並重新登入為 [檔案系統所有者](../prerequisites/file-system/overview.md) 來套用變更。
