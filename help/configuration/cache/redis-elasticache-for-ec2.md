---
title: 使用AWS ElastiCache設定Redis
description: 針對在EC2上託管的Commerce例項，瞭解如何使用AWS ElastiCache來取代本機Redis例項。 探索命令列設定、設定選項和驗證技術。
feature: Configuration, Cache
source-git-commit: 908796587e78b80d699354c0506ca948d0f37518
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# 使用AWS ElastiCache設定Redis

自Commerce 2.4.3起，Amazon EC2上代管的執行個體可能會使用AWS ElastiCache來取代本機Redis執行個體。

>[!WARNING]
>
>本節僅適用於在Amazon EC2 VPC上執行的Commerce執行個體。 它不適用於內部部署安裝。

## 先決條件

- **建立Redis OSS無伺服器快取** — 從AWS管理主控台，在EC2執行個體的相同區域和VPC中建立Redis快取。 如需指示，請參閱[AWS Elasticache檔案]&#x200B;(https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html)。

- **驗證與您的EC2 Commerce執行個體的連線**

   - 開啟與EC2執行個體的SSH連線
   - 在EC2執行個體上，安裝Redis使用者端：

     ```bash
     sudo apt-get install redis
     ```

   - 將輸入規則新增至EC2安全性群組：型別`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 將輸入規則新增至ElastiCache叢集安全性群組：型別`- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 連線至Redis CLI：

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### 設定Commerce以使用叢集

Commerce支援多種型別的快取設定。 一般而言，快取設定會在前端和後端之間分割。 前端快取分類為`default`，用於任何快取型別。 您可以自訂或分割為較低層級的快取以取得較佳的效能。 常見的Redis組態是將預設快取和頁面快取分隔到自己的Redis資料庫(RDB)中。

執行`setup`命令以指定Redis端點。

若要設定用於Redis的Commerce作為預設快取：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

若要設定Commerce以進行Redis頁面快取：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

若要設定Commerce以使用Redis進行工作階段儲存：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## 驗證連線能力

**若要確認Commerce正在與ElastiCache通訊**：

1. 開啟與Commerce EC2執行個體的SSH連線。
1. 啟動Redis監視器。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. 在Commerce UI中開啟頁面。
1. 驗證您終端機中的[快取輸出](#verify-the-redis-connection)。
