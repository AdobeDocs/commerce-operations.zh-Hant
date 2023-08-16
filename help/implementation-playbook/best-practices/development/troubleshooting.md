---
title: 疑難排解最佳實務
description: 瞭解如何疑難排解Adobe Commerce實作問題。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# 疑難排解最佳實務

請遵循這些最佳實務，以針對雲端基礎結構問題有效疑難排解Adobe Commerce。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce

## 最佳實務

| 問題型別 | 最佳實務 | 資源 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 部署問題 | **遵循部署最佳實務。** 13%的支援票證與部署問題有關。 已更新最佳實務，納入預防上述許多原因的方法。 | [建置和部署的最佳實務](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) （位於我們的開發人員檔案中）。 |
| 網站停止運作問題 | **使用「網站故障排除」。** Cron可能長時間執行並會相互超越。 這是許多中斷和效能問題的根源。 | [Site Down疑難排解員](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) 和 [如何重設cron工作](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 在我們的支援知識庫中。 |
| 效能問題 | **如果您沒有使用Adobe Commerce橫幅，請將其停用。** 當橫幅已啟用但未使用時，資源會在不需要時用來對資料庫進行查閱，這會導致效能問題。 | [停用Adobe Commerce橫幅輸出以改善效能](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) 在我們的支援知識庫中。 |
| 搜尋問題 | **Adobe Commerce 2.4.0中已移除MySQL目錄搜尋引擎。** 您必須先安裝並設定Elasticsearch主機，才能安裝2.4.0版。請參閱開發人員檔案中的安裝與設定Elasticsearch。 | [設定Elasticsearch服務](https://devdocs.magento.com/cloud/project/services-elastic.html) （位於我們的開發人員檔案中）。 |
| 自訂錯誤 | **請勿在高峰期部署。** 新增和移除使用者將觸發部署。 | [零停機部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) （位於我們的開發人員檔案中）。 |
| 資料庫錯誤和問題 | **資料庫問題會導致部署（後連結問題）、效能和網站關閉狀況。** 許多都涉及錯誤或資料庫空間配置不足。 | [MariaDB錯誤碼](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes)； [管理儲存空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （包括資料庫）。 |
| 設定問題 | **依排程建立索引，而非儲存時建立索引。** 這是最有效的索引設定。 「儲存」索引將導致完整重新索引。 | [設定索引子](../../../configuration/cli/manage-indexers.md#configure-indexers) （位於我們的開發人員檔案中）。 |
| 自訂程式碼問題 | **檢查您的緩慢查詢記錄，找出需要花費太多時間才能識別及可能終止流程的機會。** 緩慢的查詢可能會導致資料庫發生死結，進而導致網站故障和效能問題。 | [在MySQL中檢查緩慢的查詢和程式花費太長時間](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 擴充功能問題 | **僅使用Commerce Marketplace上目前已驗證的擴充功能。** | [Adobe Commerce的擴充功能](https://marketplace.magento.com/extensions.html) |
| 資源問題 | **監視可用的記憶體與空間，並最佳化儲存空間。** 在耗用大量資源（例如部署）的動作之前，您可能會有可用空間。 檔案儲存最佳化不佳（例如過多的大型豐富影像）也會造成空間不足。 資源不足會導致效能問題、網站無法使用、部署停滯以及部署失敗。 | [管理磁碟空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （在開發人員檔案中）； [檔案儲存空間不足/耗盡，特定頁面載入緩慢](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) 在我們的支援知識庫中。 |
