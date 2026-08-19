---
title: Valkey和Redis服務組態的最佳作法
description: 瞭解如何在雲端上為Adobe Commerce設定Redis和Valkey快取，包括復本連線、L2快取、過時快取和工作階段存放區。
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="雲端上的Commerce" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案上的Adobe Commerce 。"
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Valkey和Redis服務組態的最佳作法

在雲端部署上為Adobe Commerce設定Redis或Valkey以供Adobe Commerce應用程式快取、工作階段儲存空間和L2快取使用時，請使用這些建議。

如需Adobe Commerce內部部署快取組態，請參閱效能最佳化的[L2快取組態](/help/configuration/cache/level-two-cache.md)。

>[!NOTE]
>
>本主題說明Commerce應用程式快取和工作階段後端。 HTTP全頁快取（例如Fastly或Varnish）是獨立的快取層，且獨立設定。 變更應用程式快取後端不會取代或設定HTTP全頁快取。

這些建議涵蓋下列內容：

- 選取支援的快取服務
- 啟用復本連線
- 個別的快取和工作階段執行個體
- 設定快取壓縮
- 啟用非同步釋放
- 啟用多執行緒I/O
- 增加使用者端逾時和重試次數
- 設定L2快取，包括預先載入金鑰、過時快取及[!DNL Symfony] L2快取
- 檢閱設定範例

## 選取支援的快取服務

| Adobe Commerce版本 | 建議的快取服務 | L2快取實作 |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8和更早版本（當確切版本支援時） | Redis或Valkey | RemoteSynchronizedCache |
| 2.4.9和更新版本 | Valkey | symfony_l2 |

Adobe Commerce 2.4.9的快取設定以及系統需求指定Valkey的修補程式發行版本不支援Redis。 請一律驗證[快取後端選項和儲存體參考](/help/configuration/cache/cache-options.md)和[系統需求](/help/installation/system-requirements.md)中的確切Commerce版本、修補程式層級和服務版本。

>[!NOTE]
>
>確認您使用的是最新版本的`ece-tools`封裝。 如果沒有，[升級至最新版本](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)。 您可以使用`composer show magento/ece-tools` CLI命令檢查本機環境中安裝的版本。

## 啟用復本連線

啟用`.magento.env.yaml`檔案中的復本連線。 這項變更可讓Adobe Commerce使用額外的快取連線進行讀取，同時繼續使用主要端點進行寫入。 此設定可減少主要快取服務的讀取負載，並更有效地分配讀取流量。

>[!NOTE]
>
>復本連線是否可用取決於專案的拓撲（例如，單一節點與分割或HA架構）以及`ece-tools`版本。 在依賴此設定之前，請執行`echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp`並檢查`USE_SLAVE_CONNECTION`專案，以確認您的服務存在復本關係。 若要確認您的拓朴是否布建復本端點，請升級`ece-tools`並重新部署，或者如果沒有`USE_SLAVE_CONNECTION`專案，請聯絡Adobe Commerce支援。
>
>對於`symfony_l2`，復本連線支援是透過`ece-tools`和雲端修補程式更新提供。 除了變更`VALKEY_USE_SLAVE_CONNECTION: true`之外，不需要額外的快取設定。 更新至最新的`ece-tools`版本以接收修正。

>[!BEGINTABS]

>[!TAB Valkey組態]

對於Valkey，請使用：

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

如需環境變陣列態詳細資訊，請參閱雲端基礎結構指南上的&#x200B;_Commerce_&#x200B;中的[VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection)。

>[!TAB Redis組態]

對於Redis，請使用：

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

如需環境變陣列態詳細資訊，請參閱雲端基礎結構指南上的&#x200B;_Commerce_&#x200B;中的[REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection)。

>[!ENDTABS]

## 個別的快取和工作階段執行個體

快取和工作階段設定是獨立的。 無論您使用哪個快取後端或L2快取實施，`SESSION_CONFIGURATION`都不會影響快取行為。 將快取與工作階段分開可讓您獨立管理它們。 它可減少快取與工作階段流量之間的爭用，防止快取相關壓力影響工作階段，並允許每個Redis或Valkey執行個體根據其本身的工作負載調整大小與調整。

>[!IMPORTANT]
>
>在「生產」和「預備」上布建專用工作階段執行處理並非自助式。 它需要提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)以及您更新的`.magento/services.yaml`和`.magento.app.yaml`檔案，如下面的步驟3所述。

若要布建工作階段的專用執行個體，請遵循下列步驟：

>[!BEGINTABS]

>[!TAB Valkey]

1. 更新`.magento/services.yaml`設定檔，將`<version>`取代為您正在使用的服務版本。 請參閱發行版本所支援的服務版本的[系統需求](/help/installation/system-requirements.md)。

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)。 包含更新的`.magento/services.yaml`與`.magento.app.yaml`組態檔。

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

1. 從Valkey快取執行個體上的[預設資料庫](/help/configuration/cache/redis-pg-cache.md) (`db 0`)移除工作階段。

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Redis]

1. 更新`.magento/services.yaml`設定檔，將`<version>`取代為您正在使用的服務版本。

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)。 包含更新的`.magento/services.yaml`與`.magento.app.yaml`組態檔。

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

1. 從Redis快取執行個體上的[預設資料庫](/help/configuration/cache/redis-pg-cache.md) (`db 0`)移除工作階段。

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## 快取壓縮

如果您使用超過6 GB的Redis或Valkey `maxmemory`，則可以啟用快取壓縮來減少金鑰所消耗的空間。 請注意，此設定可交換使用者端效能以節省記憶體。 如果您有備用CPU容量，請考慮啟用它。 請參閱&#x200B;_組態指南_&#x200B;中的[使用工作階段存放區的Redis](/help/configuration/cache/redis-session.md)或[使用工作階段存放區的Valkey](/help/configuration/cache/valkey-session.md)。

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

若要在Adobe Commerce雲端基礎結構上啟用`lazyfree`，請提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)，要求將下列Redis或Valkey設定套用至您的環境：

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

若要在Adobe Commerce雲端基礎結構上啟用Redis I/O執行緒，請提交[Adobe Commerce支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)，要求下列I/O執行緒組態。 此設定可從主要執行緒解除安裝通訊端讀取、寫入和命令剖析，藉此提高輸送量，但代價是需提高CPU使用量。 在載入下驗證並監視主機。

>[!BEGINTABS]

>[!TAB 設定Redis的I/O執行緒]

針對Redis：

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB 設定Valkey的I/O執行緒]

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

## 設定L2快取

在`.magento.env.yaml`組態檔中設定`VALKEY_BACKEND`或`REDIS_BACKEND`部署變數，以設定L2快取。

雲端基礎結構上的Adobe Commerce提供兩種L2快取實作。

- 舊版實作使用`RemoteSynchronizedCache`搭配`Cm_Cache_Backend_File`進行本機儲存
- 現代實作使用`symfony_l2`，並遵循PSR-6規範，且效能更佳。 新式實作僅支援Valkey。

| Commerce版本 | RemoteSynchronizedCache與Valkey | 建議的設定 |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8和較舊版本<br> （如果支援Valkey） | 支援的舊版L2路徑 | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9和更新版本 | 不支援 | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>Adobe Commerce 2.4.9或更新於2.4.5-p16、2.4.6-p14、2.4.7-p9和2.4.8-p4的修補程式版本不支援Redis快取。 對於不支援Redis的快取設定，請使用Valkey。 如需依版本支援的快取服務，請參閱[系統需求](/help/installation/system-requirements.md)。

>[!BEGINTABS]

>[!TAB Valkey組態]

在支援Valkey的Commerce 2.4.8及舊版上，使用此設定：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

在Commerce 2.4.9和更新版本上，將下列設定與[!DNL Symfony] L2實作搭配使用：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Redis組態]

在支援Redis的2.4.8版和更早版本的Commerce上，使用：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

如需環境組態詳細資訊，請參閱&#x200B;_雲端基礎結構上的Commerce指南_&#x200B;中的[`REDIS_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend)。

>[!ENDTABS]

### 移轉至Valkey與[!DNL Symfony] L2快取

如果您正在將雲端專案上現有的Adobe Commerce從`RemoteSynchronizedCache` （Redis或Valkey）移轉至`symfony_l2`，請在更新`.magento.env.yaml`前檢閱下列專案。

- **變更部署變數足以啟用`symfony_l2`。** 單獨設定`VALKEY_BACKEND: symfony_l2`會自動建置完整的L2快取組態。 您不需要手動重新建立您先前使用的`RemoteSynchronizedCache`組態的`backend_options`結構。 請參閱[設定 [!DNL Symfony] 二級快取](#configure-symfony-l2-cache)。

- **從您現有的設定中移除`preload_keys`。** 如果您的`RemoteSynchronizedCache`設定在`CACHE_CONFIGURATION`下包含`preload_keys`，請在移轉時將其移除。 如需詳細資訊，請參閱[預先載入金鑰](#preload-keys)。

- **自動變更過時的快取行為。** 在`symfony_l2`底下，`ece-tools`會自動啟用一般快取型別（例如`layout`、`block_html`、`full_page`和`translate`）的過時快取，而不需要`RemoteSynchronizedCache`所需的手動前端組態。 如果您先前手動設定過時的快取，且想要保留您之前的確切行為，請在移轉前檢閱[啟用過時的快取](#enable-stale-cache)。

- **壓縮需要明確的旗標。** 如果您透過`CACHE_CONFIGURATION`自訂`symfony_l2`壓縮，僅設定`compression_lib`不會啟用壓縮 — 也必須設定`compress_data`。 請參閱[快取壓縮](#cache-compression)。

- **Redis不是`symfony_l2`支援的遠端後端。** 移轉至Valkey，作為此變更的一部分。 請參閱[設定Valkey服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)。

- **工作階段設定不受此移轉影響。** `SESSION_CONFIGURATION`獨立於快取後端，在移至`symfony_l2`時不需要變更。 請參閱[個別的快取與工作階段執行個體](#separate-cache-and-session-instances)。

>[!IMPORTANT]
>
>請勿在`app/etc/env.php`中手動設定`symfony_l2`。 透過`.magento.env.yaml`進行設定，以便`ece-tools`在部署期間套用並維護設定。 請參閱[設定 [!DNL Symfony] 二級快取](#configure-symfony-l2-cache)。

### 預先載入索引鍵

如果您使用正確的位置（`backend_options`或`remote_backend_options`下），預先載入金鑰可套用至`symfony_l2`組態。 不過，Adobe不建議搭配`symfony_l2`使用預先載入金鑰。 `symfony_l2`預先載入實作一次擷取一個索引鍵，因此不會像對`RemoteSynchronizedCache`那樣減少往返次數，而且它可以增加Valkey上的負載，而不會影響效能。

預先載入功能可讓您提供常用索引鍵清單，Magento會在第一次存取請求期間，於單一管道中擷取這些索引鍵。 接著Magento會將擷取的值保留在PHP記憶體中以供該要求剩餘部分使用，如此可減少重複的Redis或Valkey來回，並可改善這些金鑰的要求啟動載入效能。

您可以透過監視Redis或Valkey上的作用中命令來識別常用金鑰：

預先載入金鑰是在`.magento.env.yaml`組態檔中設定。 此範例顯示支援`RemoteSynchronizedCache`的Adobe Commerce 2.4.8和更早版本的設定。

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

10秒後，按&#x200B;**Ctrl+C**。然後執行下列命令：

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

此記錄會列出您可以預先載入的金鑰。 若要檢視索引鍵的內容，請執行以下命令：

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### 啟用過時的快取

過時快取是L2快取功能，可讓Adobe Commerce從`/dev/shm`提供現有的本機快取值，而其他要求已經在重新產生相同的專案。 這可防止並行請求等候。 這減少了重新產生昂貴快取專案時快取串流和鎖爭用。

若是Adobe Commerce 2.4.9和更新版本，請在`.magento.env.yaml`檔案中設定`VALKEY_BACKEND: symfony_l2`：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

`ece-tools`會自動產生`default`前端和`stale_cache_enabled`前端，並將下列快取型別對應到已啟用的前端： `layout`、`block_html`、`reflection`、`config_integration`、`config_integration_api`、`full_page`和`translate`。 這些型別不需要手動`use_stale_cache`或前端設定。 此自動對應本身就是啟用選擇性過時快取的範例。 只有特定快取型別會使用已啟用的前端，而非所有前端。 若要自訂對應至`stale_cache_enabled`的型別，或新增超出預設值的型別，請參閱[自訂 [!DNL Symfony] L2快取組態](#customize-the-symfony-l2-cache-configuration)。

>[!NOTE]
>
>`full_page`快取型別與雲端基礎結構專案上的Adobe Commerce無關，因為它們使用Fastly進行全頁快取。 因為這個原因，本區段的手動設定範例省略`full_page`，即使`ece-tools`將其包含在預設`symfony_l2`對應中。

下列舊版組態適用於Adobe Commerce 2.4.8和更早版本，其中使用`RemoteSynchronizedCache`，且需要手動過時快取和前端組態。 這裡也適用相同選擇性（而非全域）建議。

#### 舊版RemoteSynchronizedCache後端如何運作

透過`RemoteSynchronizedCache`，Magento會維護每個快取專案的兩個復本： `/dev/shm`中的本機復本，以及Redis或Valkey中的遠端復本。 當遠端副本無法使用且該金鑰已存在重新產生鎖定時，並行要求可以接收先前的本機值，而不是等到寫入新的值為止。

若要啟用2.4.8及舊版的過時快取，請在`.magento.env.yaml`檔案中進行設定。

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

>[!WARNING]
>
>上述設定會在`default`快取前端啟用過時的快取，這會將過時的快取行為套用至使用該前端的所有快取專案。 透過此設定，Magento核心快取型別可如預期運作。 不過，如果您的專案包含自訂程式碼或擴充功能，這些程式碼或擴充功能會透過一般`\Magento\Framework\App\Cache` API （例如`$this->cache->save()`）寫入快取而沒有專用的快取前端，則這些專案也可以在重新產生期間提供過時的值。
>
>
>如果這會在您的自訂內容中造成非預期的行為，請讓`default`前端停用過時的快取，並只針對選取的快取型別啟用它，如下所示。

#### 分別針對每種快取型別啟用過時快取（舊版）

您只能透過在`.magento.env.yaml`中定義專用快取前端並將選取的快取型別對應到它來啟用選取的快取型別的過時快取。 此手動方法適用於舊版`RemoteSynchronizedCache`後端；`symfony_l2`會自動執行此對應，如上所述。

若要正常運作，自訂前端必須定義為`CACHE_CONFIGURATION.frontend`下的完整前端。 僅為新前端名稱定義`use_stale_cache: true`是不夠的。

**設定範例**

對於2.4.8版和更舊版本的Redis，下列設定會為`layout`、`reflection`、`config_integration`、`config_integration_api`和`translate`快取型別啟用過時快取，而其他使用預設前端且停用過時快取的使用者：

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

>[!NOTE]
>
>如果來源前端設定了其他後端選項，請將這些選項複製到`stale_cache_enabled`，讓新的前端保持相同的行為。

### 設定[!DNL Symfony] L2快取

Adobe Commerce 2.4.9和更新版本支援`symfony_l2`快取後端。 `symfony_l2`後端是Adobe Commerce用來管理L1和L2快取行為的快取實作。 **它不會取代Redis或Valkey做為遠端快取服務。**

>[!IMPORTANT]
>
>透過`.magento.env.yaml`部署變數設定`symfony_l2`，讓`ece-tools`在部署期間套用並維護設定。 請勿在`app/etc/env.php`中手動設定`symfony_l2`，因為部署可能會覆寫手動`env.php`變更。 如果`ece-tools`未套用`symfony_l2`，Commerce可能會回覆為檔案式快取，這可能會增加磁碟I/O、增加多節點環境的檔案系統復寫負荷，並降低效能。

若要針對Adobe Commerce 2.4.9使用`symfony_l2`快取，請完成下列步驟：

- 確定雲端專案使用[`ece-tools`封裝v2002.2.12](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)或更新版本。

- 在`.magento.env.yaml`檔案中設定部署變數： `VALKEY_BACKEND`=`symfony_l2`。

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

將`VALKEY_BACKEND`部署變數設為`symfony_l2`會自動從您的Valkey服務連線詳細資料建置完整的L2快取設定，包括`default`和`stale_cache_enabled`前端，且已對映通用快取型別。 定義`CACHE_CONFIGURATION`是選擇性的，只有在您想要自訂特定的後端選項時才需要。

>[!NOTE]
>
>Adobe Commerce 2.4.9的修補程式ACP2E-5132透過最佳化標籤儲存、新增過時的快取重新產生鎖定，以及修正過時的標籤成員資格、多餘的遠端寫入和L1大小型逐出(`cleanup_percentage`)等問題，來改善[!DNL Symfony]的L2快取效能和可靠性。 這樣可以減少磁碟I/O和後端負載，同時改善快取一致性。 請參閱&#x200B;_Adobe Commerce設定指南_&#x200B;中的[增強型Symfony L2快取效能和可靠性](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability)。
>
>此修補程式包含在Commerce套件[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)的雲端修補程式中（相依性`ece-tools`），並在您更新至最新的`ece-tools`版本時於部署期間自動套用。 更新至最新版本的`ece-tools`以接收修補程式。

#### 自訂[!DNL Symfony] L2快取設定

`ece-tools`會自動衍生`default`和`stale_cache_enabled`前端的Valkey連線詳細資料(`server`、`port`、`database`、`serializer`、`compression_lib`、`persistent_id`)。 若要自訂其他後端選項（例如本機快取目錄），請將`CACHE_CONFIGURATION`與`_merge: true`以及`VALKEY_BACKEND: symfony_l2`一起定義。 您在此處定義的值會覆寫對應的自動產生預設值；任何忽略的選項都會繼續使用`ece-tools`自動衍生的值。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>定義`symfony_l2`的`CACHE_CONFIGURATION`時，如果您有意指向專案的Valkey服務以外的快取端點，則僅覆寫`server`或`port`。 `ece-tools`封裝會自動從您的Valkey服務關聯性衍生這些值。
>
>如果您覆寫`server`，則連線至專案的Valkey服務時，其值必須是`localhost`。 提供不正確的`server`或`port`值會導致部署失敗，並出現快取連線錯誤。

### 適用於Adobe Commerce Cloud的L2快取記憶體大小

L2快取使用[暫存檔案系統](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`)作為其儲存機制。 與專門化的機碼值存放區不同，tmpfs沒有機碼收回原則，因此記憶體使用量可能會無限增加。 為避免耗盡，當使用量達到可設定的臨界值（預設為95%）時，Adobe Commerce會自動清除L2儲存空間。 您可以要求較大的`/dev/shm`掛載或降低清除臨界值，以控制記憶體耗用量。

根據您的專案需求，調整L2快取記憶體使用量上限。 使用下列其中一種方法：

- 若要調整`/dev/shm`掛載大小，請建立支援票證。 針對此案例，Adobe建議將`/dev/shm`掛載大小設定為15 GB。
- 在應用程式層級調整`cleanup_percentage`屬性，以限制儲存使用量，並釋放其他服務可用的記憶體。
您可以在快取組態群組`cache/frontend/default/backend_options/cleanup_percentage`下的部署組態中調整組態。

>[!NOTE]
>
>`cleanup_percentage`可設定的選項已在Adobe Commerce 2.4.4中匯入。

下列範例顯示`.magento.env.yaml`檔案中的設定程式碼：

>[!BEGINTABS]

>[!TAB Valkey組態]

若是Commerce 2.4.9和更新版本，請使用下列設定將清除臨界值設定為90%：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Redis組態]

若是Commerce 2.4.8和較舊版本，請使用下列設定將清除臨界值設定為90%：

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

>[!ENDTABS]

快取需求會因您的專案設定和自訂第三方程式碼而異。 設定L2快取記憶體的大小，讓快取運作時不會頻繁發生臨界值點選。

理想情況下，L2快取記憶體的使用量會穩定在臨界值以下，以避免頻繁的儲存清除。

您可以執行下列CLI命令並檢閱`/dev/shm`行，檢查叢集每個節點上的L2快取儲存記憶體使用量。

```shell
df -h /dev/shm
```

使用方式會因節點而異，但會收斂到類似的值。

## 設定範例

使用以下範例作為您的Redis或Valkey服務設定的起點。


### 套用所有最佳實務建議

>[!BEGINTABS]

>[!TAB Valkey設定範例]

針對`VALKEY_BACKEND: symfony_l2`，讓`ece-tools`產生`default`和`stale_cache_enabled`前端及其快取型別對應。 請勿在廣泛的`default`前端設定`use_stale_cache`。 下方的`CACHE_CONFIGURATION`區塊僅包含明確的後端選項覆寫。

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
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

>[!TAB Redis設定範例]

對Adobe Commerce 2.4.8和更早版本上的Redis使用下列設定：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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

>[!ENDTABS]

### 依快取型別區分過時快取

>[!BEGINTABS]

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
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
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
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

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
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

>[!ENDTABS]

>[!MORELIKETHIS]
>
>- [設定Valkey服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [設定Redis服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [部署變數](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
