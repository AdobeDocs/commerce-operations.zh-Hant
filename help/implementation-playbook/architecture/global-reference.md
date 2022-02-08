---
title: Adobe Commerce全球參考體系結構
description: 利用全球參考體系結構，充分利用您的Adobe Commerce實施。
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 全局參考體系結構(GRA)

運行在多個本地市場（使用本地化貨幣、語言、媒體、共用目錄和獨特購物車）中具有多個品牌站點、希望避免實施相同功能和整合的不必要成本的企業時，「全球參考體系結構」(GRA)始終是一個不錯的選擇。

![說明體系結構中差異的成本的表](../../assets/playbooks/divergent-architecture.svg)

![表說明在體系結構中整合的成本](../../assets/playbooks/consolidated-architecture.svg)

GRA是：

- 實施方法
- 部署策略
- 流程治理模型

GRA不是：

- 產品「功能」
- 任何商務平台所獨有
- 僅用於全球業務使用案例

GRA影響：

- 代碼的傳遞方式

   - 圍繞特定用途的代碼儲存庫構建，這些儲存庫可提供不同的體驗。

- 業務系統的整合方式

   - 按品牌和/或地區整合與業務系統的連接。

- 如何開發和維護定制

   - 確保定制是集中的並特定於域的，以便所有定制工作都從整體的角度為業務完成。

- 如何啟用新市場

   - 簡化多個渠道和市場的發佈，否則將花費大量時間和金錢。
