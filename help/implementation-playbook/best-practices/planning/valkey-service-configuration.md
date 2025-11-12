---
title: Valkey服務設定的最佳實務
description: 瞭解如何使用Adobe Commerce的延伸Valkey快取實作來改善快取效能。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 9157f0176ca562c25d87c873d220f8987917cb87
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Valkey服務設定的最佳實務

Adobe建議您在設定Valkey服務時遵循下列最佳實務：

## 設定Valkey L2快取

在`VALKEY_BACKEND`組態檔中設定`.magento.env.yaml`部署變數，以設定Valkey L2快取。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

如需雲端基礎結構上的環境設定，請參閱雲端基礎結構上的[`VALKEY_BACKEND`Commerce指南](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)中的&#x200B;__。

如需內部部署安裝，請參閱[設定指南](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching)中的&#x200B;_設定Valkey頁面快取_。

>[!NOTE]
>
>確認您使用的是最新版本的`ece-tools`封裝。 如果沒有，[升級至最新版本](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)。 您可以使用`composer show magento/ece-tools` CLI命令檢查本機環境中安裝的版本。

### L2快取記憶體大小(Adobe Commerce Cloud)

L2快取使用[暫存檔案系統](https://en.wikipedia.org/wiki/Tmpfs)做為儲存機制。 與專門化的索引鍵值資料庫系統相比，暫存檔案系統沒有控制記憶體使用的索引鍵逐出原則。

缺少記憶體使用量控制會累積過時的快取記憶體，導致L2快取記憶體使用量隨著時間增長。

為了避免L2快取記憶體耗盡，Adobe Commerce會在達到特定臨界值時清除儲存空間。 預設臨界值為95%。

請務必根據快取儲存裝置的專案需求，調整L2快取記憶體的最大使用量。 使用下列其中一種方法來設定記憶體快取大小：

- 建立支援票證以要求`/dev/shm`掛載的大小變更。
- 在應用程式層級調整`cleanup_percentage`屬性，以限制儲存的最大填充百分比。 剩餘的可用記憶體可供其他服務使用。
您可以在快取組態群組`cache/frontend/default/backend_options/cleanup_percentage`下的部署組態中調整組態。

>[!NOTE]
>
>Adobe Commerce 2.4.4已匯入`cleanup_percentage`組態選項。

下列範例顯示`CACHE_CONFIGURATION`檔案中的`.magento.env.yaml`：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

快取需求可能會因專案設定和自訂第三方程式碼而異。 L2快取記憶體大小調整範圍可讓L2快取記憶體在不需要臨界值點選的情況下運作。
理想情況下，L2快取記憶體的使用量應該穩定在低於臨界值的特定層級，以避免頻繁的儲存清除。

您可以使用下列CLI命令檢查叢集每個節點上的L2快取儲存記憶體使用量，然後搜尋`/dev/shm`行。
使用方式可能因不同節點而異，但應會收斂至相同值。

```bash
df -h
```

## 啟用Valkey從屬連線

啟用`.magento.env.yaml`組態檔中的Valkey從屬連線，只允許一個節點處理讀寫流量，而其他節點則處理唯讀流量。

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

如需詳細資訊，請參閱雲端基礎結構指南[上](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection)Commerce中的&#x200B;_VALKEY_USE_SLAVE_CONNECTION_。

針對Adobe Commerce內部部署安裝，請使用`bin/magento:setup`命令設定新的Valkey快取實作。 如需詳細資訊，請參閱[組態指南](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching)中的&#x200B;_使用預設快取的Valkey_。

>[!WARNING]
>
>請&#x200B;_不_&#x200B;為雲端基礎結構專案設定Valkey從屬連線，並採用[縮放/分割架構](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture)。 這會導致Valkey連線錯誤。 如需詳細資訊，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection)指南中的&#x200B;_Valkey設定指南_。

## 預先載入索引鍵

若要在頁面之間重複使用資料，請在`.magento.env.yaml`組態檔中列出預先載入的金鑰。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

如需內部部署安裝，請參閱[設定指南](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature)中的&#x200B;_Valkey預先載入功能_。

## 啟用過時的快取

使用過時的快取記憶體，並同時產生新的快取記憶體，可減少鎖定等待時間並提升效能，尤其是在處理大量區塊和快取金鑰時。 啟用過時的快取並在`.magento.env.yaml`組態檔中定義快取型別：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

>[!NOTE]
>
>在上一個範例中，`full_page`快取與雲端基礎結構專案上的Adobe Commerce無關，因為這些專案使用[Fastly](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/cdn/fastly)。

若要設定內部部署安裝，請參閱[設定指南](../../../configuration/cache/level-two-cache.md#stale-cache-options)中的&#x200B;_過時快取選項_。

部署期間，您應該會在[建置和部署記錄檔](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/test/log-locations#build-and-deploy-logs)中看到下列行：

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## 快取壓縮

如果您使用超過6GB的Valkey `maxmemory`，則可以使用快取壓縮來減少金鑰所消耗的空間。 請注意，使用者端效能是有代價的。 如果您有備用CPU，Adobe建議啟用它們。 請參閱[組態指南](../../../configuration/cache/valkey-session.md)中的&#x200B;_使用工作階段存放區_&#x200B;的Valkey。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
