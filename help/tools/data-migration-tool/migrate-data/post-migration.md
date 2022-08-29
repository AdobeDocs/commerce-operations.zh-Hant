---
title: 資料遷移後步驟
description: 瞭解使用 [!DNL Data Migration Tool] 將資料從Magento1遷移到Magento2。
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# 資料遷移後步驟

完成遷移並徹底測試新Magento2站點後，請執行以下任務：

* 將Magento1置於維護模式並永久停止所有 [管理](https://glossary.magento.com/admin) 活動

* 開始Magento2 cron作業

* [刷新所有Magento2快取類型](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [重新索引所有Magento2索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* 更改DNS和負載平衡器以指向Magento2生產硬體
