---
title: 資料後移轉步驟
description: 瞭解使用 [!DNL Data Migration Tool] 將資料從Magento 1移轉至Magento 2後要採取的步驟。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# 資料後移轉步驟

完成移轉並徹底測試新的Magento 2網站後，請執行以下工作：

* 將Magento 1置於維護模式，並永久停止所有管理員活動

* 開始Magento 2 cron工作

* [排清所有Magento 2快取型別](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento 2索引子](../../../configuration/cli/manage-indexers.md#reindex)

* 變更DNS和負載平衡器，以指向Magento 2生產硬體
