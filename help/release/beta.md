---
title: Beta發行版本
description: 瞭解Adobe Commerce測試版以及如何參與。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"
source-git-commit: 7265cb40541f3e5a1c416094b3759f9b750153cf
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 0%

---

# Adobe Commerce測試版

Adobe Commerce測試版計畫是商家存取發行前功能和程式碼、提供意見回饋，以及指引Adobe Commerce未來發展的方法。 測試版計畫有兩種型別：

- 公用Beta：公用Beta計畫可供所有Adobe Commerce客戶和合作夥伴使用
- Private Beta：私人Beta版計畫可能需要根據資格條件來核准才能參與

>[!IMPORTANT]
>
>**法律免責宣告**<br/>
>Beta發行版本包含發行前功能及程式碼，其中可能包含瑕疵，並依「現況」提供，並無任何保固。 Adobe自行決定是否將Beta版正式發佈。 Adobe沒有義務維護、更正、更新、變更、修改、支援（透過Adobe支援服務或其他方式），或於任何特定日期前提供此類Beta版。 Beta版正式發行時，可能會受其他條款與條件的約束，包括適用的費用。 Beta發行版本可能會有所變更，恕不另行通知，包括停止發行。 建議客戶謹慎使用，並且切勿依賴Beta版的不中斷或不錯誤功能或效能。  因此，使用測試版完全由客戶自行承擔風險。

## 參與的優點

搶先使用Adobe正在開發的功能，讓客戶和合作夥伴能提供意見回饋、規劃產品開發，以及在正式發行前準備採用新功能。

## 目前的Beta計畫

如需使用中Beta版計畫的清單，請參閱下列章節。

### 全域銷售規則和依目錄檢視（公開Beta）

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

Adobe Commerce Optimizer匯入了使用彈性範圍定義銷售規則的功能，讓商家可以跨所有目錄檢視套用規則，或將規則範圍設定為特定目錄檢視。 此功能針對經營多個店面、品牌或語言的商家，簡化銷售規則管理。 目錄檢視特定規則可讓商家在需要本地化或品牌特定體驗時，針對個別管道量身打造搜尋結果和銷售邏輯。 如果目錄檢視特定規則存在，則會覆寫該檢視的全域規則，提供精確的控制同時維持有效的組態管理。

**主要優點**

- 跨所有目錄檢視全域定義銷售規則。
- 需要本地化體驗時，覆寫特定目錄檢視的規則。
- 減少跨店面的設定重複。
- 改善多品牌和多語言商務實作的擴充能力。

此功能可改善銷售彈性和營運效率，協助商家大規模提供更相關的產品探索體驗。 若要深入瞭解，請參閱[銷售規則](https://experienceleague.adobe.com/zh-hant/docs/commerce/optimizer/merchandising/rules/add)。

>[!NOTE]
>
>Beta參與者將需要重新建立任何現有的銷售規則，以善用新的目錄檢視範圍。

若要在使用此測試版功能時分享您的意見，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### 全域和每個目錄檢視的產品建議（公開Beta）

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

Adobe Commerce Optimizer引進對產品建議設定的增強控制，使商家能夠在所有目錄檢視中全域定義建議單位，或特別針對個別目錄檢視定義建議單位。

此功能可針對經營多個店面、品牌、地區或語言的企業簡化建議管理。 商家可以在全球範圍內建立建議單位一次，並將套用至所有目錄檢視，以確保跨管道的一致產品探索策略。 同時，目錄檢視特定的建議單位可讓商家在需要時為特定店面量身打造體驗。

店面參與事件和建議量度會在目錄檢視層級進行追蹤，針對不同店面的購物者行為提供更準確的深入分析。

**主要優點**

- 在所有目錄檢視中全域設定產品推薦單位。
- 針對當地語系化的店面體驗，建立目錄檢視專屬建議。
- 減少跨多品牌或多語言店面的重複設定。
- 透過目錄檢視追蹤的量度和事件，獲得更精確的深入分析。

此增強功能有助於商家提供更相關的產品探索體驗，同時簡化複雜商業環境中的建議管理。 若要深入瞭解，請參閱[建議](https://experienceleague.adobe.com/zh-hant/docs/commerce/optimizer/manage-results/recommendation-performance)

>[!NOTE]
>
>Beta參與者將需要重新建立任何現有的建議單位，以善用新的目錄檢視範圍。

若要在使用此測試版功能時分享您的意見，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### 語意搜尋：更聰明、內容感知的購物體驗(Private Beta)

僅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer專案（Adobe管理的SaaS基礎結構）。"}

語意搜尋是一種電子商務搜尋技術，可瞭解購物者查詢背後的&#x200B;*含義*，而不只是確切的字詞。 傳統關鍵字式搜尋在查詢包含不熟悉或拼錯的辭彙時通常失敗，不同於這種方式，AI支援的方法使用自然語言處理(NLP)和上下文來解譯意圖，以提供更相關的結果。

這項技術可解決傳統搜尋的主要限制：當購物者使用目錄中不存在之字詞時，便會出現零結果頁面。 透過使用AI支援的技術，它會將使用者查詢和產品資料對應到共用的語意空間。 例如，系統可辨識「跑鞋」和「慢跑運動鞋」是指相同型別的產品，啟用：

- 同義字辨識
- 內容關聯性
- 智慧型處理模糊、拼寫錯誤或複合查詢
- 瞭解自然的對話式語言

若要要求試用版計畫的邀請，請傳送電子郵件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。 Adobe團隊會採取後續步驟和資格要求來回應。

### 雲端自動化修補服務(Private Beta)

僅[!BADGE 個PaaS]{type=Informative url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端專案（Adobe管理的PaaS基礎結構）和內部部署專案的Adobe Commerce 。"}

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)會自動在雲端基礎結構[環境中將隔離的安全性修補程式套用至您的](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/overview)Adobe Commerce。

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

若要提交與Alpha和Beta版相關的意見反應，請依照[GitHub](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)上的[一般問題報告流程](https://github.com/magento/magento2)操作。

Adobe會監控針對最新Alpha或Beta版本報告的所有重大問題，並排定在GA發行日期之前要解決的優先順序。
