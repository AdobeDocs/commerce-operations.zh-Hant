---
title: env.php參考
description: 請參閱env.php檔案的值清單。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# env.php參考

該檔案 `env.php` 包含以下部分：

| 名字 | 說明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 設定管理區域 |
| `cache` | 配置 redis 頁面和默認緩存 |
| `cache_types` | 快取儲存設定 |
| `consumers_wait_for_messages` | 設定使用者處理訊息佇列訊息的方式 |
| `cron` | 啟用或停用cron工作 |
| `crypt` | 密碼編譯功能的加密金鑰 |
| `db` | 資料庫連線設定 |
| `default_connection` | 訊息佇列預設連線 |
| `directories` | Commerce目錄對應設定 |
| `downloadable_domains` | 可下載網域的清單 |
| `install` | 安裝日期 |
| `lock` | 鎖定提供者設定 |
| `MAGE_MODE` | [應用程式模式](../bootstrap/application-modes.md) |
| `queue` | [新增訊息佇列設定](../queues/manage-message-queues.md) |
| `resource` | 資源名稱到連接的映射 |
| `session` | 會話儲存數據 |
| `system` | 停用「管理員」中要編輯的欄位 |
| `x-frame-options` | [x-frame-options][x-frame-options]的設定 |

## 後端

在 **env.php 中使用節點設定`backend`商務管理 url 的 frontName**。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 緩存

使用文件中的節點`env.php`來`cache`配置 redis 頁面和預設快取。

```conf
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
]
```

在 Redis 配置](../cache/redis-pg-cache.md)中[瞭解更多資訊。

## cache_types

所有快取型別設定都可從此節點取得。

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

深入瞭解不同的[快取型別](../cli/manage-cache.md)。

## consumers_wait_for_messages

指定當處理的訊息數目小於`max_messages`值時，消費者是否應繼續輪詢訊息。 預設值為`1`。

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

下列選項可供使用：

- `1` — 消費者繼續處理來自訊息佇列的訊息，直到達到`env.php`檔案中指定的`max_messages`值為止，然後再關閉TCP連線並終止消費者處理序。 如果佇列在達到`max_messages`值之前排空，消費者會等待更多訊息到達。

  我們建議大型商戶使用此設定，因為系統預期訊息流程會持續不變，且不希望處理延遲。

- `0` — 消費者處理佇列中的可用訊息、關閉TCP連線，然後終止。 即使已處理的訊息數小於`env.php`檔案中指定的`max_messages`值，消費者也不會等候其他訊息進入佇列。 這有助於防止因訊息佇列處理長時間延遲而導致cron工作發生問題。

  我們建議將此設定用於小型商家，這類商戶不希望持續傳送訊息流，且偏好節省運算資源，以換取在數天內沒有訊息時的輕微處理延遲。

## cron

啟用或停用Commerce應用程式的cron工作。 預設會啟用cron工作。 若要停用它們，請新增`cron`設定到`env.php`檔案並將值設定為`0`。

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>停用cron工作時請小心。 當這些程式碼停用時，Commerce應用程式所需的基本流程將無法執行。

深入瞭解[Crons](../cli/configure-cron-jobs.md)。

## 地穴

Commerce使用加密金鑰來保護密碼和其他敏感資料。 此金鑰會在安裝過程中產生。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

在&#x200B;_Commerce使用手冊_&#x200B;中進一步瞭解[加密金鑰](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key)。

## db

此節點提供所有資料庫組態。

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

定義訊息佇列的預設連線。 值可以是`db`、`amqp`或自訂佇列系統（如`redismq`）。 如果您指定`db`以外的任何值，則必須先安裝並設定訊息佇列軟體。 否則，訊息將無法正確處理。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

如果系統`env.php`檔案中指定了`queue/default_connection`，則此連線會用於透過系統的所有訊息佇列，除非已在`queue_topology.xml`、`queue_publisher.xml`或`queue_consumer.xml`檔案中定義特定連線。
例如，如果`queue/default_connection`在`env.php`中是`amqp`，但在模組的佇列組態XML檔案中指定了`db`連線，模組將使用MySQL做為訊息代理人。

## 目錄

當 Web 伺服器設定為從目錄提供 `/pub` Commerce 應用以提高安全性](../../installation/tutorials/docroot.md)時，需要[設置的可選目錄映射選項。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

此節點提供清單的可下載網域。 您可以使用CLI指令來新增、移除或列出其他網域。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

深入瞭解[可下載的網域](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd)。

## 安裝

Commerce 應用程式 的安裝日期。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 鎖

鎖定提供程序設置是使用 `lock` 節點配置的。

詳細了解 [鎖定提供程式配置](../../installation/tutorials/lock-provider.md)。

## MAGE_MODE

可在此節點中設定部署模式。

```conf
'MAGE_MODE' => 'developer'
```

深入瞭解[應用程式模式](../cli/set-mode.md)。

## 佇列

此節點提供訊息佇列設定。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

深入瞭解[訊息佇列][message-queue]。

## resource

資源組態設定可在此節點中使用。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

工作階段設定儲存在`session`節點中。

```conf
'session' => [
  'save' => 'files'
],
```

深入瞭解[工作階段](../storage/sessions.md)。

## x-frame-options

x-frame-options 標頭可使用此節點進行設定。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

了解有關 x-frame-options](../security/xframe-options.md) 的更多資訊[。

## 系統

使用此節點，Commerce會鎖定`env.php`檔案中的設定值，然後停用管理員中的欄位。

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

深入瞭解[env-php-config-set](../cli/set-configuration-values.md)。

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
