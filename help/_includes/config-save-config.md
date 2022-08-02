---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 更新共用配置

**更新配置**:

1. 以檔案系統所有者身份或切換到檔案系統所有者身份登錄到開發系統。

1. 更改到應用程式根目錄並運行dump命令。

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例如，如果Commerce安裝在 `/var/www/html/magento2`，輸入：

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. 確認 `app/etc/config.php` 已更新。

   ```bash
   git status
   ```

   示例響應：

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >做 _不_ 將更改提交到 `generated`。 `pub/media`或 `pub/static` 目錄到原始碼管理。 在生成系統上生成這些檔案。 開發系統可能有代碼、主題等，尚未準備好在生產系統上使用。

1. 簽入您對 `app/etc/config.php` 僅到原始碼管理。

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
