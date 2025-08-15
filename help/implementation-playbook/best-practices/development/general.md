---
title: 一般開發最佳實務
description: 瞭解開發Adobe Commerce專案的一般最佳實務。
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Adobe Commerce的一般開發最佳實務

本主題說明健康Adobe Commerce開發流程的基準。 它描述了基本流程、編碼原則和應用程式設計原則，以指導開發人員。

>[!NOTE]
>
>Adobe技術架構師在涉及開發的參與中，會將這些最佳實務作為參考。

這些最佳實務是根據開發和提供Commerce專案的多年經驗所開發。 Adobe建議技術計畫遵循這些最佳實務，並改善現有流程和程式碼以符合這些最佳實務。

## 文字慣例

本主題的關鍵字「必須」、「不得要」、「必要」、「應得」、「不應」、「不應該」、「不應該」、「建議」、「可能」和「選用」將解譯為[RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119)中的說明。

## 程式

1. 在開始專案活動之前，必須同意已定義的專案方法。 只要有定義，可以是Scrum、Waterfall或任何其他方法或方法組合。
1. 在開發團隊可以使用版本控制系統的分支策略之前，不應開始開發。
1. 開發應該要等到開發團隊取得技術規格簽發、使用者劇本和使用案例簽發，以及測試案例簽核後才能開始。
1. 至少要等到開發和QA環境可供使用後，才能開始開發。
1. 專案特定需求是開發必須開始的需求，這些需求可能會記錄在&#x200B;_就緒的定義_&#x200B;中。
1. 登出應由獲授權登出專案交付專案的使用者端代表完成。
1. 在Agile專案方法中，簽核後可能會有其他需求。 這些需求應被視為新需求，並應據以擷取、建構和規劃。
1. 提交之前，所有開發都必須由開發人員進行功能測試。
1. 所有開發作業都應該先通過自動化測試，然後再提交程式碼審查。 這可在建立提取請求後設定為自動化程式。
1. 所有開發都必須先通過技術架構師或主要開發人員的手動程式碼稽核，才能提交以進行品質保證。
1. 所有開發作業都必須先通過品質保證，才能交付給使用者端。
1. 專案特定的傳送要求強制記錄在「完成的定義」中。

## 環境

1. 所有開發人員都應使用相同的IDE。 PhpStorm是Adobe Commerce開發的建議IDE。
1. 所有開發人員應該使用與（未來）生產伺服器上使用的相同技術棧疊來進行開發和測試。 此技術棧疊中的軟體版本必須與安裝在生產伺服器上的軟體主要和次要版本相符。 如需Adobe Commerce一般技術棧疊的詳細資訊，請參閱[系統需求](../../../installation/system-requirements.md)。
1. 系統管理員或技術架構師可能會為團隊提供集中維護的本機開發環境，以確保和促進平等和最新的本機環境。
1. 開發人員和QA工程師必須能夠存取QA環境的命令列、資料庫和記錄檔。 這可能需要VPN連線。

## 版本設定

模組版本必須遵守[Semantic Versioning 2.0.0標準](https://semver.org/)。
Adobe Commerce程式碼基底的相依性應該遵循[模組版本相依性准則](https://developer.adobe.com/commerce/php/development/versioning/dependencies/)。

## 修訂控制

認可必須伴隨有意義的認可訊息。

## 安全性

1. [不應使用不安全的函式](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/)。
1. 應該套用[XSS預防策略](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)。
1. [應該套用內容安全性原則](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)。
1. 新的Adobe Commerce執行個體應該會在尚未達到「安全性修正專案結束」日期的最新安全性版本上提供。 請參閱[Adobe Commerce軟體生命週期原則](../../../release/lifecycle-policy.md)。
