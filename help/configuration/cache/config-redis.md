---
title: 配置密文
description: 獲取Redis功能的概述並啟動Redis配置。
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 配置密文

Redis的功能包括：

- PHP會話儲存
- 基於標籤的快取清除 `foreach` 環
- 磁碟上儲存和主/從複製

## 安裝Redis

安裝和配置Redis軟體超出本指南的範圍。 查詢資源，如：

- [下載Redis頁](https://redis.io/download)
- [雷迪斯快速入門](https://redis.io/docs/getting-started/)
- [數字海洋](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis文檔頁](https://redis.io/docs)

## 設定Redis配置

根據安裝情況，您通常可以在以下檔案之一中找到Redis配置： `/etc/redis/redis.conf` 或 `/etc/redis/<port>.conf`

為了根據您的要求優化Redis實例，您可以為每個會話、Commerce快取和FPC使用一個專用實例來獲得最佳結果。

對於會話，Adobe建議您啟用持久性，以便使用下列持久性選項之一將Redis資料複製到磁碟：常規Redis資料庫備份(RDB)快照或僅追加檔案(AOF)持久性日誌。

- **Redis資料庫備份** (RDB)快照在指定時間後將完整資料庫儲存在轉儲檔案中，此時自上次保存以來已更改了最少數量的密鑰。 使用 `save` 設定在 `redis.conf` 檔案以配置此設定。

- **僅追加檔案** (AOF)將發送到Redis的每個寫操作儲存在日誌檔案中。 Redis僅在重新啟動時讀取此檔案，並使用它還原原始資料集。

還可同時啟用RDB和AOF選項。 有關持久性選項的優缺點等其他詳細資訊，請參見 [Redis持久性文檔](https://redis.io/topics/persistence)。

對於快取實例，請設定該實例，使其足夠大以儲存您的整個Commerce快取。 大小要求取決於不同的因素，如產品數量和儲存視圖。 作為起點，您可以使用檔案系統上快取資料夾的大小。 例如，如果 `var/cache` 檔案系統上的資料夾為5 GB，請設定至少為5 GB的Redis實例以啟動。 快取實例不需要持久性，因為可以還原Commerce快取。 請參閱 [Redis快取指南](https://redis.io/docs/manual/eviction/)。

對於效能調整，可以啟用以下非同步刪除設定。 這些設定不會更改Redis的行為。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

在Redis 6.x及更高版本上，您還可以添加以下值：

```ini
lazyfree-lazy-user-del yes
```
