---
title: 將Redis用於預設快取
description: 學習將Redis配置為Adobe Commerce和Magento Open Source的預設快取。
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# 將Redis用於預設快取

Commerce提供命令行選項來配置Redis頁和預設快取。 雖然可以通過編輯 `<Commerce-install-dir>app/etc/env.php` 檔案，建議使用命令行，尤其是初始配置。 命令行提供驗證，確保配置語法正確。

你必須 [安裝Redis](config-redis.md#install-redis) 再繼續。

## 配置Redis預設快取

運行 `setup:config:set` 命令並指定特定於Redis預設快取的參數。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

使用以下參數：

- `--cache-backend=redis` 啟用Redis預設快取。 如果此功能已啟用，請忽略此參數。

- `--cache-backend-redis-<parameter>=<value>` 是配置預設快取的鍵和值對的清單：

| 命令行參數 | 值 | 意義 | 預設值 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | 伺服器 | 完全限定的主機名、 IP地址或UNIX套接字的絕對路徑。 預設值127.0.0.1表示Redis安裝在Commerce伺服器上。 | `127.0.0.1` |
| `cache-backend-redis-port` | 埠 | Redis伺服器偵聽埠 | `6379` |
| `cache-backend-redis-db` | 資料庫 | 如果將Redis用於預設和全頁快取，則此為必需欄位。 必須指定其中一個快取的資料庫編號；預設情況下，其他快取使用0。<br><br>**重要**:如果將Redis用於多種類型的快取，則資料庫編號必須不同。 建議將預設的快取資料庫編號分配給0，將頁快取資料庫編號分配給1，將會話儲存資料庫編號分配給2。 | `0` |
| `cache-backend-redis-password` | 密碼 | 配置Redis密碼可啟用其內置安全功能之一：這樣 `auth` 命令，它要求客戶端進行身份驗證才能訪問資料庫。 口令直接在Redis的配置檔案中配置： `/etc/redis/redis.conf` |  |

### 示例命令

以下示例啟用Redis預設快取，將主機設定為 `127.0.0.1`，並將資料庫編號指定為0。 Redis對所有其他參數使用預設值。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## 配置Redis頁快取

要在Commerce上配置Redis頁快取，請運行 `setup:config:set` 命令。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

使用以下參數：

- `--page-cache=redis` 啟用Redis頁快取。 如果此功能已啟用，請忽略此參數。

- `--page-cache-redis-<parameter>=<value>` 是配置頁快取的鍵和值對的清單：

| 命令行參數 | 值 | 意義 | 預設值 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | 伺服器 | 完全限定的主機名、 IP地址或UNIX套接字的絕對路徑。 預設值127.0.0.1表示Redis安裝在Commerce伺服器上。 | `127.0.0.1` |
| `page-cache-redis-port` | 埠 | Redis伺服器偵聽埠 | `6379` |
| `page-cache-redis-db` | 資料庫 | 如果將Redis用於預設和全頁快取，則此為必需欄位。 必須指定其中一個快取的資料庫編號；預設情況下，其他快取使用0。<br/>**重要**:如果將Redis用於多種類型的快取，則資料庫編號必須不同。 建議將預設的快取資料庫編號分配給0，將頁快取資料庫編號分配給1，將會話儲存資料庫編號分配給2。 | `0` |
| `page-cache-redis-password` | 密碼 | 配置Redis密碼可啟用其內置安全功能之一：這樣 `auth` 命令，它要求客戶端進行身份驗證才能訪問資料庫。 在Redis配置檔案中配置密碼： `/etc/redis/redis.conf` |  |

### 示例命令

以下示例啟用Redis頁快取，將主機設定為 `127.0.0.1`，並將資料庫編號指定為1。 所有其它參數都設定為預設值。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## 結果

作為兩個示例命令的結果，Commerce將添加與以下類似的行： `<Commerce-install-dir>app/etc/env.php`:

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

## 將AWSElastiCache與您的EC2實例配合使用

從Commerce 2.4.3開始，在AmazonEC2上托管的實例可能使用AWSElastiCache代替本地Redis實例。

>[!WARNING]
>
>此部分僅適用於在AmazonEC2 VPC上運行的Commerce實例。 它不適用於內部安裝。

### 配置Redis群集

之後 [在AWS建立Redis群集](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/)，將EC2實例配置為使用ElastiCache。

1. [建立ElastiCache群集](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) EC2實例的同一區域和VPC中。
1. 驗證連接。

   - 開啟到EC2實例的SSH連接
   - 在EC2實例上，安裝Redis客戶端：

      ```bash
      sudo apt-get install redis
      ```

   - 將入站規則添加到EC2安全組：類型 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 將入站規則添加到ElastiCache群集安全組：類型 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 連接到Redis CLI:

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### 配置Commerce以使用群集

Commerce支援多種類型的快取配置。 通常，快取配置在前端和後端之間分開。 前端快取被分類為 `default`，用於任何快取類型。 您可以定制或拆分為較低級別的快取，以獲得更好的效能。 通用的Redis配置將預設快取和頁快取分離到它們自己的Redis資料庫(RDB)中。

運行 `setup` 的子菜單。

要將Commerce配置為Redis的預設快取，請執行以下操作：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

要配置Commerce以進行Redis頁快取，請執行以下操作：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

要將Commerce配置為將Redis用於會話儲存，請執行以下操作：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 驗證連接性

**驗證Commerce是否與ElastiCache通話**:

1. 開啟到Commerce EC2實例的SSH連接。
1. 啟動Redis監視器。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. 在Commerce UI中開啟頁面。
1. 驗證 [快取輸出](#verify-redis-connection) 在終端上。

## 新Redis快取實現

從Commerce 2.3.5開始，建議使用擴展的Redis快取實現： `\Magento\Framework\Cache\Backend\Redis`。

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

## Redis預載特徵

由於Commerce將配置資料儲存在Redis快取中，因此我們可以預載入在頁之間重複使用的資料。 要查找必須預載的鍵，請分析從Redis傳輸到Commerce的資料。 我們建議將載入到每頁的資料預載入，例如 `SYSTEM_DEFAULT`。 `EAV_ENTITY_TYPES`。 `DB_IS_UP_TO_DATE`。

Redis使用 `pipeline` 以組合載入請求。 密鑰應包括資料庫前置詞；例如，如果資料庫前置詞為 `061_`，預載鍵如下所示： `061_SYSTEM_DEFAULT`

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

如果您正在將預載入功能與L2快取一起使用，請不要忘記添加 `:hash` 尾碼到鍵，因為二級快取只傳輸資料的哈希，而不是資料本身：

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 並行生成

從2.4.0版開始，我們 `allow_parallel_generation` 選項。
預設情況下禁用它，我們建議在配置和/或塊過多之前禁用它。

**啟用並行生成**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

由於它是標誌，因此不能使用命令禁用它。 必須手動將配置值設定為 `false`:

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

## 驗證Redis連接

要驗證Redis和Commerce是否協同工作，請登錄到運行Redis的伺服器，開啟終端，然後使用Redis監視器命令或ping命令。

### Redis監視器命令

```bash
redis-cli monitor
```

頁面快取輸出示例：

```terminal
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

### Redis ping命令

```bash
redis-cli ping
```

預期的響應是： `PONG`

如果兩個命令都成功，則正確設定Redis。

### 檢查壓縮資料

要檢查壓縮的會話資料和頁快取， [RESP應用](https://flathub.org/apps/details/app.resp.RESP) 支援Commerce 2會話和頁面快取的自動解壓縮，並以人可讀的形式顯示PHP會話資料。
