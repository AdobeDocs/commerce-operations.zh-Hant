---
title: Redis和Valkey服務組態的最佳作法
description: 瞭解如何設定Adobe Commerce的Redis和Valkey服務。 使用L2快取記憶體、從屬連線、過時快取記憶體及工作階段分離來改善快取效能。
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="雲端上的Commerce" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案上的Adobe Commerce 。"
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: '2010'
ht-degree: 0%

---


# Redis和Valkey服務組態的最佳作法

使用這些建議來設定Adobe Commerce在雲端上的Redis或Valkey快取和工作階段。 如需內部部署快取組態，請參閱[快取後端選項和存放裝置參考](../../../configuration/cache/cache-options.md)。

- 設定L2快取
- 啟用從屬連線
- 預先載入索引鍵
- 啟用過時的快取
- 分隔快取和工作階段
- 壓縮快取
- 設定範例

>[!NOTE]
>
>確認您使用的是最新版本的`ece-tools`封裝。 如果沒有，[升級至最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html)。 您可以使用`composer show magento/ece-tools` CLI命令檢查本機環境中安裝的版本。

## 設定L2快取

在`.magento.env.yaml`組態檔中設定`REDIS_BACKEND`或`VALKEY_BACKEND`部署變數，以設定L2快取。

如需實作詳細資料、設定範例，以及部署特定的指南，請參閱效能最佳化的[L2快取設定](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/level-two-cache)。

>[!BEGINTABS]

>[!TAB Redis組態]

對於Redis，請使用：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

如需環境組態詳細資訊，請參閱&#x200B;_雲端基礎結構上的Commerce指南_&#x200B;中的[`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend)。

>[!TAB Valkey組態]

對於Valkey，請使用：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

如需環境組態詳細資訊，請參閱雲端基礎結構指南上的&#x200B;_Commerce_&#x200B;中的[`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)組態變數。

>[!ENDTABS]


### 適用於Adobe Commerce Cloud的L2快取記憶體大小

L2快取使用[暫存檔案系統](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`)作為其儲存機制。 與專門化的機碼值存放區不同，tmpfs沒有機碼收回原則，因此記憶體使用量可能會無限增加。 為避免耗盡，當使用量達到可設定的臨界值（預設為95%）時，Adobe Commerce會自動清除L2儲存空間。 您可以要求較大的`/dev/shm`掛載或降低清除臨界值，以控制記憶體耗用量。

根據您的專案需求，調整L2快取記憶體使用量上限。 使用下列其中一種方法：

- 建立支援票證以調整`/dev/shm`掛載大小。 針對此案例，Adobe建議將`/dev/shm`掛載大小設定為15 GB。
- 在應用程式層級調整`cleanup_percentage`屬性，以限制儲存使用量，並釋放其他服務可用的記憶體。
您可以在快取組態群組`cache/frontend/default/backend_options/cleanup_percentage`下的部署組態中調整組態。

>[!NOTE]
>
>`cleanup_percentage`可設定的選項已在Adobe Commerce 2.4.4中匯入。

下列範例顯示`.magento.env.yaml`檔案中的設定程式碼：

>[!BEGINTABS]

>[!TAB Redis組態]

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

>[!TAB Valkey組態]

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

>[!ENDTABS]

快取需求會因您的專案設定和自訂第三方程式碼而異。 設定L2快取記憶體的大小，讓快取運作時不會頻繁發生臨界值點選。

理想情況下，L2快取記憶體的使用量會穩定在臨界值以下，以避免頻繁的儲存清除。

您可以執行下列CLI命令並檢閱`/dev/shm`行，檢查叢集每個節點上的L2快取儲存記憶體使用量。

```shell
df -h /dev/shm
```

使用方式會因節點而異，但應該會收斂到類似的值。

## 啟用從屬連線

啟用`.magento.env.yaml`檔案中的從屬連線，讓Adobe Commerce使用額外的唯讀快取連線進行讀取，同時繼續使用主要端點進行寫入。 此設定可減少主要快取服務的讀取負載，並更有效地分配讀取流量。

>[!BEGINTABS]

>[!TAB Redis組態]

對於Redis，請使用：

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

如需環境變陣列態詳細資訊，請參閱雲端基礎結構指南上的&#x200B;_Commerce_&#x200B;中的[REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection)。

>[!TAB Valkey組態]

對於Valkey，請使用：

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

如需環境變陣列態詳細資訊，請參閱雲端基礎結構指南上的&#x200B;_Commerce_&#x200B;中的[VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection)。

>[!ENDTABS]

## 預先載入索引鍵

Magento通常會一次從Redis或Valkey載入一個索引鍵中的快取專案。 預先載入功能可讓您提供常用索引鍵清單，Magento會在第一次存取請求期間，於單一管道中擷取這些索引鍵。 接著Magento會將擷取的值保留在PHP記憶體中以供該要求剩餘部分使用，如此可減少重複的Redis或Valkey來回，並可改善這些金鑰的要求啟動載入效能。

您可以透過監視Redis或Valkey上的作用中命令來識別常用金鑰：

>[!BEGINTABS]

>[!TAB Redis預先載入金鑰組態]

預先載入金鑰是在`.magento.env.yaml`組態檔中設定。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

若要列出索引鍵，請執行以下命令：

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10秒後，按&#x200B;**[!UICONTROL Ctrl+C]**。 然後執行下列命令：

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

此記錄會列出您可以預先載入的金鑰。 若要檢視索引鍵的內容，請執行以下命令：

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

>[!TAB Valkey預先載入金鑰組態]

預先載入金鑰是在`.magento.env.yaml`組態檔中設定。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

若要列出索引鍵，請執行以下命令：

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10秒後，按&#x200B;**[!UICONTROL Ctrl+C]**。 然後執行下列命令：

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

此記錄會列出您可以預先載入的金鑰。 若要檢視索引鍵的內容，請執行以下命令：

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

>[!ENDTABS]

## 啟用過時的快取

過時快取是`RemoteSynchronizedCache`的L2快取功能。 啟用後，Adobe Commerce可在另一個要求已重新產生相同專案時，從`/dev/shm`提供現有的本機快取值，而非讓每個並行要求等待。 這減少了重新產生昂貴快取專案時快取串流和鎖爭用。

### 運作方式

透過`RemoteSynchronizedCache`，Magento會維護每個快取專案的兩個復本： `/dev/shm`中的本機復本，以及Redis或Valkey中的遠端復本。 當遠端副本無法使用且該金鑰已存在重新產生鎖定時，並行要求可以接收先前的本機值，而不是等到寫入新的值為止。

若要啟用過時的快取，請在`.magento.env.yaml`檔案中進行設定。

>[!BEGINTABS]

>[!TAB 設定Redis的過時快取]

針對Redis：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB 設定Valkey的過時快取]

若為Valkey：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>`full_page`快取型別與雲端基礎結構專案上的Adobe Commerce無關，因為它們使用[Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)。

>[!WARNING]
>
>上述設定會在`default`快取前端啟用過時的快取，這會將過時的快取行為套用至使用該前端的所有快取專案。 使用此設定時，Magento核心快取型別通常會如預期般運作。 不過，如果您的專案包含自訂程式碼或擴充功能，這些程式碼或擴充功能會透過一般`\Magento\Framework\App\Cache` API （例如`$this->cache->save()`）寫入快取而沒有專用的快取前端，則這些專案也可以在重新產生期間提供過時的值。
>
>
>如果這會在您的自訂內容中造成非預期的行為，請在`default`前端停用過時快取，並只對選取的快取型別啟用它，如通常的[內部部署](../../../configuration/cache/level-two-cache.md#stale-cache-options)一樣。

### 分別啟用每個快取型別的過時快取

您只能透過在`.magento.env.yaml`中定義專用快取前端並將選取的快取型別對應到它來啟用選取的快取型別的過時快取。

若要正常運作，自訂前端必須定義為`CACHE_CONFIGURATION.frontend`下的完整前端。 僅為新前端名稱定義`use_stale_cache: true`是不夠的。

**設定範例**

>[!BEGINTABS]

>[!TAB 設定Redis的過時快取]

針對Redis：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB 設定Valkey的過時快取]

若為Valkey：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>如果來源前端設定了其他後端選項，例如壓縮、重試、預先載入金鑰或其他調整值，請將這些選項複製到`stale_cache_enabled`，以便新的前端保持相同的行為。


## 個別的快取和工作階段執行個體

將快取與工作階段分開可讓您獨立管理它們。 它可減少快取與工作階段流量之間的爭用，防止快取相關壓力影響工作階段，並允許每個Redis或Valkey執行個體根據其本身的工作負載調整大小與調整。

請依照下列步驟，為工作階段布建專用執行個體：

>[!BEGINTABS]

>[!TAB Redis]

1. 更新`.magento/services.yaml`設定檔。

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
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

1. 請求專用於生產和中繼環境工作階段的新Redis執行個體。

   提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。 包含更新的`.magento/services.yaml`與`.magento.app.yaml`組態檔。

   此更新不會造成任何停機時間，但需要部署才能啟用新服務。

1. 確認新執行個體正在執行，並記下連線埠號碼。

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 將連線埠號碼新增至`.magento.env.yaml`設定檔。

   >[!IMPORTANT]
   >
   >只有在`ece-tools`無法從`MAGENTO_CLOUD_RELATIONSHIPS` Redis工作階段服務定義中自動偵測到Redis工作階段連線埠時，才設定此連線埠。

   >[!NOTE]
   >
   >將`disable_locking`設定為`1`以獲得最佳效能。 在極少數情況下，由於高並行工作階段活動而導致競爭情況，請將其設定為`0`以啟用鎖定。

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

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Valkey]

1. 更新`.magento/services.yaml`設定檔。

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
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
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 請求專用於生產和中繼環境工作階段的新Valkey執行個體。

   提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。 包含更新的`.magento/services.yaml`與`.magento.app.yaml`組態檔。

   此更新不會造成任何停機時間，但需要部署才能啟用新服務。

1. 確認新執行個體正在執行，並記下連線埠號碼。

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 將連線埠號碼新增至`.magento.env.yaml`設定檔。

   >[!IMPORTANT]
   >
   >只有在`ece-tools`無法從`MAGENTO_CLOUD_RELATIONSHIPS` Valkey工作階段服務定義自動偵測到Valkey工作階段連線埠時，才設定此連線埠。

   >[!NOTE]
   >
   >將`disable_locking`設定為`1`以獲得最佳效能。 在極少數情況下，由於高並行工作階段活動而導致競爭情況，請將其設定為`0`以啟用鎖定。

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 從Valkey快取執行個體上的[預設資料庫](../../../configuration/cache/redis-pg-cache.md) (`db 0`)移除工作階段。

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## 快取壓縮

如果您使用超過6 GB的Redis或Valkey `maxmemory`，則可以啟用快取壓縮來減少金鑰所消耗的空間。 請注意，此設定可交換使用者端效能以節省記憶體。 如果您有備用CPU容量，請考慮啟用它。 請參閱&#x200B;_組態指南_&#x200B;中的[使用工作階段存放區的Redis](../../../configuration/cache/redis-session.md)或[使用工作階段存放區的Valkey](../../../configuration/cache/valkey-session.md)。

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 啟用非同步釋放

若要在雲端基礎結構上的Adobe Commerce上啟用`lazyfree`，請提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)，要求將下列Redis或Valkey設定套用至您的環境：

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

啟用`lazyfree`時，Redis或Valkey會將記憶體回收解除安裝到背景執行緒，以進行逐出、過期、伺服器啟動的刪除、使用者刪除和復本資料集清除。 這減少了主執行緒封鎖，並可減少請求延遲。

>[!NOTE]
>
>`lazyfree-lazy-user-del yes`選項會使`DEL`命令的行為類似`UNLINK`，立即解除金鑰的連結，並非同步地釋放其記憶體。

>[!WARNING]
>
>由於釋放發生在背景，由已刪除、已過期或收回的金鑰使用的記憶體仍會保持配置，直到背景執行緒完成工作為止。 如果您的Redis或Valkey執行個體已處於記憶體緊張的壓力下，請謹慎測試並考慮先降低記憶體壓力。 例如，針對特定案例停用區塊快取，並依照上述說明分別停用快取和工作階段Redis例項。

## 啟用多執行緒I/O

若要在雲端基礎結構上的Adobe Commerce上啟用Redis I/O執行緒，請提交請求下列I/O執行緒設定的[Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。 此設定可從主執行緒解除安裝通訊端讀取和寫入以及命令剖析，藉此提高輸送量，但代價是需提高CPU使用量。 在載入下驗證並監視主機。

>[!BEGINTABS]

>[!TAB 設定Redis的I/O執行緒]

針對Redis：

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB 設定Valkey]的I/O執行緒

若為Valkey：

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>I/O執行緒只會平行處理使用者端I/O和剖析。 Redis指令執行仍維持單一執行緒。

>[!WARNING]
>
>啟用I/O執行緒可能會增加CPU的使用量，而且不會使每個工作負荷都受益。 從保守的值和基準開始。 如果延遲增加或CPU飽和，請減少`io-threads`或停用I/O執行緒中的讀取。


## 增加使用者端逾時和重試次數

調整`.magento.env.yaml`中的後端選項，將Redis或Valkey快取使用者端的容許度增加到短期飽和度。

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

這些設定可藉由重試連線設定並允許Redis或Valkey的更多回覆時間，減少短時間尖峰期間間歇性連線和讀取逾時錯誤。

>[!NOTE]
>
>這些設定有助於緩解短暫的擁塞，但無法修正持續性的超載。

## 設定範例

使用以下範例作為您的Redis或Valkey服務設定的起點。


### 套用所有最佳實務建議

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey設定範例]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### 套用所有最佳實務建議，並依快取型別區分過時快取

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## 其他資訊

請參閱下列相關主題：

- [設定Redis服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/redis)
- [部署變數](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)

