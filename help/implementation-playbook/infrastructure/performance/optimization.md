---
title: 效能優化
description: 瞭解有關效能優化的所有資訊以及檢查您的Adobe Commerce實施的效能所要採取的步驟。
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 效能優化

表演是一個大話題。 當用戶遇到慢速或無響應的站點時，它會影響轉換。 我們建議執行以下步驟來優化您的Adobe Commerce在雲基礎架構實施方面的效能：

- 評估問題
- 度量效能
- 確定對效能改進至關重要的系統部分
- 修改系統部分以消除瓶頸
- 測量修改後的效能
- 如果更好，就採用或恢復

## 典型效能問題

慢速體驗的影響通常由兩個指標來定義，每個因素都可能因噸位原因而引起。

高時間到第一位元組(TTFB)通常被視為定義伺服器響應速度的指示器。 此時間不僅來自處理請求的原始碼執行，還可能受以下因素的影響：

- DNS查找
- DB層查詢速度慢
- 每個應用層的CPU時間
- 記憶體限制
- I/O等待可能會影響檔案讀和寫，通過套接字連接服務
- 軟體設定（nginx、PHP、MySQL、Redis、清漆）
- 網路頻寬
- 快取錯誤
- 錯誤代碼
- 錯誤的整合方法
- 慢第三方服務響應的依賴性
- 無可擴充性的體系結構

慢速載入資源通常被視為定義靜態資源（CSS、JavaScript、影像、視頻、第三方Ajax調用響應）的指標。

Adobe Commerce可以通過其功能來擴展您的業務。

![顯示Adobe Commerce可擴展能力的圖表](../../../assets/playbooks/scalable-capabilities.svg)

推動商業規模的關鍵因素也影響著整體業績。

- 複雜和大型產品目錄
- 大量管理員
- 全球店面
- 高可變流量
- 擴展觸點
- 大量交易

對於為規模構建的分層和可快取體系結構，可以使用此圖作為參考。

![示出如何在可快取體系結構中使用Adobe CommerceGraphQL API的圖](../../../assets/playbooks/cacheable-architecture.svg)
