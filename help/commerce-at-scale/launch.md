---
title: 效能測試提示
description: 瞭解如何設定KPI以啟動您的Adobe Commerce和Adobe Experience Manager解決方案。
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# 效能測試提示

要評估上述所有更改的有效性，應在投入使用之前和將來任何主要部署到您的生產環境之前，運行徹底的效能測試。 在規劃負載測試時，盡可能模擬真實的消費者流量非常重要。

該/CIF/Adobe Commerce站AEM點資源最密集的區域是無法快取的區域，如結帳過程和站點搜索。 靜態的、因此可快取的頁面瀏覽(如用於生成詳細資訊頁面(PDP)和產品清單頁面(PLP))通常佔到電子商務站點的大部分流量，因此test中的指令碼和場景應該反映這一情況來衡量平台的限制。

如果為您的負載test運行一個指令碼，該指令碼在站點中導航，而不需要在步驟間等待時間，而且每次都會完成簽出過程，則無法可靠地指示平台的限制，因為這不是現實場景。

定義KPI應是績效test計畫中的第一步：定義在初始test期間可以test的度量，然後在將來再次度量，並在站點生效後定期度量。 這允許您跟蹤站點的效能隨時間的變化 — 啟動前後。 要定義的示例KPI可以是：

- 平均響應時間 — 到第一個位元組或最後一個位元組的時間
- 延遲
- 位元組/秒（吞吐量）
- 錯誤率
- 每小時訂單
- 每小時的頁面視圖
- 每小時唯一用戶（併發購物者）

## Jmeter准則

在開發您的/CIF/Adobe Commerce負載測試時，應考慮以AEM下Jmeter高級指南：

- 將指令碼拆分為可配置的方案，這應包括：
   - 開啟首頁
   - 開啟類別頁(PLP)
   - 查看簡單產品(PDP) — 每個迭代內有2個環路
   - 查看可配置產品 — 每個迭代內有2個循環
      - 例如，將以上步驟設定為60%的流量
   - 產品搜索
      - 例如，將目錄搜索設定為37%的流量
   - 購物車和結帳
      - 例如，完成Cart和簽出指令碼部分的用戶應預設為行業標準電子商務站點轉換率約3%
      - 由於簽出流未快取且通常是資源密集型操作，因此，如果為完成訂單的人員數量與站點瀏覽器的數量設定一個不切實際的高數字，則您的站點可以處理的流量將產生不可靠的結果。
- 在每個test運行之前清除所有快取：
   - 應完AEM全清理調度程式快取
   - Adobe Commerce的快速和內部快取應被完全刷新和清理 — 這可以通過Adobe Commerce管理員的快取控制來完成。
- 在Jmetertest中包括斜坡時段：沒有設定坡道週期意味著不會逐漸增加流量，站點也沒有機會快取頁面中任何常訪問的頁面和元件。 在現實生活中，所有高峰流量都在同一時間到達完全未連接的站點時是不尋常的，因此Jmetertest指令碼中應包含一個斜坡期，以允許快取按照真實電子商務站點上的情況進行構建。
- 應使用迭代中每個步驟之間的「等待時間」 — 實際上，用戶在訪問過程中不會立即跳到站點上的下一頁 — 當用戶閱讀該頁並決定其下一個操作時，將會有等待時間。
- 將線程組設定為無限循環，但在設定的時間x（如60分鐘）內，將提供可重複的test，中值響應時間與以前的test運行相當。 這意味著在設定加速期間後，將存在併發運行的虛擬用戶的目標數量，並且這將在設定的循環時間內繼續。
- 應使用中值時間來改善/減少平均響應時間，而不是平均響應時間。 如果有幾個邊緣結果比其他結果花費的時間長得多，則這會扭曲此平均結果，但我們感興趣的是大多數用戶的最終用戶響應時間，這更適合中值度量。
- 預設情況下，在jmeter中不收集嵌入的資源（例如，在實際用戶訪問頁面時下載的JS、CSS和其他資源）。 可以啟用此功能，但只有您正在測試的域才能啟用 — 外部資源調用仍應被排除(例如，我們不希望包括來自外部托管服務的響應時間，如 谷歌分析代碼，因為我們對它們沒有控制權)。
- 應啟用HTTP快取管理器，這使Jmeter能夠在旅途中快取頁面元素，就像實際用戶在其自己的瀏覽器上瀏覽網站時快取頁面元素一樣。 在用戶通過網站的過程中，瀏覽器只下載一次相關的嵌入式資源，然後這些資源會被用戶的瀏覽器快取。 此外，如果同一用戶在其原始訪問後的某段時間返回站點，則這些資產仍可能是快取。
- 監聽程式應保留在實際負載test運行中（如「查看結果樹」和「聚合報告」）。 在非GUI即時負載test運行中包括這一點可能會影響Jmeter報告的效能結果，因為在即時test運行中使用資源來生成報告。 這些監聽程式已從test指令碼中刪除，將替換為JTL結果檔案，然後可以使用Jmeter的「報告儀表板」功能處理該檔案。
- 已評估的目標響應時間，以便儀表板報告的「Apdex得分」可以用作衡量test運行之間更改對效能的影響的快速方法。 Apdex評分是基於在可容忍的時間內能夠訪問網站的一定人數。 如果響應時間超過某個「令人沮喪」的量，這會降低分數。 可以使用「apdex_sefised_threshold」和「apdex_perabletd_threshold」參數設定時間。
- 設定目標「每小時訂單數」度量以向業務用戶顯示，而不是虛擬用戶計數。 「虛擬用戶」可能是一個複雜的話題，要理解test在現實生活中衡量的是什麼。 通過計算站點轉換率、每小時訂單數、用戶在站點上花費的平均時間以及每個頁面負載之間的思考時間，可以使用行業標準計算來根據要實現的每小時訂單數顯示不同的負載test方案。
- 最後，您的Jmetertest伺服器應運行在地理位置上靠近大多數用戶流量來自和雲基礎架構托管位置的伺服器上 — 希望這些伺服器將相同。
