---
source-git-commit: 56974b4ada65c21ce1303e4b93bd8acb9fe41b28
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---
# Magento Open Source重要功能(v2.4.9-beta1)

## v2.4.9-beta1的重點專案

下列重點適用於Magento Open Source 2.4.9-beta1版本。

### API

#### 新增在商店檢視層級更新產品時，保留REST API中產品相簿繼承的可能性

如果承載中省略media_gallery_entries或設為NULL以防止該範圍中產品收藏館的任何變更，則透過市集範圍中的REST API更新產品不會再導致產品影像和視訊繼承全域範圍的變更。 此外，現在也可以將對應欄位設為NULL，透過REST API還原產品影像和視訊的範圍繼承

_ACP2E-4358 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 框架

#### 調查web-token/jwt-framework的最新主要版本

作為持續安全性審查程式的一部分，我們評估了最新主要版本的JWT框架，以確保未來相容性並維持強大的安全性標準。 此版本中的現有功能不受影響。

_AC-13209 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2bac8114) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/33b81f28)_

#### [第2]部分 — 使用最新可用版本更新所有js程式庫和npm相依性

composer版本支援僅針對composer版本2.2.x。 現在支援也延伸至2.4.x版。

_AC-13792 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/19844aa0)_

#### 以PHP原生函式取代carlos-mg89/oauth

以原生PHP OAuth函式取代協力廠商carlos-mg89/oauth程式庫，以改善安全性、減少外部相依性並增強平台穩定性。

_AC-14075 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7b8064f7)_

#### 調查最新版本的chart.js

將Chart.js JavaScript圖表程式庫升級至最新版本4.4.8，以改進圖表轉譯效能、增強視覺功能，並解決管理控制面板和報表模組的安全漏洞。

_AC-14304 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/768b4442)_

#### 調查最新版本查詢/更新並更新

將Uppy檔案上傳程式庫升級至4.13.4版，以提升檔案上傳功能、改善使用者體驗，並解決Adobe Commerce管理介面和前端元件檔案處理中的安全性弱點。

_AC-14307 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/eb491c05)_

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

#### 將allure-framework/allure-phpunit版本更新為3並移除2.4.9-alpha1中的原生相依性

在Adobe Commerce 2.4.9中，alloure-framework/alloure-phpunit相依性已升級至major版本3，其中新增了對PHP 8.4、PHP 8.5的支援，並使我們的Alloure型測試報告棧疊現代化。 舊版Allure PHPUnit先前所需的原生相依性已隨適用情況移除，並簡化設定和維護。

_AC-14548 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/87b8b34e)_

#### 將chart.js相依性升級至最新版本

chart.js相依性已升級至最新版本4.5.0

_AC-15133 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/657f983e)_

#### 在Adobe Commerce 2.4.9中新增Symfony 7.4 LTS和PHP 8.5的官方支援

在Adobe Commerce 2.4.9平台更新中，magento/composer套件使用的所有Symfony相依性都已更新至最新的Symfony LTS 7.4版本。 這會使Commerce的Composer工具與目前的Symfony LTS系列一致，並移除與舊版Symfony相關的先前相依性限制。 此外，在升級至Adobe Commerce 2.4.9之前，所有擴充Symfony核心類別的自訂類別都已更新符合最新Symfony需求的型別宣告和方法簽章。這樣可以防止相容性問題，並確保順利轉換至更新的框架元件。

_AC-15170 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c127d10b)_

### 其他

#### 驗證碼/重新驗證碼無法用於API/GraphQl

在Adobe Commerce 2.4.9中，當針對建立帳戶表單啟用驗證碼（或reCAPTCHA）時，現在會透過REST和GraphQL API對建立客戶帳戶強制執行相同的驗證碼驗證。

_AC-16245 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fd7f30ee)_

### 安全性

#### 改善非同步/大量請求效能

修正APSB25-08安全性修補程式之後大量非同步Web端點效能下降，導致執行時間增加的問題。

_AC-14078 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9a7352b7)_

#### 每位使用者只需設定一個已啟用的2FA提供者

現在，管理員使用者只需設定商家其中一個已啟用的2FA提供者(例如，Google Authenticator或U2F)，即可存取管理員面板。 之後可視需要設定其他啟用的提供者。 先前，當啟用多個2FA提供者(例如Google Authenticator和U2F)時，每位管理員使用者都需要設定所有已啟用的提供者，才能登入。 對於無法存取所有因素（例如U2F的硬體金鑰）的使用者來說，這會造成摩擦。

_AC-8253 - [GitHub程式碼貢獻](https://github.com/magento/security-package/commit/71e7936b)_

### 測試和預覽

#### [功能要求]行動檢視中的內容暫存預覽

管理員面板中的預備預覽功能現在可讓您精確呈現瀏覽器模擬的行動裝置預覽，提供預備更新在行動裝置上出現方式的視覺呈現。

_ACP2E-3397 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_
