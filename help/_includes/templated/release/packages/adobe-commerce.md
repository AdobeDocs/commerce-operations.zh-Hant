---
source-git-commit: 4391091cce32618dc02b0bddb62ff9d16dd12f10
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 0%

---
# Adobe Commerce套件

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce使用撰寫器來管理PHP套件。

此 `composer.json` 檔案聲明包清單，而 `composer.lock` 檔案會儲存用來建置Adobe Commerce或Magento Open Source安裝的套件完整清單（每個套件及其相依性的完整版本）。

以下參考檔案是從 `composer.lock` 檔案，且涵蓋Adobe Commerce 2.4.5中包含的必要套件。

## 相依性

`magento/product-enterprise-edition 2.4.5` 具有下列相依性：

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
ext-spl: *
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
laminas/laminas-json: ^3.3.0
laminas/laminas-mail: ^2.16.0
laminas/laminas-mime: ^2.9.1
laminas/laminas-modulemanager: ^2.11.0
laminas/laminas-mvc: ^3.3.3
laminas/laminas-server: ^2.11.1
laminas/laminas-servicemanager: ^3.11.0
laminas/laminas-soap: ^2.10.0
laminas/laminas-stdlib: ^3.7.1
laminas/laminas-uri: ^2.9.1
laminas/laminas-validator: ^2.17.0
league/flysystem: ~2.4.5
league/flysystem-aws-s3-v3: ^2.4.3
lib-libxml: *
magento/composer: ~1.8.0
magento/composer-dependency-version-audit-plugin: ~0.1
magento/framework-foreign-key: 100.4.4
magento/magento-composer-installer: >=0.3.0
magento/magento2-ee-base: 2.4.5
magento/module-admin-gws: 100.4.5
magento/module-admin-gws-configurable-product: 100.4.2
magento/module-admin-gws-staging: 100.4.2
magento/module-advanced-catalog: 100.4.2
magento/module-advanced-checkout: 100.4.5
magento/module-advanced-rule: 100.4.2
magento/module-advanced-sales-rule: 100.4.2
magento/module-async-order: 100.4.1
magento/module-async-order-graph-ql: 100.4.0
magento/module-aws-s3-customer-custom-attributes: 100.4.2
magento/module-aws-s3-gift-card-import-export: 100.4.2
magento/module-aws-s3-scheduled-import-export: 100.4.2
magento/module-banner: 101.2.5
magento/module-banner-customer-segment: 100.4.3
magento/module-banner-graph-ql: 100.4.1
magento/module-bundle-import-export-staging: 100.4.2
magento/module-bundle-staging: 100.4.5
magento/module-catalog-event: 101.1.4
magento/module-catalog-import-export-staging: 100.4.2
magento/module-catalog-inventory-staging: 100.4.3
magento/module-catalog-permissions: 100.4.5
magento/module-catalog-permissions-graph-ql: 100.4.3
magento/module-catalog-rule-staging: 100.4.5
magento/module-catalog-staging: 100.4.5
magento/module-catalog-staging-graph-ql: 100.4.4
magento/module-catalog-url-rewrite-staging: 100.4.4
magento/module-checkout-address-search: 100.4.4
magento/module-checkout-address-search-gift-registry: 100.4.1
magento/module-checkout-staging: 100.4.4
magento/module-cms-staging: 100.4.5
magento/module-configurable-product-staging: 100.4.4
magento/module-custom-attribute-management: 100.4.4
magento/module-customer-balance: 100.4.5
magento/module-customer-balance-graph-ql: 100.4.2
magento/module-customer-custom-attributes: 100.4.5
magento/module-customer-finance: 100.4.2
magento/module-customer-segment: 102.1.5
magento/module-deferred-total-calculating: 100.4.0
magento/module-downloadable-staging: 100.4.4
magento/module-elasticsearch-catalog-permissions: 100.4.1
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.0
magento/module-enterprise: 100.4.3
magento/module-gift-card: 101.3.5
magento/module-gift-card-account: 101.2.5
magento/module-gift-card-account-graph-ql: 100.4.3
magento/module-gift-card-graph-ql: 100.4.5
magento/module-gift-card-import-export: 100.4.2
magento/module-gift-card-staging: 100.4.2
magento/module-gift-message-staging: 100.4.2
magento/module-gift-registry: 101.2.5
magento/module-gift-registry-graph-ql: 100.4.1
magento/module-gift-wrapping: 101.2.4
magento/module-gift-wrapping-graph-ql: 100.4.2
magento/module-gift-wrapping-staging: 100.4.2
magento/module-google-optimizer-staging: 100.4.2
magento/module-google-tag-manager: 100.4.5
magento/module-grouped-product-staging: 100.4.3
magento/module-invitation: 100.4.4
magento/module-layered-navigation-staging: 100.4.2
magento/module-logging: 101.2.5
magento/module-login-as-customer-logging: 100.4.5
magento/module-login-as-customer-website-restriction: 100.4.3
magento/module-media-content-catalog-staging: 100.4.2
magento/module-msrp-staging: 100.4.3
magento/module-multiple-wishlist: 100.4.5
magento/module-multiple-wishlist-graph-ql: 100.4.1
magento/module-payment-staging: 100.4.2
magento/module-persistent-history: 100.4.2
magento/module-price-permissions: 100.4.1
magento/module-product-video-staging: 100.4.2
magento/module-promotion-permissions: 100.4.2
magento/module-quote-gift-card-options: 100.4.2
magento/module-quote-staging: 100.4.2
magento/module-reminder: 101.2.4
magento/module-remote-storage-commerce: 100.4.1
magento/module-resource-connections: 100.4.2
magento/module-review-staging: 100.4.2
magento/module-reward: 101.2.5
magento/module-reward-graph-ql: 100.4.4
magento/module-reward-staging: 100.4.2
magento/module-rma: 101.2.5
magento/module-rma-graph-ql: 100.4.4
magento/module-rma-staging: 100.4.2
magento/module-sales-archive: 101.0.3
magento/module-sales-rule-staging: 100.4.4
magento/module-scalable-checkout: 100.4.4
magento/module-scalable-inventory: 100.4.3
magento/module-scalable-oms: 100.4.3
magento/module-scheduled-import-export: 101.2.5
magento/module-search-staging: 100.4.3
magento/module-staging: 101.2.5
magento/module-staging-graph-ql: 100.4.2
magento/module-support: 101.2.4
magento/module-swat: 100.4.3
magento/module-target-rule: 101.2.5
magento/module-target-rule-graph-ql: 100.4.2
magento/module-versions-cms: 101.2.5
magento/module-versions-cms-page-cache: 100.4.1
magento/module-versions-cms-url-rewrite: 100.4.3
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.1
magento/module-visual-merchandiser: 100.4.5
magento/module-website-restriction: 100.4.4
magento/module-weee-staging: 100.4.2
magento/module-wishlist-gift-card: 100.4.1
magento/module-wishlist-gift-card-graph-ql: 100.4.1
magento/page-builder-commerce: 1.7.2
magento/product-community-edition: 2.4.5
magento/security-package-ee: 1.0.0
magento/theme-adminhtml-spectrum: 100.4.0
magento/zendframework1: ~1.15.0
monolog/monolog: ^2.7
pelago/emogrifier: ^6.0.0
php: ~7.4.0||~8.1.0
php-amqplib/php-amqplib: ~3.2.0
phpseclib/mcrypt_compat: ~2.0.2
phpseclib/phpseclib: ~3.0.13
ramsey/uuid: ~4.2.0
symfony/console: ~4.4.0
symfony/process: ~4.4.0
tedivm/jshrink: ~1.4.0
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
    <td>先前為videolvaro/php-amqplib。  此庫是AMQP協定的純PHP實現。 它被測試了，RabbitMQ。</td>
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

### 專有

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>類型</th>
      <th>說明</th>
    </tr>
  </thead>
  <tbody>
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
