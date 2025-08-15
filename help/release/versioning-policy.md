---
title: 發行原則
description: 瞭解不同型別的Adobe Commerce發行版本。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: f7b22089bcf88f6c881b0cbd4d7f77d795d9071b
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# Adobe Commerce發行原則

Adobe Commerce在個別模組層級（例如[）使用](https://semver.org/)語意版本設定`magento/framework 101.1.1`，但行銷版本編號不使用。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH版本**—2.4.8
   - **安全性修補程式版本**—2.4.8-p1
      - 安全性錯誤修正
      - 安全性增強功能
- **ALPHA修補程式版本**—2.4.8-alpha1
- **BETA修補程式版本**—2.4.8-beta1
- **擴充性、基礎結構和服務版本**
- **Hotfix**
- **個別修補程式**
- **自訂修補程式**

## 次要版本

下列指引適用於次要版本：

- 您可進行重大變更；針對Adobe Commerce 2.2.x編寫的程式碼可能無法再搭配Adobe Commerce 2.3.x使用。例如，次要發行版本可能會引入對主要系統需求和相依性的支援，例如PHP。
- 模組版本可能有所不同。 例如，新修補程式中會引進一些模組變更，而次要發行版本中則會引進其他模組變更。
- 次要發行版本可能包括新功能，在升級期間您可能需要或您的解決方案合作夥伴進行額外的工作，以確保相容性。
- 次要發行版本可能包括安全性和品質問題的修正。

## PATCH版本

修補程式發行主要著重於提供安全性、效能、法規遵循以及高優先順序的品質修正，協助您維持網站在尖峰時的效能。

下列准則適用於修補程式發行版本：

- 最新支援的次要版本獲得完整功能品質修正和增強功能。
- 避免進行可能破壞擴充功能或程式碼相容性的變更。 例如，針對2.2.0版編寫的程式碼仍應可在2.2.7版上運作。
- 在例外情況下，可能會發行重大變更或額外的修補程式或Hotfix，以解決安全性或法規遵循問題，以及影響重大的品質問題。 在模組層級，這些變更主要是PATCH層級；有時是次要層級。

### 安全性修補程式發行版本

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Alpha修補程式發行版本

Adobe Commerce功能的Beta前版本已開放所有Adobe Commerce客戶和Adobe合作夥伴使用。 Alpha版本旨在針對仍在積極開發中的功能提供早期意見反應和評估。 這些版本提供了在Beta和General Availability版本之前進行早期測試和整合規劃的機會。

Alpha發行版本可能不完整，且可能包含瑕疵。 產品依原樣提供，不含任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式) Alpha版本。 客戶不應依賴Alpha發行版本或任何隨附檔案或資料的正確運作或效能。 使用Alpha版本須完全由客戶自行承擔風險。

## Beta修補程式發行版本

Adobe Commerce功能正式發行前的版本已開放給所有Adobe Commerce客戶和Adobe合作夥伴使用。 它可讓您在「一般可用性」之前有額外時間檢閱程式碼和受影響的元件。

Beta發行版本可能包含瑕疵，並依「現況」提供，並無任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式) Beta版本。 客戶不應依賴Beta發行版本或任何隨附檔案或資料的正確運作或效能。 因此，客戶自行承擔使用Beta發行版本所面對的風險。

## 功能、雲端基礎結構和擴充性版本

雲端基礎結構和功能發行包含新功能和功能更新，這些功能和更新以獨立服務的形式提供，與修補程式發行版本分開。 範例包括但不限於：

- 雲端託管服務和基礎結構的更新
- B2B
- SaaS產品（目錄服務、資料連線、產品建議和即時搜尋）
- 擴充性技術(Admin UI SDK、API Mesh、App Builder Starter Kit、Eventing和Webhooks)

## Hotfix

Hotfix是包含高影響力安全性或品質修正的修補程式，例如影響許多商家的零日漏洞修正。 Adobe會視需要發行支援Adobe Commerce版本的Hotfix，在這些版本發生重大安全性或品質問題時提供支援。 Hotfix已發佈至知識庫的[已知問題區段](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)。 這些修正包含在下一個計畫的修補程式發行版本中。

>[!NOTE]
>
>Hotfix可能包含與回溯不相容的變更。

## 個別修補程式

個別修補程式包含特定問題的低影響品質修正。 這些修正會套用至支援的Adobe Commerce次要版本。 根據[軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)，Adobe會根據Adobe Commerce的需要發行個別修補程式。

>[!NOTE]
>
>個別修補程式不包含與回溯不相容的變更。

## 隔離的修補程式

隔離的修補程式是獨立於完整安全性修補程式發行的安全性修正，可加快實作。 每個獨立的修補程式都會解決特定的安全性問題，並包含在最新或即將推出的完整安全性修補程式中。 有關問題的詳細資訊可在相關安全性公告中提供，該公告連結至知識庫(KB)文章，其中包含修正詳細資訊、如何套用修正程式以及其他資訊。

請參閱[安全性中心](https://helpx.adobe.com/tw/security/products/magento.html)以尋找Adobe Commerce的最新安全性更新。

## 自訂修補程式

由非Adobe人員建立，用於修正問題或因各種原因修改Adobe Commerce程式碼。 自訂修補程式是透過[品質修補程式工具](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)提供。
