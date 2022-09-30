---
title: 發行原則
description: 了解不同類型的Adobe Commerce版本，包括次要、修補程式、安全性修補程式、功能、Hotfix、個別修補程式和自訂修補程式。
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Adobe Commerce發行原則

Adobe Commerce和Magento Open Source使用 [語義版本化](https://semver.org/) 在個別模組層級(例如 `magento/framework 101.1.1`)，但不適用於行銷版本號碼。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH發行**—2.4.1
   - **SECURITY修補程式發行**—2.4.1-p1
      - 安全性錯誤修正
      - 安全性增強功能
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

## SECURITY修補程式發行

**安全性錯誤修正**:解決已識別安全問題並在受影響的產品區域中提供預期結果的軟體代碼變更。 這些修正通常向後相容。

**安全性增強功能**:軟體改進或配置更改，以主動提高應用程式內的安全性。 這些安全性增強功能有助於解決安全風險，這些風險會影響Adobe Commerce應用程式的安全態勢，但可能後向不相容。

使用安全修補程式版本，您無需應用每季度完整修補程式版本中包含的其他品質修正和增強功能，即可確保網站的安全性。 安全修補程式版本會附加「 — pN」，其中N是以1開頭的增量修補程式版本（例如2.3.5-p1）。 安全性修補程式發行也可包含必要的Hotfix，以解決影響Adobe Commerce應用程式的重大問題。

每個安全補丁版本都基於以前的完整補丁版本。 它包含先前修補程式版本的品質和安全性修正，以及先前完整修補程式版本與安全性修補程式版本之間建立的安全性修正。

隨著我們 [新的發行策略和更新的生命週期策略](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (9/16/2021)，我們的安全性修補程式版本是根據適用於最新支援的次要版本，還是仍支援的先前次要版本行的一部分而區別：

- **最新支援次要版本的安全性修補程式發行**:

   - 最新支援次要版本(目前為Adobe Commerce 2.4)的安全性修補程式版本包括：

      - 自上次完整修補程式發行後建立的安全性錯誤修正。

      - 這些安全性修補程式版本也可包含必要的Hotfix，以解決可能影響Adobe Commerce應用程式的重大問題。
   - 最新支援次要版本(目前為Adobe Commerce 2.4)的安全性修補版本通常不包含安全性增強功能。 而是包含在最新支援次要版本的完整完整修補版本中。


- **支援舊微版本的安全修補程式版本**:

   - 舊版仍受支援的次要版本(目前為Adobe Commerce 2.3)的安全性修補程式版本包括：

      - 自先前的修補程式或安全性修補程式發行以來建立的安全錯誤修正，以及新的安全性增強功能。

      - 這些安全性修補程式版本也可包含必要的Hotfix，以解決影響Adobe Commerce應用程式的重大問題。

      |  | 安全性錯誤 | 安全性增強功能 |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | 最新支援次要版本的安全性修補程式發行（目前為2.4） | X |  |
      | 舊版、支援的次要版本（目前為2.3）的安全性修補程式版本 | X | X |


如需安全性發行的一般資訊，請參閱 [推出全新僅限安全性的修補程式版本](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). 有關下載和應用安全修補程式的說明，請參見 [快速入門安裝](../installation/composer.md).

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

- [商務升級週期的規劃和預算](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [版本設定](https://developer.adobe.com/commerce/php/development/versioning/)
- [即將發行的版本](schedule.md)
- [軟體生命週期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
