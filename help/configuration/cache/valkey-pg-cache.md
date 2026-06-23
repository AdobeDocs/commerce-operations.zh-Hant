---
title: 設定預設和頁面快取的Valkey
description: 瞭解如何設定Valkey為Adobe Commerce的預設和頁面快取後端。 探索CLI命令、env.php設定和連線驗證。
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T22:00:55.389Z'
TQID: 'https://experienceleague.adobe.com/AjJ86dYGRVFuY1T73ct1Gpcf6iDbb4ewP8OiGX8otQs'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 1281
ht-degree: 0%

---


# 設定預設和頁面快取的Valkey

Commerce提供命令列選項，用於設定Valkey預設值和頁面快取。 雖然您可以透過編輯`<Commerce-install-dir>app/etc/env.php`檔案來設定快取，但建議使用命令列的方法，尤其是對於初始設定。 命令列會提供驗證，確保組態語法正確。

{{cloud-cache-config}}

**先決條件：**

[請先安裝Valkey](config-valkey.md#install-valkey)，然後再繼續。

## 支援的框架

>[!BEGINTABS]

>[!TAB Zend快取（2.4.8和更早版本）]

- **Zend快取（2.4.8和更早版本）** — Commerce 2.4.8和更早版本的舊版Valkey後端：
   - **舊版Valkey後端** — 使用完整類別路徑(`Magento\Framework\Cache\Backend\Valkey`)
   - **預先載入金鑰** — 支援預先載入常用的快取金鑰
   - **Lua指令碼** — 記憶體回收的Lua
   - **壓縮** — 支援資料壓縮

>[!TAB Symfony快取(2.4.9+)]

- **Symfony快取(2.4.9+)** — 從Commerce 2.4.9開始，Symfony快取為Valkey提供符合PSR 6規範的現代化快取實作，並大幅改善效能：
   - **自動Valkey流水線** — 將多個作業批次化為單一請求，減少延遲
   - **PSR-6 TagAwareAdapter** — 利用原子作業有效率地讓標籤式快取失效
   - **Igbinary序列化** — 二進位序列化將快取專案大小減少45%，並將速度提高5-10%
   - **增強型持續連線** — 更穩定的連線集區，以及更妥善的處理分叉的處理程式
   - **最佳化的Lua指令碼** — 伺服器端執行結合流水線以發揮最大效率

>[!ENDTABS]

## 設定Valkey預設快取

執行`setup:config:set`命令並指定Valkey預設快取的引數。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`啟用Valkey預設快取。 如果已啟用此功能，請省略此引數。

- `--cache-backend-valkey-<parameter>=<value>`是設定預設快取的機碼值組清單：

{{valkey-redis-cli-note}}

| 命令列引數 | 值 | 含義 | 預設值 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值`127.0.0.1`表示Valkey已安裝在Commerce伺服器上。 | `127.0.0.1` |
| `cache-backend-valkey-port` | 連線埠 | Valkey伺服器接聽連線埠 | `6379` |
| `cache-backend-valkey-db` | 資料庫 | 如果您對預設和全頁快取都使用Valkey，則此為必填欄位。 指定其中一個快取的資料庫編號；另一個快取預設使用`0`。<br><br>**重要事項**：如果您對多種型別的快取使用Valkey，則資料庫編號必須不同。 Adobe建議您將預設快取資料庫編號指派給`0`，將分頁快取資料庫編號指派給`1`，並將工作階段儲存資料庫編號指派給`2`。 | `0` |
| `cache-backend-valkey-password` | 密碼 | 設定Valkey密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 密碼是直接在Valkey的組態檔中設定： `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | 啟用或停用LUA。 <br><br>**LUA**： Lua可讓我們在Valkey內執行部分應用程式邏輯，藉由原子執行來改善效能並確保資料的一致性。 | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | 啟用或停用記憶體回收的LUA。 <br><br>**LUA**： Lua可讓我們在Valkey內執行部分應用程式邏輯，藉由原子執行來改善效能並確保資料的一致性。 | `1` |

## 命令範例（預設快取）

下列範例會啟用Valkey預設快取，將主機設定為`127.0.0.1`，並將資料庫編號指派給`0`。 Valkey會針對所有其他引數使用預設值。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## 設定Valkey頁面快取

若要在Commerce上設定Valkey頁面快取，請使用其他引數執行`setup:config:set`命令。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

，並使用下列引數：

- `--page-cache=valkey`啟用Valkey頁面快取。 如果已啟用此功能，請省略此引數。

- `--page-cache-valkey-<parameter>=<value>`是設定頁面快取的機碼和值組清單：

| 命令列引數 | 值 | 含義 | 預設值 |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值`127.0.0.1`表示Valkey已安裝在Commerce伺服器上。 | `127.0.0.1` |
| `page-cache-valkey-port` | 連線埠 | Valkey伺服器接聽連線埠。 | `6379` |
| `page-cache-valkey-db` | 資料庫 | 如果您針對預設和全頁快取都使用Valkey，則此為必要專案。 指定其中一個快取的資料庫編號；另一個快取預設使用`0`。<br/>**重要事項**：如果您對多種型別的快取使用Valkey，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派給`0`，將分頁快取資料庫編號指派給`1`，並將工作階段儲存資料庫編號指派給`2`。 | `0` |
| `page-cache-valkey-password` | 密碼 | 設定Valkey密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 在Valkey組態檔中設定密碼： `/etc/valkey/valkey.conf` | |

### 命令範例（頁面快取）

下列範例會啟用Valkey頁面快取，將主機設定為`127.0.0.1`，並將資料庫編號指派給`1`。 所有其他引數都會設定為預設值。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### 檢閱Commerce環境設定

執行命令設定Valkey快取會更新Commerce環境設定(`<Commerce-install-dir>app/etc/env.php`)：

>[!BEGINTABS]

>[!TAB Zend快取（2.4.8和更早版本）]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

>[!TAB Symfony快取(2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>從Commerce 2.4.9開始，請使用簡化的後端型別`'backend' => 'valkey'`，而非完整的類別路徑。 指定簡化名稱時，會自動使用Symfony快取。

>[!ENDTABS]

## 設定其他快取選項

### Valkey預先載入功能

由於Commerce會將設定資料儲存在Valkey快取中，因此您可以預先載入在不同頁面之間重複使用的資料。 若要尋找必須預先載入的金鑰，請分析從Valkey傳輸到Commerce的資料。 Adobe建議預先載入每個頁面上載入的資料，例如`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`和`DB_IS_UP_TO_DATE`。

Valkey使用`pipeline`來複合載入要求。 金鑰應包含資料庫首碼；例如，如果資料庫首碼為`061_`，則預先載入金鑰會如下所示： `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Zend快取]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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

>[!TAB Symfony快取]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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

>[!ENDTABS]

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

>[!BEGINTABS]

>[!TAB Zend快取]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB Symfony快取]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Symfony快取效能最佳化

如果您使用Symfony快取，您可以透過設定Igbinary序列化程式、安裝igbinary PHP擴充功能和phpredis擴充功能，以及啟用持續連線來進一步最佳化效能。

### Igbinary序列化程式

Igbinary序列化程式比PHP的預設序列化提供顯著的效能改善。 必須在`app/etc/env.php`中手動設定：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
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

### PHP Redis擴充功能：phpredis與Predis的比較

Commerce 2.4.9+包含在phpredis （原生C擴充功能）和Predis （純PHP程式庫）之間的自動遞補。 為獲得最佳效能，請安裝phpredis：

**使用apt （建議用於Debian/Ubuntu）**：

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**使用pecl （替代方法）**：

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
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

持續連線會重複使用各個請求中的現有Valkey連線，快取作業速度可加快5-15%。 在`app/etc/env.php`中設定：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
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
                'server' => 'valkey',
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

以下是結合所有效能最佳化的生產就緒組態：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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

## 驗證Valkey連線

若要確認Valkey和Commerce可正常搭配運作：

1. 登入執行Valkey和Commerce的伺服器。
1. 開啟終端機。
1. 使用`valkey-cli monitor`命令或`valkey-cli ping`命令檢查連線。

如果命令成功，則Valkey正在執行，並且可以與Commerce應用程式通訊。 如果失敗，則表示Valkey與Commerce之間的連線問題您必須解決。

### Valkey monitor命令

```shell
valkey-cli monitor
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
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Valkey ping命令

```shell
valkey-cli ping
```

預期的回應是： `PONG`

如果兩個命令都成功，就會正確設定Valkey。

### 檢查壓縮資料

若要檢查壓縮的工作階段資料和頁面快取，請使用[RESP.app](https://flathub.org/apps/app.resp.RESP)工具。 它支援自動解壓縮Commerce 2工作階段和頁面快取資料，並以人類看得懂的格式顯示PHP工作階段資料。

