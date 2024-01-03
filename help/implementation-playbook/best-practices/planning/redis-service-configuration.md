---
title: Redis服務組態的最佳作法
description: 瞭解如何使用Adobe Commerce的延伸Redis快取實作來改善快取效能。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 6772c4fe31cfcd18463b9112f12a2dc285b39324
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Redis服務組態的最佳作法

- 設定Redis L2快取
- 啟用Redis從屬連線
- 預先載入索引鍵
- 啟用過時的快取
- 將Redis快取與Redis工作階段分開
- 壓縮Redis快取並使用 `gzip` 以取得較高的壓縮率

## 設定Redis L2快取

設定Redis L2快取記憶體，方法是設定 `REDIS_BACKEND` 中的部署變數 `.magento.env.yaml` 組態檔。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

如需雲端基礎結構上的環境設定，請參閱 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 在 _雲端基礎結構上的Commerce指南_.

若為內部部署安裝，請參閱 [設定Redis頁面快取](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) 在 _設定指南_.

>[!NOTE]
>
>確認您使用的是最新版本的 `ece-tools` 封裝。 如果沒有， [升級至最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). 您可以使用檢查安裝在本機環境中的版本 `composer show magento/ece-tools` CLI命令。


### L2快取記憶體大小調整(Adobe Commerce Cloud)

L2快取使用 [暫存檔案系統](https://en.wikipedia.org/wiki/Tmpfs) 作為儲存機制。 與專門化的索引鍵值資料庫系統相比，暫存檔案系統沒有控制記憶體使用的索引鍵逐出原則。

缺少記憶體使用量控制會累積過時的快取記憶體，導致L2快取記憶體使用量隨著時間增長。

為了避免L2快取記憶體耗盡，Adobe Commerce會在達到特定臨界值時清除儲存空間。 預設臨界值為95%。

請務必根據快取儲存裝置的專案需求，調整L2快取記憶體的最大使用量。 使用下列其中一種方法來設定記憶體快取大小：

- 建立支援票證以請求 `/dev/shm` 掛載。
- 調整 `cleanup_percentage` 應用程式層級的屬性，以限制儲存體的最大填入百分比。 剩餘的可用記憶體可供其他服務使用。
您可以在快取組態群組下的部署組態中調整組態 `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>此 `cleanup_percentage` 可設定的選項已在Adobe Commerce 2.4.4中推出。

下列程式碼顯示 `.magento.env.yaml` 檔案：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

快取需求可能會因專案設定和自訂第三方程式碼而異。 L2快取記憶體大小調整範圍可讓L2快取記憶體在不發生太多臨界值點選的情況下運作。
理想情況下，L2快取記憶體的使用量應該穩定在低於臨界值的特定層級，以避免頻繁的儲存清除。

您可以使用下列CLI命令來檢查叢集每個節點上的L2快取記憶體使用量，並尋找 `/dev/shm` 行。
使用方式可能因不同節點而異，但應會收斂至相同值。

```bash
df -h
```

## 啟用Redis從屬連線

在中啟用Redis從屬連線 `.magento.env.yaml` 設定檔，僅允許一個節點處理讀寫流量，而其他節點則處理唯讀流量。

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

另請參閱 [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 在 _雲端基礎結構上的Commerce指南_.

針對Adobe Commerce內部部署安裝，請使用 `bin/magento:setup` 命令。 另請參閱 [預設快取使用Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) 在 _設定指南_.

>[!WARNING]
>
>執行 _非_ 使用設定雲端基礎結構專案的Redis從屬連線 [縮放/分割架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 這會導致Redis連線錯誤。 另請參閱 [Redis設定指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 在 _雲端基礎結構上的Commerce_ 指南。

## 預先載入索引鍵

若要在頁面之間重複使用資料，請列出要在頁面中預先載入的金鑰， `.magento.env.yaml` 組態檔。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

若為內部部署安裝，請參閱 [Redis預先載入功能](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) 在 _設定指南_.

## 啟用過時的快取

使用過時的快取記憶體，並同時產生新的快取記憶體，可減少鎖定等待時間，並提升效能（尤其是在處理大量區塊和快取記憶體金鑰時）。 啟用過時的快取並在以下位置定義快取型別： `.magento.env.yaml` 設定檔：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

如需設定內部部署安裝，請參閱 [過時的快取選項](../../../configuration/cache/level-two-cache.md#stale-cache-options) 在 _設定指南_.

## 單獨的Redis快取和工作階段例項

將Redis快取與Redis工作階段分開可讓您分別管理快取與工作階段。 它可防止快取問題影響工作階段，進而影響收入。 每個Redis執行個體都以自己的核心執行，可改善效能。

1. 更新 `.magento/services.yaml` 組態檔。

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. 更新 `.magento.app.yaml` 組態檔。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 提交 [Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 請求布建專用於生產和中繼環境工作階段的新Redis執行個體。 包含更新的 `.magento/services.yaml` 和 `.magento.app.yaml` 組態檔。 這不會造成任何停機時間，但需要部署才能啟用新服務。

1. 確認新執行個體正在執行，並記下連線埠號碼。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 將連線埠號碼新增至 `.magento.env.yaml` 組態檔。

   >[!NOTE]
   >`disable_locking` 必須設為 `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 從移除工作階段 [預設資料庫](../../../configuration/cache/redis-pg-cache.md) (`db 0`)時，才會追蹤退出連結。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

部署期間，您應該會在 [建置和部署記錄](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs)：

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## 快取壓縮

如果您使用超過6GB的Redis `maxmemory`，您可以使用快取壓縮來減少索引鍵使用的空間。 請注意，使用者端效能是有代價的。 如果您有備用CPU，請啟用它。 另請參閱 [使用Redis進行工作階段儲存](../../../configuration/cache/redis-session.md) 在 _設定指南_.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 其他資訊

- [Redis頁面快取](../../../configuration/cache/redis-pg-cache.md)
- [使用Redis進行工作階段儲存](../../../configuration/cache/redis-session.md)
