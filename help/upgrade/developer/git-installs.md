---
title: 升級Git安裝
description: 升級您從Git存放庫複製的Adobe Commerce安裝。
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# 升級Git安裝

本主題說明投稿開發人員如何在不重新安裝的情況下更新Adobe Commerce。 如果您不是貢獻開發人員，請參閱[執行升級](../implementation/perform-upgrade.md)。

若要升級您是參與開發人員：

{{$include /help/_includes/server-login.md}}

1. 儲存您對`composer.json`檔案所做的任何變更，因為後續步驟會覆寫它。

1. 建立`composer.json`檔案的備份。

   ```bash
   cp composer.json composer.json.old
   ```

1. 更新您的本機存放庫以取得最新程式碼：

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >如果`git pull origin develop`失敗，請參閱[疑難排解](https://support.magento.com/hc/en-us/articles/360034229872)。

1. 比較並合併您的`composer.json.old`檔案與`composer.json`檔案。

1. 解決相依性並將確切版本寫入`composer.lock`檔案。

   ```bash
   composer update
   ```

1. 更新資料庫：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```
