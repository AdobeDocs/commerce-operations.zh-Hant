---
title: 配置Redis
description: 取得Redis功能的概觀，然後開始您的Redis設定。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 配置Redis

密文功能包括：

- PHP會話儲存
- 標籤型快取清除，不含 `foreach` 循環
- 磁碟上儲存和主/從複製

## 安裝Redis

安裝和配置Redis軟體超出本指南的範圍。 諮詢資源，例如：

- [「下載密文」頁](https://redis.io/download)
- [雷迪斯快速入門](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [密文檔案頁面](https://redis.io/docs)

## 設定Redis配置

根據您的安裝，您通常可以在下列其中一個檔案中找到您的Redis配置： `/etc/redis/redis.conf` 或 `/etc/redis/<port>.conf`

若要根據您的需求最佳化Redis例項，請針對每個工作階段、商務快取和FPC使用專用例項，以獲得最佳結果。

對於會話，Adobe建議您使用以下任一持久性選項啟用持久性以將Redis資料複製到磁碟：常規Redis資料庫備份(RDB)快照或僅附加檔案(AOF)持久性日誌。

- **Redis資料庫備份** (RDB)快照在給定時間後（自上次保存後最少更改了鍵數）將完整資料庫儲存在轉儲檔案中。 使用 `save` 設定 `redis.conf` 檔案來配置此設定。

- **僅附加檔案** (AOF)將發送到Redis的每個寫操作儲存在日誌檔案中。 Redis僅在重新啟動時讀取此檔案，並使用它還原原始資料集。

您也可以同時啟用RDB和AOF選項。 有關持久性選項的優點和缺點的其他詳細資訊，請參見 [Redis持續性檔案](https://redis.io/topics/persistence).

對於快取實例，請設定實例，使其足夠大，可以儲存整個Commerce快取。 大小需求取決於不同的因素，例如產品數量和商店檢視次數。 作為起點，您可以使用檔案系統上的快取資料夾大小。 例如，若 `var/cache` 檔案系統上的資料夾為5 GB，請設定至少為5 GB的Redis實例以啟動。 快取實例不需要持續性，因為可以還原商務快取。 請參閱 [Redis快取指南](https://redis.io/docs/manual/eviction/).

對於效能調整，您可以啟用以下非同步刪除設定。 這些設定不會變更Redis的行為。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

在Redis 6.x及更新版本上，您也可以新增下列值：

```ini
lazyfree-lazy-user-del yes
```
