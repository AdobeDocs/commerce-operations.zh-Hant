---
title: 取得驗證金鑰
description: 請依照下列步驟擷取憑證，以存取repo.magento.com上的Adobe Commerce和Magento Open Source撰寫器套件。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# 取得驗證金鑰

此 `repo.magento.com` 存放庫是儲存Adobe Commerce和Magento Open Source及協力廠商撰寫器套件的位置，且需要驗證。 使用Commerce Marketplace帳戶產生一組32個字元 *驗證金鑰* 來存取存放庫。

>[!NOTE]
>
>若要取得Adobe Commerce和Magento Open Source套件的存取權限，您必須使用與已授與這些套件存取權之MAGEID相關聯的金鑰。 MAGEID通常是 **帳單聯繫人** 在Adobe Commerce賬戶上，並且不一定 **專案擁有者** Adobe Commerce雲基礎架構專案。 如果您遇到 [錯誤](https://support.magento.com/hc/en-us/articles/360040296392)，則您可能沒有存取套件的授權，或存取權限已因帳戶上的未結髮票而過期。 連絡人 [Adobe Commerce支援](https://support.magento.com/hc/en-us) 來協助你的MAGEID。

要建立驗證密鑰，請執行以下操作：

1. 登入 [Commerce Marketplace](https://marketplace.magento.com). 如果您沒有帳戶，請按一下 **註冊**.
1. 按一下頁面右上角的帳戶名稱，然後選取 **我的設定檔**.

1. 按一下 **存取金鑰** （在「市集」標籤中）。

   ![獲取安全訪問密鑰Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. 按一下 **建立新的訪問密鑰**. 輸入金鑰的特定名稱（例如，接收金鑰的開發人員的名稱），然後按一下 **確定**.

1. 新的公開金鑰和私密金鑰現在與您的帳戶相關聯，您可以按一下加以複製。 使用專案時，請儲存此資訊或保持頁面開啟。 使用 **公開金鑰** 作為您的使用者名稱， **私密金鑰** 密碼。

## 管理驗證金鑰

您也可以停用或刪除驗證金鑰。 例如，您可以在某人離開您的組織後，基於安全原因停用或刪除金鑰。

* 要禁用密鑰：按一下 **停用**. 如果要暫停使用密鑰，可以執行此操作。
* 若要啟用先前停用的金鑰：按一下 **啟用**.
* 要刪除密鑰：按一下 **刪除**.

### 管理SSH存取權杖

若要使用SSH下載Adobe Commerce版本，您必須產生下載存取權杖。 若要產生代號：

1. 登入 [magento.com帳戶](https://account.magento.com/customer/account/login).
1. 按一下 **我的帳戶** 頁面頂端。
1. 按一下 **帳戶設定** > **下載存取權杖**.

   ![存取金鑰](../../assets/installation/connect_keys1.png)

1. 按一下 **產生新代號** 替換和禁用現有令牌。

您必須使用MAGEID加上代號才能下載版本。 您的MAGEID會顯示在帳戶頁面的左上角。

例如：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

使用驗證金鑰：

* [獲取元資料包（整合器、包裝器）](../composer.md)
* [複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) （僅限貢獻開發人員）
* [升級和管理模組](../../upgrade/modules/upgrade.md)
