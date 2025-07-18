---
title: 預設快取使用Redis
description: 瞭解如何設定Redis為Adobe Commerce的預設快取。
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 2c489f2655e6fb067de1730355df6cd3683ea562
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 0%

---

# 預設快取使用Redis

Commerce提供命令列選項來設定Redis頁面和預設快取。 雖然您可以透過編輯`<Commerce-install-dir>app/etc/env.php`檔案來設定快取，但建議使用命令列的方法，尤其是對於初始設定。 命令列會提供驗證，確保組態語法正確。

您必須[安裝Redis](config-redis.md#install-redis)，才能繼續。

## 設定Redis預設快取

執行`setup:config:set`命令並指定Redis預設快取的特定引數。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

，並使用下列引數：

- `--cache-backend=redis`啟用Redis預設快取。 如果已啟用此功能，請省略此引數。

- `--cache-backend-redis-<parameter>=<value>`是設定預設快取的機碼和值組清單：

| 命令列引數 | 值 | 含義 | 預設值 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值127.0.0.1表示Commerce伺服器上已安裝Redis。 | `127.0.0.1` |
| `cache-backend-redis-port` | 連線埠 | Redis伺服器接聽連線埠 | `6379` |
| `cache-backend-redis-db` | 資料庫 | 如果您對預設和全頁快取都使用Redis，則此為必要專案。 您必須指定其中一個快取的資料庫編號；另一個快取預設使用0。<br><br>**重要**：如果您針對一種以上的快取型別使用Redis，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派為0，將頁面快取資料庫編號指派為1，並將工作階段儲存資料庫編號指派為2。 | `0` |
| `cache-backend-redis-password` | 密碼 | 設定Redis密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 密碼是直接在Redis的組態檔中設定： `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | 啟用或停用LUA。 <br><br>**LUA**： Lua可讓我們在Redis內執行部分應用程式邏輯，藉由原子執行來改善效能並確保資料的一致性。 | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | 啟用或停用記憶體回收的LUA。 <br><br>**LUA**： Lua可讓我們在Redis內執行部分應用程式邏輯，藉由原子執行來改善效能並確保資料的一致性。 | `1` |

### 命令範例

下列範例會啟用Redis預設快取，將主機設定為`127.0.0.1`，並將資料庫編號指派為0。 Redis會針對所有其他引數使用預設值。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## 設定Redis頁面快取

若要在Commerce上設定Redis頁面快取，請使用其他引數執行`setup:config:set`命令。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

，並使用下列引數：

- `--page-cache=redis`啟用Redis頁面快取。 如果已啟用此功能，請省略此引數。

- `--page-cache-redis-<parameter>=<value>`是設定頁面快取的機碼和值組清單：

| 命令列引數 | 值 | 含義 | 預設值 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值127.0.0.1表示Commerce伺服器上已安裝Redis。 | `127.0.0.1` |
| `page-cache-redis-port` | 連線埠 | Redis伺服器接聽連線埠 | `6379` |
| `page-cache-redis-db` | 資料庫 | 如果您對預設和完整頁面快取都使用Redis，則此為必要專案。 您必須指定其中一個快取的資料庫編號；另一個快取預設使用0。<br/>**重要**：如果您針對一種以上的快取型別使用Redis，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派為0，將頁面快取資料庫編號指派為1，並將工作階段儲存資料庫編號指派為2。 | `0` |
| `page-cache-redis-password` | 密碼 | 設定Redis密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 在Redis組態檔中設定密碼： `/etc/redis/redis.conf` | |

### 命令範例

下列範例會啟用Redis頁面快取，將主機設定為`127.0.0.1`，並將資料庫編號指派為1。 所有其他引數都會設定為預設值。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## 結果

由於這兩個範例命令，Commerce將類似下列的行新增到`<Commerce-install-dir>app/etc/env.php`：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## 搭配您的EC2執行個體使用AWS ElastiCache

自Commerce 2.4.3起，Amazon EC2上代管的執行個體可能會使用AWS ElastiCache來取代本機Redis執行個體。

>[!WARNING]
>
>本節僅適用於在Amazon EC2 VPC上執行的Commerce執行個體。 它不適用於內部部署安裝。

### 設定Redis叢集

在[在AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/)上設定Redis叢集後，請設定EC2執行個體以使用ElastiCache。

1. [在相同區域和EC2執行個體的VPC中建立ElastiCache叢集](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html)。
1. 驗證連線。

   - 開啟與EC2執行個體的SSH連線
   - 在EC2執行個體上，安裝Redis使用者端：

     ```bash
     sudo apt-get install redis
     ```

   - 將輸入規則新增至EC2安全性群組：型別`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 將輸入規則新增至ElastiCache叢集安全性群組：型別`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 連線至Redis CLI：

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### 設定Commerce以使用叢集

Commerce支援多種型別的快取設定。 一般而言，快取設定會在前端和後端之間分割。 前端快取分類為`default`，用於任何快取型別。 您可以自訂或分割為較低層級的快取以取得較佳的效能。 常見的Redis組態是將預設快取和頁面快取分隔到自己的Redis資料庫(RDB)中。

執行`setup`命令以指定Redis端點。

若要設定用於Redis的Commerce作為預設快取：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

若要設定Commerce以進行Redis頁面快取：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

若要設定Commerce以使用Redis進行工作階段儲存：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 驗證連線能力

**若要確認Commerce正在與ElastiCache通訊**：

1. 開啟與Commerce EC2執行個體的SSH連線。
1. 啟動Redis監視器。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. 在Commerce UI中開啟頁面。
1. 驗證您終端機中的[快取輸出](#verify-redis-connection)。

## 新的Redis快取實作

自Commerce 2.3.5起，建議使用擴充的Redis快取實作： `\Magento\Framework\Cache\Backend\Redis`。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Redis預先載入功能

由於Commerce會將設定資料儲存在Redis快取中，因此我們可以預先載入在頁面之間重複使用的資料。 若要尋找必須預先載入的金鑰，請分析從Redis傳輸到Commerce的資料。 我們建議預先載入每個頁面上載入的資料，例如`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`、`DB_IS_UP_TO_DATE`。

Redis使用`pipeline`來複合載入要求。 金鑰應包含資料庫首碼；例如，如果資料庫首碼為`061_`，預先載入金鑰看起來會像這樣： `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

如果您搭配L2快取使用預先載入功能，別忘了將`:hash`尾碼新增至您的金鑰，因為L2快取只會傳輸資料的雜湊，不會傳輸資料本身：

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 平行產生

從2.4.0版開始，我們為想要消除等待鎖定的使用者引入了`allow_parallel_generation`選項。
預設會停用，建議您先停用，直到設定和/或區塊過多為止。

**若要啟用平行產生**：

```bash
bin/magento setup:config:set --allow-parallel-generation
```

由於它是標幟，因此您無法使用命令將其停用。 您必須手動將組態值設為`false`：

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## 驗證Redis連線

若要確認Redis與Commerce是否共同運作，請登入執行Redis的伺服器、開啟終端機，然後使用Redis監視指令或ping指令。

### Redis監視命令

```bash
redis-cli monitor
```

頁面快取輸出範例：

```
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Redis ping指令

```bash
redis-cli ping
```

預期的回應是： `PONG`

如果兩個指令都成功，Redis就會正確設定。

### 檢查壓縮資料

若要檢查壓縮的「工作階段」資料和「頁面快取」，[RESP.app](https://flathub.org/apps/details/app.resp.RESP)支援Commerce 2「工作階段」和「頁面」快取的自動解壓縮，並以可讀取的格式顯示PHP工作階段資料。
