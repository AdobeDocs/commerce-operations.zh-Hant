---
title: 發行原則
description: 瞭解不同型別的Adobe Commerce版本，包括次要、修補程式、安全性修補程式、功能、Hotfix、個別修補程式和自訂修補程式。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Adobe Commerce發行原則

Adobe Commerce在個別模組層級（例如`magento/framework 101.1.1`）使用[語意版本設定](https://semver.org/)，但行銷版本編號不使用。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH版本**—2.4.5
   - **安全性修補程式版本**—2.4.5-p1
      - 安全性錯誤修正
      - 安全性增強功能
- **BETA修補程式版本**—2.4.7-beta2
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
- 在例外情況下，可能會發行重大變更或額外的修補程式或Hotfix，以解決安全性或法規遵循問題，以及影響重大的品質問題。 在模組層級，這些變更主要是PATCH層級的變更；有時候是次要層級的變更。

### 安全性修補程式發行版本

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Beta修補程式發行版本

Adobe Commerce功能正式發行前的版本已開放給所有Adobe Commerce客戶和Adobe合作夥伴使用。 它可讓您在「一般可用性」之前有額外時間檢閱程式碼和受影響的元件。

Beta發行版本可能包含瑕疵，並「按原樣」提供，並無任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式) Beta版本。 建議客戶謹慎使用，切勿依賴Beta發行版本及/或任何隨附檔案或資料的正確運作或效能。 因此，客戶自行承擔使用Beta發行版本的所有風險。

## 功能、雲端基礎結構和擴充性版本

雲端基礎結構和功能發行包含新功能和功能更新，這些功能和更新以獨立服務的形式提供，與修補程式發行版本分開。 範例包括我們的雲端託管服務和基礎架構、B2B、SaaS產品（目錄服務、資料連線、產品推薦和即時搜尋）以及擴充性技術（API Mesh、Integration Starter Kit和Eventing）的更新。

## Hotfix

Hotfix是包含高影響力安全性或品質修正的修補程式，例如影響許多商家的零日漏洞修正。 Adobe會視需要發行Adobe Commerce版本的hotfix，這些版本仍受到關鍵安全性或品質問題的支援和影響。 Hotfix已發佈至我們知識庫的[已知問題區段](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)。 這些修正包含在下一個計畫的修補程式發行版本中。

>[!NOTE]
>
>Hotfix可能包含與回溯不相容的變更。

## 個別修補程式

個別修補程式包含特定問題的低影響品質修正。 這些修正會套用至支援的Adobe Commerce次要版本。 Adobe會根據Adobe Commerce的[軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)，視需要發行個別修補程式。

>[!NOTE]
>
>個別修補程式不包含與回溯不相容的變更。

## 隔離的修補程式

包含最新僅限安全性修補程式中包含的獨立修正，或是即將發佈的僅限安全性修補程式，將另行發行以加速實作。

## 自訂修補程式

由非Adobe人員建立，用於修正問題或因各種原因修改Adobe Commerce程式碼。 自訂修補程式是透過[品質修補程式工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)提供。
