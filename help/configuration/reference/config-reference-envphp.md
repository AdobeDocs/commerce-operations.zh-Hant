---
title: env.php參考
description: 請參閱env.php檔案的值清單。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 26fac37405ad635f297b65415517451d5149e50f
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 0%

---

# env.php參考

`env.php`檔案包含下列區段：

| 名稱 | 說明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理區域的設定 |
| `cache` | 設定Redis頁面和預設快取 |
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
| `queue` | [訊息佇列](../queues/manage-message-queues.md)設定 |
| `resource` | 將資源名稱對應到連線 |
| `session` | 工作階段儲存資料 |
| `system` | 停用「管理員」中要編輯的欄位 |
| `x-frame-options` | [x-frame-options][x-frame-options]的設定 |

## 後端

使用env.php中的&#x200B;**節點設定Commerce管理員URL的** frontName`backend`。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 快取

使用`cache`檔案中的`env.php`節點，設定redis頁面和預設快取。

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

深入瞭解[Redis組態](../cache/redis-pg-cache.md)。

## cache_type

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

- `1` — 消費者繼續處理來自訊息佇列的訊息，直到達到`max_messages`檔案中指定的`env.php`值為止，然後再關閉TCP連線並終止消費者處理序。 如果佇列在達到`max_messages`值之前排空，消費者會等待更多訊息到達。

  我們建議大型商戶使用此設定，因為系統預期訊息流程會持續不變，且不希望處理延遲。

- `0` — 消費者處理佇列中的可用訊息、關閉TCP連線，然後終止。 即使已處理的訊息數小於`max_messages`檔案中指定的`env.php`值，消費者也不會等候其他訊息進入佇列。 這有助於防止因訊息佇列處理長時間延遲而導致cron工作發生問題。

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

## 加密

Commerce使用加密金鑰來保護密碼和其他敏感資料。 此金鑰會在安裝過程中產生。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

在[Commerce使用手冊](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/encryption-key)中進一步瞭解&#x200B;_加密金鑰_。

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

如果系統`queue/default_connection`檔案中指定了`env.php`，則此連線會用於透過系統的所有訊息佇列，除非已在`queue_topology.xml`、`queue_publisher.xml`或`queue_consumer.xml`檔案中定義特定連線。
例如，如果`queue/default_connection`在`amqp`中是`env.php`，但在模組的佇列組態XML檔案中指定了`db`連線，模組將使用MySQL做為訊息代理人。

## 目錄

當網頁伺服器設定為從`/pub`目錄提供Commerce應用程式時，需要設定選擇性目錄對應選項，以提高[安全性](../../installation/tutorials/docroot.md)。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domain

此節點中可用的可下載網域清單。 您可以使用CLI指令來新增、移除或列出其他網域。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

深入瞭解[可下載的網域](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd)。

## 安裝

Commerce應用程式的安裝日期。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 鎖定

使用`lock`節點設定鎖定提供者設定。

深入瞭解[鎖定提供者組態](../../installation/tutorials/lock-provider.md)。

## 影像模式

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

x-frame-options標頭可使用此節點進行設定。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

深入瞭解[x-frame-options](../security/xframe-options.md)。

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


## 將變數新增至檔案設定

您可以使用作業系統(OS)層級的環境變數來設定或覆寫每個組態選項（具有值的變數）。

`env.php`設定儲存在具有巢狀層級的陣列中。 若要將巢狀陣列路徑轉換成OS環境變數的字串，請將路徑中的每個索引鍵串連為雙底線字元`__`、大寫及首碼為`MAGENTO_DC_`。

例如，我們將工作階段儲存處理常式從`env.php`設定轉換為作業系統環境變數。

```conf
'session' => [
  'save' => 'files'
],
```

與`__`串連，且大寫金鑰將變成`SESSION__SAVE`。

接著，我們會使用`MAGENTO_DC_`加上前置詞，以取得產生的OS環境變數名稱`MAGENTO_DC_SESSION__SAVE`。

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

另一個範例，讓我們轉換純量`env.php`組態選項路徑。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>雖然變數名稱應大寫，但值區分大小寫，並應依檔案紀錄保留。

我們只要將其大寫並加上前置詞`MAGENTO_DC_`即可接收最終的OS環境變數名稱`MAGENTO_DC_X-FRAME-OPTIONS`。

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>請注意，`env.php`內容優先順序將高於OS環境變數。

## 使用變數覆寫檔案設定

若要以OS環境變數覆寫現有的`env.php`設定選項，設定的陣列元素必須經過JSON編碼，並設定為`MAGENTO_DC__OVERRIDE` OS變數的值。

設定`MAGENTO_DC__OVERRIDE`時，Commerce架構會略過`env.php`檔案中的對應值，並直接從環境變數讀取組態。 `env.php`檔案中的值維持不變，但是被覆寫組態區段會略過。

>[!IMPORTANT]
>
>`MAGENTO_DC__OVERRIDE`變數完全略過`env.php`檔案中的指定組態區段。 此行為不同於個別`MAGENTO_DC_`變數，其優先順序低於`env.php`檔案中的值。

如果您需要覆寫多個設定選項，請在JSON編碼之前將所有選項組合在單一陣列中。

例如，讓我們覆寫下列`env.php`設定：

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

上述陣列的JSON編碼文字會是
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`。

現在，將它設定為`MAGENTO_DC__OVERRIDE`作業系統變數的值。

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>如有必要，請確定JSON編碼陣列已正確加上引號及/或逸出，以防止作業系統損毀編碼字串。