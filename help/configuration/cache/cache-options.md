---
title: 快取後端選項和儲存參考
description: 瞭解Adobe Commerce中的快取後端選項，包括檔案系統、Redis、Valkey和資料庫儲存。 探索Zend型(RemoteSynchronizedCache)和Symfony快取選項。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%
---
# 快取後端選項和儲存參考

>[!NOTE]
>
>此頁面會記錄內部部署`app/etc/env.php`設定。
>
>針對[!DNL Adobe Commerce on Cloud]個專案，`ece-tools`封裝會在部署期間根據`.magento.env.yaml`中的部署變陣列態產生結果`app/etc/env.php`組態。 您沒有編輯`env.php`檔案。  請參閱[Valkey與Redis服務組態的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration)與[部署變數](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)。

Commerce應用程式使用低階快取前端和後端來提供對快取儲存體的存取權。 Commerce支援數個快取後端和策略，分別適用於不同的使用案例。 此頁面說明可用的後端及其差異。

>[!NOTE]
>
>[Varnish](config-varnish-install.md)會處理內部部署的HTTP層級完整頁面快取。 [Fastly服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly)會處理它以進行雲端部署。 這兩種解決方案都未使用低階快取後端。

## 後端快取選項

下表總結列出可用的後端快取：

| 後端 | 說明 | 設定指南 |
| ------- | ----------- | ------------------- |
| 檔案系統 | 預設。 將快取資料儲存在`var/cache/`下的檔案中。 不需要設定。 | 不適用 |
| Redis | 記憶體中的資料存放區，用於高效能快取。 | [使用Redis作為預設快取](redis-pg-cache.md) |
| Valkey | 開放原始碼、與Redis相容的替代方案。 | [使用預設快取的Valkey](valkey-pg-cache.md) |
| 資料庫 | 由資料庫支援的自訂快取引擎 | [建立自訂快取引擎](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} （Adobe Developer檔案） |

>[!IMPORTANT]
>
>Adobe Commerce 2.4.9或更新於2.4.5-p16、2.4.6-p14、2.4.7-p9和2.4.8-p4的修補程式版本不支援Redis快取。 如果您要升級至其中一個版本，請設定Valkey並更新快取設定以使用它。 若為[!DNL Adobe Commerce on-premises]，請參閱[設定Valkey](config-valkey.md)。

## 快取後端和L2實施 {#implementation-approaches}

Commerce支援直接快取後端和L2快取。 直接後端會選取快取儲存空間。 L2快取在遠端儲存體前面新增本機快取階層。

### 直接快取後端

下表摘要`<Commerce-install-dir>/app/etc/env.php`的快取後端組態值。 它不會啟用L2快取。

| Commerce版本 | 後端 | 設定值 |
| ---------------- | ------- | -------------------- |
| 2.4.8和較舊版本（若支援） | 檔案 | 預設。 不需要設定 |
| 2.4.8和較舊版本（若支援） | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8和較舊版本（若支援） | Valkey | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9和更新版本，加上支援的背板連線埠 | 檔案 | `file` |
| 2.4.9和更新版本，加上支援的背板連線埠 | Valkey | `valkey` |

如需確切的修補程式層級支援，請參閱[系統需求](../../installation/system-requirements.md)。

>[!TAB Zend型快取（2.4.8和更早版本）]

#### 後端範例

對於內部部署，下列範例會在`<Commerce-install-dir>/app/etc/env.php`中設定直接快取後端。 它們不會啟用L2快取。 請勿在[!DNL Adobe Commerce on Cloud]部署中使用這些範例，這些部署會在部署期間使用`ece-tools`封裝產生結果`app/etc/env.php`組態。

>[!BEGINTABS]

>[!TAB Redis]

只有在支援Redis的發行版本上才使用完整的Redis類別名稱：

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Valkey]

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

## L2快取

L2 （兩級）快取會在共用遠端快取儲存體前的每個Web節點上新增本機快取階層，減少Commerce與遠端快取之間的網路流量。 如需實作選項、版本支援和組態步驟，請參閱[L2快取組態](level-two-cache.md)。

對於雲端專案，請透過[部署變數](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}中所述的部署變數來設定L2快取。

- [預設快取使用Redis](redis-pg-cache.md)
- [使用Valkey作為預設快取](valkey-pg-cache.md)
- [L2快取設定](level-two-cache.md)
