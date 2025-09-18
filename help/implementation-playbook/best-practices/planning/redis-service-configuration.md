---
title: Redis服務組態的最佳作法
description: 瞭解如何使用Adobe Commerce的延伸Redis快取實作來改善快取效能。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 9dc17a7ec44d9c146fdc2ec48e128beacc298299
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Redis服務組態的最佳作法

- 設定Redis L2快取
- 啟用Redis從屬連線
- 預先載入索引鍵
- 啟用過時的快取
- 將Redis快取與Redis工作階段分開
- 壓縮Redis快取，並使用`gzip`進行較高的壓縮

## 設定Redis L2快取

在`REDIS_BACKEND`組態檔中設定`.magento.env.yaml`部署變數，以設定Redis L2快取。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

如需雲端基礎結構上的環境設定，請參閱雲端基礎結構上的[`REDIS_BACKEND`Commerce指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hant#redis_backend)中的&#x200B;__。

若為內部部署安裝，請參閱[設定指南](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)中的&#x200B;_設定Redis頁面快取_。

>[!NOTE]
>
>確認您使用的是最新版本的`ece-tools`封裝。 如果沒有，[升級至最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=zh-Hant)。 您可以使用`composer show magento/ece-tools` CLI命令檢查本機環境中安裝的版本。


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
>`cleanup_percentage`可設定的選項已在Adobe Commerce 2.4.4中匯入。

下列程式碼顯示`.magento.env.yaml`檔案中的設定範例：

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

您可以使用下列CLI命令來檢查叢集每個節點上的L2快取儲存記憶體使用量，並尋找`/dev/shm`行。
使用方式可能因不同節點而異，但應會收斂至相同值。

```bash
df -h
```

## 啟用Redis從屬連線

啟用`.magento.env.yaml`組態檔中的Redis從屬連線，只允許一個節點處理讀寫流量，而其他節點則處理唯讀流量。

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

請參閱雲端基礎結構指南[上的](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hant#redis_use_slave_connection)Commerce中的&#x200B;_REDIS_USE_SLAVE_CONNECTION_。

針對Adobe Commerce內部部署安裝，請使用`bin/magento:setup`命令設定新的Redis快取實作。 請參閱[組態指南](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)中的&#x200B;_使用預設快取_&#x200B;的Redis。

>[!WARNING]
>
>請&#x200B;_不_&#x200B;為雲端基礎結構專案設定Redis從屬連線（使用[縮放/分割架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html?lang=zh-Hant)）。 這會導致Redis連線錯誤。 請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hant#redis_use_slave_connection)指南中的&#x200B;_Redis設定指南_。

## 預先載入索引鍵

若要在頁面之間重複使用資料，請在`.magento.env.yaml`組態檔中列出預先載入的金鑰。

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

如需內部部署安裝，請參閱[設定指南](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature)中的&#x200B;_Redis預先載入功能_。

## 啟用過時的快取

使用過時的快取記憶體，並同時產生新的快取記憶體，可減少鎖定等待時間，並提升效能（尤其是在處理大量區塊和快取記憶體金鑰時）。 啟用過時的快取並在`config.php`設定檔案中定義快取型別（僅限雲端）：

```php
'cache' => [
        'frontend' => [
            'stale_cache_enabled' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'remote_backend_options' => [
                        'persistent' => 0,
                        'server' => 'localhost',
                        'database' => '4',
                        'port' => '6370',
                        'password' => ''
                    ],
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/'
                    ],
                    'use_stale_cache' => true,
                ],
                'frontend_options' => [
                    'write_control' => false,
                ],
            ]
        ],
        'type' => [
            'default' => ['frontend' => 'default'],
            'layout' => ['frontend' => 'stale_cache_enabled'],
            'block_html' => ['frontend' => 'stale_cache_enabled'],
            'reflection' => ['frontend' => 'stale_cache_enabled'],
            'config_integration' => ['frontend' => 'stale_cache_enabled'],
            'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
            'full_page' => ['frontend' => 'stale_cache_enabled'],
            'translate' => ['frontend' => 'stale_cache_enabled']
        ],
    ]
```

>[!NOTE]
>
>在上一個範例中，`full_page`快取與雲端基礎結構專案上的Adobe Commerce無關，因為它們使用[Fastly](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly)。

若要設定內部部署安裝，請參閱[設定指南](../../../configuration/cache/level-two-cache.md#stale-cache-options)中的&#x200B;_過時快取選項_。

## 單獨的Redis快取和工作階段例項

將Redis快取與Redis工作階段分開可讓您分別管理快取與工作階段。 它可防止快取問題影響工作階段，進而影響收入。 每個Redis執行個體都以自己的核心執行，可改善效能。

1. 更新`.magento/services.yaml`設定檔。

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

1. 更新`.magento.app.yaml`設定檔。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hant#submit-ticket)，以請求布建專用於生產和中繼環境工作階段的新Redis執行個體。 包含更新的`.magento/services.yaml`與`.magento.app.yaml`組態檔。 這不會造成任何停機時間，但需要部署才能啟用新服務。

1. 確認新執行個體正在執行，並記下連線埠號碼。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 將連線埠號碼新增至`.magento.env.yaml`設定檔。

   >[!IMPORTANT]
   >
   >只有在`ece-tools`無法從`MAGENTO_CLOUD_RELATIONSHIPS` redis工作階段服務定義自動偵測到它時，才設定redis工作階段連線埠。

   >[!NOTE]
   >
   >`disable_locking`必須設定為`1`。

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 從Redis快取執行個體上的[預設資料庫](../../../configuration/cache/redis-pg-cache.md) (`db 0`)移除工作階段。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

部署期間，您應該會在[建置和部署記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hant#build-and-deploy-logs)中看到下列行：

```
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

如果您使用超過6GB的Redis `maxmemory`，則可以使用快取壓縮來減少金鑰使用的空間。 請注意，使用者端效能是有代價的。 如果您有備用CPU，請啟用它。 請參閱[組態指南](../../../configuration/cache/redis-session.md)中的&#x200B;_使用工作階段存放區_&#x200B;的Redis。

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

## 啟用Redis非同步釋放(lazyfree)

若要在雲端基礎結構上的Adobe Commerce上啟用`lazyfree`，請提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hant#submit-ticket)，要求將下列Redis設定套用至您的環境：

```
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

啟用lazyfree時，Redis會將記憶體回收解除安裝到背景執行緒，以進行搬遷、過期、伺服器啟動的刪除、使用者刪除和復本資料集清除。 這減少了主執行緒封鎖，並可減少請求延遲。

>[!NOTE]
>
>`lazyfree-lazy-user-del yes`選項會使`DEL`命令的行為類似`UNLINK`，立即解除金鑰的連結，並非同步地釋放其記憶體。

>[!WARNING]
>
>由於釋放發生在背景，由已刪除/過期/收回的金鑰使用的記憶體會保持配置，直到背景執行緒完成工作為止。 如果您的Redis已處於記憶體緊張的壓力下，請謹慎測試並考慮先降低記憶體壓力（例如，針對特定案例停用區塊快取，並依上述說明區分快取和工作階段Redis執行個體）。

## 啟用Redis多執行緒I/O

若要在雲端基礎結構上的Adobe Commerce上啟用Redis I/O執行緒，請提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hant#submit-ticket)以請求下列設定。 這可以藉由從主執行緒解除安裝通訊端讀取/寫入和命令剖析來改善輸送量，但代價是需要增加的CPU使用量。 在載入下驗證並監視主機。

```
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
```

>[!NOTE]
>
>I/O執行緒只會平行處理使用者端I/O和剖析。 Redis指令執行仍維持單一執行緒。

>[!WARNING]
>
>啟用I/O執行緒可能會增加CPU的使用量，而且不會使每個工作負荷都受益。 從保守的值和基準開始。 如果延遲增加或CPU飽和，請減少`io-threads`或停用I/O執行緒中的讀取。

## 增加Redis使用者端逾時和重試次數

調整`.magento.env.yaml`中的後端選項，將快取使用者端的容許度提升為暫時性飽和度：

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            read_timeout: 10
            connect_retries: 5
```

這些設定會延長回覆等待視窗並重試連線設定，以增加使用者端對Redis短暫阻塞的容許度。 這可以減少在短期尖峰期間發生間歇性`cannot connect to localhost:6370`和讀取逾時錯誤。

>[!NOTE]
>
>它們不是持續性多載的修正。

## 其他資訊

- [Redis頁面快取](../../../configuration/cache/redis-pg-cache.md)
- [使用Redis進行工作階段儲存](../../../configuration/cache/redis-session.md)
