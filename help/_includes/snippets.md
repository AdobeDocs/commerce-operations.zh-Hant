---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# 片段

## 僅商業 {#commerce-only}

>[!NOTE]
>
>的 [!DNL Upgrade Compatibility Tool] 僅適用於Adobe Commerce實例。

<!-- Configuration guide snippets -->

## 檔案系統所有者 {#file-system-owner}

>[!WARNING]
>
>所有MagentoCLI命令必須由 [檔案系統所有者](/help/configuration/cli/config-cli.md#prerequisites)。

## 備份命令 {#tip-backup-command}

>[!TIP]
>
>的 `support:backup` 命令 _不_ 由 `setup:backup` 的子菜單。 的 `support:backup` 命令用於備份代碼供Adobe Commerce支援部門檢查。

## 僅Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能僅適用於Adobe Commerce實例。

## 不建議使用拆分資料庫 {#deprecate-split-db}

>[!IMPORTANT]
>
>拆分資料庫功能 [棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) 在Adobe Commerce2.4.2版。 請參閱 [從拆分資料庫還原到單個資料庫](/help/configuration/storage/revert-split-database.md)。

<!-- End of Configuration guide snippets -->

## 向後不相容的更改 {#bics}

>[!NOTE]
>
>Adobe Commerce和Magento Open Source版本可能包含向後不相容的更改(BIC)。 要查看向後不相容的更改，請參閱 [BIC引用](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)。 中介紹了主要的後向不相容問題 [BIC突出顯示](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/)。 並非所有版本都引入主要BIC。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>從2.3.2版開始，我們將分配並發佈索引的Common Velubility and Explorations(CVE)編號，其中每個安全缺陷都由外部方向我們報告。 這使用戶能夠更輕鬆地識別其部署中未定址的漏洞。 您可以在以下位置瞭解有關CVE標識符的詳細資訊： [CVE](https://cve.mitre.org/)。
