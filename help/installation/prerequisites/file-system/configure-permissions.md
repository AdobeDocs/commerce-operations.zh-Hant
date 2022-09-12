---
title: 配置檔案所有權和權限
description: 請依照下列步驟，為Adobe Commerce和Magento Open Source的內部部署安裝設定檔案系統權限。
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# 配置檔案所有權和權限

本主題討論如何在安裝Adobe Commerce或Magento Open Source之前，為Web伺服器組設定讀寫權限。 這是必要的，這樣命令行才能將檔案寫入檔案系統。

您使用的程式不同，視您是否使用 [共用托管](#set-permissions-for-one-user-on-shared-hosting) 並擁有一個使用者，或 [專用伺服器](#set-ownership-and-permissions-for-two-users) 有兩個用戶。

## 為一個使用者設定共用托管的權限

本節將討論如何以同樣運行Web伺服器的用戶身份登錄到應用程式伺服器，以設定安裝前權限。 此類型的設定在共用托管環境中很常見。

若要在安裝應用程式之前設定權限：

1. 登入您的應用程式伺服器。
1. 使用共用托管提供程式提供的檔案管理器應用程式驗證是否在以下目錄中設定了寫入權限：

   * `vendor` （撰寫器或壓縮的封存安裝）
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * 任何其他靜態資源

1. 如果您有命令行訪問權限，請按所示順序輸入以下命令：

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

   要選擇在一行中輸入所有命令，請輸入以下命令，假定應用程式安裝在 `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. 如果您尚未這麼做，請透過下列其中一種方式取得應用程式：

   * [撰寫器暗語](../../composer.md)
   * [複製存放庫（僅限貢獻開發人員）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. 設定檔案系統所有權和權限後， [安裝應用程式](../../advanced.md)

>[!NOTE]
>
>若要在安裝應用程式後進一步限制權限，您可以 [設定umask](../../next-steps/set-umask.md).

## 設定兩個使用者的所有權和權限

本節探討如何為您自己的伺服器或私人托管設定設定設定所有權和權限。 在這種設定中，您通常 *不能* 以Web伺服器用戶身份登錄或切換到。 您通常以一個使用者身分登入，並以不同使用者身分執行Web伺服器。

要設定兩用戶系統的所有權和權限：

依照下列順序完成下列工作：

* [關於共用群組](#about-the-shared-group)
* [建立檔案系統所有者並為用戶提供強密碼](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [查找Web伺服器用戶組](#find-the-web-server-user-group)
* [將檔案系統所有者放在Web伺服器組中](#put-the-file-system-owner-in-the-web-server-group)
* [獲取軟體](#get-the-software)
* [設定共用群組的所有權和權限](#set-ownership-and-permissions-for-the-shared-group)

### 關於共用群組

使Web伺服器能夠在檔案系統中寫入檔案和目錄，同時維護 *所有權* 由檔案系統所有者，兩個用戶必須位於同一組中。 這是必要的，以便兩個用戶都可以共用對檔案（包括使用管理員或其他基於Web的實用程式建立的檔案）的訪問權。

本節討論如何建立檔案系統所有者並將該用戶放入Web伺服器的組中。 您可以視需要使用現有的使用者帳戶；基於安全原因，建議用戶使用強密碼。

>[!NOTE]
>
>跳到 [查找Web伺服器用戶組](#find-the-web-server-user-group) 如果您打算使用現有的使用者帳戶。

### 建立檔案系統所有者並為用戶提供強密碼

本節將討論如何建立檔案系統所有者。 (檔案系統所有者是 *命令行用戶*.)

要在CentOS或Ubuntu上建立用戶，請輸入以下命令，作為用戶使用 `root` 權限：

```bash
adduser <username>
```

要為用戶提供密碼，請輸入以下命令，作為用戶使用 `root` 權限：

```bash
passwd <username>
```

按照螢幕上的提示為用戶建立密碼。

>[!WARNING]
>
>如果你沒有 `root` 在應用程式伺服器上的權限，則可以使用其他本地用戶帳戶。 請確定使用者有強式密碼，並繼續 [將檔案系統所有者放在Web伺服器組中](#step-3-put-the-file-system-owner-in-the-web-servers-group).

例如，若要建立名為 `magento_user` 並給用戶密碼，請輸入：

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>因為建立此使用者的重點是提供新的安全性，請務必建立 [增強式密碼](https://en.wikipedia.org/wiki/Password_strength).

### 查找Web伺服器用戶組

要查找Web伺服器用戶組，請執行以下操作：

* CentOS:

   ```bash
   grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
   ```

   或

   ```bash
   grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
   ```

通常，使用者和群組名稱都 `apache`.

* 烏本圖： `ps aux | grep apache` 若要尋找Apache使用者，則 `groups <apache user>` 來尋找群組。

通常，使用者名稱和群組名稱都是 `www-data`.

### 將檔案系統所有者放在Web伺服器組中

要將檔案系統所有者放入Web伺服器的主組中（假設CentOS和Ubuntu的典型Apache組名），請輸入以下命令，作為用戶使用 `root` 權限：

* CentOS: `usermod -a -G apache <username>`
* 烏本圖： `usermod -a -G www-data <username>`

>[!NOTE]
>
>此 `-a -G` 選項很重要，因為它們會新增 `apache` 或 `www-data` as a *次要* 群組至使用者帳戶，而會保留使用者的 *主要* 群組。 將次要群組新增至使用者帳戶有助 [限制檔案所有權和權限](#set-ownership-and-permissions-for-two-users) 以確保共用群組的成員只能存取特定檔案。

例如，若要新增使用者 `magento_user` 到 `apache` CentOS上的主要群組：

```bash
sudo usermod -a -G apache magento_user
```

要確認用戶是Web伺服器組的成員，請輸入以下命令：

```bash
groups magento_user
```

下列範例結果顯示使用者的主要(`magento`)和次要(`apache`)群組。

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>通常，使用者名稱和主要群組名稱相同。

要完成該任務，請重新啟動Web伺服器：

* 烏本圖： `service apache2 restart`
* CentOS: `service httpd restart`

### 獲取軟體

如果您尚未這麼做，請透過下列其中一種方式取得軟體：

* [撰寫器暗語](../../composer.md)
* [複製存放庫（僅限貢獻開發人員）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### 設定共用群組的所有權和權限

要在安裝應用程式之前設定所有權和權限，請執行以下操作：

1. 以檔案系統所有者身份登錄到應用程式伺服器，或切換到。
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

要選擇在一行中輸入所有命令，請輸入以下命令，假定應用程式安裝在 `/var/www/html/magento2` 而web伺服器組名為 `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

在檔案系統權限設定不正確且無法由檔案系統擁有者變更的情況下，您可以以使用者身分輸入命令 `root` 權限：

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## 切換到檔案系統所有者

執行本主題中的其他任務後，輸入以下命令之一以切換到該用戶：

* 烏本圖： `su <username>`
* CentOS: `su - <username>`

例如，

```bash
su magento_user
```
