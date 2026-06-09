---
title: Beta發行版本
description: 瞭解Adobe Commerce測試版以及如何參與。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"
source-git-commit: 300ed6b9123701244042abccf70ff774ac05b0fa
workflow-type: tm+mt
source-wordcount: '1894'
ht-degree: 0%

---

# Adobe Commerce測試版

適用於[Adobe Commerce產品解決方案](https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions)的Beta方案是商家存取發行前功能與程式碼、提供意見回饋，以及引導Adobe Commerce未來的方法。 測試版計畫有兩種型別：

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

### 全域銷售規則和依目錄檢視（公開Beta）

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

Adobe Commerce Optimizer匯入了使用彈性範圍定義銷售規則的功能，讓商家可以跨所有目錄檢視套用規則，或將規則範圍設定為特定目錄檢視。 此功能針對經營多個店面、品牌或語言的商家，簡化銷售規則管理。 目錄檢視特定規則可讓商家在需要本地化或品牌特定體驗時，針對個別管道量身打造搜尋結果和銷售邏輯。 如果目錄檢視特定規則存在，則會覆寫該檢視的全域規則，提供精確的控制同時維持有效的組態管理。

**主要優點**

- 跨所有目錄檢視全域定義銷售規則。
- 需要本地化體驗時，覆寫特定目錄檢視的規則。
- 減少跨店面的設定重複。
- 改善多品牌和多語言商務實作的擴充能力。

此功能可改善銷售彈性和營運效率，協助商家大規模提供更相關的產品探索體驗。 若要深入瞭解，請參閱[銷售規則](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add)。

>[!NOTE]
>
>Beta參與者將需要重新建立任何現有的銷售規則，以善用新的目錄檢視範圍。

若要在使用此測試版功能時分享您的意見，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### 全域和每個目錄檢視的產品建議（公開Beta）

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

Adobe Commerce Optimizer引進對產品建議設定的增強控制，使商家能夠在所有目錄檢視中全域定義建議單位，或特別針對個別目錄檢視定義建議單位。

此功能可針對經營多個店面、品牌、地區或語言的企業簡化建議管理。 商家可以在全球範圍內建立建議單位一次，並將套用至所有目錄檢視，以確保跨管道的一致產品探索策略。 同時，目錄檢視特定的建議單位可讓商家在需要時為特定店面量身打造體驗。

店面參與事件和建議量度會在目錄檢視層級進行追蹤，針對不同店面的購物者行為提供更準確的深入分析。

**主要優點**

- 在所有目錄檢視中全域設定產品推薦單位。
- 針對當地語系化的店面體驗，建立目錄檢視專屬建議。
- 減少跨多品牌或多語言店面的重複設定。
- 透過目錄檢視追蹤的量度和事件，獲得更精確的深入分析。

此增強功能有助於商家提供更相關的產品探索體驗，同時簡化複雜商業環境中的建議管理。 若要深入瞭解，請參閱[建議](https://experienceleague.adobe.com/en/docs/commerce/optimizer/manage-results/recommendation-performance)

>[!NOTE]
>
>Beta參與者將需要重新建立任何現有的建議單位，以善用新的目錄檢視範圍。

若要在使用此測試版功能時分享您的意見，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### 類別銷售（公開Beta）

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

Adobe Commerce Optimizer類別銷售可協助商家控制產品在類別頁面上的訂購方式。 商戶在銷售規則工作流程中將行為設定為&#x200B;**類別規則**，以及[搜尋規則和預設產品清單規則](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/overview)。 每個規則都可以結合&#x200B;**智慧型排名** （適用的行為訊號和AI）、選擇性的&#x200B;**價格型排序**&#x200B;以及&#x200B;**手動**&#x200B;動作，例如釘選、提升和埋藏，讓團隊可以在沒有外部工具的情況下組織探索、執行促銷活動，以及將類別頁面與策略對齊。

**主要優點**

- 使用用於搜尋和預設清單的相同規則型工作流程，鎖定一或多個類別。
- 使用智慧型排名策略（例如，檢視次數最多、購買最多、加入購物車、個人化推薦、趨勢）加上可選價格排序的訂單類別清單。
- 當您需要精準放置時，在智慧型排名之上分層手動釘選、提升及隱藏動作。
- 當您的設定使用多個目錄檢視時，依目錄檢視來範圍規則。

若要深入瞭解，請參閱[類別銷售](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add)。

若要在使用此測試版功能時分享您的意見，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### 建議價格篩選器（公用Beta） {#recommendation-price-filters-public-beta}

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

[!DNL Adobe Commerce Optimizer]將&#x200B;**價格篩選器**&#x200B;新增至「產品建議」，這樣當您建立或編輯建議單位時，就可以根據價格包含或排除建議產品。 篩選器會使用店面&#x200B;**使用中價格簿**&#x200B;中每個產品的&#x200B;**最終計算價格**，包括該價格簿中的折扣和促銷（不單單是定價）。 價格規則會精簡候選者集；它們不會重新排名產品。

您可以使用商店的基本貨幣來定義具有固定最小值和最大值的&#x200B;**靜態**&#x200B;範圍，或在產品詳細資料頁面上定義&#x200B;**動態**&#x200B;規則，這些規則會使用小於或等於、大於或等於等運運算元，或在錨價的值或百分比範圍內，將建議的產品與目前檢視的&#x200B;**產品**&#x200B;進行比較。 動態篩選器適用於在產品內容中執行的SKU相關建議型別（例如，*已檢視此專案、已檢視專案*&#x200B;及類似專案&#x200B;*）。*

**主要優點**

- 在&#x200B;**篩選產品**&#x200B;步驟中使用包含和排除規則，依價格包含或排除建議適用者。
- 針對固定的銷售目標（例如預算友善的附加元件或優質追加銷售），使用靜態價格區間。
- 使用產品詳細資料頁面上的動態價格規則，可針對檢視的產品，顯示可比價格範圍內的替代方案。
- 讓篩選與購物者看到的價格保持一致，這是用於篩選和顯示的作用中價格簿的相同最終價格。

若要深入瞭解，請參閱商家指南中的[建議篩選器 — 價格](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/recommendations/filters#price)以及店面下拉式指南中的[產品建議設定](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/)。

若要在使用此測試版功能時分享您的意見，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### 雲端自動化修補服務(Private Beta)

僅[!BADGE 個PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"}

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)會自動在雲端基礎結構](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)環境中將隔離的安全性修補程式套用至您的[Adobe Commerce。

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

### 商家生產力AI助理（公用Beta）

「商戶生產力AI助理」是內嵌於Adobe Commerce管理員中的對話式介面，可協助商戶完成日常工作並使用自然語言依需求存取業務深入分析。 它可讓商家直接在其現有工作流程中管理促銷活動、更新產品目錄資訊以及擷取營運資料，例如最近的訂單或有效的促銷活動。 助理也提供內容感知指引，協助商家更有效率地導覽及使用管理員。

**主要優點**

- 使用自然語言指示，自動處理常見的銷售工作，包括促銷活動建立和目錄中繼資料更新。
- 直接在管理工作流程中存取內容協助和指引。
- 依需求查詢即時商店資料 — 例如，擷取最後10份訂單、檢視目前有效的促銷活動或檢查存貨狀態。
- 減少重複性的管理任務所花費的時間，讓商家得以專注於策略與成長。

若要參與此測試版，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### Adobe Commerce基礎（公開Alpha/Beta）

僅[!BADGE 個PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"}

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

若要提交與Alpha和Beta版相關的意見反應，請依照[GitHub](https://github.com/magento/magento2)上的[一般問題報告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)操作。

Adobe會監控針對最新Alpha或Beta版本報告的所有重大問題，並排定在GA發行日期之前要解決的優先順序。
