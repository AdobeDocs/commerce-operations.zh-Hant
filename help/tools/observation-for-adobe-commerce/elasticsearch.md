---
title: 此 [!UICONTROL Elasticsearch] 標籤
description: 瞭解 [!UICONTROL Elasticsearch] 標籤之 [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 此 [!UICONTROL Elasticsearch] 標籤

## [!UICONTROL Cluster Status Summary]:

![叢集狀態摘要](../../assets/tools/cluster-status-summary.jpg)

在選取的時間範圍內， **[!UICONTROL Cluster Status Summary]** 框架顯示顏色狀態， [!DNL Elasticsearch] 叢集已通過。 在此範例中，在選取的時間範圍內，叢集在選取的時間範圍內分別有一個處於綠色和黃色狀態。

## [!UICONTROL Active Primary Shards]

![使用中的主要分片](../../assets/tools/active-primary-shards.jpg)

此 **[!UICONTROL Active Primary Shards]** 框架會根據所選帳戶的使用中主要分片的數量，顯示不同的數字 [!DNL Elasticsearch] 服務。

從 [!DNL Elasticsearch]：最終指南 [2.x]：

&quot;In [可動態更新的索引](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html)，我們說明分片是一種Lucene索引，而 [!DNL Elasticsearch] 索引是分片的集合。 您的應用程式與索引對話，並且 [!DNL Elasticsearch] 將您的要求路由至適當的分片。 分片是比例單位。 您可以擁有的最小索引是具有單一分片的索引。 這或許足以滿足您的需求 — 單一分割可以儲存大量資料 — 但會限制您的擴充能力。」

建立索引時，會使用該索引建立多個分片。 依預設，每個新索引會分配五個主要分片，這表示一個索引可以分佈到五個節點（每個節點一個分片）。 也有復本分片。 這些主要用於容錯移轉。 復本分片可以提供讀取要求。

## [!UICONTROL Active Shards in Cluster]

![叢集中的作用中分片](../../assets/tools/active-shards-in-cluster.jpg)

此 **[!UICONTROL Active Shards in Cluster]** 影格顯示「 」中主要和復本分割的總數。 [!DNL Elasticsearch] 叢集。

## [!UICONTROL Index health - this will show the index name and color status]

![索引健康狀態](../../assets/tools/index-health.jpg)

此框架顯示索引名稱和索引顏色狀態計數。 向下捲動表格，您會看到相同的索引名稱，其顏色狀態為黃色和紅色。 27索引名稱之後的數字是狀態顏色的計數。 如果為零，則在所選時間範圍內，沒有處於該色彩狀態的索引執行個體。

## [!UICONTROL Elasticsearch Status by node information]

![Elasticsearch狀態](../../assets/tools/elasticsearch-status-by-node.jpg)

此 **[!UICONTROL Elasticsearch Status by node information]** 框架顯示 [!DNL Elasticsearch] 依顏色和節點區分的叢集狀態。 這有助於指示中的節點 [!DNL Elasticsearch] 叢集在選取的時間範圍內傳回什麼狀態。

## [!UICONTROL Elasticsearch index information]

![Elasticsearch索引資訊](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

此 **[!UICONTROL Elasticsearch index information]** 表格會顯示索引名稱、所在節點、索引檔案的數目、索引狀況以及在特定時間的索引大小（以MB為單位）。

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch處理CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

此 **[!UICONTROL Elasticsearch process CPU %]** 框架顯示處理CPU百分比，依據為 [!DNL Elasticsearch] 在選取的時間範圍內處理。

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch記憶體記憶體廢棄專案](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] 是Java程式。 如果配置的記憶體不足，它會啟動記憶體回收，以釋放記憶體。 如果記憶體回收頻繁，表示配置的記憶體可能有太多索引或分片。 可能有機會清理索引和分片，或 [!DNL Elasticsearch] 可能需要更多記憶體。

## [!UICONTROL Elasticsearch Index information]

![Elasticsearch索引資訊](../../assets/tools/elasticsearch-index-information-2.jpg)

建立及更新索引時，索引狀況可能會變更。

## [!UICONTROL Elasticsearch Index Size]

![Elasticsearch索引大小](../../assets/tools/elasticsearch-index-size.jpg)

此 **[!UICONTROL Elasticsearch Index Size]** 影格會指出所選時間範圍內的索引名稱和大小。 這可能表示網站索引的方式有問題。

## [!UICONTROL Elasticsearch Errors]

![Elasticsearch錯誤](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

此 **[!UICONTROL Elasticsearch Errors]** 框架顯示錯誤，包含 [!DNL Elasticsearch] 例如空間不足，在所有分片都失敗時、搜尋發生引數問題、版本錯誤和所有節點都無法使用時，從黃色切換到紅色狀態。

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch未指派的分片](../../assets/tools/elasticsearch-unassigned-shards.jpg)

未指派的分割會造成叢集從綠色狀態移至黃色狀態。
