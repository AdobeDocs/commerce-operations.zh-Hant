---
title: 應用修補程式
description: 瞭解將修補程式應用到Adobe Commerce或Magento Open Source項目的方法。
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# 應用修補程式

可以使用以下任何方法應用修補程式：

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [命令行](../patches/apply.md#command-line)
- [作曲家](../patches/apply.md#composer)

## 作曲家

>[!IMPORTANT]
>
>要應用正式質量修補程式，請使用 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}。 在部署任何自定義修補程式之前，請始終執行全面的測試。

要使用Composer應用自定義修補程式，請執行以下操作：

1. 開啟命令行應用程式並導航到項目目錄。
1. 添加 `cweagans/composer-patches` 插件 `composer.json` 的子菜單。

   ```bash
   composer require cweagans/composer-patches
   ```

1. 編輯 `composer.json` 並添加以下部分以指定：
   - **模組：** *\ &quot;magento/module payment\&quot;*
   - **標題：** *\&quot;MAGETWO-56934:使用無效信用卡使用Authorize.net進行訂購時，簽出頁面將凍結\&quot;*
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

   如果補丁程式影響多個模組，則必須建立多個針對多個模組的補丁程式檔案。

1. 應用修補程式。 使用 `-v` 頁籤

   ```bash
   composer -v install
   ```

1. 更新 `composer.lock` 的子菜單。 鎖定檔案跟蹤對象中每個Composer包已應用的修補程式。

   ```bash
   composer update --lock
   ```

## 命令行

要從命令行應用修補程式：

1. 將本地檔案上載到 `<Magento_root>` 使用FTP、SFTP、SSH或常規傳輸方法的伺服器上的目錄。
1. 以 [管理員用戶](../../configuration/cli/config-cli.md#prerequisites) 並驗證檔案是否位於正確的目錄中。
1. 在命令行介面中，根據修補程式擴展運行以下命令：

   ```bash
   patch < patch_file_name.patch
   ```

   該命令假定要修補的檔案相對於修補檔案位於。

   >[!NOTE]
   >
   >如果命令行顯示： `File to patch:`，即使路徑看起來正確，也無法定位目標檔案。 在命令行終端中顯示的框中，第一行顯示要修補的檔案。 複製檔案路徑並將其貼上到 `File to patch:` 按提示 `Enter` 修補程式應該已完成。

1. 要反映的更改，請刷新管理中的快取 **系統** >工具> **快取管理**。

   或者，可以使用相同的命令在本地應用修補程式，然後提交並正常推送。
