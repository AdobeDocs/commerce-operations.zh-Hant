---
title: 資料移轉後步驟
description: 了解使用 [!DNL Data Migration Tool] 將資料從Magento1移轉至Magento2。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# 資料移轉後步驟

完成遷移並徹底測試新Magento2站點後，請執行以下任務：

* 將Magento1置於維護模式並永久停止所有 [管理](https://glossary.magento.com/admin) 活動

* 開始Magento2 cron作業

* [刷新所有Magento2快取類型](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento2索引器](../../../configuration/cli/manage-indexers.md#reindex)

* 更改DNS和負載平衡器以指向Magento2生產硬體
