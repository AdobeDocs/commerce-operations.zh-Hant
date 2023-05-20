---
title: 克隆示例資料Git儲存庫
description: 按照以下步驟安裝Adobe Commerce並通過克隆Git儲存庫Magento Open Source示例資料。
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# 克隆示例資料Git儲存庫

本主題討論如何克隆Magento Open SourceGitHub儲存庫並添加示例資料。 此方法僅用於提供開發商(即計畫提供Magento Open Source代碼庫的開發商)。

如果您不是參與開發人員，請選擇頁面左側目錄中顯示的其他選項之一。

提供幫助的開發人員可以使用此方法安裝示例資料 *僅* 如果以下情況為真：

* 您使用Magento Open Source
* 你 [克隆了GitHub儲存庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>您可以將示例資料與 `develop` 分支（更新）或已釋放分支(如 `2.4` （更穩定）)。 我們建議您使用已釋放的分支，因為它更穩定。 如果您正在向儲存庫提供代碼，並且需要最新的代碼，請使用 `develop` 分支。 無論您選擇哪個分支，您都必須 [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open SourceGitHub儲存庫的相應分支。 例如， `develop` 可以使用分支 *僅* Magento Open Source `develop` 分支。

## 克隆示例資料儲存庫

本節討論如何通過克隆示例資料儲存庫來安裝示例資料。 可以使用以下任何方法克隆示例資料儲存庫：

* 與 [SSH協定](#clone-with-ssh)
* 與 [HTTPS協定](#clone-with-https)

### 使用SSH克隆

要使用SSH協定克隆示例資料GitHub儲存庫，請執行以下操作：

1. 在Web瀏覽器中，轉到 [示例資料儲存庫](https://github.com/magento/magento2-sample-data)。
1. 在分支名稱旁，按一下 **SSH** 清單中。
1. 按一下 **複製到剪貼簿**

   下圖顯示了一個示例。

   ![使用SSH克隆GitHub儲存庫](../../assets/installation/install_mage2_clone-ssh.png)

1. 更改到Web伺服器的docroot目錄。

   通常，對於烏班圖來說 `/var/www` 對於CentOS `/var/www/html`。

1. 輸入 `git clone` 然後貼上你之前獲得的值。

   以下示例：

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. 等待儲存庫在伺服器上克隆。

   >[!NOTE]
   >
   >如果顯示以下錯誤，請確保 [共用您的SSH密鑰](https://docs.github.com/articles/generating-ssh-keys/) 使用GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. 確保簽出與從主資料庫使用的分支相對應的示例資料儲存庫的分支 `magento2` 儲存庫。

   例如：

   如果你用 `2.4-develop` Magento Open SourceGitHub儲存庫的分支，示例資料分支應為 `2.4-develop`。

   要簽出正確的分支，請從示例資料儲存庫的根目錄中運行以下命令(假定您需要 `2.4-develop` 分支):

   ```bash
   git checkout 2.4-develop
   ```

1. 更改為 `<app_root>`。
1. 輸入以下命令，在克隆的檔案之間建立符號連結，以便樣例資料正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. 等待命令完成。

1. 請參閱 [設定檔案系統權限和所有權](#set-file-system-ownership-and-permissions)。

1. 運行以下命令：

   ```bash
   bin/magento setup:upgrade
   ```

### 使用HTTPS克隆

要使用HTTPS協定克隆示例資料GitHub儲存庫，請執行以下操作：

1. 在Web瀏覽器中，轉到 [示例資料儲存庫](https://github.com/magento/magento2-sample-data)。
1. 在頁面的右側，在 **克隆URL** ，按一下 **HTTPS**。
1. 按一下 **複製到剪貼簿**。

   下圖顯示了一個示例。

   ![使用HTTPS克隆GitHub儲存庫](../../assets/installation/install_mage2_clone-https.png)

1. 更改到Web伺服器的docroot目錄。

   通常，對於烏班圖來說 `/var/www` 對於CentOS `/var/www/html`。

1. 輸入 `git clone` 然後貼上你之前獲得的值。

   以下示例：

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. 等待儲存庫在伺服器上克隆。
1. 確保簽出與從主資料庫使用的分支相對應的示例資料儲存庫的分支 `magento2` 儲存庫。

   例如：

   如果你用 `2.4-develop` Magento Open SourceGitHub儲存庫的分支，示例資料分支應為 `2.4-develop`。

   要簽出正確的分支，請從示例資料儲存庫的根目錄中運行以下命令(假定您需要 `2.4-develop` 分支):

   ```bash
   git checkout 2.4-develop
   ```

1. 更改為 `<magento_root>`。
1. 輸入以下命令，在克隆的檔案之間建立符號連結，以便樣例資料正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   比如說，

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. 等待命令完成。
1. 請參閱下一節。

>[!WARNING]
>
>如果要安裝示例資料 *後* 安裝Adobe Commerce或Magento Open Source時，還必須運行以下命令以更新資料庫和模式：
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## 設定檔案系統所有權和權限

因為 `php build-sample-data.php` 指令碼在示例資料儲存庫和Magento Open Source儲存庫之間建立符號連結，您必須在示例資料儲存庫中設定檔案系統權限和所有權。 如果無法執行此操作，則會導致訪問儲存面時出錯。

要在示例資料儲存庫上設定檔案系統權限和所有權：

1. 更改到示例資料克隆目錄。
1. 設定所有權：

   ```bash
   chown -R :<your web server group name> .
   ```

   典型示例：

   * CentOS: `chown -R :apache .`

   * 烏班圖： `chown -R :www-data .`

1. 設定權限：

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. 清除靜態檔案：

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## 完成示例資料安裝

{{$include /help/_includes/sample-data-complete.md}}
