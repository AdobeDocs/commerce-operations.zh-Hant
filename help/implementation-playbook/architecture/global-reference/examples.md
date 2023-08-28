---
title: 全球參考架構範例
description: 請參閱管理大型Adobe Commerce專案的程式碼範例。
role: Developer, Architect
level: Experienced
source-git-commit: 64f330919abab9644de1163c9a6d6501a9c50cc1
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# 全球參考架構範例

本主題說明組織網路的常見方式 [全球參考架構(GRA)](overview.md) 程式碼基底。 雖然 [單獨的套件](#option-1-separate-packages) 建議使用選項，某些情況下則需要以下所述的其他選項之一。

## 定義

{{$include /help/_includes/gra-definitions.md}}

## 選項1：個別套件

另請參閱 [Composer專案結構](composer/project-structure.md) 設定此方法的最佳作法。

![說明全域參考架構之個別套件選項的圖表](../../../assets/playbooks/gra-separate-packages.png)

管理GRA Composer套件的最靈活方式是透過中繼套件。 中繼資料包含 `composer.json` 僅檔案，定義其他套裝軟體相依性。 使用建立中繼套件 [私人封裝者](https://packagist.com/) 存放庫。

### 主要專案 `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

每個模組、語言套件、主題和程式庫都有自己的Git存放庫。 每個Git存放庫都會自動同步至私人封裝存放庫，並在那裡產生套件（只要有） `composer.json` Git存放庫根目錄中的檔案。

## 選項2：大量套件

以下是單一Composer套件中多個模組的範例。

大量套件只能包含相同型別的套件。 例如，如果您有Adobe Commerce模組、主題、語言套件和程式庫的多個套件，則必須為每種型別建立個別的大量套件。

廠商目錄內的檔案結構看起來應該像下面的範例。 不過，請檢查您的專案，檢視應包含在您的Git存放庫中的專案)：

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

此 `composer.json` 檔案應如下所示：

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## 選項3：分割Git

此架構使用四個Git存放庫來儲存程式碼：

- `core`：包含Adobe Commerce核心安裝。 用於升級Adobe Commerce版本。
- `GRA`：包含GRA程式碼。 所有GRA模組、語言套件、白色標籤主題和程式庫。
- `brand/region`：每個品牌或地區有其專屬的存放庫，僅包含品牌或地區專屬的程式碼。
- `release`：上述所有專案都會合併至此Git存放庫。 此處只允許合併認可。

![說明全域參考架構之分割Git選項的圖表](../../../assets/playbooks/gra-split-git.png)

若要設定此選項：

1. 在Git中建立四種存放庫型別。 建立 `core` 和 `GRA` 存放庫僅一次。 建立一個 `brand/region` 和一個 `release` 每個品牌的存放庫。

   建議的存放庫名稱：

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (例如， `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (例如， `m2-release-emea`/`m2-release-adobe`)

1. 建立 `release/` 目錄，並執行下列動作，為所有存放庫建立共用的Git記錄。

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. 複製每個存放庫，但 `core`，位於電腦的不同目錄中。

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [使用撰寫器安裝Adobe Commerce](../../../installation/composer.md). 移除 `.gitignore` 檔案，新增 `core` 遠端、新增及認可程式碼，以及推播。

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. 在 `GRA` 存放庫，建立下列目錄：

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. 新增程式碼。 移除 `.gitignore` 檔案、新增並認可程式碼、新增遠端並推播。

1. 在 `brand/region` 存放庫。 執行與中的相同的操作 `GRA` 並牢記檔案必須是唯一的。 您無法同時在此存放庫和 `GRA` 存放庫。

1. 在 `release` 存放庫，套用合併。

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. 移除 `.gitkeep` 檔案。

1. 部署 `release` 存放庫至生產、測試、QA和開發伺服器。 升級 `core`， `GRA`、和 `brand` 程式碼可以輕鬆執行下列命令：

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## 選項4：Monorepo （建議）

此策略相當模擬Magento Open SourceGit存放庫的運作方式。

所有程式碼都在單一存放庫中開發和測試。 自動化會從此單一存放庫擷取套件，這些套件可以使用Composer安裝在UAT和生產環境中。

![說明全域參考架構之monorepo選項的圖表](../../../assets/playbooks/gra-monorepo1.png)

monorepo選項可讓您在單一存放庫中輕鬆工作，同時提供使用套件構成執行個體的靈活性。

版本設定和封裝蒸餾是使用GitHub動作或GitLab動作透過自動化完成的。

![說明全域參考架構之monorepo選項的圖表](../../../assets/playbooks/gra-monorepo2.png)

如需此自動化的詳細資訊，請參閱下列資源：

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>設定monorepo是進階功能，但以最低的間接成本提供最大的彈性。

## 不要混合策略

不建議針對GRA套件和 `app/` 品牌或區域套件的目錄。

您不僅獲得 _優點_ 但也是 _缺點_ 兩種方法的。 您應該挑選其中一項（Git或撰寫器），才能以最佳方式運作。

## 要避免的解決方案

- **表示GRA或品牌的模組命名慣例**

  代表GRA或品牌的命名模組導致缺乏彈性。 請改用Composer中繼資料來判斷模組所屬的群組。 例如，對於客戶VF，封裝 `vf/meta-gra` 包含所有GRA套件的參考，且可使用進行安裝。 `composer require vf/meta-gra` 命令。 封裝 `vf/meta-kipling` 包含所有Kipling特定套件的參考，以及 `vf/meta-gra` 封裝。 模組已命名 `vf/module-sales` 和 `vf/module-sap` 例如。 此命名慣例可讓您在品牌和GRA狀態之間移動套件，且影響較低。

- **每個執行個體的Adobe Commerce核心升級**

  為不同品牌或地區排程Adobe Commerce核心升級（包括修補程式升級），以儘可能緊密地一起執行。 由於相容性限制，針對共用模組支援多個Adobe Commerce版本會導致模組出現分叉現象，並使維護工作增加一倍多。 在繼續定期開發之前，請確定所有執行個體都在相同的Adobe Commerce版本上執行，以防止工作量增加。
