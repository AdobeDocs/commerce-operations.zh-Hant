---
title: 最佳實務
description: 使用Adobe Systems推薦的最佳實踐來管理 Adobe Systems Commerce 專案的升級過程。
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# 升級最佳實踐

本主題列出了為管理升級 Adobe Systems Commerce 專案的複雜性而應執行的操作。 您的團隊應該從專案開發開始的那一刻起考慮升級，並持續到每個版本。 通過遵循這些最佳實踐，升級過程將更容易、更快、更便宜。

>[!TIP]
>
>這些建議基於最佳實踐，並得到了合作夥伴、商家、Adobe Systems專家和社群對其影響和有效性的證據的支援。

## 影響升級的因素為何？

了解決定升級複雜性的變數很重要。 您必須在每個專案的開頭考慮這些變數，而不只是升級的時間。 專案的開發是確保未來升級順暢且您能夠控制完成升級所需工作的關鍵。

升級Adobe Commerce執行個體的工作量取決於以下因素：

- **您如何建置您的網站？**&#x200B;自訂工作量和安裝的協力廠商模組數量嚴重影響升級的複雜性。 自定義工作和模組的品質可以確定升級是否順利。

- **您是否正在略過多個版本？**&#x200B;略過發行版本會使下一次升級更複雜，從後續版本升級會使程式更容易、成本更低。

- **您正在執行哪種型別的升級？**&#x200B;升級至次要版本（例如，從2.3.x至2.4.0）比更新程式版本（例如，從2.4.2至2.4.3）之間的升級更廣泛。 安全性升級是最容易實作的型別。

## 規劃升級的最佳實務

如果您處理的專案已投入生產，升級是您提升程式碼和自訂品質以及最佳化未來升級的機會。 您今天投資的時間就是長期節省的時間。

如果您為不同的商家管理多個網站，最佳方式是擁有您正常使用的主要功能與自訂內容的基礎例項。 使用此基礎執行個體作為您的測試網站，以完成升級，然後在其他人上執行此升級。 此做法可讓您靈活地重複使用不同客戶的自訂模組，並簡化跨專案的升級。

如果您的專案已上線，我們建議您執行稽核以判斷其品質，並瞭解如何改善專案以提高升級效率。

### 開發時考慮升級

從您開始處理專案的那一刻起，您就應該考慮未來升級將如何受到您目前工作的影響。 請務必遵循Adobe Commerce開發最佳實務，如以下所述：

- [開發最佳實踐](https://developer.adobe.com/commerce/php/best-practices/)
- [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/)

開始採用 Adobe Systems Commerce 擴充性平臺（如果尚未這樣做）。 該平台允許您高效地自定義流程、集成系統和部署新功能，同時保持 SaaS-按讚 的可升級性。 其功能包括：

- **UI**&#x200B;可擴充性。 使用 PWA Studio[&#128279;](https://developer.adobe.com/commerce/pwa-studio/) 獨立於後端和中間件擴展和發展您的店面。

- **API擴充性**。 使用[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/index.html)來擴充網頁API層，方法是演化圖形資料模型並直接從圖形層執行Lambda函式。

- **Adobe I/O中介軟體和服務**。 使用Adobe的中介軟體和以[Adobe I/O](https://www.adobe.io/)建置的應用程式連線套件，將您的系統與Adobe Commerce連線。 此外，您可以使用在Adobe I/O上執行的自身商業邏輯覆寫預設行為，以擴充核心平台功能。

### 規劃升級

隨著我們不斷擴展 Adobe Systems Commerce 的功能，您關鍵在最新的可用版本上進行開發並在專案計劃中定義升級策略。 如此一來，您就能夠確保安全、符合法規，並掌握最新的增強功能，讓您能更快速地增加銷售量、更有效地營運，並在現在和未來保持競爭優勢。

為了協助您規劃並編列升級預算，您應該監視我們的[發行排程](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/planning/schedule)。 提前在團隊的待辦專案中規劃升級任務。 目標是使用GA完成這項工作。

- 使用搶鮮版來瞭解每個新版本。 搶鮮版是「一般可用性」程式碼，可供Adobe Commerce商家和所有合作夥伴在正式可用性兩週前使用。 如果您有多個商店，請使用基礎商店中的發行前，並確認您的自訂模組和主題與其相容。

- 檢閱Adobe Commerce的[升級計畫檢查清單](https://support.magento.com/hc/en-us/articles/360057968951)，協助您規劃升級。

- 計劃年初的升級。 您必須預訂預算和資源才能完成每次升級。 請記住，升級工作可能因項目而異。 利用您的經驗和知識制定盡可能準確的計劃。

- 如果您的升級花費的精力比我們在此處描述的要多，我們建議您審核您的專案並調整您的環境以減少長期維護。

### 執行升級

升級應定期進行，並按照預先定義的預算進行。 我們建議在年初排程預先核准的升級，以確保已計畫並準時完成升級。

評估升級所需完成的工作：

- 請檢閱[發行說明](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/notes/overview)以瞭解新版本的範圍與影響。

- 使用[[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md)來識別在嘗試升級至較新版本之前，必須在自訂程式碼中修正的潛在問題。

- 如果您使用協力廠商擴充功能，請驗證其與您計畫升級至的目標版本的相容性。

### Post升級測試

測試是需要最多時間的升級階段。 因此，此程式應儘可能自動化。 使用核心測試工具可讓您受益。 [應用程式測試指南](https://developer.adobe.com/commerce/testing/guide/)提供詳細資料。

在移至生產環境之前，請使用測試環境來測試和驗證您的升級。

使用&#x200B;**維護頁面**。 預先準備此頁面可讓您與客戶通訊，通知他們背景正在進行工作。 此頁面應該會顯示幾分鐘，但如果發生問題，您可能需要更長的時間使用。 為您的維護頁面提供適當的內容和設計，即使您的商店無法使用，也能為使用者提供良好的體驗。
