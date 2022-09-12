---
title: 檔案系統訪問權限
description: 請參閱如何為開發和生產系統設定商務應用程式檔案系統的擁有者或擁有者。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---


# 檔案系統訪問權限

本節討論如何為開發和生產系統設定商務檔案系統的所有者或所有者。 繼續之前，請先檢閱 [檔案系統所有權和權限概述](../../installation/prerequisites/file-system/overview.md).

本主題著重於商務開發與生產系統。 如果您要安裝商務，請參閱 [設定安裝前的所有權和權限](../../installation/prerequisites/file-system/configure-permissions.md).

下面的部分討論了一兩個檔案系統所有者的要求。 這意味著：

- **一個使用者** — 通常在共用托管提供程式上是必要的，這允許您僅訪問伺服器上的一個用戶。此用戶可以登錄、使用FTP傳輸檔案，並且此用戶也運行Web伺服器。

- **兩個使用者** — 如果您執行自己的Commerce伺服器，建議使用兩個使用者：一個用於傳輸檔案並運行命令行實用程式，另一個用於web伺服器軟體的用戶。 如果可能，這較好，因為更安全。

   而是您有不同的使用者：

   - Web伺服器用戶，運行管理和店面。

   - A _命令行用戶_，此帳戶是您可用來登入伺服器的本機使用者帳戶。 此用戶運行Commerce cron作業和命令行實用程式。

## 用於共用托管的生產檔案系統所有權（一個用戶）

若要使用單一擁有者設定，您必須以執行Web伺服器的相同使用者身分登入您的商務伺服器。 這是共用托管的典型作法。

因為有一個檔案系統擁有者的安全性較差，我們建議您盡可能將商務部署在生產環境中的私人伺服器上，而非共用托管上。

### 為預設或開發人員模式設定一個擁有者

在預設或開發人員模式下，用戶必須可寫入以下目錄：

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

您可以使用共用托管提供者提供的命令列或檔案管理程式應用程式來設定這些權限。

### 為生產模式設定一個所有者

準備好將網站部署到生產環境時，您應從下列目錄中的檔案中移除寫入存取權，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

要更新元件、安裝新元件或升級商務軟體，前面所有目錄都必須讀寫。

#### 將代碼檔案和目錄設為只讀

要從Web伺服器用戶組中刪除對檔案和目錄的寫權限：

1. 登入您的Commerce伺服器。

1. 更改到Commerce安裝目錄。

1. 變更為生產模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 刪除以下目錄的寫入權限。

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. 使命令行工具可執行。

   ```bash
   chmod u+x bin/magento
   ```

#### 使代碼檔案和目錄可寫

要使檔案和目錄可寫，以便更新元件和升級商務軟體：

1. 登入您的Commerce伺服器。
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   chmod -R u+w .
   ```

### （可選）設定 `magento_umask`

請參閱 [（可選）設定調查](../../installation/next-steps/set-umask.md) 在 _安裝指南_.

## 專用托管的生產檔案系統所有權（兩名使用者）

如果您使用自己的伺服器（包括托管提供者的專用伺服器設定），則有兩個使用者：

- 此 **網站伺服器使用者**，執行管理員和店面。

   Linux系統通常不為此用戶提供外殼；您不能以Web伺服器用戶的身份或切換到Commerce伺服器。

- 此 **命令行用戶**，您可將其作為或切換登入您的Commerce伺服器。

   Commerce使用此用戶運行CLI命令和cron。

   >[!INFO]
   >
   >命令列使用者也稱為 _檔案系統所有者_.

因為這些使用者需要存取相同的檔案，建議您建立 [共用群組](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) 他們都屬於的。 以下過程假定您已完成此操作。

請參閱下列其中一節：

- 開發人員或預設模式下的兩個檔案系統所有者
- 兩個檔案系統所有者處於生產模式

### 為預設模式或開發人員模式設定兩個擁有者

以下目錄中的檔案必須在開發人員和預設模式下由用戶都可寫：

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

設定 [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) 位於目錄上，因此權限始終從父目錄繼承。

>[!INFO]
>
>`setgid` 僅應用於目錄， _not_ 檔案。

此外，目錄應由Web伺服器組可寫。 因為這些目錄中可能存在內容，所以遞回新增權限。

#### 設定權限和 `setgid`

若要設定 `setgid` 和開發人員模式的權限：

1. 以檔案系統擁有者身分登入或切換至您的Commerce伺服器。
1. 按所示順序輸入以下命令：

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 兩個檔案系統所有者處於生產模式

準備好將網站部署到生產環境時，您應從下列目錄中的檔案中移除寫入存取權，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### 將代碼檔案和目錄設為只讀

要從Web伺服器用戶組中刪除檔案和目錄的可寫權限：

1. 登入您的Commerce伺服器。
1. 更改到Commerce安裝目錄。
1. 作為檔案系統所有者，請輸入以下命令以更改為生產模式：

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 以用戶身份輸入以下命令 `root` 權限：

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### 使代碼檔案和目錄可寫

要使檔案和目錄可寫，以便更新元件和升級商務軟體：

1. 登入您的Commerce伺服器。
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
