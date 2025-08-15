---
title: 如何使用 [!DNL Observation for Adobe Commerce] nerdlet
description: 瞭解如何使用 [!DNL Observation for Adobe Commerce] nerdlet。
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# 如何使用[!DNL Observation for Adobe Commerce] Nerdlet

## 檢視問題的一般方法

檢查環境資源狀態：

* 檢查&#x200B;**[!UICONTROL Storage Free and MySQL % free storage by node]**&#x200B;個框架的%。

   * 如果您發現儲存空間不足，請依照框架標題中的連結操作。

* 檢查&#x200B;**[!UICONTROL free system memory and Swap memory free in bytes]**&#x200B;個框架的%。

   * 如果這些顯示非常低的記憶體狀態，就可能是問題的成因。

* 檢查&#x200B;**[!UICONTROL Alerts during the timeframe]**&#x200B;框架。

   * 雲端基礎結構上的Adobe Commerce提供[!DNL Managed alerts]。 您可以按一下標題中的連結來檢視[!DNL Support Knowledge Base]篇文章，這些文章將協助您判斷特定警示的動作。

* 檢查&#x200B;**[!UICONTROL CPU % by host]**&#x200B;框架：如果它顯示有高的CPU使用率，請檢查框架標題中的[!DNL Support Knowledge Base]文章。 此外，檢查以確保資料庫匯入/匯出或備份未在尖峰流量期間完成。

* 檢查&#x200B;**[!UICONTROL Web Traffic volume compared to one week ago]**&#x200B;時間格：如果流量遠高於同一期間的前一週，可以解釋嗎（例如，促銷活動或已經行銷的新產品）？
   * 如果無法解釋流量增加，請檢視生產環境的平均回應時間（毫秒）。 對回應時間有貢獻的流量是否與正常情況不同？ 展開時間範圍以檢視是否為異常。
   * 流量的增加是否會影響Web交易？ 檢查&#x200B;**[!UICONTROL Response Code]**&#x200B;框架是否有錯誤。 如果網站關閉，您可以按一下框架標題中的`Site Down?`連結。 框架會識別發生的任何錯誤及其頻率。
   * 有人將變更部署至您的網站嗎？ **[!UICONTROL Deployment Log Entries]**&#x200B;框架將指出是否在問題時間範圍內完成了任何部署。 如果問題是在部署後立即出現，可能是部署活動增加了額外的負載到網站（快取已清除、服務已重新啟動等）。
   * 是否發生放大或縮小的情況？ 如果您的網站是暫時擴充的，它可能已回復到原始的叢集大小。 如果提出增加網站容量的要求，可能會發生向上擴充。 檢查&#x200B;**[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**&#x200B;框架。 此框架有時會偵測到某個特定節點上的中斷情形。 如果您看到大小減少，表示可能有一或多個節點發生問題。

* **[!UICONTROL IP Frequency]**&#x200B;索引標籤會識別來自對原始伺服器發出的IP位址的請求頻率（表示無法從[!DNL Fastly]提供請求，因為它並未快取74）。

   * 對於任何[!DNL Fastly]相關問題，請檢查&#x200B;**[!UICONTROL Fastly Cache]**&#x200B;框架，並選取「錯誤」面向以檢視錯誤的請求百分比。 如果與非網頁載入一致，則可能會指出後端問題。
   * 如果載入似乎不是因為網路流量，則可能是錯誤或非Web要求的累積，例如緩慢的查詢或[!DNL crons]。

* 檢查&#x200B;**[!UICONTROL Database Errors]**&#x200B;影格是否有可能與問題/問題時間表一致的錯誤。
* 檢查&#x200B;**[!UICONTROL Database mysql-slow.log]**&#x200B;框架以識別正在發生的SQL敘述句。 如果未最佳化查詢，`INSERT`、`UPDATE`和`DELETE`命令可能需要一些時間。 即使是`SELECT`陳述式，如果針對大型資料表執行，也可能非常低效。
* **[!UICONTROL PHP States]**&#x200B;和&#x200B;**[!UICONTROL PHP Errors]**&#x200B;框架會顯示PHP的潛在問題。 **[!UICONTROL PHP States]**&#x200B;框架會顯示PHP處理序終止、啟動以及服務依節點到達就緒狀態時。 **[!UICONTROL PHP Errors]**&#x200B;框架可協助隔離問題與PHP有關的問題，例如記憶體大小、背景工作或伺服器數目。
* 若要檢視交易中的延遲，可以依欄排序「交易 — 平均、最大、最小」表格，以顯示執行時間最長的交易持續時間。 超載叢集在交易中將具有潛在持續時間，但也會顯示可能指出方法或[!DNL cron]問題的異常。
* **[!UICONTROL Cron error]**&#x200B;框架將顯示[!DNL cron]個鎖定、可能與[!DNL cron]個記錄檔關聯的SQL錯誤，以及當有專用的中繼環境時，可能在生產環境中執行的共用中繼環境[!DNL crons]。
* [!UICONTROL ElasticSearch Errors]框架顯示可能表示[!DNL Elasticsearch]查詢、資料或索引有重大問題的錯誤。
