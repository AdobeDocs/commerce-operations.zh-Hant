---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# 更新建置系統

**若要更新組建系統**：

1. 以檔案系統擁有者的身分登入組建系統。
1. 變更至應用程式根目錄。

   ```bash
   cd <Magento root dir>
   ```

1. 從原始檔控制提取變更到`app/etc/config.php`。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 編譯程式碼。

   ```bash
   bin/magento setup:di:compile
   ```

1. 編譯程式碼之後，產生靜態檢視檔案。

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. 檢查原始檔控制中的變更。

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
