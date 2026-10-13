---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%
---
# Adobe Commerce重要功能(v2.4.10)

## v2.4.10-alpha1的重點專案

下列重點適用於Adobe Commerce 2.4.10-alpha1版本。

### Braintree

#### Fastlane

新增Fastlane by PayPal支援，提供更快速、更安全的訪客結帳體驗。
客戶可以選擇加入以儲存付款和運送詳細資料，以便日後更快購買。
回訪的Fastlane客戶可使用一次性程式碼進行驗證，並擷取其儲存的資訊。
客戶也可以在結帳時新增或變更其儲存的卡片和運送地址。
也支援Fastlane樣式和組態選項。

_BUNDLE-3521_

#### Braintree Insights

推出Braintree Insights，以Magento Admin為商戶提供集中式付款績效報表。
提供交易、結算、拒絕、閘道拒絕及付款方式資料的可見度。
支援依網站、日期範圍以及每日、每週或每月間隔篩選。
允許商戶匯入最多13個月的歷史交易資料以用於報告。
包括資料保留和自動清理，可維護長達3年的交易資料。

_BUNDLE-3522_

#### Swish — 當地付款方式

在Braintree Magento擴充功能中引入Swish作為新的瑞典當地付款方法。
符合必要的瑞典商家、國家/地區、貨幣和支付設定時，即可使用Swish。
擁有瑞典運送或帳單地址的客戶可在結帳期間使用Swish完成付款。
新增對成功、已取消和失敗的Swish付款流程的支援，以及適當的結帳回應。
只有在滿足所有必要的組態條件時，才會顯示Swish。

_BUNDLE-3523_

#### 升級版本至v4.9.0

將Braintree模組從v4.8.0升級至v4.9.0。
此升級包含最新的Braintree模組變更和改良。
已驗證Braintree結帳和付款處理在升級後是否如預期繼續運作。
現有客戶結帳和訂單建立流程在升級模組後仍可正常運作。
已執行基本回歸測試，以確保升級不會引入任何問題

_BUNDLE-3530_

### 框架

#### [2.4.10-alpha1]平台元件升級

Adobe Commerce 2.4.10-alpha1包含一組平台相依性升級、相容性改善、前端程式庫更新和穩定性修正。 此版本包含下列完成的變更：

- Predis：將`predis/predis`從2.x升級至3.x，改善與Redis和Valkey環境的相容性，並使Redis使用者端與最新支援的相依性版本保持一致。
- Magento Composer安裝程式：修正`magento-composer-installer`可能未完成安裝程式就自動離開的問題，改善Composer型安裝的可靠性。
- Knockout.js：將Knockout.js從3.5.1升級至3.5.3，以及必要的驗證和相容性更新。
- Chart.js：將Chart.js從4.5.0升級至4.5.1，包括必要的驗證和相容性更新。
- Less.js：將Less.js從4.2.2升級至4.6.4，並附帶相關的驗證和相容性更新。
- 更新：從5.0.0升級至5.2.0，包括必要的驗證和相容性變更。
- jQuery UI： jQuery UI已從1.14.1升級至1.14.2，並隨附相關的驗證和相容性更新。
- PHP 8.5相容性：解決與`chr()`相關的PHP 8.5淘汰問題，確保為函式提供有效的位元組值，並改善與PHP 8.5的相容性。
- 目錄搜尋：修正處理期間可能暫停`catalogsearch_fulltext`重新索引的問題，改善目錄搜尋索引的可靠性。
- js-cookie：將js-cookie從3.0.5升級至3.0.7或適用的支援版本，解決相依性和相容性需求。

_AC-17061_

#### 確保B2B 1.5.3-p1/1.5.4-alpha1與2.4.10-alpha1、2.4.9-p1、2.4.8-p6、2.4.7-p11和2.4.6-p16的相容性

B2B 1.5.4-alpha1與下列Adobe Commerce發行版本相容：2.4.9、2.4.8、2.4.7和2.4.6。

_AC-17100_

#### 升級NPM相依性並使其現代化

將下列npm相依性更新至其最新的安全版本，以解決已知的安全漏洞：

- 底線
- imagemin-svgo
- glob
- 伺服 — 靜態
- grunt
- 較少
- uglify-js
- 已標籤
- clean-css
- 最小值
- trim-newlines
- terser
- css-select
- n檢查
- semver-regex
- http-cache-semantics
- js-yaml
- package-json

這些相依性更新在維護現有應用程式功能的同時，可減輕所識別的安全性弱點。

_AC-17372_

#### 升級NPM相依性： underscore.js (1.13.7 → 1.13.8)

將underscore.js從1.13.7更新至1.13.8，以包含最新的上游修正和穩定性改善。

_AC-17486 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升級NPM相依性： imagemin-svgo (9.0.0 → 12.0.0)

將imagemin-svgo從9.0.0更新至12.0.0，以包含最新的上游修正、安全性更新和SVG最佳化改進。

_AC-17657 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升級NPM相依性：eslint-formatter-junit (8.40.0 → 9.0.1)

將eslint-formatter-junit從8.40.0更新至9.0.1，以包含ESLint報告的最新上游修正和相容性改善。

_AC-17659 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升級NPM相依性： glob (11.0.0 → 13.0.0)

將glob從11.0.0更新至13.0.0，以包含最新的上游修正、效能改進和相容性增強功能。

_AC-17660 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升級NPM相依性：grunt-eslint (25.0.0 → 26.0.0)

將grunt-eslint從25.0.0更新至26.0.0，以包含最新的上游修正和相容性改善。

_AC-17661 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 升級NPM相依性：伺服器靜態(1.16.2 → 2.2.1)

將伺服器靜態從1.16.2更新至2.2.1，以包含最新的上游修正、安全性更新和相容性改善。

_AC-17662 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 針對Grunt和Less升級最新的NPM相依性

將Grunt和Less更新至支援的最新版本，改善前端組建穩定性和相容性。

_AC-17663 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 將NPM覆寫相依性升級至最新支援的版本

將多個NPM覆寫相依性更新為最新支援的版本，改善安全性、組建穩定性和相容性。

_AC-17664 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c69ec9c5)_

#### [B2B]採購單未透過ActiveMQ自動轉換為銷售訂單

修正當使用ActiveMQ並透過cron (bin/magento cron:run)執行消費者時，透過啟用自動核准的店面所下的採購單未自動轉換為銷售訂單的問題。 以前，訊息會新增至ActiveMQ佇列，但除非消費者是透過CLI手動啟動，否則不會進行處理。 透過此修正，消費者現在可在cron執行後依預期處理訊息，確保使用ActiveMQ的B2B商家可順暢地轉換訂單。

_AC-17679_

#### Symfony L2快取最佳化及舊版快取回溯相容性

Adobe Commerce 2.4.10現在提供最佳化的Symfony L2快取支援，同時保留現有的Zend型快取實作作為預設值。

想要使用Symfony快取的商家必須明確啟用它，並更新Symfony L1/L2實作特有的必要快取設定。 繼續使用Zend型快取的現有商家不需要變更任何設定。

這種雙快取記憶體方法可讓商戶根據需求靈活地採用Symfony快取記憶體，同時確保與現有快取記憶體組態和部署回溯相容。

_AC-17865_

### 其他

#### 國家/地區（州/省）的管理員管理

商家現在可以直接從管理介面管理國家/地區子區域（例如州和省）。 這項新功能可讓商家：

- 檢視、新增、編輯、停用或移除任何國家/地區的區域。
- 在結帳、客戶地址表單以及管理訂單建立期間，立即將新區域顯示為下拉式清單選項，不需要變更程式碼。
- 編輯區域顯示名稱（包括當地語係化名稱）和ISO代碼。
- 停用由現有訂單、地址或稅捐規則參考的區域（確保歷史資料保持準確），同時防止硬性刪除此類區域。
- 所有預先定義的區域保持不變，現在可以在新介面中看到和管理。

此功能可完全回溯相容，並確保客戶面對和API位址行為保持一致。

_AC-16192_

#### 將predis/predis從2.x升級至3.x

Redis使用者端資料庫predis/predis已從2.x版升級至3.x版。 此主要版本升級會遵循最新的相依性標準、改善相容性，並確保長期可維護性。

_AC-17101 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/de7188da)_

#### 將knockout.js從3.5.1版升級至3.5.3版

將knockout.js程式庫從3.5.1版升級至3.5.3版。 此更新針對所有在店面和管理程式中使用「去底版」繫結的UI元件，帶來上游錯誤修正和穩定性改善。

_AC-17366 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/de7188da)_

#### 2.4.10-alpha1升級清漆至9版

Adobe Commerce 2.4.10與Varnish 9.0版相容。

_AC-17972_
