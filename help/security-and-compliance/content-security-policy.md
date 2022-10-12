---
title: 內容安全性原則概述
description: 了解如何使用內容安全性原則改善Adobe Commerce或Magento Open Source存放區的安全態勢。
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# 內容安全性原則概述

內容安全性原則(CSP)可協助偵測及緩解跨網站指令碼(XSS)和相關資料插入攻擊，為Adobe Commerce和Magento Open Source安裝提供額外的防禦層級。 此常見的攻擊向量通過注入惡意內容來發揮作用，這些內容錯誤地聲稱源自網站。 惡意內容載入並執行後，可以啟動未授權的資料傳輸。

CSP提供一組標準化指示，告訴瀏覽器哪些內容資源可信、哪些應被封鎖。 CSP可使用謹慎定義的原則，限制瀏覽器內容，僅允許顯示白名單資源。

## 設定

為避免干擾網站操作，CSP可分階段實作。 CSP有兩種基本的操作模式： `report-only mode` 和 `restrict mode`. Adobe Commerce 2.3.5版標誌著我們實作的第一階段，並將CSP提供於 `report-only mode` 依預設。 在未來的版本中， `restrict mode` 預設為啟用，以提供其他現成可用的保護。

**僅報表模式**:系統會指示瀏覽器報告違反策略的情況，但不強制執行。 每當請求的資源違反CSP時，瀏覽器就會將產生的錯誤記錄到主控台。 然後，控制台日誌可用於調查每個違規的原因。

請務必在發生所有CSP錯誤時加以檢閱，並調整原則，直到將所有必要資源加入白名單為止。 切換至 `restrict mode` 不再發生錯誤時。 否則，設定不良的CSP可能會導致瀏覽器顯示空白頁面，並出現許多主控台錯誤。 正確設定的CSP可傳送白名單內容，而不會影響效能。

**限制模式**:系統會指示瀏覽器強制執行所有內容原則，並將發佈限制在白名單資源。 由於CSP是從伺服器（而非管理員）設定，因此大部分的商家都需要系統整合商或開發人員協助才能正確設定。 請參閱 [內容安全性原則](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 在 _商務PHP擴展_ 開發人員指南。

## 報表

依預設，CSP會將錯誤傳送至瀏覽器主控台，但可依HTTP要求設定以收集錯誤記錄。 此外，您還可以使用數種協力廠商服務來監控、收集和報告CSP違規情形。

[報表URI](https://report-uri.io/) 是可監控CSP違規情況，並在控制面板中顯示結果的服務。 每當發生CSP違反情形時，商家和開發人員都可使用服務接收報表。
