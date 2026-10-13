---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%
---
# Magento Open Source重要功能(v2.4.10)

## v2.4.10-alpha1的重點專案

下列重點適用於Magento Open Source 2.4.10-alpha1版本。

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

### 其他

#### 將predis/predis從2.x升級至3.x

Redis使用者端資料庫predis/predis已從2.x版升級至3.x版。 此主要版本升級會遵循最新的相依性標準、改善相容性，並確保長期可維護性。

_AC-17101 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/de7188da)_

#### 將knockout.js從3.5.1版升級至3.5.3版

將knockout.js程式庫從3.5.1版升級至3.5.3版。 此更新針對所有在店面和管理程式中使用「去底版」繫結的UI元件，帶來上游錯誤修正和穩定性改善。

_AC-17366 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/de7188da)_
