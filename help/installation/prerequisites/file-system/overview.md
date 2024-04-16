---
title: 檔案擁有權和許可權
description: 瞭解使用Adobe Commerce內部部署安裝時檔案系統許可權的重要性。
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 檔案擁有權和許可權

在開發環境中確保您的Adobe Commerce或Magento Open Source安裝安全，以協助防止與未授權人員或程式存取（並可能傷害）您的系統相關的問題，這點很重要。 請使用下列檔案系統擁有權和許可權准則來保護您的安裝。

## 檔案系統擁有者

檔案系統擁有者是擁有並保留檔案系統中檔案寫入許可權的使用者。

檔案系統擁有者有兩種型別：

- **與單一使用者共用託管**

  共用託管提供者可讓您以單一使用者身分登入應用程式伺服器。 您可以以單一使用者身分登入、使用FTP傳輸檔案以及執行網頁伺服器。 您可以選擇設定 [`umask`](#restrict-access-with-a-umask) 以進一步限制存取，尤其是在生產環境中。

- **兩個使用者的私人託管**

  如果您管理應用程式伺服器，私人託管會很有用。 每個使用者都有特定的職責：

   - 此 _Web伺服器使用者_ 執行管理員和店面。

   - 此 _命令列使用者_ 執行cron作業和命令列公用程式。

  兩位使用者都需要相同的檔案系統許可權，因此最好使用 [共用群組](configure-permissions.md#set-ownership-and-permissions-for-two-users) 並設定 [`umask`](#restrict-access-with-a-umask).

### 使用umask限制存取

若要加強安全性，尤其是在共用託管系統的生產環境中，您可以使用 `umask` 以限制存取。 A `umask` — 也稱為 _檔案系統建立遮罩_ — 是一組位元，可控制如何為新建立的檔案設定檔案許可權。

>[!WARNING]
>
>檔案系統安全性既複雜又重要。 強烈建議您在決定要設定的許可權層級之前，先洽詢經驗豐富的系統管理員或網路管理員。 我們提供您可使用的機制，但建立許可權策略是您的責任。

Adobe Commerce使用三位元預設遮罩： `002`. 從UNIX預設值（檔案為666，目錄為777）中減去預設遮色片。

例如：

- **775用於目錄** — 使用者可完全控制，群組可完全控制，且所有人都能周遊目錄。 共用託管提供者通常需要這些許可權。

- **檔案為664** — 使用者可寫入、群組可寫入，其他使用者皆為唯讀。

如需關於建立 `magento_umask` 檔案，請參閱 [設定umask](../../next-steps/set-umask.md).

## 許可權、擁有權和應用程式模式

建議您在使用不同的Adobe Commerce應用程式模式時，使用不同的許可權和擁有權：

- 預設
- 開發人員
- 生產

另請參閱 [關於模式](../../../configuration/bootstrap/application-modes.md) 在 _設定指南_.

我們將在中進一步討論許可權建議 [檔案系統存取許可權](../../../configuration/deployment/file-system-permissions.md) 在 _設定指南_.

>[!TIP]
>
>安裝Adobe Commerce或Magento Open Source之前，請先檢閱 [設定檔案擁有權和許可權](configure-permissions.md).
