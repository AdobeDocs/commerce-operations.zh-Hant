---
title: L2快取設定
description: 瞭解如何設定L2快取。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: ba3c656566af47f16f58f476d7bc9f4781bb0234
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# L2快取設定

快取可減少遠端快取儲存與Commerce應用程式之間的網路流量。 標準Commerce執行個體每個請求會傳輸約300 kb，而流量在某些情況下可能會快速增加到超過~1000個請求。

若要減少Redis的網路頻寬，請將快取資料儲存在每個網頁節點的本機，並使用遠端快取有兩個用途：

- 檢查快取資料版本，並確定最新的快取儲存在本機
- 將最新的快取從遠端電腦傳輸至本機電腦

Commerce會將雜湊資料版本儲存在Redis中，尾碼為&#39;:hash&#39;附加至一般索引鍵。 如果有過時的本機快取，資料會透過快取配接器傳輸到本機電腦。

>[!INFO]
>
>對於雲端基礎結構上的Adobe Commerce，您可以針對L2快取設定使用[部署變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend)。

## 設定範例

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

從[!DNL Commerce] 2.4開始，`use_stale_cache`選項在某些特定情況下可以改善效能。

一般來說，從效能方面來說，可以接受以等待鎖定來取捨，但商家擁有的區塊或快取數目越多，等待鎖定的時間就越多。 在某些情況下，您可以等待處理程式的&#x200B;**個金鑰** \* **查詢逾時**&#x200B;時間。 在極少數的情況下，商家在`Block/Config`快取中可能有數百個金鑰，因此即使是小型的鎖定查閱逾時也可能需要幾秒鐘的時間。

過時的快取只適用於L2快取記憶體。 使用過時的快取記憶體，您可以傳送過時的快取記憶體，同時在平行程式中產生新的快取記憶體。 若要啟用過時的快取，請新增`'use_stale_cache' => true`至L2快取的頂端設定。

Adobe建議僅對從中獲益最大的快取型別啟用`use_stale_cache`選項，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe不建議為`use_stale_cache`快取型別啟用`default`選項。

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
