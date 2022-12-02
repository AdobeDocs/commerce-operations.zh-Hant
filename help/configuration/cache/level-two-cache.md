---
title: 二級快取配置
description: 了解如何設定二級快取。
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# 二級快取配置

快取可減少遠程快取儲存與Commerce應用程式之間的網路流量。 標準商務例項每個請求會傳輸約300 kb，而在某些情況下，流量可能會快速成長至約1000個請求。

要將網路頻寬減少到Redis，請將快取資料本地儲存在每個Web節點上，並將遠程快取用於兩個用途：

- 檢查快取資料版本，並確保將最新快取儲存在本機
- 將最新快取從遠程電腦傳輸到本地電腦

商務會將雜湊資料版本儲存在Redis中，尾碼「：hash」會附加至一般索引鍵。 如果存在過期的本地快取，則使用快取適配器將資料傳輸到本地電腦。

>[!INFO]
>
>若是雲端基礎架構上的Adobe Commerce，您可以使用 [部署變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 用於二級快取配置。

## 設定範例

使用以下示例修改或替換 `app/etc/env.php` 檔案。

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
                ],
                'use_stale_cache' => false,
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

- `backend` 是L2快取實作。
- `backend_options` 是二級快取配置。
   - `remote_backend` 是遠端快取實作：Redis或MySQL。
   - `remote_backend_options` 是遠程快取配置。
   - `local_backend` 是本機快取實作： `Cm_Cache_Backend_File`
   - `local_backend_options` 是本機快取設定。
      - `cache_dir` 是儲存本地快取的目錄的檔案快取特定選項。
   - `use_stale_cache` 是可啟用或停用陳舊快取的標幟。

Adobe建議使用Redis進行遠端快取(`\Magento\Framework\Cache\Backend\Redis`)和 `Cm_Cache_Backend_File` 對於共用記憶體中資料的本地快取，請使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe建議使用 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 功能，因為它能顯著降低Redis的壓力。 別忘了為預先載入金鑰新增尾碼「：hash」。

## 過時快取選項

開始使用 [!DNL Commerce] 2.4, `use_stale_cache` 選項在某些情況下可改善效能。

通常，從效能方面來說，等待鎖的取捨是可接受的，但商家擁有的塊或快取數量越多，等待鎖花費的時間就越多。 在某些情況下，您可以等待 **鍵數** \* **查閱逾時** 處理的時間。 在某些罕見情況下，商家可能會在 `Block/Config` 快取，因此，即使鎖的查詢逾時很小，也可能需要數秒。

過時快取只能與二級快取一起使用。 使用過時快取時，您可以傳送過時快取，而同時產生新的快取。 要啟用過時快取，請添加 `'use_stale_cache' => true` 到L2快取的頂端配置。

Adobe建議啟用 `use_stale_cache` 選項，僅適用於從中獲益最多的快取類型，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

下列程式碼顯示範例設定：

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
                ],
                'use_stale_cache' => false,
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
