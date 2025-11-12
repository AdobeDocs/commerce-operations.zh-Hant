---
title: 使用Valkey作為預設快取
description: 瞭解如何將Valkey設定為Adobe Commerce的預設快取。 探索命令列設定、設定選項和驗證技術。
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: e9f1bef9f97a0e1d738f1221758f1b9a0a238da1
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# 使用Valkey作為預設快取

Commerce提供命令列選項來設定Valkey頁面和預設快取。 雖然您可以透過編輯`<Commerce-install-dir>app/etc/env.php`檔案來設定快取，但建議使用命令列的方法，尤其是對於初始設定。 命令列會提供驗證，確保組態語法正確。

您必須[安裝Valkey](config-redis.md#install-redis)，才能繼續。

## 設定Valkey預設快取

執行`setup:config:set`命令並指定Valkey預設快取的引數。

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`啟用valkey預設快取。 如果已啟用此功能，請省略此引數。

- `--cache-backend-valkey-<parameter>=<value>`是設定預設快取的機碼值組清單：

>[!NOTE]
>
>從&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;開始，**Valkey**&#x200B;已因授權變更正式取代CLI工具中的Redis。 Valkey是Redis的分支，可維護幾乎相同的功能。 對於&#x200B;**版本2.4.8和更早版本**，用於設定Valkey的CLI命令與Redis的命令相同，可確保順暢的回溯相容性，並簡化移轉或雙環境支援。 下列範例顯示Valkey特定命令。

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

| 命令列引數 | 值 | 含義 | 預設值 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值`127.0.0.1`表示Valkey已安裝在Commerce伺服器上。 | `127.0.0.1` |
| `cache-backend-valkey-port` | 連線埠 | Valkey伺服器接聽連線埠 | `6379` |
| `cache-backend-valkey-db` | 資料庫 | 如果您對預設和全頁快取都使用Valkey，則此為必填欄位。 您必須指定其中一個快取的資料庫編號；另一個快取預設使用`0`。<br><br>**重要**：如果您將Valkey用於多種快取型別，則資料庫編號必須不同。 Adobe建議您將預設快取資料庫編號指派給`0`，將分頁快取資料庫編號指派給`1`，並將工作階段儲存資料庫編號指派給`2`。 | `0` |
| `cache-backend-valkey-password` | 密碼 | 設定Valkey密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 直接在Valkey組態檔中設定密碼： `/etc/valkey/valkey.conf` | |

### 命令範例

下列範例會啟用Valkey預設快取，將主機設定為`127.0.0.1`，並將資料庫編號指派給`0`。 Valkey會針對所有其他引數使用預設值。

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>從&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;開始，**Valkey**&#x200B;已因授權變更正式取代CLI工具中的Redis。 Valkey是Redis的分支，可維護幾乎相同的功能。 對於&#x200B;**版本2.4.8和更早版本**，用於設定Valkey的CLI命令與Redis的命令相同，可確保順暢的回溯相容性，並簡化移轉或雙環境支援。 下列範例顯示Valkey特定命令。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## 設定頁面快取

若要在Commerce上設定Valkey頁面快取，請使用其他引數執行`setup:config:set`命令。

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

，並使用下列引數：

- `--page-cache=valkey`啟用Valkey頁面快取。 如果已啟用此功能，請省略此引數。

- `--page-cache-valkey-<parameter>=<value>`是設定頁面快取的機碼和值組清單：

>[!NOTE]
>
>從&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;開始，**Valkey**&#x200B;已因授權變更正式取代CLI工具中的Redis。 Valkey是Redis的分支，可維護幾乎相同的功能。 對於&#x200B;**版本2.4.8和更早版本**，用於設定Valkey的CLI命令與Redis的命令相同，可確保順暢的回溯相容性，並簡化移轉或雙環境支援。 下列範例顯示Valkey特定命令。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| 命令列引數 | 值 | 含義 | 預設值 |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | 伺服器 | 完整的主機名稱、IP位址或UNIX通訊端的絕對路徑。 預設值`127.0.0.1`表示Valkey已安裝在Commerce伺服器上。 | `127.0.0.1` |
| `page-cache-valkey-port` | 連線埠 | Valkey伺服器接聽連線埠。 | `6379` |
| `page-cache-valkey-db` | 資料庫 | 如果您針對預設和全頁快取都使用Valkey，則此為必要專案。 您必須指定其中一個快取的資料庫編號；另一個快取預設使用`0`。<br/>**重要**：如果您將Valkey用於多種快取型別，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派給`0`，將分頁快取資料庫編號指派給`1`，並將工作階段儲存資料庫編號指派給`2`。 | `0` |
| `page-cache-valkey-password` | 密碼 | 設定Valkey密碼可啟用其中一項內建的安全性功能： `auth`命令，它要求使用者端驗證以存取資料庫。 在Valkey組態檔中設定密碼： `/etc/valkey/valkey.conf` | |

### 命令範例

下列範例會啟用Valkey頁面快取，將主機設定為`127.0.0.1`，並將資料庫編號指派給`1`。 所有其他引數都會設定為預設值。

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>從&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;開始，**Valkey**&#x200B;已因授權變更正式取代CLI工具中的Redis。 Valkey是Redis的分支，可維護幾乎相同的功能。 對於&#x200B;**版本2.4.8和更早版本**，用於設定Valkey的CLI命令與Redis的命令相同，可確保順暢的回溯相容性，並簡化移轉或雙環境支援。 下列範例顯示Valkey特定命令。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## 結果

由於這兩個範例命令，Commerce將類似下列的行新增到`<Commerce-install-dir>app/etc/env.php`：

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

## 新的Valkey快取實作

[!BADGE 2.4.9-alpha]{type=Negative tooltip="僅適用於2.4.9 Alpha。"}

從Adobe Commerce 2.4.9開始，Adobe建議使用Valkey快取實作： `\Magento\Framework\Cache\Backend\Valkey`。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Valkey預先載入功能

由於Commerce會將設定資料儲存在Valkey快取中，因此您可以預先載入在不同頁面之間重複使用的資料。 若要尋找必須預先載入的金鑰，請分析從Valkey傳輸到Commerce的資料。 Adobe建議預先載入每個頁面上載入的資料，例如`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`和`DB_IS_UP_TO_DATE`。

Valkey使用`pipeline`來複合載入要求。 金鑰應包含資料庫首碼；例如，如果資料庫首碼為`061_`，則預先載入金鑰會如下所示： `061_SYSTEM_DEFAULT`

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

搭配L2快取使用預先載入功能時，您必須將`:hash`尾碼新增至您的金鑰。 L2快取只會傳輸資料的雜湊，不會傳輸實際資料。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 平行產生

從Commerce 2.4.0版開始，Adobe為想要消除等待鎖定的使用者引入了`allow_parallel_generation`選項。
預設會停用，Adobe建議您在設定和/或區塊數量過多前將其停用。

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
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## 驗證Valkey連線

若要確認Valkey和Commerce是否正常運作，請登入執行Valkey的伺服器、開啟終端機，然後使用`valkey-cli monitor`命令或`redis-cli ping`命令。

### Valkey monitor命令

```bash
valkey-cli monitor
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

### Valkey ping命令

```bash
valkey-cli ping
```

預期的回應是： `PONG`

如果兩個命令都成功，就會正確設定Valkey。

### 檢查壓縮資料

為了檢查壓縮的工作階段資料和頁面快取，[RESP.app](https://flathub.org/apps/app.resp.RESP)支援自動解壓縮Commerce 2工作階段和頁面快取，並以人類可讀的格式顯示PHP工作階段資料。
