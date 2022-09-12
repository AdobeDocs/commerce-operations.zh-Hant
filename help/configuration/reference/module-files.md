---
title: 模組配置檔案
description: 了解如何使用設定類型自訂模組。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---


# 模組組態檔概觀

本公司 `config.xml` 舊版Commerce中使用的設定檔案現在分為多個檔案，位於各種模組目錄中。 僅當模組請求特定配置類型時，商務的多個配置檔案才按需載入。

您可以使用這些檔案，也稱為 _配置類型_：自訂模組行為的特定方面。

多個模組可以聲明影響相同配置類型（如事件）的配置檔案，並合併這些多個配置檔案。

以下是此主題中使用的常見辭彙：

- **組態物件** — 負責定義和驗證配置類型的商務庫或類。 例如， `config.xml` is [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **配置階段** — 階段定義為 _主要_, _全球_，和 _區域_. 每個階段都決定何時載入配置類型並與同名配置類型合併。 例如， `module.xml` 檔案與其他檔案合併 `module.xml` 檔案。

- **配置範圍** — 作用域與配置級互補，定義配置類型模型。 例如， `adminhtml` 是一個區域範圍，在階段與其他模組一起載入。 `adminhtml` 設定。 如需詳細資訊，請參閱 [模組和區域](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## 配置載入和合併

本節探討如何載入和合併組態檔。

### 商務如何載入配置檔案

Commerce會以下列順序載入配置檔案（所有路徑都與您的Commerce安裝目錄相關）:

- 主配置([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml))。 此檔案用於引導Commerce。
- 來自模組的全局配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`)。 從所有模組收集特定配置檔案並將它們合併。
- 來自模組的區域特定配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`)。 從所有模組收集配置檔案，並將它們合併到全局配置中。 某些區域特定配置可以覆蓋或擴展全局配置。

where

- `<your component base dir>` 是元件所在的基目錄。 典型值為 `app/code` 或 `vendor` 相對於Commerce安裝目錄。
- `<vendorname>` 是元件的供應商名稱；例如，商務的供應商名稱是 `magento`.
- `<component-type>` 是下列其中一項：

   - `module-`:擴充功能或模組。
   - `theme-`:主題。
   - `language-`:語言包。

>[!INFO]
>
>目前，主題位於 `<magento_root>/app/design/frontend` 或 `<magento_root>/app/design/adminhtml`.

- `<component-name>`:元件的名稱，如 [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### 配置檔案合併

配置檔案中的節點根據其完全限定的XPath合併，該XPath具有在 `$idAttributes` 陣列聲明為其標識符。 此識別碼對於相同父節點下巢狀的所有節點必須是唯一的。

商務應用程式合併算法：

- 如果節點標識符相等（或者沒有定義標識符），則覆蓋節點中的所有基礎內容（屬性、子節點和標量內容）。
- 如果節點標識符不相等，則節點是父節點的新子節點。
- 如果原始文檔具有多個具有相同標識符的節點，則會觸發錯誤，因為無法識別標識符。

合併配置檔案後，生成的文檔將包含原始檔案中的所有節點。

>[!INFO]
>
>您可以使用 [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 用於調試和了解背後邏輯的類 [配置檔案載入器](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) 和 [合併設定](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) 程式。

## 配置類型、對象和介面

以下各節提供有關配置類型、其相應配置對象以及可用於處理對象的介面的資訊：

### 配置類型和對象

下表顯示了與其相關的每種配置類型和商務配置對象。

| 組態檔 | 說明 | 階段 | 組態物件 |
| --- | --- | --- | --- |
| `address_formats.xml` | 地址格式聲明 | 主要，全局 | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [訪問控制清單](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | 全球 | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [進階報表](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | 主要，全局 | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | 快取類型聲明 | 主要，全局 | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | 目錄屬性配置 | 全球 | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` 和 `env.php` | [部署配置](../reference/deployment-files.md) | 這些檔案可由內部配置處理器讀取/寫入。 | 沒有對象，無法自定義 |
| `config.xml` | 系統配置 | 主要，全局 | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [定義消息隊列系統的各個方面](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | 全球 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [配置cron組](../cron/custom-cron-reference.md#configure-cron-groups) | 全球 | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [指定cron組選項](../cron/custom-cron-reference.md) | 全球 | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [聲明性綱要](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | 全球 | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [依賴插入](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) 配置 | 主要，全局，區域 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | 提供EAV屬性配置 | 全球 | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | 電子郵件範本設定 | 全球 | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [搜尋引擎地區設定秒數設定](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | 全球 | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | 事件/觀察者設定 | 全球，區域 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | 導出實體配置 | 全球 | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [擴充功能屬性](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | 全球 | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | 定義欄位集 | 全球 | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [聲明索引器](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | 全球 | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | 聲明導入實體 | 全球 | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 定義管理員的功能表項目 | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | 定義模組配置資料和軟相關性 | 主要，全局 | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView配置](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | 主要，全局 | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 支付模組配置 | 主要，全局 | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento(_P)](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) 組態檔 | 全球 | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF設定 | 全球 | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 提供產品選項設定 | 全球 | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 定義產品類型 | 全球 | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [定義現有隊列與其用戶之間的關係](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | 全球 | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [定義發佈主題的交換。](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | 全球 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [定義消息路由規則、聲明隊列和交換](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | 全球 | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [進階報表](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | 全球 | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | 定義模組資源 | 全球 | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [路由](https://developer.adobe.com/commerce/php/development/components/routing/) 配置 | 區域 | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 定義銷售總額配置 | 全球 | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 提供搜尋引擎設定 | 全球 | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | 定義目錄搜索配置 | 全球 | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | 定義觸發私人內容區塊快取失效的動作 | 前端 | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | 定義系統配置頁的選項 | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | 模組驗證配置檔案 | 全球 | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | 定義Vendor_Module視圖配置值 | 全球 | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [設定Web API](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | 全球 | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [定義REST自定義路由](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | 全球 | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | 定義介面工具集 | 全球 | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 定義每個國家/地區的郵遞區號格式 | 全球 | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 配置介面

您可以使用下方的介面與組態檔互動 [Magento\框架\配置](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

如果您 [建立配置類型](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` 提供下列介面：

- [框架\配置\轉換器介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)，可將XML轉換為配置的記憶體內陣清單示。
- [框架\配置\資料介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)，會擷取指定範圍中的設定資料。
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)，可識別要讀取的檔案的位置 [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)，會從儲存中讀取配置資料，並選取其讀取的儲存。

也就是說，檔案系統、資料庫、其他儲存器根據合併規則合併配置檔案，並使用驗證結構驗證配置檔案。

- [框架\配置\方案定位器介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php)，可找出XSD架構。
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)，它返回作用域清單。
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)，會擷取驗證狀態。
