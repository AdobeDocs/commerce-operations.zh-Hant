---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Adobe Commerce重要功能(v2.4.9)

## v2.4.9中的重點專案

下列重點適用於Adobe Commerce 2.4.9版本。

### REST API變更

#### 在商店檢視層級執行REST API產品收藏館繼承控制

當承載中省略`media_gallery_entries`或設為`NULL`時，透過存放區範圍中的REST API更新產品不再導致產品影像和視訊繼承全域範圍的變更。 現在也可以透過REST API將對應欄位設定為`NULL`，以還原產品影像和影片的範圍繼承。

在商店檢視層級透過REST API更新產品時：

- 現在省略`media_gallery_entries`或將其設定為NULL將會保留來自預設/全域相簿的繼承。
- 若要還原特定相簿屬性（例如`label`、`position`、`disabled`、`video_title`、`video_description`）的繼承，請在`media_gallery_entries`陣列中將這些欄位設定為NULL。

這項變更可確儲存放區檢視可以輕鬆維持或還原預設的相簿值，減少混淆，並使相簿管理更加一致。

_ACP2E-4358 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/f7bbcb4e)_

### GraphQL API變更

#### Magento Open Source現在提供`clearCart`個GraphQL突變

[clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/) GraphQL突變現在可供所有Magento Open Source使用者使用。 之前，您只能在Adobe Commerce中使用此突變。

_AC-16683 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/4449d914)_

#### 來自`applyGiftCardToCart` GraphQL突變的更多描述性錯誤

增強`applyGiftCardToCart`突變的錯誤處理。 此突變現在會傳回過期或零餘額禮品卡等案例的特定錯誤訊息，以改善購物者體驗。 此外，後端可防止將額外的禮品卡套用至已免費的訂單。

_LYNX-787_

#### 新的`clearWishlist` GraphQL突變會一次移除所有願望清單專案

新增`clearWishlist`變異，從單一呼叫的願望清單中移除所有專案。

_LYNX-790_

#### 整合式驗證的新`exchangeExternalCustomerToken` GraphQL突變

引入新的`exchangeExternalCustomerToken` GraphQL突變，透過整合權杖驗證使用者並傳回客戶權杖和相關客戶資料。

_LYNX-815_


#### 新的GraphQL查詢會傳回套用的客戶群組、區段和購物車規則ID

新的GraphQL查詢會傳回已套用客戶群組、客戶區段和購物車規則的編碼`uid`。

_LYNX-867_

#### 當購物車清空時，會自動清除贈品選項

修正在移除所有專案後，空購物車中保留贈品選項的問題。 現在當購物車清空時，贈品選項會自動清除，符合優惠券的現有行為。

_LYNX-786_

#### 當賓客和客戶購物車合併時，贈品選項會一致地合併

增強購物車合併時禮品選項的處理能力，以確保更一致的使用者體驗。 贈品選項現在會遵循優先順序的合併邏輯，防止當訪客使用者登入且其購物車與現有客戶購物車合併時意外覆寫。

_LYNX-788_

#### GraphQL `OrderTotal`回應中的新`grand_total_excl_tax`欄位

新欄位`OrderTotal.grand_total_excl_tax`已新增至GraphQL訂單回應。 此欄位提供訂單不含稅的總計，讓直接從API存取不含稅總計變得更容易。

優點：

- 透過GraphQL輕鬆擷取任何訂單的總計（不含稅）。
- 簡化與需要免稅總額的外部系統的整合。
- 減少使用者端自訂計算的需求。

_LYNX-892_

#### 歷史訂單會顯示目前無存貨產品的詳細資料

即使產品已無庫存，歷史訂單現在仍會顯示明細專案的完整產品詳細資料，因此客戶和商家會保留購買專案的完整記錄。

_LYNX-913_

#### reCAPTCHA驗證已新增至`updateCustomer`、`updateCustomerV2`和`contactUs`個GraphQL變動

為對應的店面表單啟用reCAPTCHA時，`updateCustomer`、`updateCustomerV2`和`contactUs`個GraphQL變動現在會強制執行相同的驗證，有助於防止透過API自動濫用。

_LYNX-941_

#### reCAPTCHA驗證已新增至`applyCouponsToCart` GraphQL突變

為優惠券表單啟用reCAPTCHA時，`applyCouponsToCart` GraphQL突變現在會強制執行相同的驗證，有助於防止透過API進行優惠券程式碼列舉。

_LYNX-942_

#### B2B GraphQL API `customer_id`欄位已還原並完全支援

B2B GraphQL API中的`customer_id`欄位已還原，現在會在公司管理查詢和變動中傳回正確的值。 之前，該欄位已棄用並傳回`null`，因此其對B2B整合的效用受到限制。

_LYNX-955_

### 管理員UI

#### 型錄價格規則網格的「動作」功能表

Commerce管理員中的&#x200B;**目錄價格規則**&#x200B;格線現在包含&#x200B;**動作**&#x200B;功能表，可讓商家一次啟用、停用或刪除多個規則。 如此一來，目錄價格規則管理與可用於&#x200B;**購物車價格規則**&#x200B;的現有大量動作一致，大幅減少管理大型規則集所需的時間。

_AC-13916_

#### 用於內容暫存的行動檢視預覽

Admin中的分段預覽功能現在可正確呈現瀏覽器模擬的行動裝置預覽，因此商家可以在行動裝置上線前檢視分段更新在行動裝置上的顯示情形。

_ACP2E-3397 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/520f9e30)_

#### 新的管理員設定可在登入時控制訪客和客戶購物車合併行為

當訪客登入且已有客戶購物車時，商家現在可以選擇合併購物車專案的方式：

- **訪客優先順序** — 使用訪客購物車數量。
- **客戶優先順序** — 使用客戶購物車數量。
- **合併數量** （預設） — 加總兩個數量。

在&#x200B;**商店** > **組態** > **銷售** > **結帳**&#x200B;中，在&#x200B;**購物車合併偏好設定**&#x200B;下設定此行為。 此設定適用於所有產品型別，讓商家在登入時可完全控制訪客和客戶購物車的合併方式。

_LYNX-889_

### Braintree

#### 快速簽出

- **Google Pay快速付款表中的促銷優惠方案**

  Google Pay快速付款表現在支援促銷與優惠代碼。 購物者可以直接在Google付款表內套用、檢視和移除Commerce購物車促銷活動，好讓快速結帳客戶可獲得與標準結帳流程相同的折扣和獎勵。

  _BUNDLE-3476_

- **Apple Pay快速付款表中的促銷優惠方案**

  Apple Pay快速付款表現在支援促銷與優惠代碼。 購物者可直接在Apple Pay工作表中套用優惠券，因此快速結帳使用者可享有與標準結帳流程相同的折扣和促銷活動。

  _BUNDLE-3477_

- 在Chrome和Firefox上&#x200B;**Apple Pay**

  Apple Pay現在可用於Chrome和Firefox，而不僅僅是Safari。 啟用Apple Pay Express後，PDP、迷你購物車、購物車和結帳頁面上會提供Apple Pay按鈕，而客戶透過iPhone掃描程式碼即可完成付款。

  _BUNDLE-3478_

- **PayPal Express的伺服器端送貨回撥**

  PayPal Express送貨回撥已從使用者端移至伺服器端。 這直接在PayPal模式中提供動態出貨方法、即時成本計算以及精確的購物車層級詳細資訊，進而提升可靠性並為未來功能（例如連絡人模組支援、應用程式切換流程及Venmo Express）奠定基礎。

  _BUNDLE-3479_

- **美國商家快速結帳的PayPal連絡模組**

  我們為美國商家推出新的PayPal連絡人模組。 啟用後，使用PayPal Express的買家可以在快捷流程（PDP、迷你購物車、購物車、結帳快遞）期間，直接在PayPal模式中檢視並更新與商家共用的電子郵件地址和電話號碼。 接著，選取的聯絡詳細資料會儲存在Commerce訂單中。

  _BUNDLE-3480_

#### 付款方法

- **Braintree付款的ELO卡型別支援**

  新增Braintree支付中ELO卡型別的支援。 管理員可以在信用卡設定中啟用ELO，客戶可以在結帳時使用ELO卡付款。

  _BUNDLE-3464_

- 波蘭購物者的&#x200B;**BLIK當地付款方式**

  新增BLIK，作為波蘭購物者的全新當地付款方式。 這可在現有Braintree當地支付方式(LPM)流程中實現基於銀行的安全的BLIK支付，改善波蘭客戶的結帳便利性和轉換。

  _BUNDLE-3481_

- **依商業發票付款 — 德國的新的BNPL付款方式**

  已新增[!DNL Pay Upon Invoice]作為德國買家的新本機付款方式。 [!DNL Pay Upon Invoice]是由PayPal和Ratepay支援的「立即購買，稍後付款(BNPL)」選項(「Rechnungskauf mit Ratepay」)，客戶可在30天內先收到貨品並支付發票，而不需要PayPal帳戶。 因為這不是立即付款，所以定購是由PayPal的伺服器端webhook驅動。

  _BUNDLE-3475_

#### 卡片存放

- **透過帳戶區域存放Google Pay**

  在Braintree中啟用Google Pay Vault時，客戶現在可以透過帳戶區域儲存其Google Pay卡片。 儲存的卡片會顯示在已儲存的付款方式下，可用於結帳時未來的購買，並可由客戶刪除。 這將儲存庫支援擴展到卡片和PayPal之外，擴展到Google Pay。

  _BUNDLE-3459_

- **Braintree存放卡的即時帳戶更新程式(RTAU)**

  Braintree新增的即時帳戶更新程式(RTAU)功能可確保當卡片過期或被取代時，保險儲存的Visa、萬事達卡和Discover卡片詳細資料會自動更新。 這樣可將失敗的付款減至最少，使Commerce Vault保持最新狀態，並跳過不支援的型別（預付、Apple支付、Google支付），而不會發生錯誤。

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

#### SRI雜湊儲存重構後，多主題和多地區設定存放區的頁面載入速度更快

SRI雜湊儲存現在會依區域、主題和區域設定產生個別檔案，而非單一大型`sri-hashes.json`檔案。 這項變更可確保每個頁面都只載入相關的雜湊檔案，進而縮短頁面載入時間，並降低使用多個主題或區域設定的商店的記憶體使用量。

_AC-16113 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/bc83cd2c)_

#### 新增與PHPUnit 12的相容性

Adobe Commerce Composer相依性已升級為`phpunit/phpunit` 12.x。 所有測試都更新為相容性、改善安全性，並與最新的PHPUnit功能保持一致。 此升級可讓Adobe Commerce為未來的PHP和PHPUnit發行做好準備。

_AC-14808_

#### 新增與RabbitMQ 4.2的相容性

RabbitMQ 4.2現在是支援的訊息代理人。 此更新是短期相容性路徑，可讓依賴AMQP通訊協定的商戶在2026年2月RabbitMQ 4.1支援終止前繼續使用RabbitMQ，而不需立即移轉至STOMP。 對於長期部署，請使用Apache ActiveMQ Artemis作為RabbitMQ的長期替代方案。

_AC-16117_

#### Apache ActiveMQ Artemis是RabbitMQ的長期替代方案

Apache ActiveMQ Artemis是Adobe Commerce的建議長期訊息代理人，受RabbitMQ 4.1相關的支援終止風險所驅動。 Commerce發行版本2.4.6到2.4.9完全支援ActiveMQ Artemis。 在Adobe Commerce Cloud上，它會以AWS ActiveMQ的形式提供，以用於雲端原生部署。 佇列消費者和發佈者都可以設定為使用STOMP。


現有的RabbitMQ 4安裝仍與想要在短期內繼續使用目前訊息佇列服務的商戶相容 — 請參閱上述[新增與RabbitMQ 4.2](#add-compatibility-with-rabbitmq-42)的相容性。 規劃移轉至ActiveMQ Artemis以獲得長期支援。

_AC-14558_

#### 新增對Valkey 9.x的支援

Adobe Commerce 2.4.9擴大對Valkey的支援，作為與Redis相容的快取後端：

- **Valkey 9.x** — Adobe Commerce 2.4.9中推出的全面支援，包括與Redis的完整CLI命令同位功能，以及更新的管理及雲端組態選項，以便順暢設定。 這項工作是由Redis 7.2支援終止和授權變更所推動，為商家提供了可靠、完全受支援的Redis替代方案。

_AC-14103、AC-14604、AC-16122_

#### 新增對OpenSearch 3.x的支援

Adobe Commerce 2.4.9與OpenSearch 3.x完全相容，最新的次要版本現在是建議的搜尋引擎。 商戶可享有更優異的效能、安全性和長期支援，同時保留與OpenSearch 2.x的回溯相容性。

_AC-11846、AC-16403_

#### 新增對MariaDB 11.8和12.x的支援

MariaDB 11.8和12.x現在是支援的資料庫版本，讓商家能夠採用最新版本，以改善SQL效能和長期平台穩定性。

_AC-16533_

### PHP和撰寫器

#### php 8.5相容性

Adobe Commerce 2.4.9現在支援PHP 8.5和PHP 8.4，可讓您在最新安全且相容的PHP版本上執行您的商店。 所有核心功能、套件擴充功能（包括頁面產生器、B2B、Braintree等）和Adobe SaaS服務都與PHP 8.5相容。

- PHP 8.5和8.4完全受支援。
- PHP 8.3僅允許用於升級目的（不建議用於生產）。
- 確保Adobe Commerce安裝符合PCI規範並符合未來需求。

_AC-15615_

#### PHP 8.2支援已移除

從Adobe Commerce 2.4.9開始，不再支援PHP 8.2。 此平台現在針對PHP 8.3和更新版本，更新了核心程式碼、相依性和工具，以便在PHP 8.4和8.5上以簡潔可靠的方式執行。

_AC-15758_

#### 已驗證Composer 2.9相容性

Adobe Commerce 2.4.9與Composer 2.x完全相容，包括Composer 2.9。 與舊版Composer 2.x的回溯相容性得以保留，為使用最新版Composer的商家和開發人員確保穩定的建置和部署體驗。

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

從Adobe Commerce 2.4.9開始，已過時的Zend_Cache元件已由Symfony Cache元件取代。 此更新增強了快取效能和可維護性，並確保與PHP 8.x和未來平台更新的長期相容性。 現有的快取後端和快取管理命令仍受到完整支援，不需變更即可進行目前的整合。

_AC-15823_

#### WYSIWYG編輯器從TinyMCE移轉至GegRTE

由於對TinyMCE 5和6的支援終止以及與TinyMCE 7的授權不相容，Adobe Commerce WYSIWYG編輯器已移轉至開放原始碼[GreatRTE](https://hugerte.org/)編輯器。 此移轉確保Adobe Commerce仍符合開放原始碼授權，避免已知的TinyMCE 6漏洞，並為商家和開發人員提供現代且受支援的編輯體驗。

_AC-14568_

#### 原生MVC實作會取代Laminas MVC

Adobe Commerce已引進原生MVC實作，取代舊有的Laminas MVC，以確保超越PHP 8.5的長期相容性和穩定性。 此變更可加強效能、減少外部相依性，並為Commerce提供更符合未來需求的基礎。

_AC-15160_

#### 官方Symfony 7.4 LTS支援

在Adobe Commerce 2.4.9平台更新中，所有Symfony相依性均已更新至最新的Symfony LTS 7.4版本。 所有延伸Symfony核心類別的自訂類別都已更新符合最新Symfony要求的型別宣告和方法簽章，防止相容性問題，並確保順利轉換至更新的框架元件。

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

現在，管理員使用者只需設定商家其中一個已啟用的2FA提供者（例如，Google Authenticator或U2F），即可存取管理員面板。 之後可視需要設定其他啟用的提供者。 先前，當啟用多個2FA提供者時，每個管理員使用者都必須在登入前設定所有這些2FA提供者，這會導致使用者無法存取每個提供者。

_AC-8253 - [GitHub程式碼貢獻](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

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
