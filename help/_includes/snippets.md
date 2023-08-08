---
source-git-commit: 20add0a748e8df38dff48a779c63e1177d2a022d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---
# 代碼片段

## 僅限Commerce {#commerce-only}

>[!NOTE]
>
>此 [!DNL Upgrade Compatibility Tool] 僅適用於Adobe Commerce執行個體。

<!-- Configuration guide snippets -->

## 檔案系統擁有者 {#file-system-owner}

>[!WARNING]
>
>所有MagentoCLI指令都必須由 [檔案系統擁有者](/help/configuration/cli/config-cli.md#prerequisites).

## 備份命令 {#tip-backup-command}

>[!TIP]
>
>此 `support:backup` 命令為 _非_ 執行的相同程式碼備份 `setup:backup` 命令。 此 `support:backup` 命令是用來備份程式碼，以供Adobe Commerce支援人員檢查。

## 僅限Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能僅適用於Adobe Commerce執行個體。

## 已棄用分割資料庫 {#deprecate-split-db}

>[!IMPORTANT]
>
>分割資料庫功能為 [已棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) 在Adobe Commerce 2.4.2版中。 另請參閱 [從分割資料庫還原為單一資料庫](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 與舊版不相容的變更 {#bics}

>[!NOTE]
>
>Adobe Commerce和Magento Open Source版本可能包含與舊版不相容的變更(BIC)。 若要複查與舊版不相容的變更，請參閱 [BIC參考](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 主要與回溯不相容的問題說明於 [BIC重點專案](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). 並非所有發行版本都會推出主要BIC。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>從2.3.2版開始，我們將指派並發佈索引式常見漏洞和暴露(CVE)編號，其中會包含外部各方回報給我們的每個安全性錯誤。 這可讓使用者更輕鬆地識別其部署中未解決的漏洞。 如需瞭解有關CVE識別碼的詳細資訊，請參閱 [CVE](https://cve.mitre.org/).

## 其他發行資訊 {#other-release-info}

>[!NOTE]
>
>雖然這些發行說明中所述的增強功能和錯誤修正程式碼與Adobe Commerce捆綁在一起，但其中幾個專案(例如B2B、頁面產生器和Progressive Web Application(PWA) Studio)也獨立發行。 這些專案的錯誤修正記錄在每個專案檔案中提供的個別專案特定發行資訊中。 另請參閱 [產品版本總覽](/help/release/release-notes/overview.md).
