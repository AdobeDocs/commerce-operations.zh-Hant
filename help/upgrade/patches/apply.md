---
title: 應用修補程式
description: 了解將修補程式套用至Adobe Commerce或Magento Open Source專案的方法。
source-git-commit: e2ddb30da8dd86236e1dcf33a3f911b67384a6d7
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# 應用修補程式

可以使用以下任何方法應用修補程式：

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}
- [命令列](../patches/apply.md#command-line)
- [撰寫器](../patches/apply.md#composer)

## 撰寫器

>[!IMPORTANT]
>
>要應用官方質量補丁程式，請使用 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}。 部署任何自定義修補程式之前，請始終執行全面的測試。

要使用撰寫器應用自定義修補程式，請執行以下操作：

1. 開啟命令列應用程式，並導覽至專案目錄。
1. 新增 `cweagans/composer-patches` 外掛程式 `composer.json` 檔案。

   ```bash
   composer require cweagans/composer-patches
   ```

1. 編輯 `composer.json` 檔案並新增下列區段以指定：
   - **模組：** *\&quot;magento/module-payment\&quot;*
   - **標題：** *\&quot;MAGETWO-56934:使用無效信用卡進行訂購時結帳頁面凍結\&quot;*
   - **修補程式路徑：** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   例如：

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   如果修補程式影響多個模組，則必須建立以多個模組為目標的多個修補程式檔案。

1. 應用修補程式。 使用 `-v` 選項。

   ```bash
   composer -v install
   ```

1. 更新 `composer.lock` 檔案。 鎖定檔案跟蹤哪些修補程式已應用於對象中的每個Composer包。

   ```bash
   composer update --lock
   ```

## 命令列

要從命令行應用修補程式：

1. 將本機檔案上傳至 `<Magento_root>` 目錄（使用FTP、SFTP、SSH或您的一般傳輸方法）。
1. 以 [管理員使用者](../../configuration/cli/config-cli.md#prerequisites) 並驗證檔案是否位於正確的目錄中。
1. 在命令行介面中，根據修補程式擴展運行以下命令：

   ```bash
   patch < patch_file_name.patch
   ```

   該命令假定要修補的檔案相對於修補檔案位於。

   >[!NOTE]
   >
   >如果命令行顯示： `File to patch:`，即使路徑看起來正確，亦無法找到預期的檔案。 在命令行終端機中顯示的框中，第一行顯示要修補的檔案。 複製檔案路徑並貼入 `File to patch:` 提示並按下 `Enter` 修補程式應已完成。

1. 若要反映變更，請重新整理「管理員」底下的快取 **系統** >工具> **快取管理**.

   或者，可以使用相同命令在本地應用修補程式，然後正常提交和推送。
