---
title: 疑難排解最佳實務
description: 瞭解如何疑難排解Adobe Commerce實作問題。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 疑難排解最佳實務

請遵循這些最佳實踐，以便就雲端基礎結構問題對Adobe Systems商務進行有效的故障排除。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce

## 最佳實務

| 問題型別 | 最佳實務 | 資源 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 部署問題 | **遵循部署最佳實務。** 13%的支援票證涉及部署問題。 已更新最佳實務，納入預防上述許多原因的方法。 | 在開發人員檔案中[組建和部署的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices)。 |
| 網站停止運作問題 | **使用Site Down疑難排解員。**&#x200B;個Cron可能長時間執行且可能互相超載。 這是許多中斷和效能問題的根源。 | [Site Down Troubleshooter](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en)和[如何在我們的支援知識庫中重設cron工作](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en)。 |
| 效能問題 | **如果您沒有使用Adobe Commerce橫幅，請停用它。**&#x200B;當橫幅已啟用但未使用時，資源會在不需要時用來對資料庫進行查閱，而且會造成效能問題。 | [停用Adobe Commerce橫幅輸出，以改善我們的支援知識庫中的效能](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html)。 |
| 搜尋問題 | **已在Adobe Commerce 2.4.0中移除MySQL目錄搜尋引擎。**&#x200B;您必須先安裝並設定Elasticsearch主機，才能安裝2.4.0版。請參閱開發人員檔案中的安裝與設定Elasticsearch。 | [如需Elasticsearch開發人員檔中的設定服務](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) 。 |
| 自訂錯誤 | **請勿在高峰期部署。**&#x200B;新增和移除使用者將會觸發部署。 | 在開發人員檔案中[零停機部署](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)。 |
| 資料庫錯誤和問題 | **資料庫問題會導致部署（連結後問題）、效能和網站停機。**&#x200B;許多都包含錯誤或資料庫空間配置不足。 | [MariaDB錯誤碼](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes)；[在開發人員檔案中管理儲存空間](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) （包括資料庫）。 |
| 設定問題 | **依排程建立索引，而非儲存時建立索引。**&#x200B;這是最有效的索引設定。 「儲存」索引將導致完整重新索引。 | 在開發人員檔案中[設定索引子](../../../configuration/cli/manage-indexers.md#configure-indexers)。 |
| 自訂程式碼問題 | **檢查您的緩慢查詢記錄檔，找出識別或可能終止程式花費太多時間完成的機會。**&#x200B;緩慢的查詢可能導致資料庫死結，導致網站故障和效能問題。 | [在MySQL中檢查緩慢的查詢和程式花費太長時間](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 擴充功能問題 | **僅使用Commerce Marketplace上目前已驗證的擴充功能。** | Adobe Commerce的[延伸模組](https://marketplace.magento.com/extensions.html) |
| 資源問題 | **監視可用的記憶體與空間，並最佳化儲存空間。**&#x200B;在耗用大量資源的動作（例如部署）之前，您可能有可用的空間。 檔案儲存最佳化不佳（例如過多的大型豐富影像）也會造成空間不足。 資源不足會導致效能問題、網站無法使用、部署停滯以及部署失敗。 | [在開發人員檔案中管理磁碟空間](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)；[檔案儲存空間不足/耗盡，特定頁面載入速度緩慢](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en)在我們的支援知識庫中。 |
