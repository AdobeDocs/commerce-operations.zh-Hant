---
source-git-commit: 00b8e1bb5ee259763ddb2c52065cee2af98641e0
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# 2024年10月Adobe Commerce 2.4.7 Beta重點說明

## 反白顯示

此版本的Adobe Commerce包含數項安全性修正與平台改良。

### 安全性

此版本中的下列安全性增強功能可改善與最新安全性最佳實務的相容性：

>[!NOTE]
>
>如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>設定</strong></td>
            <td>此版本包含下列安全性設定的增強功能：
              <ul>
                <li><strong>加密金鑰輪換</strong>：現在有新的CLI命令可用來變更您的加密金鑰。 如需詳細資訊，請參閱<a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">疑難排解加密金鑰輪換： CVE-2024-34102</a>知識庫文章。<!-- AC-12589 --></li>
                <li><strong>一次性密碼(OTP)設定</strong>：需要此更新才能解決2.4.7中<a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">回溯不相容變更</a>所導致的錯誤。<strong>[!UICONTROL OTP Window]</strong>欄位的描述現在提供設定的正確說明，預設值已從<code>1</code>變更為<code>29</code>。<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Platform

此次發行的下列平台升級可確保Adobe Commerce仍會是強大且可靠的平台，足以滿足現代商務環境的需求：

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>資料庫</strong></td>
            <td>根據我們的<a href="/help/release/lifecycle-policy.md">支援生命週期原則</a>，Adobe Commerce現在與下列資料庫技術的下列長期支援(LTS)版本相容：
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_（支援至2029年）_</em>：舊版(MariaDB 10.6)於2026年終止服務，因此此升級對於維持系統完整性和效能至關重要。 系統仍支援MariaDB 10.6，但Adobe建議在升級至Adobe Commerce 2.4.8時升級至MariaDB 11.4。</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_（支援到2032年）_</em>：舊版(MySQL 8.0)於2026年結束生命週期，因此此升級對於維持系統完整性和效能至關重要。 仍支援MySQL 8.0，但Adobe建議在升級至Adobe Commerce 2.4.8時升級至MySQL 8.4</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>此發行版本包含下列PHP增強功能：
            <ul>
              <li><strong>PHP 8.1</strong>：此發行版本移除了Adobe Commerce 2.4.8的PHP 8.1相容性。您必須先升級至PHP 8.3，才能升級至Adobe Commerce 2.4.8。</li>
              <li><strong>PHP 8.2</strong>： PHP 8.2的重大變更之一涉及將null傳遞至不可為nullable的內部函式引數的淘汰。 此版本解決核心平台元件中已棄用的PHP 8.1功能，並確保與PHP 8.2的相容性。</li>
              <li><strong>PHPUnit 10</strong>：此版本解決數項重要問題、增強相容性，並確保Adobe Commerce測試架構符合最新的業界標準。 Adobe建議所有擁有自訂內容的Commerce Marketplace廠商和客戶，確認其單位和整合測試會在PHPUnit 10 （而非9）上執行。</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>元件</strong></td>
            <td>下列協力廠商<a href="/help/release/packages/adobe-commerce.md">元件和相依性</a>已更新至最新穩定版本，以提升平台穩定性和效能：
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>搜尋</strong></td>
            <td>Adobe Commerce現在已針對OpenSearch 2.x最佳化，不再與Elasticsearch相容。 程式碼基底中現在已不建議使用所有Elasticsearch7和8模組及類別。 Adobe強烈建議針對內部部署和雲端基礎結構部署轉換至OpenSearch，以確保持續的支援和相容性。 請參閱<a href="/help/upgrade/prepare/opensearch-migration.md">移轉至OpenSearch</a>。
              <ul>
                <li>Elasticsearch7和Elasticsearch8選項現在在管理員設定中標籤為「（已棄用）」。</li>
                <li>當使用者在管理員設定中選擇Elasticsearch作為搜尋引擎時，Commerce會顯示通知，指出： <em>「Adobe不再支援此搜尋引擎選項。 我們建議改用OpenSearch做為搜尋引擎。"</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### 效能

此版本包含下列效能增強功能：

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>索引子</strong></td>
            <td>安裝新版Adobe Commerce或從舊版升級時，所有索引器的預設<a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">索引器模式</a>現在是[!UICONTROL **Update by Schedule**]。 新的預設值可確保索引器符合建議的設定，進而改善系統效能並減少潛在問題。</td>
        </tr>
    </tbody>
</table>

### 品質

此版本包含下列品質增強功能：

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>詳細目錄</strong></td>
           <td>系統現在運作時沒有InventoryIndexer引進的先前隱藏的目錄相依性，確保產品建立、顯示模式切換、庫存狀態變更和其他相關功能如預期般運作。 以前，這種隱藏的相依性會導致不一致的情況，因為不同的實體已同步化，而索引器使用不同的實體。</td>
        </tr>
        <tr>
            <td><strong>訂購</strong></td>
            <td>為了將混淆最小化，<a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">訂單詳細資料</a>頁面中的[!UICONTROL **Submit Comment**]按鈕標籤變更為[!UICONTROL **Update**]。</td>
        </tr>
    </tbody>
</table>

### GraphQL

此版本包含下列GraphQL增強功能：

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>一般增強功能</strong></td>
           <td>此版本包含下列一般GraphQL API增強功能：
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>：已將<code>grouped_product_image</code>和<code>configurable_product_image</code>欄位新增至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a>型別。</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>：已將下列新欄位新增至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a>型別，以支援精確的定價顯示和折扣計算：
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrices</strong>：已將<code>grand_total_excluding_tax</code>欄位新增至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a>型別，提供明確的含稅定價。</li>
              <li><!--LYNX-542--><strong>updateCartItems變異</strong>：已更新<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a>變異，以傳回包含錯誤詳細資訊的成功回應，而非例外狀況。 增強錯誤對應以提高使用者通知的清晰度。</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config查詢</strong>：已將<code>theme</code>欄位引入<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a>查詢。 此欄位可讓您指定用來呈現reCaptcha的主題名稱。</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>：在<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a>中引入<code>quantity</code>欄位，以提供庫存層級的詳細資料。 它會根據管理員設定顯示可用庫存或Null。</li>
               <li><!--LYNX-460--><strong>套裝產品</strong>：修正套裝產品的定價顯示，確保價格與貨幣資訊準確。</li>
               <li><!--LYNX-547--><strong>數量</strong>：已針對數量不足且無法使用的通知調整訊息。</li>
               <li><!--LYNX-541--><strong>UnffectedStockError型別</strong>：新增新的<code>InsufficientStockError</code>型別，以處理庫存量不足的情況。 已調整結構描述以支援新的錯誤型別，進而增強錯誤報告功能。</li>
               <li><!--LYNX-476--><strong>庫存量</strong>：加強錯誤訊息，以包含可用的庫存量。 在訂單更新期間，為使用者提供更清楚的存貨層次深入分析。</li>
               <li><!--LYNX-377--><strong>要求的數量</strong>：已新增<code>not_available_message</code>至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>。</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>客戶管理</strong></td>
           <td>此版本包含下列客戶管理增強功能：
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken變異</strong>：改善<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a>變體的錯誤處理，以提供未確認電子郵件的特定訊息。 支援更佳的使用者指引和錯誤解決方案。</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail突變</strong>：新增重新傳送電子郵件確認的<code>resendConfirmationEmail</code>突變。</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Order management</strong></td>
           <td>此版本包含下列使用者訂單管理增強功能：
             <ul>
              <li><!--LYNX-470--><strong>第一筆訂單的日期</strong>：已將新的<code>date_of_first_order</code>欄位新增至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a>型別。</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>：擴充<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a>型別以包含自訂屬性，增強訂單詳細資料的可見度。 支援在訂單確認頁面上顯示的其他資訊。</li>
              <li><!--LYNX-458--><strong>guestOrder和guestOrderByToken查詢</strong>：已更新<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a>和<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a>查詢以包含自訂位址屬性，確保新帳戶的完整位址資訊。</li>
              <li><!--LYNX-450--><strong>CustomerOrder型別</strong>：已新增<code>is_virtual</code>欄位至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>型別，支援虛擬產品識別。 藉由區分虛擬與實體產品來增強訂單處理能力。</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>：已新增類似於<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a>的<code>OrderItemPrices</code>型別至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a>，其中包含數個新的價格欄位。</li>
              <li><!--LYNX-448--><strong>合併來賓訂單</strong>：改善API功能，根據電子郵件比對將來賓訂單與客戶帳戶合併。 簡化回頭客戶的訂單管理。</li>
              <li><!-- LYNX-523: --><strong>available_actions欄位</strong>：已擴充<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>型別以包含<code>available_actions</code>欄位，以便進行更好的訂單管理。 「available_actions」欄位對應至列示可針對訂單執行之可能動作的列舉。</li>
              <li><!-- LYNX-524 --><strong>CustomerOrder型別</strong>：已將<code>customer_info</code>欄位新增至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>型別。 此欄位需要和<code>OrderCustomerInfo</code>，這會定義有關客戶名稱的詳細資料。</li>
              <li><!--LYNX-519--><strong>訂單取消的錯誤碼</strong>：已將詳細的錯誤碼新增至<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a>型別。 改善訂單取消流程的錯誤處理和使用者回饋。</li>
              <li><!--LYNX-515--><strong>啟用來賓使用者來建立訂單退貨</strong>：已調整<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a>突變以支援來賓訂單退貨。</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder突變</strong>：新增新的<code>confirmCancelOrder</code>突變，方便訪客使用者取消訂單。</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
