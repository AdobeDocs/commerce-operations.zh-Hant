---
title: env.php參考
description: 請參閱env.php檔案的值清單。
source-git-commit: fe5e16d44213d1864a62230029e9e206eecd1717
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# env.php參考

此 `env.php` 檔案包含下列章節：

| 名稱 | 說明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理區域的設定 |
| `cache` | 配置密文頁和預設快取 |
| `cache_types` | 快取儲存設定 |
| `consumers_wait_for_messages` | 配置使用者處理來自訊息佇列的訊息的方式 |
| `cron` | 啟用或停用cron作業 |
| `crypt` | 加密函式的加密密鑰 |
| `db` | 資料庫連接設定 |
| `default_connection` | 消息隊列預設連接 |
| `directories` | 商務目錄映射設定 |
| `downloadable_domains` | 可下載網域清單 |
| `install` | 安裝日期 |
| `lock` | 鎖定提供程式設定 |
| `MAGE_MODE` | 此 [應用程式模式](../bootstrap/application-modes.md) |
| `queue` | [消息隊列](../queues/manage-message-queues.md) 設定 |
| `resource` | 將資源名稱映射到連接 |
| `session` | 會話儲存資料 |
| `system` | 停用管理員中的編輯欄位 |
| `x-frame-options` | 設定 [x-frame-options][x-frame-options] |

## 後端

設定 **frontName** (使用 `backend` env.php中的節點。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 快取

使用配置密文頁面和預設快取 `cache` 節點 `env.php` 檔案。

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

深入了解 [Redis配置](../cache/redis-pg-cache.md).

## cache_types

所有快取類型配置都可從此節點獲得。

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

深入了解不同 [快取類型](../cli/manage-cache.md).

## consumers_wait_for_messages

指定如果已處理的訊息數小於 `max_messages` 值。 預設值為 `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

可使用下列選項：

- `1` — 消費者會繼續處理來自訊息佇列的訊息，直到到達 `max_messages` 在中指定的值 `env.php` 檔案，然後關閉TCP連接並終止使用者進程。 如果佇列在到達 `max_messages` 值，則使用者會等待更多訊息送達。

   我們建議大型商戶使用此設定，因為預期會有持續的訊息流，且處理延遲不會受到歡迎。

- `0` — 消費者處理隊列中的可用消息、關閉TCP連接並終止。 即使已處理的訊息數量小於 `max_messages` 在中指定的值 `env.php` 檔案。 這有助於防止因訊息佇列處理延遲過長而導致cron作業問題。

   我們建議針對不期望訊息流持續且偏好保留運算資源的較小商戶使用此設定，以換取在數天內無訊息時，處理延遲較小的情況。

## cron

啟用或停用商務應用程式的cron作業。 預設會啟用cron作業。 若要停用，請新增 `cron` 設定 `env.php` 檔案，並將值設為 `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>禁用cron作業時請小心。 禁用時，將不運行商務應用程式所需的基本進程。

深入了解 [克龍](../cli/configure-cron-jobs.md).

## 加密

商務使用加密密鑰來保護密碼和其他敏感資料。 此金鑰會在安裝程式期間產生。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

深入了解 [加密密鑰](https://docs.magento.com/user-guide/system/encryption-key.html) 在 _商務使用手冊_.

## db

此節點中提供所有資料庫配置。

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

定義消息隊列的預設連接。 值可以是 `db`, `amqp`，或自訂佇列系統，例如 `redismq`. 如果您指定 `db`，必須先安裝並配置消息隊列軟體。 否則，訊息將無法正確處理。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

若 `queue/default_connection` 在系統中指定 `env.php` 檔案中，此連接用於通過系統的所有消息隊列，除非在中定義了特定連接 `queue_topology.xml`, `queue_publisher.xml` 或 `queue_consumer.xml` 檔案。
例如，若 `queue/default_connection` is `amqp` in `env.php` 但 `db` 在模組的隊列配置XML檔案中指定連接，該模組將使用MySQL作為消息代理。

## 目錄

當Web伺服器配置為從 `/pub` 目錄 [改善安全性](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## 可下載的網域

此節點中可用的可下載網域清單。 可以使用CLI命令添加、刪除或列出其他域。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

深入了解 [可下載的網域](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## 安裝

商務應用程式的安裝日期。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 鎖

使用 `lock` 節點。

深入了解 [鎖定提供程式配置](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

可以在此節點中配置部署模式。

```conf
'MAGE_MODE' => 'developer'
```

深入了解 [應用程式模式](../cli/set-mode.md).

## 佇列

此節點中提供消息隊列配置。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

深入了解 [訊息佇列][message-queue].

## 資源

此節點中提供資源配置設定。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## 工作階段

工作階段設定會儲存在 `session` 節點。

```conf
'session' => [
  'save' => 'files'
],
```

深入了解 [工作階段](../storage/sessions.md).

## x-frame-options

可使用此節點配置x-frame-options標頭。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

深入了解 [x-frame-options](../security/xframe-options.md).

## 系統

使用此節點，商務會鎖定 `env.php` 檔案，然後停用「管理員」中的欄位。

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

深入了解 [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
