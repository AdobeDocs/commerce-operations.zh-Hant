---
source-git-commit: a3fa25993f365a85307db45ef16f68eeb12604bb
workflow-type: tm+mt
source-wordcount: '2192'
ht-degree: 0%

---
# Magento Open Source套件

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source使用撰寫器來管理PHP套件。

此 `composer.json` 檔案聲明包清單，而 `composer.lock` 檔案會儲存用來建置Adobe Commerce或Magento Open Source安裝的套件完整清單（每個套件及其相依性的完整版本）。

以下參考檔案是從 `composer.lock` 檔案，且涵蓋Magento Open Source2.4.5中包含的必要套件。

## 相依性

`magento/product-community-edition 2.4.5` 具有下列相依性：

```config
colinmollenhour/cache-backend-file: ~1.4.1
colinmollenhour/cache-backend-redis: 1.14.2
colinmollenhour/credis: 1.13.0
colinmollenhour/php-redis-session-abstract: ~1.4.5
composer/composer: ^1.9 || ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0
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
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.14
guzzlehttp/guzzle: ^7.4.2
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ~4.5.0
laminas/laminas-db: ^2.15.0
laminas/laminas-dependency-plugin: ^2.2.0
laminas/laminas-di: ^3.7.0
laminas/laminas-escaper: ~2.10.0
laminas/laminas-eventmanager: ^3.5.0
laminas/laminas-feed: ^2.17.0
laminas/laminas-http: ^2.15.0
laminas/laminas-mail: ^2.16.0
laminas/laminas-mime: ^2.9.1
laminas/laminas-modulemanager: ^2.11.0
laminas/laminas-mvc: ^3.3.3
laminas/laminas-servicemanager: ^3.11.0
laminas/laminas-soap: ^2.10.0
laminas/laminas-stdlib: ^3.7.1
laminas/laminas-uri: ^2.9.1
laminas/laminas-validator: ^2.17.0
league/flysystem: ~2.4.5
league/flysystem-aws-s3-v3: ^2.4.3
lib-libxml: *
magento/adobe-stock-integration: 2.1.4
magento/composer: ~1.8.0
magento/composer-dependency-version-audit-plugin: ~0.1
magento/framework: 103.0.5
magento/framework-amqp: 100.4.3
magento/framework-bulk: 101.0.1
magento/framework-message-queue: 100.4.5
magento/google-shopping-ads: 4.0.1
magento/inventory-metapackage: 1.2.5
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.3.0
magento/magento2-base: 2.4.5
magento/module-admin-adobe-ims: 100.4.0
magento/module-admin-analytics: 100.4.4
magento/module-admin-notification: 100.4.4
magento/module-adobe-ims: 2.1.4
magento/module-adobe-ims-api: 2.1.2
magento/module-advanced-pricing-import-export: 100.4.5
magento/module-advanced-search: 100.4.3
magento/module-amqp: 100.4.2
magento/module-analytics: 100.4.5
magento/module-asynchronous-operations: 100.4.5
magento/module-authorization: 100.4.5
magento/module-aws-s3: 100.4.3
magento/module-backend: 102.0.5
magento/module-backup: 100.4.5
magento/module-bundle: 101.0.5
magento/module-bundle-graph-ql: 100.4.5
magento/module-bundle-import-export: 100.4.4
magento/module-cache-invalidate: 100.4.3
magento/module-captcha: 100.4.5
magento/module-cardinal-commerce: 100.4.3
magento/module-catalog: 104.0.5
magento/module-catalog-analytics: 100.4.2
magento/module-catalog-cms-graph-ql: 100.4.1
magento/module-catalog-customer-graph-ql: 100.4.4
magento/module-catalog-graph-ql: 100.4.5
magento/module-catalog-import-export: 101.1.5
magento/module-catalog-inventory: 100.4.5
magento/module-catalog-inventory-graph-ql: 100.4.2
magento/module-catalog-rule: 101.2.5
magento/module-catalog-rule-configurable: 100.4.4
magento/module-catalog-rule-graph-ql: 100.4.2
magento/module-catalog-search: 102.0.5
magento/module-catalog-url-rewrite: 100.4.5
magento/module-catalog-url-rewrite-graph-ql: 100.4.3
magento/module-catalog-widget: 100.4.5
magento/module-checkout: 100.4.5
magento/module-checkout-agreements: 100.4.4
magento/module-checkout-agreements-graph-ql: 100.4.1
magento/module-cms: 104.0.5
magento/module-cms-graph-ql: 100.4.2
magento/module-cms-url-rewrite: 100.4.4
magento/module-cms-url-rewrite-graph-ql: 100.4.3
magento/module-compare-list-graph-ql: 100.4.1
magento/module-config: 101.2.5
magento/module-configurable-import-export: 100.4.3
magento/module-configurable-product: 100.4.5
magento/module-configurable-product-graph-ql: 100.4.5
magento/module-configurable-product-sales: 100.4.2
magento/module-contact: 100.4.4
magento/module-cookie: 100.4.5
magento/module-cron: 100.4.5
magento/module-csp: 100.4.4
magento/module-currency-symbol: 100.4.3
magento/module-customer: 103.0.5
magento/module-customer-analytics: 100.4.2
magento/module-customer-downloadable-graph-ql: 100.4.1
magento/module-customer-graph-ql: 100.4.5
magento/module-customer-import-export: 100.4.5
magento/module-deploy: 100.4.5
magento/module-developer: 100.4.5
magento/module-dhl: 100.4.4
magento/module-directory: 100.4.5
magento/module-directory-graph-ql: 100.4.3
magento/module-downloadable: 100.4.5
magento/module-downloadable-graph-ql: 100.4.5
magento/module-downloadable-import-export: 100.4.4
magento/module-eav: 102.1.5
magento/module-eav-graph-ql: 100.4.2
magento/module-elasticsearch: 101.0.5
magento/module-elasticsearch-6: 100.4.5
magento/module-elasticsearch-7: 100.4.5
magento/module-email: 101.1.5
magento/module-encryption-key: 100.4.3
magento/module-fedex: 100.4.3
magento/module-gift-message: 100.4.4
magento/module-gift-message-graph-ql: 100.4.3
magento/module-google-adwords: 100.4.2
magento/module-google-analytics: 100.4.1
magento/module-google-gtag: 100.4.0
magento/module-google-optimizer: 100.4.4
magento/module-graph-ql: 100.4.5
magento/module-graph-ql-cache: 100.4.2
magento/module-grouped-catalog-inventory: 100.4.2
magento/module-grouped-import-export: 100.4.3
magento/module-grouped-product: 100.4.5
magento/module-grouped-product-graph-ql: 100.4.5
magento/module-import-export: 101.0.5
magento/module-indexer: 100.4.5
magento/module-instant-purchase: 100.4.4
magento/module-integration: 100.4.5
magento/module-jwt-framework-adapter: 100.4.1
magento/module-jwt-user-token: 100.4.0
magento/module-layered-navigation: 100.4.5
magento/module-login-as-customer: 100.4.5
magento/module-login-as-customer-admin-ui: 100.4.5
magento/module-login-as-customer-api: 100.4.4
magento/module-login-as-customer-assistance: 100.4.4
magento/module-login-as-customer-frontend-ui: 100.4.4
magento/module-login-as-customer-graph-ql: 100.4.2
magento/module-login-as-customer-log: 100.4.3
magento/module-login-as-customer-page-cache: 100.4.4
magento/module-login-as-customer-quote: 100.4.3
magento/module-login-as-customer-sales: 100.4.4
magento/module-marketplace: 100.4.3
magento/module-media-content: 100.4.3
magento/module-media-content-api: 100.4.4
magento/module-media-content-catalog: 100.4.3
magento/module-media-content-cms: 100.4.3
magento/module-media-content-synchronization: 100.4.4
magento/module-media-content-synchronization-api: 100.4.3
magento/module-media-content-synchronization-catalog: 100.4.2
magento/module-media-content-synchronization-cms: 100.4.2
magento/module-media-gallery: 100.4.4
magento/module-media-gallery-api: 101.0.4
magento/module-media-gallery-catalog: 100.4.2
magento/module-media-gallery-catalog-integration: 100.4.2
magento/module-media-gallery-catalog-ui: 100.4.2
magento/module-media-gallery-cms-ui: 100.4.2
magento/module-media-gallery-integration: 100.4.4
magento/module-media-gallery-metadata: 100.4.3
magento/module-media-gallery-metadata-api: 100.4.2
magento/module-media-gallery-renditions: 100.4.3
magento/module-media-gallery-renditions-api: 100.4.2
magento/module-media-gallery-synchronization: 100.4.4
magento/module-media-gallery-synchronization-api: 100.4.3
magento/module-media-gallery-synchronization-metadata: 100.4.1
magento/module-media-gallery-ui: 100.4.4
magento/module-media-gallery-ui-api: 100.4.3
magento/module-media-storage: 100.4.4
magento/module-message-queue: 100.4.5
magento/module-msrp: 100.4.4
magento/module-msrp-configurable-product: 100.4.2
magento/module-msrp-grouped-product: 100.4.2
magento/module-multishipping: 100.4.5
magento/module-mysql-mq: 100.4.3
magento/module-new-relic-reporting: 100.4.3
magento/module-newsletter: 100.4.5
magento/module-newsletter-graph-ql: 100.4.2
magento/module-offline-payments: 100.4.3
magento/module-offline-shipping: 100.4.4
magento/module-page-cache: 100.4.5
magento/module-payment: 100.4.5
magento/module-payment-graph-ql: 100.4.0
magento/module-paypal: 101.0.5
magento/module-paypal-captcha: 100.4.2
magento/module-paypal-graph-ql: 100.4.3
magento/module-persistent: 100.4.5
magento/module-product-alert: 100.4.4
magento/module-product-video: 100.4.5
magento/module-quote: 101.2.5
magento/module-quote-analytics: 100.4.4
magento/module-quote-bundle-options: 100.4.1
magento/module-quote-configurable-options: 100.4.1
magento/module-quote-downloadable-links: 100.4.1
magento/module-quote-graph-ql: 100.4.5
magento/module-related-product-graph-ql: 100.4.2
magento/module-release-notification: 100.4.3
magento/module-remote-storage: 100.4.3
magento/module-reports: 100.4.5
magento/module-require-js: 100.4.1
magento/module-review: 100.4.5
magento/module-review-analytics: 100.4.2
magento/module-review-graph-ql: 100.4.1
magento/module-robots: 101.1.1
magento/module-rss: 100.4.3
magento/module-rule: 100.4.4
magento/module-sales: 103.0.5
magento/module-sales-analytics: 100.4.2
magento/module-sales-graph-ql: 100.4.5
magento/module-sales-inventory: 100.4.2
magento/module-sales-rule: 101.2.5
magento/module-sales-sequence: 100.4.2
magento/module-sample-data: 100.4.3
magento/module-search: 101.1.5
magento/module-security: 100.4.5
magento/module-send-friend: 100.4.3
magento/module-send-friend-graph-ql: 100.4.1
magento/module-shipping: 100.4.5
magento/module-sitemap: 100.4.4
magento/module-store: 101.1.5
magento/module-store-graph-ql: 100.4.3
magento/module-swagger: 100.4.4
magento/module-swagger-webapi: 100.4.1
magento/module-swagger-webapi-async: 100.4.1
magento/module-swatches: 100.4.5
magento/module-swatches-graph-ql: 100.4.3
magento/module-swatches-layered-navigation: 100.4.1
magento/module-tax: 100.4.5
magento/module-tax-graph-ql: 100.4.1
magento/module-tax-import-export: 100.4.4
magento/module-theme: 101.1.5
magento/module-theme-graph-ql: 100.4.2
magento/module-translation: 100.4.5
magento/module-ui: 101.2.5
magento/module-ups: 100.4.5
magento/module-url-rewrite: 102.0.4
magento/module-url-rewrite-graph-ql: 100.4.4
magento/module-user: 101.2.5
magento/module-usps: 100.4.4
magento/module-variable: 100.4.3
magento/module-vault: 101.2.5
magento/module-vault-graph-ql: 100.4.1
magento/module-version: 100.4.2
magento/module-webapi: 100.4.4
magento/module-webapi-async: 100.4.3
magento/module-webapi-security: 100.4.2
magento/module-weee: 100.4.5
magento/module-weee-graph-ql: 100.4.2
magento/module-widget: 101.2.5
magento/module-wishlist: 101.2.5
magento/module-wishlist-analytics: 100.4.3
magento/module-wishlist-graph-ql: 100.4.5
magento/page-builder: 1.7.2
magento/security-package: 1.1.4
magento/theme-adminhtml-backend: 100.4.5
magento/theme-frontend-blank: 100.4.5
magento/theme-frontend-luma: 100.4.5
magento/zendframework1: ~1.15.0
monolog/monolog: ^2.7
paypal/module-braintree: 4.4.0
pelago/emogrifier: ^6.0.0
php: ~7.4.0||~8.1.0
php-amqplib/php-amqplib: ~3.2.0
phpseclib/mcrypt_compat: ~2.0.2
phpseclib/phpseclib: ~3.0.13
ramsey/uuid: ~4.2.0
symfony/console: ~4.4.0
symfony/process: ~4.4.0
tedivm/jshrink: ~1.4.0
temando/module-shipping: 2.0.0
tubalmartin/cssmin: 4.1.1
web-token/jwt-framework: ^v2.2.7
webonyx/graphql-php: ~14.11.6
wikimedia/less.php: ^3.0.0
```

## 第三方授權

### Apache-2.0、LGPL-2.1-only

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>資料庫</td>
    <td>用於Elasticsearch的PHP客戶端</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
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
    <td>AWS PHP的常見運行時</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>資料庫</td>
    <td>AWS SDK for PHP — 在PHP專案中使用Amazon Web Services</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>元包</td>
    <td>BraintreeMagento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>資料庫</td>
    <td>Javascript版本LESS的PHP埠http://lesscss.org（最初由Josh Schmidt維護）</td>
  </tr>
  </tbody>
</table>

### BSD-2 — 子句

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">培根/培根 — qr碼</a>
    </td>
    <td>資料庫</td>
    <td>BaconQrCode是PHP的QR碼生成器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">貝貝雷伊/阿塞特</a>
    </td>
    <td>資料庫</td>
    <td>精簡斷言程式庫，以便在業務模型中進行輸入驗證。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>資料庫</td>
    <td>PHP 7.1枚舉實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe writer</a>
    </td>
    <td>資料庫</td>
    <td>安全寫檔案的工具，以避免競爭條件</td>
  </tr>
  </tbody>
</table>

### BSD-3 — 子句

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento-module</td>
    <td>庫存Zend_Cache_Backend_File後端對於標籤的清除效能極差，導致它隨著快取項目數增加而變得無法使用。 此後端會進行許多變更，導致效能大幅提升，尤其是標籤清除。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>使用Redis的Zend_Cache後端完全支援標籤。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>資料庫</td>
    <td>具有樂觀鎖定的基於Redis的會話處理程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>資料庫</td>
    <td>reCAPTCHA的用戶端程式庫，此免費服務可保護網站免受垃圾郵件和濫用。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">拉米納斯/拉米納斯 — 卡普查</a>
    </td>
    <td>資料庫</td>
    <td>使用Figlet、影像、ReCaptcha等產生及驗證CAPTCHA</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">層粘連碼</a>
    </td>
    <td>資料庫</td>
    <td>PHP Reflection API的擴充功能、靜態程式碼掃描和程式碼產生</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>資料庫</td>
    <td>提供了基於嵌套對象屬性的用戶介面，用於在應用程式代碼中訪問此配置資料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">拉米納/拉米納 — db</a>
    </td>
    <td>資料庫</td>
    <td>資料庫抽象層、SQL抽象、結果集抽象，以及RowDataGateway和TableDataGateway實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-dependency-plugin.git">laminas/laminas-dependency-plugin</a>
    </td>
    <td>composer-plugin</td>
    <td>將zendframework和zfcampus軟體包替換為其Laminas項目等價項。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">拉米納/拉米納</a>
    </td>
    <td>資料庫</td>
    <td>PSR-11容器的自動依賴注入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">層帶/層帶擒縱機</a>
    </td>
    <td>資料庫</td>
    <td>安全無虞地逸出HTML、HTML屬性、JavaScript、CSS和URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>資料庫</td>
    <td>觸發和偵聽PHP應用程式內的事件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">層帶/層帶供料</a>
    </td>
    <td>資料庫</td>
    <td>提供建立和使用RSS和原子源的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas/http</a>
    </td>
    <td>資料庫</td>
    <td>為執行超文本傳輸協定(HTTP)請求提供了簡單的介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>資料庫</td>
    <td>為將原生PHP序列化為JSON和將JSON解碼為原生PHP提供了方便的方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">層帶/層帶裝載機</a>
    </td>
    <td>資料庫</td>
    <td>自動載入和外掛程式載入策略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">拉米納/拉米納郵件</a>
    </td>
    <td>資料庫</td>
    <td>提供通用功能來撰寫和發送文本和MIME相容的多部分電子郵件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas/mime</a>
    </td>
    <td>資料庫</td>
    <td>建立和分析MIME消息和部件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>資料庫</td>
    <td>用於laminas-mvc應用的模組化應用系統</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas/mvc</a>
    </td>
    <td>資料庫</td>
    <td>Laminas的事件驅動MVC層，包括MVC應用程式、控制器和插件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas/recaptcha</a>
    </td>
    <td>資料庫</td>
    <td>ReCaptcha Web服務的OOP包裝</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas路由器</a>
    </td>
    <td>資料庫</td>
    <td>用於HTTP和控制台應用程式的靈活路由系統</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>資料庫</td>
    <td>建立基於反射的RPC伺服器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas服務管理器</a>
    </td>
    <td>資料庫</td>
    <td>工廠驅動的依賴注射容器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">層帶/層帶會話</a>
    </td>
    <td>資料庫</td>
    <td>物件導向的PHP會話和儲存介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">層粘蛋白/層粘蛋白皂</a>
    </td>
    <td>資料庫</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas/stdlib</a>
    </td>
    <td>資料庫</td>
    <td>SPL擴展、陣列實用程式、錯誤處理程式等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">層疊/層疊文本</a>
    </td>
    <td>資料庫</td>
    <td>建立FIGlet和基於文本的表</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>資料庫</td>
    <td>輔助操作和驗證「統一資源標識符」(URI)的元件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas驗證器</a>
    </td>
    <td>資料庫</td>
    <td>適用於多種域的驗證類，以及連結驗證器以建立複雜驗證標準的能力</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">層帶/層帶視圖</a>
    </td>
    <td>資料庫</td>
    <td>靈活的視圖層支援和提供多個視圖層、幫助器等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">拉米納斯/拉米納斯 — 贊德框架橋</a>
    </td>
    <td>資料庫</td>
    <td>將舊式ZF類名稱別名用於Laminas Project。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php剖析器</a>
    </td>
    <td>資料庫</td>
    <td>以PHP編寫的PHP解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>資料庫</td>
    <td>在PHP中建置的Javascript縮制器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">圖巴馬丁/克斯明</a>
    </td>
    <td>資料庫</td>
    <td>YUI CSS壓縮器的PHP埠</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1或更新版本

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlputeral</a>
    </td>
    <td>資料庫</td>
    <td>在PHP中寫入的符合標準的HTML過濾器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>資料庫</td>
    <td>先前為videolvaro/php-amqplib。  此庫是AMQP協定的純PHP實現。 已經對RabbitMQ進行了測試。</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree/php</a>
    </td>
    <td>資料庫</td>
    <td>BraintreePHP客戶端庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">磚/數</a>
    </td>
    <td>資料庫</td>
    <td>任意精度算術庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>資料庫</td>
    <td>var_export()的強大替代，它可以導出封閉項和不帶__set_state()的對象</td>
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
      <a href="https://github.com/colinmollenhour/credis.git">科林莫倫霍爾/克雷德</a>
    </td>
    <td>資料庫</td>
    <td>Credis是連線至Redis金鑰值存放區的輕量型介面，可在有效能提升時包裝phpredis程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>資料庫</td>
    <td>可讓您找到系統CA套件組合的路徑，並包含Mozilla CA套件組合的後援。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">撰寫器/撰寫器</a>
    </td>
    <td>資料庫</td>
    <td>Composer可幫助您聲明、管理和安裝PHP項目的依賴項。 它可確保您的堆疊位置正確無誤。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>資料庫</td>
    <td>處理中繼資料縮制和擴充的小型公用程式程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">撰寫器/pcre</a>
    </td>
    <td>資料庫</td>
    <td>PCRE包裝庫，提供類型安全的preg_*替換。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">composer/semver</a>
    </td>
    <td>資料庫</td>
    <td>提供實用程式、版本限制剖析和驗證的Semver程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>資料庫</td>
    <td>SPDX許可證清單和驗證庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>資料庫</td>
    <td>在不執行Xdebug的情況下重新啟動程式。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">端陣/qr碼</a>
    </td>
    <td>資料庫</td>
    <td>Endroid QR碼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">齊穆埃爾/古茲萊斯特雷姆</a>
    </td>
    <td>資料庫</td>
    <td>要與elasticsearch-php一起使用的guzzle/streams（放棄）的分叉</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>資料庫</td>
    <td>與elasticsearch-php一起使用的guzzle/RingPHP（放棄）的分叉</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/fgrosse/PHPASN1.git">fgrosse/phpasn1</a>
    </td>
    <td>資料庫</td>
    <td>一種PHP框架，它允許您使用ITU-T X.690編碼規則對任意ASN.1結構進行編碼和解碼。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>資料庫</td>
    <td>Guzzle是PHP HTTP客戶端庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promises</a>
    </td>
    <td>資料庫</td>
    <td>Guzzle承諾圖書館</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>資料庫</td>
    <td>PSR-7報文實現，也提供常用實用程式方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json結構描述</a>
    </td>
    <td>資料庫</td>
    <td>驗證JSON結構的程式庫。</td>
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
    <td>AWS Flysystem的S3檔案系統適配器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>資料庫</td>
    <td>Flysystem的MIME類型檢測</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">單對數</a>
    </td>
    <td>資料庫</td>
    <td>將日誌發送到檔案、套接字、收件箱、資料庫和各種Web服務</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>資料庫</td>
    <td>聲明性指定如何從JSON檔案擷取元素</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>資料庫</td>
    <td>RFC 4648編碼的常時實現(Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>資料庫</td>
    <td>來自PHP 7的random_bytes()和random_int()的PHP 5.x填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">亞速爾/表情符</a>
    </td>
    <td>資料庫</td>
    <td>在您的HTML程式碼中，將CSS樣式轉換為內嵌樣式屬性</td>
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
    <td>適用於PHP專案的現代DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>資料庫</td>
    <td>PHP 5.x-8.x填充功能（用於MCRYPT擴展）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>資料庫</td>
    <td>PHP安全通信庫 — RSA、AES、SSH2、SFTP、X.509等的純PHP實施。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/容器</a>
    </td>
    <td>資料庫</td>
    <td>公用容器介面（PHP圖PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>資料庫</td>
    <td>事件處理的標準介面。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>資料庫</td>
    <td>HTTP用戶端的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>資料庫</td>
    <td>PSR-7 HTTP報文工廠的常見介面</td>
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
      <a href="https://github.com/ralouphie/getallheaders.git">拉盧菲/蓋塔勒海德</a>
    </td>
    <td>資料庫</td>
    <td>蓋塔頭的多填。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">拉姆西/集合</a>
    </td>
    <td>資料庫</td>
    <td>用於表示和操控集合的PHP庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>資料庫</td>
    <td>用於生成和使用通用唯一標識符(UUID)的PHP庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>資料庫</td>
    <td>針對PHP的CommonJS Promises/A的輕量型實作</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>資料庫</td>
    <td>PHP中寫入的CSS檔案的解析器</td>
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
    <td>PHAR檔案格式實用程式，用於PHP升級時</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>資料庫</td>
    <td>PHP的AES密鑰包。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/base64url.git">spomky-labs/base64url</a>
    </td>
    <td>資料庫</td>
    <td>Base 64 URL安全編碼/解碼PHP庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>資料庫</td>
    <td>一種PHP庫，用於根據RFC 4226（HOTP算法）和RFC 6238（TOTP算法）生成一次性密碼，並與Google Authenticator相容</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>資料庫</td>
    <td>可協助您尋找、載入、結合、自動填入及驗證任何類型的設定值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>資料庫</td>
    <td>輕鬆建立美觀且可測試的命令列介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>資料庫</td>
    <td>將CSS選擇器轉換為XPath表達式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/debug.git">symfony/debug</a>
    </td>
    <td>資料庫</td>
    <td>提供工具以便於調試PHP代碼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency inclestion</a>
    </td>
    <td>資料庫</td>
    <td>允許您標準化和集中在應用程式中構建對象的方式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">符合/過時合同</a>
    </td>
    <td>資料庫</td>
    <td>觸發淘汰通知的一般函式和慣例</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>資料庫</td>
    <td>提供管理錯誤和輕鬆調試PHP代碼的工具</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>資料庫</td>
    <td>提供工具，讓您的應用程式元件可借由發送事件並監聽事件來彼此通訊</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contracts</a>
    </td>
    <td>資料庫</td>
    <td>與發送事件相關的通用抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>資料庫</td>
    <td>為檔案系統提供基本實用程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>資料庫</td>
    <td>通過直觀的Fluent介面查找檔案和目錄</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-contracts</a>
    </td>
    <td>資料庫</td>
    <td>與HTTP客戶端相關的通用抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>資料庫</td>
    <td>為HTTP規範定義物件導向層</td>
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
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>資料庫</td>
    <td>類型函式的符號填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-idn</a>
    </td>
    <td>資料庫</td>
    <td>為國際網際網路的idn_to_ascii和idn_to_utf8函式填寫符號</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-normalizer</a>
    </td>
    <td>資料庫</td>
    <td>Intl的Normalizer類的Symfonypolyfill及相關函式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>資料庫</td>
    <td>Mbstring擴展的Symfony Polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>資料庫</td>
    <td>Symfony Polyfill將一些PHP 7.2+功能回溯到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>資料庫</td>
    <td>Symfony Polyfill將一些PHP 7.3+功能回溯到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>資料庫</td>
    <td>Symfony Polyfill將一些PHP 8.0+功能回溯到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>資料庫</td>
    <td>Symfony Polyfill將一些PHP 8.1+功能回溯到較低的PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>資料庫</td>
    <td>在子進程中執行命令</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-contracts</a>
    </td>
    <td>資料庫</td>
    <td>與寫入服務相關的通用抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>資料庫</td>
    <td>提供在任意PHP變數中游走的機制</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">防毒機/安全裝置</a>
    </td>
    <td>資料庫</td>
    <td>PHP核心函式會擲回例外，而非在錯誤時傳回FALSE</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony捆綁</td>
    <td>PHP和Symfony套件的JSON物件簽署和加密程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>資料庫</td>
    <td>用斷言驗證方法輸入/輸出，並帶有好的錯誤消息。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>資料庫</td>
    <td>GraphQL參考實作的PHP埠</td>
  </tr>
  </tbody>
</table>

### OSL-3.0、AFL-3.0

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>不適用</td>
  </tr>
  <tr>
    <td>
      temando/模組 — 卸貨器
    </td>
    <td>magento2-module</td>
    <td>從Magento2中刪除Temando多承運人運送擴展</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      temando/module-shipping
    </td>
    <td>元包</td>
    <td>Magento2的Temando多承運人運輸擴展</td>
  </tr>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2毒液/cborencode</a>
    </td>
    <td>資料庫</td>
    <td>用於PHP的CBOR編碼器</td>
  </tr>
  </tbody>
</table>

### 專屬

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>magento2-module</td>
    <td>從MagentoBraintree2.2.0模組取用Gene Commerce for PayPal。</td>
  </tr>
  </tbody>
</table>
