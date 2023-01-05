---
title: '"[!DNL Upgrade Compatibility Tool] 要求」'
description: 驗證您的系統是否滿足運行 [!DNL Upgrade Compatibility Tool] 填入Adobe Commerce專案的命令列介面。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Adobe Commerce存取金鑰

{{commerce-only}}

您必須 [Adobe Commerce存取金鑰](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 下載及使用 [!DNL Upgrade Compatibility Tool]. 將您的Adobe Commerce存取金鑰新增至 `auth.json` 檔案，位於 `~/.composer` 依預設。

>[!NOTE]
>
>檢查 **COMPOSER_HOME** 環境變數，查看位置 `auth.json` 檔案的位置。

此 **公開金鑰** 與 _用戶名_ 而 **私密金鑰** 是 _密碼_:

## Adobe Commerce存取金鑰範例

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> 如果您未正確設定 **Adobe Commerce存取金鑰**，則無法下載 [!DNL Upgrade Compatibility Tool] 和 `composer create-project` 命令將失敗。

執行 `composer install` 安裝相依性。

## 系統需求

使用 [!DNL Upgrade Compatibility Tool] 在命令行介面中：

| **需求** | **限制** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 撰寫器 | 無已知要求。 |
| Node.js | Node.js版本 `^12.22.0`, `^14.17.0`，或 `>=16.0.0` (請參閱 [安裝Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| 記憶體限制 | 至少2GB RAM。 |

[!DNL Upgrade Compatibility Tool] requiles [PCNTL](https://www.php.net/manual/en/book.pcntl.php) 和執行的其他PHP擴充功能。 使用 `composer check-platform-reqs` 命令：

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce僅支援Linux作業系統。 您可以執行 [!DNL Upgrade Compatibility Tool] 在Linux作業系統中。 您不必執行 [!DNL Upgrade Compatibility Tool] Adobe Commerce例項的位置。

必須 [!DNL Upgrade Compatibility Tool] 存取Adobe Commerce執行個體的原始碼。 例如，您可以將其安裝在一台伺服器上，並將其指向另一台伺服器上的Adobe Commerce安裝。

如果您執行 [!DNL Upgrade Compatibility Tool] 針對具有大型模組和檔案的Adobe Commerce執行個體，此工具可能需要大量記憶體（至少2GB）。
