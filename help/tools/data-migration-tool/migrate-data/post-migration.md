---
title: 資料移轉後步驟
description: 了解使用 [!DNL Data Migration Tool] 將資料從Magento1移轉至Magento2。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# 資料移轉後步驟

完成遷移並徹底測試新Magento2站點後，請執行以下任務：

* 將Magento1置於維護模式，並永久停止所有管理活動

* 開始Magento2 cron作業

* [刷新所有Magento2快取類型](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento2索引器](../../../configuration/cli/manage-indexers.md#reindex)

* 更改DNS和負載平衡器以指向Magento2生產硬體
