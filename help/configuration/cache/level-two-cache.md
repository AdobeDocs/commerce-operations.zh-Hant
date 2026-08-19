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
source-git-commit: 7ebadd26eee51aa2c2f3dfe8a8a2ed3dc20657b9
workflow-type: tm+mt
source-wordcount: 1725
ht-degree: 0%

---

# 效能最佳化的L2快取記憶體設定

L2 （兩級）快取可減少遠端快取儲存體（Redis或Valkey）與Commerce應用程式之間的網路流量，方法是在每個Web節點上新增本機快取層。 標準Commerce執行個體每個請求會傳輸約300 KB，而流量在某些情況下可能會快速增加到超過1000個請求。

透過L2快取，每個Web節點都會將經常存取的資料儲存在本機，並使用遠端快取有兩個用途：

- 檢查快取資料版本，以確保最新的快取儲存在本機
- 正在將更新的快取資料從遠端存放區傳輸到本機電腦

Commerce會將雜湊資料版本儲存在遠端快取中，並將尾碼附加至一般金鑰`:hash`。 當本機快取已過期時，會透過快取配接器從遠端電腦擷取資料。

Adobe Commerce提供兩種L2快取實作：

| 實施 | 版本 | 說明 |
| -------------- | ------- | ----------- |
| [舊版(`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Zend型兩級快取，具有`Cm_Cache_Backend_File`用於本機儲存 |
| [現代(`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony快取型L2，符合PSR-6規範，效能更佳。 支援Valkey。 |

Symfony L2快取是Adobe Commerce 2.4.9及更新版本的建議實作。 它提供符合PSR 6的現代化快取實作，比傳統`RemoteSynchronizedCache`有顯著的效能改善。

## 舊版L2快取設定(RemoteSynchronizedCache)

舊版L2快取設定指示適用於舊版Adobe Commerce。 如果您使用Adobe Commerce 2.4.9或更新版本，請使用Valkey搭配[Modern Symfony L2快取實作](#modern-symfony-l2-cache-implementation)。

>[!NOTE]
>
>本頁僅說明內部部署設定。 若為雲端上的Adobe Commerce，請參閱[設定L2快取](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)。

對於支援Redis的Adobe Commerce內部部署版本，請使用以下範例來修改或取代`app/etc/env.php`檔案中的現有快取區段。

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
  - `local_backend`是本機快取實作： `Cm_Cache_Backend_File`。
  - `local_backend_options`是本機快取設定。
  - `cache_dir`是儲存本機快取之目錄的檔案快取特定選項。

對於支援Redis的2.4.9之前的Adobe Commerce版本，Adobe建議使用Redis進行遠端快取(`\Magento\Framework\Cache\Backend\Redis`)，並使用`Cm_Cache_Backend_File`在共用記憶體中本機快取資料，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`。

Adobe建議使用[`cache preload`](redis-pg-cache.md#redis-preload-feature)功能，因為它可大幅降低Redis的壓力。 別忘了為預先載入金鑰新增尾碼`:hash`。

## 過時的快取選項

從Commerce 2.4開始，`use_stale_cache`選項可在平行程式中產生新快取資料時，提供先前快取的資料，藉此改善特定情況下的效能。 本節中說明的建議快取型別和權衡適用於舊版`RemoteSynchronizedCache`和`symfony_l2`實作。 如需`symfony_l2`組態範例，請參閱[具有過時快取的Symfony L2快取](#symfony-l2-cache-with-stale-cache)。

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

下列程式碼顯示舊版`RemoteSynchronizedCache`後端的設定範例。 如需`symfony_l2`範例，請參閱[具有過時快取的Symfony L2快取](#symfony-l2-cache-with-stale-cache)。

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

>[!IMPORTANT]
>
>Redis不支援做為遠端快取後端，開頭為：
>
>- Adobe Commerce 2.4.9和更新版本
>- 2.4.8-p4和更新版本的修補程式
>- 2.4.7-p9和更新版本的修補程式
>- 2.4.6-p14和更新版本的修補程式
>- 2.4.5-p16和更新版本的修補程式
>
>如果您要升級超過這些版本，請設定Valkey並更新您的快取設定以使用`symfony_l2`。 請參閱[設定Valkey](config-valkey.md)和[系統需求](../../installation/system-requirements.md)。

### Symfony L2快取記憶體的優點

- **現代架構：**&#x200B;建置在Symfony快取元件上（符合PSR-6）
- **效能更佳：**&#x200B;原生支援Igbinary序列化、gzip壓縮和Lua指令碼
- **持續連線：**&#x200B;可減少連線集區的Valkey連線額外負荷
- **預先載入金鑰：**&#x200B;支援重要資料的快取金鑰預先載入
- **過時快取支援：**&#x200B;與`use_stale_cache`選項完全相容
- **簡化設定：**&#x200B;清除程式後端型別名稱(`valkey`， `file`)

### 從RemoteSynchronizedCache移轉至Symfony L2

如果您要將內部部署安裝從舊版`RemoteSynchronizedCache`後端升級至`symfony_l2`，請先檢閱下列專案，然後再更新`app/etc/env.php`。 僅變更`backend`值是不夠的。 組態結構、金鑰名稱及某些預設行為會有所不同。

- **組態結構變更。** `remote_backend`、`remote_backend_options`和`local_backend`在`symfony_l2`下使用不同的值。 例如，`remote_backend`會變成`'valkey'`，而非完整類別名稱。 請使用下方的[設定範例](#configuration-example-with-symfony-l2-cache)作為您的起點，而非就地編輯您現有的舊組態。

- 不建議將&#x200B;**`preload_keys`與`symfony_l2`.**&#x200B;搭配使用 如果您的舊組態包含`preload_keys`，請在移轉時將其移除。 預先載入金鑰不會改善`symfony_l2`下的效能，而且會觸發其他不必要的金鑰查閱，增加Valkey的負載。

- **壓縮需要明確的旗標。** 單獨設定`compression_lib`不會啟用`symfony_l2`下的壓縮。 如需必要的`compress_data`設定，請參閱Symfony L2快取的[後端選項](#backend-options-for-symfony-l2-cache)。

- **預設不會針對手動設定的內部部署啟用過時快取。** `symfony_l2`底下的`use_stale_cache`預設為`false` （請參閱[後端選項表](#backend-options-for-symfony-l2-cache)）。 如果您的舊組態使用`stale_cache_enabled`前端，您必須使用[Symfony L2快取中的模式（具有過時的快取](#symfony-l2-cache-with-stale-cache)）明確地重新建立它。

>[!NOTE]
>
>設定`VALKEY_BACKEND: symfony_l2`部署變數的雲端環境上的Adobe Commerce具有其完整的L2設定，包括`stale_cache_enabled`前端，是由`ece-tools`自動產生。 請參閱[設定Symfony L2快取](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)，瞭解雲端特有的行為。

- **Redis不是`symfony_l2`支援的遠端後端。** 移轉至Valkey，作為此變更的一部分。 請參閱[設定Valkey](config-valkey.md)。

### 使用Symfony L2快取的設定範例

>[!NOTE]
>
>此範例適用於內部部署`app/etc/env.php`設定。 對於雲端上的Adobe Commerce，快取設定是由`ece-tools`自動管理。 請參閱[設定Symfony L2快取](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)，而非直接編輯`env.php`。

在`app/etc/env.php`檔案中，為L2快取使用簡化的`symfony_l2`後端型別。 此範例不包含`preload_keys`組態，不建議與`symfony_l2`搭配使用。 如需詳細資訊，請參閱[從RemoteSynchronizedCache移轉至Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2)。

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
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
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

請參閱[過時快取選項](#stale-cache-options)，瞭解哪些快取型別受益於過時快取及原因。

使用下列範例來設定`symfony_l2`過時快取支援的個別前端：

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
                    'compress_data' => '1',
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
                    'compress_data' => '1',
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
| -------- | ------ | --------- | --------------------------------------------------------------------- |
| `remote_backend` | 字串 | `'valkey'` | 遠端後端型別： `valkey`或`file`。 使用`valkey`進行L2快取。 |
| `remote_backend_options` | 陣列 | `[]` | 遠端後端設定（請參閱Valkey檔案） |
| `local_backend` | 字串 | `'file'` | 本機後端型別： `file`或`apcu` |
| `local_backend_options` | 陣列 | `[]` | 本機後端設定 |
| `cleanup_percentage` | 整數 | `95` | L1快取清理閾值(1-100) |
| `use_stale_cache` | 布林值 | `false` | 啟用過時的快取，以獲得高可用性 |
| `compress_data` | 布林值 | `false` | 與`compression_lib`結合時啟用壓縮。 單獨設定`compression_lib`不會啟用壓縮。 |
| `persistent` | 布林值 | `true` | 控制到遠端後端的持續連線。 設定為`false` (`'0'`)以符合舊版Zend快取行為，其預設為非持續連線。 |


>[!NOTE]
>
>- `remote_backend`選項也接受`redis`的值，但官方不支援Redis （請參閱上文[Modern Symfony L2快取實作](#modern-symfony-l2-cache-implementation)下的備註）。
>
>- 舊版`RemoteSynchronizedCache`組態中使用的`frontend_options.write_control`不適用於`symfony_l2`。

### 增強的Symfony L2快取記憶體效能與可靠性

>[!NOTE]
>
>這些改善適用於使用`symfony_l2`的Adobe Commerce 2.4.9部署，並可在修補程式ACP2E-5132中取得。 若為Adobe Commerce內部部署，請使用Quality Patches Tool (QPT)套用此修補程式。 若為雲端上的Adobe Commerce，此修補程式會透過[Commerce的雲端修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest)自動傳送。

最新的更新改善了Symfony L2快取記憶體的擴充性，減少不必要的檔案系統I/O，並增強快取記憶體一致性和可靠性。

#### 最佳化的Symfony L2快取標籤儲存

針對Valkey支援的部署最佳化Symfony L2快取行為，消除多餘的檔案系統標籤索引寫入。 快取標籤現在僅儲存在Valkey中，使Symfony L2快取行為與舊版快取實施一致。 這樣可以減少不必要的磁碟I/O，改善快取寫入效能，並防止`var/cache/symfony/tags/`目錄成長。

#### 改善檔案式快取行為

對於使用檔案式快取（沒有Valkey）的部署，會繼續維護本機標籤索引以支援快取失效。 標籤索引現在會寫入已設定的`cache_dir`，而不是先前硬式編碼的`var/cache`位置，以確保一致的快取目錄使用方式，並改善對自訂快取設定的支援。

#### 重新標籤後過時標籤成員資格修正

重新標籤快取專案可能會讓該專案與其不再所屬的標籤相關聯。 過時的標籤會籍現在會在重新標籤時清除，因此快取專案只會由目前指派給它們的標籤失效。

#### 針對未變更的儲存進行備援遠端寫入修正

儲存含有未變更內容的快取專案仍會觸發寫入遠端(Valkey)後端。 現在，當內容未變更時會略過儲存，減少不必要的遠端寫入。

#### L1依大小修正搬遷(cleanup_percentage)

用於L1以大小為基礎的逐出的`cleanup_percentage`臨界值未一致地觸發清除。 L1快取逐出現在會正確遵循設定的`cleanup_percentage`。

#### 舊快取的重新產生鎖定

當啟用`use_stale_cache`且專案的遠端復本暫時無法使用時，只有一個處理序現在會取得短期鎖定，以重新產生該專案。 相同專案的其他並行請求會繼續提供現有的本機值，而非自行重新產生，減少重新產生踩踏次數及多餘的後端負載。

#### 影響

- 針對Valkey支援的Symfony L2快取部署，消除多餘的檔案系統標籤索引寫入，減少磁碟I/O，並防止`var/cache/symfony/tags/`目錄的不必要成長。
- 確保檔案式快取部署一致地使用設定的`cache_dir`作為本機標籤索引，同時保留快取失效行為。
- 防止重新標籤後留下的過時標籤成員資格導致不正確的快取失效。
- 減少未變更快取儲存所不需要的遠端寫入，降低網路和後端負載。
- 確保L1快取逐出在設定的`cleanup_percentage`臨界值處可靠觸發。
- 選取每個索引鍵的單一再生器，而非重建每個並行請求，以減少`use_stale_cache`專案的再生次數。

如需詳細的組態選項，請參閱：

- [具有Symfony快取的Valkey快取設定](valkey-pg-cache.md)

>[!MORELIKETHIS]
>
>- [快取總覽和組態選項](caching-overview.md)
>- [快取後端選項和儲存參考](cache-options.md)
>- [設定快取前端和型別](cache-types.md)
>- [為預設和頁面快取設定Redis](redis-pg-cache.md)
