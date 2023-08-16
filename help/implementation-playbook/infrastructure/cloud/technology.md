---
title: 雲端基礎結構技術
description: 進一步瞭解我們在雲端基礎結構上用於Adobe Commerce的技術集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 技術

如我們先前所述，Adobe Commerce運用許多軟體解決方案來支援該平台。 具體來說，與生產環境相關，我們已在雲端基礎結構上細分Adobe Commerce中包含的一些技術解決方案和功能，這些解決方案和功能有助於充分利用您的生產環境。

![圖表顯示雲端基礎結構技術上的Adobe Commerce](../../../assets/playbooks/infrastructure-technology.svg)

## 軟體解決方案

- **Nginx** — 使用PHP-FPM的網頁伺服器。 有一個執行個體具有多個背景工作程式。

- **GlusterFS** — 用來管理所有靜態檔案部署及與四個目錄掛載同步化的檔案伺服器：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** — 每個VM一台伺服器，只有一個作用中，另外兩台作為復本。

- **Elasticsearch** — 搜尋Adobe Commerce 2.2.x版和更新版本。

- **OpenSearch** — 搜尋Adobe Commerce 2.4.6版和更新版本。

- **加萊拉** — 資料庫叢集，每個節點有一個MariaDB MySQL資料庫，每個資料庫的唯一ID自動增加設定為三。

## 功能和優點

- 在VPC中有三個專用執行個體，在三個獨立的可用區或資料中心間有一個彈性負載平衡器。

- 針對可能導致單一執行個體失敗的事件，提供更高的恢復能力。 例如，整個AWS可用區域或資料中心發生中斷。

- 在15分鐘內即可將零停機時間擴充至整個棧疊，包括Web、快取、搜尋和資料庫。
