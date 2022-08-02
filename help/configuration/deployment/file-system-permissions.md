---
title: 檔案系統訪問權限
description: 請參閱如何為開發和生產系統設定Commerce應用程式檔案系統的所有者或所有者。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# 檔案系統訪問權限

本節討論如何為開發和生產系統設定Commerce檔案系統的所有者或所有者。 在繼續之前，請查看中討論的概念 [檔案系統所有權和權限概述](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。

本主題側重於商業開發和生產系統。 如果要安裝Commerce，請參閱 [設定預安裝所有權和權限](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html)。

下面的部分討論一兩個檔案系統所有者的要求。 這意味著：

- **一個用戶** — 通常，在共用主機提供程式上是必需的，這允許您只訪問伺服器上的一個用戶。此用戶可以使用FTP登錄、傳輸檔案，並且此用戶還運行Web伺服器。

- **兩個用戶** — 如果您運行自己的Commerce伺服器，我們建議兩個用戶：一個用於傳輸檔案並運行命令行實用程式，另一個用於web伺服器軟體。 在可能的情況下，這更可取，因為它更安全。

   相反，您有不同的用戶：

   - 運行Admin和storefront的Web伺服器用戶。

   - A _命令行用戶_，這是一個本地用戶帳戶，可用於登錄到伺服器。 此用戶運行Commerce cron作業和命令行實用程式。

## 用於共用主機的生產檔案系統所有權（一個用戶）

要使用單所有者設定，您必須以運行Web伺服器的同一用戶身份登錄到Commerce伺服器。 這是共用托管的典型操作。

由於擁有一個檔案系統所有者的安全性較差，因此建議您在生產環境中部署Commerce，而不是在共用主機上部署（如果可能）。

### 為預設或開發人員模式設定一個所有者

在預設或開發模式下，用戶必須可寫下列目錄：

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

您可以使用共用主機提供程式提供的命令行或檔案管理器應用程式設定這些權限。

### 為生產模式設定一個所有者

當您準備將站點部署到生產環境時，應從以下目錄中的檔案中刪除寫訪問權限，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

要更新元件、安裝新元件或升級Commerce軟體，前面的所有目錄都必須是讀寫目錄。

#### 使代碼檔案和目錄為只讀

要從Web伺服器用戶組中刪除對檔案和目錄的寫入權限：

1. 登錄到Commerce伺服器。

1. 更改到Commerce安裝目錄。

1. 更改為生產模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 刪除對以下目錄的寫入權限。

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. 使命令行工具可執行。

   ```bash
   chmod u+x bin/magento
   ```

#### 使代碼檔案和目錄可寫

要使檔案和目錄可寫，以便您可以更新元件和升級Commerce軟體：

1. 登錄到Commerce伺服器。
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   chmod -R u+w .
   ```

### （可選）設定 `magento_umask`

請參閱 [（可選）設定umask](https://devdocs.magento.com/guides/v2.4/install-gde/install/post-install-umask.html) 的 _安裝指南_。

## 專用主機（兩個用戶）的生產檔案系統所有權

如果您使用自己的伺服器（包括主機提供商的專用伺服器設定），則有兩個用戶：

- 的 **Web伺服器用戶**，運行管理和店面。

   Linux系統通常不為此用戶提供Shell;您不能以Web伺服器用戶身份或切換到Commerce伺服器。

- 的 **命令行用戶**，您將其作為或切換到登錄到Commerce伺服器。

   Commerce使用此用戶運行CLI命令和cron。

   >[!INFO]
   >
   >命令行用戶也稱為 _檔案系統所有者_。

由於這些用戶需要訪問相同的檔案，因此建議您建立 [共用組](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html#mage-owner-about-group) 他們都屬於的。 以下過程假定您已經完成此操作。

請參閱以下部分之一：

- 開發人員或預設模式下的兩個檔案系統所有者
- 兩個檔案系統所有者處於生產模式

### 為預設或開發者模式設定兩個所有者

以下目錄中的檔案必須由開發人員和預設模式下的用戶都可寫：

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

設定 [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) 位於目錄上，因此權限始終從父目錄繼承。

>[!INFO]
>
>`setgid` 僅應用於目錄， _不_ 到D3

此外，目錄應由Web伺服器組可寫。 由於這些目錄中可能存在內容，因此以遞歸方式添加權限。

#### 設定權限和 `setgid`

設定 `setgid` 和開發人員模式的權限：

1. 以檔案系統所有者身份或切換到檔案系統所有者身份登錄到Commerce伺服器。
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

當您準備將站點部署到生產環境時，應從以下目錄中的檔案中刪除寫訪問權限，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### 使代碼檔案和目錄為只讀

要從Web伺服器用戶組中刪除對檔案和目錄的可寫權限：

1. 登錄到Commerce伺服器。
1. 更改到Commerce安裝目錄。
1. 作為檔案系統所有者，輸入以下命令以更改為生產模式：

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 以用戶身份輸入以下命令 `root` 權限：

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### 使代碼檔案和目錄可寫

要使檔案和目錄可寫，以便您可以更新元件和升級Commerce軟體：

1. 登錄到Commerce伺服器。
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
