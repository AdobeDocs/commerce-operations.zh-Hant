---
title: Redis服務配置的最佳做法
description: 了解如何使用Adobe Commerce的延伸Redis快取實作，以改善快取效能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 92faa85b51a1fd5314a5906e8650b03723118ce1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Redis服務配置的最佳做法

- 使用延伸Redis快取實作，其中包括下列最佳化措施，以將對來自Adobe Commerce的每個請求執行的Redis查詢數減到最少：
   - 縮小Redis和Adobe Commerce之間的網路資料傳輸大小
   - 通過提高適配器自動確定需要載入的內容的能力，降低CPU週期的Redis消耗
   - 減少Redis寫入操作上的競爭條件
- 將Redis快取與Redis會話分開
- 壓縮Redis快取並使用 `gzip` 提高效能

## 延伸密文快取實作

更新您的設定，以使用延伸Redis快取實作 `\Magento\Framework\Cache\Backend\Redis`.

### 配置雲部署

設定 `REDIS_BACKEND` 部署變數 `.magento.env.yaml` 設定檔。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

如需詳細資訊，請參閱 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 變數說明，於 _雲端基礎架構商務指南_.

>[!NOTE]
>
> 檢查 `ece-tools` 版本，使用 `composer show magento/ece-tools` 命令。 如有必要， [更新至最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>做 _not_ 使用 [縮放架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 這會導致Redis連接錯誤。 請參閱 [Redis配置指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 在 _雲基礎架構上的商務_ 指南。

### 配置內部部署

對於Adobe Commerce內部部署，請使用 `bin/magento:setup` 命令。 如需指示，請參閱 [預設快取使用Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 將快取和會話實例分開

將Redis快取與Redis會話分開，可以單獨管理快取和會話，以防止快取問題影響會話。

1. 更新 `.magento/services.yaml` 設定檔。

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. 更新 `.magento.app.yaml` 設定檔。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 提交 [Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 更改Pro生產和測試環境上的Redis服務配置。 納入更新的 `.magento/services.yaml` 和 `.magento.app.yaml` 組態檔。

1. 驗證新實例是否正在運行，並記下埠號。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 將埠號添加到 `.magento.env.yaml` 設定檔。

   >[!NOTE]
   >`disable_locking` 必須設為 `1`.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 從 [預設資料庫](../../../configuration/cache/redis-pg-cache.md) (`db 0`)。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

在部署期間，您應會在 [建置和部署記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## 快取壓縮

請使用快取壓縮，但請注意，與用戶端效能之間有取捨。 如果有備用CPU，請啟用它。 請參閱 [使用Redi作為會話儲存](../../../configuration/cache/redis-session.md).

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 其他資訊

- [密頁快取](../../../configuration/cache/redis-pg-cache.md)
- [使用Redi作為會話儲存](../../../configuration/cache/redis-session.md)
