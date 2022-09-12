---
title: 複製範例資料Git存放庫
description: 請依照下列步驟安裝Adobe Commerce，並複製Git存放庫以Magento Open Source範例資料。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# 複製範例資料Git存放庫

本主題探討如何複製Magento Open SourceGitHub存放庫，並新增範例資料。 此方法僅適用於貢獻開發人員(亦即計畫貢獻Magento Open Source程式碼基底的開發人員)。

如果您不是貢獻開發人員，請選擇頁面左側目錄中顯示的其他選項之一。

貢獻開發人員可使用此方法安裝範例資料 *僅限* 如果以下是true:

* 您使用Magento Open Source
* 您 [複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>您可以將範例資料與 `develop` 分支（更新）或已釋放的分支(例如 `2.4` （更穩定）)。 建議您使用已發行的分支，因為它更穩定。 如果您要向存放庫貢獻程式碼，且需要最新的程式碼，請使用 `develop` 分支。 無論您選擇哪個分支，您都必須 [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open SourceGitHub存放庫的對應分支。 例如， `develop` 可使用分支 *僅限* 與Magento Open Source `develop` 分支。

## 複製範例資料存放庫

本節探討如何複製範例資料存放庫，以安裝範例資料。 您可以透過下列任一方式複製範例資料存放庫：

* 使用複製 [SSH通訊協定](#clone-with-ssh)
* 使用複製 [HTTPS通訊協定](#clone-with-https)

### 使用SSH複製

若要使用SSH通訊協定複製範例資料GitHub存放庫：

1. 在網頁瀏覽器中，前往 [資料存放庫範例](https://github.com/magento/magento2-sample-data).
1. 在分支名稱旁，按一下 **SSH** 從清單中。
1. 按一下 **複製到剪貼簿**

   下圖顯示了一個示例。

   ![使用SSH複製GitHub存放庫](../../assets/installation/install_mage2_clone-ssh.png)

1. 更改到Web伺服器的docroot目錄。

   通常，對於烏邦圖來說 `/var/www` 而對CentOS來說 `/var/www/html`.

1. 輸入 `git clone` 並貼上您先前取得的值。

   以下範例：

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. 等待儲存庫在伺服器上克隆。

   >[!NOTE]
   >
   >如果顯示下列錯誤，請確定您 [共用您的SSH金鑰](https://docs.github.com/articles/generating-ssh-keys/) 搭配GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. 請務必勾選與主要分支相對應的範例資料存放庫分支 `magento2` 存放庫。

   例如：

   如果您使用 `2.4-develop` Magento Open SourceGitHub存放庫的分支，範例資料分支應為 `2.4-develop`.

   如果您使用 `2.4.3` Magento Open SourceGitHub存放庫的分支，範例資料分支應為 `2.4.3`.

   若要結帳正確的分支，請從範例資料存放庫的根目錄中執行下列命令(假設您需要 `2.4.3` 分支):

   ```bash
   git checkout 2.4.3
   ```

1. 變更為 `<app_root>`.
1. 輸入以下命令，在複製的檔案之間建立符號連結，以便樣例資料正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. 等待命令完成。

1. 請參閱 [設定檔案系統權限和所有權](#set-file-system-ownership-and-permissions).

1. 執行下列命令：

   ```bash
   bin/magento setup:upgrade
   ```

### 使用HTTPS複製

若要使用HTTPS通訊協定複製範例資料GitHub存放庫：

1. 在網頁瀏覽器中，前往 [資料存放庫範例](https://github.com/magento/magento2-sample-data).
1. 在頁面的右側，在 **原地複製URL** 欄位，按一下 **HTTPS**.
1. 按一下 **複製到剪貼簿**.

   下圖顯示了一個示例。

   ![使用HTTPS複製GitHub存放庫](../../assets/installation/install_mage2_clone-https.png)

1. 更改到Web伺服器的docroot目錄。

   通常，對於烏邦圖來說 `/var/www` 而對CentOS來說 `/var/www/html`.

1. 輸入 `git clone` 並貼上您先前取得的值。

   以下範例：

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. 等待儲存庫在伺服器上克隆。
1. 請務必勾選與主要分支相對應的範例資料存放庫分支 `magento2` 存放庫。

   例如：

   如果您使用 `2.4-develop` Magento Open SourceGitHub存放庫的分支，範例資料分支應為 `2.4-develop`.

   如果您使用 `2.4.3` Magento Open SourceGitHub存放庫的分支，範例資料分支應為 `2.4.3`.

   若要結帳正確的分支，請從範例資料存放庫的根目錄中執行下列命令(假設您需要 `2.4.3` 分支):

   ```bash
   git checkout 2.4.3
   ```

1. 變更為 `<magento_root>`.
1. 輸入以下命令，在複製的檔案之間建立符號連結，以便樣例資料正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   例如，

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. 等待命令完成。
1. 請參閱下一節。

>[!WARNING]
>
>如果要安裝示例資料 *after* 安裝Adobe Commerce或Magento Open Source時，您還必須運行以下命令以更新資料庫和架構：
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## 設定檔案系統所有權和權限

因為 `php build-sample-data.php` 指令碼會在示例資料儲存庫和Magento Open Source儲存庫之間建立symlink，則必須在示例資料儲存庫中設定檔案系統權限和所有權。 若未能這麼做，會導致存取店面時發生錯誤。

要在示例資料儲存庫上設定檔案系統權限和所有權：

1. 更改到示例資料克隆目錄。
1. 設定所有權：

   ```bash
   chown -R :<your web server group name> .
   ```

   典型範例：

   * CentOS: `chown -R :apache .`

   * 烏本圖： `chown -R :www-data .`

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

## 完成範例資料安裝

{{$include /help/_includes/sample-data-complete.md}}
