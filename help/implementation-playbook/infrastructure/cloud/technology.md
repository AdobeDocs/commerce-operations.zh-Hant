---
title: 雲基礎架構技術
description: 更仔細地瞭解我們在雲基礎架構上為Adobe Commerce使用的技術的集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 技術

正如我們所提到的，Adobe Commerce利用多種軟體解決方案來支援該平台。 具體來說，在與生產相關的過程中，我們分析了Adobe Commerce雲基礎架構中包括的一些技術解決方案和功能，這些解決方案和功能有助於充分利用您的生產環境。

![顯示Adobe Commerce雲基礎架構技術的圖表](../../../assets/playbooks/infrastructure-technology.svg)

## 軟體解決方案

- **恩金** — 使用PHP-FPM的Web伺服器。 有一個實例，具有多個工作程式。

- **格盧斯特** — 檔案伺服器，用於管理所有靜態檔案部署和同步，具有四個目錄裝載：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **雷迪斯** — 每個VM有一台伺服器，只有一個活動伺服器，另兩個作為副本。

- **Elasticsearch** — 搜索Adobe Commerce2.2.x及更高版本。

- **加萊拉** — 每個節點有一個MariaDB MySQL資料庫的資料庫群集，每個資料庫上的唯一ID的自動增量設定為3。

## 功能和優勢

- VPC中有三個專用實例，跨三個獨立的可用區域或資料中心有一個彈性負載平衡器。

- 針對可能導致單個實例失敗的事件提供了更高的恢復能力。 例如，整個AWS可用區或資料中心的停機。

- 在不到15分鐘的時間內，整個堆棧（包括Web 、快取、搜索和資料庫）都實現了零停機擴展。
