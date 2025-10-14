---
title: Adobe Commerce上的受管理警示： [!DNL Redis] 記憶體嚴重警示
description: 本文提供當您在 [!DNL Redis] 中收到Adobe Commerce的 [!DNL New Relic]記憶體嚴重警示時的疑難排解步驟。 需要立即採取行動來解決問題。
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
exl-id: 1233889e-8c02-4ad6-b12c-683010b7bf35
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# Adobe Commerce上的受管理警示： [!DNL Redis]記憶體嚴重警示

本文提供當您在[!DNL Redis]中收到Adobe Commerce的[!DNL New Relic]記憶體嚴重警示時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![new_relic_redis_memory_critical.png](../../assets/managed-alerts/new_relic_redis_memory_critical.png)

## 受影響的產品和版本

雲端基礎結構上所有版本的Adobe Commerce Pro計畫架構

## 問題

如果您已為Adobe Commerce[!DNL New Relic]註冊了[個受管理的警示，且超過一或多個警示臨界值，則您將在](managed-alerts-for-magento-commerce.md)中收到警示。 這些警報由Adobe開發，使用支援和工程部門的見解為商戶提供一組標準警報。

**<u>做！</u>**

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱《Commerce安裝指南》中的[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱《Commerce安裝指南》中的[維護IP位址劐免清單](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。

**<u>不要！</u>**

* 啟動其他行銷活動，為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會在CPU或磁碟上造成額外的壓力。
* 執行任何主要管理任務(即Commerce管理員中的主要動作，例如資料匯入/匯出、清除媒體、儲存具有大量指派產品的類別以及大量更新)。
* 清除您的快取。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解。

**由於這是嚴重警示，強烈建議您先完成步驟1，再嘗試疑難排解問題（從步驟2開始）。**

1. 檢查Adobe Commerce支援票證是否存在。 如需相關步驟，請參閱Commerce支援知識庫中的[追蹤您的支援票證](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case)。 支援人員可能已經收到[!DNL New Relic]臨界值警示、建立票證並開始處理問題。 如果票證不存在，請建立一個。 票證應具有下列資訊：

   * 連絡原因：選取&#x200B;**[!UICONTROL New Relic CRITICAL alert received]**。
   * 警示的說明。
   * [[!DNL New Relic] 事件連結](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/)。 這包含在您的[Adobe Commerce](managed-alerts-for-magento-commerce.md)受管理警示中。

1. 如果沒有支援票證，請前往[!DNL Redis]one.newrelic.com[&#x200B; > &#x200B;](https://login.newrelic.com) > **[!UICONTROL Infrastructure]**&#x200B;頁面，檢查&#x200B;**[!UICONTROL Third-party services]**&#x200B;已使用的記憶體是否在增加或減少，然後選取[!DNL Redis]儀表板。 如果它是穩定或遞增的，請[提交支援票證](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)以升級您的叢集，或將`maxmemory`限制增加到下一個層級。
1. 如果您無法識別[!DNL Redis]記憶體耗用量增加的原因，請檢閱最近的趨勢，以識別最近的程式碼部署或設定變更（例如，新客戶群組和目錄的大型變更）的相關問題。 建議您檢閱過去七天的活動，以瞭解程式碼部署或變更中的任何關聯。
1. 檢查協力廠商擴充功能是否有不當行為：

   * 請嘗試找出與最近安裝的協力廠商擴充功能之間的關聯性，以及問題開始的時間。
   * 檢閱可能影響Adobe Commerce快取並導致快取快速增長的擴充功能。 例如，自訂配置區塊、覆寫快取功能，以及將大量資料儲存在快取中。

1. 如果沒有證據顯示擴充功能有不當行為，請[安裝最新修補程式，以修正雲端基礎結構上Adobe Commerce的 [!DNL Redis] 問題](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues)。
1. 如果上述步驟無法協助您識別或疑難排解問題的來源，請考慮啟用L2快取以減少應用程式與[!DNL Redis]之間的網路流量。 如需L2快取的一般資訊，請參閱Commerce設定指南中的Adobe Commerce應用程式中的[L2快取](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cache/level-two-cache)。 若要啟用雲端基礎結構的L2快取，請嘗試下列步驟：

   * 若版本低於2002.1.2，請升級ECE工具。
   * 使用[使用REDIS\_BACKEND變數](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend)並更新`.magento.env.yaml`檔案來設定L2快取：

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
