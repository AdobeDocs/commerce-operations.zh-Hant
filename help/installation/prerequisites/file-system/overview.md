---
title: 檔案擁有權和許可權
description: 瞭解使用Adobe Commerce內部部署安裝時檔案系統許可權的重要性。
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# 檔案擁有權和許可權

在開發環境中確保Adobe Commerce的安裝安全非常重要，這樣有助於防止未經授權的人員或程式存取（並可能損害）您的系統時出現問題。 請使用下列檔案系統擁有權和許可權准則來保護您的安裝。

## 檔案系統擁有者

檔案系統擁有者是擁有並保留檔案系統中檔案寫入許可權的使用者。

檔案系統擁有者有兩種型別：

- **與單一使用者共用主控**

  共用託管提供者可讓您以單一使用者身分登入應用程式伺服器。 您可以以單一使用者身分登入、使用FTP傳輸檔案以及執行網頁伺服器。 您可以選擇設定[`umask`](#restrict-access-with-a-umask)來進一步限制存取，尤其是在生產環境中。

- **與兩個使用者進行私人託管**

  如果您管理應用程式伺服器，私人託管會很有用。 每個使用者都有特定的職責：

   - _網頁伺服器使用者_&#x200B;執行管理員和店面。

   - _命令列使用者_&#x200B;執行cron作業和命令列公用程式。

  兩個使用者都需要相同的檔案系統許可權，因此最好使用[共用群組](configure-permissions.md#set-ownership-and-permissions-for-two-users)並設定[`umask`](#restrict-access-with-a-umask)。

### 使用umask限制存取

若要加強安全性，尤其是在共用託管系統上的生產環境中，您可以使用`umask`來限制存取。 `umask` （也稱為&#x200B;_檔案系統建立遮罩_）是一組位元，可控制如何為新建立的檔案設定檔案許可權。

>[!WARNING]
>
>檔案系統安全性既複雜又重要。 強烈建議您在決定要設定的許可權層級之前，先洽詢經驗豐富的系統管理員或網路管理員。 我們提供您可使用的機制，但建立許可權策略是您的責任。

Adobe Commerce使用三位元預設遮罩： `002`。 從UNIX預設值（檔案為666，目錄為777）中減去預設遮色片。

例如：

- 目錄&#x200B;**的** 775 — 由使用者完全控制，由群組完全控制，並讓每個人都能周遊目錄。 共用託管提供者通常需要這些許可權。

- **664適用於檔案** — 使用者可寫入、群組可寫入，其他所有人則為唯讀。

如需建立`magento_umask`檔案的詳細資訊，請參閱[設定umask](../../next-steps/set-umask.md)。

## 許可權、擁有權和應用程式模式

建議您在使用不同的Adobe Commerce應用程式模式時，使用不同的許可權和擁有權：

- 預設
- 開發人員
- 生產

請參閱&#x200B;_組態指南_&#x200B;中的[關於模式](../../../configuration/bootstrap/application-modes.md)。

我們在&#x200B;_設定指南_&#x200B;的[檔案系統存取許可權](../../../configuration/deployment/file-system-permissions.md)中進一步討論許可權建議。

>[!TIP]
>
>安裝Adobe Commerce之前，請檢閱[設定檔案擁有權和許可權](configure-permissions.md)。
