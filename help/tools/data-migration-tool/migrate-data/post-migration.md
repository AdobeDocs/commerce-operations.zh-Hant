---
title: 資料遷移後步驟
description: 瞭解使用 [!DNL Data Migration Tool] 將資料從Magento1遷移到Magento2。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# 資料遷移後步驟

完成遷移並徹底測試新Magento2站點後，請執行以下任務：

* 將Magento1置於維護模式並永久停止所有管理活動

* 開始Magento2 cron作業

* [刷新所有Magento2快取類型](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento2索引器](../../../configuration/cli/manage-indexers.md#reindex)

* 更改DNS和負載平衡器以指向Magento2生產硬體
