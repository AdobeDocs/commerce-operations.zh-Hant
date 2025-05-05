---
title: Adobe Commerce的管理警報： CPU警告警報
description: 本文提供當您在 [!DNL New Relic]中收到Adobe Commerce的CPU警告警示時的疑難排解步驟。 需要立即採取行動來解決問題。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 09b5331df0b7504b1a3a792d4203f0eaaab842cc
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---


# Adobe Commerce的管理警報： CPU警告警報

本文提供當您在[!DNL New Relic]中收到Adobe Commerce的CPU警告警報時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![CPU警告警示](../../assets/managed-alerts/cpu-warning-magento-managed.png){width="500"}

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce Pro計畫架構

## 問題

如果您已為Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)註冊了個受管理的警示，且超過一或多個警示臨界值，則您將在[!DNL New Relic]中收到警示。 這些警報由Adobe開發，可讓客戶運用支援和工程部門的見解獲得標準集合。

<u> **做！** </u>

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱Commerce安裝指南中的[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱《Commerce安裝指南》中的[維護IP位址劐免清單](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。

<u>**不要！**</u>

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會在CPU或磁碟上造成額外的壓力。
* 執行任何主要管理工作(例如Commerce管理、資料匯入/匯出)。
* 清除您的快取。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

1. 使用[[!DNL New Relic] APM的「交易」頁面](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)來識別具有效能問題的交易：
   * 依遞增[!DNL Apdex]分數排序交易。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)表示使用者對您的Web應用程式與服務的回應時間感到滿意。 [低 [!DNL Apdex] 分數](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce)可能表示瓶頸（回應時間較長的交易）。 通常是資料庫[!DNL Redis]或PHP。 如需相關步驟，請參閱[!DNL New Relic] [檢視不滿意程度最高的交易 [!DNL Apdex] ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#apdex-dissat)。
   * 依最高輸送量、最慢的平均回應時間、最耗時的值和其他臨界值來排序交易。 如需相關步驟，請參閱[[!DNL New Relic] 尋找特定效能問題](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。
1. 如果您仍在努力識別來源，請使用[[!DNL New Relic] APM的[基礎結構]頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/)來識別資源繁重的服務。 如需相關步驟，請參閱[!DNL New Relic] [基礎架構監視主機頁面： [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)。
1. 如果您識別來源，請透過SSH連線至環境以進行進一步調查。 如需相關步驟，請參閱「雲端上的Commerce指南」中的[SSH至您的環境](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh)。
1. 如果您仍在努力找出來源：
   * 檢閱最近的趨勢，以識別最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。
   * 請考慮檢查及停用平面目錄。 如需相關步驟，請參閱Commerce支援知識庫中的[效能緩慢、執行緩慢且長時間的cron](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons)。
   * 如果您懷疑您遭受DDoS攻擊，請嘗試封鎖機器人流量。 如需相關步驟，請參閱Commerce支援知識庫中的[如何封鎖Fastly層級](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level)上Adobe Commerce的惡意流量。
1. 如果問題似乎是暫時性的，請執行升級等緩解步驟，或將網站置於維護模式。 如需相關步驟，請參閱Commerce支援知識庫中的[如何要求暫時調整大小](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize)，以及Commerce安裝指南中的[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 如果升級將網站恢復為正常運作，請考慮請求永久升級(聯絡您的Adobe客戶團隊)，或嘗試透過執行負載測試和最佳化查詢，或降低服務壓力的程式碼，在您的專用測試中重現問題。 如需相關步驟，請參閱Commerce on Cloud指南中的[載入和壓力測試](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing)。
