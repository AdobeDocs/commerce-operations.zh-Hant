---
title: 升級Git安裝
description: 升級從Git存放庫複製的Adobe Commerce或Magento Open Source安裝。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# 升級Git安裝

本主題說明協助開發人員如何不重新安裝即可更新Adobe Commerce或Magento Open Source。 如果您不是貢獻開發人員，請參閱 [執行升級](../implementation/perform-upgrade.md).

若要升級（若您是協助開發人員）:

1. 登入您的伺服器。

1. 切換至 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. 更改到克隆應用程式的目錄。 例如，

   ```bash
   cd /var/www/magento2
   ```

1. 儲存您對 `composer.json` 檔案，因為後續步驟會覆寫它。

1. 建立備份 `composer.json` 檔案。

   ```bash
   cp composer.json composer.json.old
   ```

1. 更新本機存放庫以取得最新程式碼：

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >若 `git pull origin develop` 失敗，請參閱 [疑難排解](https://support.magento.com/hc/en-us/articles/360034229872).

1. 比較並合併 `composer.json.old` 檔案 `composer.json` 檔案。

1. 解析相依性，並將確切的版本寫入 `composer.lock` 檔案。

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
