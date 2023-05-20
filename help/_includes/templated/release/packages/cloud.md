---
source-git-commit: a1f99f839f11ab42356b87a69398999bb03cd544
workflow-type: tm+mt
source-wordcount: '2674'
ht-degree: 0%

---
# 用於Adobe Commerce的雲包

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/cloud/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/cloud/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/magento-cloud-metapackage' package
 -->

<!-- The edition variable contains `cloud` value from the _data/names.yml file
 -->

Adobe Commerce在雲基礎架構上使用Composer管理PHP包。

的 `composer.json` 檔案聲明包清單，而 `composer.lock` 檔案儲存用於構建Adobe Commerce或Magento Open Source安裝的軟體包的完整清單（每個軟體包及其依賴項的完整版本）。

以下參考文檔是從 `composer.lock` 檔案，並涵蓋Adobe Commerce雲基礎架構2.4.6中包含的所需包。

## 依賴項

`magento/magento-cloud-metapackage 2.4.6` 具有以下依賴關係：

```config
fastly/magento2: ^1.2.34
magento/ece-tools: ^2002.1.0
magento/module-paypal-on-boarding: ~100.5.0
magento/product-enterprise-edition: >=2.4.6 <2.4.7
```

## 第三方許可證

### 僅Apache-2.0、LGPL-2.1

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
      elasticsearch/elasticsearch
    </td>
    <td>庫</td>
    <td>用於Elasticsearch的PHP客戶端</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>庫</td>
    <td>用於OpenSearch的PHP客戶端</td>
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
    <td>庫</td>
    <td>Adobe StockAPI庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>庫</td>
    <td>AWSPHP通用運行時</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>庫</td>
    <td>AWSSDK用於PHP — 在PHP項目中使用Amazon Web Services</td>
  </tr>
  <tr>
    <td>
      paypal/module頭樹
    </td>
    <td>元包</td>
    <td>BraintreeMagento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>庫</td>
    <td>LESS處理器的PHP埠</td>
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
      <a href="https://github.com/Bacon/BaconQrCode.git">培根/培根二碼</a>
    </td>
    <td>庫</td>
    <td>BaconQrCode是用於PHP的QR碼生成器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">貝貝雷 — 阿塞特</a>
    </td>
    <td>庫</td>
    <td>用於業務模型中輸入驗證的精簡斷言庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>庫</td>
    <td>PHP 7.1枚舉實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe writer</a>
    </td>
    <td>庫</td>
    <td>安全寫入檔案、避免競賽條件的工具</td>
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
    <td>馬根托模</td>
    <td>庫Zend_Cache_Backend_File後端對於通過標籤進行清理的效能極差，這使得它隨著快取項目數的增加變得不可用。 此後端進行許多更改，從而極大地提高了效能，尤其是對於標籤清理。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>庫</td>
    <td>具有樂觀鎖定的基於Redis的會話處理程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/fastly/fastly-magento2.git">快速/magento2</a>
    </td>
    <td>magento2模</td>
    <td>用於2.4.xMagento的Rebisty CDN模組</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">火庫/php/jwt</a>
    </td>
    <td>庫</td>
    <td>用於對PHP中的JSON Web令牌(JWT)進行編碼和解碼的簡單庫。 應符合當前規範。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">谷歌/重新捕獲</a>
    </td>
    <td>庫</td>
    <td>reCAPTCHA客戶端庫，這是一種免費服務，可保護網站免受垃圾郵件和濫用。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>使用Figlets、影像、ReCaptcha等生成和驗證驗證驗證碼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">層粘連蛋白/層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>PHP Reflection API的擴展、靜態代碼掃描和代碼生成</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas配置</a>
    </td>
    <td>庫</td>
    <td>提供了基於嵌套對象屬性的用戶介面，用於訪問應用程式碼中的此配置資料</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>強密碼工具和密碼散列</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>資料庫抽象層、SQL抽象、結果集抽象以及RowDataGateway和TableDataGateway實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">層粘連體/層粘連體</a>
    </td>
    <td>庫</td>
    <td>用於PSR-11容器的自動依賴注入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">層帶/層帶擒縱機</a>
    </td>
    <td>庫</td>
    <td>安全地轉義HTML、HTML屬性、JavaScript、CSS和URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">層粘連蛋白/層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>觸發和偵聽PHP應用程式內的事件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">層粘連蛋白/層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>提供建立和使用RSS和Atom源的功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">層疊/層疊檔案</a>
    </td>
    <td>庫</td>
    <td>查找PHP類檔案</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">層帶/層帶過濾器</a>
    </td>
    <td>庫</td>
    <td>以寫程式方式過濾和規範化資料和檔案</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">層帶/層帶</a>
    </td>
    <td>庫</td>
    <td>為執行超文本傳輸協定(HTTP)請求提供了簡單的介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">層粘膠/層粘膠 — i18n</a>
    </td>
    <td>庫</td>
    <td>為應用程式提供翻譯，並篩選和驗證國際化值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas json</a>
    </td>
    <td>庫</td>
    <td>為將本機PHP序列化為JSON和將JSON解碼為本機PHP提供了方便的方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">層板/層板裝載機</a>
    </td>
    <td>庫</td>
    <td>自動載入和插件載入策略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">層粘膠/層粘膠郵件</a>
    </td>
    <td>庫</td>
    <td>提供編寫和發送符合文本和MIME的多部分電子郵件的通用功能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">層粘連蛋白/層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>建立加密的偽隨機數，並管理大整數</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">拉米納斯/拉米納斯</a>
    </td>
    <td>庫</td>
    <td>建立和分析MIME消息和部件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">層合/層合模組管理器</a>
    </td>
    <td>庫</td>
    <td>用於laminas-mvc應用的模組化應用系統</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">層粘膠/層粘膠/mvc</a>
    </td>
    <td>庫</td>
    <td>Laminas的事件驅動MVC層，包括MVC應用程式、控制器和插件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">層帶/層帶</a>
    </td>
    <td>庫</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas權限acl</a>
    </td>
    <td>庫</td>
    <td>為權限管理提供輕量化、靈活的訪問控制清單(ACL)實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">層粘連/層粘連</a>
    </td>
    <td>庫</td>
    <td>ReCaptcha Web服務的OOP包裝</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">層疊/層疊路由器</a>
    </td>
    <td>庫</td>
    <td>用於HTTP和控制台應用的靈活路由系統</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas伺服器</a>
    </td>
    <td>庫</td>
    <td>建立基於反射的RPC伺服器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas服務管理器</a>
    </td>
    <td>庫</td>
    <td>工廠驅動的依賴關係注入容器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">層粘連/層粘連</a>
    </td>
    <td>庫</td>
    <td>物件導向的PHP會話和儲存介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">層粘膠/層粘膠皂</a>
    </td>
    <td>庫</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">層粘連蛋白/層粘連蛋白</a>
    </td>
    <td>庫</td>
    <td>SPL擴展、陣列實用程式、錯誤處理程式等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">層帶/層帶文本</a>
    </td>
    <td>庫</td>
    <td>建立FIGlet和基於文本的表</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">層帶/層帶</a>
    </td>
    <td>庫</td>
    <td>幫助處理和驗證「統一資源標識符(URI)」的元件</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">層粘連蛋白/層粘連蛋白驗證劑</a>
    </td>
    <td>庫</td>
    <td>用於廣泛域的驗證類，以及鏈驗證器建立複雜驗證標準的能力</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">層帶/層帶視圖</a>
    </td>
    <td>庫</td>
    <td>靈活的視圖層支援和提供多個視圖層、幫助程式等</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">拉米納斯/拉米納斯 — 結構橋</a>
    </td>
    <td>庫</td>
    <td>將舊ZF類名稱別名與Laminas Project等價。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php解析器</a>
    </td>
    <td>庫</td>
    <td>用PHP編寫的PHP解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>庫</td>
    <td>PHP中內置的Javascript Minifier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">圖巴馬丁/cssmin</a>
    </td>
    <td>庫</td>
    <td>UYI CSS壓縮機的PHP埠</td>
  </tr>
  </tbody>
</table>

### BSD-3 — 子句修改

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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache backend-redis</a>
    </td>
    <td>馬根托模</td>
    <td>Zend_Cache後端使用完全支援標籤的Redis。</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1或更高版本

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
      <a href="https://github.com/ezyang/htmlpurifier.git">埃茲揚/html淨化器</a>
    </td>
    <td>庫</td>
    <td>寫入PHP的符合標準的HTML篩選器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-ampqplib/php-ampqplib</a>
    </td>
    <td>庫</td>
    <td>原為videlalvaro/php-amqplib。  該庫是AMQP協定的純PHP實現。 它已經測試過RabbitMQ。</td>
  </tr>
  </tbody>
</table>

### 麻省理工

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
      <a href="https://github.com/braintree/braintree_php.git">腦樹/腦樹/php</a>
    </td>
    <td>庫</td>
    <td>BraintreePHP客戶端庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">磚/數學</a>
    </td>
    <td>庫</td>
    <td>任意精度算術庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">磚型和瓦列克斯波特</a>
    </td>
    <td>庫</td>
    <td>var_export()的一個強大替代方法，它可以導出不帶__set_state()的封閉和對象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">克里斯蒂安 — 里森/base32</a>
    </td>
    <td>庫</td>
    <td>根據RFC 4648編碼/解碼器的Base32</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">科林莫倫霍爾/克里德</a>
    </td>
    <td>庫</td>
    <td>Credis是Redis鍵值儲存的輕量介面，當可用時，該介面將封裝phpredis庫以獲得更好的效能。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">編寫器/ca捆綁包</a>
    </td>
    <td>庫</td>
    <td>用於查找系統CA包的路徑，並包括對Mozilla CA包的回退。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">編寫器/類映射生成器</a>
    </td>
    <td>庫</td>
    <td>用於掃描PHP代碼並生成類映射的實用程式。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">作曲家/作曲家</a>
    </td>
    <td>庫</td>
    <td>Composer可幫助您聲明、管理和安裝PHP項目的依賴項。 它確保您在任何位置都擁有正確的堆棧。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">編寫器/元資料迷你符</a>
    </td>
    <td>庫</td>
    <td>處理元資料精簡和擴展的小型實用程式庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">編寫器/打印機</a>
    </td>
    <td>庫</td>
    <td>PCRE包裝庫，提供類型安全的預包裝_*更換。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">作曲家/塞姆弗</a>
    </td>
    <td>庫</td>
    <td>提供實用程式、版本約束分析和驗證的Semver庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">作曲家/spdx許可證</a>
    </td>
    <td>庫</td>
    <td>SPDX許可證清單和驗證庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug處理程式</a>
    </td>
    <td>庫</td>
    <td>在不使用Xdebug的情況下重新啟動進程。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/annotations.git">原則/注釋</a>
    </td>
    <td>庫</td>
    <td>Docblock批注分析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/deprecations.git">教條/貶損</a>
    </td>
    <td>庫</td>
    <td>trigger_error(E_USER_DEPRECATED)或PSR-3日誌記錄上的一個小層，帶有禁用所有棄用或有選擇地禁用包的選項。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">學說/雷克薩斯</a>
    </td>
    <td>庫</td>
    <td>PHP原則詞法分析器庫，可用於自頂向下、遞歸下降分析器。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">端陣/qr碼</a>
    </td>
    <td>庫</td>
    <td>端陣QR碼</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">齊穆埃爾/古茲萊特雷姆</a>
    </td>
    <td>庫</td>
    <td>要與elasticsearch-php一起使用的Quzzle/streams（已放棄）叉</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">齊穆埃爾/靈菲律賓比索</a>
    </td>
    <td>庫</td>
    <td>與elasticsearch-php一起使用的Fork Guzzle/RingPHP（已放棄）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/FriendsOfPHP/proxy-manager-lts.git">friendsofphp/proxy manager-lts</a>
    </td>
    <td>庫</td>
    <td>向ocramius/proxy-manager添加對更多PHP版本的支援</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/bzikarsky/gelf-php.git">graylog2/gelf-php</a>
    </td>
    <td>庫</td>
    <td>用於向GELF相容後端（如Graylog2）發送日誌消息的php實現。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>庫</td>
    <td>Guzzle是PHP HTTP客戶端庫</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/承諾</a>
    </td>
    <td>庫</td>
    <td>Guzzle承諾圖書館</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>庫</td>
    <td>PSR-7消息實現，它還提供了常用實用方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/illuminate/collections.git">照亮/收集</a>
    </td>
    <td>庫</td>
    <td>「照明集合」包。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/illuminate/config.git">照明/配置</a>
    </td>
    <td>庫</td>
    <td>「照明配置」包。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/illuminate/contracts.git">照明/合同</a>
    </td>
    <td>庫</td>
    <td>「照明合同」包。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/illuminate/macroable.git">照明/宏</a>
    </td>
    <td>庫</td>
    <td>Lixcule Macroable包。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainb/json架構</a>
    </td>
    <td>庫</td>
    <td>驗證json架構的庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">聯飛系統</a>
    </td>
    <td>庫</td>
    <td>PHP的檔案儲存抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">聯盟/flysystem-aws-s3-v3</a>
    </td>
    <td>庫</td>
    <td>AWSS3檔案系統適配器，用於Flysystem。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">聯盟/MIME類型檢測</a>
    </td>
    <td>庫</td>
    <td>Flysystem的Mime類型檢測</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">單對數/單對數</a>
    </td>
    <td>庫</td>
    <td>將日誌發送到檔案、套接字、收件箱、資料庫和各種Web服務</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>庫</td>
    <td>聲明性地指定如何從JSON文檔中提取元素</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/briannesbitt/Carbon.git">奈斯博特/碳</a>
    </td>
    <td>庫</td>
    <td>支援281種不同語言的DateTime的API擴展。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>庫</td>
    <td>RFC 4648編碼的恆時實現(Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>庫</td>
    <td>PHP 7中隨機位元組()和隨機int()的PHP 5.x填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">亞速爾/表情符</a>
    </td>
    <td>庫</td>
    <td>在HTML代碼中將CSS樣式轉換為內聯樣式屬性</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>庫</td>
    <td>將CSS選擇器轉換為XPath查詢。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>庫</td>
    <td>用於PHP項目的現代DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt compat</a>
    </td>
    <td>庫</td>
    <td>PHP 5.x-8.x多填充，用於mcrypt擴展</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">ppseclib/ppseclib</a>
    </td>
    <td>庫</td>
    <td>PHP安全通信庫 — RSA、AES、SSH2、SFTP、X.509等的純PHP實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/快取</a>
    </td>
    <td>庫</td>
    <td>用於快取庫的公共介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/容器</a>
    </td>
    <td>庫</td>
    <td>公用容器介面（PHP圖PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/事件調度程式</a>
    </td>
    <td>庫</td>
    <td>用於事件處理的標準介面。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http客戶端</a>
    </td>
    <td>庫</td>
    <td>HTTP客戶端的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http工廠</a>
    </td>
    <td>庫</td>
    <td>PSR-7 HTTP消息工廠的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http消息</a>
    </td>
    <td>庫</td>
    <td>HTTP消息的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/日誌</a>
    </td>
    <td>庫</td>
    <td>記錄庫的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/simple-cache.git">psr/simple cache</a>
    </td>
    <td>庫</td>
    <td>用於簡單快取的通用介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getalheaders</a>
    </td>
    <td>庫</td>
    <td>getalleheaders的聚合填充。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">拉姆齊/收集</a>
    </td>
    <td>庫</td>
    <td>用於表示和操作集合的PHP庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">拉姆齊/uuid</a>
    </td>
    <td>庫</td>
    <td>用於生成和使用通用唯一標識符(UUID)的PHP庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">反應/承諾</a>
    </td>
    <td>庫</td>
    <td>PHP的CommonJS承諾/A的輕量級實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>庫</td>
    <td>PHP中寫入的CSS檔案解析器</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>庫</td>
    <td>JSON線條</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar utis</a>
    </td>
    <td>庫</td>
    <td>PHAR檔案格式實用程式，用於PHP播放時</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/信號處理器</a>
    </td>
    <td>庫</td>
    <td>簡單的unix信號處理程式，在不支援信號的地方靜默失敗，以便輕鬆跨平台開發</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>庫</td>
    <td>PHP的AES密鑰包。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky labs/otpp</a>
    </td>
    <td>庫</td>
    <td>一種PHP庫，用於根據RFC 4226（HOTP算法）和RFC 6238（TOTP算法）生成一次性密碼，並與Google驗證器相容</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki框架</a>
    </td>
    <td>庫</td>
    <td>用於管理公鑰基礎架構的PHP框架。 它包括X.509公鑰證書、屬性證書、認證請求和認證路徑驗證。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symony/config</a>
    </td>
    <td>庫</td>
    <td>幫助您查找、載入、組合、自動填充和驗證任何類型的配置值</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symony/console</a>
    </td>
    <td>庫</td>
    <td>輕鬆建立漂亮且可測試的命令行介面</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css選擇器</a>
    </td>
    <td>庫</td>
    <td>將CSS選擇器轉換為XPath表達式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/依賴關係注入</a>
    </td>
    <td>庫</td>
    <td>允許您標準化和集中應用程式中構建對象的方式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">符合/貶損合同</a>
    </td>
    <td>庫</td>
    <td>觸發棄用通知的通用函式和約定</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error處理程式</a>
    </td>
    <td>庫</td>
    <td>提供工具來管理錯誤並簡化PHP代碼的調試</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/事件調度程式</a>
    </td>
    <td>庫</td>
    <td>提供工具，通過分派事件並傾聽事件，使您的應用程式元件能夠彼此通信</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event dispatcher-contracts</a>
    </td>
    <td>庫</td>
    <td>與調度事件相關的通用抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symony/檔案系統</a>
    </td>
    <td>庫</td>
    <td>為檔案系統提供基本實用程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symony/finder</a>
    </td>
    <td>庫</td>
    <td>通過直觀的流暢介面查找檔案和目錄</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http基礎</a>
    </td>
    <td>庫</td>
    <td>為HTTP規範定義物件導向的層</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http內核</a>
    </td>
    <td>庫</td>
    <td>提供將請求轉換為響應的結構化流程</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>庫</td>
    <td>為包含來自ICU庫的附加資料的C國際擴展提供PHP替換層</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill類型</a>
    </td>
    <td>庫</td>
    <td>類型函式的符號多填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">符號/多填字</a>
    </td>
    <td>庫</td>
    <td>Intl的字素_*函式的Symfony多填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl</a>
    </td>
    <td>庫</td>
    <td>Symfony多填充intl的idn_to_ascii和idn_to_utf8函式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl — 正規化器</a>
    </td>
    <td>庫</td>
    <td>Intl正規化子類的Symfony多填充及相關函式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill mbstring</a>
    </td>
    <td>庫</td>
    <td>Mbstring副檔名的Symfony多填充</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>庫</td>
    <td>Symfony多填充將某些PHP 7.2+功能反饋到低PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>庫</td>
    <td>Symfony多填充將某些PHP 7.3+功能反饋到低PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>庫</td>
    <td>Symfony多填充將某些PHP 8.0+功能反饋到低PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>庫</td>
    <td>Symfony多填充將某些PHP 8.1+功能反饋到低PHP版本</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">符號/進程</a>
    </td>
    <td>庫</td>
    <td>在子進程中執行命令</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/proxy-manager-bridge.git">symfony/proxy manager橋</a>
    </td>
    <td>山橋</td>
    <td>為ProxyManager與各種Symfony元件整合</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/serializer.git">符號/序列化程式</a>
    </td>
    <td>庫</td>
    <td>處理將資料結構（包括對象圖形）序列化和反序列化為陣列結構或其他格式（如XML和JSON）。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">Symfony/服務合同</a>
    </td>
    <td>庫</td>
    <td>與書寫服務相關的通用抽象</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">符號/字串</a>
    </td>
    <td>庫</td>
    <td>提供物件導向的API，以統一方式處理位元組、UTF-8代碼點和字元簇</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/translation.git">符號/翻譯</a>
    </td>
    <td>庫</td>
    <td>提供工具來國際化應用程式</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/translation-contracts.git">符號/翻譯合同</a>
    </td>
    <td>庫</td>
    <td>與翻譯相關的通用摘要</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var dumper</a>
    </td>
    <td>庫</td>
    <td>提供用於遍歷任意PHP變數的機制</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml.git">symony/yaml</a>
    </td>
    <td>庫</td>
    <td>載入和轉儲YAML檔案</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">防毒裝置/安全裝置</a>
    </td>
    <td>庫</td>
    <td>PHP核心函式，在出錯時不返回FALSE而引發異常</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web令牌/jwt框架</a>
    </td>
    <td>對稱叢</td>
    <td>用於PHP和Symfony捆綁包的JSON對象簽名和加密庫。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>庫</td>
    <td>斷言以驗證方法輸入/輸出，並顯示好的錯誤消息。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>庫</td>
    <td>PHP埠的GraphQL參考實現</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/zordius/lightncandy.git">佐迪烏斯/輕巧糖果</a>
    </td>
    <td>庫</td>
    <td>PHP實現手把(http://handlebarsjs.com/)和八字鬍(http://mustache.github.io/)的速度極快。</td>
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
    <td>magento2模</td>
    <td>不適用</td>
  </tr>
  <tr>
    <td>
      temando/模組卸船機
    </td>
    <td>magento2模</td>
    <td>從Magento2中刪除Temando多承運人發運擴展</td>
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
      temando/module裝運
    </td>
    <td>元包</td>
    <td>用於Magento2的Temando多載貨船運擴展</td>
  </tr>
  </tbody>
</table>

### 菲律賓比索

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
    <td>庫</td>
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
  <tr>
    <td>
      paypal/module頭樹核
    </td>
    <td>magento2模</td>
    <td>Gene Commerce for PayPal從MagentoBraintree2.2.0模組轉換。</td>
  </tr>
  </tbody>
</table>
