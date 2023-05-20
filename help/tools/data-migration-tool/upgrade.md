---
title: 升級 [!DNL Data Migration Tool]
description: 瞭解如何升級 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 升級 [!DNL Data Migration Tool]

確保當前Magento2安裝和 [!DNL Data Migration Tool] 完全匹配，您可能需要升級該工具。

## 先決條件

升級之前 [!DNL Data Migration Tool]，您必須：

* 升級Magento軟體以獲取最新版本

* 備份 `vendor/magento/data-migration-tool` 目錄

* 確保 [!DNL Data Migration Tool] 版本與Magento應用程式版本匹配

### 升級您的Magento軟體

如果你還沒做， [升級Magento軟體](../../upgrade/overview.md)。

### 備份 `vendor/magento/data-migration-tool` 目錄

升級之前 [!DNL Data Migration Tool]，至少備份 `vendor/magento/data-migration-tool` 的子菜單。 在升級期間，可以刪除該代碼並用更新的代碼替換。

您還可以使用以下命令備份整個Magento代碼庫和資料庫：

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>的 `vendor/magento/data-migration-tool` 目錄包含您的自定義代碼。 備份失敗意味著您在升級過程中可能會丟失自定義項。


### 確保版本匹配

的版本 [!DNL Data Migration Tool] 你的Magento軟體必須完全匹配。 例如，Magento2.1.2要求2.1.2版 [!DNL Data Migration Tool]。

查看 [安裝 [!DNL Data Migration Tool]](install.md) 主題：

* [檢查](install.md#check-your-version) 您的Magento2版

* [查找](install.md#find-released-versions-of-data-migration-tool) 已發佈版本 [!DNL Data Migration Tool]

* [檢查](install.md#check-version-of-installed-data-migration-tool) 這樣 [!DNL Data Migration Tool] 版本

## 升級 [!DNL Data Migration Tool]

1. 以或切換到的方式登錄到應用程式伺服器， [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 更改到應用程式根目錄。
1. 輸入以下命令：

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   何處 `<version>` 必須與Magento2代碼庫的版本匹配。

   例如，對於2.1.2版，請輸入：

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 命令完成時等待。
