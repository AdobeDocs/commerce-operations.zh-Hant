---
title: '[!DNL Upgrade Compatibility Tool]需求'
description: 確認您的系統符合在Adobe Commerce專案的命令列介面中執行 [!DNL Upgrade Compatibility Tool] 的必要需求。
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Adobe Commerce存取金鑰

{{commerce-only}}

您必須有[Adobe Commerce存取金鑰](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys)才能下載及使用[!DNL Upgrade Compatibility Tool]。 將您的Adobe Commerce存取金鑰新增至您的`auth.json`檔案，該檔案預設位於`~/.composer`。

>[!NOTE]
>
>檢查您的&#x200B;**COMPOSER_HOME**&#x200B;環境變數，以檢視`auth.json`檔案的位置。

**公開金鑰**&#x200B;對應至&#x200B;_使用者名稱_，而&#x200B;**私密金鑰**&#x200B;為&#x200B;_密碼_：

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
> 如果您未正確設定&#x200B;**Adobe Commerce存取金鑰**，將無法下載[!DNL Upgrade Compatibility Tool]，`composer create-project`命令將會失敗。

在終端機中執行`composer install`以安裝相依性。

## 系統需求

在命令列介面中使用[!DNL Upgrade Compatibility Tool]的最低需求為：

| **需求** | **限制** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 作曲者 | 沒有已知的需求。 |
| Node.js | Node.js版本`^12.22.0`、`^14.17.0`或`>=16.0.0` （請參閱[安裝Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)） |
| 記憶體限制 | 至少2GB RAM。 |

[!DNL Upgrade Compatibility Tool]需要[PCNTL](https://www.php.net/manual/en/book.pcntl.php)和其他PHP延伸才能執行。 使用`composer check-platform-reqs`命令檢查所需的PHP副檔名：

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

只有Linux作業系統支援Adobe Commerce。 您可以在Linux作業系統中執行[!DNL Upgrade Compatibility Tool]。 您不必執行Adobe Commerce執行個體所在的[!DNL Upgrade Compatibility Tool]。

[!DNL Upgrade Compatibility Tool]必須能夠存取Adobe Commerce執行個體的原始程式碼。 例如，您可以將其安裝在一部伺服器上，並指向另一部伺服器上的Adobe Commerce安裝。

如果您針對具有大型模組和檔案的Adobe Commerce執行個體執行[!DNL Upgrade Compatibility Tool]，則工具可能需要大量RAM （至少2GB）。

針對雲端基礎結構[!DNL Upgrade Compatibility Tool]專案上的[[!DNL Site-Wide Analysis Tool]Adobe Commerce，從](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) [執行](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}。
