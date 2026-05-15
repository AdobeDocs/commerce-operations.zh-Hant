---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Magento Open Source重要功能(v2.4.9)

## v2.4.9中的重點專案

下列重點適用於Magento Open Source 2.4.9版本。

### API

#### 新增在商店檢視層級更新產品時，保留REST API中產品相簿繼承的可能性

如果承載中省略media_gallery_entries或設為NULL以防止該範圍中產品收藏館的任何變更，則透過市集範圍中的REST API更新產品不會再導致產品影像和視訊繼承全域範圍的變更。 此外，現在也可以將對應欄位設為NULL，透過REST API還原產品影像和視訊的範圍繼承。

_ACP2E-4358 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### 透過帳戶區域儲存Google Pay

在Adobe Commerce 2.4.9中，當在Braintree中啟用Google Pay Vault時，客戶現在可以透過帳戶區域來儲存其Google Pay卡片。 儲存的卡片會顯示在已儲存的付款方式下，可用於結帳時未來的購買，並可由客戶刪除。 這將儲存庫支援擴展到卡片和PayPal之外，擴展到Google Pay。

_BUNDLE-3459_

#### 即時帳戶更新程式(RTAU)

適用於Braintree的Adobe Commerce 2.4.9中的即時帳戶更新程式(RTAU)功能可確保在卡片過期或被取代時，存放的Visa、Mastercard和Discover卡片詳細資料會自動更新。 這樣可將失敗的付款減至最少，使Magento Vault保持最新狀態，並跳過不支援的型別（預付、Apple支付、Google支付），而不會發生錯誤。

_BUNDLE-3462_

#### Braintree卡付款的ELO卡型別支援

在Adobe Commerce 2.4.9中，Braintree Payments已新增對ELO卡型別的支援。 管理員現在可以在信用卡設定中啟用ELO，客戶可以在結帳時使用ELO卡成功下訂單，確保透過Braintree進行順暢的交易。

_BUNDLE-3464_

#### 依商業發票付款

針對Adobe Commerce 2.4.9 （Braintree擴充功能），為德國買家新增了全新的當地付款方法「依發票付款」。 「依商業發票付款」是PayPal + Ratepay (Rechnungskauf mit Ratepay)所支援的「立即購買，稍後付款(BNPL)」選項，客戶可先收到貨品並在30天內支付商業發票，而不需要PayPal帳戶。 因為這不是立即付款，所以定購是由PayPal的伺服器端webhook所驅動。

_BUNDLE-3475_

#### 將優惠方案新增至Google支付快速薪資表

對於Adobe Commerce 2.4.9中的Braintree擴充功能， Google支付快速薪資表現在支援促銷/優惠代碼。 購物者可以直接在Google付款表內套用、檢視和移除Magento購物車促銷活動，確保快速結帳客戶可獲得與標準結帳流程相同的折扣和獎勵。

_BUNDLE-3476_

#### 將優惠方案新增至Apple支付快速付款表

對於Adobe Commerce 2.4.9中的Braintree擴充功能， Apple支付快速薪資表現在支援促銷/優惠代碼。 購物者可直接在Apple Pay工作表中套用優惠券，因此快速結帳使用者可享有與標準結帳流程相同的折扣和促銷活動。

_BUNDLE-3477_

#### 在Chrome和Firefox上透過Apple Pay付款

至於Adobe Commerce 2.4.9中的Braintree擴充功能，Apple Pay現在可用於Chrome和Firefox，而不僅僅是Safari。 啟用Apple Pay Express後，Apple Pay按鈕可在支援的店面位置使用，客戶可使用iPhone掃描程式碼以完成付款。

_BUNDLE-3478_

#### 伺服器端送貨回撥

針對Adobe Commerce 2.4.9中的Braintree擴充功能，PayPal Express送貨回撥已從使用者端移至伺服器端。 這直接在PayPal模式中提供動態出貨方法、即時成本計算以及精確的購物車層級詳細資訊，進而提升可靠性並為未來功能（例如連絡人模組支援、應用程式切換流程及Venmo Express）奠定基礎。

_BUNDLE-3479_

#### PayPal聯絡模組

針對Adobe Commerce 2.4.9中的Braintree擴充功能，我們為美國商家匯入了全新的PayPal連絡人模組。 啟用後，使用PayPal Express的買家可以在快捷流程（PDP、迷你購物車、購物車、結帳快遞）期間，直接在PayPal模式中檢視並更新與商家共用的電子郵件地址和電話號碼。 接著，選取的聯絡詳細資料會儲存在Adobe Commerce訂單中。

_BUNDLE-3480_

#### BLIK （當地付款方式）

在Adobe Commerce 2.4.9中的Braintree擴充功能中，BLIK已新增為波蘭購物者的全新當地付款方法。 這可在現有Braintree當地支付方式(LPM)流程中實現基於銀行的安全的BLIK支付，改善波蘭客戶的結帳便利性和轉換。

_BUNDLE-3481_

#### 基數整合更新CSP原則

針對Adobe Commerce 2.4.9中的Braintree擴充功能，內容安全性原則(CSP)已更新，以支援最新的Cardinal (3-D Secure)整合需求。 這可確保在瀏覽器CSP允許在3-D Secure流程中使用的所有基數託管指令碼、iframe和相關資源，以防止封鎖請求和中斷的質詢/驗證體驗。

_BUNDLE-3485_

### 框架

#### 將web-token/jwt-framework程式庫升級至最新主要版本

作為持續安全性審查程式的一部分，我們評估了最新主要版本的JWT框架，以確保未來相容性並維持強大的安全性標準。 此版本中的現有功能不受影響。

_AC-13209 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2bac8114) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/33b81f28)_

#### [第2]部分 — 使用最新可用版本更新所有js程式庫和npm相依性

composer版本支援僅針對composer版本2.2.x。 現在支援也延伸至2.4.x版。

_AC-13792 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/19844aa0)_

#### 以PHP原生函式取代carlos-mg89/oauth

以原生PHP OAuth函式取代協力廠商carlos-mg89/oauth程式庫，以改善安全性、減少外部相依性並增強平台穩定性。

_AC-14075 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7b8064f7)_

#### 升級Jquery/Uppy並更新程式庫最新版本

將Uppy檔案上傳程式庫升級至4.13.4版，以提升檔案上傳功能、改善使用者體驗，並解決Adobe Commerce管理介面和前端元件檔案處理中的安全性弱點。

_AC-14307 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/eb491c05)_

#### 將jquery-validate程式庫升級至最新版本

將jQuery Validate程式庫升級至1.21.0版，以強化表單驗證功能、改善使用者體驗，並確保在管理和前端介面中，所有Adobe Commerce表單都具備現代瀏覽器相容性。

_AC-14403 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 將jquery-ui程式庫升級至最新版本

將jQuery UI程式庫升級至1.14.1版，以強化使用者介面Widget、改善協助工具，並確保所有Adobe Commerce管理和前端介面元件都具備現代瀏覽器相容性。

_AC-14417 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/77c589a6)_

#### 將less.js程式庫升級至最新版本

將Less.js CSS前置處理器升級至4.2.2版，以增強CSS編譯效能、改善語法支援，並更新所有Adobe Commerce前端和管理主題的主題建置流程。

_AC-14418 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 將moment-timezone-with-data.js程式庫升級至最新版本

將時刻時區資料庫升級至0.5.43版，以增強時區處理能力、使用最新IANA時區資料庫變更更新時區資料，並改善所有Adobe Commerce國際和多時區作業的日期/時間處理準確性。

_AC-14419 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 將underscore.js程式庫升級至最新版本

將Underscore.js公用程式庫升級至1.13.7版，以增強JavaScript功能程式設計功能、改善資料操控效能，並確保所有Adobe Commerce前端和管理介面元件都具備現代瀏覽器相容性。

_AC-14420 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

#### 將allure-framework/allure-phpunit版本更新為3並移除2.4.9-alpha1中的原生相依性

在Adobe Commerce 2.4.9中，alloure-framework/alloure-phpunit相依性已升級至major版本3，其中新增了對PHP 8.4、PHP 8.5的支援，並使我們的Alloure型測試報告棧疊現代化。 舊版Allure PHPUnit先前所需的原生相依性已隨適用情況移除，並簡化設定和維護。

_AC-14548 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/87b8b34e)_

#### 將chart.js相依性升級至最新版本

chart.js相依性已升級至最新版本4.5.0。

_AC-15133 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/657f983e)_

#### 在Adobe Commerce 2.4.9中新增Symfony 7.4 LTS和PHP 8.5的官方支援

在Adobe Commerce 2.4.9平台更新中，magento/composer套件使用的所有Symfony相依性都已更新至最新的Symfony LTS 7.4版本。 這會使Commerce的Composer工具與目前的Symfony LTS系列一致，並移除與舊版Symfony相關的先前相依性限制。 此外，在升級至Adobe Commerce 2.4.9之前，所有擴充Symfony核心類別的自訂類別都已更新符合最新Symfony需求的型別宣告和方法簽章。 這樣可以防止相容性問題，並確保順利轉換至更新的框架元件。

_AC-15170 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### 確保Open Source中有clearCart GraphQL變異功能

透過Adobe Commerce 2.4.9，所有Open Source使用者現在都可使用clearCart GraphQL突變。 之前，您只能在Adobe Commerce中存取此突變，但現在，這也是Open Source的標準GraphQL購物車功能的一部分。
此突變的檔案已更新，以反映其在2.4.9版Open Source中的可用性。
請參閱[clearCart GraphQL突變檔案](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/)。

_AC-16683 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9]使用管理員設定合併來賓和客戶購物車邏輯

已引入新的管理員設定選項，以控制購物者登入時訪客和客戶購物車合併的方式。 此增強功能可讓您靈活定義最符合業務需求的購物車合併行為。

_LYNX-889_

#### [AC-2.4.9]取得無存貨產品的歷史訂單

歷史訂單現在會顯示產品詳細資料，即使現在無庫存。

_LYNX-913_

#### [AC-2.4.9] [CE]針對遺失的GraphQL變動實作ReCaptcha

ReCaptcha驗證已新增到updateCustomer、updateCustomerV2和contactUs變動。

_LYNX-941_

### 其他

#### 驗證碼/reCAPTCHA無法用於API/GraphQL

在Adobe Commerce 2.4.9中，當針對建立帳戶表單啟用驗證碼（或reCAPTCHA）時，現在會透過REST和GraphQL API對建立客戶帳戶強制執行相同的驗證碼驗證。

_AC-16245 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/fd7f30ee)_

#### 應更新braintree分支，以支援PHP 8.5

Braintree支付擴充功能已更新，以支援最新的PHP 8.5執行階段，同時保持與PHP 8.4的相容性。

_BUNDLE-3493_

#### 新增清除願望清單作業

新增新的clearWishlist變異以支援大量作業，可讓所有專案在單一動作中從願望清單移除。

_LYNX-790_

#### 引入exchangeExternalCustomerToken突變

推出新的GraphQL突變exchangeExternalCustomerToken，可透過整合權杖驗證使用者，並傳回客戶權杖和相關客戶資料

_LYNX-815_

#### [AC]介紹傳回套用群組、區段和購物車規則ID的GraphQL查詢

GraphQL查詢公開以擷取套用之客戶群組、客戶區段和購物車規則的編碼uid。

_LYNX-867_

#### [AC-2.4.9]介紹OrderTotal.grand_total_excl_tax欄位

新欄位OrderTotal.grand_total_excl_tax已新增至GraphQL訂單回應。 此欄位提供訂單不含稅的總計，讓直接從API存取不含稅總計變得更容易。

優點：

- 透過GraphQL輕鬆擷取任何訂單的總計（不含稅）。
- 簡化與需要免稅總額的外部系統的整合。
- 減少使用者端自訂計算的需求。

_LYNX-892_

### PCI、安全性

#### 重新調整SRI儲存裝置，以提高效能效率

SRI雜湊儲存現在會針對每個區域、主題和區域設定產生個別檔案，而非單一大型sri-hashes.json。 這項變更可確保每個頁面都只載入相關的雜湊檔案，進而改善效能，並減少對擁有多個主題或地區設定的商店的記憶體使用量。

_AC-16113 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/bc83cd2c)_

### 安全性

#### 改善非同步/大量請求效能

修正APSB25-08安全性修補程式之後大量非同步Web端點效能下降，導致執行時間增加的問題。

_AC-14078 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9a7352b7)_

#### 每位使用者只需設定一個已啟用的2FA提供者

現在，管理員使用者只需設定商家其中一個已啟用的2FA提供者（例如，Google Authenticator或U2F），即可存取管理員面板。 之後可視需要設定其他啟用的提供者。 先前，當啟用多個2FA提供者（例如Google Authenticator和U2F）時，每位管理員使用者都需要設定所有已啟用的提供者，才能登入。 對於無法存取所有因素（例如U2F的硬體金鑰）的使用者來說，這會造成摩擦。

_AC-8253 - [GitHub程式碼貢獻](https://github.com/magento/security-package/commit/71e7936b)_
