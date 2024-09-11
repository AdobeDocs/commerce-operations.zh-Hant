---
title: Beta發行版本
description: 瞭解Adobe Commerce測試版以及如何參與。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 050d5877fae4cb9caaee06598f4429ea8857b1d2
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# Adobe Commerce測試版

Adobe Commerce測試版計畫是商家存取發行前功能和程式碼、提供意見回饋，以及指引Adobe Commerce未來發展的方法。 測試版計畫有兩種型別：

- 公用Beta：公用Beta計畫可供所有Adobe Commerce客戶和合作夥伴使用
- Private Beta：私人Beta版計畫可能需要根據資格條件來核准才能參與

>[!IMPORTANT]
>
>Beta發行版本可能包含瑕疵，並依「現況」提供，並無任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式)Beta版。 建議客戶謹慎使用，切勿依賴測試版和/或任何隨附檔案或資料的正確運作或效能。 Beta版中的功能和API可能會有所變更，恕不另行通知。 因此，使用測試版完全由客戶自行承擔風險。

## 參與的優點

透過Adobe正在開發的功能，客戶和合作夥伴就能提供意見回饋、規劃產品開發，並準備在正式發行前採用新功能。

## 目前的Beta計畫

如需使用中Beta版計畫的清單，請參閱下列章節。

### Commerce (Private Beta)的Experience Manager Assets整合

適用於Commerce的Experience Manager Assets整合可讓您有效率地從Experience Manager Assets將大量產品影像管理和傳送至Adobe Commerce，而不需要耗費太多或完全不需要的營運工作。

主要功能：

- 隨插即用整合 — 開箱即用的Adobe可將Experience Manager Assets與Adobe Commerce整合，讓商家能夠專注於最重要的事項，同時降低營運成本並提高效率。

- 大規模個人化產品影像 — 使用Experience Manager Assets透過簡易的UI式編輯工具、使用Adobe Firefly的創成式內容建立和指派資產工作流程，為個人化Commerce體驗產生數百萬種產品變體，以確保品牌一致性。 只要您對資產滿意，即可使用Experience Manager Assets整合，將資產順暢地傳送至Commerce店面。

- 輕鬆上線 — 透過可設定的同步程式來簡化商家上線，該程式會啟用Experience Manager Assets存放庫和Commerce目錄之間的完整同步。

- 彈性比對策略 — 此整合包括根據產品SKU的預設資產比對演演算法，可在AEM Assets和Commerce之間同步影像，並可使用Adobe Developer App Builder進行擴充。 與您的解決方案合作夥伴合作，在整合的基礎上建立自訂資產比對策略，以容納任何資產管理存放庫結構。

若要參與測試版，請傳送電子郵件要求給[Shaun McCran](mailto:mccran@adobe.com)。

### IBM Sterling Order Management系統整合(Private Beta)

此IBM Sterling Order Management整合加速器可讓Adobe Commerce客戶開始使用IBM Sterling OMS支援的進階訂單管理功能。 有了這項整合，商家可以：

- 即時掌握客戶的存貨層次和準確的交貨日期。
- 根據可設定規則自動搜尋訂單，以便最佳化履行網路與存貨。
- 從單一儀表板跨管道的統一訂單檢視，讓您的支援團隊可以提供卓越的服務，並快速識別和處理例外狀況。
- 樣板化的退貨管理流程，可簡化退貨管理。

若要參與此測試版，請傳送電子郵件要求給[sbieber@adobe.com](mailto:sbieber@adobe.com)。

### 資料連線與Audience Activation(公開Beta)

擴展Adobe Commerce與Adobe Experience Platform之間的資料共用，以產生更強大的個人化體驗。 此功能可讓商家：

- 共用Commerce客戶設定檔
- 建立自訂屬性

若要參與此測試版，請傳送電子郵件要求給[DataConnection@adobe.com](mailto:DataConnection@adobe.com)。

### Adobe Commerce Foundation (公用Beta)

每個Adobe Commerce Foundation測試版包含排程發行日期前提供給Adobe Commerce核心程式碼的所有變更，包括但不限於下列功能區域：

- 最新的安全性修正
- 效能改良
- GraphQL改良功能
- 一般品質錯誤修正
- 社群貢獻
- 支援與[Adobe Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)相容性所需的變更

#### 命名慣例和排程

Adobe通常會每年發佈兩次測試版修補程式。

Beta發行套件有`-betaX`尾碼。 例如，Adobe Commerce 2.4.7 Beta版套件會使用以下命名慣例：

- `2.4.7-beta1`
- `2.4.7-beta2`

如需即將發佈的公開測試版發行日期清單，請參閱[發行排程](schedule.md)。


#### Beta版本存取權

Adobe Commerce Beta版的發佈方式與任何其他Adobe Commerce修補程式版本相同： `https://repo.magento.com`上的Composer中繼套件。 原始程式碼可在[GitHub](https://github.com/magento/magento2)上取得。

如需詳細資訊，請參閱[撰寫器安裝快速入門](../installation/composer.md)。

#### 問題報告

Adobe不提供Beta版的標準Adobe支援服務。

若要提交與Beta版相關的意見反應，請依照[GitHub](https://github.com/magento/magento2)上的[一般問題報告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)操作。

我們的內部團隊將監控針對最新測試版報告的所有嚴重問題，並排定在GA發行日期之前要解決的優先順序。
