---
title: 雲基礎架構技術
description: 進一步了解我們在雲基礎架構上用於Adobe商務的技術集合。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# 技術

如前所述，Adobe商務利用多種軟體解決方案來支援該平台。 具體來說，就生產而言，我們已劃分雲端基礎架構上Adobe商務中包含的部分技術解決方案和功能，協助您充份運用生產環境。

![顯示雲基礎架構技術Adobe商務的圖表](../../../assets/playbooks/infrastructure-technology.svg)

## 軟體解決方案

- **Nginx** — 使用PHP-FPM的Web伺服器。有一個例項包含多個背景工作。

- **GlusterFS** — 用於管理所有靜態檔案部署和與四個目錄裝載同步的檔案伺服器：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** — 每個VM一個伺服器，只有一個活動伺服器，另兩個作為副本。

- **Elasticsearch** — 搜尋Adobe商務2.2.x版和更新版本。

- **Galera** — 每個節點具有一個MariaDB MySQL資料庫的資料庫群集，每個資料庫中唯一ID的自動增量設定為3。

## 功能與優點

- VPC中有三個專用實例，在三個獨立的可用區或資料中心之間有一個彈性負載平衡器。

- 針對可能導致單個執行個體失敗的事件提供更高的可復原性。 例如，整個AWS可用區或資料中心的停機。

- 在不到15分鐘內，整個堆棧（包括Web、快取、搜索和資料庫）的零停機擴展。
