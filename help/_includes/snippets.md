---
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# 代碼片段

## 僅限Commerce {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool]僅適用於Adobe Commerce執行個體。

<!-- Configuration guide snippets -->

## 檔案系統擁有者 {#file-system-owner}

>[!WARNING]
>
>所有MagentoCLI命令都必須由[檔案系統擁有者](/help/configuration/cli/config-cli.md#prerequisites)執行。

## 備份命令 {#tip-backup-command}

>[!TIP]
>
>`support:backup`命令是&#x200B;_不是_&#x200B;由`setup:backup`命令執行的相同程式碼備份。 `support:backup`命令是用來備份程式碼，以供Adobe Commerce支援人員檢查。

## 僅限Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能僅適用於Adobe Commerce執行個體。

## 已棄用分割資料庫 {#deprecate-split-db}

>[!IMPORTANT]
>
>Adobe Commerce 2.4.2版中的分割資料庫功能已[棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157)。 請參閱[從分割資料庫還原至單一資料庫](/help/configuration/storage/revert-split-database.md)。

<!-- End of Configuration guide snippets -->

## 與舊版不相容的變更 {#bics}

>[!NOTE]
>
>Adobe Commerce版本可能包含與舊版不相容的變更(BIC)。 若要檢閱回溯不相容的變更，請參閱[BIC參考](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)。 在[BIC重點專案](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/)中說明嚴重的回溯不相容問題。 並非所有發行版本都會推出主要BIC。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>從2.3.2版開始，我們將指派並發佈索引式常見漏洞和暴露(CVE)編號，其中會包含外部各方回報給我們的每個安全性錯誤。 這可讓使用者更輕鬆地識別其部署中未解決的漏洞。 您可以在[CVE](https://cve.mitre.org/)進一步瞭解CVE識別碼。

## 其他發行資訊 {#other-release-info}

>[!NOTE]
>
>雖然這些發行說明中所述的增強功能和錯誤修正程式碼與Adobe Commerce捆綁在一起，但其中幾個專案(例如B2B、頁面產生器和Progressive Web Application(PWA) Studio)也獨立發行。 這些專案的錯誤修正記錄在每個專案檔案中提供的個別專案特定發行資訊中。 請參閱[產品版本總覽](/help/release/release-notes/overview.md)。

## PHP程式控制 {#php-process-control}

您必須先在PHP中啟用「程式控制」支援(`pcntl`)，才能以平行模式執行索引器。 請參閱PHP檔案中的[安裝](https://www.php.net/manual/en/pcntl.installation.php)。
