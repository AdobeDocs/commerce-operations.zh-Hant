---
title: 績效基準
description: 檢閱托管於Adobe Commerce雲端基礎架構之Adobe實作的效能基準結果。
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: 09a42dc68836b34eab2c9d90879b897729cd1b09
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# 基準摘要

Adobe Commerce 2.4.5效能基準結果反映部署了下列基礎架構和其他元件的Adobe Commerce執行個體所測量的效能。
- [Pro雲環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) with [縮放架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [適用於Adobe Commerce的B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe CommerceInventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

沒有其他自訂項目。

下列資訊會摘要基準結果，並提供測試期間所使用環境和資料的相關資訊。

## 關鍵效能量度

下圖顯示效能基準的商務儲存配置以及測試結果中的關鍵效能度量。

![效能基準JMeter和生產基礎架構](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

基於模擬企業B2C組織的測試標準，系統可以在標準負載流處理高峰時段處理請求的流量和訂單號。

### 效能重點

- **訂購** — 每分鐘處理3,481筆訂單，同時在第99個百分位數的回應時間維持在2秒以內（99%的要求服務時間少於2秒）。
- **頁面檢視** — 在第99個百分位數中，處理每小時超過200萬次頁面檢視，但回應時間仍少於2秒。
- **有效SKU** — 客戶概況包括2.42億種不同的價格變化(<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>)，用於250,000種產品。
- **GraphQL請求** — 系統縮放至每分鐘10,500個GraphQL未執行請求，同時在第99個百分位數中維持回應時間少於2秒。
- **同時管理員使用者** — 系統可調整規模，以支援500名同時執行的管理員使用者，同時在第99個百分位數的回應時間維持在2秒以內。

## 測試環境

針對部署在具有縮放架構的Pro雲環境中的Adobe Commerce 2.4.5執行個體進行測試，以取得效能基準結果。 執行個體也安裝、設定和啟用Adobe Commerce B2B、Inventory management和Adobe Stock整合模組。

已使用 <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">效能工具包</a>.

效能測量是根據針對客戶和商務使用者的模擬日常商店活動而得出。 這些值反映每個案例接近最大的吞吐量，但不反映獨特的業務模型，如私人銷售或快閃銷售。

- **LUMA店面**
   - 3000個併發用戶
   - 設為30%的CDN快取點擊率

      快取層的有效使用會增加每小時的頁面檢視次數。

- **GraphQL API**
   - 250個併發線程
   - 設為0%的CDN快取點擊率

      GraphQL前面的快取層可大幅改善回應時間。

- **管理網站**
   - 500名同時使用者
   - 設為0%的CDN快取點擊率

## 測試環境規格

已使用針對Adobe Commerce例項執行的JMeter載入設定檔完成載入測試。 在測試過程中，使用了3個Web節點和3個服務節點。 下面的映像詳細說明了JMeter和生產基礎架構的入口點。

![效能基準JMeter和生產基礎架構](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### 應用程式

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> 使用Pro架構部署在雲基礎架構上。

### 基礎設施

針對效能基準，已在 [可擴展的基礎結構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) 具有以下容量。

- **Web節點規範**
   - vCPU 216（72 x 3節點）
   - 記憶體432 GiB（144 x 3節點）
   - 網路頻寬768 Gbps（256 x 3節點）
   - 100 GB的已配置儲存

- **服務節點規格**
   - vCPU 192（64 x 3節點）
   - 記憶體768 GiB（256 x 3節點）
   - 網路頻寬60 Gbps（20 x 3節點）
   - EBS頻寬40800 Mbps(13600 x 3節點)
   - 1100 GB的已配置儲存
