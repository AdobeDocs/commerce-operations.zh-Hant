---
source-git-commit: 3bc225485fa5a4c2b3565014af4ed81dc37fc4ab
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Magento Open Source發行說明(v2.4.9-alpha2)

## v2.4.9-alpha2的重點專案

下列重點適用於Magento Open Source 2.4.9-alpha2版本。

### 框架

#### 新增對OpenSearch 3的支援

Adobe Commerce 2.4.9現在與OpenSearch 3.x完全相容。此更新可讓商家受益於效能、安全性和長期支援的改善，同時保持與OpenSearch 2.x的回溯相容性。

_AC-11846_

#### 將Nginx版本從1.26更新至1.28

用於開發和測試環境(涵蓋目前支援的所有Adobe Commerce版本)的Nginx版本從1.26更新至1.28，與最新的穩定Nginx版本一致。
PR層級測試現在會針對Nginx 1.28執行，以確認所有Adobe Commerce版本的完整相容性和支援。

_AC-14104_

#### 調查最新版本的jquery-validate

將jQuery Validate程式庫升級至1.21.0版，以強化表單驗證功能、改善使用者體驗，並確保在管理和前端介面中，所有Adobe Commerce表單都具備現代瀏覽器相容性。

_AC-14403 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 調查最新版本的jquery-ui

將jQuery UI程式庫升級至1.14.1版，以強化使用者介面Widget、改善協助工具，並確保所有Adobe Commerce管理和前端介面元件都具備現代瀏覽器相容性。

_AC-14417 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/77c589a6)_

#### 調查最新版本less.js

將Less.js CSS前置處理器升級至4.2.2版，以增強CSS編譯效能、改善語法支援，並更新所有Adobe Commerce前端和管理主題的主題建置流程。

_AC-14418 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 調查最新版本moment-timezone-with-data.js

將時刻時區資料庫升級至0.5.43版，以增強時區處理能力、使用最新IANA時區資料庫變更更新時區資料，並改善所有Adobe Commerce國際和多時區作業的日期/時間處理準確性。

_AC-14419 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 調查最新版本的underscore.js

將Underscore.js公用程式庫升級至1.13.7版，以增強JavaScript功能程式設計功能、改善資料操控效能，並確保所有Adobe Commerce前端和管理介面元件都具備現代瀏覽器相容性。

_AC-14420 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 從TinyMCE移轉至Hugerte.org

由於TinyMCE 5和6的支援終止以及授權與TinyMCE 7不相容，目前Adobe Commerce WYSIWYG編輯器的實作已從TinyMCE移轉至開放原始碼GreatRTE編輯器(https://hugerte.org/)。
此移轉確保Adobe Commerce仍符合開放原始碼授權，避免已知的TinyMCE 6漏洞，並為商家和開發人員提供現代且受支援的編輯體驗。

_AC-14568_

#### 新增2.4.9-alpha2的完整Valkey 8.x支援

Adobe Commerce 2.4.9具有完整的CLI命令支援Valkey，可映象目前現有的Redis功能。 已更新管理員和雲端設定，提供順暢的Valkey設定。
此更新透過支援Valkey 8.x確保Adobe Commerce保持經得起未來考驗和效能，為Redis的商家和開發人員提供生命週期即將結束時的可靠替代方案。

_AC-14604_

### 其他

#### 更新適用於CNS建置和測試的AWS Valkey 8.x服務

更新適用於CNS組建的AWS Valkey 8.x服務

_AC-14470_

#### 2.4.9-alpha2 - 8月核心品質改善

_AC-14700_

### 安全性

#### 2.4.9-alpha2的安全性改善

_AC-14610_

### 送貨

#### 將USPS整合從過時的網頁工具API移轉至新的RESTful USPS API

為了遵循USPS在2026年1月25日宣佈淘汰舊版Web Tools API，Adobe Commerce USPS整合已移轉至新的RESTful USPS API。
重要增強功能：

* Dual API支援：管理員使用者現在可以透過組態設定，在舊版Web Tools API和新RESTful USPS API之間選擇。
* 驗證升級：實作OAuth 2.0以安全API存取。
* 改善資料格式：從XML轉換為JSON，以實現更乾淨、更有效的通訊。
* 新增管理欄位：
   * 閘道REST URL （根據模式：開發或即時）
   * 使用者端ID與密碼
   * 帳戶型別、帳戶號碼
   * CRID、MID、郵件程式識別碼
   * 適用於國際出貨的AES/ITN
   * REST特定允許的送貨方法

此移轉作業可確保Adobe Commerce符合USPS標準、提升系統可靠性，並保障商家的航運整合。

_AC-13257_
