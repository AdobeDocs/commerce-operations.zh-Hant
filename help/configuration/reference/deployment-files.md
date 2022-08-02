---
title: 部署的配置檔案
description: 瞭解配置檔案在安裝Commerce應用程式時的工作方式。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# 部署的配置檔案

Adobe Commerce提供配置檔案，使您能夠輕鬆自定義元件並建立配置類型以擴展預設功能。 部署配置過程由用於安裝的共用配置和特定於系統的配置組成。 商務的部署配置分為 [`app/etc/config.php`](../reference/config-reference-configphp.md) 和 [`app/etc/env.php`](../reference/config-reference-envphp.md)。

- `app/etc/config.php` 是 _共用_ 配置檔案。
該檔案包含已安裝的模組、主題和語言包的清單；和共用配置設定。

   將此檔案簽入到原始碼管理中，並將其用於開發、轉移和生產系統。

   從2.2版開始， `app/etc/config.php` 檔案不再是 `.gitignore` 的子菜單。
這樣做是為了促進 [管道部署](../deployment/technical-details.md)。

- `app/etc/env.php` 包含特定於安裝環境的設定。

一起， `config.php` 和 `env.php` 稱為Commerce _部署配置_ 因為檔案是在安裝過程中建立的，並且啟動Commerce應用程式時需要這些檔案。

>[!INFO]
>
>的 [!DNL Commerce 2] 部署配置替換 `local.xml` 在 [!DNL Magento 1.x]。

與其他 [模組配置檔案](../reference/module-files.md)，在初始化期間，Commerce部署配置將載入到記憶體中，未與任何其他檔案合併，因此無法擴展。 (`config.php` 和 `env.php` 但是，它們會相互合併。)

## 有關部署配置的詳細資訊

`config.php` 和 `env.php` 是返回的PHP檔案 [多維關聯陣列](https://www.w3schools.com:443/php/php_arrays.asp)基本上是配置參數和值的分層排列。

此陣列的頂層 _配置段_。 段具有由任意鍵區分的任意內容（標量值或嵌套陣列），其中鍵和值對都由Commerce框架定義。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) 僅提供對這些節的訪問權限，但不允許擴展這些節。

在下一個層次級別上，每個段中的項目根據 [模組](https://glossary.magento.com/module) 序列定義，它通過合併除禁用模組外的所有模組配置檔案來獲得。

以下各節討論部署配置的結構和內容：

- 管理已安裝的模組
- 系統特定配置

## 管理已安裝的模組

的 `config.php` 檔案包含已安裝模組的清單。 Adobe Commerce提供命令行和基於web的實用程式來管理模組（安裝、卸載、啟用、禁用或升級）。

示例：

- 卸載元件： [`bin/magento setup:uninstall`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall.html)
- 檢查元件的狀態： [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- 啟用或禁用元件： [`bin/magento module:disable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable)。 [`bin/magento module:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable)。

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

值 `1` 或 `0` 指示是啟用還是禁用模組。

Commerce應用程式無法識別禁用的模組；換句話說，它們不參與合併配置、依賴項注入、事件、插件等。 禁用的模組不修改 [店面](https://glossary.magento.com/storefront) 或 [管理](https://glossary.magento.com/admin) 不影響路由。

在代碼庫中，禁用模組和缺失模組的唯一實際區別是，自動載入器找到了禁用模組，其類和常數可用於在其他代碼中重用。
