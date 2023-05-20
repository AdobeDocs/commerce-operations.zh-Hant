---
title: '"[!DNL Data Migration Tool] 先決條件'
description: 在開始使用之前，瞭解您需要做什麼 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 先決條件

開始遷移之前，請確保滿足以下要求。

## Magento2系統

* 設定Magento2系統，使其滿足 [系統要求](../../installation/system-requirements.md)。

   使用至少與現有Magento1系統匹配的拓撲和設計。

* [安裝Magento2](../../installation/overview.md)。

## 克龍

不要開始Magento2 Cron作業。

## 資料庫

* 安裝後，備份或 [轉儲](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) Magento2資料庫。 這允許您在遷移不成功時恢復初始資料庫狀態。

* 驗證 [!DNL Data Migration Tool] 具有連接Magento1和Magento2資料庫的網路訪問權限。

   在防火牆中開啟埠，以便遷移工具可以與資料庫通信。

* 確保MySQL帳戶具有訪問Magento資料庫的所有必要權限。

如果為Magento1資料庫啟用了二進位日誌，請設定全局 [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL系統變數到 `1`或 [SUPER特權](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) 你的帳戶。

* 我們建議在遷移前在Magento2儲存中建立新實體（產品、類別和屬性），因為 [!DNL Data Migration Tool] 用第1Magento中的舊實體覆蓋這些新實體。

## 擴展

將Magento1擴展代碼遷移到Magento2。

要查找最新的擴展版本，請訪問 [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) 或聯繫您的分機提供商。

您還可以使用 [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md)。
