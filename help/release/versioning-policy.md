---
title: 發行原則
description: 了解不同類型的Adobe Commerce版本，包括次要、修補程式、安全性修補程式、功能、Hotfix、個別修補程式和自訂修補程式。
source-git-commit: 1705e930b7ab0176722c4f911dd06f448f992373
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---


# Adobe Commerce發行原則

Adobe Commerce和Magento Open Source使用 [語義版本化](https://semver.org/) 在個別模組層級(例如 `magento/framework 101.1.1`)，但不適用於行銷版本號碼。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH發行**—2.4.5
   - **SECURITY修補程式發行**—2.4.5-p1
      - 安全性錯誤修正
      - 安全性增強功能
- **測試版修補程式發行**—2.4.7-beta1
- **功能發行**
- **Hotfix**
- **個別修補程式**
- **自訂修補程式**

## 次要版本

下列准則適用於次要版本：

- 可能發生重大變更；為Adobe Commerce 2.2.x撰寫的程式碼不再適用於Adobe Commerce 2.3.x。例如，次要版本可引入對主要系統需求和依賴項（如PHP）的支援。
- 模組版本可能有所不同。 例如，某些模組變更會引入新修補程式中，而其他則會引入次要版本中。
- 次要版本可能包含新功能，這些新功能可能需要您或您的解決方案合作夥伴在升級期間進行額外工作，以確保相容性。
- 次要版本可包含安全性和品質問題的修正。

## PATCH發行

修補程式版本主要側重於提供安全性、效能、合規性和高優先順序質量修正，以幫助您的站點在高峰時保持運行。

以下准則適用於修補程式版本：

- 最新支援的次要版本會收到完整的功能品質修正和增強功能。
- 可以避免可能中斷擴充功能或程式碼相容性的變更。 例如，為2.2.0版撰寫的程式碼仍應適用於2.2.7版。
- 在例外的情況下，可能會發佈中斷的更改或其他修補程式或修補程式，以解決安全性或合規性問題以及高影響質量問題。 在模組層面，這些主要是PATCH層面的變更；有時會進行微幅變更。

### SECURITY修補程式發行

**安全性錯誤修正**:解決已識別安全問題並在受影響的產品區域中提供預期結果的軟體代碼變更。 這些修正通常向後相容。

**安全性增強功能**:軟體改進或配置更改，以主動提高應用程式內的安全性。 這些安全性增強功能有助於解決安全風險，這些風險會影響Adobe Commerce應用程式的安全態勢，但可能後向不相容。

使用安全修補程式版本，您無需應用完整修補程式版本中包含的其他品質修正和增強功能，即可確保網站的安全性。 安全修補程式版本會附加「 — pN」，其中N是以1開頭的增量修補程式版本（例如2.3.5-p1）。 安全性修補程式發行也可包含必要的Hotfix，以解決影響Adobe Commerce應用程式的重大問題。

每個安全補丁版本都基於以前的完整補丁版本。 它包含先前修補程式版本的品質和安全性修正，以及先前完整修補程式版本與安全性修補程式版本之間建立的安全性修正。

有關下載和應用安全修補程式的說明，請參見 [快速入門安裝](../installation/composer.md#example---security-patch).

## 測試版修補程式發行

Adobe Commerce功能的正式發行前皆已公開提供給所有Adobe Commerce客戶和Adobe合作夥伴。 它可讓您在正式發行前多花點時間檢閱程式碼和受影響的元件。

測試版可能包含缺陷，按「原樣」提供，不提供任何類型的保證。 Adobe沒有義務維護、更正、更新、更改、修改或其他支援(通過Adobe支援服務或其他)測試版。 建議客戶小心，不要依賴測試版本和/或任何隨附的檔案或資料的正確運作或效能。 因此，使用測試版本完全有客戶自行承擔的風險。

## 功能發行

功能版本包含除了修補程式版本以外，以獨立服務形式提供的新功能和功能更新。 例如，產品Recommendations和即時搜索等服務、獨立模組(如PWA Studio和Inventory management(MSI))，以及對雲服務和基礎架構的更新。

## Hotfix

Hotfix是包含高影響安全性或品質修正的修補程式，例如對影響許多商家的零日漏洞進行修正。 Adobe發行Adobe Commerce版本的Hotfix，這些版本仍受到重大安全性或品質問題的支援，並會視需要受到影響。 會將Hotfix發佈至 [已知問題區段](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 知識庫。 這些修正包含在下一個計畫的修補程式發行中。

>[!NOTE]
>
>Hotfix可包含不相容的後向變更。

## 個別修補程式

單個修補程式包含針對特定問題的低影響質量修正。 這些修正會套用至支援的次要版本Adobe Commerce。 Adobe會根據我們的 [軟體生命週期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>單個修補程式不包含向後不相容的更改。

## 自訂修補程式

由非Adobe人員建立，以因各種原因修正問題或修改Adobe Commerce程式碼。 自定義修補程式通過 [質量修補工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## 相關主題

- [版本設定](https://developer.adobe.com/commerce/php/development/versioning/)
- [即將發行的版本](schedule.md)
- [軟體生命週期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
