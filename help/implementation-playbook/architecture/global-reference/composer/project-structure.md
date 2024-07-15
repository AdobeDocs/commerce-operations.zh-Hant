---
title: Composer專案結構
description: 瞭解如何設定及維護全域參考架構範例中所述的個別套件選項。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Composer專案結構

本指南說明如何設定及維護全域參考架構(GRA)範例中說明的[個別套件選項](../examples.md#option-1-separate-packages)。

## 必要條件

開始之前，請先確認下列事項：

- 您有Git存放庫
- 您有Composer存放庫（本主題重點說明Private Packagist）
- 您已將Composer存放庫設定為映象`repo.magento.com`和`packagist.org`存放庫

## 主要Git專案存放庫

主要Git專案存放庫應僅包含Composer專案。 您可以使用Composer套件管理其他所有專案。 主要專案絕不應該包含下列檔案結構以外的任何內容，因為Composer會透過相依性安裝所有其他套件：

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

將下列內容新增至`.gitignore`檔案：

```tree
/*
!/composer.json
!/composer.lock
```

## 初始化主要專案

1. 建立名為`project-<region/country/brand>`的Git存放庫。

1. 建立`composer.json`和`composer.lock`檔案：

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

1. 將`app/etc/config.xml`檔案新增至Git存放庫。

   您可以使用要建立的模組來安裝其他區域或品牌特定檔案，例如`.htaccess`、Google或Bing驗證文字檔、可執行檔，或其他未由Adobe Commerce模組管理的靜態檔案。

   使用`magento2-component`型別套件建立檔案對應，以在`composer install`和`composer update`作業期間將檔案複製到主要Git存放庫。

1. 建立遵循命名慣例`component-environment-<region/country/brand>`的Git存放庫：

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

1. 將`app/etc/config.php`檔案新增為`composer.json`檔案的`extra.map`屬性中的對應：

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

1. 驗證`composer.json`檔案並將其提交至Git存放庫：

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

1. 驗證Composer是否從`<client>/component-environment-<region/country/brand>`複製`app/etc/config.php`檔案。

## 部署程式碼

在Web伺服器上，您可以使用Composer部署程式碼，但無法更新主要專案。 使用撰寫器重新安裝專案並搭配每個新部署，免除生產及測試伺服器存取Git的需求。

## 新增其他執行個體和套件

每個執行個體(地區、品牌或其他獨特的Adobe Commerce安裝)應該有自己的&#x200B;**主要專案**&#x200B;執行個體、**特定中繼套件**&#x200B;和&#x200B;**環境元件套件**。 **GRA中繼資料**&#x200B;應在所有執行個體之間&#x200B;**共用**。

下列任一專案應需要功能套件(例如Adobe Commerce模組、主題、語言套件和程式庫)和協力廠商套件：

- **GRA Metapackage** — 安裝在&#x200B;_所有_&#x200B;執行個體上
- **執行個體專屬中繼套件** — 適用於安裝在單一品牌或區域上

>[!IMPORTANT]
>
>不需要位於`main`或`release`分支上主要專案的`composer.json`檔案中的封裝。

## 準備開發

若要進行開發，請安裝您維護之所有模組的`develop`版本。

根據您的分支策略，您可能會有`develop`、`qa`、`uat`和`main`個分支。 每個分支都存在於具有`dev-`首碼的撰寫器中。 因此`develop`分支必須透過Composer做為版本`dev-develop`。

1. 在所有模組和專案存放庫中建立`develop`個分支。

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

   上一步會在`composer.json`檔案中產生下列各行：

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**請勿將這`composer.json`個檔案變更合併**&#x200B;至您的生產分支。 僅在`release`和`main`分支上安裝穩定版本的套件。 您可以為`qa`個分支和其他非主要分支定義這些相依性。
