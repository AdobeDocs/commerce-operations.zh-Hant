---
title: 雲基礎架構技術
description: 進一步了解我們在雲端基礎架構上用於Adobe Commerce的技術集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: 683ce0a72aca0319ade2e4ccfd7a8e541a228156
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 技術

如前所述，Adobe Commerce利用多種軟體解決方案來支援該平台。 具體來說，就生產而言，我們已劃分了Adobe Commerce雲端基礎架構中包含的部分技術解決方案和功能，這些解決方案和功能可協助您充分利用生產環境。

![關於雲基礎架構技術的Adobe Commerce圖表](../../../assets/playbooks/infrastructure-technology.svg)

## 軟體解決方案

- **Nginx** — 使用PHP-FPM的Web伺服器。 有一個例項包含多個背景工作。

- **GlusterFS** — 用於管理所有靜態檔案部署和與四個目錄裝載同步的檔案伺服器：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **雷迪斯** — 每個VM一個伺服器，其中只有一個活動，另兩個作為副本。

- **Elasticsearch** — 搜尋Adobe Commerce 2.2.x版和更新版本。

- **OpenSearch** — 搜尋Adobe Commerce 2.4.6版和更新版本。

- **加萊拉** — 資料庫群集，每個節點一個MariaDB MySQL資料庫，每個資料庫的唯一ID自動增量設定為3。

## 功能與優點

- VPC中有三個專用實例，在三個獨立的可用區或資料中心之間有一個彈性負載平衡器。

- 針對可能導致單個執行個體失敗的事件提供更高的可復原性。 例如，整個AWS可用區或資料中心停機。

- 在不到15分鐘內，整個堆棧（包括Web、快取、搜索和資料庫）的零停機擴展。
