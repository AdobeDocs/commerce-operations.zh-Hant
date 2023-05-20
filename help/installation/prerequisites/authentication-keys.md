---
title: 獲取您的身份驗證密鑰
description: 按照以下步驟檢索憑據以訪問repo.magento.com上的Adobe Commerce和Magento Open Source作曲家包。
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# 獲取您的身份驗證密鑰

的 `repo.magento.com` 儲存庫是儲存Adobe Commerce和Magento Open Source及第三方Composer軟體包並需要身份驗證的位置。 使用Commerce Marketplace帳戶生成一對32個字元 *身份驗證密鑰* 訪問儲存庫。

要獲得對Adobe Commerce和Magento Open Source包的訪問權限，必須使用與已授予對這些包訪問權限的MAGEID關聯的密鑰。 MAGEID通常是Adobe Commerce帳戶上的主要聯繫人，並且可能並不總是Adobe Commerce雲基礎架構項目的項目所有者。

>[!TIP]
>
>如果遇到 [錯誤](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)，您可能沒有訪問包的授權，或者訪問權限由於帳戶上的未清發票而已過期。
>
>* 如果您是帳戶上的主要聯繫人，請確保帳戶上沒有列出未清發票。
>* 如果主要聯繫人提供的鍵無效且帳戶上沒有未清發票，請聯繫 [Adobe Commerce支援](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 使用主要聯繫人的MAGEID獲得幫助。


要建立驗證密鑰：

1. 登錄到 [Commerce Marketplace](https://marketplace.magento.com)。 如果您沒有帳戶，請按一下 **註冊**。
1. 按一下頁面右上角的帳戶名並選擇 **我的個人資料**。

1. 按一下 **訪問密鑰** 的子菜單。

   ![獲取安全訪問密鑰，Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. 按一下 **建立新訪問密鑰**。 輸入密鑰的特定名稱（例如，接收密鑰的開發人員的名稱），然後按一下 **確定**。

1. 新的公鑰和私鑰現在與您的帳戶相關聯，您可以按一下該帳戶進行複製。 使用項目時保存此資訊或保持頁面開啟。 使用 **公鑰** 以及 **私鑰** 密碼。

## 管理您的身份驗證密鑰

您也可以禁用或刪除驗證密鑰。 例如，出於安全原因，您可以在某人離開您的組織後禁用或刪除密鑰。

* 禁用鍵：按一下 **禁用**。 如果要暫停使用密鑰，可以執行此操作。
* 要啟用以前禁用的密鑰，請執行以下操作：按一下 **啟用**。
* 要刪除鍵：按一下 **刪除**。

### 管理SSH訪問令牌

要使用SSH下載Adobe Commerce版本，必須生成下載訪問令牌。 要生成令牌：

1. 登錄到 [magento.com帳戶](https://account.magento.com/customer/account/login)。
1. 按一下 **我的帳戶** 頁面頂部。
1. 按一下 **帳戶設定** > **下載訪問令牌**。

   ![訪問您的密鑰](../../assets/installation/connect_keys1.png)

1. 按一下 **生成新令牌** 替換和禁用現有標籤。

您必須使用MAGEID加令牌來下載版本。 您的MAGEID顯示在帳戶頁面的左上角。

例如：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

使用您的身份驗證密鑰：

* [獲取元包（積分器、打包器）](../composer.md)
* [克隆GitHub儲存庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) （僅提供開發者）
* [升級和管理模組](../../upgrade/modules/upgrade.md)
