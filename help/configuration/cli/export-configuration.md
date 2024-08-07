---
title: 匯出組態設定
description: 將Adobe Commerce組態設定匯出至組態檔（也稱為組態傾印）。
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 匯出組態設定

在Commerce 2.2和更新版本的[管道部署模型](../deployment/technical-details.md)中，您可以跨系統維持一致的設定。 在開發系統的「管理員」中設定設定之後，請使用下列命令將這些設定匯出至組態檔：

```bash
bin/magento app:config:dump {config-types}
```

_config_types_&#x200B;是以空格分隔的要傾印的設定型別清單。 可用的型別包括`scopes`、`system`、`themes`和`i18n`。 如果未指定組態型別，則命令會傾印所有系統組態資訊。

以下範例僅傾印範圍和主題：

```bash
bin/magento app:config:dump scopes themes
```

命令執行後，會更新下列組態檔：

- `app/etc/config.php`

  這是所有Commerce執行個體的共用設定檔。
將此專案納入原始檔控制，以便在開發、組建和生產系統之間共用。

  請參閱[config.php參考](../reference/config-reference-configphp.md)。

- `app/etc/env.php`

  這是特定於環境的組態檔。
它包含適用於個別環境的敏感和系統專屬設定。

  請&#x200B;_不_&#x200B;將此檔案包含在原始檔控制中。

  請參閱[env.php參考](../reference/config-reference-envphp.md)。

## 敏感或系統專屬設定

若要設定寫入`env.php`的敏感設定，請使用[`bin/magento config:sensitive:set`](set-configuration-values.md#set-values)命令。

透過參照模組[`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific)檔案中的[`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php)，將組態值指定為敏感或系統特定的。

若要在使用`config_types`時匯出其他系統設定，請考慮使用[`bin/magento config:set`](set-configuration-values.md#set-values)命令。
