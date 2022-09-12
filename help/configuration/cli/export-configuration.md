---
title: 導出配置設定
description: 將Adobe Commerce組態設定匯出至組態檔，也稱為組態傾印。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# 導出配置設定

在Commerce 2.2及更新版本中 [管道部署模型](../deployment/technical-details.md)，您可以跨系統維持一致的設定。 在開發系統的「管理員」中設定設定後，請使用下列命令將這些設定匯出至設定檔：

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ 是以空格分隔的要傾印的組態類型清單。 可用類型包括 `scopes`, `system`, `themes`，和 `i18n`. 如果未指定配置類型，則命令將轉儲所有系統配置資訊。

以下示例僅轉儲作用域和主題：

```bash
bin/magento app:config:dump scopes themes
```

命令執行後，會更新下列組態檔：

- `app/etc/config.php`

   這是所有Commerce執行個體的共用設定檔案。
將此內容納入您的原始碼控制中，以便在開發、構建和生產系統之間共用。

   請參閱 [config.php參考](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   這是特定於環境的配置檔案。
它包含個別環境的敏感和系統專屬設定。

   做 _not_ 將此檔案包含在原始碼控制項中。

   請參閱 [env.php參考](../reference/config-reference-envphp.md).

## 敏感或系統特定設定

設定寫入的敏感設定 `env.php`，請使用 [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) 命令。

配置值通過引用指定為敏感值或系統特定值 [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) 在模組的 [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) 檔案。

要導出其他系統設定，請使用 `config_types`，請考慮使用 [`bin/magento config:set`](set-configuration-values.md#set-values) 命令。
