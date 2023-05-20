---
title: 發佈策略
description: 瞭解不同類型的Adobe Commerce版本，包括次要版本、修補程式、安全修補程式、功能、修補程式、單個修補程式和自定義修補程式。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Adobe Commerce發佈政策

Adobe Commerce和Magento Open Source使用 [語義版本](https://semver.org/) 在單個模組級別(例如 `magento/framework 101.1.1`)，但不適用於市場營銷版本號。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH**—2.4.5
   - **SECURITY修補程式版本**—2.4.5-p1
      - 安全錯誤修復
      - 安全增強
- **BETA修補程式版本**—2.4.7-beta1
- **功能發佈**
- **修補程式**
- **單個修補程式**
- **自定義修補程式**

## 次要版本

以下准則適用於次要版本：

- 突破性改變是可能的；為Adobe Commerce2.2.x編寫的代碼可能不再適用於Adobe Commerce2.3.x。例如，次要版本可以引入對主要系統要求和依賴項（如PHP）的支援。
- 模組版本可能有所不同。 例如，某些模組更改在新修補程式中引入，而其他模組更改在次要發行版中引入。
- 次要版本可以包括一些新功能，這些功能可能需要您或您的解決方案合作夥伴在升級過程中進行額外工作，以確保相容性。
- 次要版本可以包括針對安全性和質量問題的修復。

## PATCH

修補程式版本主要側重於提供安全性、效能、合規性和高優先順序質量的修復，以幫助您的站點在其高峰時運行。

以下准則適用於修補程式版本：

- 最新支援的次發行版可獲得完整的功能質量修復和增強功能。
- 避免可能中斷擴展或代碼相容性的更改。 例如，為2.2.0版編寫的代碼仍應用於2.2.7版。
- 在例外情況下，可能會發佈中斷更改或附加補丁程式或熱修補程式，以解決安全或合規性問題以及高影響質量問題。 在模組層面上，這些大多是PATCH層面的變化；有時MINOR級別更改。

### SECURITY修補程式版本

**安全錯誤修復**:一種軟體代碼更改，它解決所識別的安全問題並在受影響的產品區域中提供預期結果。 這些修復程式通常向後相容。

**安全增強**:軟體改進或配置更改，以主動提高應用程式內的安全性。 這些安全增強功能有助於解決安全風險，這些風險會影響Adobe Commerce應用程式的安全態勢，但可能後退不相容。

使用安全修補程式版本，您無需應用完整修補程式版本中包含的其他質量修復和增強功能，就可以使站點更加安全。 安全修補程式版本後面附加「 — pN」，其中N是以1開頭的增量修補程式版本(例如2.3.5-p1)。 安全修補程式版本還可包括解決影響Adobe Commerce應用程式的關鍵問題所需的修補程式。

每個安全修補程式版本都基於先前的完整修補程式版本。 它包含來自先前修補程式版本的質量和安全修復程式以及在先前完整修補程式版本和安全修補程式版本之間建立的安全修復程式。

有關下載和應用安全修補程式的說明，請參見 [快速啟動安裝](../installation/composer.md#example---security-patch)。

## BETA修補程式版本

Adobe Commerce功能的預上市版本向所有Adobe Commerce客戶和Adobe夥伴公開。 它允許在「General Availability（一般可用性）」之前額外的時間來查看代碼和受影響的元件。

Beta版本可能包含缺陷，並提供「原樣」，不提供任何保證。 Adobe將沒有義務維護、更正、更新、更改、修改或以其他方式支援(通過Adobe支援服務或其他方式)測試版。 建議客戶謹慎行事，不要以任何方式依賴測試版和/或任何隨附文檔或資料的正確功能或效能。 因此，任何使用Beta版本都完全有客戶的風險。

## 功能發佈

功能版本包含作為獨立服務提供的新功能和功能更新，這些功能和更新與修補程式版本不同。 示例包括產品Recommendations和即時搜索等服務、PWA Studio和Inventory management(MSI)等獨立模組，以及我們的雲服務和基礎架構的更新。

## 修補程式

修補程式是包含高影響安全性或高質量修補程式的修補程式，如對零天漏洞的修補，這些漏洞會影響許多商家。 Adobe為Adobe Commerce版本發佈熱修復程式，這些修補程式仍然受到關鍵安全性或質量問題的支援和影響，如需要。 將修補程式發佈到 [「已知問題」部分](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 知識庫。 這些修復程式包含在下一個計畫的修補程式版本中。

>[!NOTE]
>
>修補程式可包含向後不相容的更改。

## 單個修補程式

單個修補程式包含針對特定問題的低影響質量修復。 這些修復程式應用於支援的次要版本的Adobe Commerce。 Adobe根據我們的要求，為Adobe Commerce發佈所需的單個修補程式 [軟體生命週期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

>[!NOTE]
>
>單個修補程式不包含向後不相容的更改。

## 自定義修補程式

由非Adobe人員建立，用於解決問題或出於各種原因修改Adobe Commerce代碼。 通過 [質量修補程式工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。

## 相關主題

- [版本控制](https://developer.adobe.com/commerce/php/development/versioning/)
- [即將發佈的版本](schedule.md)
- [軟體生命週期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
