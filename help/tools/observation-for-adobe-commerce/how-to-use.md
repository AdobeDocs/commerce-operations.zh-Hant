---
title: 「如何使用 [!DNL Observation for Adobe Commerce] 內爾特
description: 瞭解如何使用 [!DNL Observation for Adobe Commerce] 書呆子。
source-git-commit: 69bcb755c3c1f9a820856ac69ce12eb85c686213
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 如何使用 [!DNL Observation for Adobe Commerce] 內萊

## 處理問題的一般方法

檢查環境資源狀態：

* 檢查% **[!UICONTROL Storage Free and MySQL % free storage by node]** 框。

   * 如果看到低儲存，請按照框架標題中的連結操作。

* 檢查% **[!UICONTROL free system memory and Swap memory free in bytes]** 框。

   * 如果這些顯示的記憶體狀態非常低，則它們可能會導致問題。

* 檢查 **[!UICONTROL Alerts during the timeframe]** 框。

   * Adobe Commerce提供雲基礎架構 [!DNL Managed alerts]。 可以按一下標題中的連結查看 [!DNL Support Knowledge Base] 有助於確定特定警報的部件上的操作的文章。

* 檢查 **[!UICONTROL CPU % by host]** 幀：如果CPU利用率很高，請檢查 [!DNL Support Knowledge Base] 框的標題中的文章。 另外，檢查以確保在通信高峰期不執行資料庫導入/導出或備份。

* 檢查 **[!UICONTROL Web Traffic volume compared to one week ago]** 幀：如果流量比前一週同期高得多，可以解釋嗎（例如，銷售活動或已營銷的新產品）?
   * 如果無法解釋通信量的增加，請查看生產環境的平均響應時間（毫秒）。 導致響應時間的較高流量是否與正常情況不同？ 擴展時間範圍，查看是否是異常。
   * 流量的增加是否會影響Web事務？ 檢查 **[!UICONTROL Response Code]** 錯誤框。 如果站點關閉，可按一下 *[!UICONTROL Site Down?]* 連結。 幀將識別發生的任何錯誤及其頻率。
   * 是否有人將更改部署到您的網站？ 的 **[!UICONTROL Deployment Log Entries]** 框架將指示在問題時間段內是否執行過任何部署。 如果問題在部署後立即出現，則可能是部署活動正在向站點添加額外負載（清除快取、重新啟動服務等）。
   * 是否發生了更大或縮小？ 如果您的站點已臨時調整大小，則它可能已返回到其原始群集大小。 如果請求增加站點容量，則可能會發生更大。 檢查 **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** 框。 此幀有時會檢測某個特定節點上的中斷。 如果看到大小減小，則可能表示存在一個或多個節點的問題。

* 的 **[!UICONTROL IP Frequency]** 頁籤標識來自源伺服器的IP地址的請求頻率(這意味著無法從 [!DNL Fastly] 直到74，它沒有快取)。

   * 對於任何 [!DNL Fastly] 相關問題，檢查 **[!UICONTROL Fastly Cache]** 框，並選擇「錯誤」方面以查看錯誤請求的百分比。 如果與非Web負載重合，則可能會指示後端問題。
   * 如果載入似乎不是由於Web通信，則可能會出現錯誤或生成非Web請求，如慢速查詢或克隆。

* 檢查 **[!UICONTROL Database Errors]** 可能與問題/問題時間表一致的錯誤幀。
* 檢查 **[!UICONTROL Database mysql-slow.log]** 框架，用於標識正在發生的SQL陳述式。 `INSERT`。 `UPDATE`, `DELETE` 如果查詢未優化，則命令可能需要一段時間。 甚至 `SELECT` 如果對大型表執行此操作，語句會非常低效。
* **[!UICONTROL PHP States]** 和 **[!UICONTROL PHP Errors]** 幀將顯示PHP的潛在問題。 的 **[!UICONTROL PHP States]** 幀將按節點顯示PHP進程終止、啟動以及服務達到就緒狀態。 的 **[!UICONTROL PHP Errors]** 框架有助於確定PHP的問題所在，如記憶體大小、工作程式或伺服器數量。
* 要查看事務處理中的延遲，可以按列對事務處理 — 平均、最大、最小表進行排序，以顯示最長運行的事務持續時間。 重載的群集在事務中具有潛在的持續時間，但它也會顯示異常，這些異常可能會查明某個方法或cron的問題。
* 的 **[!UICONTROL Cron error]** frame將顯示cron鎖定、可能與cron日誌關聯的SQL錯誤，以及當存在專用暫存環境時可能在生產環境中運行的共用暫存cron。
* 的 [!UICONTROL ElasticSearch Errors] 幀顯示可能表示與 [!DNL Elasticsearch] 查詢、資料或索引。
