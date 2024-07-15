---
title: 效能最佳化
description: 瞭解效能最佳化的所有資訊，以及檢閱Adobe Commerce實作效能所需的步驟。
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 效能最佳化

效能是一個大主題。 當使用者遇到緩慢或無回應的網站時，它會影響轉換。 建議您遵循下列步驟，在雲端基礎結構實施上最佳化Adobe Commerce的效能：

- 評估問題
- 測量績效
- 找出系統效能提升的關鍵部分
- 修改系統部分以移除瓶頸
- 測量修改後的效能
- 如果情況更好，請採用或回覆

## 典型的效能問題

緩慢體驗的影響通常由兩個指標定義，每個因素都可能由於多種原因而產生。

高第一位元組時間(TTFB)通常被視為定義伺服器回應速度的指標。 時間不僅來自處理請求的原始程式碼執行，也可能受到以下因素的影響：

- DNS查閱
- 來自DB層的查詢速度緩慢
- 每個應用程式層的CPU時間
- 記憶體限制
- I/O等待可能會影響檔案讀取和寫入，透過通訊端連線服務
- 軟體設定(nginx、PHP、MySQL、Redis、Varnish)
- 網路頻寬
- 錯誤的快取
- 程式碼錯誤
- 錯誤的整合方法
- 協力廠商服務回應緩慢的相依性
- 無擴充能力的架構

載入緩慢的資源通常被視為定義靜態資源(CSS、JavaScript、影像、視訊、第三方Ajax呼叫回應)的指標。

Adobe Commerce可透過其功能與您的業務一同擴展：

![顯示Adobe Commerce可擴充功能的圖表](../../../assets/playbooks/scalable-capabilities.svg)

此外也有推動商業規模的關鍵因素，也會影響整體效能。

- 複雜的大型產品目錄
- 大量管理員
- 全域店面
- 高變數流量
- 展開接觸點
- 大量交易

針對針對規模而建置的分層式可快取架構，您可以使用此圖表作為參考。

![圖表顯示如何在可快取架構中使用Adobe Commerce GraphQL API](../../../assets/playbooks/cacheable-architecture.svg)
