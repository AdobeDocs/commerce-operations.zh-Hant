---
title: 服務配置路徑參考
description: 請參閱服務配置值清單。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# 服務配置路徑參考

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **服務**。

的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用配置檔案， `app/etc/config.php`，它應該在原始碼管理中。 要可選地覆蓋任何配置設定或設定敏感設定，請參閱 [使用環境變數覆蓋配置設定](override-config-settings.md#environment-variables)。 此主題確實 _不_ 清單 [敏感值和系統特定值](config-reference-sens.md)。

## Commerce Web API路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **服務** > **Web API**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 預設響應字元集 | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許匿名來賓訪問 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **服務** > **OAuth**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 客戶令牌生存時間（小時） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理令牌生存時間（小時） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清除概率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 到期期 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 到期期 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth使用者憑據HTTP Post max重定向 | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth使用者憑據HTTP後超時 | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
