---
title: 效能最佳化的L2快取記憶體設定
description: 瞭解如何在Adobe Commerce中設定L2快取，以減少網路流量並改善效能。 探索舊版和Symfony實作選項。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
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
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: d9152906a6fbbd765a60e3aeacdbf7cc7527529d
workflow-type: tm+mt
source-wordcount: 1166
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
| [舊版(`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Zend型兩級快取，具有`Cm_Cache_Backend_File`用於本機儲存 |
| [現代(`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony快取型L2，符合PSR-6規範，效能更佳。 僅支援Valkey。 |

## 舊版L2快取設定(RemoteSynchronizedCache)

>[!NOTE]
>
>舊版L2快取設定指示適用於舊版Adobe Commerce。 如果您使用Adobe Commerce 2.4.9或更新版本，請使用Valkey搭配[Symfony 2進行L2快取](#modern-symfony-l2-cache-implementation)。

快取設定指示取決於您的部署型別：

- **對於雲端上的Adobe Commerce**，請在`.magento.env.yaml`中設定[`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend)或[`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)部署變數來設定L2快取。 如需設定範例，請參閱[設定L2快取](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)。

- **對於支援Redis**&#x200B;的Adobe Commerce內部部署版本，請使用下列範例來修改或取代`app/etc/env.php`檔案中的現有快取區段。

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
]
```

其中：

- `backend`是L2快取實作。
- `backend_options`是L2快取設定。
  - `remote_backend`是遠端快取實作： Redis或MySQL。
  - `remote_backend_options`是遠端快取設定。
  - `local_backend`是本機快取實作： `Cm_Cache_Backend_File`
  - `local_backend_options`是本機快取設定。
  - `cache_dir`是儲存本機快取之目錄的檔案快取特定選項。

若為Adobe Commerce Adobe，建議使用Redis進行遠端快取(`\Magento\Framework\Cache\Backend\Redis`)，並使用`Cm_Cache_Backend_File`在共用記憶體中本機快取資料，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

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

在Commerce 2.4.9+版中，請使用Symfony快取架構的L2快取實作（`symfony_l2`後端），而非舊版的L2快取。 Symfony L2快取提供符合PSR 6的現代化快取實作，其效能比傳統`RemoteSynchronizedCache`有顯著改善。

>[!NOTE]
>
>對於雲端上的Adobe Commerce，ECE工具套件(`ece-tools`)會自動管理此設定。 不要直接編輯`app/etc/env.php` — 部署會覆寫手動變更。 如需雲端設定，請參閱[改為設定Symfony L2快取](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)。

>[!IMPORTANT]
>
>{{redis-cache-support}}
>
>由於`symfony_l2`僅可在Adobe Commerce 2.4.9及更高版本中使用，請將其設定為Valkey作為遠端後端。 Redis不是正式支援的`symfony_l2`遠端後端。 如需依版本支援的快取服務，請參閱[系統需求](../../installation/system-requirements.md)。

### Symfony L2快取記憶體的優點

- **現代架構**：建置在Symfony快取元件上（符合PSR-6）
- **效能更佳**：原生支援Igbinary序列化、gzip壓縮和Lua指令碼
- **持續連線**：減少連線集區的Valkey連線額外負荷
- **預先載入金鑰**：支援重要資料的快取金鑰預先載入
- **過時快取支援**：與`use_stale_cache`選項完全相容
- **簡化組態**：清除後端型別名稱(`valkey`， `file`)

### 使用Symfony L2快取的設定範例

對L2快取使用簡化的`symfony_l2`後端型別：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
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
                'remote_backend' => 'valkey',
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
                'remote_backend' => 'valkey',
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
| `remote_backend` | 字串 | `'valkey'` | 遠端後端型別： `valkey`或`file`。 使用`valkey`進行L2快取。 |
| `remote_backend_options` | 陣列 | `[]` | 遠端後端設定（請參閱Valkey檔案） |
| `local_backend` | 字串 | `'file'` | 本機後端型別： `file`或`apcu` |
| `local_backend_options` | 陣列 | `[]` | 本機後端設定 |
| `cleanup_percentage` | 整數 | `95` | L1快取清理閾值(1-100) |
| `use_stale_cache` | 布林值 | `false` | 啟用過時的快取，以獲得高可用性 |

>[!NOTE]
>
>`remote_backend`選項也接受`redis`的值。 不過，Redis不是官方支援的Adobe Commerce 2.4.9及更新版本的快取服務。 Adobe建議僅使用`valkey`設定`symfony_l2`。 如需依版本支援的快取服務，請參閱[系統需求](../../installation/system-requirements.md)。

### 增強的Symfony L2快取記憶體效能與可靠性

>[!NOTE]
>
>這些改善適用於使用`symfony_l2`的Adobe Commerce 2.4.9部署，並可搭配ACP2E-5132修補程式使用。 如需最新修補程式發行說明，請參閱[Commerce雲端修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest)。

#### 最佳化的Symfony L2快取標籤儲存

針對Valkey支援的部署最佳化Symfony L2快取行為，消除多餘的檔案系統標籤索引寫入。 快取標籤現在僅儲存在Valkey中，使Symfony L2快取行為與舊版快取實施一致。 這樣可以減少不必要的磁碟I/O，改善快取寫入效能，並防止`var/cache/symfony/tags/`目錄成長。

#### 改善檔案式快取行為

對於使用檔案式快取（沒有Valkey）的部署，會繼續維護本機標籤索引以支援快取失效。 標籤索引現在會寫入已設定的`cache_dir`，而不是先前硬式編碼的`var/cache`位置，以確保一致的快取目錄使用方式，並改善對自訂快取設定的支援。

#### 改善快取失效

快取失效現在會使用以TTL為基礎的重新產生鎖定搭配適當的L1標籤清除，消除標籤失效後可能持續存在的過時快取專案。

#### 預設為啟用壓縮

Symfony L2快取記憶體現在預設啟用Redis/Valkey壓縮(`compress_data`)，減少記憶體耗用和網路流量，並符合舊版快取實作的預設行為。

#### 影響

- 針對Valkey支援的Symfony L2快取部署，消除多餘的檔案系統標籤索引寫入。
- 減少磁碟I/O並改善快取寫入效能。
- 防止`var/cache/symfony/tags/`目錄的不必要增長。
- 確保檔案式快取部署一致地使用設定的`cache_dir`，同時保留快取失效行為。
- 透過以TTL為基礎的重新產生鎖定和適當的L1標籤清除，消除過時的快取專案。
- 在預設啟用`compress_data`的情況下，減少記憶體耗用和網路流量。

如需詳細的組態選項，請參閱：
- [具有Symfony快取的Valkey快取設定](valkey-pg-cache.md)

