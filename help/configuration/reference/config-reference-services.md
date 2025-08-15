---
title: 服務設定路徑參考
description: 請參閱服務組態值清單。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# 服務設定路徑參考

此區段列出&#x200B;**商店** >設定> **設定** > **服務**&#x200B;底下「管理員」中選項的變數名稱和設定路徑。

[`magento app:config:dump`命令](../cli/export-configuration.md)將這些值寫入到共用組態檔`app/etc/config.php`，它應該是在原始檔控制中。 若要選擇性地覆寫任何組態設定或設定敏感設定，請參閱[使用環境變數覆寫組態設定](override-config-settings.md#environment-variables)。 此主題&#x200B;_不_&#x200B;列出[敏感值和系統特定值](config-reference-sens.md)。

## Commerce Web API路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **服務** > **網頁API**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 預設回應字元集 | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許匿名訪客存取 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **服務** > **OAuth**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 客戶權杖存留期（小時） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理Token期限（小時） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清除機率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效期 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效期 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth消費者憑證HTTP貼文最大重新導向 | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth消費者憑證HTTP Post逾時 | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
