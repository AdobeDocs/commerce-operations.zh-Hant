---
title: 設定預設和頁面快取的Redis
description: 瞭解如何將Redis設定為Adobe Commerce的預設和頁面快取後端。 探索CLI命令、env.php設定和連線驗證。
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ec95c99d060f3c45095236d41729648abf389dd1
workflow-type: tm+mt
source-wordcount: 1411
ht-degree: 0%

---

# 為預設和頁面快取設定Redis

{{cloud-cache-config}}

Commerce提供命令列選項來設定Redis頁面和預設快取。 雖然您可以透過編輯`<Commerce-install-dir>app/etc/env.php`檔案來設定快取，但建議使用命令列的方法，尤其是對於初始設定。 命令列會提供驗證，確保組態語法正確。

**先決條件：**

[安裝Redis](config-redis.md#install-redis)，然後再繼續。

>[!NOTE]
>
>對於在EC2上託管的Commerce執行個體，您可以使用AWS ElastiCache來取代本機Redis執行個體。 請參閱[為EC2執行個體設定Elasticache](redis-elasticache-for-ec2.md)。

## Redis快取實作

Adobe Commerce已使用這些Redis快取後端實作：

- **舊版Redis後端** (`Cm_Cache_Backend_Redis`) — 在舊版Redis設定中使用的已棄用實作。
- **Redis後端** (`Magento\Framework\Cache\Backend\Redis`) — 此主題中命令列組態用於預設和頁面快取的後端。
- **L2快取後端** (`Magento\Framework\Cache\Backend\RemoteSynchronizedCache`) — 使用Redis做為遠端後端和本機檔案快取儲存體的兩級快取實作，以跨節點同步處理快取資料。 請參閱[兩級快取組態](level-two-cache.md)。

## 設定Redis預設快取

執行`setup:config:set`命令並指定Redis預設快取專用的引數。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

常見引數包括：

- `--cache-backend=redis`啟用Redis預設快取。 如果已啟用此功能，請省略此引數。

- `--cache-backend-redis-<parameter>=<value>`是設定預設快取的機碼和值組清單：

| 命令列引數 | 值 | 含義 | 預設值 |
| --- | --- | --- | --- |
| `cache-backend-redis-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值127.0.0.1表示Commerce伺服器上已安裝Redis。 | `127.0.0.1` |
| `cache-backend-redis-port` | 連線埠 | Redis伺服器接聽連線埠 | `6379` |
| `cache-backend-redis-db` | 資料庫 | 如果您對預設和全頁快取都使用Redis，則此為必要專案。 指定其中一個快取的資料庫編號；另一個快取預設使用0。<br><br>**重要事項**：如果您對多種型別的快取使用Redis，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派為0，將頁面快取資料庫編號指派為1，並將工作階段儲存資料庫編號指派為2。 | `0` |
| `cache-backend-redis-password` | 密碼 | 設定Redis密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 密碼是直接在Redis的組態檔中設定： `/etc/redis/redis.conf` | |
| `cache-backend-redis-compress-data` | compress_data | 設定為`0`以停用壓縮。 | `1` |
| `cache-backend-redis-compression-lib` | compression_lib | 要使用的壓縮程式庫。 支援的值包括`snappy`、`lzf`、`l4z`、`zstd`和`gzip`。 留空以自動決定。 | |
| `cache-backend-redis-use-lua` | use_lua | 啟用或停用所有Redis作業的Lua指令碼。 <br><br>**預設：保留在`0`.** Lua模式預設為停用，以防止在啟用Lua時，隨附的Redis程式庫(1.17.x)出現的已知效能回歸和GraphQL快取遺漏問題。 | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | 啟用或停用記憶體回收的Lua指令碼（`backend_clean_cache` cron工作）。 <br><br>**預設：保留在`1`.** 刻意啟用，以確保在GC期間進行原子標籤設定清理。 若沒有它，當`backend_clean_cache` cron與快取儲存作業同時執行時，可能會發生競爭條件，使快取專案在快取標籤索引中沒有對應的記錄。 這會導致標籤式失效自動失敗 — 例如，更新產品價格可能不會使產品快取失效，而是需要完整的快取排清。 | `1` |

### Lua模式

啟用時，Lua模式會將多個Redis作業（快取寫入、標籤更新、記憶體回收）整合到透過`EVALSHA`在伺服器端執行的單一Atomic指令碼。 這可防止並行請求中的交錯，例如，確保將快取專案及其標籤成員資格一起寫入。

>[!WARNING]
>
>不瞭解Adobe Commerce版本的影響，請勿變更`use_lua`和`use_lua_on_gc`的預設值：
>
>- **`use_lua`**：在Adobe Commerce 2.4.7或2.4.8 （資料庫`colinmollenhour/cache-backend-redis` 1.17.1）上啟用此專案可能會導致快取損毀，以及GraphQL快取遺漏問題。
>- **`use_lua_on_gc`**：在Adobe Commerce 2.4.8上停用此專案會移除廢棄專案收集期間的原子保護，而且可能導致標籤式快取失效無訊息地失敗，需要完整快取排清才能復原。

## 命令範例（預設快取）

下列範例會啟用Redis預設快取，將主機設定為`127.0.0.1`，並將資料庫編號指派為0。 Redis會針對所有其他引數使用預設值。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## 設定Redis頁面快取

若要在Commerce上設定Redis頁面快取，請使用其他引數執行`setup:config:set`命令。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

常見引數包括：

- `--page-cache=redis`啟用Redis頁面快取。 如果已啟用此功能，請省略此引數。

- `--page-cache-redis-<parameter>=<value>`是設定頁面快取的機碼和值組清單：

| 命令列引數 | 值 | 含義 | 預設值 |
| --- | --- | --- | --- |
| `page-cache-redis-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值127.0.0.1表示Commerce伺服器上已安裝Redis。 | `127.0.0.1` |
| `page-cache-redis-port` | 連線埠 | Redis伺服器接聽連線埠 | `6379` |
| `page-cache-redis-db` | 資料庫 | 如果您對預設和完整頁面快取都使用Redis，則此為必要專案。 指定其中一個快取的資料庫編號；另一個快取預設使用0。<br/>**重要事項**：如果您對多種型別的快取使用Redis，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派為0，將頁面快取資料庫編號指派為1，並將工作階段儲存資料庫編號指派為2。 | `0` |
| `page-cache-redis-password` | 密碼 | 設定Redis密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 在Redis組態檔中設定密碼： `/etc/redis/redis.conf` | |
| `page-cache-redis-compress-data` | compress_data | 設定為`1`以壓縮整頁快取。 使用`0`停用壓縮。 | `0` |
| `page-cache-redis-compression-lib` | compression_lib | 要使用的壓縮程式庫。 支援的值包括`snappy`、`lzf`、`l4z`、`zstd`和`gzip`。 留空以自動決定。 | |

下列範例會啟用Redis頁面快取，將主機設定為`127.0.0.1`，並將資料庫編號指派給`1`。 所有其他引數都會設定為預設值。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### 檢閱Commerce環境設定

執行命令設定Redis快取更新Commerce環境設定(`<Commerce-install-dir>app/etc/env.php`)：

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

## 設定其他快取選項

### Redis預先載入功能

由於Commerce會將設定資料儲存在Redis快取中，因此您可以預先載入在不同頁面之間重複使用的資料。 若要尋找必須預先載入的金鑰，請分析從Redis傳輸到Commerce的資料。 Adobe建議預先載入每個頁面上載入的資料，例如`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`和`DB_IS_UP_TO_DATE`。

Redis使用`pipeline`來複合載入要求。 金鑰應包含資料庫首碼；例如，如果資料庫首碼為`061_`，則預先載入金鑰會如下所示： `061_SYSTEM_DEFAULT`

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

搭配L2快取使用預先載入功能時，您必須將`:hash`尾碼新增至您的金鑰。 L2快取只會傳輸資料的雜湊，不會傳輸實際資料。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### 平行產生

從Commerce 2.4.0版開始，Adobe為想要消除等待鎖定的使用者引入了`allow_parallel_generation`選項。 預設會停用，Adobe建議您在設定和/或區塊數量過多前將其停用。

**若要啟用平行產生**：

```shell
bin/magento setup:config:set --allow-parallel-generation
```

由於它是標幟，因此您無法使用命令將其停用。 手動將設定值設為`false`：

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

## 效能最佳化

如果您使用Symfony快取，您可以透過設定Igbinary序列化程式、安裝igbinary PHP擴充功能和phpredis擴充功能，以及啟用持續連線來進一步最佳化效能。

### Igbinary序列化程式

Igbinary序列化程式比PHP的預設序列化提供顯著的效能改善。 必須在`app/etc/env.php`中手動設定：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### 安裝PHP Igbinary擴充功能

若要使用igbinary序列化，您必須安裝PHP Igbinary延伸模組。

**使用apt （建議用於Debian/Ubuntu）**：

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**使用pecl （替代方法）**：

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### PHP Redis擴充功能

當您的環境支援原生PHP Redis擴充功能(`phpredis`)時，請使用該擴充功能：

#### 使用apt

對於Debian或Ubuntu，請使用`apt`：

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

#### 使用pecl

作為替代方法，請使用`pecl`：

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/<version>/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**效能比較**：

| 作業 | Predis | phpredis | 改進 |
|-----------|--------|----------|-------------|
| 快取取得 | 1-5毫秒 | 0.5至2毫秒 | 速度加快2至3倍 |
| 快取集 | 2-6毫秒 | 0.8至2.5毫秒 | 速度加快2至3倍 |
| 標籤作業 | 10-30毫秒 | 3-10毫秒 | 速度加快3至4倍 |

### 持續連線

持續連線會重複使用各個請求中的現有Redis連線，快取作業速度可提升5-15%。 在`app/etc/env.php`中設定：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>請使用每個快取型別的唯一`persistent_id`來避免連線衝突。

### 完成最佳化的設定

以下是整合所有效能最佳化的生產就緒Redis設定：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## 驗證Redis連線

若要確認Redis和Commerce可正常搭配運作：

1. 登入執行Redis和Commerce的伺服器。
1. 開啟終端機。
1. 使用`redis-cli monitor`命令或`redis-cli ping`命令檢查連線。

如果命令成功，則Redis正在執行，並且可以與Commerce應用程式通訊。 如果失敗，則Redis與Commerce之間存在您需要解決的連線問題。

### Redis監視命令

```shell
redis-cli monitor
```

頁面快取輸出範例：

```text
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
...
```

如果兩個指令都成功，Redis就會正確設定。

### 檢查壓縮資料

若要檢查壓縮的工作階段資料和頁面快取，請使用[RESP.app](https://flathub.org/apps/details/app.resp.RESP)工具。 它支援自動解壓縮Commerce 2工作階段和頁面快取資料，並以可讀取的格式顯示PHP工作階段資料。
