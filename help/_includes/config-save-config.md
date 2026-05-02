---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 更新共用設定

**若要更新組態**：

1. 以檔案系統擁有者的身分登入或切換到您的開發系統。

1. 變更至應用程式根目錄，然後執行傾印命令。

   ```shell
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例如，如果Commerce安裝在`/var/www/html/magento2`中，請輸入：

   ```shell
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. 確認`app/etc/config.php`已更新。

   ```shell
   git status
   ```

   範例回應：

   ```text
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >請&#x200B;_不_&#x200B;將變更提交至`generated`、`pub/media`或`pub/static`目錄至原始檔控制。 您會在建置系統上產生這些檔案。 開發系統可能有程式碼、主題等未準備好用於生產系統的專案。

1. 只將您對`app/etc/config.php`的變更籤入至原始檔控制。

   ```shell
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
