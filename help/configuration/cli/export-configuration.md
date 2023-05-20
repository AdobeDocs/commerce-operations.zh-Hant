---
title: 導出配置設定
description: 將Adobe Commerce配置設定導出到配置檔案，也稱為配置轉儲。
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 導出配置設定

在Commerce 2.2及更高版本中 [流水線部署模型](../deployment/technical-details.md)，您可以跨系統維護一致的配置。 在開發系統的管理中配置設定後，請使用以下命令將這些設定導出到配置檔案：

```bash
bin/magento app:config:dump {config-types}
```

_配置類型_ 是要轉儲的配置類型清單（以空格分隔）。 可用類型包括 `scopes`。 `system`。 `themes`, `i18n`。 如果未指定配置類型，則命令將轉儲所有系統配置資訊。

以下示例僅轉儲作用域和主題：

```bash
bin/magento app:config:dump scopes themes
```

執行命令後，將更新以下配置檔案：

- `app/etc/config.php`

   這是所有Commerce實例的共用配置檔案。
將此內容包括在原始碼管理中，以便在開發、構建和生產系統之間共用。

   請參閱 [config.php引用](../reference/config-reference-configphp.md)。

- `app/etc/env.php`

   這是特定於環境的配置檔案。
它包含針對各個環境的敏感和系統特定的設定。

   做 _不_ 在原始碼管理中包含此檔案。

   請參閱 [env.php引用](../reference/config-reference-envphp.md)。

## 敏感或系統特定設定

設定寫入的敏感設定 `env.php`，使用 [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) 的子菜單。

通過引用將配置值指定為敏感值或特定於系統 [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) 在 [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) 的子菜單。

使用時導出其他系統設定 `config_types`，考慮使用 [`bin/magento config:set`](set-configuration-values.md#set-values) 的子菜單。
