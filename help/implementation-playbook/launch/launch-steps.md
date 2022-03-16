---
title: 啟動步驟
description: 使用我們的發佈核對表確保順利實施Adobe Commerce站點。
exl-id: d7807b2f-85c0-4e3e-a473-c65dbec44d28
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# 啟動步驟

在測試並完成啟動前核對表後，我們可以開始在進行切換時啟動的最後步驟。 這些步驟包括輸入站點啟動（上線）票證、切斷訪問權限，最後在上線時測試您的商店。

Adobe Commerce支援人員在此過程中與您合作，檢查狀態並幫助解決任何問題。 應使用票證跟蹤所有問題，以最好地捕獲所發生的情況和解決方式。 當您開始將更新的連續迭代部署到已啟動的儲存時，可能會再次出現類似的問題。 這些票證有助於查明問題並幫助調整部署任務。

- 將應用程式配置為基URL
   - 將DNS切換到新站點
   - 訪問DNS服務
   - 更新域和主機名的A和CNAME記錄
   - 等待TTL時間傳遞並訪問儲存

- 完全test
   - 驗證網站的所有功能
   - 驗證CDN快取
   - 驗證所有整合第三方服務
   - 驗證所有第三方系統

- 如果出現任何問題，請聯繫Adobe Commerce熱線，以防阻止上線

![顯示啟動過程第3階段的圖](../../assets/playbooks/launch-steps-3.svg)
