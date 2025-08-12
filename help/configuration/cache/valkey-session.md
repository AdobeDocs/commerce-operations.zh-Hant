---
title: 使用Valkey進行工作階段儲存
description: 瞭解如何設定工作階段存放區的Valkey。
feature: Configuration, Cache
exl-id: 986ddb5c-8fc5-4210-8a41-a29e3a7625b7
source-git-commit: bc0274074c0254f649af2f9e2b288017ac82ce9b
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---


# 使用Valkey進行工作階段儲存

>[!IMPORTANT]
>
>您必須[安裝Valkey](config-valkey.md#install-valkey)，才能繼續。

Adobe Commerce提供命令列選項，用於設定Valkey工作階段存放區。

執行`setup:config:set`命令並指定Valkey特定引數。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey`啟用Valkey工作階段存放區。 如果已啟用此功能，請忽略此引數。

- `--session-save-valkey-<parameter_name>=<parameter_value>`是設定工作階段存放區的引數/值配對清單：

| 命令列引數 | 引數名稱 | 含義 | 預設值 |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | 主機 | 完整的主機名稱、IP位址或絕對路徑（若使用UNIX通訊端）。 | localhost |
| session-save-valkey-port | 連線埠 | Valkey伺服器接聽連線埠。 | 6379 |
| session-save-valkey-password | 密碼 | 如果Valkey伺服器需要驗證，請指定密碼。 | 空白 |
| session-save-valkey-timeout | 逾時 | 連線逾時（秒）。 | 2.5 |
| session-save-valkey-persistent-id | persistent_identifier | 啟用持續連線的唯一字串（例如，sess-db0）。<br>[phpredis和php-fpm的已知問題](https://github.com/phpredis/phpredis/issues/70)。 |
| session-save-valkey-db | 資料庫 | 唯一的Valkey資料庫編號，建議用來防止資料遺失。<br><br>**重要**：如果您將Valkey用於多種快取型別，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派給`0`，將分頁快取資料庫編號指派給`1`，並將工作階段儲存資料庫編號指派給`2`。 | 0 |
| session-save-valkey-compression-threshold | compression_threshold | 設定為`0`以停用壓縮（建議在`suhosin.session.encrypt = On`時使用）。 | 2048 |
| session-save-valkey-compression-lib | compression_library | 選項： gzip、lzf、lz4或snappy。 | gzip |
| session-save-valkey-log-level | log_level | 設為下列任一項，依從少到多的順序列出：<ul><li>0 （緊急：只有最嚴重的錯誤）<li>1 （警示：需要立即動作）<li>2 （嚴重：應用程式元件無法使用）<li>3 （錯誤：執行階段錯誤，非嚴重，但必須監視）<li>4 （警告：其他資訊，建議）<li>5 （注意：正常但重要的情況）<li>6 （資訊：資訊訊息）<li>7 （除錯：僅供開發或測試使用的最多資訊）</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | 可等候鎖定一個工作階段的最大處理序數目。 對於大型生產叢集，請將此項設定為至少PHP流程數的10%。 | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | 嘗試解除前端（亦即storefront）工作階段鎖定之前等待的秒數。 | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | 嘗試中斷Admin HTML （即管理員）工作階段鎖定之前的等待秒數。 | 30 |
| session-save-valkey-first-lifetime | first_lifetime | 非機器人第一次寫入工作階段的期限（以秒為單位），或使用`0`加以停用。 | 600 |
| session-save-valkey-bot-first-lifetime | bot_first_lifetime | 機器人第一次寫入工作階段的存留期（以秒為單位），或使用`0`加以停用。 | 60 |
| session-save-valkey-bot-lifetime | bot_lifetime | 後續寫入的機器人工作階段存留期（以秒為單位），或使用`0`加以停用。 | 7200 |
| session-save-valkey-disable-locking | disable_locking | 完全停用工作階段鎖定。 | 0 (false) |
| session-save-valkey-min-lifetime | min_lifetime | 工作階段存留期下限（以秒為單位）。 | 60 |
| session-save-valkey-max-lifetime | max_lifetime | 最長工作階段存留期（以秒為單位）。 | 2592000 （720小時） |
| session-save-valkey-sentinel-master | sentinel_master | Valkey Sentinel主名稱。 | 空白 |
| session-save-valkey-sentinel-servers | sentinel_servers | Valkey Sentinel伺服器清單（以逗號分隔）。 | 空白 |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | 驗證Valkey Sentinel主要狀態旗標。 | 0 (false) |
| session-save-valkey-sentinel-connect-retries | sentinel_connect_retries | Sentinels的連線重試。 | 5 |

## 範例

下列範例將Valkey設為工作階段資料存放區，將主機設為`127.0.0.1`，將記錄層級設為`4`，並將資料庫編號設為`2`。 所有其他引數都會設定為預設值。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

### 結果

Commerce將類似下列的行新增至`<magento_root>app/etc/env.php`：

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>工作階段記錄的TTL使用Cookie期限的值，此值是在管理員中設定。 如果Cookie期限設定為`0` （預設為`3600`），則Valkey工作階段會在min_lifetime中指定的秒數內到期（預設為`60`）。 此差異是因為Valkey和工作階段Cookie解譯期限值`0`的方式有所差異。 如果不希望出現這種行為，請增加min_lifetime的值。

## 驗證Valkey連線

若要確認Valkey和Commerce是否正常運作，請登入Valkey執行所在的伺服器、開啟終端機，然後使用`valkey-cli monitor`命令或`redis-cli ping`命令。

### Valkey monitor命令

```bash
valkey-cli monitor
```

工作階段儲存輸出範例：

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Valkey ping命令

```bash
valkey-cli ping
```

預期的回應是： `PONG`。

如果兩個命令都成功，就會正確設定Valkey。

### 檢查壓縮資料

為了檢查壓縮的工作階段資料和頁面快取，[RESP.app](https://flathub.org/apps/app.resp.RESP)支援自動解壓縮Commerce 2工作階段和頁面快取，並以人類可讀的格式顯示PHP工作階段資料。
