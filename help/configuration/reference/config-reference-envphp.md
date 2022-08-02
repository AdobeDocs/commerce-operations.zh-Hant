---
title: env.php引用
description: 請參見env.php檔案的值清單。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# env.php引用

的 `env.php` 檔案包含以下部分：

| 名稱 | 說明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理區的設定 |
| `cache` | 配置密文頁和預設快取 |
| `cache_types` | 快取儲存設定 |
| `consumers_wait_for_messages` | 配置使用者處理來自消息隊列的消息的方式 |
| `cron` | 啟用或禁用cron作業 |
| `crypt` | 加密函式的加密密鑰 |
| `db` | 資料庫連接設定 |
| `directories` | 商業目錄映射設定 |
| `downloadable_domains` | 可下載域清單 |
| `install` | 安裝日期 |
| `lock` | 鎖定提供程式設定 |
| `MAGE_MODE` | 的 [應用模式](../bootstrap/application-modes.md) |
| `queue` | [消息隊列](../queues/manage-message-queues.md) 設定 |
| `resource` | 資源名稱到連接的映射 |
| `session` | 會話儲存資料 |
| `system` | 禁用管理員中的編輯欄位 |
| `x-frame-options` | 設定 [x幀選項][x-frame-options] |

## 後端

配置 **前名** 使用 `backend` env.php中的節點。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 快取

使用 `cache` 中的 `env.php` 的子菜單。

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

瞭解詳情 [Redis配置](../cache/redis-pg-cache.md)。

## 快取類型

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

瞭解有關不同的詳細資訊 [快取類型](../cli/manage-cache.md)。

## conduser_wait_for_messages

指定如果已處理的消息數小於 `max_messages` 值。 預設值為 `1`。

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

以下選項可用：

- `1` — 使用者繼續處理來自消息隊列的消息，直到到達 `max_messages` 值 `env.php` 關閉TCP連接並終止使用者進程之前的檔案。 如果隊列在到達前空 `max_messages` 值，用戶等待更多消息到達。

   我們建議對大型商戶進行此設定，因為預期會有恆定的消息流，且處理延遲是不可取的。

- `0` — 使用者處理隊列中的可用消息，關閉TCP連接，然後終止。 即使已處理的消息數小於 `max_messages` 值 `env.php` 的子菜單。 這有助於防止由於消息隊列處理中的長時間延遲而導致的cron作業問題。

   我們建議將此設定用於較小的商家，這些商家不期望消息流保持恆定，並希望保存計算資源，以換取在數天內沒有消息時出現微小的處理延遲。

## 克隆

啟用或禁用Commerce應用程式的cron作業。 預設情況下，啟用cron作業。 要禁用它們，請添加 `cron` 配置 `env.php` 檔案並將值設定為 `0`。

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>禁用cron作業時要小心。 禁用它們後，Commerce應用程式所需的基本進程將不運行。

瞭解有關 [克龍](../cli/configure-cron-jobs.md)。

## 冷凍

Commerce使用加密密鑰來保護密碼和其他敏感資料。 此密鑰在安裝過程中生成。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

瞭解有關 [加密密鑰](https://docs.magento.com/user-guide/system/encryption-key.html) 的 _《 Commerce使用手冊》_。

## 資料庫

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

## 目錄

當Web伺服器配置為從中為Commerce應用服務時，需要設定的可選目錄映射選項 `/pub` 目錄 [提高安全性][change-docroot-to-pub]。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## 可下載域

此節點中可用的可下載域的清單。 可以使用CLI命令添加、刪除或列出其他域。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

瞭解有關 [可下載的域](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd)。

## 安裝

Commerce應用程式的安裝日期。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 鎖

使用 `lock` 的下界。

瞭解有關 [鎖定提供程式配置][lock-provider-config]。

## 影像模式

可以在此節點中配置部署模式。

```conf
'MAGE_MODE' => 'developer'
```

瞭解有關 [應用模式](../cli/set-mode.md)。

## 隊列

消息隊列配置在此節點中可用。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

瞭解有關 [消息隊列][message-queue]。

## 資源

資源配置設定在此節點中可用。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## 會話

會話配置儲存在 `session` 的下界。

```conf
'session' => [
  'save' => 'files'
],
```

瞭解有關 [會話](../storage/sessions.md)。

## x幀選項

可使用此節點配置x幀選項頭。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

瞭解有關 [x幀選項](../security/xframe-options.md)。

## 系統

使用此節點，Commerce將鎖定 `env.php` 檔案，然後禁用管理中的欄位。

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

瞭解詳情 [env-php-config集](../cli/set-configuration-values.md)。

<!-- Link definitions -->

[change-docroot-to-pub]: https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html
[encryption-key]: https://docs.magento.com/user-guide/system/encryption-key.html
[lock-provider-config]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-lock.html
[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
