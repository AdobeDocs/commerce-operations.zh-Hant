---
title: Beta發行版本
description: 瞭解Adobe Commerce測試版以及如何參與。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 937e883e74d3a0b32a25dbdf3db0347398ef6ba3
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Adobe Commerce測試版

Adobe Commerce測試版計畫是商家存取發行前功能和程式碼、提供意見回饋，以及指引Adobe Commerce未來發展的方法。 測試版計畫有兩種型別：

- 公用Beta：公用Beta計畫可供所有Adobe Commerce客戶和合作夥伴使用
- Private Beta：私人Beta版計畫可能需要根據資格條件來核准才能參與

>[!IMPORTANT]
>
>Beta發行版本可能包含瑕疵，並依「現況」提供，並無任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式)測試版。 建議客戶謹慎使用，切勿依賴測試版和/或任何隨附檔案或資料的正確運作或效能。 Beta版中的功能和API可能會有所變更，恕不另行通知。 因此，使用測試版完全由客戶自行承擔風險。

## 參與的優點

搶先使用Adobe正在開發的功能，讓客戶和合作夥伴能提供意見回饋、規劃產品開發，以及在正式發行前準備採用新功能。

## 目前的Beta計畫

如需使用中Beta版計畫的清單，請參閱下列章節。

### 語意搜尋：更聰明、內容感知的購物體驗（私人測試版）

語意搜尋是一種電子商務搜尋技術，可瞭解購物者查詢背後的&#x200B;*含義*，而不只是確切的字詞。 傳統關鍵字式搜尋在查詢包含不熟悉或拼錯的辭彙時通常失敗，不同於這種方式，AI支援的方法使用自然語言處理(NLP)和上下文來解譯意圖，以提供更相關的結果。

這項技術可解決傳統搜尋的主要限制：當購物者使用目錄中不存在之字詞時，便會出現零結果頁面。 透過使用AI支援的技術，它會將使用者查詢和產品資料對應到共用的語意空間。 例如，系統可辨識「跑鞋」和「慢跑運動鞋」是指相同型別的產品，啟用：

- 同義字辨識
- 內容關聯性
- 智慧型處理模糊、拼寫錯誤或複合查詢
- 瞭解自然的對話式語言

若要要求試用版計畫的邀請，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。 Adobe團隊會採取後續步驟和資格要求來回應。

### 雲端自動化修補服務(Private Beta)

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)會自動在雲端基礎結構[環境中將隔離的安全性修補程式套用至您的](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)Adobe Commerce。

在2025年10月，Cloud Automation Patching Service的測試版將新增至[全網站分析工具儀表板](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard)。 此服務透過簡化的修補工作流程支援Commerce專案管理員，包括：

- 自動安裝修補程式
- 復原復原
- 部署後驗證。

此服務可確保您以最少的手動工作量和風險，維持安全、穩定和更新的環境。

Beta版包含下列功能：

- **自動安裝修補程式**：簡化並自動修補各環境的重要弱點。
- **將風險降至最低**：使用部署後健康狀態檢查與回覆功能來防止網站中斷。

>[!NOTE]
>
>由於Cloud Automation修補服務會自動套用隔離的安全性修補程式，因此您必須擁有[貢獻者或專案管理員角色](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access)才能使用它。

若要參與此測試版，請完成並提交[Cloud Automation Patching Service - Beta登錄檔單](https://forms.office.com/r/3Wfxj5nPdB)。

### IBM Sterling Order Management系統整合(Private Beta)

此IBM Sterling Order Management整合加速器可讓Adobe Commerce客戶開始使用IBM Sterling OMS支援的進階訂單管理功能。 有了這項整合，商家可以：

- 即時掌握客戶的存貨層次和準確的交貨日期。
- 根據可設定規則自動搜尋訂單，以便最佳化履行網路與存貨。
- 從單一儀表板跨管道的統一訂單檢視，讓您的支援團隊可以提供卓越的服務，並快速識別和處理例外狀況。
- 樣板化的退貨管理流程，可簡化退貨管理。

若要參與此測試版，請傳送電子郵件要求給[sbieber@adobe.com](mailto:sbieber@adobe.com)。

### Adobe Commerce基礎(公開Alpha/Beta)

每個Adobe Commerce Foundation Alpha和Beta版都包含依排程發行日期傳送至Adobe Commerce核心程式碼的所有變更，包括但不限於下列功能區域：

- 最新的安全性修正
- 效能改良
- GraphQL改良功能
- 一般品質錯誤修正
- 社群貢獻
- 支援與[Adobe Commerce服務](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)相容性所需的變更

#### 命名慣例和排程

Adobe通常每年會發行數次alpha和beta修補程式。

Alpha發行套件有`-alphaX`尾碼。 例如，Adobe Commerce 2.4.7 alpha發行套件會使用以下命名慣例：

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta發行套件有`-betaX`尾碼。 例如，Adobe Commerce 2.4.7 Beta版套件會使用以下命名慣例：

- `2.4.7-beta1`
- `2.4.7-beta2`

請參閱[發行排程](schedule.md)，以取得即將發行的公開Alpha和Beta版的發行日期清單。

#### 發行存取權

Adobe Commerce Alpha和Beta版本的發行方式與任何其他Adobe Commerce修補程式版本相同：做為`https://repo.magento.com`上的撰寫器中繼資料。 原始程式碼可在[GitHub](https://github.com/magento/magento2)上取得。

如需詳細資訊，請參閱[撰寫器安裝快速入門](../installation/composer.md)。

#### 問題報告

Adobe不提供alpha版和beta版的標準Adobe支援服務。

若要提交與Alpha和Beta版相關的意見反應，請依照[GitHub](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)上的[一般問題報告流程](https://github.com/magento/magento2)操作。

Adobe會監控針對最新Alpha或Beta版本報告的所有重大問題，並排定在GA發行日期之前要解決的優先順序。
