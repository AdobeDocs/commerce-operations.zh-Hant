---
title: 如何使用 [!DNL Observation for Adobe Commerce] Nerdlet
description: 瞭解如何使用 [!DNL Observation for Adobe Commerce] 書呆子。
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# 如何使用 [!DNL Observation for Adobe Commerce] Nerdlet

## 檢視問題的一般方法

檢查環境資源狀態：

* 檢查% **[!UICONTROL Storage Free and MySQL % free storage by node]** 框架。

   * 如果您發現儲存空間不足，請依照框架標題中的連結操作。

* 檢查% **[!UICONTROL free system memory and Swap memory free in bytes]** 框架。

   * 如果這些顯示非常低的記憶體狀態，就可能是問題的成因。

* 檢查 **[!UICONTROL Alerts during the timeframe]** 框架。

   * 雲端基礎結構上的Adobe Commerce提供 [!DNL Managed alerts]. 您可以按一下標題中的連結以檢視 [!DNL Support Knowledge Base] 協助判斷特定警示之您動作的相關文章。

* 檢查 **[!UICONTROL CPU % by host]** 框架：如果顯示有高的CPU使用率，請檢查 [!DNL Support Knowledge Base] 框架標題中的文章。 此外，檢查以確保資料庫匯入/匯出或備份未在尖峰流量期間完成。

* 檢查 **[!UICONTROL Web Traffic volume compared to one week ago]** 框架：如果流量比同一期間的上週高出許多，可以解釋嗎（例如，促銷活動或已經行銷的新產品）？
   * 如果無法解釋流量增加，請檢視生產環境的平均回應時間（毫秒）。 對回應時間有貢獻的流量是否與正常情況不同？ 展開時間範圍以檢視是否為異常。
   * 流量的增加是否會影響Web交易？ 檢查 **[!UICONTROL Response Code]** 錯誤框架。 如果網站關閉，您可以按一下 `Site Down?` 框架標題中的連結。 框架會識別發生的任何錯誤及其頻率。
   * 有人將變更部署至您的網站嗎？ 此 **[!UICONTROL Deployment Log Entries]** 框架會指出是否在問題時間範圍內完成任何部署。 如果問題是在部署後立即出現，可能是部署活動增加了額外的負載到網站（快取已清除、服務已重新啟動等）。
   * 是否發生放大或縮小的情況？ 如果您的網站是暫時擴充的，它可能已回復到原始的叢集大小。 如果提出增加網站容量的要求，可能會發生向上擴充。 檢查 **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** 框架。 此框架有時會偵測到某個特定節點上的中斷情形。 如果您看到大小減少，表示可能有一或多個節點發生問題。

* 此 **[!UICONTROL IP Frequency]** tab會識別來自對原始伺服器發出的IP位址的請求頻率（這表示無法從提供請求） [!DNL Fastly] 做為74)。

   * 針對任何 [!DNL Fastly] 相關問題，請檢查 **[!UICONTROL Fastly Cache]** 框架，並選取錯誤面向以檢視錯誤的請求百分比。 如果與非網頁載入一致，則可能會指出後端問題。
   * 如果載入似乎不是因為網路流量，則可能是錯誤或非Web請求的累積，例如緩慢查詢或 [!DNL crons].

* 檢查 **[!UICONTROL Database Errors]** 與問題/問題時間表可能一致的錯誤影格。
* 檢查 **[!UICONTROL Database mysql-slow.log]** 框架來識別正在發生的SQL敘述句。 `INSERT`， `UPDATE`、和 `DELETE` 如果查詢未最佳化，命令可能需要一些時間。 平均 `SELECT` 如果針對大型資料表執行陳述式，可能會非常低效。
* **[!UICONTROL PHP States]** 和 **[!UICONTROL PHP Errors]** 框架會顯示PHP的潛在問題。 此 **[!UICONTROL PHP States]** 框架會顯示PHP流程終止、啟動以及服務依節點到達就緒狀態時的情況。 此 **[!UICONTROL PHP Errors]** 框架可協助隔離PHP問題的位置，例如記憶體大小、背景工作或伺服器數目。
* 若要檢視交易中的延遲，可以依欄排序「交易 — 平均、最大、最小」表格，以顯示執行時間最長的交易持續時間。 超載叢集在交易中會有潛在的持續時間，但也會顯示可能指出方法或問題的異常 [!DNL cron].
* 此 **[!UICONTROL Cron error]** 框架將會顯示 [!DNL cron] 鎖定，可能相關聯的SQL錯誤 [!DNL cron] 記錄檔和共用的測試環境 [!DNL crons] 有專用的中繼環境時，生產環境中可能正在執行的專案。
* 此 [!UICONTROL ElasticSearch Errors] 框架顯示可能表示重大問題的錯誤 [!DNL Elasticsearch] 查詢、資料或索引。
