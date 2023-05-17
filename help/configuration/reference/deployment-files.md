---
title: 部署的配置檔案
description: 了解設定檔如何用於安裝商務應用程式。
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: dd990800551dd2ba35ebc7d2bc04edeb1b183d6f
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 部署的配置檔案

Adobe Commerce提供組態檔，讓您輕鬆自訂元件並建立組態類型以擴充預設功能。 部署配置過程包含用於安裝的共用和特定於系統的配置。 商務的部署配置由 [`app/etc/config.php`](../reference/config-reference-configphp.md) 和 [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` 是 _共用_ 設定檔。
該檔案包含已安裝的模組、主題和語言包的清單；和共用組態設定。

   將此檔案檢入到原始碼控制項，並在開發、測試和生產系統中使用它。

- `app/etc/env.php` 包含安裝環境專屬的設定。

一起， `config.php` 和 `env.php` 稱為商務 _部署配置_ 因為檔案是在安裝期間建立的，是啟動商務應用程式的必要檔案。

>[!INFO]
>
>此 [!DNL Commerce 2] 部署組態已更換 `local.xml` in [!DNL Magento 1.x].

與其他 [模組配置檔案](../reference/module-files.md)，則初始化期間、未與任何其他檔案合併且無法擴充時，商務部署設定會載入記憶體中。 (`config.php` 和 `env.php` 不過，會相互合併。)

## 部署配置的詳細資訊

`config.php` 和 `env.php` 是返回 [多維關聯陣列](https://www.w3schools.com:443/php/php_arrays.asp)，基本上是配置參數和值的分層排列。

此陣列的頂級為 _設定區段_. 段具有由任意鍵區分的任意內容（標量值或嵌套陣列），其中鍵和值對均由Commerce框架定義。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) 僅提供這些區段的存取權，但不允許您延伸這些區段。

在下一個層次級別，每個段中的項目根據模組序列定義進行排序，該定義通過合併除禁用模組之外的所有模組的配置檔案而獲得。

以下幾節將討論部署配置的結構和內容：

- 管理已安裝的模組
- 系統特定配置

## 管理已安裝的模組

此 `config.php` 檔案包含已安裝模組的清單。 Adobe Commerce提供命令列和網頁型公用程式，以管理模組（安裝、解除安裝、啟用、停用或升級）。

範例：

- 卸載元件： [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- 檢查元件的狀態： [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- 啟用或禁用元件： [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

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

值 `1` 或 `0` 指示模組是啟用還是禁用。

禁用的模組不能被Commerce應用程式識別；換句話說，使用者不會參與合併設定、相依性插入、事件、外掛程式等。 禁用的模組不會修改店面或管理員，也不會影響路由。

禁用模組和代碼庫中缺少模組的唯一實際區別是自動載入器找到禁用模組，其類和常數可在其他代碼中重用。
