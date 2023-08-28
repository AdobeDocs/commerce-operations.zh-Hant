---
title: Composer專案結構
description: 瞭解如何設定及維護全域參考架構範例中所述的個別套件選項。
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Composer專案結構

本指南說明如何設定及維護 [個別套件選項](../examples.md#option-1-separate-packages) 全球參考架構(GRA)範例中說明。

## 必要條件

開始之前，請先確認下列事項：

- 您有Git存放庫
- 您有Composer存放庫（本主題重點說明Private Packagist）
- 您已將Composer存放庫設定為映象 `repo.magento.com` 和 `packagist.org` 存放庫

## 主要Git專案存放庫

主要Git專案存放庫應僅包含Composer專案。 您可以使用Composer套件管理其他所有專案。 主要專案絕不應該包含下列檔案結構以外的任何內容，因為Composer會透過相依性安裝所有其他套件：

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

將下列內容新增至 `.gitignore` 檔案：

```tree
/*
!/composer.json
!/composer.lock
```

## 初始化主要專案

1. 建立名為的Git存放庫 `project-<region/country/brand>`.

1. 建立 `composer.json` 和 `composer.lock` 檔案：

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## 儲存非模組檔案

1. 新增 `app/etc/config.xml` 檔案存放庫中。

   您可以使用要建立的模組來安裝其他區域或品牌專屬檔案，例如 `.htaccess`、Google或Bing驗證文字檔、可執行檔，或其他不受Adobe Commerce模組管理的靜態檔案。

   使用 `magento2-component` 輸入套件以建立檔案對應，以在檔案複製期間將檔案複製到主Git存放庫 `composer install` 和 `composer update` 操作。

1. 建立遵循命名慣例的Git存放庫 `component-environment-<region/country/brand>`：

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. 新增 `app/etc/config.php` 檔案作為中的對應 `extra.map` 您的屬性 `composer.json` 檔案：

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. 驗證您的 `composer.json` 檔案並將其提交到Git存放庫：

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## 設定中繼

1. 建立下列Git存放庫：

   - `meta-gra`
   - `meta-<region/country/brand>`

1. 設定下列相依性樹狀結構：

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. 建立GRA中繼資料：

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 建立品牌中繼資料：

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 需要透過主要專案中的相依性管理進行收集：

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 確認撰寫器已複製 `app/etc/config.php` 檔案來源 `<client>/component-environment-<region/country/brand>`.

## 部署程式碼

在Web伺服器上，您可以使用Composer部署程式碼，但無法更新主要專案。 使用撰寫器重新安裝專案並搭配每個新部署，免除生產及測試伺服器存取Git的需求。

## 新增其他執行個體和套件

每個例項(地區、品牌或其他獨特的Adobe Commerce安裝)應各有不同 **主要專案** 例項， **特定中繼**、和 **環境元件套件**. 此 **GRA中繼資料** 應為 **已共用** 橫跨所有執行個體。

下列任一專案應需要功能套件(例如Adobe Commerce模組、主題、語言套件和程式庫)和協力廠商套件：

- **GRA中繼資料** — 安裝於 _全部_ 執行個體
- **例項特定中繼資料** — 適用於安裝在單一品牌或區域上

>[!IMPORTANT]
>
>不需要主專案的套件 `composer.json` 上的檔案 `main` 或 `release` 分支。

## 準備開發

若要進行開發，請安裝 `develop` 維護的所有模組版本。

根據您的分支策略，您可能會 `develop`， `qa`， `uat`、和 `main` 分支。 Composer中的每個分支都具有 `dev-` 前置詞。 因此 `develop` 可以透過Composer要求分支為版本 `dev-develop`.

1. 建立 `develop` 在所有模組和專案存放庫中分支。

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   上一步驟會在 `composer.json` 檔案：

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**不要合併** 這些 `composer.json` 對您的生產分支的檔案變更。 僅在上安裝穩定版本的套件 `release` 和 `main` 分支。 您可以定義下列相依性 `qa` 分支和其他非主要分支。
