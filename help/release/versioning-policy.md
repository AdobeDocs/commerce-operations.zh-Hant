---
title: 發行原則
description: 瞭解不同型別的Adobe Commerce版本，包括次要、修補程式、安全性修補程式、功能、Hotfix、個別修補程式和自訂修補程式。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Adobe Commerce發行原則

Adobe Commerce使用 [語意版本設定](https://semver.org/) 在個別模組層級(例如 `magento/framework 101.1.1`)，但不適用於行銷版本號碼。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH版本**—2.4.5
   - **安全性修補程式發行版本**—2.4.5-p1
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
- 在例外情況下，可能會發行重大變更或額外的修補程式或Hotfix，以解決安全性或法規遵循問題，以及影響重大的品質問題。 在模組層級，這些主要是PATCH層級的變更；有時是次要層級的變更。

### 安全性修補程式發行版本

{{$include /help/_includes/security-patch-release-overview.md}}

## BETA修補程式版本

Adobe Commerce功能正式發行前的版本已開放給所有Adobe Commerce客戶和Adobe合作夥伴使用。 它可讓您在「一般可用性」之前有額外時間檢閱程式碼和受影響的元件。

Beta版可能包含瑕疵，並「按原樣」提供，不含任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式)Beta版。 建議客戶謹慎使用，切勿依賴Beta版及/或任何隨附檔案或資料的正確運作或效能。 因此，任何使用測試版都是由客戶自行承擔風險。

## 擴充性、基礎結構和服務版本

包含新功能和功能更新的功能發行版本，這些更新以獨立服務的形式提供，與修補程式發行版本分開。 範例包括API Mesh和Eventing等擴充性技術、Product Recommendations和Live Search等SaaS產品、B2B和PWA Studio等獨立模組，以及我們的雲端託管服務和基礎結構的更新。

## Hotfix

Hotfix是包含高影響力安全性或品質修正的修補程式，例如影響許多商家的零日漏洞修正。 Adobe Commerce版本的Adobe發行hotfix仍受支援，並視需要受到關鍵安全性或品質問題的影響。 Hotfix會發佈至 [已知問題區段](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 我們的知識庫。 這些修正包含在下一個計畫的修補程式發行版本中。

>[!NOTE]
>
>Hotfix可能包含回溯不相容的變更。

## 個別修補程式

個別修補程式包含特定問題的低影響品質修正。 這些修正會套用至支援的Adobe Commerce次要版本。 Adobe會根據Adobe Commerce的需求，依照我們的 [軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>個別修補程式不包含回溯不相容的變更。

## 自訂修補程式

由非Adobe人員建立，用於修正問題或因各種原因修改Adobe Commerce程式碼。 自訂修補程式是透過 [品質修補工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## 相關主題

- [版本設定](https://developer.adobe.com/commerce/php/development/versioning/)
- [即將發行的版本](schedule.md)
- [軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
