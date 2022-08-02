---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# 更新生成系統

**更新生成系統**:

1. 以檔案系統所有者身份登錄到生成系統。
1. 更改到應用程式根目錄。

   ```bash
   cd <Magento root dir>
   ```

1. 將更改拉入 `app/etc/config.php` 從原始碼管理。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 編譯代碼。

   ```bash
   bin/magento setup:di:compile
   ```

1. 編譯代碼後，生成靜態視圖檔案。

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. 檢查對原始碼管理所做的更改。

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
