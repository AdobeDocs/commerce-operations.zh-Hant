---
title: 「 [!UICONTROL Elasticsearch] 頁籤
description: 瞭解 [!UICONTROL Elasticsearch] 頁籤 [!DNL Observation for Adobe Commerce]。
source-git-commit: 2427a18ea67833bc50912ef78be29d4320b5b205
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# 的 [!UICONTROL Elasticsearch] 頁籤

## [!UICONTROL Cluster Status Summary]:

![群集狀態摘要](../../assets/tools/cluster-status-summary.jpg)

在選定的時間範圍內， **[!UICONTROL Cluster Status Summary]** 框顯示 [!DNL Elasticsearch] 群集已通過。 在本示例中，在所選時間範圍內，群集在所選時間範圍內曾處於「綠色」狀態一次，而處於「黃色」狀態一次。

## [!UICONTROL Active Primary Shards]

![活動主分片](../../assets/tools/active-primary-shards.jpg)

的 **[!UICONTROL Active Primary Shards]** 幀將根據所選帳戶的活動主分片數顯示不同的數字 [!DNL Elasticsearch] 服務。

從 [!DNL Elasticsearch]:最終指南 [2.x]:

&quot;在 [動態可更新索引](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html)我們解釋說，碎片是一個Lucene指數 [!DNL Elasticsearch] index是碎片的集合。 您的應用程式會與索引對話， [!DNL Elasticsearch] 將您的請求路由到相應的碎片。 碎片是比例單位。 你可以擁有的最小的索引是一個包含單個碎片的索引。 這可能足以滿足您的需求 — 單個碎片可以容納大量資料 — 但會限制您擴展的能力。」

建立索引時，會使用該索引建立多個分片。 預設情況下，每個新索引分配五個主分片，這意味著一個索引可以跨五個節點分佈（每個節點分片一個）。 還有復製片。 這些主要用於故障切換。 副本分片可以為讀取請求提供服務。

## [!UICONTROL Active Shards in Cluster]

![群集中的活動分片](../../assets/tools/active-shards-in-cluster.jpg)

**[!UICONTROL Active Shards in Cluster]**  — 主分片和副本分片 [!DNL Elasticsearch] 群集。

## [!UICONTROL Index health - this will show the index name and color status]

![索引健康](../../assets/tools/index-health.jpg)

此框架將顯示索引名稱和索引顏色狀態計數。 向下滾動表時，您將看到具有「黃色」和「紅色」狀態的相同索引名稱。 27索引名稱后面的數字是狀態顏色的計數。 如果為零，則在這些選定時間幀期間沒有索引處於該顏色狀態的實例。

## [!UICONTROL Elasticsearch Status by node information]

![Elasticsearch狀態](../../assets/tools/elasticsearch-status-by-node.jpg)

的 **[!UICONTROL Elasticsearch Status by node information]** 框顯示 [!DNL Elasticsearch] 按顏色、按節點分類群集狀態。 這將有助於指明 [!DNL Elasticsearch] 群集正在返回選定時間段內的狀態。

## [!UICONTROL Elasticsearch index information]

![Elasticsearch索引資訊](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

此 **[!UICONTROL Elasticsearch index information]** 該表以MB為單位顯示特定時間的索引名稱、所在節點、索引文檔數、索引運行狀況和索引大小。

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch進程CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

的 **[!UICONTROL Elasticsearch process CPU %]** 幀顯示進程CPU% [!DNL Elasticsearch] 在選定的時間範圍內進行處理。

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch記憶體垃圾](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] 是Java進程。 如果它在分配的記憶體上運行不足，它將啟動垃圾收集以釋放記憶體。 如果垃圾回收頻繁，則表明分配的記憶體可能有過多的索引或碎片。 可能有機會清理指數和碎片，或 [!DNL Elasticsearch] 可能需要更多記憶體。

## [!UICONTROL Elasticsearch Index information]

![Elasticsearch索引資訊](../../assets/tools/elasticsearch-index-information-2.jpg)

在建立和更新索引時，索引運行狀況可能會發生變化。

## [!UICONTROL Elasticsearch Index Size]

![Elasticsearch索引大小](../../assets/tools/elasticsearch-index-size.jpg)

的 **[!UICONTROL Elasticsearch Index Size]** frame指示所選時段內的索引名稱和大小。 它可能表示站點索引方式存在問題。

## [!UICONTROL Elasticsearch Errors]

![Elasticsearch錯誤](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

的 **[!UICONTROL Elasticsearch Errors]** 幀將顯示錯誤 [!DNL Elasticsearch] 如空間不足、從「黃色」切換到「紅色」狀態、當所有分片失敗、搜索出現參數問題、版本錯誤以及所有節點不可用時。

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch未分配的分片](../../assets/tools/elasticsearch-unassigned-shards.jpg)

未分配的分片將導致群集從綠色狀態移動到黃色狀態。
