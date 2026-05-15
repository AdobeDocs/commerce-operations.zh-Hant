---
title: 安裝及設定Valkey
description: 瞭解如何使用Adobe Commerce安裝和設定Valkey以快取和工作階段儲存。 探索最佳化和效能調整的選項。
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# 安裝及設定Valkey

Valkey是開放原始碼、與Redis相容的記憶體內部資料存放區，可作為快取後端及工作階段存放區使用。 主要功能包括：

- PHP工作階段儲存
- 標籤式快取清除，不含`foreach`回圈
- 磁碟上儲存和主/從復寫

## 安裝Valkey

若要安裝及設定Valkey軟體，請參閱下列資源：

- [下載Valkey頁面](https://valkey.io/download/){target="_blank"}
- [Valkey快速入門](https://valkey.io/topics/quickstart/){target="_blank"}
- [Valkey檔案頁面](https://valkey.io/docs){target="_blank"}

## 設定值鍵組態

視您的安裝而定，您通常可以在`/etc/valkey/valkey.conf`檔案或`/etc/valkey/<port>.conf`檔案中找到您的Valkey組態。

若要針對您的需求最佳化Valkey執行個體，請為每個工作階段使用專屬的執行個體、Commerce快取和FPC，以獲得最佳結果。

Adobe建議對工作階段啟用持續性，以便將Valkey資料複製到磁碟。 您可以使用Valkey Database Backup (RDB)快照或僅附加檔案(AOF)持續性記錄檔。

- **RDB** （Valkey資料庫）快照在指定時間後，將完整的資料庫儲存在傾印檔案中，而自上次儲存後的最小金鑰數目已變更。 使用`valkey.conf`檔案內的`save`設定來設定此設定。

- **僅附加檔案** (AOF)會將每個傳送給Valkey的寫入作業儲存在日誌檔中。 Valkey只會在重新啟動時讀取此檔案，並使用它來還原原始資料集。

您也可以同時啟用RDB和AOF選項。 如需其他詳細資訊，包括持續性選項的優缺點，請參閱[Valkey持續性檔案](https://valkey.io/topics/persistence/)。

對於快取執行個體，請設定執行個體，使其足以儲存整個Commerce快取。 大小需求取決於不同的因素，例如產品數量和商店檢視。 首先，您可以使用檔案系統上快取資料夾的大小。 例如，如果檔案系統上的`var/cache`資料夾為5 GB，請將Valkey執行個體設定為至少5 GB才能啟動。 快取執行個體不需要持續性，因為Commerce快取可以復原。

如需進行效能調整，您可以啟用下列非同步刪除的設定。 這些設定不會變更Valkey的行為。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
