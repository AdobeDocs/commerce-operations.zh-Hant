---
title: 套用修補程式
description: 瞭解將修補程式套用至Adobe Commerce專案的方法。
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 套用修補程式

您可以使用下列任一方法來套用修補程式：

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [命令列](../patches/apply.md#command-line)
- [作曲者](../patches/apply.md#composer)


>[!TIP]
>
>請參閱[最佳實務](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md)，以取得企業規模集中修正Adobe Commerce的相關資訊。

## 作曲者

>[!IMPORTANT]
>
>若要套用正式品質修補程式，請使用[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}。 在部署任何自訂修補程式之前，請務必執行完整的測試。

若要使用Composer套用自訂修補程式：

1. 開啟您的命令列應用程式，並導覽至您的專案目錄。
1. 將`cweagans/composer-patches`外掛程式新增至`composer.json`檔案。

   ```bash
   composer require cweagans/composer-patches
   ```

1. 編輯`composer.json`檔案並新增以下區段以指定：
   - **模組：** *\&quot;magento/module-payment\&quot;*
   - **標題：** *\&quot;MAGETOW-56934：使用Authorize.net訂購時信用卡無效結帳頁面凍結\&quot;*
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

   如果修補程式影響多個模組，您必須建立多個以多個模組為目標的修補程式檔案。

1. 套用修補程式。 只有在您想要檢視偵錯資訊時才使用`-v`選項。

   ```bash
   composer -v install
   ```

1. 更新`composer.lock`檔案。 鎖定檔案會追蹤哪些修補程式已套用至物件中的每個Composer套件。

   ```bash
   composer update --lock
   ```

## 命令列

若要從命令列套用修補程式：

1. 使用FTP、SFTP、SSH或您的一般傳輸方法，將本機檔案上傳至伺服器上的`<Magento_root>`目錄。
1. 以[管理員使用者](../../configuration/cli/config-cli.md#prerequisites)身分登入伺服器，並確認檔案在正確的目錄中。
1. 在命令列介面中，根據修補程式副檔名執行以下命令：

   ```bash
   patch < patch_file_name.patch
   ```

   該命令假定要修補的檔案相對於修補檔案定位。

   >[!NOTE]
   >
   >如果命令列顯示： `File to patch:`，表示它找不到預期的檔案，即使路徑看起來是正確的。 在命令列終端機中顯示的方塊中，第一行顯示要修補的檔案。 複製檔案路徑並將其貼到`File to patch:`提示字元並按`Enter`，修補程式應該會完成。

1. 若要反映變更，請在&#x200B;**系統** >工具> **快取管理**&#x200B;下重新整理管理員中的快取。

   或者，您也可以使用相同的指令在本機套用修補程式，然後正常確認並推送。
