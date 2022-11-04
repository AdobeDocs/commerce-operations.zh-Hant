---
title: 疑難排解最佳實務
description: 了解如何疑難排解Adobe Commerce實作問題。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 疑難排解最佳實務

請依照下列最佳實務，針對雲端基礎架構問題有效疑難排解Adobe Commerce。

## 受影響的產品和版本

Adobe Commerce雲基礎架構

## 最佳實務

| 問題類型 | 最佳實務 | 資源 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 部署問題 | **遵循部署最佳實務。** 13%的支援票證涉及部署問題。 最佳實務已更新，加入可預防其中許多原因的方法。 | [建置和部署的最佳實務](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 在開發人員檔案中。 |
| 網站關閉問題 | **使用「站點故障診斷程式」。** Cron可能會長時間運行，並且會互相溢出。 它們是許多中斷和效能問題的源頭。 | [站點故障診斷程式](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) 和 [如何重設cron作業](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 在我們的支援知識庫中。 |
| 效能問題 | **如果您未使用Adobe Commerce橫幅，請加以停用。** 當橫幅已啟用但未使用時，資源將用於在不需要時對資料庫進行查閱，這將導致效能問題。 | [停用Adobe Commerce橫幅輸出以改善效能](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html)我們的支援知識庫中的。 |
| 搜尋問題 | **Adobe Commerce 2.4.0已移除MySQL目錄搜尋引擎。** 在安裝2.4.0版之前，您必須先安裝並配置Elasticsearch主機。請參閱開發人員檔案中的安裝和配置Elasticsearch。 | [設定Elasticsearch服務](https://devdocs.magento.com/cloud/project/services-elastic.html) 在開發人員檔案中。 |
| 自訂錯誤 | **高峰時段不要部署。** 新增和移除使用者會觸發部署。 | [零停機部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) 在開發人員檔案中。 |
| 資料庫錯誤和問題 | **資料庫問題導致部署（掛接後問題）、效能和站點故障情況。** 許多操作涉及錯誤或資料庫空間分配不足。 | [MariaDB錯誤代碼](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [管理儲存空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （包括資料庫）。 |
| 設定問題 | **在保存時按計畫（而非索引）進行索引。** 這是最有效的索引配置。 保存時的索引將導致完全重新索引。 | [配置索引器](../../../configuration/cli/manage-indexers.md#configure-indexers) 在開發人員檔案中。 |
| 自訂程式碼問題 | **檢查您緩慢的查詢日誌，以發現並可能終止需要太多時間才能完成的進程的機會。** 查詢速度緩慢可能導致資料庫死鎖，導致站點停機和效能問題。 | [在MySQL中檢查慢速查詢和進程花費太長時間](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 擴充功能問題 | **僅在Commerce Marketplace上目前使用已驗證的擴充功能。** | [Adobe Commerce的擴充功能](https://marketplace.magento.com/extensions.html) |
| 資源問題 | **監視可用記憶體和空間並優化儲存。** 在佔用大量資源（例如部署）的操作之前，您可能有可用空間。 檔案儲存的最佳化不佳（例如，大型、豐富的映像過多）也會導致空間不足。 資源不足會導致效能問題、站點故障、部署停滯和部署失敗。 | [管理磁碟空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html) 在開發人員檔案中； [檔案儲存空間低/耗盡，特定頁面載入速度緩慢](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) 在我們的支援知識庫中。 |
