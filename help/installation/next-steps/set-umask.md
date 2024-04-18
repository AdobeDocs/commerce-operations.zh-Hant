---
title: 設定umask （選擇性）
description: 透過限制檔案系統許可權，改善Adobe Commerce內部部署安裝的安全性狀態。
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 設定umask （選擇性）

Web伺服器群組必須具有檔案系統中特定目錄的寫入許可權；不過，您可能想要更嚴格的安全性，尤其是在生產環境中。 我們為您提供靈活性，讓您能夠使用 [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

我們的解決方案是讓您可選擇建立名為的檔案 `magento_umask` 位於應用程式根目錄中，以限制Web伺服器群組和其他人的許可權。

>[!NOTE]
>
>我們建議僅在單使用者或共用託管系統上變更umask。 如果您有私人應用程式伺服器，群組必須擁有檔案系統的寫入許可權；群組會移除群組的寫入許可權。

預設umask (不含 `magento_umask` 指定)為 `002`，這表示：

* 775用於目錄，表示使用者可完全控制、群組可完全控制，並可讓每個人周遊目錄。 共用託管提供者通常需要這些許可權。

* 664適用於檔案，這表示使用者可寫入、群組可寫入，而其他所有人則為唯讀

常見的建議是使用值 `022` 在 `magento_umask` 檔案，亦即：

* 755適用於目錄：使用者的完整控制許可權，其他所有人都可周遊目錄。
* 644適用於檔案：使用者的讀寫許可權，其他所有人設為唯讀。

要設定 `magento_umask`：

1. 在命令列終端機中，以以下身分登入您的應用程式伺服器 [檔案系統擁有者](../prerequisites/file-system/overview.md).
1. 瀏覽至應用程式安裝目錄：

   ```bash
   cd <Application install directory>
   ```

1. 使用以下命令建立名為的檔案 `magento_umask` 並撰寫 `umask` 其值。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   您現在應該要有名為的檔案 `magento_umask` 在 `<Magento install dir>` 唯一的內容為 `umask` 數字。

1. 登出並重新登入，作為 [檔案系統擁有者](../prerequisites/file-system/overview.md) 以套用變更。
