---
title: 模組組態檔
description: 瞭解如何使用設定型別來自訂模組。
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---

# 模組組態檔概觀

舊版Commerce中使用的`config.xml`組態檔職責現在由位於不同模組目錄中的數個檔案分擔。 只有當模組請求特定設定型別時，Commerce才會視需要載入多個設定檔案。

您可以使用這些檔案（也稱為&#x200B;_組態型別_）來自訂模組行為的特定方面。

多個模組可宣告會影響相同組態型別的組態檔案（例如事件），然後合併這些多個組態檔案。

以下是此主題中使用的常用辭彙：

- **組態物件** — 負責定義及驗證組態型別的Commerce程式庫或類別。 例如，`config.xml`的組態物件是[Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php)。

- **組態階段** — 階段定義為&#x200B;_主要_、_全域_&#x200B;和&#x200B;_區域_。 每個階段會決定何時載入組態型別並與相同名稱的組態型別合併。 例如，`module.xml`個檔案與其他`module.xml`個檔案合併。

- **組態範圍** — 作為組態階段的補充，範圍定義了組態型別模型。 例如，`adminhtml`是在階段與其他模組`adminhtml`設定一起載入的區域範圍。 如需詳細資訊，請參閱[模組和區域](https://developer.adobe.com/commerce/php/architecture/modules/areas/)。

## 設定載入和合併

本節討論如何載入及合併組態檔。

### Commerce如何載入設定檔案

Commerce會依照以下順序載入設定檔(所有路徑都相對於Commerce安裝目錄)：

- 主要組態([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml))。 此檔案用於啟動Commerce。
- 來自模組(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`)的全域組態。 會從所有模組收集特定組態檔，並將它們合併在一起。
- 來自模組(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`)的區域特定組態。 從所有模組收集組態檔，並將其合併至全域組態。 某些區域特定設定可能會覆寫或擴充全域設定。

位置

- `<your component base dir>`是元件所在的基本目錄。 相對於Commerce安裝目錄，一般值為`app/code`或`vendor`。
- `<vendorname>`是元件的廠商名稱；例如，Commerce的廠商名稱為`magento`。
- `<component-type>`為下列其中一項：

   - `module-`：擴充功能或模組。
   - `theme-`：主題。
   - `language-`：語言套件。

>[!INFO]
>
>目前，主題位於`<magento_root>/app/design/frontend`或`<magento_root>/app/design/adminhtml`下。

- `<component-name>`： [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json)中定義的元件名稱。

### 設定檔合併

組態檔中的節點會根據其完整限定的XPath進行合併，XPath在`$idAttributes`陣列中定義特殊屬性，宣告為其識別碼。 此識別碼對巢狀內嵌於相同父項節點下的所有節點而言必須是唯一的。

Commerce應用程式合併演演算法：

- 如果節點識別碼相等（或如果未定義識別碼），則會覆寫節點中的所有基礎內容（屬性、子節點和純量內容）。
- 如果節點識別碼不相等，則該節點是父節點的新子節點。
- 如果原始檔案有多個具有相同識別碼的節點，則會觸發錯誤，因為無法辨別識別碼。

合併組態檔案後，產生的檔案會包含原始檔案中的所有節點。

>[!INFO]
>
>您可以使用[\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php)類別進行偵錯，並瞭解[組態檔載入器](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125)與[合併組態](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144)處理序背後的邏輯。

## 組態型別、物件和介面

以下各節提供有關配置型別、其對應的配置物件以及可用於處理物件的介面的資訊：

### 組態型別和物件

下表顯示每種設定型別及其相關的Commerce設定物件。

| 組態檔 | 說明 | 階段 | 設定物件 |
| --- | --- | --- | --- |
| `address_formats.xml` | 位址格式宣告 | 主要，全域 | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [存取控制清單](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | 全域 | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [進階報告]https://developer.adobe.com/commerce/php/development/advanced-reporting/data-collection/) | 主要，全域 | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | 快取型別宣告 | 主要，全域 | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | 目錄屬性設定 | 全域 | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php`和`env.php` | [部署組態](../reference/deployment-files.md) | 這些檔案可由內部設定處理器讀取/寫入。 | 沒有物件，無法自訂 |
| `config.xml` | 系統組態 | 主要，全域 | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [定義訊息佇列系統的方面](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | 全域 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [設定cron群組](../cron/custom-cron-reference.md#configure-cron-groups) | 全域 | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [指定cron群組選項](../cron/custom-cron-reference.md) | 全域 | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [宣告式結構描述](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | 全域 | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [相依性插入](https://developer.adobe.com/commerce/php/development/components/dependency-injection/)組態 | 主要、全域、區域 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | 提供EAV屬性組態 | 全域 | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | 電子郵件範本設定 | 全域 | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [搜尋引擎地區設定停用字詞設定](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | 全域 | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | 事件/觀察者設定 | 全域，區域 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | 匯出實體設定 | 全域 | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [延伸屬性](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | 全域 | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | 定義欄位集 | 全域 | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [宣告索引子](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | 全域 | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | 宣告匯入實體 | 全域 | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 定義管理員的功能表專案 | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | 定義模組設定資料和軟性相依性 | 主要，全域 | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView設定](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | 主要，全域 | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 付款模組設定 | 主要，全域 | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_持續](https://developer.adobe.com/commerce/php/module-reference/module-persistent/)設定檔 | 全域 | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF設定 | 全域 | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 提供產品選項設定 | 全域 | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 定義產品型別 | 全域 | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [定義現有佇列與其消費者之間的關係](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | 全域 | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [定義發佈主題的Exchange。](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | 全域 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [定義郵件路由規則，宣告佇列和交換](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | 全域 | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [進階報告](https://developer.adobe.com/commerce/php/development/advanced-reporting/report-xml/) | 全域 | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | 定義模組資源 | 全域 | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [路由](https://developer.adobe.com/commerce/php/development/components/routing/)設定 | 區域 | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 定義銷售總計設定 | 全域 | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 提供搜尋引擎設定 | 全域 | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | 定義目錄搜尋設定 | 全域 | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | 定義會觸發私人內容區塊快取失效的動作 | 前端 | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | 定義系統組態頁面的選項 | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | 模組驗證設定檔 | 全域 | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | 定義Vendor_Module檢視設定值 | 全域 | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [設定網頁API](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | 全域 | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [定義REST自訂路由](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | 全域 | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | 定義Widget | 全域 | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 定義每個國家/地區的郵遞區號格式 | 全域 | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 設定介面

您可以使用[Magento\架構\組態](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config)下的介面與組態檔互動。

如果您[建立組態型別](../reference/config-create-types.md#create-configuration-types)，就可以使用這些介面。

`Magento\Framework\Config`提供下列介面：

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)，它會將XML轉換成組態的記憶體陣列表示。
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)，它會擷取指定範圍內的組態資料。
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)，可識別[Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)要讀取的檔案位置。
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)，會從存放裝置讀取組態資料，並選取要讀取的存放裝置。

也就是說，檔案系統、資料庫和其他儲存體會根據合併規則合併組態檔，並使用驗證結構來驗證組態檔。

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php)，可找到XSD結構描述。
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)，傳回範圍清單。
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)，它會擷取驗證狀態。
