---
title: 「如何使用 [!DNL Observation for Adobe Commerce] nerlet
description: 了解如何使用 [!DNL Observation for Adobe Commerce] 內德萊特。
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# 如何使用 [!DNL Observation for Adobe Commerce] 內爾特

## 一般的問題處理方法

檢查環境資源狀態：

* 檢查% **[!UICONTROL Storage Free and MySQL % free storage by node]** 框架。

   * 如果您看到儲存空間不足，請遵循框架標題中的連結。

* 檢查% **[!UICONTROL free system memory and Swap memory free in bytes]** 框架。

   * 如果這些顯示的記憶體非常低，則可能是問題的成因。

* 檢查 **[!UICONTROL Alerts during the timeframe]** 框。

   * Adobe Commerce在雲基礎架構中提供 [!DNL Managed alerts]. 您可以按一下標題中的連結以查看 [!DNL Support Knowledge Base] 可協助判斷您特定警報動作的文章。

* 檢查 **[!UICONTROL CPU % by host]** 框架：如果CPU利用率高，請檢查 [!DNL Support Knowledge Base] 框架標題中的文章。 此外，檢查以確保在高峰流量期間不會執行資料庫導入/導出或備份。

* 檢查 **[!UICONTROL Web Traffic volume compared to one week ago]** 框架：如果同一期間的流量比前一週高得多，可以解釋它嗎（例如銷售促銷活動或已推銷的新產品）?
   * 如果無法解釋流量增加，請查看生產環境的平均回應時間（毫秒）。 造成回應時間的流量是否高於正常值？ 展開時間範圍以查看是否為異常。
   * 流量增加是否會影響Web交易？ 檢查 **[!UICONTROL Response Code]** 錯誤的框架。 如果網站關閉，您可以按一下 `Site Down?` 框架標題中的連結。 該框架將識別發生的任何錯誤及其頻率。
   * 有人將變更部署至您的網站嗎？ 此 **[!UICONTROL Deployment Log Entries]** frame會指出在問題時間範圍內是否已完成任何部署。 如果問題在部署後立即出現，則可能是部署活動正在向站點添加額外負載（快取已清除、服務重新啟動等）。
   * 是否發生了大小調整或大小調整？ 如果網站已暫時調整大小，則可能已恢復為原始叢集大小。 如果提出要求以增加網站容量，可能會發生更新。 檢查 **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** 框。 此幀有時會檢測到某個特定節點的中斷。 如果看到大小減小，表示一或多個節點出現問題。

* 此 **[!UICONTROL IP Frequency]** 索引標籤會識別對來源伺服器提出之IP位址的要求頻率(表示無法從 [!DNL Fastly] 截至74日，未快取)。

   * 適用於任何 [!DNL Fastly] 相關問題，請檢查 **[!UICONTROL Fastly Cache]** 框架中，然後選取「錯誤」面向，以查看錯誤請求的百分比。 如果符合非Web載入，則可能表示後端問題。
   * 如果載入似乎並非由於Web流量所致，則可能會發生錯誤或非Web請求的建立，例如查詢速度緩慢或 [!DNL crons].

* 檢查 **[!UICONTROL Database Errors]** 可能與問題/問題時間軸一致的錯誤幀。
* 檢查 **[!UICONTROL Database mysql-slow.log]** 用於標識正在發生的SQL陳述式的框架。 `INSERT`, `UPDATE`，和 `DELETE` 如果查詢未優化，則命令可能需要一段時間。 平均 `SELECT` 如果對大型表執行語句，則效率會非常低。
* **[!UICONTROL PHP States]** 和 **[!UICONTROL PHP Errors]** 框架將顯示PHP的潛在問題。 此 **[!UICONTROL PHP States]** frame將顯示PHP進程終止、啟動，以及當服務按節點到達就緒狀態時。 此 **[!UICONTROL PHP Errors]** frame可能有助於隔離PHP的問題，如記憶體大小、工作人員或伺服器數量。
* 要查看事務中的延遲，可以按列排序事務 — 平均、最大、最小表，以顯示運行最長的事務持續時間。 多載的叢集在交易中會有延遲的持續時間，但也會顯示異常，這些異常可能會找出方法或 [!DNL cron].
* 此 **[!UICONTROL Cron error]** 框將顯示 [!DNL cron] 鎖，可能與關聯的SQL錯誤 [!DNL cron] 記錄檔和共用中繼 [!DNL crons] 當有專用的中繼環境時，可能會在生產環境中執行。
* 此 [!UICONTROL ElasticSearch Errors] 框顯示錯誤，這些錯誤可能表示 [!DNL Elasticsearch] 查詢、資料或索引。
