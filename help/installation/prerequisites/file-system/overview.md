---
title: 檔案所有權和權限
description: 瞭解在處理Adobe Commerce和Magento Open Source的內部安裝時檔案系統權限的重要性。
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 檔案所有權和權限

在開發環境中保護您的Adobe Commerce或Magento Open Source安裝，以幫助防止與未經授權的人員或過程訪問您的系統相關的問題，這一點非常重要。 使用以下檔案系統所有權和權限准則來保護安裝。

## 檔案系統所有者

檔案系統所有者是擁有並持有對檔案系統中檔案的寫入權限的用戶。

檔案系統所有者有兩種類型：

- **與單個用戶共用主機**

   共用主機提供程式使您能夠以一個用戶身份登錄到應用程式伺服器。 作為單個用戶，您可以使用FTP登錄、傳輸檔案並運行Web伺服器。 您可以選擇設定 [`umask`](#restrict-access-with-a-umask) 進一步限制訪問，特別是在生產環境中。

- **具有兩個用戶的私有主機**

   管理應用程式伺服器時，專用主機服務非常有用。 每個用戶都有特定的責任：

   - 的 _Web伺服器用戶_ 運行管理員和店面。

   - 的 _命令行用戶_ 運行cron作業和命令行實用程式。
   兩個用戶對檔案系統的權限相同，因此最好使用 [共用組](configure-permissions.md#set-ownership-and-permissions-for-two-users) 並設定 [`umask`](#restrict-access-with-a-umask)。

### 使用umask限制訪問

要加強安全性，特別是在共用主機系統上的生產環境中，您可以使用 `umask` 限制訪問。 A `umask` — 也稱為a _檔案系統建立掩碼_ — 是一組位，用於控制如何為新建立的檔案設定檔案權限。

>[!WARNING]
>
>檔案系統的安全性是複雜和重要的。 我們強烈建議您在確定要設定的權限級別之前，先咨詢有經驗的系統管理員或網路管理員。 我們為您提供了使用機制，但建立權限策略是您的責任。

Adobe Commerce和Magento Open Source使用三位預設掩碼： `002`。 從UNIX的檔案預設值666和目錄預設值777中減去預設掩碼。

例如：

- **目錄775** — 用戶的完全控制、組的完全控制，並使每個人都能夠遍歷目錄。 這些權限通常是共用主機提供程式所必需的。

- **檔案664** — 用戶可寫，組可寫，其他所有人只讀。

有關建立的詳細資訊 `magento_umask` 檔案，請參閱 [設定umask](../../next-steps/set-umask.md)。

## 權限、所有權和應用程式模式

當您使用不同的Adobe Commerce和Magento Open Source應用模式時，我們建議您使用不同的權限和所有權：

- 預設
- 開發人員
- 生產

請參閱 [關於模式](../../../configuration/bootstrap/application-modes.md) 的 _配置指南_。

我們將在中進一步討論權限建議 [檔案系統訪問權限](../../../configuration/deployment/file-system-permissions.md) 的 _配置指南_。

>[!TIP]
>
>在安裝Adobe Commerce或Magento Open Source之前，請查看 [配置檔案所有權和權限](configure-permissions.md)。
