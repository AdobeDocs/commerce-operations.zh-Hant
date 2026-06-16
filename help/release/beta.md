---
title: Beta發行版本
description: 瞭解Adobe Commerce測試版以及如何參與。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"
source-git-commit: bf0f269900468870a1da7b5360548d49e009097c
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 0%

---

# Adobe Commerce測試版

適用於[Adobe Commerce產品解決方案](https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions)的Beta方案是商家存取發行前功能與程式碼、提供意見回饋，以及引導Adobe Commerce未來的方法。 測試版計畫有兩種型別：

- 公用Beta：公用Beta計畫可供所有Adobe Commerce客戶和合作夥伴使用
- Private Beta：私人Beta版計畫可能需要根據資格條件來核准才能參與

>[!IMPORTANT]
>
>**法律免責宣告**<br/>
>Beta發行版本包含發行前功能及程式碼，其中可能包含瑕疵，並依「現況」提供，無任何保固。Adobe自行決定是否將Beta版正式發佈。Adobe沒有義務維護、更正、更新、變更、修改、支援（透過Adobe支援服務或其他方式），或於任何特定日期前提供此類Beta版。Beta版正式發行時，可能會受其他條款與條件的約束，包括適用的費用。Beta發行版本可能會有所變更，恕不另行通知，包括停止發行。建議客戶謹慎使用，並且切勿依賴Beta版的不中斷或不錯誤功能或效能。 因此，使用測試版完全由客戶自行承擔風險。

## 參與的優點

搶先使用Adobe正在開發的功能，讓客戶和合作夥伴能提供意見回饋、規劃產品開發，以及在正式發行前準備採用新功能。

## 目前的Beta計畫

如需使用中Beta版計畫的清單，請參閱下列章節。

### 搜尋比對和排名(Private Beta)

Adobe正在改善產品探索如何在[!DNL Adobe Commerce]和[!DNL Adobe Commerce Optimizer]上為[!DNL Live Search]的搜尋結果排名。 更新會將&#x200B;**精確和接近的字詞比對**&#x200B;優先排序，然後比對&#x200B;**所有查詢詞出現在相同可搜尋屬性**&#x200B;中的位置，最後&#x200B;**跨欄位**&#x200B;比對（包括支援自動完成樣式建議的行為）。 這種分層模型可協助高意圖查詢先呈現最相關的產品，同時仍傳回有用的替代方案。

相同的關聯性模型會與&#x200B;**搜尋權重**、**智慧型排名**、**同義字**&#x200B;和&#x200B;**銷售規則** （圖釘、提升、埋藏）互動。 德文店面可針對複合字詞使用&#x200B;**解組合**，採用相同的整體優先順序方法。

**主要優點**

- 更強大的提升功能，可精確和近似地比對片語（包括標準化形式，例如單數與複數）。
- 當所有查詢字詞一起出現在一個可搜尋欄位中時排名較高。
- 在查詢時，更明確地期望權重、智慧型排名和手動規則如何結合。
- 有關在變更後驗證高值查詢和調校提升規則的指南。

深入瞭解[Adobe Commerce Optimizer (SaaS)](https://experienceleague.adobe.com/zh-hant/docs/commerce/optimizer/manage-results/search-relevance-matching)和[即時搜尋(PaaS)](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-admin/search-relevance-matching)中的搜尋比對和排名策略。

若要要求此私人測試版的邀請，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。 Adobe團隊會採取後續步驟和資格要求來回應。

### 建議價格篩選器（公用Beta） {#recommendation-price-filters-public-beta}

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

[!DNL Adobe Commerce Optimizer]將&#x200B;**價格篩選器**&#x200B;新增至「產品建議」，這樣當您建立或編輯建議單位時，就可以根據價格包含或排除建議產品。 篩選器會使用店面&#x200B;**使用中價格簿**&#x200B;中每個產品的&#x200B;**最終計算價格**，包括該價格簿中的折扣和促銷（不單單是定價）。 價格規則會精簡候選者集；它們不會重新排名產品。

您可以使用商店的基本貨幣來定義具有固定最小值和最大值的&#x200B;**靜態**&#x200B;範圍，或在產品詳細資料頁面上定義&#x200B;**動態**&#x200B;規則，這些規則會使用小於或等於、大於或等於等運運算元，或在錨價的值或百分比範圍內，將建議的產品與目前檢視的&#x200B;**產品**&#x200B;進行比較。 動態篩選器適用於在產品內容中執行的SKU相關建議型別（例如，*已檢視此專案、已檢視專案*&#x200B;及類似專案&#x200B;*）。*

**主要優點**

- 在&#x200B;**篩選產品**&#x200B;步驟中使用包含和排除規則，依價格包含或排除建議適用者。
- 針對固定的銷售目標（例如預算友善的附加元件或優質追加銷售），使用靜態價格區間。
- 使用產品詳細資料頁面上的動態價格規則，可針對檢視的產品，顯示可比價格範圍內的替代方案。
- 讓篩選與購物者看到的價格保持一致，這是用於篩選和顯示的作用中價格簿的相同最終價格。

若要深入瞭解，請參閱商家指南中的[建議篩選器 — 價格](https://experienceleague.adobe.com/zh-hant/docs/commerce/optimizer/merchandising/recommendations/filters#price)以及店面下拉式指南中的[產品建議設定](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/?lang=zh-Hant)。

若要在使用此測試版功能時分享您的意見，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### 雲端自動化修補服務(Private Beta)

僅[!BADGE 個PaaS]{type=Informative url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"}

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)會自動在雲端基礎結構[&#128279;](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/overview)環境中將隔離的安全性修補程式套用至您的Adobe Commerce。

在2025年10月，Cloud Automation Patching Service的測試版將新增至[全網站分析工具儀表板](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard)。 此服務透過簡化的修補工作流程支援Commerce專案管理員，包括：

- 自動安裝修補程式
- 復原復原
- 部署後驗證。

此服務可確保您以最少的手動工作量和風險，維持安全、穩定和更新的環境。

Beta版包含下列功能：

- **自動安裝修補程式**：簡化並自動修補各環境的重要弱點。
- **將風險降至最低**：使用部署後健康狀態檢查與回覆功能來防止網站中斷。

>[!NOTE]
>
>由於Cloud Automation修補服務會自動套用隔離的安全性修補程式，因此您必須擁有[貢獻者或專案管理員角色](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/project/user-access)才能使用它。

若要參與此測試版，請完成並提交[Cloud Automation Patching Service - Beta登錄檔單](https://forms.office.com/r/3Wfxj5nPdB)。

### 商家生產力AI助理（公用Beta）

「商戶生產力AI助理」是內嵌於Adobe Commerce管理員中的對話式介面，可協助商戶完成日常工作並使用自然語言依需求存取業務深入分析。 它可讓商家直接在其現有工作流程中管理促銷活動、更新產品目錄資訊以及擷取營運資料，例如最近的訂單或有效的促銷活動。 助理也提供內容感知指引，協助商家更有效率地導覽及使用管理員。

**主要優點**

- 使用自然語言指示，自動處理常見的銷售工作，包括促銷活動建立和目錄中繼資料更新。
- 直接在管理工作流程中存取內容協助和指引。
- 依需求查詢即時商店資料 — 例如，擷取最後10份訂單、檢視目前有效的促銷活動或檢查存貨狀態。
- 減少重複性的管理任務所花費的時間，讓商家得以專注於策略與成長。

若要參與此測試版，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### Adobe Commerce基礎（公開Alpha/Beta）

僅[!BADGE 個PaaS]{type=Informative url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"}

每個Adobe Commerce Foundation Alpha和Beta版都包含依排程發行日期傳送至Adobe Commerce核心程式碼的所有變更，包括但不限於下列功能區域：

- 最新的安全性修正
- 效能改良
- GraphQL改良功能
- 一般品質錯誤修正
- 社群貢獻
- 支援與[Adobe Commerce服務](https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/home)相容性所需的變更

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

若要提交與Alpha和Beta版相關的意見反應，請依照[GitHub](https://github.com/magento/magento2)上的[一般問題報告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)操作。

Adobe會監控針對最新Alpha或Beta版本報告的所有重大問題，並排定在GA發行日期之前要解決的優先順序。
