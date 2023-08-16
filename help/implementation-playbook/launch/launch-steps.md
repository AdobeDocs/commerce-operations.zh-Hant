---
title: 啟動步驟
description: 請使用啟動檢查清單，確保Adobe Commerce網站實施順暢。
exl-id: d7807b2f-85c0-4e3e-a473-c65dbec44d28
feature: Configuration, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# 啟動步驟

測試並完成啟動前檢查清單後，我們可以在轉換時開始啟動的最後步驟。 這些步驟包括輸入網站啟動（上線）票證、切換存取權，以及最後在商店上線時測試。

Adobe Commerce支援人員會透過程式與您合作，檢查狀態並幫助解決發生的任何問題。 應使用票證追蹤所有問題，以便最妥善地擷取所發生的情況以及問題的解決方式。 當您開始將更新的持續反複部署到已啟動商店時，可能會再次發生類似問題。 這些票證有助於查明問題並幫助調整部署任務。

- 將應用程式設定為基底URL
   - 將DNS切換至新站台
   - 存取您的DNS服務
   - 更新網域和主機名稱的A和CNAME記錄
   - 等候TTL時間過去並存取您的商店

- 在生產環境中完全測試
   - 驗證網站的所有功能
   - 驗證CDN快取
   - 驗證所有整合的協力廠商服務
   - 驗證所有協力廠商系統

- 如果有任何問題阻止上線，請聯絡Adobe Commerce熱線

![顯示啟動流程階段3的圖表](../../assets/playbooks/launch-steps-3.svg)
