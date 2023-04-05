---
title: 安裝擴充功能
description: 請依照下列步驟，安裝Adobe Commerce或Magento Open Source擴充功能。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 安裝擴充功能

延伸或自訂Adobe Commerce的程式碼，Magento Open Source行為稱為擴充功能。 您可以選擇在 [Commerce Marketplace](https://marketplace.magento.com) 或其他擴充功能發佈系統。

擴充功能包括：

- 模組(擴充Adobe Commerce和Magento Open Source功能)
- 主題（變更店面和管理員的外觀和風格）
- 語言套件（當地化店面和管理員）

>[!TIP]
>
>本主題說明如何使用命令列安裝您從Commerce Marketplace購買的擴充功能。 可以使用相同的過程來安裝 _any_ 擴充功能；您只需要擴充功能的撰寫器名稱和版本。 若要尋找，請開啟擴充功能的 `composer.json` ，並記下 `"name"` 和 `"version"`.

在安裝之前，您可能想：

1. 備份資料庫。
1. 啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

若要安裝擴充功能，您必須：

1. 從Commerce Marketplace或其他擴充功能開發人員取得擴充功能。
1. 如果您從Commerce Marketplace安裝擴充功能，請確定 `repo.magento.com` 存放庫存在於 `composer.json` 檔案：

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. 取得擴充功能的撰寫器名稱和版本。
1. 更新 `composer.json` 檔案，其中包含副檔名的名稱和版本。
1. 確認已正確安裝擴充功能。
1. 啟用並設定擴充功能。

## 取得擴充功能撰寫器名稱和版本

如果您已經知道擴充功能的撰寫器名稱和版本，請略過此步驟，並繼續 [更新您的 `composer.json` 檔案](#update-your-composer-file).

若要從Commerce Marketplace取得擴充功能的撰寫器名稱和版本：

1. 登入 [Commerce Marketplace](https://marketplace.magento.com) 使用您用來購買擴充功能的使用者名稱和密碼。

1. 在右上角，按一下 **您的姓名** > **我的設定檔**.

   ![存取您的Marketplace帳戶](../../assets/installation/marketplace-my-profile.png)

1. 按一下 **我的購買**.

   ![Marketplace購買歷史記錄](../../assets/installation//marketplace-my-purchases.png)

1. 找到您要安裝的擴充功能，然後按一下 **技術詳細資訊**.

   ![技術詳細資訊會顯示擴充功能的撰寫器名稱](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>或者，您也可以找到的撰寫器名稱和版本 _any_ 擴充功能(無論您是在Commerce Marketplace或其他位置購買) `composer.json` 檔案。

## 更新您的撰寫器檔案

將擴充功能的名稱和版本新增至 `composer.json` 檔案：

1. 導覽至專案目錄並更新 `composer.json` 檔案。

   ```bash
   composer require <component-name>:<version>
   ```

   例如，

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. 輸入 [驗證金鑰](../prerequisites/authentication-keys.md). 您的公開金鑰是您的使用者名稱；您的私密金鑰是您的密碼。

1. 等待撰寫器完成專案相依性的更新，並確定沒有任何錯誤：

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## 驗證擴充功能

若要確認已正確安裝擴充功能，請執行下列命令：

```bash
bin/magento module:status J2t_Payplug
```

依預設，擴充功能可能已停用：

```terminal
Module is disabled
```

擴充功能名稱的格式為 `<VendorName>_<ComponentName>`;這是與撰寫器名稱不同的格式。 使用此格式啟用擴充功能。 如果您不確定擴充功能名稱，請執行：

```bash
bin/magento module:status
```

並在「已停用模組清單」下尋找擴充功能。

## 啟用擴充功能

除非您先清除產生的靜態檢視檔案，否則某些擴充功能無法正常運作。 使用 `--clear-static-content` 選項，在啟用擴充功能時清除靜態檢視檔案。

1. 啟用擴充功能並清除靜態檢視檔案：

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   您應會看到下列輸出：

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. 註冊擴充功能：

   ```bash
   bin/magento setup:upgrade
   ```

1. 重新編譯您的專案：在生產模式中，您可能會收到「請重新運行Magento編譯命令」的消息。 應用程式不會提示您在「開發人員」模式下運行編譯命令。

   ```bash
   bin/magento setup:di:compile
   ```

1. 確認已啟用擴充功能：

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   您應該會看到輸出，驗證擴充功能已不再停用：

   ```terminal
   Module is enabled
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 視需要在「管理」中設定擴充功能。

>[!TIP]
>
>如果在瀏覽器中載入店面時遇到錯誤，請使用以下命令清除快取： `bin/magento cache:flush`.

## 升級擴充功能

若要更新或升級模組或擴充功能：

1. 從Marketplace或其他擴充功能開發人員下載更新的檔案。 記下模組名稱和版本。

1. 將內容導出到應用程式根目錄。

1. 如果模組的撰寫器套件存在，請執行下列其中一項。

   按模組名稱更新：

   ```bash
   composer update vendor/module-name
   ```

   按版本更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 運行以下命令以升級、部署和清除快取。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
