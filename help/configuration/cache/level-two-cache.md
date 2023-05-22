---
title: 二級快取配置
description: 瞭解配置L2快取。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# 二級快取配置

快取使遠程快取儲存和Commerce應用程式之間的網路流量減少。 標準Commerce實例每個請求傳輸約300 kb，在某些情況下，流量可能會迅速增長到超過1000個請求。

要減少Redis的網路頻寬，請將快取資料本地儲存在每個Web節點上，並使用遠程快取用於以下兩個目的：

- 檢查快取資料版本並確保本地儲存最新快取
- 將最新的快取從遠程電腦傳輸到本地電腦

Commerce在Redis中儲存散列資料版本，並在常規鍵後附加尾碼「：hash」。 如果存在過時的本地快取，則使用快取適配器將資料傳輸到本地電腦。

>[!INFO]
>
>對於Adobe Commerce的雲基礎架構，您可以 [部署變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) L2快取配置。

## 配置示例

使用以下示例修改或替換 `app/etc/env.php` 的子菜單。

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

位置：

- `backend` 是L2快取實現。
- `backend_options` 是L2快取配置。
   - `remote_backend` 是遠程快取實現：Redis或MySQL。
   - `remote_backend_options` 是遠程快取配置。
   - `local_backend` 是本地快取實現： `Cm_Cache_Backend_File`
   - `local_backend_options` 是本地快取配置。
      - `cache_dir` 是儲存本地快取的目錄的檔案快取特定選項。
   - `use_stale_cache` 是啟用或禁用陳舊快取的標誌。

Adobe建議使用Redis進行遠程快取(`\Magento\Framework\Cache\Backend\Redis`) `Cm_Cache_Backend_File` 用於共用記憶體中資料的本地快取，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe建議使用 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 因為它顯著地降低了雷迪斯的壓力。 不要忘記為預載入鍵添加尾碼「：hash」。

## 過時的快取選項

開始於 [!DNL Commerce] 2.4, `use_stale_cache` 選項可以在某些特定情況下提高效能。

通常，從效能方面來說，等待鎖定的取捨是可接受的，但商家擁有的塊或快取數量越大，等待鎖定所花費的時間就越多。 在某些情況下，您可以 **鍵數** \* **查找超時** 進程的時間。 在一些罕見的情況下，商戶可以在 `Block/Config` 快取，因此即使鎖的查找超時很小，也可能需要幾秒。

陳舊快取只能與L2快取一起使用。 如果快取過時，您可以發送過時的快取，而新快取正在並行進程中生成。 要啟用過時的快取，請添加 `'use_stale_cache' => true` 到L2快取的頂部配置。

Adobe建議啟用 `use_stale_cache` 選項，僅適用於從中獲益最多的快取類型，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

以下代碼顯示了一個配置示例：

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
