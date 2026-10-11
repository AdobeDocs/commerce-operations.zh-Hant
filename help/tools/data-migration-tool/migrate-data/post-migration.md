---
title: 資料後移轉步驟
description: 瞭解使用[!DNL Data Migration Tool]將資料從Magento 1移轉至Magento 2後需要採取哪些步驟。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%
---
# 資料後移轉步驟

完成移轉並徹底測試新Magento 2網站後，請執行以下工作：

* 將Magento 1置於維護模式並永久停止所有管理員活動

* 啟動Magento 2 cron工作

* [清除所有Magento 2快取型別](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento 2索引器](../../../configuration/cli/manage-indexers.md#reindex)

* 變更DNS和負載平衡器，以指向Magento 2生產硬體
