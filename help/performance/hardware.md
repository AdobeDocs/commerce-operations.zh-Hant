---
title: 硬體Recommendations
description: 檢閱與Adobe Commerce部署最佳效能相關的建議硬體清單。
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# 硬體建議

## CPU

[!DNL Commerce] Web節點會提供未快取或無法透過應用程式快取的所有請求。 一個CPU核心可提供大約兩個（有時最多四個） [!DNL Commerce] 有效地要求。 使用以下方程式來決定您需要處理所有傳入請求而不將其放入佇列中的網路節點/核心數：

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

如果您預期商店的負載會變更，您可以手動增加作用中銷售期間的Web節點/核心數量。 或者，可以使用自動縮放模型來自動延伸Web層。

## 記憶體

### PHP

根據您系統部署的方式，Magento有不同的PHP記憶體需求。  一般來說，如果您要設定單一伺服器存放區，建議您為2G設定PHP記憶體。  如果您使用管道部署來設定網站，建議在您的組建伺服器上使用2 GB，在網頁節點上使用1 GB。

案例和預期的PHP記憶體需求：

* 僅供店面頁面使用的Webnode：256 MB
* Webnode使用大型目錄為管理員頁面提供服務： 1 GB
* [!DNL Commerce] cron使用大型目錄索引網站：>256 MB (請參閱 [進階設定](../performance/advanced-setup.md) 以調整最佳效能。)
* [!DNL Commerce] 編譯和部署靜態資產：756 MB
* [!DNL Commerce] 效能工具組設定檔產生：大於1 GB PHP RAM，大於16 MB [!DNL MySQL] TMP_TABLE_SIZE與MAX_HEAP_TABLE_SIZE設定

### [!DNL MySQL]

此 [!DNL Commerce] 資料庫（以及任何其他資料庫）會受可用於儲存資料和索引的記憶體數量影響。 有效運用 [!DNL MySQL] 資料索引，可用的記憶體量至少應接近資料庫中儲存資料大小的一半。

### 快取

如果您要部署多個 [!DNL Commerce] 並使用Redis或 [!DNL Varnish] 對於您的快取，請記住以下原則：

* [!DNL Varnish] 全頁快取記憶體失效有效，建議配置足夠的記憶體至 [!DNL Varnish] 將您最常用的頁面儲存在記憶體中
* 工作階段快取是為Redis個別執行個體設定的良好候選專案。  此快取型別的記憶體設定應考慮網站的購物車丟棄策略，以及工作階段預計要在快取中保留多久
* Redis應配置足夠的記憶體，以保留記憶體中的所有其他快取，達到最佳效能。  區塊快取將是決定要設定的記憶體數量的關鍵因素。  區塊快取會隨著網站頁數的增加而成長（sku數x商店檢視數）

## 網路頻寬

充足的網路頻寬是Web節點、資料庫、快取/工作階段伺服器和其他服務之間資料交換的關鍵需求之一。 因為 [!DNL Commerce] 有效利用快取以獲得高效能，您的系統可主動與Redis等快取伺服器交換資料。 如果Redis位於遠端伺服器上，您必須在Web節點和快取伺服器之間提供足夠的網路通道，以防止讀取/寫入作業出現瓶頸。
