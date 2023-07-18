---
source-git-commit: e883ab0e6fca468bd3701e6789ac5132c7f1ee4d
workflow-type: tm+mt
source-wordcount: '2491'
ht-degree: 0%

---
# Magento Open Source套件

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock_beta.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock_beta.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source使用Composer來管理PHP套件。

此 `composer.json` 檔案會宣告套件清單，而 `composer.lock` file會儲存用來建置Adobe Commerce或Magento Open Source安裝的套件完整清單（每個套件及其相依性的完整版本）。

下列參考檔案產生自 `composer.lock` 檔案，並涵蓋Magento Open Source2.4.7-beta1中包含的必要套件。

## 相依性

`magento/product-community-edition 2.4.7-beta1` 具有下列相依性：

```config
adobe-commerce/adobe-ims-metapackage: ^2.2
adobe-commerce/os-extensions-metapackage: ~1.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.14
colinmollenhour/credis: ^1.13
colinmollenhour/php-redis-session-abstract: ^1.5
composer/composer: ^2.0, !=2.2.16
doctrine/annotations: ^1.13
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
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/adobe-stock-integration: 2.1.6-beta1
magento/composer: ^1.9.0
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.7-beta1
magento/framework-amqp: 100.4.5-beta1
magento/framework-bulk: 101.0.3-beta1
magento/framework-message-queue: 100.4.7-beta1
magento/inventory-metapackage: 1.2.7-beta1
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento2-base: 2.4.7-beta1
magento/module-admin-analytics: 100.4.6-beta1
magento/module-admin-notification: 100.4.6-beta1
magento/module-advanced-pricing-import-export: 100.4.7-beta1
magento/module-advanced-search: 100.4.5-beta1
magento/module-amqp: 100.4.4-beta1
magento/module-analytics: 100.4.7-beta1
magento/module-async-config: 100.4.0-beta1
magento/module-asynchronous-operations: 100.4.7-beta1
magento/module-authorization: 100.4.7-beta1
magento/module-aws-s3: 100.4.5-beta1
magento/module-backend: 102.0.7-beta1
magento/module-backup: 100.4.7-beta1
magento/module-bundle: 101.0.7-beta1
magento/module-bundle-graph-ql: 100.4.7-beta1
magento/module-bundle-import-export: 100.4.6-beta1
magento/module-cache-invalidate: 100.4.5-beta1
magento/module-captcha: 100.4.7-beta1
magento/module-cardinal-commerce: 100.4.5-beta1
magento/module-catalog: 104.0.7-beta1
magento/module-catalog-analytics: 100.4.4-beta1
magento/module-catalog-cms-graph-ql: 100.4.3-beta1
magento/module-catalog-customer-graph-ql: 100.4.6-beta1
magento/module-catalog-graph-ql: 100.4.7-beta1
magento/module-catalog-import-export: 101.1.7-beta1
magento/module-catalog-inventory: 100.4.7-beta1
magento/module-catalog-inventory-graph-ql: 100.4.4-beta1
magento/module-catalog-rule: 101.2.7-beta1
magento/module-catalog-rule-configurable: 100.4.6-beta1
magento/module-catalog-rule-graph-ql: 100.4.4-beta1
magento/module-catalog-search: 102.0.7-beta1
magento/module-catalog-url-rewrite: 100.4.7-beta1
magento/module-catalog-url-rewrite-graph-ql: 100.4.5-beta1
magento/module-catalog-widget: 100.4.7-beta1
magento/module-checkout: 100.4.7-beta1
magento/module-checkout-agreements: 100.4.6-beta1
magento/module-checkout-agreements-graph-ql: 100.4.2
magento/module-cms: 104.0.7-beta1
magento/module-cms-graph-ql: 100.4.4-beta1
magento/module-cms-url-rewrite: 100.4.6-beta1
magento/module-cms-url-rewrite-graph-ql: 100.4.4
magento/module-compare-list-graph-ql: 100.4.3-beta1
magento/module-config: 101.2.7-beta1
magento/module-configurable-import-export: 100.4.5-beta1
magento/module-configurable-product: 100.4.7-beta1
magento/module-configurable-product-graph-ql: 100.4.7-beta1
magento/module-configurable-product-sales: 100.4.4-beta1
magento/module-contact: 100.4.6-beta1
magento/module-contact-graph-ql: 100.4.0-beta1
magento/module-cookie: 100.4.7-beta1
magento/module-cron: 100.4.7-beta1
magento/module-csp: 100.4.6-beta1
magento/module-currency-symbol: 100.4.5-beta1
magento/module-customer: 103.0.7-beta1
magento/module-customer-analytics: 100.4.4-beta1
magento/module-customer-downloadable-graph-ql: 100.4.3-beta1
magento/module-customer-graph-ql: 100.4.7-beta1
magento/module-customer-import-export: 100.4.7-beta1
magento/module-deploy: 100.4.7-beta1
magento/module-developer: 100.4.7-beta1
magento/module-dhl: 100.4.5
magento/module-directory: 100.4.7-beta1
magento/module-directory-graph-ql: 100.4.5-beta1
magento/module-downloadable: 100.4.7-beta1
magento/module-downloadable-graph-ql: 100.4.6
magento/module-downloadable-import-export: 100.4.5
magento/module-eav: 102.1.7-beta1
magento/module-eav-graph-ql: 100.4.4-beta1
magento/module-elasticsearch: 101.0.7-beta1
magento/module-elasticsearch-7: 100.4.7-beta1
magento/module-email: 101.1.7-beta1
magento/module-encryption-key: 100.4.5-beta1
magento/module-fedex: 100.4.5-beta1
magento/module-gift-message: 100.4.6-beta1
magento/module-gift-message-graph-ql: 100.4.5-beta1
magento/module-google-adwords: 100.4.4-beta1
magento/module-google-analytics: 100.4.3-beta1
magento/module-google-gtag: 100.4.2-beta1
magento/module-google-optimizer: 100.4.6-beta1
magento/module-graph-ql: 100.4.7-beta1
magento/module-graph-ql-cache: 100.4.4-beta1
magento/module-grouped-catalog-inventory: 100.4.4-beta1
magento/module-grouped-import-export: 100.4.5-beta1
magento/module-grouped-product: 100.4.7-beta1
magento/module-grouped-product-graph-ql: 100.4.7-beta1
magento/module-import-export: 101.0.7-beta1
magento/module-indexer: 100.4.7-beta1
magento/module-instant-purchase: 100.4.6-beta1
magento/module-integration: 100.4.7-beta1
magento/module-jwt-framework-adapter: 100.4.2
magento/module-jwt-user-token: 100.4.1
magento/module-layered-navigation: 100.4.7-beta1
magento/module-login-as-customer: 100.4.7-beta1
magento/module-login-as-customer-admin-ui: 100.4.7-beta1
magento/module-login-as-customer-api: 100.4.6-beta1
magento/module-login-as-customer-assistance: 100.4.6-beta1
magento/module-login-as-customer-frontend-ui: 100.4.5
magento/module-login-as-customer-graph-ql: 100.4.4-beta1
magento/module-login-as-customer-log: 100.4.5-beta1
magento/module-login-as-customer-page-cache: 100.4.5
magento/module-login-as-customer-quote: 100.4.4
magento/module-login-as-customer-sales: 100.4.5
magento/module-marketplace: 100.4.5-beta1
magento/module-media-content: 100.4.5-beta1
magento/module-media-content-api: 100.4.6-beta1
magento/module-media-content-catalog: 100.4.5-beta1
magento/module-media-content-cms: 100.4.5-beta1
magento/module-media-content-synchronization: 100.4.6-beta1
magento/module-media-content-synchronization-api: 100.4.5-beta1
magento/module-media-content-synchronization-catalog: 100.4.4-beta1
magento/module-media-content-synchronization-cms: 100.4.4-beta1
magento/module-media-gallery: 100.4.6-beta1
magento/module-media-gallery-api: 101.0.6-beta1
magento/module-media-gallery-catalog: 100.4.4-beta1
magento/module-media-gallery-catalog-integration: 100.4.4-beta1
magento/module-media-gallery-catalog-ui: 100.4.4-beta1
magento/module-media-gallery-cms-ui: 100.4.4-beta1
magento/module-media-gallery-integration: 100.4.6-beta1
magento/module-media-gallery-metadata: 100.4.5-beta1
magento/module-media-gallery-metadata-api: 100.4.4-beta1
magento/module-media-gallery-renditions: 100.4.5-beta1
magento/module-media-gallery-renditions-api: 100.4.4-beta1
magento/module-media-gallery-synchronization: 100.4.6-beta1
magento/module-media-gallery-synchronization-api: 100.4.5-beta1
magento/module-media-gallery-synchronization-metadata: 100.4.3-beta1
magento/module-media-gallery-ui: 100.4.6-beta1
magento/module-media-gallery-ui-api: 100.4.5-beta1
magento/module-media-storage: 100.4.6-beta1
magento/module-message-queue: 100.4.7-beta1
magento/module-msrp: 100.4.6-beta1
magento/module-msrp-configurable-product: 100.4.4-beta1
magento/module-msrp-grouped-product: 100.4.4-beta1
magento/module-multishipping: 100.4.7-beta1
magento/module-mysql-mq: 100.4.5-beta1
magento/module-new-relic-reporting: 100.4.5-beta1
magento/module-newsletter: 100.4.7-beta1
magento/module-newsletter-graph-ql: 100.4.4-beta1
magento/module-offline-payments: 100.4.5-beta1
magento/module-offline-shipping: 100.4.6-beta1
magento/module-open-search: 100.4.1-beta1
magento/module-page-cache: 100.4.7-beta1
magento/module-payment: 100.4.7-beta1
magento/module-payment-graph-ql: 100.4.1
magento/module-paypal: 101.0.7-beta1
magento/module-paypal-captcha: 100.4.4-beta1
magento/module-paypal-graph-ql: 100.4.4
magento/module-persistent: 100.4.7-beta1
magento/module-product-alert: 100.4.6-beta1
magento/module-product-video: 100.4.7-beta1
magento/module-quote: 101.2.7-beta1
magento/module-quote-analytics: 100.4.6-beta1
magento/module-quote-bundle-options: 100.4.3-beta1
magento/module-quote-configurable-options: 100.4.3-beta1
magento/module-quote-downloadable-links: 100.4.3-beta1
magento/module-quote-graph-ql: 100.4.7-beta1
magento/module-related-product-graph-ql: 100.4.4-beta1
magento/module-release-notification: 100.4.5-beta1
magento/module-remote-storage: 100.4.5-beta1
magento/module-reports: 100.4.7-beta1
magento/module-require-js: 100.4.3-beta1
magento/module-review: 100.4.7-beta1
magento/module-review-analytics: 100.4.4-beta1
magento/module-review-graph-ql: 100.4.3-beta1
magento/module-robots: 101.1.3-beta1
magento/module-rss: 100.4.4
magento/module-rule: 100.4.5
magento/module-sales: 103.0.7-beta1
magento/module-sales-analytics: 100.4.4-beta1
magento/module-sales-graph-ql: 100.4.6
magento/module-sales-inventory: 100.4.3
magento/module-sales-rule: 101.2.7-beta1
magento/module-sales-sequence: 100.4.4-beta1
magento/module-sample-data: 100.4.5-beta1
magento/module-search: 101.1.7-beta1
magento/module-security: 100.4.7-beta1
magento/module-send-friend: 100.4.5-beta1
magento/module-send-friend-graph-ql: 100.4.2
magento/module-shipping: 100.4.7-beta1
magento/module-sitemap: 100.4.6-beta1
magento/module-store: 101.1.7-beta1
magento/module-store-graph-ql: 100.4.5-beta1
magento/module-swagger: 100.4.6-beta1
magento/module-swagger-webapi: 100.4.3-beta1
magento/module-swagger-webapi-async: 100.4.3-beta1
magento/module-swatches: 100.4.7-beta1
magento/module-swatches-graph-ql: 100.4.4
magento/module-swatches-layered-navigation: 100.4.3-beta1
magento/module-tax: 100.4.7-beta1
magento/module-tax-graph-ql: 100.4.2
magento/module-tax-import-export: 100.4.6-beta1
magento/module-theme: 101.1.7-beta1
magento/module-theme-graph-ql: 100.4.3
magento/module-translation: 100.4.7-beta1
magento/module-ui: 101.2.7-beta1
magento/module-ups: 100.4.7-beta1
magento/module-url-rewrite: 102.0.6-beta1
magento/module-url-rewrite-graph-ql: 100.4.6-beta1
magento/module-user: 101.2.7-beta1
magento/module-usps: 100.4.6-beta1
magento/module-variable: 100.4.5-beta1
magento/module-vault: 101.2.7-beta1
magento/module-vault-graph-ql: 100.4.2
magento/module-version: 100.4.3
magento/module-webapi: 100.4.6-beta1
magento/module-webapi-async: 100.4.5-beta1
magento/module-webapi-security: 100.4.4-beta1
magento/module-weee: 100.4.7-beta1
magento/module-weee-graph-ql: 100.4.4-beta1
magento/module-widget: 101.2.7-beta1
magento/module-wishlist: 101.2.7-beta1
magento/module-wishlist-analytics: 100.4.5-beta1
magento/module-wishlist-graph-ql: 100.4.7-beta1
magento/page-builder: 1.7.4-beta1
magento/security-package: 1.1.6-beta1
magento/theme-adminhtml-backend: 100.4.6
magento/theme-frontend-blank: 100.4.7-beta1
magento/theme-frontend-luma: 100.4.7-beta1
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
symfony/process: ^5.4
symfony/string: ^5.4
tedivm/jshrink: ^1.4
temando/module-shipping: 2.0.0
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
    <td>PHP的AWS通用執行階段</td>
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
    <td>較少處理器的PHP連線埠</td>
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
    <td>業務模型中用於輸入驗證的精簡宣告庫。</td>
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
    <td>安全寫入檔案的工具，以避免競爭情況</td>
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
    <td>坯件Zend_Cache_Backend_File後端的標籤清除效能極差，導致隨著快取專案數的增加無法使用。 此後端進行許多變更，大幅提升效能，尤其是標籤清理方面。</td>
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
    <td>reCAPTCHA的使用者端資料庫，此免費服務可保護網站免受垃圾郵件和濫用。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>資料庫</td>
    <td>使用Figlet、影像、ReCaptcha等產生及驗證碼等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>資料庫</td>
    <td>PHP Reflection API、靜態程式碼掃描和程式碼產生的擴充功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">層板/層板 — 組態</a>
    </td>
    <td>資料庫</td>
    <td>提供巢狀物件屬性型使用者介面，用於存取應用程式程式碼中的此設定資料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">層板/層板 — 加密</a>
    </td>
    <td>資料庫</td>
    <td>強大的加密工具和密碼雜湊</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>資料庫</td>
    <td>資料庫抽象層、SQL抽象化、結果集抽象化，以及RowDataGateway和TableDataGateway實作</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>資料庫</td>
    <td>PSR-11容器的自動化相依性插入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">層疊/層疊 — 逸出</a>
    </td>
    <td>資料庫</td>
    <td>安全地逸出HTML、HTML屬性、JavaScript、CSS和URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>資料庫</td>
    <td>在PHP應用程式中觸發和監聽事件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">層合板/層合板饋送</a>
    </td>
    <td>資料庫</td>
    <td>提供建立和使用RSS和Atom摘要的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">層疊/層疊 — 檔案</a>
    </td>
    <td>資料庫</td>
    <td>找到PHP類別檔案</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">圖層/圖層濾鏡</a>
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
      <a href="https://github.com/laminas/laminas-i18n.git">層粘連體/層粘連體 — i18n</a>
    </td>
    <td>資料庫</td>
    <td>為您的應用程式提供翻譯，並篩選及驗證國際化值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>資料庫</td>
    <td>提供將原生PHP序列化為JSON並將JSON解碼為原生PHP的便利方法</td>
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
      <a href="https://github.com/laminas/laminas-mail.git">層疊/層疊</a>
    </td>
    <td>資料庫</td>
    <td>提供撰寫和傳送文字及MIME相容多部分電子郵件訊息的通用功能</td>
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
      <a href="https://github.com/laminas/laminas-mime.git">層疊/層疊 — mime</a>
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
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>資料庫</td>
    <td>ReCaptcha Web服務的OOP包裝函式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-route</a>
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
    <td>工廠導向的相依性插入容器</td>
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
      <a href="https://github.com/laminas/laminas-soap.git">羊層肉/羊層肉</a>
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
    <td>協助操控和驗證「統一資源識別碼(URI)」的元件</td>
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
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-view</a>
    </td>
    <td>資料庫</td>
    <td>彈性檢視層可支援並提供多個檢視層、協助程式等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>資料庫</td>
    <td>將舊版ZF類別名稱別名變更為Laminas專案的對等名稱。</td>
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
    <td>PHP內建的Javascript縮制器</td>
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
      <a href="https://github.com/ezyang/htmlpurifier.git">額澤洋/htmlpurifier</a>
    </td>
    <td>資料庫</td>
    <td>以PHP撰寫的符合標準的HTML篩選器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>資料庫</td>
    <td>先前稱為videlalvaro/php-amqplib。  此程式庫是AMQP通訊協定的純PHP實作。 已針對RabbitMQ進行測試。</td>
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
    <td>var_export()的強大替代方法，可以在不使用__set_state()的情況下匯出封閉點和物件</td>
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
    <td>Credis是Redis索引鍵值存放區的輕量型介面，可在取得phpredis資料庫時將其換行，以獲得更優異的效能。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>資料庫</td>
    <td>可讓您尋找系統CA套件的路徑，並包含Mozilla CA套件的備援。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">composer/class-map-generator</a>
    </td>
    <td>資料庫</td>
    <td>用來掃描PHP程式碼和產生類別對映的公用程式。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">composer/composer</a>
    </td>
    <td>資料庫</td>
    <td>Composer可協助您宣告、管理和安裝PHP專案的相依性。 它可確保您在任何地方都有正確的棧疊。</td>
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
    <td>PCRE包裝程式庫，提供型別安全的預浸料_*取代物。</td>
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
      <a href="https://github.com/doctrine/annotations.git">doctrine/annotations</a>
    </td>
    <td>資料庫</td>
    <td>Docblock註解剖析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/deprecations.git">doctrine/deprecations</a>
    </td>
    <td>資料庫</td>
    <td>在trigger_error(E_USER_DEPRECATED)或PSR-3記錄之上的小層，提供選項以停用所有過時專案或選擇性地針對套件使用。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">doctrine/lexer</a>
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
    <td>要與elasticsearch-php一起使用的插銷/串流（已捨棄）復本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>資料庫</td>
    <td>與elasticsearch-php一起使用的guzzle/RingPHP （已放棄）分支</td>
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
    <td>PSR-7訊息實作，也提供常見的公用程式方法</td>
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
    <td>PHP的檔案儲存擷取</td>
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
      <a href="https://github.com/Seldaek/monolog.git">monolog/monolog</a>
    </td>
    <td>資料庫</td>
    <td>將您的記錄檔傳送至檔案、通訊端、收件匣、資料庫和各種網路服務</td>
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
    <td>RFC 4648編碼的固定時間實作(Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>資料庫</td>
    <td>PHP 7中的random_bytes()和random_int()的PHP 5.x polyfill</td>
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
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>資料庫</td>
    <td>PHP 5.x-8.x polyfill for mcrypt extension</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
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
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
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
    <td>PHP的CommonJS Promise/A的輕量型實作</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>資料庫</td>
    <td>以PHP寫入之CSS檔案的剖析器</td>
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
    <td>PHAR檔案格式公用程式，當PHP朝上時適用</td>
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
    <td>根據RFC 4226 （HOTP演演算法）和RFC 6238 （TOTP演演算法）產生一次性密碼且與Google Authenticator相容的PHP程式庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>資料庫</td>
    <td>用於管理公開金鑰基礎結構的PHP架構。 它包含X.509公開金鑰憑證、屬性憑證、憑證請求和憑證路徑驗證。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>資料庫</td>
    <td>協助您尋找、載入、合併、自動填寫及驗證任何型別的設定值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/主控台</a>
    </td>
    <td>資料庫</td>
    <td>輕鬆建立美觀且可測試的命令列介面</td>
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
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contracts</a>
    </td>
    <td>資料庫</td>
    <td>觸發淘汰通知的一般函式和慣例</td>
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
    <td>提供可讓您的應用程式元件透過傳送事件並聆聽它們而彼此通訊的工具</td>
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
    <td>提供C intl擴充功能的PHP取代層，其中包含來自ICU程式庫的其他資料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>資料庫</td>
    <td>用於Ctype函式的Symfony Polyfill</td>
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
    <td>Mbstring延伸的Symfony polyfill</td>
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
    <td>Symfony polyfill將某些PHP 8.0+功能回移植到較低的PHP版本</td>
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
    <td>為字串提供物件導向的API，並以統一的方式處理位元組、UTF-8程式碼點和字形叢集</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>資料庫</td>
    <td>提供用於瀏覽任何任意PHP變數的機制</td>
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
    <td>擲回例外狀況而不是在錯誤時傳回FALSE的PHP核心函式</td>
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
  <tr>
    <td>
      Temando/module-shipping-remover
    </td>
    <td>magento2-module</td>
    <td>從Magento2移除Temando多承運商送貨擴充功能</td>
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
  <tr>
    <td>
      temando/module-shipping
    </td>
    <td>中繼封裝</td>
    <td>Magento2的Temando多承運商延長運送期</td>
  </tr>
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