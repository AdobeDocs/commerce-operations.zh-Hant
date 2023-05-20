---
title: 硬體Recommendations
description: 查看與Adobe Commerce和Magento Open Source部署的最佳效能相關的建議硬體清單。
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# 硬體建議

## CPU

[!DNL Commerce] Web節點為未快取或無法通過應用程式快取的所有請求提供服務。 一個CPU內核可以運行兩個（有時最多4個） [!DNL Commerce] 請求。 使用以下公式來確定處理所有傳入請求而不將它們放入隊列所需的Web節點/內核數：

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

如果您期望商店的負載發生變化，則可以手動增加活動銷售期間的Web節點/核心數。 或者，自動縮放模型可用於自動擴展網層。

## 記憶體

### 菲律賓比索

Magento的PHP記憶體要求根據系統的部署方式而有所不同。  通常，如果要設定單個伺服器儲存，建議為2G配置PHP記憶體。  如果您正在使用管道部署設定站點，建議在生成伺服器上使用2 GB的容量，在Web節點上使用1 GB的容量。

方案和預期的PHP記憶體要求：

* 僅提供儲存前頁的Web節點：256 MB
* 為具有大目錄的管理頁提供服務的Web節點：1 GB
* [!DNL Commerce] cron索引具有大目錄的站點：>256 MB(請參閱 [高級設定](../performance/advanced-setup.md) 以調整最佳效能。)
* [!DNL Commerce] 編譯和部署靜態資產：756 MB
* [!DNL Commerce] 效能工具包配置檔案生成：>1 GB PHP RAM,>16 MB [!DNL MySQL] TMP_TABLE_SIZE &amp;MAX_HEAP_TABLE_SIZE設定

### [!DNL MySQL]

的 [!DNL Commerce] 資料庫（以及任何其他資料庫）對用於儲存資料和索引的可用記憶體量非常敏感。 有效利用 [!DNL MySQL] 資料索引，可用記憶體量至少應接近資料庫中儲存資料大小的一半。

### 快取

如果要部署多個 [!DNL Commerce] 然後使用Redis或 [!DNL Varnish] 對於快取，請牢記以下原則：

* [!DNL Varnish] 全頁快取記憶體無效，建議分配足夠的記憶體 [!DNL Varnish] 保存最常用的頁面
* 會話快取是為Redis的單獨實例配置的好候選。  此快取類型的記憶體配置應考慮站點的購物車放棄策略以及會話在快取中應保留多長時間
* Redis應分配足夠的記憶體以將所有其他快取保存在記憶體中，以獲得最佳效能。  塊快取將是決定要配置的記憶體量的關鍵因素。  塊快取相對於站點上的頁數增長（skus數x儲存視圖數）

## 網路頻寬

足夠的網路頻寬是Web節點、資料庫、快取/會話伺服器和其他服務之間資料交換的關鍵要求之一。 因為 [!DNL Commerce] 有效地利用快取實現高效能，您的系統可以主動與快取伺服器（如Redis）交換資料。 如果Redis位於遠程伺服器上，則必須在Web節點和快取伺服器之間提供足夠的網路通道，以防止讀/寫操作出現瓶頸。
