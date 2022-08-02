---
title: 將Redis用於會話儲存
description: 瞭解如何為會話儲存配置Redis。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 1%

---


# 將Redis用於會話儲存

>[!IMPORTANT]
>
>你必須 [安裝Redis](config-redis.md#install-redis) 再繼續。


Commerce現在提供命令行選項來配置Redis會話儲存。 在以前版本中，您編輯了 `<Commerce install dir>app/etc/env.php` 的子菜單。 命令行提供驗證，是推薦的配置方法，但您仍然可以編輯 `env.php` 的子菜單。

運行 `setup:config:set` 命令並指定特定於Redis的參數。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

何處

`--session-save=redis` 啟用Redis會話儲存。 如果此功能已啟用，請忽略此參數。

`--session-save-redis-<parameter_name>=<parameter_value>` 是配置會話儲存的參數/值對的清單：

| 命令行參數 | 參數名稱 | 意義 | 預設值 |
|--- |--- |--- |--- |
| 會話保存 — redis-host | 主機 | 完全限定的主機名、 IP地址或絕對路徑（如果使用UNIX套接字）。 | 本地主機 |
| 會話保存 — 密碼埠 | 埠 | Redis伺服器偵聽埠。 | 6379 |
| 會話保存密碼 | 密碼 | 如果Redis伺服器需要驗證，則指定密碼。 | 空 |
| 會話save-redis-timeout | 超時 | 連接超時（秒）。 | 2.5 |
| 會話save-redis-persistent-id | persistent_identifier | 用於啟用永久連接的唯一字串（例如sess-db0）。<br>[phpredis和php-fpm的已知問題](https://github.com/phpredis/phpredis/issues/70)。 |
| session-save-redis-db | 資料庫 | 唯一的Redis資料庫編號，建議使用此編號來防止資料丟失。<br><br>**重要**:如果將Redis用於多種類型的快取，則資料庫編號必須不同。 建議將預設的快取資料庫編號分配給0，將頁快取資料庫編號分配給1，將會話儲存資料庫編號分配給2。 | 0 |
| 會話保存 — Redis壓縮閾值 | 壓縮閾值 | 設定為0以禁用壓縮(建議在 [suhosin.session.encrypt =開啟](https://suhosin.org/stories/howtos.html))。<br>[超過64 KB的字串的已知問題](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18)。 | 2048 |
| session save-redis-compression-lib | 壓縮庫 | 選項：gzip、lzf、lz4或snappy。 | gzip |
| 會話保存 — redis-log級 | 日誌級別 | 設定為以下任一項，按從最少詳細到最詳細的順序列出：<ul><li>0(緊急：只有最嚴重的錯誤)<li>1(警報：需要立即操作)<li>2(關鍵：應用程式元件不可用)<li>3(錯誤：運行時錯誤，非關鍵，但必須監視)<li>4(警告：其他資訊，建議)<li>5(通知：正常但重要的條件)<li>6(資訊：資訊消息)<li>7（調試）僅用於開發或測試的最多資訊)</ul> | 1 |
| 會話保存 — redis-max-concurrency | 最大併發 | 可等待一個會話上鎖定的進程的最大數量。 對於大型生產群集，將此值至少設定為PHP進程數的10%。 | 6 |
| 會話保存 — Redis-Break-after-Frontend | break_after_frontend | 嘗試斷開前端（即店面）會話的鎖之前等待的秒數。 | 5 |
| session save-redis-break-after-adminhtml | break_after_adminhtml | 嘗試為adminhtml（即Admin）會話斷開鎖定之前等待的秒數。 | 30 |
| 會話保存 — Redis第一生命期 | 第一個生命期 | 第一次寫入時非bot的會話的生存時間（秒），或使用0禁用。 | 600 |
| session save-redis-bot-first-lifetime | bot_first_lifetime | 第一次寫入時bot的會話的生存時間（秒），或使用0禁用。 | 60 |
| 會話保存 — redis-bot-lifetime | bot_lifetime | 在後續寫入時bot的會話生存期（以秒為單位），或使用0禁用。 | 7200 |
| 會話保存 — 密文 — 禁用 — 鎖定 | 禁用鎖定 | 完全禁用會話鎖定。 | 0（假） |
| 會話保存 — redis-min-lifetime | 最小生存時間 | 最小會話生存時間（秒）。 | 60 |
| session save-redis-max-lifetime | 最大生存時間 | 最大會話生存時間（秒）。 | 2592000（720小時） |
| session save-redis-sentinel-master | sentilel_master | Redis Sentinel主名稱 | 空 |
| session save-redis-sentinel-servers | sentinel伺服器 | Redis Sentinel伺服器清單，逗號分隔 | 空 |
| session save-redis-sentinel-verify-master | sentinel_verify_master | 驗證Redis Sentinel主狀態標誌 | 0（假） |
| session save-redis-sentinel-connect-retries | sentinel_connect_retries | Sentinel的連接重試次數 | 5 |

## 示例

以下示例將Redis設定為會話資料儲存，將主機設定為 `127.0.0.1`，將日誌級別設定為4，並將資料庫編號設定為2。 所有其它參數都設定為預設值。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 結果

Commerce將類似於以下的行添加到 `<magento_root>app/etc/env.php`:

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>會話記錄的TTL使用Cookie生存期的值，該值在Admin中配置。 如果Cookie生存期設定為0（預設值為3600），則Redis會話將以min_lifetime中指定的秒數（預設值為60）過期。 此差異是由於Redis和會話Cookie在解釋0的生存期值時的方式不同。 如果不需要該行為，請增加min_lifetime的值。

## 驗證Redis連接

要驗證Redis和Commerce是否協同工作，請登錄到運行Redis的伺服器，開啟終端，然後使用Redis監視器命令或ping命令。

### Redis監視器命令

```bash
redis-cli monitor
```

會話儲存輸出示例：

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis ping命令

```bash
redis-cli ping
```

`PONG` 應該是回應。

如果兩個命令都成功，則正確設定Redis。

### 檢查壓縮資料

要檢查壓縮的會話資料和頁快取， [RESP應用](https://flathub.org/apps/details/app.resp.RESP) 支援Commerce 2會話和頁面快取的自動解壓縮，並以人可讀的形式顯示PHP會話資料。

