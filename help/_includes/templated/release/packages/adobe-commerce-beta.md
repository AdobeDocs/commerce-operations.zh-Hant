---
source-git-commit: d720b64f315d1e4b6fb7868d911eb3af089e3fa4
workflow-type: tm+mt
source-wordcount: '2459'
ht-degree: 0%

---
# Adobe Commerce套件

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock_beta.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock_beta.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce使用Composer來管理PHP套件。

此 `composer.json` 檔案會宣告套件清單，而 `composer.lock` file會儲存用來建置Adobe Commerce或Magento Open Source安裝的套件完整清單（每個套件的完整版本及其相依性）。

下列參考檔案產生自 `composer.lock` 檔，並涵蓋Adobe Commerce 2.4.7-beta2中的必要套件。

## 相依性

`magento/product-enterprise-edition 2.4.7-beta2` 具有下列相依性：

```config
adobe-commerce/extensions-metapackage: ~2.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.14
colinmollenhour/credis: ^1.13
colinmollenhour/php-redis-session-abstract: ^1.5
composer/composer: ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0 || ~8.5.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.16
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ^4.5
laminas/laminas-db: ^2.15
laminas/laminas-di: ^3.7
laminas/laminas-escaper: ^2.10
laminas/laminas-eventmanager: ^3.5
laminas/laminas-feed: ^2.17
laminas/laminas-file: ^2.11
laminas/laminas-filter: ^2.17
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.3
laminas/laminas-oauth: ^2.4
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.11
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.9.0
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework-foreign-key: 100.4.5
magento/magento-composer-installer: >=0.4.0
magento/magento2-ee-base: 2.4.7-beta2
magento/module-admin-gws: 100.4.7-beta2
magento/module-admin-gws-configurable-product: 100.4.3
magento/module-admin-gws-staging: 100.4.3
magento/module-advanced-catalog: 100.4.3
magento/module-advanced-checkout: 100.4.7-beta2
magento/module-advanced-rule: 100.4.4-beta2
magento/module-advanced-sales-rule: 100.4.4-beta2
magento/module-application-server: 100.4.0-beta2
magento/module-application-server-new-relic: 100.4.0-beta2
magento/module-async-order: 100.4.3-beta2
magento/module-async-order-graph-ql: 100.4.1
magento/module-aws-s3-customer-custom-attributes: 100.4.3
magento/module-aws-s3-gift-card-import-export: 100.4.3
magento/module-aws-s3-scheduled-import-export: 100.4.3
magento/module-banner: 101.2.7-beta2
magento/module-banner-customer-segment: 100.4.5-beta2
magento/module-banner-graph-ql: 100.4.3-beta2
magento/module-banner-staging: 100.4.1-beta2
magento/module-bundle-import-export-staging: 100.4.3
magento/module-bundle-staging: 100.4.7-beta2
magento/module-catalog-event: 101.1.6-beta2
magento/module-catalog-import-export-staging: 100.4.4-beta2
magento/module-catalog-inventory-staging: 100.4.5-beta2
magento/module-catalog-permissions: 100.4.7-beta2
magento/module-catalog-permissions-graph-ql: 100.4.5-beta2
magento/module-catalog-rule-staging: 100.4.7-beta2
magento/module-catalog-staging: 100.4.7-beta2
magento/module-catalog-staging-graph-ql: 100.4.6-beta2
magento/module-catalog-url-rewrite-staging: 100.4.6-beta2
magento/module-checkout-address-search: 100.4.6-beta2
magento/module-checkout-address-search-gift-registry: 100.4.2
magento/module-checkout-staging: 100.4.6-beta2
magento/module-cms-staging: 100.4.7-beta2
magento/module-configurable-product-staging: 100.4.6-beta2
magento/module-custom-attribute-management: 100.4.6-beta2
magento/module-customer-balance: 100.4.7-beta2
magento/module-customer-balance-graph-ql: 100.4.3
magento/module-customer-custom-attributes: 100.4.7-beta2
magento/module-customer-custom-attributes-graph-ql: 100.4.0-beta2
magento/module-customer-finance: 100.4.4-beta2
magento/module-customer-segment: 102.1.7-beta2
magento/module-customer-segment-graph-ql: 100.4.0-beta2
magento/module-deferred-total-calculating: 100.4.2-beta2
magento/module-downloadable-staging: 100.4.6-beta2
magento/module-elasticsearch-catalog-permissions: 100.4.3-beta2
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.2-beta2
magento/module-enterprise: 100.4.5-beta2
magento/module-gift-card: 101.3.7-beta2
magento/module-gift-card-account: 101.2.7-beta2
magento/module-gift-card-account-graph-ql: 100.4.4
magento/module-gift-card-graph-ql: 100.4.7-beta2
magento/module-gift-card-import-export: 100.4.4-beta2
magento/module-gift-card-staging: 100.4.4-beta2
magento/module-gift-message-staging: 100.4.4-beta2
magento/module-gift-registry: 101.2.7-beta2
magento/module-gift-registry-graph-ql: 100.4.2
magento/module-gift-wrapping: 101.2.6-beta2
magento/module-gift-wrapping-graph-ql: 100.4.4-beta2
magento/module-gift-wrapping-staging: 100.4.4-beta2
magento/module-google-optimizer-staging: 100.4.4-beta2
magento/module-google-tag-manager: 100.4.7-beta2
magento/module-grouped-product-staging: 100.4.5-beta2
magento/module-import-csv: 100.4.1-beta2
magento/module-import-csv-api: 100.4.1-beta2
magento/module-import-json: 100.4.0-beta2
magento/module-import-json-api: 100.4.0-beta2
magento/module-invitation: 100.4.6-beta2
magento/module-layered-navigation-staging: 100.4.4-beta2
magento/module-logging: 101.2.7-beta2
magento/module-login-as-customer-logging: 100.4.7-beta2
magento/module-login-as-customer-website-restriction: 100.4.4
magento/module-media-content-catalog-staging: 100.4.4-beta2
magento/module-msrp-staging: 100.4.5-beta2
magento/module-multiple-wishlist: 100.4.7-beta2
magento/module-multiple-wishlist-graph-ql: 100.4.2
magento/module-payment-staging: 100.4.4-beta2
magento/module-persistent-history: 100.4.4-beta2
magento/module-price-permissions: 100.4.3-beta2
magento/module-product-video-staging: 100.4.4-beta2
magento/module-promotion-permissions: 100.4.4-beta2
magento/module-quote-gift-card-options: 100.4.3
magento/module-quote-staging: 100.4.4-beta2
magento/module-reminder: 101.2.6-beta2
magento/module-remote-storage-commerce: 100.4.2
magento/module-resource-connections: 100.4.4-beta2
magento/module-review-staging: 100.4.4-beta2
magento/module-reward: 101.2.7-beta2
magento/module-reward-graph-ql: 100.4.5
magento/module-reward-staging: 100.4.4-beta2
magento/module-rma: 101.2.7-beta2
magento/module-rma-graph-ql: 100.4.6-beta2
magento/module-rma-staging: 100.4.4-beta2
magento/module-sales-archive: 101.0.5-beta2
magento/module-sales-rule-staging: 100.4.6-beta2
magento/module-scalable-checkout: 100.4.6-beta2
magento/module-scalable-inventory: 100.4.5-beta2
magento/module-scalable-oms: 100.4.5-beta2
magento/module-scheduled-import-export: 101.2.7-beta2
magento/module-search-staging: 100.4.5-beta2
magento/module-staging: 101.2.7-beta2
magento/module-staging-graph-ql: 100.4.3
magento/module-support: 101.2.6-beta2
magento/module-swat: 100.4.4
magento/module-target-rule: 101.2.7-beta2
magento/module-target-rule-graph-ql: 100.4.4-beta2
magento/module-versions-cms: 101.2.7-beta2
magento/module-versions-cms-page-cache: 100.4.2
magento/module-versions-cms-url-rewrite: 100.4.5-beta2
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.2
magento/module-visual-merchandiser: 100.4.7-beta2
magento/module-website-restriction: 100.4.6-beta2
magento/module-weee-staging: 100.4.4-beta2
magento/module-wishlist-gift-card: 100.4.2
magento/module-wishlist-gift-card-graph-ql: 100.4.2
magento/page-builder-commerce: 1.7.4-beta2
magento/product-community-edition: 2.4.7-beta2
magento/security-package-ee: 1.0.2-beta2
magento/theme-adminhtml-spectrum: 100.4.1
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0, <2.0.1
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
ramsey/uuid: ^4.2
symfony/console: ^5.4
symfony/intl: ^5.4
symfony/process: <=5.4.23
symfony/string: ^5.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
```

## 協力廠商授權

### Apache-2.0、LGPL-2.1-only

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      elasticsearch/elasticsearch
    </td>
    <td>資料庫</td>
    <td>Elasticsearch的PHP使用者端</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>資料庫</td>
    <td>OpenSearch的PHP使用者端</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>資料庫</td>
    <td>Adobe Stock API程式庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>資料庫</td>
    <td>適用於PHP的AWS Common Runtime</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>資料庫</td>
    <td>適用於PHP的AWS SDK — 在PHP專案中使用Amazon Web Services</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>中繼封裝</td>
    <td>BraintreeMagento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>資料庫</td>
    <td>LESS處理器的PHP連線埠</td>
  </tr>
  </tbody>
</table>

### BSD-2 — 子句

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">培根/培根 — qr-code</a>
    </td>
    <td>資料庫</td>
    <td>BaconQrCode是PHP的QR程式碼產生器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">beberlei/assert</a>
    </td>
    <td>資料庫</td>
    <td>業務模型中用於輸入驗證的精簡宣告程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>資料庫</td>
    <td>PHP 7.1列舉實作</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>資料庫</td>
    <td>安全寫入檔案的工具，避免競爭情況</td>
  </tr>
  </tbody>
</table>

### BSD-3 — 子句

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colimollenhour/cache-backend-file</a>
    </td>
    <td>magento-module</td>
    <td>庫存Zend_Cache_Backend_File後端透過標籤進行清除的效能極差，導致隨著快取專案數的增加無法使用。 此後端進行許多變更，大幅提升效能，尤其是標籤清除作業。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colimollenhour/php-redis-session-abstract</a>
    </td>
    <td>資料庫</td>
    <td>具有樂觀鎖定的Redis型工作階段處理常式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>資料庫</td>
    <td>在PHP中編碼和解碼JSON Web權杖(JWT)的簡單程式庫。 應符合目前的規格。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>資料庫</td>
    <td>reCAPTCHA使用者端程式庫，此免費服務可保護網站遠離垃圾郵件與不當使用。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">拉米納斯/拉米納斯 — 驗證碼</a>
    </td>
    <td>資料庫</td>
    <td>使用Figlet、影像、ReCaptcha等專案產生及驗證驗證碼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas碼</a>
    </td>
    <td>資料庫</td>
    <td>PHP Reflection API、靜態程式碼掃描和程式碼產生的擴充功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">層板/層板 — 組態</a>
    </td>
    <td>資料庫</td>
    <td>提供巢狀物件屬性型使用者介面，用於存取應用程式程式碼內的此設定資料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">層粘連體/層粘連體</a>
    </td>
    <td>資料庫</td>
    <td>強大的加密工具和密碼雜湊功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>資料庫</td>
    <td>資料庫抽象層、SQL抽象層、結果集抽象層，以及RowDataGateway和TableDataGateway實作</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">萊米納斯/萊米納斯 — 迪</a>
    </td>
    <td>資料庫</td>
    <td>PSR-11容器的自動化相依性插入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/laminas-escaper</a>
    </td>
    <td>資料庫</td>
    <td>安全且安全地逸出HTML、HTML屬性、JavaScript、CSS和URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>資料庫</td>
    <td>觸發並接聽PHP應用程式中的事件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">層疊/層疊 — 饋送</a>
    </td>
    <td>資料庫</td>
    <td>提供建立和使用RSS和Atom摘要的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>資料庫</td>
    <td>找到PHP類別檔案</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">層疊/層疊 — 濾鏡</a>
    </td>
    <td>資料庫</td>
    <td>以程式設計方式篩選及標準化資料和檔案</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>資料庫</td>
    <td>提供執行超文字傳輸通訊協定(HTTP)要求的簡易介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">雷米納斯/雷米納斯 — i18n</a>
    </td>
    <td>資料庫</td>
    <td>提供應用程式的翻譯，並篩選及驗證國際化值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>資料庫</td>
    <td>提供了將原生PHP序列化為JSON並將JSON解碼為原生PHP的便利方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">層疊/層疊 — 載入器</a>
    </td>
    <td>資料庫</td>
    <td>自動載入和外掛程式載入策略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">層疊/層疊 — 郵件</a>
    </td>
    <td>資料庫</td>
    <td>提供一般化的功能，以撰寫及傳送文字和MIME相容的多部分電子郵件訊息</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>資料庫</td>
    <td>建立加密安全的偽隨機數，並管理大整數</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">層板/層板MIME</a>
    </td>
    <td>資料庫</td>
    <td>建立和剖析MIME訊息和部分</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>資料庫</td>
    <td>適用於Laminas-mvc應用程式的模組化應用程式系統</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>資料庫</td>
    <td>Laminas的事件導向MVC層，包括MVC應用程式、控制器和外掛程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">雷米納斯/雷米納斯 — 奧auth</a>
    </td>
    <td>資料庫</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>資料庫</td>
    <td>提供輕量且有彈性的存取控制清單(ACL)實作，以進行許可權管理</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">拉米納斯/拉米納斯 — 雷卡普查</a>
    </td>
    <td>資料庫</td>
    <td>ReCaptcha Web服務的OOP包裝函式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas路由器</a>
    </td>
    <td>資料庫</td>
    <td>適用於HTTP和主控台應用程式的彈性路由系統</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>資料庫</td>
    <td>建立反射式RPC伺服器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>資料庫</td>
    <td>工廠驅動相依性注入容器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>資料庫</td>
    <td>PHP工作階段和儲存的物件導向介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">羊皮面/羊皮面</a>
    </td>
    <td>資料庫</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>資料庫</td>
    <td>SPL擴充功能、陣列公用程式、錯誤處理常式等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">層疊/層疊 — 文字</a>
    </td>
    <td>資料庫</td>
    <td>建立FIGlet和文字型表格</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>資料庫</td>
    <td>協助處理和驗證「統一資源識別碼(URI)」的元件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>資料庫</td>
    <td>適用於多種網域的驗證類別，以及鏈結驗證器以建立複雜驗證條件的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">萊米納斯/萊米納斯維尤</a>
    </td>
    <td>資料庫</td>
    <td>彈性檢視層可支援並提供多個檢視層、協助程式等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>資料庫</td>
    <td>將舊版ZF類別名稱命名為Laminas專案對等項。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>資料庫</td>
    <td>以PHP撰寫的PHP剖析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>資料庫</td>
    <td>內建於PHP的Javascript Minifier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>資料庫</td>
    <td>YUI CSS壓縮器的PHP連線埠</td>
  </tr>
  </tbody>
</table>

### BSD-3 — 條款 — 修改

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colimollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>使用Redis的Zend_Cache後端，完全支援標籤。</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1或更新版本

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">額則陽/htmlpurifier</a>
    </td>
    <td>資料庫</td>
    <td>以PHP撰寫的符合標準的HTML篩選器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>資料庫</td>
    <td>原稱videlalvaro/php-amqplib。  此程式庫是AMQP通訊協定的純PHP實作。 並針對RabbitMQ進行測試。</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>資料庫</td>
    <td>BraintreePHP使用者端程式庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">磚/數學</a>
    </td>
    <td>資料庫</td>
    <td>任意精確度算術程式庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">磚/varexporter</a>
    </td>
    <td>資料庫</td>
    <td>var_export()的強大替代方案，可在不使用__set_state()的情況下匯出關閉項和物件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>資料庫</td>
    <td>根據RFC 4648的Base32編碼器/解碼器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colimollenhour/credis</a>
    </td>
    <td>資料庫</td>
    <td>Credis是Redis索引鍵值存放區的輕量型介面，可在取得phpredis資料庫時將其包裝起來，以提升效能。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>資料庫</td>
    <td>可讓您尋找系統CA套件的路徑，並包含Mozilla CA套件的遞補內容。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">composer/class-map-generator</a>
    </td>
    <td>資料庫</td>
    <td>掃描PHP程式碼和產生類別對映的公用程式。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">作曲者/作曲者</a>
    </td>
    <td>資料庫</td>
    <td>Composer可協助您宣告、管理和安裝PHP專案的相依性。 它可確保您隨時隨地擁有正確的棧疊。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>資料庫</td>
    <td>處理中繼資料縮制和擴充的小型公用程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">composer/pcre</a>
    </td>
    <td>資料庫</td>
    <td>提供型別安全預浸料取代的PCRE包裝程_*庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">composer/semver</a>
    </td>
    <td>資料庫</td>
    <td>提供公用程式、版本限制剖析和驗證的伺服器程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>資料庫</td>
    <td>SPDX授權清單和驗證程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>資料庫</td>
    <td>在不使用Xdebug的情況下重新啟動程式。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/annotations.git">學說/註解</a>
    </td>
    <td>資料庫</td>
    <td>Docblock註解剖析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">學說/詞法分析器</a>
    </td>
    <td>資料庫</td>
    <td>PHP Doctrine Lexer剖析器程式庫，可用於自上而下的遞回下降剖析器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>資料庫</td>
    <td>Endroid QR碼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>資料庫</td>
    <td>要與elasticsearch-php一起使用的guzzle/streams （已捨棄）分支</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>資料庫</td>
    <td>要與elasticsearch-php一起使用的guzzle/RingPHP （已放棄）分支</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>資料庫</td>
    <td>Guzzle是PHP HTTP使用者端程式庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promise</a>
    </td>
    <td>資料庫</td>
    <td>Guzzle promise程式庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>資料庫</td>
    <td>PSR-7訊息實作，也提供通用公用程式方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>資料庫</td>
    <td>驗證json結構描述的程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">league/flysystem</a>
    </td>
    <td>資料庫</td>
    <td>PHP的檔案儲存抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>資料庫</td>
    <td>適用於Flysystem的AWS S3檔案系統配接卡。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>資料庫</td>
    <td>Flysystem的MIME型別偵測</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">獨白/獨白</a>
    </td>
    <td>資料庫</td>
    <td>將您的記錄傳送至檔案、通訊端、收件匣、資料庫和各種網站服務</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>資料庫</td>
    <td>以宣告方式指定如何從JSON檔案中擷取元素</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>資料庫</td>
    <td>RFC 4648編碼的常數時間實作(Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>資料庫</td>
    <td>PHP 7的random_bytes()和random_int()的PHP 5.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrifier</a>
    </td>
    <td>資料庫</td>
    <td>將CSS樣式轉換為HTML程式碼中的內嵌樣式屬性</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>資料庫</td>
    <td>將CSS選取器轉換為XPath查詢。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>資料庫</td>
    <td>PHP專案的現代DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclab/mcrypt_compat</a>
    </td>
    <td>資料庫</td>
    <td>PHP 5.x-8.x polyfill for mcrypt延伸模組</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclab/phpseclab</a>
    </td>
    <td>資料庫</td>
    <td>PHP Secure Communications Library - RSA、AES、SSH2、SFTP、X.509等的純PHP實作。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/cache</a>
    </td>
    <td>資料庫</td>
    <td>快取程式庫的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/clock</a>
    </td>
    <td>資料庫</td>
    <td>讀取時鐘的通用介面。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>資料庫</td>
    <td>通用容器介面（PHP圖PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>資料庫</td>
    <td>用於事件處理的標準介面。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>資料庫</td>
    <td>HTTP使用者端的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>資料庫</td>
    <td>PSR-7 HTTP訊息處理站的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>資料庫</td>
    <td>HTTP訊息的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>資料庫</td>
    <td>記錄程式庫的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>資料庫</td>
    <td>getallheaders的polyfill。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">拉姆齊/collection</a>
    </td>
    <td>資料庫</td>
    <td>用於表示和處理集合的PHP程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>資料庫</td>
    <td>用於產生和使用通用唯一識別碼(UUID)的PHP程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>資料庫</td>
    <td>PHP的CommonJS Promise/A的輕量級實作</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>資料庫</td>
    <td>以PHP撰寫之CSS檔案的剖析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>資料庫</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>資料庫</td>
    <td>PHAR檔案格式公用程式，用於當PHP將您變成像片時</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>資料庫</td>
    <td>簡單的Unix訊號處理常式，在訊號不支援輕鬆跨平台開發時無訊息失敗</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>資料庫</td>
    <td>PHP的AES金鑰換行。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>資料庫</td>
    <td>用於根據RFC 4226 （HOTP演演算法）和RFC 6238 （TOTP演演算法）產生一次性密碼並與Google Authenticator相容的PHP程式庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>資料庫</td>
    <td>用於管理公開金鑰基礎結構的PHP架構。 它包含X.509公開金鑰憑證、屬性憑證、憑證要求及憑證路徑驗證。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>資料庫</td>
    <td>協助您尋找、載入、組合、自動填寫及驗證任何型別的設定值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/主控台</a>
    </td>
    <td>資料庫</td>
    <td>輕鬆建立美觀且可測試的指令行介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>資料庫</td>
    <td>將CSS選取器轉換為XPath運算式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/相依性插入</a>
    </td>
    <td>資料庫</td>
    <td>可讓您標準化並集中處理應用程式中建構物件的方式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contract</a>
    </td>
    <td>資料庫</td>
    <td>用於觸發淘汰通知的通用函式和慣例</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>資料庫</td>
    <td>提供管理錯誤和輕鬆偵錯PHP程式碼的工具</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>資料庫</td>
    <td>提供工具，可讓您的應用程式元件透過傳送事件並接聽它們來彼此通訊</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contracts</a>
    </td>
    <td>資料庫</td>
    <td>與分派事件相關的一般抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/檔案系統</a>
    </td>
    <td>資料庫</td>
    <td>提供檔案系統的基本公用程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>資料庫</td>
    <td>透過直覺式的流暢介面尋找檔案和目錄</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>資料庫</td>
    <td>定義HTTP規格的物件導向圖層</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>資料庫</td>
    <td>提供將請求轉換為回應的結構化程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>資料庫</td>
    <td>為C intl擴充功能提供PHP取代層，其中包含來自ICU程式庫的其他資料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>資料庫</td>
    <td>Ctype函式的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>資料庫</td>
    <td>用於intl的grapheme_*函式的Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>資料庫</td>
    <td>intl的idn_to_ascii和idn_to_utf8函式的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>資料庫</td>
    <td>intl的Normalizer類別和相關函式的Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>資料庫</td>
    <td>Mbstring延伸的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>資料庫</td>
    <td>Symfony polyfill將一些PHP 7.2+功能回移植到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>資料庫</td>
    <td>Symfony polyfill將一些PHP 7.3+功能回移植到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>資料庫</td>
    <td>Symfony polyfill將一些PHP 8.0+功能回移植到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>資料庫</td>
    <td>Symfony polyfill將一些PHP 8.1+功能回移植到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>資料庫</td>
    <td>Symfony polyfill將一些PHP 8.3+功能回移植到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>資料庫</td>
    <td>執行子處理序中的命令</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">交響曲/服務合約</a>
    </td>
    <td>資料庫</td>
    <td>與撰寫服務相關的一般抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>資料庫</td>
    <td>為字串提供物件導向的API，並以統一的方式處理位元組、UTF-8字碼點和字首叢集</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>資料庫</td>
    <td>提供用於瀏覽任意PHP變數的機制</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>資料庫</td>
    <td>允許將任何可序列化的PHP資料結構匯出為純PHP程式碼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">編碼機器/保險箱</a>
    </td>
    <td>資料庫</td>
    <td>擲回例外狀況而非錯誤時傳回FALSE的PHP核心函式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>PHP和Symfony套件組合的JSON物件簽署和加密程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>資料庫</td>
    <td>驗證方法輸入/輸出的斷言，帶有不錯的錯誤訊息。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>資料庫</td>
    <td>GraphQL參考實作的PHP連線埠</td>
  </tr>
  </tbody>
</table>

### OSL-3.0、AFL-3.0

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>magento2-module</td>
    <td>不適用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>magento2-module</td>
    <td>不適用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>magento2-module</td>
    <td>不適用</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>不適用</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>資料庫</td>
    <td>PHP的CBOR編碼器</td>
  </tr>
  </tbody>
</table>

### Proprietary

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### proprietary

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>型別</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>magento2-module</td>
    <td>取自Gene Commerce for PayPal的MagentoBraintree2.2.0模組。</td>
  </tr>
  </tbody>
</table>
