---
title: 檔案所有權和權限
description: 了解使用Adobe Commerce和Magento Open Source的內部部署時，檔案系統權限的重要性。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# 檔案所有權和權限

在開發環境中保護您的Adobe Commerce或Magento Open Source安裝，有助於防止與未經授權的人員或程式存取您的系統相關的問題，並且可能對您的系統造成傷害，這一點非常重要。 使用下列檔案系統所有權和權限准則來保護您的安裝。

## 檔案系統所有者

檔案系統所有者是擁有檔案系統中檔案的寫入權限並擁有該權限的用戶。

檔案系統所有者有兩種類型：

- **與單一使用者共用托管**

   共用的托管提供程式可讓您以一個使用者身分登入應用程式伺服器。 您只要是單一使用者，即可使用FTP登入、傳輸檔案，以及執行Web伺服器。 您可以選擇設定 [`umask`](#restrict-access-with-a-umask) 以進一步限制存取，尤其是在生產環境中。

- **由兩個使用者進行私人托管**

   如果您管理應用程式伺服器，專用托管會很實用。 每個使用者都有特定的責任：

   - 此 _網站伺服器使用者_ 執行管理員和店面。

   - 此 _命令行用戶_ 運行cron作業和命令行實用程式。
   這兩個使用者對檔案系統都需要相同的權限，因此最好使用 [共用群組](configure-permissions.md#set-ownership-and-permissions-for-two-users) 並設定 [`umask`](#restrict-access-with-a-umask).

### 使用Umask限制訪問

若要加強安全性，尤其是在共用主機系統上的生產環境中，您可以使用 `umask` 限制存取。 A `umask` — 也稱為a _檔案系統建立掩碼_ — 是一組位，控制如何為新建立的檔案設定檔案權限。

>[!WARNING]
>
>檔案系統安全是複雜而重要的。 在決定要設定的權限級別之前，強烈建議您咨詢經驗豐富的系統管理員或網路管理員。 我們提供機制供您使用，但您應負責建立權限策略。

Adobe Commerce和Magento Open Source使用三位元的預設遮色片： `002`. 從UNIX預設值中減去666（檔案）和777（目錄）的預設掩碼。

例如：

- **目錄為775** — 由用戶完全控制，由組完全控制，並使每個人都能遍歷目錄。 共用托管提供者通常需要這些權限。

- **檔案為664** — 用戶可寫，組可寫，其他所有人都可只讀。

如需建立 `magento_umask` 檔案，請參閱 [設定仲裁](../../next-steps/set-umask.md).

## 權限、所有權和應用程式模式

當您使用不同的Adobe Commerce和Magento Open Source應用程式模式時，建議您使用不同的權限和所有權：

- 預設
- 開發人員
- 生產

請參閱 [關於模式](../../../configuration/bootstrap/application-modes.md) 在 _設定指南_.

我們進一步討論權限建議，於 [檔案系統訪問權限](../../../configuration/deployment/file-system-permissions.md) 在 _設定指南_.

>[!TIP]
>
>安裝Adobe Commerce或Magento Open Source之前，請檢閱 [配置檔案所有權和權限](configure-permissions.md).
