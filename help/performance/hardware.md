---
title: 硬體Recommendations
description: 檢閱與Adobe Commerce和Magento Open Source部署最佳效能相關的建議硬體清單。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# 硬體建議

## CPU

[!DNL Commerce] 網路節點會提供所有未快取或無法透過應用程式快取的請求。 一個CPU核心可提供約2個（有時最多4個） [!DNL Commerce] 請求。 使用以下公式可確定處理所有傳入請求而不將其放入隊列所需的Web節點/核心數：

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

如果您預期某商店的負載會改變，則可以手動增加活動銷售期間的Web節點/核心數量。 或者，自動縮放模型可用於自動延伸網頁層。

## 記憶體

### PHP

Magento的PHP記憶體需求因系統部署方式而異。  通常，如果要設定單個伺服器儲存，建議為2G配置PHP記憶體。  如果您使用管道部署來設定網站，建議您在組建伺服器上配置2 GB和Web節點配置1 GB。

方案和預期的PHP記憶體要求：

* 僅在前面提供服務的Web節點：256 MB
* 為具有大目錄的管理頁面提供服務的網站節點：1 GB
* [!DNL Commerce] cron為具有大目錄的網站建立索引：>256 MB(請參閱 [進階設定](../performance/advanced-setup.md) 調整以獲得最佳效能。)
* [!DNL Commerce] 編譯和部署靜態資產：756兆位元組
* [!DNL Commerce] 效能工具包配置檔案生成：>1 GB PHP RAM,>16 MB [!DNL MySQL] TMP_TABLE_SIZE和MAX_HEAP_TABLE_SIZE設定

### [!DNL MySQL]

此 [!DNL Commerce] 資料庫（以及任何其他資料庫）對可用於儲存資料和索引的記憶體量非常敏感。 有效利用 [!DNL MySQL] 資料索引，可用記憶體量至少應接近資料庫中儲存資料的一半大小。

### 快取

如果要部署多個 [!DNL Commerce] 和使用Redis或 [!DNL Varnish] 對於您的快取，請牢記以下原則：

* [!DNL Varnish] 全頁快取記憶體失效有效，建議分配足夠的記憶體 [!DNL Varnish] 記住最受歡迎的頁面
* 工作階段快取是為Redis的另一個例項進行配置的理想候選項。  此快取類型的記憶體配置應考慮網站的購物車放棄策略，以及工作階段預計會保留在快取中的時間
* Redis應分配足夠的記憶體來將所有其他快取保存在記憶體中，以獲得最佳效能。  塊快取將是決定要配置的記憶體量的關鍵因素。  區塊快取會隨著網站上的頁面數（sku數x儲存檢視數）而增加

## 網路頻寬

足夠的網路頻寬是Web節點、資料庫、快取/會話伺服器和其他服務之間資料交換的關鍵要求之一。 因為 [!DNL Commerce] 有效利用快取實現高效能，您的系統可以主動與快取伺服器（如Redis）交換資料。 如果Redis位於遠程伺服器上，則必須在Web節點和快取伺服器之間提供足夠的網路通道，以防止讀/寫操作出現瓶頸。
