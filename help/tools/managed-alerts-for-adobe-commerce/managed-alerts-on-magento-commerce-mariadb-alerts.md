---
title: 在Adobe Commerce上管理警報：MariaDB警報
description: 本文提供當您在 [!DNL New Relic]中收到Adobe Commerce的MariaDB警示時的疑難排解步驟。 MariaDB警報會監控高查詢負載以及過度的資料操作語言(DML)查詢。 兩者都可能導致使用者體驗降低甚至停機。 您可以接收兩種警報。
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# 在Adobe Commerce上管理警報：MariaDB警報

本文提供當您在[!DNL New Relic]中收到Adobe Commerce的MariaDB警示時的疑難排解步驟。 MariaDB警報會監控高查詢負載以及過度的資料操作語言(DML)查詢。 兩者都可能導致使用者體驗降低甚至停機。 您可以接收兩種警報：

* DML查詢警告
* DML查詢嚴重

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce Pro計畫架構

## 問題

如果您已為Adobe Commerce[!DNL New Relic]註冊了[個Managed警示，且超過一或多個警示臨界值，則您將在](managed-alerts-for-magento-commerce.md)中收到一個Managed警示。 這些警報由Adobe開發，可讓客戶運用支援和工程部門的見解獲得標準集合。

**做！**

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱Commerce安裝指南中的[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱[維護免除IP位址清單](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。
* 結束任何指令碼，例如匯入，在網站效能受到影響時可能導致警示。

**不要！**

* 執行索引子或其他cron，可能會對MariaDB造成額外的壓力。
* 執行任何主要管理任務(即Commerce管理、資料匯入/匯出)。
* 清除您的快取。

## 解決方案

**DML查詢(使用UPDATE、INSERT和DELETE修改資料庫的查詢)**

如果您收到「DML查詢嚴重」警示，請從步驟1開始。 如果您收到「DML查詢警告」警示，請從步驟2開始。

1. 檢查Adobe Commerce支援票證是否存在。 如需相關步驟，請參閱我們的知識庫[追蹤您的支援票證](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case)。 支援人員可能已收到[!DNL New Relic]臨界值警示、建立票證並開始處理問題。 如果票證不存在，請建立一個。 票證應具有下列資訊：
   * 連絡原因：選取&#x200B;**[!UICONTROL New Relic MariaDB alert received]**。
   * 警示的說明。
   * [[!DNL New Relic] 事件連結](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 這包含在您的[Adobe Commerce](managed-alerts-for-magento-commerce.md)受管理警示中。
1. 若要識別問題的來源，請嘗試識別DML查詢：
   1. 使用New Relic [資料庫頁面](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)中的步驟來檢閱您的資料庫作業。
   1. 依&#x200B;**[!UICONTROL CALL COUNT]**&#x200B;排序，然後按&#x200B;**[!UICONTROL OPERATION]**。 檢閱`INSERT`、`DELETE`和`UPDATE`作業。
   1. 尋找高平均
   1. 按一下以尋找資料庫作業呼叫者。 這將會依時間識別使用該查詢的交易。
   1. 尋找程式碼最佳化或作業最佳化：
      * 程式碼最佳化：透過大量插入/更新、減少索引使用或節流程式碼，將查詢最佳化。
      * 作業最佳化：解除安裝資源密集的資料修改，以縮短流量時間。
      * 其他最佳化：確保您使用最新版的ECE-Tools。 如需相關步驟，請參閱Commerce on Cloud指南中的[更新ece-tools版本](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)。
