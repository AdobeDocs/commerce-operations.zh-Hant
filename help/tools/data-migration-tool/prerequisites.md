---
title: '"[!DNL Data Migration Tool] 必要條件'
description: 「開始使用前，請先了解您需要做什麼 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。」
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# [!DNL Data Migration Tool] 必要條件

開始移轉之前，請確定已符合下列需求。

## Magento2系統

* 設定Magento2系統，使其符合 [系統需求](../../installation/system-requirements.md).

   使用至少與現有Magento1系統匹配的拓撲和設計。

* [安裝Magento2](../../installation/overview.md).

## Cron

請勿啟動Magento2 cron作業。

## 資料庫

* 安裝後，備份或 [轉儲](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) Magento2資料庫。 這允許您在遷移失敗時恢復初始資料庫狀態。

* 確認 [!DNL Data Migration Tool] 具有連接Magento1和Magento2資料庫的網路訪問權限。

   在防火牆中開啟埠，以便遷移工具可以與資料庫通信。

* 確保您的MySQL帳戶具有訪問Magento資料庫的所有必要權限。

如果為Magento1資料庫啟用了二進位日誌記錄，請設定全局 [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL系統變數 `1`，或授予 [超級特權](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) 到您的帳戶。

* 移轉前，我們不建議在Magento2商店中建立新實體（產品、類別和屬性），因為 [!DNL Data Migration Tool] 使用Magento1中的舊實體覆寫此類新實體。

## 擴充功能

將Magento1擴充程式碼移轉至Magento2。

若要尋找最新的擴充功能版本，請造訪 [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) 或聯絡您的擴充功能提供者。

您也可以使用 [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
