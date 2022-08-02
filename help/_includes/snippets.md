---
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '97'
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
