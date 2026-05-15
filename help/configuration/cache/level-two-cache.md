---
title: 效能最佳化的L2快取記憶體設定
description: 瞭解如何在Adobe Commerce中設定L2快取，以減少網路流量並改善效能。 探索舊版和Symfony實作選項。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: 605b2e59d200bc8eeab43e91006a3f95e6a6c138
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# 效能最佳化的L2快取記憶體設定

L2 （兩級）快取可減少遠端快取儲存體（Redis或Valkey）與Commerce應用程式之間的網路流量，方法是在每個Web節點上新增本機快取層。 標準Commerce執行個體每個請求會傳輸約300 KB，而流量在某些情況下可能會快速增加到超過1000個請求。

透過L2快取，每個Web節點都會將經常存取的資料儲存在本機，並使用遠端快取有兩個用途：

- 檢查快取資料版本，以確保最新的快取儲存在本機
- 正在將更新的快取資料從遠端存放區傳輸到本機電腦

Commerce會將雜湊資料版本儲存在遠端快取中，並將尾碼附加至一般金鑰`:hash`。 當本機快取已過期時，會透過快取配接器從遠端電腦擷取資料。

有兩種可用的L2快取實施：

| 實施 | 版本 | 說明 |
| -------------- | ------- | ----------- |
| [舊版(`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | 2.4.x | Zend型兩級快取，具有`Cm_Cache_Backend_File`用於本機儲存 |
| [現代(`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony Cache架構的L2，符合PSR-6規範，效能更佳 |

>[!INFO]
>
>對於雲端基礎結構上的Adobe Commerce，您可以針對L2快取設定使用[部署變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hant#redis_backend)。

## 舊版L2快取設定(RemoteSynchronizedCache)

使用以下範例來修改或取代`app/etc/env.php`檔案中的現有快取區段。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

其中：

- `backend`是L2快取實作。
- `backend_options`是L2快取設定。
   - `remote_backend`是遠端快取實作： Redis或MySQL。
   - `remote_backend_options`是遠端快取設定。
   - `local_backend`是本機快取實作： `Cm_Cache_Backend_File`
   - `local_backend_options`是本機快取設定。
   - `cache_dir`是儲存本機快取之目錄的檔案快取特定選項。

Adobe建議使用Redis進行遠端快取(`\Magento\Framework\Cache\Backend\Redis`)，並使用`Cm_Cache_Backend_File`進行共用記憶體中資料的本機快取，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe建議使用[`cache preload`](redis-pg-cache.md#redis-preload-feature)功能，因為它可大幅降低Redis的壓力。 別忘了為預先載入金鑰新增尾碼&#39;:hash&#39;。

## 過時的快取選項

從Commerce 2.4開始，`use_stale_cache`選項可在平行程式中產生新快取資料時，提供先前快取的資料，藉此改善特定情況下的效能。

一般而言，從效能的角度來看，鎖定等待的權衡是可接受的。 不過，隨著區塊或快取專案數量增加，鎖定需要更多時間。 在某些情況下，等待最多可以是&#x200B;**金鑰數目** x **處理程式查詢逾時**。 在極少數的情況下，商家的`Block/Config`快取中可能會有數百個金鑰，因此即使是小型的鎖定查閱逾時也可能需要幾秒鐘。

>[!IMPORTANT]
>
>過時的快取只適用於L2快取記憶體。 若要啟用它，請將`'use_stale_cache' => true`新增至L2快取前端的最上層設定。

Adobe建議僅對從中獲益最大的快取型別啟用`use_stale_cache`選項，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe不建議為`default`快取型別啟用`use_stale_cache`選項。

下列程式碼顯示設定範例：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
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
],
```

## 現代Symfony L2快取實作

[!BADGE 2.4.9-beta]{type=Negative tooltip="僅適用於2.4.9 Beta版。"}

從Commerce 2.4.9開始，您可以使用Symfony快取型的L2快取實作（`symfony_l2`後端），此實作提供符合PSR 6的現代化快取實作，其效能比傳統`RemoteSynchronizedCache`有顯著改善。

### Symfony L2快取記憶體的優點

- **現代架構**：建置在Symfony快取元件上（符合PSR-6）
- **效能更佳**：原生支援Igbinary序列化、gzip壓縮和Lua指令碼
- **持續連線**：減少連線集區的Redis或Valkey連線負荷
- **預先載入金鑰**：支援重要資料的快取金鑰預先載入
- **過時快取支援**：與`use_stale_cache`選項完全相容
- **簡化組態**：清除後端型別名稱(`redis`、`valkey`、`file`)

### 使用Symfony L2快取的設定範例

對L2快取使用簡化的`symfony_l2`後端型別：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Redis with Symfony Cache
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Symfony L2快取記憶體與過時的快取記憶體

設定個別前端以支援過時的快取：

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
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
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Symfony L2快取記憶體的後端選項

| 選項 | 型別 | 預設 | 說明 |
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | 字串 | `'redis'` | 遠端後端型別： `redis`、`valkey`或`file` |
| `remote_backend_options` | 陣列 | `[]` | 遠端後端設定（請參閱Redis/Valkey檔案） |
| `local_backend` | 字串 | `'file'` | 本機後端型別： `file`或`apcu` |
| `local_backend_options` | 陣列 | `[]` | 本機後端設定 |
| `cleanup_percentage` | 整數 | `90` | L1快取清理閾值(1-100) |
| `use_stale_cache` | 布林值 | `false` | 啟用過時的快取，以獲得高可用性 |

### Valkey支援

`symfony_l2`後端也支援Valkey做為遠端後端：

```php
'backend_options' => [
    'remote_backend' => 'valkey',  // Use Valkey instead of Redis
    'remote_backend_options' => [
        'server' => 'localhost',
        'database' => '0',
        'port' => '6379',
        'serializer' => 'igbinary',
        'compression_lib' => 'gzip',
    ],
    // ... rest of configuration
]
```

如需詳細的組態選項，請參閱：
- [使用Symfony快取的Redis快取設定](redis-pg-cache.md)
- [具有Symfony快取的Valkey快取設定](valkey-pg-cache.md)
