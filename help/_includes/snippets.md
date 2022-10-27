---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# 程式碼片段

## 僅商務 {#commerce-only}

>[!NOTE]
>
>此 [!DNL Upgrade Compatibility Tool] 僅適用於Adobe Commerce執行個體。

<!-- Configuration guide snippets -->

## 檔案系統所有者 {#file-system-owner}

>[!WARNING]
>
>所有MagentoCLI命令必須由 [檔案系統所有者](/help/configuration/cli/config-cli.md#prerequisites).

## 備份命令 {#tip-backup-command}

>[!TIP]
>
>此 `support:backup` 命令為 _not_ 由 `setup:backup` 命令。 此 `support:backup` 命令用於備份代碼以供Adobe Commerce支援檢查。

## 僅限Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能僅適用於Adobe Commerce執行個體。

## 已棄用拆分資料庫 {#deprecate-split-db}

>[!IMPORTANT]
>
>拆分資料庫功能是 [已棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) 在2.4.2版Adobe Commerce中。 請參閱 [從拆分資料庫還原到單個資料庫](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 向後不相容的更改 {#bics}

>[!NOTE]
>
>Adobe Commerce和Magento Open Source版本可能包含不相容於向後的更改(BIC)。 要查看向後不相容的更改，請參閱 [BIC引用](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 若要了解主要的回溯不相容問題，請參閱 [BIC亮點](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). 並非所有版本都引入了主要BIC。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>從2.3.2版開始，我們會指派並發佈已編列索引的常見弱點和風險(CVE)編號，並由外部方回報每個安全錯誤。 這可讓使用者更輕鬆地識別部署中未解決的弱點。 如需深入了解CVE識別碼，請前往 [CVE](https://cve.mitre.org/).
