---
title: 排除最佳做法
description: 瞭解如何解決Adobe Commerce實施問題。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# 排除最佳做法

請遵循這些最佳實踐，在雲基礎架構問題上對Adobe Commerce進行有效的故障排除。

## 受影響的產品和版本

Adobe Commerce在雲基礎架構上

## 最佳做法

| 問題類型 | 最佳做法 | 資源 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 部署問題 | **遵循部署最佳做法。** 13%的支援票證涉及部署問題。 最佳做法已經更新，以包括防止許多這些原因的方法。 | [構建和部署的最佳做法](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 我們的開發人員文檔中。 |
| 站點關閉問題 | **使用「站點關閉」(Site Down)「故障排除器」(Troubleshooter)。** Cron可以運行很長，並且可以互相溢出。 它們是許多停機和效能問題的根源。 | [站點關閉疑難解答](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) 和 [如何重置cron作業](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 我們的支援知識庫。 |
| 效能問題 | **如果不使用Adobe Commerce橫幅，請將其禁用。** 啟用但未使用標題時，資源用於在不需要時對資料庫進行查找，這將導致效能問題。 | [禁用Adobe Commerce橫幅輸出以提高效能](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) 我們的支援知識庫。 |
| 搜索問題 | **MySQL目錄搜索引擎已在Adobe Commerce2.4.0中刪除。** 必須在安裝2.4.0版之前安裝並配置Elasticsearch主機。請參閱開發人員文檔中的「安裝和配置Elasticsearch」。 | [設定Elasticsearch服務](https://devdocs.magento.com/cloud/project/services-elastic.html) 我們的開發人員文檔中。 |
| 自定義錯誤 | **在高峰時段不要部署。** 添加和刪除用戶將觸發部署。 | [零停機部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) 我們的開發人員文檔中。 |
| 資料庫錯誤和問題 | **資料庫問題導致部署（掛接後問題）、效能和站點關閉情況。** 許多錯誤或資料庫空間分配不足。 | [MariaDB錯誤代碼](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [管理儲存空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （包括資料庫）。 |
| 配置問題 | **按計畫而不是按保存時的索引進行索引。** 這是最有效的索引配置。 「保存時索引」將導致完全重新索引。 | [配置索引器](../../../configuration/cli/manage-indexers.md#configure-indexers) 我們的開發人員文檔中。 |
| 自定義代碼問題 | **檢查查詢日誌速度慢的情況，以發現可能會中斷需要花費太多時間才能完成的進程。** 查詢速度慢可能導致資料庫死鎖，導致站點停機和效能問題。 | [在MySQL中檢查慢查詢和過長的進程](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 擴展問題 | **僅使用Commerce Marketplace上當前已驗證的擴展。** | [Adobe Commerce擴展](https://marketplace.magento.com/extensions.html) |
| 資源問題 | **監視可用記憶體和空間並優化儲存。** 在消耗大量資源（例如，部署）的操作之前，您可能有可用空間。 檔案儲存優化不足（例如，大型富映像過多）也會導致空間不足。 資源不足導致效能問題、站點停機、部署停滯和部署失敗。 | [管理磁碟空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html) 在開發人員文檔中； [檔案儲存低/耗盡，特定頁載入速度慢](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) 我們的支援知識庫。 |
