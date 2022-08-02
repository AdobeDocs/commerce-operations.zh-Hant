---
title: 模組配置檔案
description: 瞭解如何使用配置類型自定義模組。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '2019'
ht-degree: 0%

---


# 模組配置檔案概述

C.A.B. `config.xml` Commerce早期版本中使用的配置檔案現在被分成多個檔案，這些檔案位於各種模組目錄中。 僅當模組請求特定配置類型時，Commerce的多個配置檔案才會按需載入。

可以使用這些檔案，也稱為 _配置類型_ — 定制模組行為的特定方面。

多個模組可以聲明影響相同配置類型（例如，事件）的配置檔案，並合併這些多個配置檔案。

以下是本主題中使用的常用術語：

- **配置對象** — 負責定義和驗證配置類型的Commerce庫或類。 例如， `config.xml` 是 [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php)。

- **配置階段** — 階段定義為 _主_。 _全球_, _面積_。 每個階段確定何時載入配置類型並與同一命名的配置類型合併。 比如說， `module.xml` 檔案與其他檔案合併 `module.xml` 的子菜單。

- **配置範圍** — 作用域與配置階段互補，定義配置類型模型。 比如說， `adminhtml` 是與其他模組一起載入的區域範圍。 `adminhtml` 配置。 有關詳細資訊，請參見 [模組和區域](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_and_areas.html)。

## 配置載入和合併

本節討論如何載入和合併配置檔案。

### Commerce如何載入配置檔案

Commerce按以下順序載入配置檔案（所有路徑都與Commerce安裝目錄相關）:

- 主配置([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml))。 此檔案用於引導Commerce。
- 模組的全局配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`)。 從所有模組收集某些配置檔案並將它們合併在一起。
- 模組中的特定區域配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`)。 從所有模組收集配置檔案並將它們合併到全局配置中。 某些特定區域的配置可以覆蓋或擴展全局配置。

何處

- `<your component base dir>` 是元件所在的基目錄。 典型值為 `app/code` 或 `vendor` 相對於Commerce安裝目錄。
- `<vendorname>` 是元件的供應商名稱；例如，Commerce的供應商名稱為 `magento`。
- `<component-type>` 是以下之一：

   - `module-`:擴展或模組。
   - `theme-`:的子菜單。
   - `language-`:語言包。

>[!INFO]
>
>目前，主題位於 `<magento_root>/app/design/frontend` 或 `<magento_root>/app/design/adminhtml`。

- `<component-name>`:元件的名稱（如中定義） [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json)。

### 配置檔案合併

配置檔案中的節點基於其完全限定的XPath合併，該XPath具有在中定義的特殊屬性 `$idAttributes` 陣列聲明為其標識符。 對於嵌套在同一父節點下的所有節點，此標識符必須唯一。

商業應用合併算法：

- 如果節點標識符相等（或未定義標識符），則覆蓋節點中的所有基礎內容（屬性、子節點和標量內容）。
- 如果節點標識符不相等，則節點是父節點的新子節點。
- 如果原始文檔具有多個具有相同標識符的節點，則會觸發錯誤，因為無法識別標識符。

合併配置檔案後，生成的文檔將包含原始檔案中的所有節點。

>[!INFO]
>
>您可以使用 [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 用於調試和理解背後邏輯的類 [配置檔案載入程式](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) 和 [合併配置](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) 處理。

## 配置類型、對象和介面

以下各節提供有關配置類型、其相應配置對象以及可用於處理這些對象的介面的資訊：

- [配置類型和對象](#config-files-classes-objects)
- [配置介面](#config-files-classes-int)

### 配置類型和對象

下表顯示了每種配置類型及其相關的Commerce配置對象。

| 配置檔案 | 說明 | 舞台 | 配置對象 |
| --- | --- | --- | --- |
| `address_formats.xml` | 地址格式聲明 | 主要，全局 | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [訪問控制清單](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication.html#relationship-between-aclxml-and-webapixml) | 全球 | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [高級報告](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | 主要，全局 | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | 快取類型聲明 | 主要，全局 | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | 目錄屬性配置 | 全球 | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` 和 `env.php` | [部署配置](../reference/deployment-files.md) | 這些檔案可由內部配置處理器讀/寫。 | 沒有對象，無法自定義 |
| `config.xml` | 系統配置 | 主要，全局 | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [定義消息隊列系統的各個方面](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#communicationxml) | 全球 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [配置cron組](../cron/custom-cron-reference.md#configure-cron-groups) | 全球 | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [指定cron組選項](../cron/custom-cron-reference.md) | 全球 | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [聲明性架構](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html) | 全球 | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [依賴項注入](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/depend-inj.html) 配置 | 主要、全局、區域 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | 提供EAV屬性配置 | 全球 | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | 電子郵件模板配置 | 全球 | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [搜索引擎區域設定停止字配置](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | 全球 | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | 事件/觀察器配置 | 全局，區域 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | 導出實體配置 | 全球 | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [擴展屬性](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/attributes.html#extension) | 全球 | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | 定義欄位集 | 全球 | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [聲明索引器](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html) | 全球 | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | 聲明導入實體 | 全球 | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 定義管理員的菜單項 | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | 定義模組配置資料和軟依賴關係 | 主要，全局 | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView配置](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html#mview-configuration) | 主要，全局 | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 付款模組配置 | 主要，全局 | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento(_P)](https://devdocs.magento.com/guides/v2.4/mrg/module-persistent.html) 配置檔案 | 全球 | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF設定 | 全球 | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 提供產品選項配置 | 全球 | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 定義產品類型 | 全球 | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [定義現有隊列與其使用者之間的關係](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queueconsumerxml) | 全球 | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [定義發佈主題的交換。](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuepublisherxml) | 全球 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [定義消息路由規則、聲明隊列和交換](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuetopologyxml) | 全球 | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [高級報告](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | 全球 | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | 定義模組資源 | 全球 | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [路由](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/routing.html) 配置 | 面積 | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 定義銷售總額配置 | 全球 | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 提供搜索引擎配置 | 全球 | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | 定義目錄搜索配置 | 全球 | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | 定義觸發私有內容塊快取無效的操作 | 前 | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | 定義系統配置頁的選項 | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | 模組驗證配置檔案 | 全球 | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | 定義Vendor_Module視圖配置值 | 全球 | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [配置Web API](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/service-contracts/service-to-web-service.html) | 全球 | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [定義REST自定義路由](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/webapi/custom-routes.html) | 全球 | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | 定義小部件 | 全球 | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 定義每個國家/地區的郵遞區號格式 | 全球 | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 配置介面

您可以使用下面的介面與配置檔案交互 [Magento\框架\配置](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config)。

如果 [建立配置類型](../reference/config-create-types.md#create-configuration-types)。

`Magento\Framework\Config` 提供了以下介面：

- [框架\配置\轉換器介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)，它將XML轉換為配置的記憶體陣清單示。
- [框架\配置\資料介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)，它檢索指定作用域中的配置資料。
- [框架\配置\檔案解析器介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)，它標識要讀取的檔案的位置 [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)。
- [框架\配置\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)，從儲存中讀取配置資料並選擇從中讀取的儲存。

即，檔案系統、資料庫、其他儲存器按照合併規則合併配置檔案，並用驗證方案驗證配置檔案。

- [框架\配置\架構定位器介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php)，它定位XSD架構。
- [框架\配置\作用域清單介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)，返回作用域清單。
- [框架\配置\驗證狀態介面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)，它檢索驗證狀態。
