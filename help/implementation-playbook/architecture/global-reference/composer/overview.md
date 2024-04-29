---
title: Composer開發
description: 瞭解如何在「vendor/」目錄中就地開發撰寫器模組。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Composer開發

本主題說明就地開發Composer模組的建議方法（如中的Git存放庫） `vendor/` 目錄)，並將這些模組新增至您的主要Git專案。

>[!NOTE]
>
>這些准則主要適用於 [全球參考架構(GRA)](../overview.md) 專案。

## 準備開發分支

1. 在您的主要Git存放庫中建立或簽出開發分支。
1. 您需要維護的每個模組都有開發版本。

   在此範例中，主要Git存放庫中的每個分支都代表Composer套件版本。 此情境中建議的Composer版本命名慣例是 `dev-` 後面接著分支名稱。 例如：

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. 如果另一個撰寫器套件需要模組的特定版本(例如， `client/module-example 1.0.12`)，以別名安裝：

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   對於 `qa` 分支，取代 `dev-develop` 替換為 `dev-qa`.

## 將套件轉換為Git存放庫

依預設，封裝不包含 `.git/` 目錄。 Composer可以從Git簽出套件，而不是使用預先建立的Composer套件。 此方法的優點是，您可以在開發期間輕鬆修改套件。

1. 從移除模組 `vendor/` 目錄。

   ```bash
   rm -rf vendor/client/module-example
   ```

1. 使用重新安裝模組 [指定的Git來源](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. 確認Composer套件現在是Git存放庫：

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. 若要將多個模組批次轉換為Git存放庫（例如「使用者端」模組）：

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## 開始開發

1. 建立或出庫特徵/工作分支。 以下範例顯示與Jira票證名稱相同的分支。

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. 在變更模組中的分支後，請透過排清Adobe Commerce快取和靜態內容來檢視變更。

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## 使用您的開發更新主要專案

修改您的主要Git存放庫以更新您的 `composer.lock` 檔案。 如果您的模組是新的，請啟用它。

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
