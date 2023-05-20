---
title: 配置檔案所有權和權限
description: 按照以下步驟為Adobe Commerce和Magento Open Source的本地安裝配置檔案系統權限。
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---

# 配置檔案所有權和權限

本主題討論如何在安裝Adobe Commerce或Magento Open Source之前設定Web伺服器組的讀寫權限。 這是必需的，因此命令行可以將檔案寫入檔案系統。

您使用的過程不同，具體取決於您是否使用 [共用主機](#set-permissions-for-one-user-on-shared-hosting) 擁有一個用戶，或者 [專用伺服器](#set-ownership-and-permissions-for-two-users) 並有兩個用戶。

## 為共用主機上的一個用戶設定權限

本節討論如果以同樣運行Web伺服器的同一用戶身份登錄應用程式伺服器，如何設定預安裝權限。 此類型的設定在共用主機環境中是常見的。

要在安裝應用程式之前設定權限：

1. 登錄到應用程式伺服器。
1. 使用共用主機提供程式提供的檔案管理器應用程式驗證是否在以下目錄上設定了寫入權限：

   * `vendor` （合成器或壓縮存檔安裝）
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * 任何其他靜態資源

1. 如果您具有命令行訪問權限，請按顯示的順序輸入以下命令：

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   要（可選）在一行中輸入所有命令，請輸入以下內容(假定應用程式已安裝在 `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. 如果尚未執行此操作，請通過以下方法之一獲取應用程式：

   * [作曲家集合](../../composer.md)
   * [克隆儲存庫（僅提供開發人員）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. 設定檔案系統所有權和權限後， [安裝應用程式](../../advanced.md)

>[!NOTE]
>
>要在安裝應用程式後進一步限制權限，您可以 [配置umask](../../next-steps/set-umask.md)。

## 為兩個用戶設定所有權和權限

本節討論如何設定您自己的伺服器或專用主機安裝程式的所有權和權限。 在此類設定中，通常 *不能* 以Web伺服器用戶身份登錄或切換到。 通常，您以一個用戶身份登錄，並以其他用戶身份運行Web伺服器。

要設定雙用戶系統的所有權和權限：

按顯示的順序完成以下任務：

* [關於共用組](#about-the-shared-group)
* [建立檔案系統所有者並為用戶提供強密碼](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [查找Web伺服器用戶組](#find-the-web-server-user-group)
* [將檔案系統所有者置於Web伺服器組中](#put-the-file-system-owner-in-the-web-server-group)
* [獲取軟體](#get-the-software)
* [設定共用組的所有權和權限](#set-ownership-and-permissions-for-the-shared-group)

### 關於共用組

使Web伺服器能夠寫入檔案系統中的檔案和目錄，同時維護 *所有權* 由檔案系統所有者，兩個用戶必須位於同一組中。 這是必要的，以便兩個用戶都可以共用對檔案（包括使用管理員或其他基於Web的實用程式建立的檔案）的訪問權。

本節討論如何建立檔案系統所有者並將該用戶放入Web伺服器的組中。 如果您願意，可以使用現有用戶帳戶；出於安全原因，我們建議用戶使用強密碼。

>[!NOTE]
>
>跳至 [查找Web伺服器用戶組](#find-the-web-server-user-group) 的子菜單。

### 建立檔案系統所有者並為用戶提供強密碼

本節討論如何建立檔案系統所有者。 (檔案系統所有者是另一個術語 *命令行用戶*。)

要在CentOS或Ubuntu上建立用戶，請以用戶身份輸入以下命令 `root` 權限：

```bash
adduser <username>
```

要向用戶提供密碼，請以用戶身份輸入以下命令 `root` 權限：

```bash
passwd <username>
```

按照螢幕上的提示為用戶建立密碼。

>[!WARNING]
>
>如果你沒有 `root` 權限，您可以使用其他本地用戶帳戶。 確保用戶具有強密碼並繼續 [將檔案系統所有者置於Web伺服器組中](#step-3-put-the-file-system-owner-in-the-web-servers-group)。

例如，要建立名為 `magento_user` 並為用戶提供密碼，輸入：

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>因為建立此用戶的意義是提供更高的安全性，因此請確保建立 [強密碼](https://en.wikipedia.org/wiki/Password_strength)。

### 查找Web伺服器用戶組

要查找Web伺服器用戶組：

* CentOS:

   ```bash
   grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
   ```

   或

   ```bash
   grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
   ```

通常，用戶和組名稱 `apache`。

* 烏班圖： `ps aux | grep apache` 查找Apache用戶，然後 `groups <apache user>` 的子菜單。

通常，用戶名和組名都 `www-data`。

### 將檔案系統所有者置於Web伺服器組中

要將檔案系統所有者置於Web伺服器的主組中（假定CentOS和Ubuntu的典型Apache組名），請以用戶身份輸入以下命令 `root` 權限：

* CentOS: `usermod -a -G apache <username>`
* 烏班圖： `usermod -a -G www-data <username>`

>[!NOTE]
>
>的 `-a -G` 選項很重要，因為它們會添加 `apache` 或 `www-data` 作為 *次* 組到用戶帳戶，這將保留用戶 *主* 組。 將輔助組添加到用戶帳戶有助於 [限制檔案所有權和權限](#set-ownership-and-permissions-for-two-users) 確保共用組的成員僅有權訪問某些檔案。

例如，要添加用戶 `magento_user` 到 `apache` CentOS上的主組：

```bash
sudo usermod -a -G apache magento_user
```

要確認用戶是Web伺服器組的成員，請輸入以下命令：

```bash
groups magento_user
```

以下示例結果顯示用戶的主要(`magento`)和輔助(`apache`)組。

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>通常，用戶名和主組名相同。

要完成任務，請重新啟動Web伺服器：

* 烏班圖： `service apache2 restart`
* CentOS: `service httpd restart`

### 獲取軟體

如果尚未這樣做，請通過以下方法之一獲取軟體：

* [作曲家集合](../../composer.md)
* [克隆儲存庫（僅提供開發人員）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### 設定共用組的所有權和權限

要在安裝應用程式之前設定所有權和權限：

1. 以檔案系統所有者身份或切換到身份登錄到應用程式伺服器。
1. 按所示順序輸入以下命令：

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

要（可選）在一行中輸入所有命令，請輸入以下內容(假定應用程式已安裝在 `/var/www/html/magento2` 而Web伺服器組名稱 `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

在檔案系統權限設定不正確且無法由檔案系統所有者更改的情況下，您可以以用戶身份輸入該命令 `root` 權限：

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## 切換到檔案系統所有者

在執行本主題中的其他任務後，輸入以下命令之一以切換到該用戶：

* 烏班圖： `su <username>`
* CentOS: `su - <username>`

比如說，

```bash
su magento_user
```
