---
source-git-commit: fd421e8c2455a2b45d3f3cc93573d2a609e4936d
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 0%

---
# Adobe Commerce重要功能(v2.4.9-beta1)

## v2.4.9-beta1的重點專案

下列重點適用於Adobe Commerce 2.4.9-beta1版本。

### API

#### 在商店檢視層級執行REST API產品收藏館繼承控制

當承載中省略`media_gallery_entries`或設為`NULL`時，透過存放區範圍中的REST API更新產品不再導致產品影像和視訊繼承全域範圍的變更。 現在也可以透過REST API將對應欄位設定為`NULL`，以還原產品影像和影片的範圍繼承。

_ACP2E-4358 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 管理員UI

#### 型錄價格規則網格的「動作」功能表

「Commerce管理員」中的「目錄價格規則」格線現在包含「動作」功能表，可讓商家一次啟用、停用或刪除多個目錄價格規則。 這樣一來，目錄價格規則管理與購物車價格規則可用的現有大量動作一致，大幅減少管理大型規則集所需的時間。

_AC-13916_

#### 用於內容暫存的行動檢視預覽

Admin中的預備預覽功能現在可讓您精確呈現瀏覽器模擬的行動裝置預覽，提供預備更新在行動裝置上出現方式的視覺呈現。

_ACP2E-3397 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### 快速簽出

- **Google Pay快速付款表中的促銷優惠方案**

  Google支付快速薪資表現在支援促銷與優惠代碼。 購物者可以直接在Google付款表內套用、檢視和移除Commerce購物車促銷活動，確保快速結帳客戶可獲得與標準結帳流程相同的折扣和獎勵。

  _BUNDLE-3476_

- **Apple Pay快速付款表中的促銷優惠方案**

  Apple支付快速薪資表現在支援促銷與優惠代碼。 購物者可直接在Apple Pay工作表中套用優惠券，因此快速結帳使用者可享有與標準結帳流程相同的折扣和促銷活動。

  _BUNDLE-3477_

- 在Chrome和Firefox上&#x200B;**Apple Pay**

  Apple Pay現在可用於Chrome和Firefox，而不僅僅是Safari。 啟用Apple Pay Express後，Apple Pay按鈕可在支援的店面位置使用，客戶可使用iPhone掃描程式碼以完成付款。

  _BUNDLE-3478_

- **PayPal Express的伺服器端送貨回撥**

  PayPal Express送貨回撥已從使用者端移至伺服器端。 這直接在PayPal模式中提供動態出貨方法、即時成本計算以及精確的購物車層級詳細資訊，進而提升可靠性並為未來功能（例如連絡人模組支援、應用程式切換流程及Venmo Express）奠定基礎。

  _BUNDLE-3479_

- **美國商家快速結帳的PayPal連絡模組**

  我們為美國商家推出新的PayPal連絡人模組。 啟用後，使用PayPal Express的買家可以在快捷流程（PDP、迷你購物車、購物車、結帳快遞）期間，直接在PayPal模式中檢視並更新與商家共用的電子郵件地址和電話號碼。 接著，選取的聯絡詳細資料會儲存在Commerce訂單中。

  _BUNDLE-3480_

#### 付款方法

- **Braintree付款的ELO卡型別支援**

  新增ELO卡型別至Braintree付款的支援。 管理員現在可以在信用卡設定中啟用ELO，客戶可以在結帳時使用ELO卡成功下訂單，確保透過Braintree進行順暢的交易。

  _BUNDLE-3464_

- 波蘭購物者的&#x200B;**BLIK當地付款方式**

  新增BLIK，作為波蘭購物者的全新當地付款方式。 這可在現有Braintree當地支付方式(LPM)流程中實現基於銀行的安全的BLIK支付，改善波蘭客戶的結帳便利性和轉換。

  _BUNDLE-3481_

- **依商業發票付款 — 德國的新的BNPL付款方式**

  為德國買家新增新的當地付款方式「依商業發票付款」。 「依商業發票付款」是PayPal與Ratepay支援的「立即購買，稍後付款(BNPL)」選項(「Rechnungskauf mit Ratepay」)，客戶可在30天內先收到貨品並支付商業發票，而不需要PayPal帳戶。 因為這不是立即付款，所以定購是由PayPal的伺服器端webhook驅動。

  _BUNDLE-3475_

#### 卡片存放

- **透過帳戶區域存放Google Pay**

  在Braintree中啟用Google Pay Vault時，客戶現在可以透過帳戶區域儲存其Google Pay卡片。 儲存的卡片會顯示在已儲存的付款方式下，可用於結帳時未來的購買，並可由客戶刪除。 這將儲存庫支援擴展到卡片和PayPal之外，擴展到Google Pay。

  _BUNDLE-3459_

- **Braintree存放卡的即時帳戶更新程式(RTAU)**

  Braintree新增的即時帳戶更新程式(RTAU)功能可確保當卡片過期或被取代時，保險儲存的Visa、萬事達卡和Discover卡片詳細資料會自動更新。 這樣可將失敗的付款減至最少，使Commerce Vault保持最新狀態，並跳過不支援的型別(預付、Apple支付、Google支付)，而不會發生錯誤。

  _BUNDLE-3462_

#### 管理工具

- **將Commerce訂單連結至Braintree入口網站**

  Braintree入口網站連結現在已新增到Commerce管理員中的訂單詳細資料。 按一下連結，使用Commerce訂單中的貿易商ID和交易ID，在Braintree入口網站（在新標籤中）中開啟相關交易。 如此一來，不需分別登入兩個系統，即可直接交叉參照。

  _BUNDLE-3461_

#### 安全性與相容性

- **3D Secure的Cardinal整合內容安全性原則更新**

  內容安全性原則(CSP)已更新，以支援最新的Cardinal (3-D Secure)整合需求。 這可確保在瀏覽器CSP允許在3-D Secure流程中使用的所有基數託管指令碼、iframe和相關資源，以防止封鎖請求和中斷的挑戰或驗證體驗。

  _BUNDLE-3485_

- **Braintree付款延伸模組PHP 8.5相容性**

  Braintree支付擴充功能已更新，以支援PHP 8.5執行階段，同時保持與PHP 8.4的相容性。

  _BUNDLE-3493_

### 平台與基礎結構

#### OpenSearch 3.x支援

Adobe Commerce 2.4.9-beta1與OpenSearch 3.x完全相容。此更新可讓商家受益於效能、安全性和長期支援的改善，同時保持與OpenSearch 2.x的回溯相容性。

_AC-11846_

#### 完整Valkey 8.x支援

Adobe Commerce 2.4.9-beta1新增對Valkey 8.x的完整支援，作為與Redis相容的快取後端，包括與Redis的完整CLI命令同位檢查。 已更新管理員和雲端設定選項，提供順暢的Valkey設定。 這項支援是由Redis 7.2支援終止和授權變更所驅動，為商家提供跨Commerce發行系列2.4.5到2.4.9-beta1的可靠、完全受支援的Redis替代方案。

_AC-14103、AC-14604_

#### Apache ActiveMQ Artemis支援已取代RabbitMQ

新增對Apache ActiveMQ Artemis的支援，作為RabbitMQ的策略替代方案，由RabbitMQ 4相關的支援終止風險驅動。 Commerce發行版本2.4.6到2.4.9-beta1完全支援ActiveMQ Artemis，包括使用AWS ActiveMQ進行雲端原生部署的Adobe Commerce Cloud，並且支援佇列消費者和發行者的STOMP設定。 現有的RabbitMQ 4安裝仍與想要繼續使用目前訊息佇列服務的商戶相容。

_AC-14558_

### PHP和撰寫器

#### php 8.5相容性

從Adobe Commerce 2.4.9-beta1版開始，該平台與PHP 8.5完全相容，同時保留對PHP 8.4的支援，並允許PHP 8.3用於僅限升級的情況。 此工作會更新核心程式碼、相依性和工具，讓商戶可以在PHP 8.4支援終止之前安全地移至較新的PHP版本，以維持PCI法規遵循和長期平台健康狀態。

_AC-15615_

#### PHP 8.2支援已移除

從Adobe Commerce 2.4.9-beta1開始，不再支援PHP 8.2。 此平台現在針對PHP 8.3和更新版本，更新了核心程式碼、相依性和工具，以便在PHP 8.4和8.5上以簡潔可靠的方式執行。

_AC-15758_

#### 已驗證Composer 2.9相容性

Adobe Commerce 2.4.9-beta1與Composer 2.x （包括Composer 2.9）完全相容。這種對齊方式可保留回溯相容性，並確保商家和開發人員使用最新版Composer獲得穩定的建置和部署體驗。

_AC-14481_

### 框架

#### JWT框架安全性和相容性更新

在持續的平台安全性審查中，已對Web權杖JWT架構相依性進行評估並更新至最新主要版本，確保未來在所有Commerce整合中都能相容於權杖型驗證，並符合強大的安全性標準。 現有功能會完全保留。

_AC-13209 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/2bac8114) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/33b81f28)_

#### Adobe Commerce功能測試框架已更新為Symfony LTS相依性

Adobe Commerce功能測試架構(MFTF)已更新，以根據web-token/jwt-framework升級的要求，使用最新的Symfony LTS相依性，包括symfony/config。 這解決了先前的相依性衝突，並確保了功能測試的穩定且受支援的棧疊。

_AC-13244_

#### 原生PHP OAuth函式取代協力廠商程式庫

協力廠商`carlos-mg89/oauth`程式庫已由原生PHP OAuth函式取代，改善安全性、減少外部相依性，並增強平台穩定性。

_AC-14075 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/7b8064f7)_

#### Symfony快取元件取代Zend_Cache

從Adobe Commerce 2.4.9-beta1版開始，已過時的Zend_Cache元件已由Symfony Cache元件取代。 此更新增強了快取效能和可維護性，並確保與PHP 8.x和未來平台更新的長期相容性。 現有的快取後端和快取管理命令仍受到完整支援，不需變更即可進行目前的整合。

_AC-15823_

#### WYSIWYG編輯器從TinyMCE移轉至GegRTE

由於對TinyMCE 5和6的支援終止以及與TinyMCE 7的授權不相容，Adobe Commerce WYSIWYG編輯器已移轉至開放原始碼[GreatRTE](https://hugerte.org/)編輯器。 此移轉確保Adobe Commerce仍符合開放原始碼授權，避免已知的TinyMCE 6漏洞，並為商家和開發人員提供現代且受支援的編輯體驗。

_AC-14568_

#### 原生MVC實作會取代Laminas MVC

Adobe Commerce已引進原生MVC實作，取代舊有的Laminas MVC，以確保超越PHP 8.5的長期相容性和穩定性。此變更可加強效能、減少外部相依性，並為Commerce提供更符合未來需求的基礎。

_AC-15160_

#### 官方Symfony 7.4 LTS支援

在Adobe Commerce 2.4.9-beta1平台更新中，所有Symfony相依性都已更新至最新的Symfony LTS 7.4版本。 所有延伸Symfony核心類別的自訂類別都已更新符合最新Symfony要求的型別宣告和方法簽章，防止相容性問題，並確保順利轉換至更新的框架元件。

_AC-15170 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/c127d10b)_

#### 誘惑PHPUnit相依性已升級至版本3

`allure-framework/allure-phpunit`相依性已升級至主要版本3，新增對PHP 8.4和PHP 8.5的支援，並更新Allure型測試報告棧疊。 舊版Allure PHPUnit先前所需的原生相依性已移除，而可簡化設定與維護。

_AC-14548 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/87b8b34e)_

#### New Relic報告已更新至NerdGraph API

New Relic報告模組已更新，以支援New Relic的NerdGraph (GraphQL)變更追蹤API，同時完全保留現有的REST v2部署標籤整合。 此次變更提供更豐富的部署中繼資料、區域端點支援（美國和EU），以及可透過管理員設定進行設定，而不會中斷現有設定。

_AC-15461_

#### JavaScript程式庫更新

- **Chart.js已更新至4.5.0**&#x200B;版

  將Chart.js JavaScript圖表程式庫升級至4.5.0版，以改進圖表轉譯效能、增強視覺功能，並解決管理控制面板和報表模組的安全漏洞。

  _AC-14304、AC-15133 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/768b4442)、[GitHub程式碼貢獻](https://github.com/magento/magento2/commit/657f983e)_

- **更新檔案上傳程式庫至4.13.4**&#x200B;版

  將Uppy檔案上傳程式庫升級至4.13.4版，以提升檔案上傳功能、改善使用者體驗，並解決Adobe Commerce管理介面和前端元件檔案處理中的安全性弱點。

  _AC-14307 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/eb491c05)_

- **jQuery驗證程式庫已升級至1.21.0**&#x200B;版

  將jQuery Validate程式庫升級至1.21.0版，以強化表單驗證功能、改善使用者體驗，並確保在管理和前端介面中，所有Adobe Commerce表單都具備現代瀏覽器相容性。

  _AC-14403 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

- **jQuery UI程式庫已升級至1.14.1**&#x200B;版

  將jQuery UI程式庫升級至1.14.1版，以強化使用者介面Widget、改善協助工具，並確保所有Adobe Commerce管理和前端介面元件都具備現代瀏覽器相容性。

  _AC-14417 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/77c589a6)_

- **Less.js CSS前置處理器已升級至4.2.2**&#x200B;版

  將Less.js CSS前置處理器升級至4.2.2版，以增強CSS編譯效能、改善語法支援，並更新所有Adobe Commerce前端和管理主題的主題建置流程。

  _AC-14418 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

- **時區資料庫已升級至0.5.43**&#x200B;版

  將時刻時區資料庫(`moment-timezone-with-data.js`)升級至0.5.43版，以提升時區處理能力、使用最新IANA時區資料庫變更更新時區資料，並改善所有Adobe Commerce國際和多時區作業的日期和時間處理準確性。

  _AC-14419 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

- **Underscore.js公用程式庫已升級至1.13.7**&#x200B;版

  將Underscore.js公用程式庫升級至1.13.7版，以增強JavaScript功能程式設計功能、改善資料操控效能，並確保所有Adobe Commerce前端和管理介面元件都具備現代瀏覽器相容性。

  _AC-14420 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/98b2848a)_

### 安全性

#### REST和GraphQL API現已強制進行驗證碼驗證

為「建立帳戶」表單啟用CAPTCHA （或reCAPTCHA）時，現在會透過REST和GraphQL API針對客戶帳戶建立強制執行相同的CAPTCHA驗證。

_AC-16245_

#### 改善非同步/大量請求效能

此修正解決APSB25-08安全性修補程式之後引入的大量非同步Web API端點效能降低的問題，並還原預期執行時間。

_AC-14078 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/9a7352b7)_

#### 簡化的雙因素驗證設定

現在，管理員使用者只需設定商家其中一個已啟用的2FA提供者(例如，Google Authenticator或U2F)，即可存取管理員面板。 之後可視需要設定其他啟用的提供者。 先前，當多個2FA提供者已啟用時，每個管理員使用者都必須在可登入前設定所有已啟用的提供者，這會對無法存取所有因數的使用者造成摩擦。

_AC-8253 - [GitHub程式碼貢獻](https://github.com/magento/security-package/commit/71e7936b)_

### 送貨

#### 將USPS整合移轉至RESTful USPS API

為了遵循USPS宣佈的舊版Web Tools API的淘汰，Adobe Commerce已將USPS整合移轉至新的RESTful USPS API。

重要增強功能：

- Dual API支援：管理員使用者現在可以透過組態設定，在舊版Web Tools API和新RESTful USPS API之間選擇。
- 驗證升級：使用OAuth 2.0進行安全API存取。
- 改善資料格式：使用JSON而非XML，以實現更清晰、更有效的通訊。
- 新增管理欄位：
   - 閘道REST URL （根據模式：開發或即時）
   - 使用者端ID和密碼
   - 帳戶型別、帳戶號碼
   - CRID、MID、郵件程式識別碼
   - 適用於國際出貨的AES/ITN
   - REST特定允許的送貨方法

此移轉作業可確保Adobe Commerce符合USPS標準、提升系統可靠性，並保障商家的航運整合。

_AC-13257_

#### 將DHL整合移轉至MyDHL RESTful API

內建的DHL送貨整合現在支援MyDHL RESTful API，同時保留與舊版DHL Express XML API的相容性。 商家可以選擇在Admin中使用哪個DHL API，受益於現代REST功能，而不會破壞現有的XML式設定。

_AC-13258_
