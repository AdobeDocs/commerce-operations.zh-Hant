---
title: Adobe Commerce上的受管警報：CPU嚴重警報
description: 本文提供當您在 [!DNL New Relic]中收到Adobe Commerce的CPU嚴重警報時的疑難排解步驟。 需要立即採取行動來解決問題。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: b30266b8f39989103ca70fa3e57ade8cea9b0dcc
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Adobe Commerce上的受管警報：CPU嚴重警報

本文提供當您在[!DNL New Relic]中收到Adobe Commerce的CPU嚴重警報時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![磁碟嚴重警示](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce Pro計畫架構

## 問題

如果您已為Adobe Commerce](managed-alerts-for-magento-commerce.md)註冊了[個Managed警示，且超過一或多個警示臨界值，則您將在[!DNL New Relic]中收到一個Managed警示。 這些警報由Adobe Commerce開發，可讓客戶運用支援和工程部門的見解獲得標準集合。

<u>**做！**</u>：

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱Commerce安裝指南中的[啟用或停用維護模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱《Commerce安裝指南》中的[維護IP位址劐免清單](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。

<u>**不要！**</u>：

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，這可能會在CPU或磁碟上造成額外的壓力。
* 執行任何主要管理工作(例如Commerce管理、資料匯入/匯出)。
* 清除您的快取。

如果您在調查並解決警示原因之前執行任何「不執行」動作，您的網站可能會變成無回應（如果您尚未發生網站中斷）。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

>[!WARNING]
>
>由於這是嚴重警示，強烈建議您先完成&#x200B;**步驟1**，再嘗試疑難排解問題（從步驟2開始）。

檢查Adobe Commerce支援票證是否存在。 如需相關步驟，請參閱Commerce支援知識庫中的[追蹤您的支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case)。 支援人員可能已收到[!DNL New Relic]臨界值警示、建立票證，並開始處理問題。 如果票證不存在，請建立一個。 票證應具有下列資訊：

1. 連絡原因：選取&#x200B;**[!UICONTROL New Relic CRITICAL alert received]**。
1. 警示的說明。
1. [[!DNL New Relic] 事件連結](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 這包含在您的[Adobe Commerce](managed-alerts-for-magento-commerce.md)受管理警示中。
1. 使用[[!DNL New Relic] APM的「交易」頁面](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)來識別具有效能問題的交易：
   * 依遞增Apdex分數排序交易。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)表示使用者對您的Web應用程式與服務的回應時間感到滿意。 [低 [!DNL Apdex] 分數](managed-alerts-for-magento-commerce-apdex-warning-alert.md)可能表示瓶頸（回應時間較長的交易）。 通常，它與資料庫、[!DNL Redis]或PHP有關。 如需相關步驟，請參閱New Relic [檢視不滿意程度最高的交易 [!DNL Apdex] 2}。](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)
   * 依最高輸送量、最慢的平均回應時間、最耗時的值和其他臨界值來排序交易。 如需步驟，請參閱[!DNL New Relic] [尋找特定效能問題](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。
1. 如果您仍在努力識別來源，請使用[[!DNL New Relic] APM的[基礎結構]頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page)來識別資源密集的服務。 如需相關步驟，請參閱[!DNL New Relic] [基礎架構監視主機頁面：處理序標籤](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)。
1. 如果您識別來源，請透過SSH連線至環境以進行進一步調查。 如需相關步驟，請參閱「雲端上的Commerce指南」中的[SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)。
1. 如果您仍在努力找出來源：
   * 檢閱最近的趨勢，以識別最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。
   * 請考慮檢查及停用平面目錄。 如需相關步驟，請參閱Commerce支援知識庫中的[效能緩慢、執行緩慢且長時間的cron](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons)。
   * 如果您懷疑您遭受DDoS攻擊，請嘗試封鎖機器人流量。 如需相關步驟，請參閱Commerce支援知識庫中的[如何封鎖Fastly層級](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level)上雲端基礎結構上Adobe Commerce的惡意流量。
1. 如果問題似乎是暫時性的，請執行升級等緩解步驟，或將網站置於維護模式。 如需相關步驟，請參閱Commerce支援知識庫中的[如何要求暫時調整大小](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize)，以及Commerce安裝指南中的[啟用或停用維護模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 如果升級將網站恢復為正常運作，請考慮請求永久升級(聯絡您的Adobe客戶團隊)，或嘗試透過執行負載測試並最佳化查詢或降低服務壓力的程式碼，在您的專用測試中重現問題。 如需相關步驟，請參閱雲端上的Commerce指南中的[載入與壓力測試](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing)。
