---
title: 效能基準
description: 查看托管在Adobe雲基礎架構上的Adobe Commerce實施的效能基準結果。
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: eeb7146a8051e8692ebf974d65db75a4999cf2e6
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# 基準摘要

Adobe Commerce2.4.5效能基準結果反映了在Adobe Commerce實例上使用以下基礎架構和附加元件所衡量的效能。
- [Pro雲環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) 與 [擴展架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [Adobe CommerceB2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe CommerceInventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

沒有其他自定義項。

以下資訊匯總了基準結果，並提供了有關測試期間使用的環境和資料的資訊。

## 關鍵效能指標

下圖顯示了效能基準的Commerce儲存配置以及test結果中的關鍵效能度量。

![效能基準JMeter和生產基礎架構](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

基於模仿企業B2C組織的測試標準，該系統可以在高峰時間處理請求的通信量和訂單號，並且處於標準負載流。

### 效能亮點

- **訂單** — 處理了每分鐘3,481個訂單，同時將第99百分點的響應時間維持在2秒以下（99%的請求都在響應時間小於2秒的情況下得到了服務）。
- **頁面視圖** — 每小時處理200多萬頁面視圖，同時為第99百分點保留不到2秒的響應時間。
- **有效SKU** — 客戶概況包括2.42億種不同的價格變化(<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>25萬種產品。
- **GraphQL請求** — 系統將每分鐘擴展到10,500個GraphQL未快取的請求，同時為第99百分位將響應時間保持在不到2秒。
- **併發管理用戶** — 系統按比例擴展，支援500個併發管理員用戶，同時將第99百分點的響應時間保持在2秒以內。

## Test環境

通過對部署在具有擴展架構的Pro雲環境中的Adobe Commerce2.4.5實例進行測試，獲得效能基準結果。 該實例還安裝、配置和啟用了Adobe CommerceB2B、Inventory management和Adobe Stock整合模組。

已使用以下元件生成test配置檔案的效能測試資料： <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">效能工具包</a>。

效能測量基於客戶及業務用戶的模擬日常儲存活動。 這些值反映了每個案例接近最大的吞吐量，但並不反映獨特的業務模型，如私人銷售或快閃記憶體銷售。

- **LUMA店面**
   - 3000個併發用戶
   - 設定為30%的CDN快取命中率

      快取層的有效使用將增加每小時的頁面視圖數。

- **GraphQLAPI**
   - 250個併發線程
   - 設定為0% CDN快取命中率

      在GraphQL前面的快取層中，響應時間顯著提高。

- **管理網**
   - 500個併發用戶
   - 設定為0% CDN快取命中率

## Test環境規範

已使用針對Adobe Commerce實例運行的JMeter負載配置檔案完成負載測試。 在test過程中，使用了3個Web節點和3個服務節點。 以下影像詳細描述了JMeter和生產基礎架構的入口點。

![效能基準JMeter和生產基礎架構](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### 應用程式

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce2.4.5</a> 部署在雲基礎架構上，採用Pro體系結構。

### 基礎設施

對於效能基準，Adobe Commerce2.4.5部署在 [可擴展基礎架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) 具有以下容量。

- **Web節點規範**
   - vCPU 216（72 x 3節點）
   - 記憶體432 GiB（144 x 3節點）
   - 網路頻寬768 Gbps（256 x 3節點）
   - EBS頻寬57000 Mbps（19000 x 3節點）
   - 調配的儲存100 GB

- **服務節點規範**
   - vCPU 192（64 x 3節點）
   - 記憶體768 GiB（256 x 3節點）
   - 網路頻寬60 Gbps（20 x 3節點）
   - EBS頻寬40800 Mbps（13600 x 3節點）
   - 調配的儲存1100 GB
