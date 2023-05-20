---
title: 升級基於Git的安裝
description: 升級從Git儲存庫克隆的Adobe Commerce或Magento Open Source安裝。
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# 升級基於Git的安裝

本主題討論了派遣開發人員如何在不重新安裝的情況下更新Adobe Commerce或Magento Open Source。 如果您不是派遣開發人員，請參閱 [執行升級](../implementation/perform-upgrade.md)。

如果您是參與開發人員，則要升級：

{{$include /help/_includes/server-login.md}}

1. 保存對 `composer.json` 檔案，因為後續步驟將覆蓋它。

1. 建立備份 `composer.json` 的子菜單。

   ```bash
   cp composer.json composer.json.old
   ```

1. 更新本地儲存庫以獲取最新代碼：

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >如果 `git pull origin develop` 失敗，請參閱 [故障排除](https://support.magento.com/hc/en-us/articles/360034229872)。

1. 比較並合併 `composer.json.old` 檔案 `composer.json` 的子菜單。

1. 解決依賴項，並將精確版本寫入 `composer.lock` 的子菜單。

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
